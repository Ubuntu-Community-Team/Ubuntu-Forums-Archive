---
title: "Ubuntu 5.04 GRUB Problem! Please Help"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by karthikb23 on 2008-04-20
Hi,
Having got Ubuntu CDs for V 5.04 during my college days, decided finally to install it.

My Set Up:
HD1: 40 GB - Already has Win XP Pro. MBR contains NTLDR.
HD2: New, 80 GB:
         2 Partitions exist: 30 GB - ext3, 1 GB - SWAP. (Rest is free and unmounted)

I planned to install GRUB on HD2. GRUB Installation asks me if it can overwrite MBR.
But instead, i install it on HD2, which is mounted as root.

Now, i aim to make both disks bootable, and let each OS know about the presence of the other. (By altering menu.lst, c:\boot.ini).
Based on the boot priority, the appropriate boot loader program would show me a menu.

After Ubuntu installation, on reboot, GRUB starts as expected.

I try to boot 'Linux kernal 2.6.12-9-386', but I get the following error:

[COLOR="Red"]root(hd1,0)            (which is correct)
FS is FAT, partition type is 0xc        :confused:  
File not found[/COLOR]

I earlier had a FAT32 share partition, but i removed it, thinking that was the problem. But this issue still persists.

A look at my 'menu.lst' and 'fstab' files:

[COLOR="Purple"]title		Ubuntu, kernel 2.6.10-5-386 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1


[COLOR="DarkGreen"]FSTAB Contents:[/COLOR]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0[/COLOR]

I now feel stuck! Any help is really appreciated!:)

---

### Post by Vermind on 2008-04-20
Hello.
I think this is a simple mixup on the part of GRUB.
When You start GRUB on the second disk, unless You have explicitly told it that the second disk is not the first, it will think that the disk it is on is hd0. Therefore, You have two alternatives:
Either 
1. change Your GRUB config to refer to the Linux as hd0, and Windows disk as hd1,
or
2. tell grub how it really goes.

You can boot the Linux in GRUB by pressing e for edit on the Linux entry and changing the hd1 to hd0. Then You can  proceed with alternative 1 or 2.

1. just edit menu.lst and change the hd1 to hd0.

2. Make a file called  /boot/grub/device.map, with the content: 
```
(hd0)   /dev/hda
(hd1)   /dev/hdb

```

then start grub with ```
grub --device-map=/boot/grub/device.map
```.
In the GRUB shell, issue the commands
```
root (hd1,0)
setup (hd1)
quit
```

---

### Post by karthikb23 on 2008-04-21
Thanks Vermind.
But my question:

If you check the menu.lst file, it seems perfect:

title Ubuntu, kernel 2.6.10-5-386 
root (hd1,0)
kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/hdb1 ro quiet splash
initrd /boot/initrd.img-2.6.10-5-386
savedefault
boot

i.e. GRUB knows the kernal image is on (hd1,0) at root /dev/hdb1 and I checked the location of kernal image, which is also correct as stated above.
Now in GRUB terms, hd1 surely refers to my second HD. i.e. slave HD.

Since i can see a menu, it means GRUB worked until stage 2.

If GRUB now has been told to pick kernal image from /dev/hdb1, why isn't it doing so?

I agree with what you say, i.e. it is still trying to refer the image from hda1, and hence says the FS is FAT (my windows HD, hda1).

But this really confuses me now. Why cant it do what it has been asked to? :(

---

### Post by karthikb23 on 2008-04-21
Ah Vermind!
I now understand what you say.
Regardless of what HD0/HD1 means, for GRUB, the HD it is installed on is HD0 i.e. the first HD.

On seeing HD1, it goes to my windows HD, and tries to boot my kernal from there, which obviously does not exist.

Right?

But i still find it perplexing, as to how GRUB can be blind like this :)

I mean my BIOS can tell which is HD0, and HD1.
Since i boot from HD1 for GRUB, i think GRUB too shd know it is on HD1, the second hard drive.

---

### Post by Vermind on 2008-04-21
Hello,
Well, to tell grub which is which, You need the device.map file and installing grub from the grub prompt, as I posted above.
So, first boot the Linux by changing the hd1 to hd0, editing in the GRUB bootup screen, then:

Make a file called /boot/grub/device.map, with the content:

```
(hd0)   /dev/hda
(hd1)   /dev/hdb

```

then start grub with
```
grub --device-map=/boot/grub/device.map

```
.
In the GRUB shell, issue the commands
```
root (hd1,0)
setup (hd1)
quit

```

I think this should fix it.

Why GRUB does this:
I have a setup where I have two hard disks with a boot partition, that are mirrored with software RAID. both disks also have GRUB on the MBR. I have told both GRUBs that they are hd0. This is because if one boot partition fails, the other can take over like nothing ever happened.

---

### Post by jocko on 2008-04-21
> **karthikb23 said:**
> Hi,
Having got Ubuntu CDs for V 5.04 during my college days, decided finally to install it.

Any reason why you don't get 7.10 or even 8.04? Pretty much has happened in ubuntu the three years that have passed since 5.04 was released, so I'm sure 7.10 or 8.04 (once it's finally released later this week) will cause less problems for you.

---

### Post by karthikb23 on 2008-04-21
Thanks a lot guys!

Seems a lot clearer and makes sense, wld try it over t weekend, when i get my hands back on my PC.

As for the Ubuntu version, yes, i have placed an order for t latest CD :)
Anyways, would prefer to first install a lower version, and then upgrade the kernal myself :biggrin:

---

### Post by karthikb23 on 2008-04-21
Would this work too?
In menu.lst:

map (hd0) (hd1)
map (hd1) (hd0)

Everything else remains unchanged.

---

### Post by Vermind on 2008-04-21
Hello,
Yes, I think that would work.

---

### Post by Archmage on 2008-04-21
Are you really want to install three year old software that isn't supporter anymore on your PC? Get the latest. Make it Xubuntu, if you have a small system and be happy.

---

### Post by gpilkay on 2008-04-21
Your system sounds quite similar to mine, I have a Celeron D with two 80 gig hard drives.  After you make sure XP is ok, what I did was set my Windows drive to SLAVE, with the new blank HD as MASTER.  This makes the Ubuntu drive boot first and handle Grub, while the XP drive remains untouched.  It worked very well for me.

However, please keep in mind your Ubuntu version is quite old.  I did mine with 7.04, later upgraded to 7.10.  Ubuntu CAN run on very low spec hardware, I have Ubuntu 7.10 (normal Ubuntu, not Xubuntu or the like) on a Celeron COPPERMINE processor with 345 mg RAM.  Sure it's a bit slow, but it was better then Windows ME.  That, and the whole system cost me TEN BUCKS.

It's now my Grandma's old-radio-show player and sudoku machine.

I would recommend getting a more current distribution, as they tend to be less buggy and better supported on most hardware.  If you don't have a CD burner, no problem, Ship-it will send you a CD free.

---

