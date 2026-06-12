---
title: "gRUB DOES NOT WORK"
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by Aceninja on 2008-03-29
I just installed Ubuntu 8.04 using the alt install cd and the installation went smooth.

After the reboot, when Grub gives me the option to boot Ubuntu or XP Pro, and I choose Ubuntu. I get the following error: 21 : Selected disk does not exist

How do i fix this? And how come it's happening on an install? I haven't messed with any setting whatsoever.

I am using a separate SATA hdd for Ubuntu and another one for Win Xp. In addition to these, I've got 2 hdds in a RAID 1 config (soft raid - Intel IC7HR) and one external hdd plugged into an e-sata port. I'm guessing those should not be a factor. 

In BIOS I have the hdd w/ linux installed as # 1 for boot. 

Any assistance you can provide will be highly appreciated!

ps: Complete n00b here....

---

### Post by darkenergy on 2008-03-29
try once pressing "e" when you selected ubuntu and see where grub is looking for the kernel.
if it is pointing to the wrong device you can correct it

if this doesn't work try entering the "console" and type "find <kernel>" you will get a list of ervery kernel grub can find

---

### Post by confused57 on 2008-03-29
> **Aceninja said:**
> I just installed Ubuntu 8.04 using the alt install cd and the installation went smooth.

After the reboot, when Grub gives me the option to boot Ubuntu or XP Pro, and I choose Ubuntu. I get the following error: 21 : Selected disk does not exist

How do i fix this? And how come it's happening on an install? I haven't messed with any setting whatsoever.

I am using a separate SATA hdd for Ubuntu and another one for Win Xp. In addition to these, I've got 2 hdds in a RAID 1 config (soft raid - Intel IC7HR) and one external hdd plugged into an e-sata port. I'm guessing those should not be a factor. 

In BIOS I have the hdd w/ linux installed as # 1 for boot. 

Any assistance you can provide will be highly appreciated!

ps: Complete n00b here....

Can you boot Windows, using grub or Windows bootloader?
Boot a live cd & post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

