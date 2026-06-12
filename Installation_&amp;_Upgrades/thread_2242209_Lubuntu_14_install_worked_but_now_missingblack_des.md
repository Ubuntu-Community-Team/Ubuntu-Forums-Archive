---
title: "Lubuntu 14 install worked but now missing/black desktop"
date: 2014-08-31
forum: Installation &amp; Upgrades
---

### Post by 222fbj on 2014-08-31
I have an old AMD64 system that has been running Lubuntu 12 for a few years.  I tried to upgrade to 14 and now have a problem after this sequence of events:
[LIST=1]
[*]I installed deja dup backup (a simple backup front end) and backed up the only user's home folder.
[*]I tried using 'Upgrade to 14' button in the System Updates tool and it got as far as the 'configuring software' section where it hung while "preparing to configure libtelepathy-glib0".
[*]I used unetbootin to create a usb stick to boot and install Lubuntu14 which wiped the old install.
[*]The install options were chosen to create a user with autologin enabled; and then booted to the desktop successfully.
[*]I used apt to install Chromium and a few other packages including deja dup (so I could restore the user home folder).
[*]I ran deja dup restore which ran without errors and seemed to work fine.)
[*]The Updates Available window appeared and I installed the available updates (about 60mb).  I then used 'Restart Now' to finish the update process.
[*]The system rebooted **_now I get solid black desktop with only the cursor showing._**
[*]I can right click to bring up the menu and launch terminal.  I can launch pcmanfm from terminal.  At this point I have a solid black screen with only the terminal window and pcmanfm windows visible.  I used pcmanfm to browse user folders (desktop and a few others) and the restored items are there.
[*]I tried using the right click menu to open Openbox settings but nothing appears.
[*]I can also Logout which brings up the shutdown-logout menu. If I logout I get the login screen (with purple wavy wallpaper) and the login box.
[/LIST]

Any ideas how I might fix this 'mising desktop' problem?  I am hoping there are some commands I can run from the terminal window to provide more info on the problem and/or fix it.  Thanks!

---

### Post by ibjsb4 on 2014-08-31
Got one thought.

Your getting right click>menu.  Thats telling me your on a openbox session.  At the login screen, can you change it to lubuntu?

---

### Post by 222fbj on 2014-08-31
Thanks!!! The Login Screen 'Lubuntu Netbook' option worked.  From there I used Synaptic to install LXDE.  Now I login with LXDE and it looks as I expected/wanted. 

I don't understand why the Lubuntu image I used (lubuntu-14.04.1-desktop-amd64) would not install LXDE, or what happened to leave me with Openbox instead of LXDE.  If someone could explain this I'd be interested.

Thanks

---

