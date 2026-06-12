---
title: "Error message upon new install"
date: 2019-05-19
forum: Installation &amp; Upgrades
---

### Post by chopra on 2019-05-19
Hi Guys,
I just got a new laptop, Toshiba Tecra C40, and decided to install Ubuntu 18.04 LTS on it.  I've installed Ubuntu on a previous laptop, but that was back in the 14 LTS days.

Anyway, I followed a similar procedure as I did last time.  I wanted to have a dual boot, so before installing Ubuntu, I shrank the main windows partition from 900 GB to 430 GB, leaving some empty space.

I then inserted a USB drive and chose the option "Try Ubuntu without installing".  Once on, I used GParted to create an ext4 primary partition and a 6 GB swap partition in the available space created by shrinking Windows.

Then, I clicked on the install desktop icon, and, for the installation options, I chose "full installation", and "something else" instead of wipe out windows.
I then assigned the ext4 partition to the / mount point, and installed.  (I had seen on the internet that some people create another partition and mount it to /home, but I didn't do that.)

I got a warning saying that the partition hadn't been formatted, and that if I had an /etc or /lib or /boot directory in any partition, it would be deleted.  I don't have any other linux OS's on this machine, so I ignored the warning, and continued.  Everything went fine, except at the end, when I got a message saying there were errors during installation, and it needed to reboot to try and fix them.

Rebooting was difficult. When it turned off, I removed the thumbdrive, then it immediately started zipping through all these errors on the screen I couldn't record.
Then, it froze, and I pressed the power button to get it to go off.

After starting it up again, everything seems fine.  I get the grub menu, I can choose windows or ubuntu, windows works fine, and I so far haven't noticed any problems with ubuntu.

However, I'm wondering if there may be some lingering errors in the system, and if there's an easy way to check, given the error message. If not, I could just keep running and wait to see if there's problems, but an ounce of of prevention is a pound of cure, so I just thought I'd ask if anyone has any thoughts.

Thanks, chopra

PS There was a bunch of errors in the /var/log/syslog file that I didn't understand. Why would something say "ignored relative path"?  They may or may not mean anything.

I did get the following output on my var/log/syslog file, which I've never seen before:
```
May 18 19:57:38 Toshiba-TECRA-C40-D ureadahead[268]: ureadahead:systemd: Ignored relative path
May 18 19:57:38 Toshiba-TECRA-C40-D ureadahead[268]: ureadahead:unit-root: Ignored relative path
May 18 19:57:38 Toshiba-TECRA-C40-D ureadahead[268]: ureadahead:lib: Ignored relative path
May 18 19:57:38 Toshiba-TECRA-C40-D ureadahead[268]: ureadahead:modules: Ignored relative path
May 18 19:57:38 Toshiba-TECRA-C40-D ureadahead[268]: ureadahead:: Ignored relative path
May 18 19:57:38 Toshiba-TECRA-C40-D ureadahead[268]: ureadahead:run: Ignored relative path
May 18 19:57:38 Toshiba-TECRA-C40-D ureadahead[268]: ureadahead:systemd: Ignored relative path
May 18 19:57:38 Toshiba-TECRA-C40-D ureadahead[268]: ureadahead:unit-root: Ignored relative path
May 18 19:57:38 Toshiba-TECRA-C40-D ureadahead[268]: ureadahead:lib64: Ignored relative path
May 18 19:57:38 Toshiba-TECRA-C40-D ureadahead[268]: ureadahead:: Ignored relative path
May 18 19:57:38 Toshiba-TECRA-C40-D ureadahead[268]: ureadahead:run: Ignored relative path
May 18 19:57:38 Toshiba-TECRA-C40-D ureadahead[268]: ureadahead:systemd: Ignored relative path
May 18 19:57:38 Toshiba-TECRA-C40-D ureadahead[268]: ureadahead:unit-root: Ignored relative path
May 18 19:57:38 Toshiba-TECRA-C40-D ureadahead[268]: ureadahead:proc: Ignored relative path
May 18 19:57:38 Toshiba-TECRA-C40-D ureadahead[268]: ureadahead:: Ignored relative path
May 18 19:57:38 Toshiba-TECRA-C40-D ureadahead[268]: ureadahead:run: Ignored relative path
May 18 19:57:38 Toshiba-TECRA-C40-D ureadahead[268]: ureadahead:systemd: Ignored relative path
May 18 19:57:38 Toshiba-TECRA-C40-D ureadahead[268]: ureadahead:unit-root: Ignored relative path
May 18 19:57:38 Toshiba-TECRA-C40-D ureadahead[268]: ureadahead:root: Ignored relative path
May 18 19:57:38 Toshiba-TECRA-C40-D ureadahead[268]: ureadahead:: Ignored relative path
May 18 19:57:38 Toshiba-TECRA-C40-D ureadahead[268]: ureadahead:run: Ignored relative path
May 18 19:57:38 Toshiba-TECRA-C40-D ureadahead[268]: ureadahead:systemd: Ignored relative path
May 18 19:57:38 Toshiba-TECRA-C40-D ureadahead[268]: ureadahead:unit-root: Ignored relative path
May 18 19:57:38 Toshiba-TECRA-C40-D ureadahead[268]: ureadahead:run: Ignored relative path
May 18 19:57:38 Toshiba-TECRA-C40-D ureadahead[268]: ureadahead:boltd: Ignored relative path
```

There's also a few other error messages in the file highlighted in red:
```
May 18 19:53:31 Toshiba-TECRA-C40-D gpu-manager[650]: Error: can't open /lib/modules/4.18.0-20-generic/updates/dkms
May 18 19:53:31 Toshiba-TECRA-C40-D kernel: [    1.132593] tpm tpm0: A TPM error (2314) occurred attempting the self test
May 18 19:53:31 Toshiba-TECRA-C40-D kernel: [    1.183681] RAS: Correctable Errors collector initialized.
May 18 19:53:31 Toshiba-TECRA-C40-D kernel: [    7.237454] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
May 18 19:53:38 Toshiba-TECRA-C40-D snapd[678]: helpers.go:145: error trying to compare the snap system key: system-key missing on disk
May 18 19:53:39 Toshiba-TECRA-C40-D snapd[678]: stateengine.go:102: state ensure error: Get [https://api.snapcraft.io/api/v1/snaps/sections:](https://api.snapcraft.io/api/v1/snaps/sections:) dial tcp: lookup api.snapcraft.io: no such host

May 18 19:54:08 Toshiba-TECRA-C40-D gnome-shell[908]: Error looking up permission: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.impl.portal.PermissionStore was not provided by any .service files
May 18 19:54:12 Toshiba-TECRA-C40-D gnome-shell[908]: JS ERROR: TypeError: this._currentWindow is null#012_setCurrentRect@resource:///org/gnome/shell/ui/keyboard.js:536:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_init/<@resource:///org/gnome/shell/ui/keyboard.js:503:13
May 18 19:54:12 Toshiba-TECRA-C40-D gnome-shell[908]: JS ERROR: TypeError: this._currentWindow is null#012_setCurrentRect@resource:///org/gnome/shell/ui/keyboard.js:536:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_init/<@resource:///org/gnome/shell/ui/keyboard.js:503:13
May 18 19:54:15 Toshiba-TECRA-C40-D gnome-shell[908]: JS ERROR: TypeError: this._currentWindow is null#012_setCurrentRect@resource:///org/gnome/shell/ui/keyboard.js:536:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_init/<@resource:///org/gnome/shell/ui/keyboard.js:503:13
May 18 19:54:22 Toshiba-TECRA-C40-D gnome-shell[908]: message repeated 14 times: [ JS ERROR: TypeError: this._currentWindow is null#012_setCurrentRect@resource:///org/gnome/shell/ui/keyboard.js:536:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_init/<@resource:///org/gnome/shell/ui/keyboard.js:503:13]
May 18 19:54:23 Toshiba-TECRA-C40-D /usr/lib/gdm3/gdm-x-session[1687]: #011(WW) warning, (EE) error, (NI) not implemented, (??) unknown.

May 18 19:55:43 Toshiba-TECRA-C40-D gnome-shell[1849]: JS ERROR: TypeError: this._currentWindow is null#012_setCurrentRect@resource:///org/gnome/shell/ui/keyboard.js:536:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_init/<@resource:///org/gnome/shell/ui/keyboard.js:503:13#012pushModal@resource:///org/gnome/shell/ui/modalDialog.js:226:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012open@resource:///org/gnome/shell/ui/modalDialog.js:155:14#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_ensureOpen@resource:///org/gnome/shell/ui/components/polkitAgent.js:212:14#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_onSessionRequest@resource:///org/gnome/shell/ui/components/polkitAgent.js:310:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22
May 18 19:55:43 Toshiba-TECRA-C40-D gnome-shell[1849]: JS ERROR: TypeError: this._currentWindow is null#012_setCurrentRect@resource:///org/gnome/shell/ui/keyboard.js:536:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_init/<@resource:///org/gnome/shell/ui/keyboard.js:503:13
May 18 19:55:43 Toshiba-TECRA-C40-D gnome-shell[1849]: message repeated 3 times: [ JS ERROR: TypeError: this._currentWindow is null#012_setCurrentRect@resource:///org/gnome/shell/ui/keyboard.js:536:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_init/<@resource:///org/gnome/shell/ui/keyboard.js:503:13]
```

---

### Post by DuckHook on 2019-05-19
Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

