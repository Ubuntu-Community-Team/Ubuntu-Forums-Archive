---
title: "Dual-boot question"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by bickelk on 2010-05-02
I'm am fairly new to Linux, although I have used PCLinuxOS for a while. I want to install the new Ubuntu that was just release but need some help to do it the way I would like.
 
I have two hard drives one with Windows 7 and one that currently has PCLinuxOS. I want to whipe the PCLinuxOS one and put Ubuntu one it but I don't want Ubuntu's boot loader to have the Windows drive in it. I want to pick which one to boot by using my BIOS's boot selector. How can I set this up. I don't want the Linux drive to boot or modify anything on the Windows drive. That way if I decided to change stuff in the future it would be easy and neither of the drive would depend on the other to boot.

---

### Post by AzT3K on 2010-05-03
As long as the OSs are on seperate hard disks they shouldn't interfere with each other.

If they are on the same hard disk ie in dfferent partitions, when u install ubuntu it will overwrite the master boot record of the drive and u will be using ubuntu's boot loader.

You can install grub to the same partition as ubuntu rather than to the master boot record, but you need to read the guide installing grub for that:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by bickelk on 2010-05-03
But as long as they are two separt hard drives, the boot partitions of each are function separte of each other. Corrent?
 
Also, is there a way to keep the windows drive from mounting in Ubuntu and also the other way around as well?

---

### Post by Bucky Ball on 2010-05-03
Generally the install identifies there is a Windows partition and asks if you would like to include it in the grub menu. Say no. You can also tell the installer which partition to put the grub on so just don't put it on the Windows one. 

Sounds laborious changing drives in the BIOS. The windows bootloader will NEVER include a Linux entry and if you reinstall windows it is simply a matter of reinstalling grub or, if on another partition to Windows, telling grub which partition Windows is on (may work without needing to).

Right click windows drive and 'unmount', BTW.

---

### Post by bickelk on 2010-05-03
It's not very hard to select which to boot that way. I just choose a setting it the BIOS so that it always asks which disk to boot from. From then on every time I start the computer it asks just like the grub menu would. No sure if all motherboard can do that but I have always liked that feature on mine.
 
I get the boot partiton thing now, and will do that but my second post was refering to making sure that the Windows drive would not mount in Ubuntu after Ubuntu started. I don't want it accesible from within Ubuntu.

---

### Post by Bucky Ball on 2010-05-03
I am using 8.04 but this should be the same.

First backup /fstab

```
sudo cp /etc/fstab /etc/fstab.backup
```

In a terminal:

```
sudo nano /etc/fstab
```

Look for the entry for the Windows partition and put a # in front of it so it will be ignored on boot like so:

```
# Entry for /dev/sdd2 :
# UUID=f6beac14-d4ec-4b90-ac38-d995a8a0acf9 / ext3 relatime,errors=remount-ro 0 1
```

Yours may look different but which ever line is applicable, add #

---

### Post by efflandt on 2010-05-03
Even a Windows partition on the same drive is not mounted automatically.  It will appear in Places, but is not mounted unless you click on it, and then you have to be an sudo user and enter a password.

To put grub on the mbr of 2nd drive (or any external drive) you have to pay attention to the **Advanced** button, at the summary screen after selecting partitions and setting up your user, just before installation proceeds.

---

### Post by AzT3K on 2010-05-03
Dual boot is broken in 10.04 - as in grub wont detect your windows install - i wouldn't reccommend attempting it unless you want to manually edit your grub.cfg file after install to point to windows.

Windows 7 and vista disregards disks it cant mount or what ever windows calls it. sometimes it shows them breifly but they do hide automatically eventually. it can be a bit frightening when it does show them in explorer and u click on it and says "Format disk?".

ubuntu will show the windows disks in nautilus but it wont automatically mount them unless they are in your /etc/fstab file

---

### Post by bickelk on 2010-05-03
Thanks for all the help, I went ahead and insatlled Ubuntu on the second hard drive lucky I thought to click the Advanced button that I see efflandt mentioned. So I got grub on the second drive as well. And I now see what you meant by it not mounting the Windows drive.

Thanks for all the help guys, here's hoping that my experience with Ubuntu is better than I had with PCLinuxOS. (so far, I think it should be. especially with as much help as people are willing to offer)

---

### Post by Bucky Ball on 2010-05-03
Hope you love it. Remember though, 10.04 has only been out a week or so; teething problems are possible but from most reports pretty smooth sailing so far.

---

