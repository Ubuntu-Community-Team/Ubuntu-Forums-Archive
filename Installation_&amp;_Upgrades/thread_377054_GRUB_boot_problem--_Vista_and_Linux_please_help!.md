---
title: "GRUB boot problem-- Vista and Linux please help!"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by herbster on 2007-03-05
I have my pc set up as: IDE2 [slave] with Ubuntu and SATA with Vista (I have no IDE1 master right now as I took the drive out, it's bad, I'm getting a new one).
My BIOS boot order is booting off the SATA.

When I boot up off SATA, it says "GRUB Hard Disk Error" and hangs, I can't do anything but hit reboot on PC. When I boot from the IDE2, and I choose Vista in GRUB menu, it says "Unidentified executable" or something similar and hit enter to continue, which takes me back to GRUB menu, and if I choose Ubuntu, it says "cannot mount selected partition." However, I can use Super Grub Disk to boot into both. 

Here is the relevant part of my /boot/grub/menu.lst:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista Ultimate
root		(sd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Here is my device.map:

```
(hd0)	/dev/hda
(hd1)	/dev/hdb
(hd2)	/dev/sda
```

And here is my fdisk -l output:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38914   312568832    7  HPFS/NTFS

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4791    38483676   83  Linux
/dev/hdb2            4792        4998     1662727+   5  Extended
/dev/hdb5            4792        4998     1662696   82  Linux swap / Solaris
```


What I did was sudo grub-install /dev/sda, and it said install was fine, but of course it's not booting properly :(

Please help, what looks like it needs changing ?? This is really frustrating :( :(

UPDATE: I used my Vista DVD to repair my Vista boot record. However, when I boot off SATA (Vista) it still hangs at Grub Hard Disk Error. Yet, now when I use Super Grub Disk to boot up, I can boot both Ubuntu and Vista fine by editing the Grub entry for Vista to root (hd0,0) and it goes. I guess I am confused as to which drive to boot off of or why when I boot off of the Ubuntu IDE it gives me those errors near the top of my post??

---

### Post by Gerard Barberi on 2007-03-05
Try 

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_boot_into_Windows_installed_on_a_seperate_SATA_drive](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_boot_into_Windows_installed_on_a_seperate_SATA_drive)

---

### Post by herbster on 2007-03-06
Gerard,

I tried that. The problem is I have to install GRUB onto the SATA drive which has Vista on it and overwrite Vista's boot record. How do I do that ????

---

### Post by bulldog on 2007-03-06
> **herbster said:**
> Gerard,

I tried that. The problem is I have to install GRUB onto the SATA drive which has Vista on it and overwrite Vista's boot record. How do I do that ????

Don't do that!!
Your device.map shows three hdd's,you have removed one so there's an error.
Simple as that.

Edit:
Remove the drive that's not existing anymore from the device.map.
Set boot from the IDE disk,which has GRUB in the MBR I presume,in the BIOS.
Modify your menu.lst and maybe the fstab too.

If you're planning to replace your busted hdd with another one,you'll get the same problems again,if you modify things.

As I read you have GRUB on the Sata disk already,because you get a Grub error!
Just use the super GRUB disk to boot for now,and when you have replaced your hdd with a new one we can try to solve things.

Make in your menu.lst the (sd0,0) entry of Vista into (hd0.0) and see if it will boot from GRUB.

---

### Post by herbster on 2007-03-06
bulldog,

So I need to remove which one? I am confused because I know hd1(hda) which has Linux is correct and shuold stay, but then hd0 and hd2 I don't understand because hd2 in device.map says /dev/sda, which is my SATA, but when it boots it's read as hd0, so which one do I remove or what do I change????

---

### Post by bulldog on 2007-03-06
> **herbster said:**
> bulldog,

So I need to remove which one? I am confused because I know hd1(hda) which has Linux is correct and shuold stay, but then hd0 and hd2 I don't understand because hd2 in device.map says /dev/sda, which is my SATA, but when it boots it's read as hd0, so which one do I remove or what do I change????

If you're planning to replace your disk don't modify anything,because you'll get the same problems again.

But I saw in your menu.lst in the Vista entry (sd0,0) and this should be (hd0,0) if you boot from the Sata disk.

You have to understand GRUB names hdd's like (hd0),(hd1) and so on,**not** sd0!!

So you'll have to change your menu.lst and try if Vista will boot.

**EDIT**
You can try to edit the device.map and comment out the (hd0) /dev/hda [just place ## in front of it]
Boot from the sata disk afterwards and with a little luck you can boot ubuntu and Vista again.
When you have replaced your defective hdd,just remove the ## and all should be normal again.

---

### Post by herbster on 2007-03-06
bulldog,

Ok I made the changes, and I used Super Grub Disk to restore the MBR to my SATA and now when I turn on my computer it goes straight into Vista, there is no GRUB. Again, I have IDE master with Ubuntu and SATA with Vista, and here is my current menu.lst and device.map:

```

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
# title		Microsoft Windows XP Professional
# root		(hd0,0)
# savedefault
# makeactive
# chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

device.map:
```
## (hd0)	/dev/hda
(hd1)	/dev/hdb
(hd2)	/dev/sda
```

So the thing is, if I boot up with my Super Grub Disk I can choose Ubuntu or Vista just fine, but if not, it goes straight to Vista. There is no GRUB showing up now.

---

### Post by confused57 on 2007-03-06
bulldog has given you some excellent advice...he's not online right now, but I can give you a few things to try.  My suggestion would be to select your hdb Ubuntu drive in bios as the first hard drive in the boot sequence, this should give you a grub menu at bootup.  Selecting hdb as the first hard drive(SATA as 2nd)  will cause grub to designate this drive as hd0.
What you can try, is at the grub menu at bootup, highlight the entry to boot Ubuntu, press "e" to edit, change the line with "root (hd1,0)" to "root (hd0,0)", without the quotes...then press "b" to boot.   These changes are temporary, so they won't hurt your system setup, and can be made permanent in your /boot/grub/menu.lst.  If this works, I would recommend that you leave hdb as your first boot device & boot Vista from grub with an entry similar to this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map   (hd0) (hd1)
map   (hd1) (hd0)
chainloader	+1

I didn't realize the Super Grub Disk was capable of restoring Vista code to the mbr, interesting.

bulldog will probably be back before I even send this, but thought I'd offer some suggestions in the meantime.

---

### Post by herbster on 2007-03-06
confused57,

That worked PERFECTLY! Thank you soooo much!!! :) :)

