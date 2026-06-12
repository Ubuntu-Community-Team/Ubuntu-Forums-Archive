---
title: "GRUB problem - error 23 w/ scsi"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by tdwp603 on 2008-03-06
hi, i've been trying to get grub to boot up windows xp on another hard drive, a SCSI.

it gives me this error: error 23: error while parsing number

here is my partition table:
> Disk /dev/hdc: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde65de65

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        7165    57552831   83  Linux
/dev/hdc2   *        7166        7475     2490075    c  W95 FAT32 (LBA)

Disk /dev/sda: 36.4 GB, 36419584000 bytes
255 heads, 63 sectors/track, 4427 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4c902449

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4426    35551813+   7  HPFS/NTFS


^ the xp hard drive is /dev/sda1 i believe. ^

here is my menu.lst:
> 
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c2edf050-da1a-4da9-a9a6-f095bbb32f9b ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c2edf050-da1a-4da9-a9a6-f095bbb32f9b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title           Microsoft Windows XP
rootnoverify    (sd0,0)
chainloader        +1

am i missing something? 
is the root wrong?

any problems please assess

thanks,
-johnny

---

### Post by Herman on 2008-03-07
```
title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=c2edf050-da1a-4da9-a9a6-f095bbb32f9b ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

 title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=c2edf050-da1a-4da9-a9a6-f095bbb32f9b ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

title           Microsoft Windows XP
rootnoverify    ([COLOR=Red]**s**[/COLOR]d0,0)
chainloader        +1
``````
                              title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=c2edf050-da1a-4da9-a9a6-f095bbb32f9b ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=c2edf050-da1a-4da9-a9a6-f095bbb32f9b ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

title           Microsoft Windows XP
rootnoverify    ([COLOR=Sienna]**h**[/COLOR]d2,0)
[COLOR=Sienna]**makeactive**[/COLOR]
chainloader        +1                                
```Regards, Herman :)

---

### Post by tdwp603 on 2008-03-07
i changed it herman, now there is no error, but it says "starting up..." and does nothing for a long time, almost 10 minutes. any ideas?
do think its appropriate to change boot loaders? if so which one? LILO?

---

### Post by Herman on 2008-03-07
:) I'm sorry, tdwp603, I forgot you'd need a pair of 'map' commands as well, to fool Windows into thinking it's in the first hard disk, try this and Windows should boot now,
```
title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=c2edf050-da1a-4da9-a9a6-f095bbb32f9b ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

 title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=c2edf050-da1a-4da9-a9a6-f095bbb32f9b ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

title           Microsoft Windows XP
rootnoverify    (hd2,0)
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader        +1
```
LiLo is a good boot loader, but Ubuntu uses file system UUIDs now. You would need to edit your /etc/fstab file in order to use LiLo these days, and that's more work. 
Besides that, as always you need remember to run /etc/liloconfig every time there's a kernel update. 
LiLo doesn't have a [command line interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") to help you boot in an emergency either, so GRUB is the better boot loader of the two at the moment

If you're a LiLo fan and you especially want to use LiLo you can if you want, [LiLo Page]("http://users.bigpond.net.au/hermanzone/p4.html")
 
 Regards, Herman :)

---

### Post by tdwp603 on 2008-03-07
ok now it says the "NTDLR" is missing"
reinstallation?
any ideas herman?
at the moment im browsing the forum for some clues on how to solve this.
thanks a lot by the way for helping me. :)

-johnny

EDIT: ok something is fishy. i just copied the ntdlr file from the xp cd onto the scsi (xp) and it still has the same problem. :confused:
grub buggy with scsi hmm.. 
i might go to lilo if i can't get this working in the next couple days.

---

### Post by Herman on 2008-03-07
> ok now it says the "NTDLR" is missing" Windows always says that, it's just to scare you. NTLDR will be there alright. If you want to check, do this, [            A Birds's eye view of Windows XP]("http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP")
>  reinstallation? No, not necessary, you can do it if you want.
>  any ideas herman? Yup, read this, [ NTLDR is missing, press any key to restart]("http://users.bigpond.net.au/hermanzone/p15.htm#NTLDR_is_missing_press_any_key_to").
Especailly go to this website, [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm"), and follow the instructions there and download an .iso file tomake yourself a special boot CD from there, or a floppy disk.
It has a special generic boot.ini file ion it so you can boot Windows in any partition in a first or second hard disk, I'm not sure if it can boot Windows in a third hard disk, we might need to modify it.
>  at the moment im browsing the forum for some clues on how to solve this.
thanks a lot by the way for helping meGood.
>  EDIT: ok something is fishy. i just copied the ntdlr file from the xp cd onto the scsi (xp) and it still has the same problem. :confused:
grub buggy with scsi hmm.. 
i might go to lilo if i can't get this working in the next couple days. No, it isn't a GRUB problem, GRUB is doing it's part fo the job okay, but after GRUB hands over control to the Windows boot loader, NTLDR, something is going wrong. Probably NTLDR is confused because Windows is in a third hard disk, or something like that. Normally GRUB's map commands fix that.
I need some time to thing a little more....
Try changing the map commands to,
title           Microsoft Windows XP
rootnoverify    (hd2,0)
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader        +1maybe and see what happens.

For a different way to do things, you might try [    Changing the hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority"), and make your Windows hard disk be your number2 hard disk, that's a bit more the same as what lots of other people do, and we know it should work okay then, (we think), at least it will make it easier to boot with that boot disc I mentioned.
>  thanks a lot by the way for helping me. :)No problem, just keep trying and you'll get there. 
Regards, Herman :)

---

