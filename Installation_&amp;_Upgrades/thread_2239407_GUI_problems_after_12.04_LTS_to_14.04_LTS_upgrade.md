---
title: "GUI problems after 12.04 LTS to 14.04 LTS upgrade"
date: 2014-08-13
forum: Installation &amp; Upgrades
---

### Post by beamvr62 on 2014-08-13
I did the update from 12.04 LTS to 14.04 LTS using Update manager and can't get the GUI properly started. There weren't any issues during the update itself but after the reboot I did not get any further than a blinking prompt after the character based 14.04 welcome screen. In grub this is the 3.13.0-33 option. The same option in recovery mode and then starting graphics in safe mode gives the same results.

One of the other grub options is 3.0.0-19. With this option I get a low-res graphical login screen with the familiar bar with the clock etc. at the top but after successfully logging in the bar disappears and I get a an empty background and nothing like menubars at the side.

I Downloaded the 14.04 LTS Live / Install DVD and it runs fine, picking the right settings for screen resolution etc.

What can I do to get my updated 14.04 LTS running? I've tried to remove nvidia using sudo apt-get remove --purge nvidia* but got the reply access to a file was denied.

My HW is a 3 year old i5 with Nvidia graphics.

Help to get this resolved is much appreciated.

---

### Post by plucky on 2014-08-13
> I did the update from 12.04 LTS to 14.04 LTS using Update manager and can't get the GUI properly started. 

Is this the HW support Update or the Distribution-Upgrade to 14.04.1?

> I've tried to remove nvidia using sudo apt-get remove --purge nvidia* but got the reply access to a file was denied.


That is probably because the hard drive wasn't mounted.

1) Boot to recovery mode.
2) Enable Network. (this will mount the hard drive)
3) Go to root shell.
4) Remove the nvidia* driver.
5) Reboot

See if 12.04 now starts with the nouveau driver.
Select 2D mode and login.

> What can I do to get my updated 14.04 LTS running?

If the above works you are on 12.04.5 and you will have to run the upgrade again.

Good Luck

---

### Post by beamvr62 on 2014-08-13
Thnx plucky, this was great help to get it running again. :-)

Some remarks:
- With the [COLOR=#000000]3.13.0-33 recovery option I could not both mount the disk and go to root shell
- So I used the [/COLOR][COLOR=#000000]3.0.0-19 recovery option and followed your steps. Got to the root shell by Ctrl-Alt-F1 once I was asked to log in btw
- After reboot the straight 3.0.0-19 and logged in into a 14.04 LTS

Many thanks for helping out![/COLOR]

---

