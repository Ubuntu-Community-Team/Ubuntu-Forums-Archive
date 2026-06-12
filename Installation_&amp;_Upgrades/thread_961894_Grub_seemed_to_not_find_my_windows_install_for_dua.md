---
title: "Grub seemed to not find my windows install for dual booting."
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by wormeyman on 2008-10-28
I checked in gparted and fortunatly i did not overwrite it like i had feared it's just sitting there in /dev/sdb1 waiting for me to load it is there a utility that'll re-build my grub file or do i have to add it manually?

---

### Post by Pumalite on 2008-10-28
[http://www.supergrubdisk.org/wiki/Edit_menu_lst](http://www.supergrubdisk.org/wiki/Edit_menu_lst)

---

### Post by caljohnsmith on 2008-10-28
I don't know of any good way to automatically configure Grub to add Windows to your boot menu, but that link that Pumalite gave is an excellent place to start to learn how to do it yourself. If you get stuck and need help, then first post:
```
sudo fdisk -lu
```
Let me know which drive you are booting from on start up, and we can work from there. :)

---

### Post by wormeyman on 2008-10-28
```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		db599480-ca06-404b-ab90-8ed4b182c232
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=db599480-ca06-404b-ab90-8ed4b182c232 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		db599480-ca06-404b-ab90-8ed4b182c232
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=db599480-ca06-404b-ab90-8ed4b182c232 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		db599480-ca06-404b-ab90-8ed4b182c232
kernel		/boot/memtest86+.bin
quiet

title 		Windows XP
root		(hd1,0)
makeactive
chainloader +1
```

when i select windows xp it get stuck at starting up

---

### Post by caljohnsmith on 2008-10-28
If you post "sudo fdisk -lu" it will make it more clear, but if you are booting from your sda drive and Windows is on your sdb drive, you should be able to use the following to boot Windows;
```
title	   Windows XP
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```

---

### Post by wormeyman on 2008-10-28
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb5e5d0f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   149838254    74919096   83  Linux
/dev/sda2       149838255   156296384     3229065    5  Extended
/dev/sda5       149838318   156296384     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdfc6dfc7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   156280319    78140128+   7  HPFS/NTFS
/dev/sdb2       156280320   312576704    78148192+   7  HPFS/NTFS


```

sdb1 is where i keep my windows install sdb2 is where i store games.

---

### Post by caljohnsmith on 2008-10-28
OK, since you have 3 drives, you'll have to try two ways of booting Windows, so first open a terminal (applications > accessories > terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
And at the bottom add the two following entries:
```
title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Save, reboot, and one of them should work to boot Windows. Once you find which one works, you can delete the other one from your menu.lst. Let me know how it goes.

---

### Post by wormeyman on 2008-10-28
hd1 is what worked.

[http://www.computerhope.com/issues/ch000465.htm#b](http://www.computerhope.com/issues/ch000465.htm#b)

I'm going to try and follow those instructions.

```

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		db599480-ca06-404b-ab90-8ed4b182c232
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=db599480-ca06-404b-ab90-8ed4b182c232 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		db599480-ca06-404b-ab90-8ed4b182c232
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=db599480-ca06-404b-ab90-8ed4b182c232 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		db599480-ca06-404b-ab90-8ed4b182c232
kernel		/boot/memtest86+.bin
quiet

title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by wormeyman on 2008-10-28
Yay i'm posting this from windows right now thanks for the help now i can switch when i need too.  It seems that i don't have a boot.ini at all but it still loads fine so that's cool

---

### Post by swatsbiz on 2009-02-06
Hi,

I'm struggling with a similar problem - I can't find my Windows Vista installation.

Here's my output from sudo fdisk -lu

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd109d73d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    84293054    42146496    7  HPFS/NTFS
/dev/sda2        84293055   312576704   114141825    f  W95 Ext'd (LBA)
/dev/sda5        84293118   312576704   114141793+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4c984c97

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    81915434    40957686    7  HPFS/NTFS
/dev/sdb2        81915435   230275709    74180137+   f  W95 Ext'd (LBA)
/dev/sdb3       230275710   312576704    41150497+  83  Linux
/dev/sdb5        81915498   163830869    40957686    7  HPFS/NTFS
/dev/sdb6       163830933   227255489    31712278+   7  HPFS/NTFS
/dev/sdb7       227255553   230275709     1510078+  82  Linux swap / Solaris

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9c309c30

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    39070079    19535008+   7  HPFS/NTFS
/dev/sdc2        39070080   234420479    97675200    f  W95 Ext'd (LBA)
/dev/sdc5   *    39070143   117210239    39070048+   7  HPFS/NTFS
/dev/sdc6       117210303   234420479    58605088+  83  Linux


I have tried a number of combinations for Grub, and here's how I've abandoned it:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows NT/2000/XP (loader)
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista Ultimate (loader)
root		(hd0,1)
savedefault
makeactive
map		(hd1) (hd0)
map		(hd0) (hd1)
chainloader	+1

What should my Vista be entered as?

many Thanks
David

---

### Post by caljohnsmith on 2009-02-06
Swatsbiz, I think it would be better for you to start your own thread rather than resurrect this old thread. How about starting your own thread, download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what it will take to boot Vista.

---

