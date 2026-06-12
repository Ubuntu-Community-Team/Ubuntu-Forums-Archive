---
title: "problems with upgrade kubuntu 12.04 to 14.04"
date: 2014-09-04
forum: Installation &amp; Upgrades
---

### Post by r.stiltskin on 2014-09-04
Login problem is solved.  Just posting here to document in case it is useful to anyone (and to see if anyone has any info about the kdm.log error messages).

Upgrade from Kubuntu 12.04 to 14.04 on my HP Pavilion dm4t-3000 (core i7-2640m with Intel Graphics 3000) seemed to complete successfully but after rebooting it briefly displayed a Kubuntu splash and then the screen went blank -- no login window and no real clues about what was wrong.  Editing the grub command line (eliminating quiet splash) to display boot messages didn't help.  Booting in recovery mode didn't help.  I was able to ctrl-alt-f2 to a command line login.  I checked a few logs -- dmesg, Xorg.0.log -- but didn't see anything there that was helpful.  I did notice that there were two display manager logs -- lightdm/lightdm.log and kdm.log -- and wondered about that.  I don't know why both are installed.  In the kdm.log i found:
klauncher(1268) kdemain: No DBUS session-bus found.  Check if you have started the DBUS server.
and
kdeinit4: Communication error with launcher.  Exiting!

I took a few stabs in the dark (not knowing if this would help or make matters worse)
sudo apt-get remove lightdm
sudo apt-get purge Xorg
sudo apt-get remove xserver-xorg
sudo apt-get install kubuntu-desktop
but these steps didn't seem to change anything.

Finally I tried
sudo dpkg-reconfigure kdm
and this quickly brought up a dialog saying that there were two display managers installed (lightdm and kdm) and asked me to choose which would be primary.  I chose kdm, and after the reconfigure process completed I rebooted and this time got a normal kdm login prompt and a normal kubuntu session.

There was a notification that "Language support is incomplete, additional packages are required", but didn't give any more details (which packages?)  Then I noticed an icon in the system tray area with a mouseover message about "Authentication is required" and something about polkid.subject.pid and polkit.caller-pid.  Not very informative but I took a chance and entered my password and a few packages were automatically installed: gimp-help-common:amd64, thunderbird-locale-en:amd64, language-pack-gnome-en:amd64, gimp-help-en:amd64, poppler-data:amd64, language-pack-gnome-en-base:amd64 and one removed: gs-cjk-resource:amd64
After this the "Language support incomplete" message went away and everything seems to be working normally.

Every time I boot the kdm.log still contains those messages:
klauncher(1266) kdemain: No DBUS session-bus found.  Check if you have started the DBUS server.
and
kdeinit4: Communication error with launcher.  Exiting!
but as I said, everything that I have used so far seems to be working, so I don't know what those messages are about.

---

