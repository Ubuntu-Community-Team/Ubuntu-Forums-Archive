---
title: "GRUB hosed on SATA drive"
date: 2006-08-10
forum: Installation &amp; Upgrades
---

### Post by Nachtengel on 2006-08-10
When installing to a SATA drive, the MBR seems to be broken, as grub doesn't recognize the fact that I've formatted my drives.  Using GParted will sometimes give me an "unkown" filesystem type when I open it, but other times will retain the formatting scheme I am listing... that is until reboot.

I am trying to install Dapper on an 80 GB SATA II drive formatted like so:

sda1  -  64MB  - /boot  - ext3
sda2  -  8129MB - linux-swap
sda 3 - rest of the space - /  - reiserfs

Thus far I've gotten a Grub error 15, and a few cases where the drives weren't actaully formatted when Gparted indicated they were.  What gives?

Anyone have any advice?

---

### Post by tagra123 on 2006-08-11
Boot a live cd go to a terminal and type:

grub
find /boot/grub/stage1  

### it will  print something similar to (hd0,1)

### the hd0 could also be (hd1,1) etc...

### if (hd0,1) is returned type the commands below

root (hd0,1)
setup (hd0)
quit

Reboot the computer - this worked for me after moving a harddrive.

---

### Post by VirtuAlex on 2006-08-11
If you have IDE drive in the sytem try to boot from it - sometimes grub installs mbr to IDE instead of sata, even if sata is your boot drive during installation.

---

### Post by Nachtengel on 2006-08-12
Now that you mention it, I did try and use an IDE drive to boot from temporarily earlier and kind of left it in the machine.  I took it out and tried installing again, this time with only SATA drives in the machine.  Still the same problem persisits.

As for the grub commands

```
find /boot/grub/stage1
Error 15: File not Found
```

I'll try the other commands anyways:

```
root (sda,0)
Error 23: Error while parsing number

boot (sda,0)
Error 8: Kernel must be loaded before booting

devive sda
Error 11: Unrecognized Device String

device sda1
Error 11: Unrecognized Device String
```



Am I just making syntax errors, or does this speak of a larger issue?

---

### Post by Pablo El Vagabundo on 2006-08-14
Hey, 

If you installed ubuntu with the IDE drive in initally I would suggest wiping everything and trying a clean install with the IDE drive removed.

However from the post above I can see a small mistake, grub devices are not like the linux device.

You have:

root (sda,0)

This should be:

root (hd0,0)

It is odd that the find command did not return results. 

Also the liveCD has an option on the menu to boot from the first hard drive. This worked for me when the bootloader was installed on my IDE drive.

You asked for a step by step in your PM:

- Booted into the sata installation using the liveCD option above. (This is the same as using the live CD, mounting the root on the sata and then chrooting it. There are instructions around the forums for this.)

- The weird problem I was having was that the /boot/grub/menu.lst had the wrong device names, so I switched them (hd0 was sata and hd1 was IDE). But that might not be something you had to do.

- I typed grub in the console.
- I typed find /boot/grub/stage1
- The grub console had the devices different from the menu.lst (ide was hd0 and sata hd1)

root (hd1,1) 

<the device was hd1 and the partition was 1, the partions start at 0, so it was the second partition for me>

setup (hd1)

<this installed grub into the mbr of the sata disk, using the information i the menu.lst>

You might be having a similar problem, the menu.lst devices might not be correct, in which case you would get the Error 15.

Hope this helps, I know it is a little disorganised.


Regards, 

Pablo

---

