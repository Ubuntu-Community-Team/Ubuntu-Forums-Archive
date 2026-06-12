---
title: "Fresh install, keyboard and mouse do not work"
date: 2011-07-18
forum: Installation &amp; Upgrades
---

### Post by SoFl W on 2011-07-18
Xubuntu 11.4 dual boot on a secondary Dell Dimension 8400 machine that I have.
This machine had 10.4LTS on it with a dual boot configuration and worked fine.  I wanted to test out 11.4 Xubuntu so I installed using a USB drive.  During the installation everything seemed to work fine.  I could use the keyboard and mouse to answer all the installation questions.  During the installation I clicked on one of the information screens that describes various features of Ubuntu, the browser opened up and I was able to read about it.  (I think it was "get involved" but it isn't important)  The installed finished, I clicked on "restart"  I am able to make selections at the grub menu, however as soon as I get to Ubuntu login screen the keyboard stops functioning.  The caps/scroll/num lock keys do not light, the mouse is lighted but the mouse cursor does not move.

The mouse and keyboard are USB, not wireless.

Any ideas?

---

### Post by Toz on 2011-07-18
Some things to try:

1. If you unplug and replug the keyboard mouse, do they begin to work?

2. Are you going through some sort of USB hub? If so, try directly plugging them in.

3. Check your BIOS. Is there anything in there about enabling legacy usb support? Or anything similar usb configuration option that you could try?

---

### Post by SoFl W on 2011-07-19
1) No
2) No
3) Checked the BIOS, they work at the grub menu, and it worked on the previous Ubuntu install, just doesn't work now.

---

### Post by Quackers on 2011-07-19
Are you installing 11-04 or 11-10?
This has happened with 11-10 (development release) and the fix is to drop to a root shell and run a command, but that should not be necessary with 11-04 as it doesn't use the same versions of packages.

---

### Post by Toz on 2011-07-19
Try the **pci=nocrs** kernel boot parameter.

Edit Grub2 Entry Howto: [https://help.ubuntu.com/community/Grub2#Editing%20the%20GRUB%202%20Menu%20During%20Boot]("https://help.ubuntu.com/community/Grub2#Editing%20the%20GRUB%202%20Menu%20During%20Boot")

Reference Link: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/647043/]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/647043/")

---

### Post by SoFl W on 2011-07-19
Thank you.
I will have to read through that and try again, adding "pci=nocrs" to the bottom of the boot commands didn't work, but I was just rushing quickly and hoping for the best.  (I might have spelled it wrong)  I will try again after making sure I am doing everything correctly and it is in the correct place.

Thank you for pointing me to that.

---

### Post by SoFl W on 2011-07-21
No that didn't seem to work.  I should point out that it works if I boot from the USB stick.  I should check the boot log for errors.

---

### Post by Toz on 2011-07-21
Just did some more googling.

[http://ubuntuforums.org/showthread.php?t=581160]("http://ubuntuforums.org/showthread.php?t=581160") - suggests trying **acpi=force irqpoll** kernel parameters.

[http://timesinker.blogspot.com/2010/07/ubuntu-1004-usb-mouse-keyboard-problems.html]("http://timesinker.blogspot.com/2010/07/ubuntu-1004-usb-mouse-keyboard-problems.html") suggests **pci=noacpi**

[http://www.linuxquestions.org/questions/linux-newbie-8/usb-mouse-and-keyboard-not-working-after-ubuntu-8-10-upgrade-681284/]("http://www.linuxquestions.org/questions/linux-newbie-8/usb-mouse-and-keyboard-not-working-after-ubuntu-8-10-upgrade-681284/") - suggests a change/addition to /etc/X11/xorg.conf. This will be difficult if you can't type. 

Which leads me to....Can you try to select the Recovery option in grub and see if you can get a console prompt where the keyboard works? Lets see if its a kernel issue or an X issue.

---

### Post by SoFl W on 2011-09-27
I am sorry I never checked back on this thread.  I am marking this as solved, I installed Fedora on that machine, and will probably try something else.  It was a spare machine and I just don't have the time to mess with it.

Thank your for your help and replies, if I get the chance I will try it again.

---