Mount your root partition, see the output of  "fdisk -l":
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/xxx /media/ubuntu
```
substitute your root partition for /dev/hdxxx

Then post the output of:
```
gedit /media/ubuntu/boot/grub/menu.lst
```
you just need to post the boot entries for Ubuntu & Windows

and
```
gedit /media/ubuntu/boot/grub/device.map
```

Did you have the external drive connected when you installed Hardy?

---

### Post by Aceninja on 2008-03-29
I was able to boot off the live cd (7.04 version) and get into the terminal.

There I did sudo fdisk-l and got the following:

> ubuntu@ubuntu:~$ sudo fdisk -l



Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS



Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1               1        4310    34620043+  83  Linux

/dev/sdb2            4311        4500     1526175    5  Extended

/dev/sdb5            4311        4500     1526143+  82  Linux swap / Solaris



Disk /dev/sdc: 250.0 GB, 250059350016 bytes

255 heads, 63 sectors/track, 30401 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes



   Device Boot      Start         End      Blocks   Id  System

/dev/sdc1               1       30400   244187968+   7  HPFS/NTFS



Disk /dev/sdd: 250.0 GB, 250059350016 bytes

255 heads, 63 sectors/track, 30401 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

 

  Device Boot      Start         End      Blocks   Id  System

/dev/sdd1   *           1       30401   244196001    7  HPFS/NTFS



Disk /dev/sde: 150.0 GB, 150039945216 bytes

255 heads, 63 sectors/track, 18241 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes



   Device Boot      Start         End      Blocks   Id  System

/dev/sde1   *           1       18240   146512768+   7  HPFS/NTFS




Umm I couldn't go any further than that as I did not know which one was the root partition I was supposed to mount? Is it linux, or swap?

And yes I did have the external drive connected when installing Ubuntu.

---

### Post by confused57 on 2008-03-29
You want to mount the linux root partition, /dev/sdb1:
```
sudo mount -t ext3 /dev/sdb1 /media/ubuntu
```

---

### Post by Aceninja on 2008-03-29
Okay I mounted the linux partition and then i typed in:

gedit /media/ubuntu/boot/grub/menu.lst

and this is what I got:

> title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=6da3ea6b-eb94-4c81-b70d-9e5afb55afa3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=6da3ea6b-eb94-4c81-b70d-9e5afb55afa3 ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


here is my device map:

> 
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
(hd4)	/dev/sde

---

### Post by confused57 on 2008-03-29
Are you able to boot Windows from grub or it's own bootloader?

You can try a little trial & error in an attempt to boot Ubuntu...make sure your Ubuntu entry is highlighted in your grub boot menu, press "e" to edit, highlight the line with root, press "e" again, change root from (hd3,0) to (hd0,0), press "enter", then "b" to boot...if (hd0,0) doesn't work, you can try (hd1,0), then (hd2,0).  This is temporary if it works, but can be made permanent in your /boot/grub/menu.lst.

---

### Post by Aceninja on 2008-03-30
Nope I can't even load WIN from Grub now. And when I substitute 3,0 by 1,0 , 2,0 etc it gives me an error 17: Cannot mount selected partition. And for 4,0 it gives me an error 21. This is driving me crazy. Any ideas on how to make this work?

---

### Post by confused57 on 2008-03-30
> **Aceninja said:**
> Nope I can't even load WIN from Grub now. And when I substitute 3,0 by 1,0 , 2,0 etc it gives me an error 17: Cannot mount selected partition. And for 4,0 it gives me an error 21. This is driving me crazy. Any ideas on how to make this work?
Try installing grub to the drive's mbr that Ubuntu is installed to, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
read the instructions, but it'll be something like:
```
sudo grub
find /boot/grub/stage1
```
this "should" return "root (hd3,0)", then to setup grub to the mbr:
```
root (hd3,0)
setup (hd3)
quit
```

Then set your bios to boot first to the Ubuntu drive, if you get a grub boot menu, then try the "e" method I described earlier, change root to (hd0,0), then "b" to boot.  If this works, it shouldn't be too difficult to add an entry to boot Windows.

---

### Post by Aceninja on 2008-03-30
OK I tried the steps mentioned above and this is what I got:

> 
sudo grub


grub> find /boot/grub/stage1
 (hd1,0)

grub> root (hd3,0)

grub> setup (hd3)

Error 17: Cannot mount selected partition


Hmm would reinstalling the OS help and specifying Grub location during install? Just a thought..

---

### Post by Aceninja on 2008-03-30
okay! I just changed the grub to 0,0 during boot and it worked!! I am in Ubuntu 8.04 right now and it looks great! Now how would I make the change permanent? I dont know if windows works at the moment, but who cares!..lol okay I do want win to work. will post the results of that in a bit.

---

### Post by confused57 on 2008-03-30
> **Aceninja said:**
> okay! I just changed the grub to 0,0 during boot and it worked!! I am in Ubuntu 8.04 right now and it looks great! Now how would I make the change permanent? I dont know if windows works at the moment, but who cares!..lol okay I do want win to work. will post the results of that in a bit.
Here's how to make the change permanent, from a terminal:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
change root for all your Ubuntu entries to (hd0,0)...also, change the line with #groot to (hd0,0), leave the # in front of groot.

If your current Windows entry doesn't work, you can try:
```
title Microsoft Windows XP Professional
root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```
or root (hd3,0), and change map lines accordingly.

---

### Post by Aceninja on 2008-03-30
Thanks a lot for your help! I was able to boot into Ubuntu and XP using your advice!

I do have another problem now...Ubuntu's crashed! It wont boot.. As I type this I am looking at a black screen with a lot of error codes. One of them says Fixing recursive fault but reboot is needed!

BUG: scheduling while atomic: console_setup Tainted: G D 2.6.24-12-generic # 1

And it gives me a bunch of other error codes after that? Any ideas would be highly appreciated!

---

### Post by confused57 on 2008-03-31
> **Aceninja said:**
> Thanks a lot for your help! I was able to boot into Ubuntu and XP using your advice!

I do have another problem now...Ubuntu's crashed! It wont boot.. As I type this I am looking at a black screen with a lot of error codes. One of them says Fixing recursive fault but reboot is needed!

BUG: scheduling while atomic: console_setup Tainted: G D 2.6.24-12-generic # 1

And it gives me a bunch of other error codes after that? Any ideas would be highly appreciated!
I'm not familiar with the error(s) you're describing, did you change any configurations files or install any programs, other than security updates from Ubuntu?

What you might want to do is set up your bios boot order as it was when you installed Windows, then reinstall Windows IPL(Initial Program Loader):
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
You can use a Windows install cd(not a recovery one), boot, press "r", enter FIXMBR...or Super Grub Disk can do this.

Once you're able to boot Windows, using Windows IPL...then reset your bios boot order to boot your Ubuntu drive first(after cd rom), reinstall Ubuntu...there is an "Advanced" button you can click to select where to install grub, you can change the default (hd0) to /dev/sdb(or however your Ubuntu drive is designated by the installer).

The advantage of setting your system up this way is that if Ubuntu fails to boot from grub, you can change your bios hard drive boot order to boot Windows.

---

