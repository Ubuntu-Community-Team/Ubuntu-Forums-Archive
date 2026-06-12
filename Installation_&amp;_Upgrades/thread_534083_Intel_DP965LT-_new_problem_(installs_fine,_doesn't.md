---
title: "Intel DP965LT- new problem (installs fine, doesn't boot)"
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by lackhead on 2007-08-24
Hey all-

    So, I am yet another frustrated admin trying to get Ubuntu, or any Linux for that matter, to install on my box using an Intel DP965LT motherboard.  I've seen the other problems that this board has had, both on the net and in this forum, but I haven't had anybody mention the same problem I am having.  First, the specs:

Intel Dp965LT motherboard (BIOS version MQ96510J.86A.1699, also tried 1689)
Intel Core 2 Duo E6700
4x2G Kingston PC2-5300
Seagate Barracuda SATA drive
Asus GeForce 7300GS
Sony DVD-ROM

   So far I am not having the cd-rom issues that others have mentioned.  In fact,  the install goes swimmingly (desktop, server and alternate).  But, when the machine reboots, it comes up and when you would expect to see the grub menu (or the grub countdown) all I get is a black screen and blinking cursor.  The machine isn't dead- it responds to Cntl-Alt-Del, but it never gets any further.  What's weirder is that if I boot off the install CD, I can select "Install from first hard drive" and it does kick up grub, starts the boot, and will eventually come all the way up although it does take a long time, spits out this message and an error:

.
.
kinit: name_to_dev_t(/dev/sda2) = sda2(8,2)
kinit: trying to resume from /dev/sda2
kinit: No resume image, doing normal boot
.
.
e1000: eth0: e1000_request_irq: Unable to allocate MSI interrupt Error: -22
.
.


Also, when booting this way the system is slow, and I can't write to the disk even though everything is mounted RW. 

   Bwah? 

   Memtest checks out. I have 5 identical machines and all of them have the same behavior (odds of hardware problems low, but not totally out of the picture). I have tried other SATA controllers in a PCI slot, same problem. I've tried different disks...same problem.  Played with the BIOS settings for the disks, nothing helps. I've tried unplugging the DVD-rom after installation (before rebooting) and I get a "No bootable device found" error. 

   Oh, and windows installs/boots just fine. Great. 

   So, I'm left thinking that something weird is going on in the BIOS, perhaps an interrupt problem?  But uh, I'm not sure where to turn at this point. If anybody else has any pointers or suggestions (or a solution!) I'd be very happy for some insight. 


Thanks!!!


-c

---

### Post by lackhead on 2007-08-29
Any thought that this might be some weird interrupt problem? That's just a stab in the dark. Given that Windows works and Linux doesn't seem to, I doubt it is a hardware issue. 



-c

---

### Post by Nzer24 on 2007-09-06
Did you try reinstalling grub manually?

I had a problem with booting where grub didn't appear and that fixed it.

Heres how you can do it if you so choose:

- Use the live CD to get to a terminal
- Make sure the partition w/ Ubuntu is mounted
- Type the following:
sudo grub
find /boot/grub/stage1
root (hd_,_)                     (insert the result of the "find" command)
setup (hd0)
quit

This will write a new version of grub to your MBR and allow the primary bootloader to start.

P.S. I only got the grub to work on my computer after booting from the install disk... If I figure out the rest of th problem I'll tell you.

---