---

### Post by confused57 on 2007-03-06
> **herbster said:**
> confused57,

That worked PERFECTLY! Thank you soooo much!!! :) :)

Great, I was hoping it would...I suppose you know how to make it permanent in your menu.lst file, if you want to leave your system set up this way.

If you do, make sure to change  this entry in your menu.lst:
```
# groot=(hd0,0)
```

You can find this entry near the top middle of your menu.lst, e.g.

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

If you happen to have a kernel update, update-grub is run, which reads this line to write your kernel entries into your menu.lst file.  Type it exactly as I've listed it, you need the # in front of the entry.

There's some excellent info on this site explaining how grub works:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by herbster on 2007-03-06
> **confused57 said:**
> If you do, make sure to change  this entry in your menu.lst:
```
# groot=(hd0,0)
```

You can find this entry near the top middle of your menu.lst, e.g.

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)
This part I understand...

> **confused57 said:**
> If you happen to have a kernel update, update-grub is run, which reads this line to write your kernel entries into your menu.lst file.  Type it exactly as I've listed it, you need the # in front of the entry.

This I don't.. what exactly am I doing in this part? Where? Terminal? In Ubuntu? What am I typing in?

---

### Post by confused57 on 2007-03-07
The second quote was just an explanation of why this section needs to be changed to #groot=(hd0,0)...sorry it was "confusing", you can essentially ignore what I mentioned here.

I believe you already know how to edit your /boot/grub/menu.lst, just in case:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

then just change the entry I mentioned to 
```
# groot=(hd0,0)
```

your previous entry was probably "# groot=(hd1,0)"

---

### Post by herbster on 2007-03-07
confused57,

Sorry for my confusion ;) I fixed up menu.lst and it's all good.. again, thanks so much for your help dude, this has been a headache :)

---

