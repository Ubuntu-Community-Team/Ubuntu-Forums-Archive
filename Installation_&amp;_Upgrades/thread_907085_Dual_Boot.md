---
title: "Dual Boot"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by cmpx17 on 2008-09-01
Hi All,

I can't seem to solve this problem using google, mainly cause it's a bit of an odd situation. Though it seems like it should be fairly common. 

I used to have XP installed on an IDE hard drive and this was it. Then when I got Vista I installed it to a new SATA hard drive, Vista happily noticed XP was there and it's boot manager let me dual boot into Vista (default) or XP. However I never use XP anymore and I wanted to install ubuntu for various reasons so I thought I'd install it over XP onto the IDE hard drive. I read that Ubuntu happily dual boots with Vista do I didn't think this would be a problem. During install I selected 'use whole drive' and the IDE HDD (formerly XP). Now Ubuntu (or rather GRUB) didn't have Vista as an option so I added it to menu.lst, but when I select it I get the error

```
"NTLDR is missing.
Press Ctrl+Alt+Del to restart."
```

The entry I added to menu.lst is

```
title 		Microsoft Windows Vista (R)
root         	(hd0,0)
chainloader	+1
#find --set-root /bootmgrv
#chainloader /bootmgrv
```

I've tried various combinations of the commented / uncommented lines and most give the less helpful "error number 23, error parsing number". It might be worth adding that I wish to keep GRUB as my boot manager, though I've read that Vista's bootmgr wont let one load non MS OS's so this is kind of implied.

If anyone can help me get dual boot back it would be much appreciated.

---

### Post by manishtech on 2008-09-01
```
title         Microsoft Windows Vista (R)
root             (hd0,0)
chainloader    +1
#find --set-root /bootmgrv
#chainloader /bootmgrv 

```
 Is this SATA HDD your first HDD or second? If you added it later, then edit (hd0,0) with (hd1,0) and then try.

Hope this works!

---

### Post by caljohnsmith on 2008-09-01
It looks like your entry in menu.lst for Windows Vista is not correct, so please post the following:
```
sudo fdisk -lu
 
```
Also, what is (hdX,Y) for the Ubuntu entries in menu.lst?

---

### Post by cmpx17 on 2008-09-01
manishtech, I tried what you suggested and that produced the following error

```
Error 13: Invalid or unsupported executable format

Press any key to continue
```

I searched for bootmgr and winloader.exe on the vista HDD and found about thrity copies of each, is this normal?

caljohnsmith, the output of fdisk is as follows

```
Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6bec295b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   321669494   160834716    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5824af44

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   303467849   151733893+  83  Linux
/dev/sdb2       303467850   312576704     4554427+   5  Extended
/dev/sdb5       303467913   312576704     4554396   82  Linux swap / Solaris

Disk /dev/sdd: 1031 MB, 1031798784 bytes
255 heads, 32 sectors/track, 246 cylinders, total 2015232 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          32     1999199      999584    6  FAT16
```

Does this help at all?

---

### Post by caljohnsmith on 2008-09-01
I can't be for sure since you didn't mention what (hdX,Y) is for your Ubuntu entries in menu.lst, but give this a try first:
```
title         Microsoft Windows Vista (R)
root             (hd1,0)
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```
If that doesn't work, please post the full contents of your menu.lst.

---

### Post by cmpx17 on 2008-09-01
I tried what you suggested caljohnsmith, I am still getting the same error number 13. When I swapped line one to 
```

root   (hd0,0)
```

It said 'starting up...' but then froze like that. FYI I made this edit from within Grub. 

The other options listed in menu.lst are

```
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=404e1e29-39d4-47cd-b4d2-efd096c9542e ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=404e1e29-39d4-47cd-b4d2-efd096c9542e ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

title 		Microsoft Windows Vista (R)
root             (hd1,0)
makeactive
map        	(hd0) (hd1)
map	        (hd1) (hd0)
chainloader	+1
#find --set-root /bootmgrv
#chainloader /bootmgrv


### END DEBIAN AUTOMAGIC KERNELS LIST
```

So it looks like the Ubuntu is (hd1,0) which would suggest Vista is on something different, I added this drive after though, so does this mean it is (hd2,0)?

---

### Post by cmpx17 on 2008-09-01
Scratch that suggest, apparently (hd2,0) doesn't exist. Duh.

---

### Post by caljohnsmith on 2008-09-01
OK, it looks like Vista is indeed on (hd0,0). I know Windows XP can be booted without the "makeactive" option (which sets its boot flag), but I don't know for sure for Vista; so before doing anything else, give this a try in your menu.lst:
```
title 		Microsoft Windows Vista (R)
root             (hd0,0)
makeactive
chainloader	+1
```
And I would recommend deleting the following lines since they aren't going to help at any point:
```
#find --set-root /bootmgrv
#chainloader /bootmgrv

```
So if the above Vista entry doesn't work, then it is a high probability the problem is with your Vista partition. So Vista was working fine until you installed Ubuntu? You didn't change anything with the Vista HDD at all? If that is true, the next step would be to use your Vista Recovery CD/DVD (or [download one here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/") if you don't have one), and run the following command:
```
bootrec /fixboot
```
That will make sure your Vista's partition boot sector is OK. Let me know how it goes or if you need more details/info. :)

---

### Post by cmpx17 on 2008-09-01
Yeah I already tried

```
title 		Microsoft Windows Vista (R)
root             (hd0,0)
makeactive
chainloader	+1
```

but to no avail. I suspected it might be something to do with the vista partition (oh, and no I haven't changed a thing on it) my guess was that the vista boot stuff was actually on the XP disk as I 'upgraded' from XP but it let me do a clean install onto my new disk. I'll have a root around for my DVD and let you know.

---

### Post by cmpx17 on 2008-09-02
Cool, it worked. Though I had to try a couple of times with the bootrec.

Thanks

---

### Post by caljohnsmith on 2008-09-02
> **cmpx17 said:**
> Cool, it worked. Though I had to try a couple of times with the bootrec.

Thanks
I'm glad Vista is working for you now. :) And just to help out others who have the same problem, would you mind taking just a minute and let everyone know exactly how you fixed it with your Vista DVD? In other words, did you do:
```
bootrec /rebuildbcd
```
Or did you use the Vista recovery options?

---

