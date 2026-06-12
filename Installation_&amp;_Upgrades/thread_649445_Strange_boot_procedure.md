---
title: "Strange boot procedure"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by etech1 on 2007-12-24
Hello all,

Awhile ago (July) I installed Fiesty to a WinXP system with two sata drives and one sata raid 0 array. The first drive contains XP's C: along with a data partition (D:) and a 2GB Ubuntu swap partition
The second drive has one XP data partition and a hidden to XP partition created by Acronis true image to store backup disk images. I manually created a 12 GB ext3 partition on some unformated space on this drive for Ubuntu. Installation went well but on rebooting there's no Grub boot menu, it just boots  into Windows as always.
After much forum searching and expermenting I found I could use my motherboards bios boot manager and select the second sata drive to boot from. Now a command line style Grub 1.5 loads and gives a few different options to boot but none of them work, it say drive not found or something. What does work is entering "e" on the first option, then it list " (root hd3,3). Hitting "e" again alows me to modify the line to "(hd0,3). Hitting "b" allows Ubuntu to boot and everything's fine.

Due to inpart the booting hassle, not being able to see the raid array and certain video driver difficulties I diding use the OS much but then I heard about 7.10 and deceided to give it another go.
I used the manual disk prep option putting the OS on the same ext3 partition hoping this time I would get the graphical pre boot Grub but it's no go:(   I still have to use the Grub edit command.
The good news is most of the problems I was having with 7.04 are fixable with 7.10.

While I don't mind choosing the boot drive in the bios, is there any way to make root (hd0,3) be the default boot option or an option I can select as editing the line for every boot is no fun.

Thanks for any help with this!

---

### Post by logos34 on 2007-12-25
This should answer any question you have about grub:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

All you have to do is edit menu.lst after you bootinto ubuntu:

gksudo gedit /boot/grub/menu.lst

change 'groot' and root lines to (hd0,3).  

You can also modify the windows entry to allow you to boot it from grub (save you having to change the bios order back and forth). You will need to add '[map' lines ]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")and possibly edit /boot/grub/device.map to correspond to the new drive boot order.

---

### Post by etech1 on 2007-12-25
Thank you for the info - modifying the menu.1st did the trick although there were no "groot" entries.

My DFI motherboard allows accessing the boot order by pressing esc after the system POST. It defaults to the first drive (Windows) when not used. It's handy for booting from a CD/DVD/HDD without changing the boot order.
Grub actually list Windows/Longhorn and selecting it will boot Windows from Grub. I think theboot  problem originaly started when I removed a dual boot XP/Vista RC1 installation and replaced Vista with Fiesty. One day I'll nuke everything and start over, I'm sure Ubuntu will boot properly after that.

---

### Post by logos34 on 2007-12-25
> **etech1 said:**
> Thank you for the info - modifying the menu.1st did the trick although there were no "groot" entries.

You're welcome!  Actually groot line is (should be) on line #74.  That needs to be correct for the next kernel update (update-grub).

---

