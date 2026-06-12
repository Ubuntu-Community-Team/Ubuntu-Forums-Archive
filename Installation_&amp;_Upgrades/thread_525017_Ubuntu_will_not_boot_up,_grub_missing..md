---
title: "Ubuntu will not boot up, grub missing."
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by Phalax on 2007-08-13
I guess you can say I am one of the most destructive people out there :), but hey how else do we learn? Anyways here is another story...I just got done reformatting my whole entire system for nice fresh installs of both Windows XP and Ubuntu 7.04 32-bit. I installed Windows XP beautifully, so I went on and got my copy of partition magic created a new partition for a different OS, formatted it as a EXT3, 80GB. Then made a Swap partition before the Linux one and after the windows one and made that 2047.3mb. Put my copy of Ubuntu into the DvD drive restarted the system and installed Ubuntu perfect! did the "sudo apt-get update, sudo apt-get upgrade, sudo apt-get distro-upgrade" just to make sure everything went ok. Installed Beryl, Wii black theme with the DroplineNEU Icons, updated my nvidia drivers with envy. As I slept peacefully at night I downloaded Flash Player since it downloads at 1.2kb sec off their site! Woke up ran the install and it went all well. I then rebooted my system to fix up my XP a little bit and there it happened Error could not boot.....blah blah x000 bunch of numbers basically "Blue Screen Of Death". Did everything I could think of for 3 hours. So the only thing I could do is reformat my C: partition and reinstall Windows XP, but stupid me forgot all about the boot or I think its called the Grub "The window where you choose between Ubuntu and Windows to boot into" After I installed Windows it would not let me boot up into Ubuntu in fact just boots straight to windows. I have partition magic, the Ubuntu 7.04 DvD with System -> Partition Tool. I was wondering without reinstalling Ubuntu is there anyway to fix this so I can choose to boot up into Ubuntu again?

I wish my Windows XP and Ubuntu will become friends till I get out of college and stop fighting with each other :) Imagine this happening during the middle of a very important essay lol ouch :)

Sorry for the long boring story lol.

Thank you guys!

---

### Post by merlinus on 2007-08-13
Boot from ubuntu live cd, get to a terminal and enter, one at a time:

```

sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx)
quit

```

Substitute results from find for (hdx,x).  It will probably be (hd0,1).

-merlin

---

