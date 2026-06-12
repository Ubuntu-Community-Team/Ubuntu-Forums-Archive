---
title: "Dual Boot Issues"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by MCAccord on 2008-02-17
Hey everyone, my computer just completely crashed, so I'm in the process of doing a reinstall. I run MythTV and I want to be able to run XP64 as well. I installed Ubuntu on my 500GB SATA HD, but I haven't been able to get to it because my BIOS always says "Error Loading the Operating System". I'm running an 160GB IDE HD underneath my DVD-RW for the XP64 and Windows Server. I think my BIOS gives priority to the IDE channel 1 (which is what my DVD-RW and 160GB HD are on) and second priority to the SATA. I'm installing Windows now, hoping I'll get a little farther, but once I do, I still don't have a way to get into Linux. Any thoughts?
Here's what my machine is:
PCChips A13G+
AMD 64 3500+
1GB Memory
160GB IDE HD (IDE 1)
500GB SATA HD (apparently IDE2, since the MB doesn't have a 2nd IDE channel)
DVD-RW (IDE 1)
Thanks for the help.

---

### Post by 0vermind on 2008-02-17
I used to have sooooo many problems with Dual Boot!

The drives shouldn't matter, please note that no matter how hard you try the motherboard will insist on putting IDE first. Appends with me all the time, you just need to tell Windows and Ubuntu to deal with it. 

Here is what you need to do, install Windows first! XP, Vista w/e install that first. The plan out where you are going to install ubuntu, for me this requires an extra step, my partition tables skip numbers from the order 0,1,4,5,6 skipping 2 and 3 for me. 
This might not be the case for you, but I had to grab Super Grub Disk from here: [http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download) and then boot to the ubuntu cd and partition how I want or windows), then I boot to that CD and find the hd I want to install on and note the location.

For example say I wanted to install ubuntu on the second hd 4th partition so I boot to that Super Grub Disk and go to start with help, and then tools ->show partitions-> find the hd, and then count the items the forth one down is what I wanted, so I wrote down what mine said, mine says "hd1, 7" (again yours will be different).

Then I install ubuntu, and at the very last page were it reviews your information click advanced setup for grub. It will say install on "hd0" erase that and put hd1 (this is my number you need to put here the number you wrote down from Super Gurb Disk). I can't remember if it has parentheses so if the default there says (hd0) make sure to leave those parentheses there (e.g. this is in parentheses). 

Then back in Windows, this is where it get's tricky I'm not sure about XP but for Vista to add Ubuntu to the bootloader you download EasyBCD and then go to the linux section and select the actuall partition you installed on.

Yes, this is a bit complicated. Hope it's not too much for you.

Hope this helps you!
-Mike

---

### Post by sodasound on 2008-02-17
Okay, different problem, while we're here. I started out on Debian a month ago, then added Ubuntu Multimedia. Now I want to kick Debian off to get the rest of my hard-drive back. Any suggestions? (other than starting over with a fresh install)...I'm a total newbie.:guitar:

---

### Post by oilchangeguy on 2008-02-17
> **sodasound said:**
> Okay, different problem, while we're here. I started out on Debian a month ago, then added Ubuntu Multimedia. Now I want to kick Debian off to get the rest of my hard-drive back. Any suggestions? (other than starting over with a fresh install)...I'm a total newbie.:guitar:

run the live cd, and use gparted to expand the ubuntu partition.

---

### Post by MCAccord on 2008-02-17
Okay, now I'm confused. I'm not sure you understand what's going on here? Or maybe it's just me... Anyways...

I currently have 2 HDs. One is a SATA, and will house my MythTV installation and nothing else. The other is a IDE, it will contain 2 partitions one for XP64 and the other for Server 2003. As of now, I apparently have both XP64 and Ubuntu installed, yet I can't boot into Ubuntu.

---

### Post by adrian15 on 2008-02-19
> **MCAccord said:**
> Okay, now I'm confused. I'm not sure you understand what's going on here? Or maybe it's just me... Anyways...

I currently have 2 HDs. One is a SATA, and will house my MythTV installation and nothing else. The other is a IDE, it will contain 2 partitions one for XP64 and the other for Server 2003. As of now, I apparently have both XP64 and Ubuntu installed, yet I can't boot into Ubuntu.

**Boot with Super Grub Disk -> Super Grub Disk (With Help) -> Linux -> Fix Boot of Linux**

If it works... I mean if when you boot you see the grub menu then you will probably have an error 21 in grub so you will need to boot with a ubuntu live cd, chroot into your ubuntu partition, edit menu.lst so that groot matches your settings(hd1,X) or (hd2,X) or whatever and then run update-grub. Exit from the chroot and reboot and it should be done.

Just try the Fix Boot of Linux and see if you see any change. If nothing happens you can still try with **Boot & Tools -> LiveSwap -> Easy LiveSwap and Boot with Super Grub Disk -> Super Grub Disk (With Help) -> Linux -> Fix Boot of Linux** again.

adrian15

---

