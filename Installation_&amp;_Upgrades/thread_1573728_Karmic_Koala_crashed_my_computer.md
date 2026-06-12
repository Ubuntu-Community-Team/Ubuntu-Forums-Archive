---
title: "Karmic Koala crashed my computer"
date: 2010-09-13
forum: Installation &amp; Upgrades
---

### Post by Fazl on 2010-09-13
HI everyone, I need some help!

I just upgraded from Jaunty to Karmic, but once I loaded Karmic and rebooted, my computer will not complete the boot up sequence and go into any desktop. It starts the initial boot sequence with the mouse appearing and then goes to the screen that looks like it has an atom cloud. After that, the screen goes black and the mouse-arrow turns into that white rotating wheel, but it stays that way. It never actually goes into any type of operation! I tried to go from the command line and find Lucid to overlay it on Karmic and hopefully solve the problem. It just looks like to me that several of the packages I downloaded through my upgrade manager were corrupted. My computer doesn't even seem to be acknowledging my password because it gives me an error 32:must be authenticated. Can someone help?!

---

### Post by Fazl on 2010-09-13
I also wanted to mention that I have a message that comes on the command line. It says 

HOST CONTROLLER PROCESS ERROR, SOMETHING BAD HAPPENED

HOST CONTROLLER HALTED: VERY BAD

HC DIED; CLEANING UP

I think these errors contribute to the problem if not being the problem in itself. Thanks for any help anyone can offer!

---

### Post by mörgæs on 2010-09-13
My guess is that the title should be 'upgrade crashed my computer'. 

If you can boot a live 9.10 or 10.04 with good results, the best solution is probably to reinstall while having wired internet connection.

---

### Post by Fazl on 2010-09-13
Thats the thing. I don't have a live CD. I just downloaded the upgrade through the update manager. Now, the best I can do is get to the commandline and I don't know how to download from there. When I used the apt-get command, it says it already has the latest version. Is there a way I can re-install the Karmic with what I already have? Or maybe fix the host controller? Also, when I try to boot from the command line (with the option of network connection), I still get the controller error and it never lets me actually issue any commands.

---

### Post by garvinrick4 on 2010-09-13
A live Cd is an install CD from Ubuntu, do you have any computer to download a file with and just BURN it to a CD. Any burning program as slow as it lets you. And then you can just reinstall. 
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by Fazl on 2010-09-13
Well thats kind of the main problem I have. I have one laptop which has a CD drive and that is the one I am having a problem with. My other laptop is a netbook which has no cd drive. Unfortunately I have no CDs either and my linux laptop's USBs have also fried apparently because I keep getting tons of over-current messages on. The over-current blocks me from entering any commands at the command line prompt because it keeps pumping out thousands of overcurrent messages which I have no idea of stopping. The only interface I seem to be able to communicate with the computer through is the Grub command line. If I had a live cd, it would have made my life a lot easier, but unfortunately, it was my dumb mistake not to make one before I did the upgrade. My only other back up CD is a few thousand miles away! I have an internet connex which seems to be the only way I can get the distro. Is there any way I can do that from the Grub command line?

---

### Post by mörgæs on 2010-09-13
The GRUB command line can not be used in this context.

On most machines it is also possible to install the Ubuntu ISO on a USB stick and boot from that, if the settings in BIOS are correct.

---

### Post by Fazl on 2010-09-13
Right now I am trying to figure out how to access my USB flash drives from the command line in Karmic. I managed to get to a functioning command line (I don't know how) but I can't seem to get to my USB drives. My computer's integral USB ports are fried, so I am using a PCI card with USB 2.0 port converters on them. When is use the LSUSB command, it recognized them, but I don't know how to get into the actual flash drive. Can anyone help?

---

