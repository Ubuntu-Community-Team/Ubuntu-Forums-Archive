---
title: "New hard drive, Grub not working Error 17"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by boxybrown on 2007-05-26
Here is my system before  I did anything:

250GB IDE on the Primary IDE channel as slave: 3 Partitions of NTFS with one being a bootable Windows XP partition
320GB SATA: Bootable Feisty Partition, Swap Partition and Large NTFS partition for storage.

Grub worked fine here and would boot both Windows and Ubuntu.

Now I got a 250gb HD for free to install so I plugged it into the Secondary IDE channel as Master.  

After restarting.  Grub gives error 17 when trying to boot anything from Ubuntu and error 13 when trying to boot XP.  

I ran the Ubuntu live CD and restored GRUB in the MBR, but that did nothing.  Then I realized that by adding the third hard drive, it moved the MBR from hd1 to hd2 (my motherboard places all IDE drives in order before any SATA drives) so I changed the grub config file to hd2 as the location of Ubuntu.  But I'm still thrown the same errors.  I'm fairly certain that if I reinstall Feisty, everything would be fine, but I would rather not do that.

Does anyone have a suggestion or know a solution to this?

Thanks

---

### Post by boxybrown on 2007-05-26
After still searching forums and google for hours, no solution.  So I became impatient and I backed up everything that was important and reinstalled Ubuntu.  Same setup as before now but with a newly installed Grub.  Problem is that I still cannot boot into anything!  Grub throws me error 15 now when I try to boot!  And still error 13 with Windows.  Does anyone know a possible solution?

---

### Post by aqualad on 2007-05-26
This is a half question/half thought, but I was under the impression that you can only have one bootable drive in the computer.  Though, I would understand if you could use 2 given that one is SATA and one is IDE

Have you considered this or did you know that this would work beforehand?  Just trying to stir up some thought..

---

### Post by confused57 on 2007-05-26
If you have access to another pc, you might want to burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

For the time being, if you want to get Windows booting:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

You could mount your linux partition, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

you could then check the output of your /boot/grub/menu.lst & /boot/grub/device.map files.

---

### Post by boxybrown on 2007-05-27
> **aqualad said:**
> This is a half question/half thought, but I was under the impression that you can only have one bootable drive in the computer.  Though, I would understand if you could use 2 given that one is SATA and one is IDE

Have you considered this or did you know that this would work beforehand?  Just trying to stir up some thought..

Hmm that would make some sense.  I might change some partitions around to put them all one one drive.  I had two bootable drives beforehand when I had one SATA and one IDE.  But with the two IDEs and the Sata, the double drive may be confusing GRUB I guess.

Oh and I have been using a live CD, I have the ultimate Boot CD which has Super Grub CD on it.  I can use it to boot into windows, but I can't get into my Ubuntu no matter how hard I try.  Since I have already deletede my Ubuntu.  I have nothing to lose I guess.  I'll see how this goes.

---

