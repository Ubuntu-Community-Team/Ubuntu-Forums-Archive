---
title: "Grub help"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by skate_3214 on 2006-06-16
Hi i recently upgraded to the new linux kernel and it has wiped out the windows XP entry in grubs menu.lst file could anyone help me put it back in there. The XP partition is on the first hard drive second partition, any help would be appreciated.

---

### Post by Herman on 2006-06-16
skate_3214,
Please open up a terminal and enter the following code, ```
sudo fdisk -lu
``` and post the results here so people can see your partition numbers in case they aren't in disk order.
Also please post the bottom section of your /boot/grub/menu.lst file,```
sudo gedit /boot/grub/menu.lst
```Thanks, :D Herman

---

### Post by skate_3214 on 2006-06-16
This is what i got when i put sudo fdisk -lu into the terminal:

> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    10747484     5373711    b  W95 FAT32
/dev/sda2        10747485    72180044    30716280    7  HPFS/NTFS
/dev/sda3   *   308480130   312576704     2048287+  82  Linux swap / Solaris
/dev/sda4        72180045   308480129   118150042+  83  Linux

Partition table entries are not in disk order

Heres the bottom of my menu.lst:

> ## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda4 ro quiet splash rootflags=data=writeback
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda4 ro single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda4 ro quiet splash rootflags=data=writeback
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda4 ro single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by SiriusIntent on 2006-06-16
I have the same problem and have been trying to work on it for a few hours now so any help would be apreciated.

> 
Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   390716864   195358401    7  HPFS/NTFS

Disk /dev/hdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders, total 39876480 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63    10490444     5245191   83  Linux
/dev/hdb2        10490445    39873329    14691442+   5  Extended
/dev/hdb5        10490508    12578894     1044193+  82  Linux swap / Solaris
/dev/hdb6        12578958    39873329    13647186   83  Linux

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    52436159    26218048+   7  HPFS/NTFS
/dev/sda2        52436160   234420479    90992160    f  W95 Ext'd (LBA)
/dev/sda5        52436223   234420479    90992128+   7  HPFS/NTFS


Here's the grub menu.lst:

> ## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##
title		Microsoft Media Center Edition
root		(hd2,0)
savedefault
makeactive
chainloader	+1

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Linux Operating Systems:
#root

title		Ubuntu, kernel 2.6.15-25-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

#title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hdb1 ro single
#initrd		/boot/initrd.img-2.6.15-25-386
#boot

#title		Ubuntu, kernel 2.6.15-23-386
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-23-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro single
#initrd		/boot/initrd.img-2.6.15-23-386
#boot

### END DEBIAN AUTOMAGIC KERNELS LIST


