---
title: "Ubuntu 20.04 stopped booting - advice on how to fix"
date: 2021-05-03
forum: Installation &amp; Upgrades
---

### Post by carusoswi on 2021-05-03
I run a dual boot with Windows 10.  With various Ubuntu versions over the years, I have never encountered a boot issue.  I had been working in Win10, but when I tried to boot back into Ubuntu, Grub appeared and allowed me to select the OS, but the boot failed.  Advice was that I needed to run fsck (sp?).  From the screen presented, I cannot get into a terminal to run it (and would likely not be in the correct directory to have that command available.

I have done some online reading and see repeated suggestions with commands that I can run from TTY1, but have not found a way to execute the required command (instructions say from log on screen, but ctrl-F1 doesn't respond for me there).

I have created a bootable Ubuntu ISO USB thumb drive, so no problem loading a version of Ubuntu from it.

I know I can reinstall from the thumb drive, but would rather try repairing my existing installation, if possible.  I cannot imagine what caused this problem, as I have not made any system changes in my setup.

If there is information that I have omitted, please advise and I will try to get it for you.

Thanks in advance for any assistance.

Caruso

---

### Post by yancek on 2021-05-03
>  but the boot failed.  Advice was that I needed to run fsck (sp?).  

What does 'boot failed' mean.  Exactly what happens?  Blinking cursor, black screen, warning/error message.  Where do you see the message to run fsck?  Is it on screen when you try to boot?  If so, run it from there.

---

### Post by ajgreeny on 2021-05-03
From the live USB booted into Ubuntu run terminal command ```
sudo fdisk -l
``` to find the partition listing of your hard disk.

From this it should be possible to figure out which is the root partition of your installed Ubuntu system and once you know that to be, for example, /dev/sda2, run terminal command ```
sudo e2fsck /dev/sda2
``` and that may find filesystem problems and offer to fix them.

It's a very long time since I saw this problem but the solution I mentioned fixed it quickly and easily.

---

### Post by grahammechanical on 2021-05-03
For information purposes.

At the Grub menu select Advanced Options for Ubuntu. Then select a Linux kernel that has recovery mode. The recovery menu has an option to get to a root shell prompt. We can run commands from there. If we want to run a command that installs a package from the internet then we first have to select Network from the recovery menu to set up the internet connection. Typing exit in the root shell prompt will bring us back to the recovery menu.

Regards.

---

### Post by carusoswi on 2021-05-04
> **yancek said:**
> What does 'boot failed' mean.  Exactly what happens?  Blinking cursor, black screen, warning/error message.  Where do you see the message to run fsck?  Is it on screen when you try to boot?  If so, run it from there.

Thanks for your reply.

I had previously experienced extremely slow boot times for Ubuntu, and, following advice given on this forum, had run commands that show me line by line progress of my Ubuntu boot progress.  For whatever reason, that, without further action on my part, cleared up my slow boot times.

Due to that setup, I am left with whatever part of the boot process still shows on my screen after failure.  I am unable (or don't know how) to capture all of that output, but typed what was showing after boot failure and typed it manually to a gmail message which I sent to myself so that I could copy/paste it here.  Here is that partial output:

[   4.661718] random: 7 urandom warning(s) missed due to ratelimiting /dev/sdb1:
Inode 141994 extent tree (at level 1) could be shorter. IGNORED.
/dev/sdb1: Inode 149884 extent tree (at level 1) could be shorter. IGNORED.
/dev/sdb1:
Inode 155682 extent tree (at Level 1) coud be shorter. IGNORED.
/dev/sdb1:
Inodes that were part of a corrupted orphan linked list found.

/dev/sdb1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e., without -a or -p options)
fsck exited with status code 4
done.
Failure: File system check of the root filesystem failed
The root filesystem on /dev/sdb1 requires a manual fsck

BusyBox v1.30l.1 (Ubuntu 1:1.30.1-4ubuntu6.3) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [   386.527198] logitech-hidpp-device 003:046D:405B.005: HID++ 4.5
device connected.
{   402.631021} Logitech-hidpp-device 0003:046D:406B.0006: HID++ 4.5 device connected.

(at this point, I am left with a blinking cursor (_).  If I press enter, I get:
(initramfs)
Hitting enter again will return the same initramfs message.

Again, this is that portion of the output of my boot progress that remains (has not scrolled off of) my screen following failure.  Note that previous to this boot failure problem, I would observe my boot progress as it scrolled by (too fast to really read what was going on), and, after it completed, the screen would go blank briefly, then the Ubuntu desktop would appear.  I don't remember exactly when it was that I ran the commands to display this line by line boot progress, but I imagine it has been at least a couple of years, so that is not part of the problem.

I hope this sufficiently answers your question.

Again, thanks for the reply and any advice you can offer.

Caruso

---

### Post by carusoswi on 2021-05-04
> **ajgreeny said:**
> From the live USB booted into Ubuntu run terminal command ```
sudo fdisk -l
``` to find the partition listing of your hard disk.

From this it should be possible to figure out which is the root partition of your installed Ubuntu system and once you know that to be, for example, /dev/sda2, run terminal command ```
sudo e2fsck /dev/sda2
``` and that may find filesystem problems and offer to fix them.

It's a very long time since I saw this problem but the solution I mentioned fixed it quickly and easily.

Thanks for the reply.  I know that Ubuntu is installed on /dev/sdb1.  Will try running the command there and see how it goes.

Caruso

---

### Post by carusoswi on 2021-05-04
> **grahammechanical said:**
> For information purposes.

At the Grub menu select Advanced Options for Ubuntu. Then select a Linux kernel that has recovery mode. The recovery menu has an option to get to a root shell prompt. We can run commands from there. If we want to run a command that installs a package from the internet then we first have to select Network from the recovery menu to set up the internet connection. Typing exit in the root shell prompt will bring us back to the recovery menu.

Regards.

I tried this, but, perhaps did not type the command correctly.  Will try ajgreeny's code and see how it goes.  Thanks for the reply.

Caruso

---

### Post by carusoswi on 2021-05-04
All:
Ajgreeny's solution worked a treat.  The command ran through that output I posted in reply to yancek, and offered to fix the problem with each of the imode extent trees that were ignored (all I needed to do was answer 'y' to each offer) and several other errors that fsck found, and now my system is accessible.  I cannot tell you how pleased I am to have my system back without having to reinstall over it.

If that output I posted to yancek gives any clue as to what caused this issue, I'd be glad to know of it.  I spend most all of my time in Ubuntu, but have a couple of applications that only run in Windows, and will not run in Wine.

Grahammechanical:  I tried dropping to a command line from Advanced Options (I hit 'C', maybe that's wrong).  I wound up at a Grub> prompt.  I'll have to try that again and look to see if there is an option that I overlooked.

Once again, I want to thank all three of you for your willingness to offer assistance.

Caruso

---

### Post by ajgreeny on 2021-05-04
There are several things that can cause the filesystem corruption problems that lead to the busybox problem you saw, most often it's probably the result of an unclean shutdown of some sort, or if you have mounted a partition an not unmounted it properly before removing it, unlikely in your case with an internal disk.

It can also be the result of imminent hardware failure starting to show so it may be worth using gnome-disks, just called ***Disks*** in your menu to check the disk with the **Smart** tools it includes by highlighting the partition, clicking on the three dots icon and choosing **Smart data & Self tests** to see if that finds anything.

---

### Post by carusoswi on 2021-05-04
> **ajgreeny said:**
> There are several things that can cause the filesystem corruption problems that lead to the busybox problem you saw, most often it's probably the result of an unclean shutdown of some sort, or if you have mounted a partition an not unmounted it properly before removing it, unlikely in your case with an internal disk.

It can also be the result of imminent hardware failure starting to show so it may be worth using gnome-disks, just called ***Disks*** in your menu to check the disk with the **Smart** tools it includes by highlighting the partition, clicking on the three dots icon and choosing **Smart data & Self tests** to see if that finds anything.

Thanks for the additional information.  I might be guilty of pulling a USB stick without first ejecting, but that isn't normal for me.  I do have a 4TB external drive which I use both in Ubuntu and in Windows, but I never disconnect it in either OS without ejecting it (in Ubuntu) or 'safely removing it' in Windows.  Of shutting down uncleanly I could be guilty, but mostly in Windows when it decides to take forever to shut down (I really don't like Windows).

Thanks to you, I have the solution to this problem if it should ever reoccur.

Thanks so much for your help.

Caruso

---

