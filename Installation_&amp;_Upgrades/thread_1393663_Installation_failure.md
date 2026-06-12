---
title: "Installation failure"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by maxiz on 2010-01-29
Hi,
 
I've been trying to install Ubuntu 9.10 on my laptop which already has win xp on one partition. I used wubi to download and install ubuntu. The installation goes fine and when it's completed asks me to reboot the system. 
 
The problem comes when I select the ubuntu from the OS options. 
The screen shows the following output and stays on it indefinitely.
 
output:
[Linux - bzImage, setup = 0x3400, size = 0x3b26e0]
[Initrd, addr = 0x37a72000,  size = 0x57d098]
 
The installation was done on a partition of 26 GB with 15 GB allocated for ubuntu. 
 
System Specs:
Acer TravelMate 4010
1.25 GB RAM
 
Ubuntu 8.04 used to work on this laptop before, but now even that is not working.
I had completely formatted my harddrive after a system failure. All the troubles mentioned above started showing up when I tried to install ubuntu after the harddrive format. Win XP works fine.
 
It would be a great help if someone could tell me what's going wrong with my ubuntu installation.

---

### Post by quixote on 2010-01-31
I suspect the problem is not with the installation as such but with the bootloader which is what points the computer to the ubuntu installation when the machine starts up.  If the bootloader blew up, then that would explain why you can't see your other ubuntu (8.04) install either.  

A bootloader wouldn't survive a re-format.  If you re-installed Windows first (which is the order you're supposed to do it in), then it would put it's own bootloader there and ignore all other systems.  (It's Windows.  What can I say? ;))

So, quite possibly, all you need to do is reinstall your grub bootloader, which sees ubuntu and windows.  Unfortunately, I don't know anything about the wubi method of installing, so I'm not sure how that changes what you tell grub.

To install old grub (Karmic uses grub2, but you can also point to it with old grub, which I'm more familiar with) follow the detailed instructions at "[Recovering ubuntu after installing windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")."  It looks involved and tedious, but, really!, if you just carefully follow those instructions everything is fixed.

They also have a section on doing it via Grub2, which looks dead easy, actually.

As I say, I don't how any of this changes with a wubi install.  Maybe somebody else can jump in and tell us.

---

### Post by maxiz on 2010-01-31
Thanks a lot for that reply... though the steps look a lot to do, i'll give it a try...
let's see whether it works or not :)

---