The current Windows XP entry doesnt work at all, but I have another way of getting into Windows but it means I have to change the boot order via the BIOS in order to change OS! :( 

Thanks for any help!

---

### Post by SiriusIntent on 2006-06-16
I probably should mention that Windows XP is located on the SATA 120gig drive on the first partition 25gig.

---

### Post by Herman on 2006-06-16
skate_3214, try this and see if it works,> ## ## End Default Options ##

title Ubuntu, kernel 2.6.12-10-386
root (hd0,3)
kernel /boot/vmlinuz-2.6.12-10-386 root=/dev/sda4 ro quiet splash rootflags=data=writeback
initrd /boot/initrd.img-2.6.12-10-386
savedefault
boot

title Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root (hd0,3)
kernel /boot/vmlinuz-2.6.12-10-386 root=/dev/sda4 ro single rootflags=data=writeback
initrd /boot/initrd.img-2.6.12-10-386
boot

title Ubuntu, kernel 2.6.12-9-386
root (hd0,3)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/sda4 ro quiet splash rootflags=data=writeback
initrd /boot/initrd.img-2.6.12-9-386
savedefault
boot

title Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root (hd0,3)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/sda4 ro single rootflags=data=writeback
initrd /boot/initrd.img-2.6.12-9-386
boot

title Ubuntu, memtest86+
root (hd0,3)
kernel /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP 
root        (hd0,1)
savedefault
makeactive
chainloader    +1

I pasted the last two lots of commands at the bottom of your menu.lst, I hope it's correct. Good luck, just copy this and paste it to the bottom of yours, if you still have trouble, let me (or somebody) know. :D Herman

---

### Post by Herman on 2006-06-16
SiriusIntent, this one's for you, try it and see, yours is a little more of a challenge, I hope I got it right the first time.
> ## ## End Default Options ##
title Microsoft Media Center Edition
root (hd2,0)
savedefault
makeactive
chainloader +1

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title Linux Operating Systems:
#root

title Ubuntu, kernel 2.6.15-25-386
root (hd1,0)
kernel /boot/vmlinuz-2.6.15-25-386 root=/dev/hdb1 ro quiet splash
initrd /boot/initrd.img-2.6.15-25-386
savedefault
boot

#title Ubuntu, kernel 2.6.15-25-386 (recovery mode)
#root (hd1,0)
#kernel /boot/vmlinuz-2.6.15-25-386 root=/dev/hdb1 ro single
#initrd /boot/initrd.img-2.6.15-25-386
#boot

#title Ubuntu, kernel 2.6.15-23-386
#root (hd1,0)
#kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro quiet splash
#initrd /boot/initrd.img-2.6.15-23-386
#savedefault
#boot

#title Ubuntu, kernel 2.6.15-23-386 (recovery mode)
#root (hd1,0)
#kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro single
#initrd /boot/initrd.img-2.6.15-23-386
#boot

### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP 
root        (hd2,0)
savedefault
makeactive
chainloader    +1
Again, let me know if you still have trouble. 

By the way, [GAG Boot Manager]("http://gag.sourceforge.net/") will always boot Windows for you in an emergency, and it will also boot Ubuntu as well if you add Lilo or GRUB to the first sector of your Ubuntu partition. (Leave your existing GRUB on MBR ). For how to download GAG and make a GAG boot floppy disk or CD, and install Lilo to Ubuntu partition, [*click here*]("http://users.bigpond.net.au/hermanzone/p12.htm").
Regards, Herman :D

---

### Post by SiriusIntent on 2006-06-16
Thanks for the assistance Herman but the script written for my Grub menu.lst...isnt that the exact same thing that I have?

Here's mine (top of the menu.lst)
> 
title Microsoft Media Center Edition
root (hd2,0)
savedefault
makeactive
chainloader +1


Here's yours
> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP
root (hd2,0)
savedefault
makeactive
chainloader +1


---

### Post by grexk on 2006-06-16
Just a tip:
 Go to command in the Grub shell then type "root (hd[press tab])" will list available partitions. Hope this will help.

---

### Post by Herman on 2006-06-16
SiriusIntent, if the above doesn't work, try adding in these map commands. I'm sorry I don't have a multiple disk computer to try these out myself, I have only learned about these from reading threads here at the Ubuntu forums, I hope I've got it right.
>  # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP 
map (hd0) (hd2)
map (hd2) (hd0)
root        (hd2,0)
savedefault
makeactive
chainloader    +1

---

### Post by Herman on 2006-06-16
> Thanks for the assistance Herman but the script written for my Grub menu.lst...isnt that the exact same thing that I have?

Here's mine (top of the menu.lst) Okay, yes it is, I'm not sure but it might make a difference if it's placed under the divider for non Linux operating systems or not. Quite possibly you are right. it might not matter. Try the map commands then.
Regards, Herman :D

---

### Post by SiriusIntent on 2006-06-16
Thanks Herman! It worked once I mapped the drives, but I think I changed the mapping a little im in windows xp now so I cant check but i think it went like this:

> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP
map (hd0) (hd0)
map (hd2) (hd1)
root (hd2,0)
savedefault
makeactive
chainloader +1


---

### Post by Herman on 2006-06-16
SiriusIntent, thanks for the feedback, I'm glad you got it working. I'll make a note and pay more attention next time I see another example of that mpa command in use so I can get it right a little quicker next time, Regards, Herman. :D

EDIT, Oh, by the way, it doesn't matter what you type on the line 'title', you can put Microsoft Media Center Edition back there again if you want, or anything you like on that line. I just didn't look that high up on your menu.lst the first time, I'm used to the Windows entries being at the bottom.

---

### Post by skate_3214 on 2006-06-16
Thanks alot Herman it worked perfectly, thats what i like about the linux community theres always someone willing to help. Once again thank you.;)

---

### Post by Herman on 2006-06-16
:D Great! Thanks for the feedback, skate_3214 :D

---

