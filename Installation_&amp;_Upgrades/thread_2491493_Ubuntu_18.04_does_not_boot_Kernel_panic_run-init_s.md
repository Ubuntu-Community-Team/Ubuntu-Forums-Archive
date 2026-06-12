---
title: "Ubuntu 18.04 does not boot Kernel panic run-init: /sbin/init: no such file or direc"
date: 2023-10-11
forum: Installation &amp; Upgrades
---

### Post by kristine55 on 2023-10-11
I have UBUNTU 18.04
While my grandson was playing on the internet the system frooze. I had to do turn off the laptop (Dell Inspiron 7720)
Since then my system does not boot. I have following message: Kernel panic - not syncing: Attempted to kill init! exitcode=0x00000100

I can boot my system with an USB, but I don't know what to do from there. I've looked on the forums and found some indications, but since I am a beginner I don't manage to get it fixed. 

I did this

[LIST]
[*]boot to a Ubuntu Live DVD/USB
[*]open a terminal window by pressing Ctrl+Alt+T
[*]type sudo fdisk -l
[*]identify the /dev/sdXX device name for your "Linux Filesystem"
[*]type sudo fsck -f /dev/sdXX, replacing sdXX with the number you found earlier
[*]repeat the fsck command if there were errors
[*]type reboot
[/LIST]
 It does not help, my system does not boot
I have tried to do boot repair... It created a  boot-info file on this site [http://paste.ubuntu.com/p/4WWydzvN9w/](http://paste.ubuntu.com/p/4WWydzvN9w/) maybe this can help?

I would absolutely prefer not to reinstall the complete system. 

Is there anyone who can help me please? Please be aware that I need complete explanations since I am not an UBUNTU specialist, I am just using it...So I need step-by-step instructions. 

Thank you
kristine

[https://www.dropbox.com/scl/fi/kc8cm98l2rgdxoopqw71c/2023-10-10-17.06.32.jpg?rlkey=dn72agnzq5hdx7w079z5o0hz2&dl=0](https://www.dropbox.com/scl/fi/kc8cm98l2rgdxoopqw71c/2023-10-10-17.06.32.jpg?rlkey=dn72agnzq5hdx7w079z5o0hz2&dl=0)



[LIST]
[/LIST]

---

### Post by TheFu on 2023-10-11
Do you have ESM support?  If not, you should know that support for 18.04 ended last April.  

It would have been easier to upgrade before support ended. Now, doing a fresh install is the easy solution. Just be certain to backup anything you don't want to lose before doing a fresh install.

---

### Post by yancek on 2023-10-11
Boot the Dell and access the BIOS firmware and move Ubuntu up to first in the boot priority boot options.  Line 68 of boot repair shows it is Boot000C*  I don't see any other obvious problems that would prevent booting.  Manually forcing power off is always a bad idea and may be the source of the problem.  An alternative method with a frozen system is to simultaneously hold down the left Alt key and the prt sc key in the upper right of the keyboard.  While doing this, type the following letters consecutively (r e i s u b)and when you have finished thecomputer should reboot. 

Are you using an Ubuntu 18.04 USB?  or some other system/release?  Can you mount and access the installed system when booted into the live usb? 
When you ran the filesystem check (fsck), did you get any output such as warning or error messages?  If so, what were they?

---

### Post by MAFoElffen on 2023-10-11
What I suspect... It was shutdown (forced) while the filesystem was open. Then on next boot had a problem finding a file... Even in 18.04 LTS, "/sbin/init" is actually a symlink file that points to directory "/lib/systemd/systemd/"... 

Forcing a shutdown on a computer sometimes causes file corruption or a file may be locked in an open state. The way to correct that is to run a utility called "fsck", which stands for "filesystem checker", which checks the filesystem and can repair it. That would be the very first thing I would do, since that is the most likely culprit. 

The easiest way to do that, is to boot straight to the installed Grub2 menu, and choose "Advanced Options" > Choose a menu option the includes "Rescue Mode" > At the Rescue menu select "fsck"... That will run and repair all the filesystems that are mounted in you fstab file. That is a file that the boot process uses to assemble and check track of where all the pieces are that need to be put together as one.

The Grub2 menu and the Rescue menu should still work, as they are in another part of the filesystem (hopefully).

If not, then post back here, and I will guide you to be able to run that utility from an Installer LiveUSB, which you mentioned you have and your system boots from.

As a sidenote: After we get you back up and running, then we can guide you to be able to get you on a currently supported LTS release.

---

