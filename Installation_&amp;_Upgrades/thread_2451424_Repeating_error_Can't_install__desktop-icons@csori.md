---
title: "Repeating error: Can't install  desktop-icons@csoriano"
date: 2020-10-04
forum: Installation &amp; Upgrades
---

### Post by Paddy Landau on 2020-10-04
On my fresh installation of Ubuntu 20.04 a couple of weeks ago, I kept having a problem with the default Gnome extension [Desktop Icons]("https://extensions.gnome.org/extension/1465/desktop-icons/"), in addition to which it has badly limited functionality.

Unfortunately, it cannot be uninstalled the normal way.

So, I followed instructions (as advised in several places) to uninstall it as follows.
```
sudo rm --recursive /usr/share/gnome-shell/extensions/desktop-icons@csoriano/   # After making a backup
```
With that gone, I was able to install the oddly-named but far superior [Desktop Icons NG (DING)]("https://extensions.gnome.org/extension/2087/desktop-icons-ng-ding/") (by the same author), which works perfectly.

Unfortunately, I get the following notification several times a day:[INDENT]Can't install "desktop-icons@csoriano":
This is an extension enabled by your current mode, you can't install manually any update in that session.[/INDENT]
[ATTACH=CONFIG]287098[/ATTACH]
I cannot get rid of this error. I tried two things.

[LIST]
[*]I uninstalled Desktop Icons NG (DING), and restored the deleted folder. That made no difference, and in any case it didn't restore the original Desktop Icons as you might think it would.
[*]I attempted to install Desktop Icons, but it refuses to install, giving the same error.
[/LIST]
I don't know what else to do.

I subsequently reinstalled Desktop Icons NG (DING), otherwise I have nothing on my desktop, but this error continues to notify me several times a day.

Here is my list of extensions.
```
$ gnome-extensions listcaffeine@patapon.info
clipboard-indicator@tudmotu.com
clock-override@gnomeshell.kryogenix.org
user-theme@gnome-shell-extensions.gcampax.github.com
TopIcons@phocean.net
ding@rastersoft.com
wsmatrix@martin.zurowietz.de
ubuntu-appindicators@ubuntu.com
ubuntu-dock@ubuntu.com
```
I'm using standard Ubuntu 20.04 with Gnome 3.36.3

How can I stop these notifications, please?

---

### Post by Paddy Landau on 2020-10-09
I posted this question on Ask Ubuntu, and it [has an answer]("https://askubuntu.com/a/1281240/2088").

---

