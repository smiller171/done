<h1 align="center">
  <img src="https://i.imgur.com/0LElCjU.png" alt="done" width="300"></a>
  <br>
</h1>

<h4 align="center">A <a href="https://fishshell.com/">fish shell</a> package to automatically receive notifications when long processes finish.</h4>

<p align="center">
  <a href="https://opencollective.com/done" alt="Financial Contributors on Open Collective"><img src="https://opencollective.com/done/all/badge.svg?label=financial+contributors" /></a> <img src="https://img.shields.io/badge/stability-stable-green.svg" alt="Stability: Stable">
  <img src="https://img.shields.io/github/release/smiller171/done.svg" alt="Release version">
  <img src="https://img.shields.io/badge/fish-%3E=2.3.0-orange.svg" alt="fish >=2.3.0">
  <img src="https://img.shields.io/badge/license-MIT-lightgray.svg" alt="License: MIT">
</p>
<br>

Just go on with your normal life. You will get a notification when a process takes more than 5 seconds finish, and the terminal window not in the foreground.

After installing you could type, for instance `sleep 6`, and start using other app. After 6 seconds you should get a notification.

This is a fork of [franciscolourenco/done](https://github.com/fanciscolourenco/done). I intend to keep it somewhat maintained, but time constraints abound. Pull requests welcome, I'll get to them as soon as I can. If you're interested in helping maintain, let me know in a GH issue or conversation.

## Installation

#### Using [Fisher](https://github.com/jorgebucaran/fisher)

```fish
fisher install smiller171/done
```

#### Manually

```fish
curl -Lo ~/.config/fish/conf.d/done.fish --create-dirs https://raw.githubusercontent.com/smiller171/done/master/conf.d/done.fish
```

#### Arch Linux

Install the `fish-done` package from AUR.

```fish
yay -S fish-done
```

## Dependencies

- If you want notifications with icons on macOS, please install `terminal-notifier` with

```fish
brew install terminal-notifier
```

- If you are using https://swaywm.org please install `jq`.


- If you are using Windows Subsystem for Linux (WSL) you may need to install [wslu](https://github.com/wslutilities/wslu), but usually it is pre-installed.

## Updating

```fish
fisher update smiller171/done
```

## Settings

#### Only display notifications if a command takes more than a certain amount of time

```fish
set -U __done_min_cmd_duration 5000  # default: 5000 ms
```

#### Prevent specific commands from triggering notifications. Accepts a regex.

This is useful to exclude commands like `git commit` for instance, since it could trigger unwanted notifications if it is configured to use an external editor. This is also useful with `set -U __done_allow_nongraphical 1` to prevent notifications for commands normally run interactively that you do not want to get done notifications for.

```fish
set -U __done_exclude 'git (?!push|pull)'  # default: all git commands, except push and pull. accepts a regex.
```

#### Execute a custom command instead of showing the default notifications. The `done` notification title and message can also be passed.

```fish
set -U __done_notification_command "your-command \$title \$message"
```

#### Play sound when showing notifications.

```fish
set -U __done_notify_sound 1
```

#### When using `sway`, do not show notifications for visible windows.

```fish
set -U __done_sway_ignore_visible 1
```

#### For Linux, set the urgency level for notifications sent via notify-send (low, normal, critical). The default is "normal" for regular commands, and "critical" for failed commands.

```fish
set -U __done_notification_urgency_level low
set -U __done_notification_urgency_level_failure normal
```

#### Allow notifications to be sent on systems without graphical capabilities. Note this requires you to also set `__done_notification_command`.

```fish
set -U __done_allow_nongraphical 1
```
#### For Linux, set the timeout in milliseconds at which to expire the notification. The default is "0" (never expire).

```fish
set -U __done_expire_time 3000 # 3 seconds
```
## Support

- [fish](https://fishshell.com) 2.3.0+
- macOS 10.8+ via Notification Center.
- Linux via `notify-send`. Otherwise bell sound is played.
- Windows 10 via Windows Subsystem for Linux (WSL) and PowerShell.

## Credits

- [Scott Miller](https://github.com/smiller171) - Fork maintainer
- [Francisco Lourenço](https://github.com/franciscolourenco/) - Original Maintainer
- [Daniel Wehner](https://dawehner.github.io/) - Proof of Concept
- [Thanh Duc Nguyen](http://iamthanh.com/) - Logo

## Contributors

This is a fork of franciscolourenco/done. I intend to keep it somewhat maintained, but time constraints abound. Pull requests welcome, I'll get to them as soon as I can. If you're interested in helping maintain, let me know in a GH issue or conversation.

This project exists thanks to all the people who contribute. [[Contribute](CONTRIBUTING.md)].
<a href="https://github.com/franciscolourenco/done/graphs/contributors"><img src="https://opencollective.com/done/contributors.svg?width=890&button=false" /></a>

## License

Done is MIT licensed. See [LICENSE](LICENSE) for details.
