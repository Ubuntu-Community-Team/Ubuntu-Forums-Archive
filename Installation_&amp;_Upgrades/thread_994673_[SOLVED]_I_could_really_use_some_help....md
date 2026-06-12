---
title: "[SOLVED] I could really use some help..."
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by stackbaxter on 2008-11-27
Hello all, I'm a card carrying linux/ubuntu noob-ee.
I haven't touched command line stuff since the days when dos reigned so it's almost like looking at it for the first time. i've been windowfied.
  here's the deal:  my machine is a compaq presario (i know, it was an emergency) pentium dual core, 1.6, 2 gig ram, vista 32 home, i have a 320 gig hd, and an older 20 gig hd.   i finally took the ubuntu plunge after almost destroying my computer due to vista's incompetence at seemingly simple tasks.  
   So i download the 8.10 live disk, boot from it and partition my 320 gig, and attempt to install ubuntu as a dual boot, installs fine, but doesn't give a boot option and goes straight to windows. then i install ubuntu on the 20 gig, installs fine but when booting from 20 gig get the "error 18" after it tries to load grub. 
     I haven't had a solid chunk of time to sit in front of the thing and work it out, just an hour here and there, so it could be something relatively easy.   then, i'm not sure what i did, i think i reinstalled it on the 320 gig but had it partition the partition i initially made, then i tried to boot from the 20 gig, and i think by default, it booted from the partition within the partition on the 320.  so then i tried to clean things up by erasing the partitions on the 320 from the live cd, but i can't erase them all, then i tried reinstalling on the 20 gig and messed around with the bootloader, and still the error 18.  and this whole time i vaguely know what i'm doing. at some point i went through the 320 and repartitioned parts of it for the root and the boot sections, there was already a swap,
   any advice would be ridiculously appreciated.  
ideally i would like to have ubuntu on the 20 gig to mess around with and get to know, otherwise a dual boot situation would be fine too.
  thanks to all who sympathize and to those who boldly tread forth to aid a flailing failing ubuntuser 

-S:confused:

---

### Post by TFX360 on 2008-11-27
StackBaxter,


Looksy [here]("http://ubuntuforums.org/showthread.php?t=993866").


Should help!


Bye,


TFX

---

### Post by caljohnsmith on 2008-11-27
Since you have an older computer, it is not a great surprise that you would unfortunately get a Grub error 18; that error is usually because the BIOS cannot access anything on the HDD past either 8.5 GB or 137 GB, depending on how old the BIOS is. It sounds like yours is the former case since the drive is only 20 GB. Fortunately the solution is usually very simple; when you go through the Ubuntu installer, choose the "manual" partitioning option, and create an additional ~200 MB ext3 partition at the very beginning of the drive, and then set the mount point on that partition as "/boot" in the installer. In other words, you are creating an additional "/boot" partition at the beginning of the drive in addition to your main Ubuntu partition, swap partition, and any other partitions you might want. Give that a shot and let me know how it goes, or if you need more info/details, feel free to ask. You might also want to see [this tutorial]("http://www.herman.linuxmaniac.net/p23.html") if you would like some help going through the installation process step-by-step. :)

---

### Post by stackbaxter on 2008-11-27
ha! i did exactly that, i thought i was golden, now it reports "error 15"

i did some quick research, couldn't find anything useful on the subject other than it indicates a missing file.  i did see something about somebody added a separate boot partition before the windows partition which then followed with the rest of ubuntu and it solved the dual boot probs. so i just moved my windows partition 200 mb to the right, not going to bother with the rest today.  but not being able to boot from the 20 gig is puzzling.  grub does load, it just errors out.  
  i'm not going to stop tryin'.;-)
any ideas?
thanks,

-S

---

### Post by caljohnsmith on 2008-11-28
> **stackbaxter said:**
> ha! i did exactly that, i thought i was golden, now it reports "error 15"

i did some quick research, couldn't find anything useful on the subject other than it indicates a missing file.  i did see something about somebody added a separate boot partition before the windows partition which then followed with the rest of ubuntu and it solved the dual boot probs. so i just moved my windows partition 200 mb to the right, not going to bother with the rest today.  but not being able to boot from the 20 gig is puzzling.  grub does load, it just errors out.  
  i'm not going to stop tryin'.;-)
any ideas?
thanks,

-S
If you moved your Windows partition to the right, unfortunately I don't think you will be able to boot it again without fixing its boot sector and changing some of the values in its registry. But don't panic, in the meantime you can probably access all your files in Windows from say the Ubuntu Live CD just fine. Do you get that Grub error 15 before seeing a Grub menu, or after you choose to boot Ubuntu? How about from your Live CD, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
And we can go from there.

---

### Post by stackbaxter on 2008-11-28
> **caljohnsmith said:**
> If you moved your Windows partition to the right, unfortunately I don't think you will be able to boot it again without fixing its boot sector and changing some of the values in its registry. But don't panic, in the meantime you can probably access all your files in Windows from say the Ubuntu Live CD just fine. Do you get that Grub error 15 before seeing a Grub menu, or after you choose to boot Ubuntu? How about from your Live CD, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
And we can go from there.

okay, Here's what i got:

Disk /dev/sda: 20.4 GB, 20491075584 bytes
255 heads, 63 sectors/track, 2491 cylinders, total 40021632 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfc60fc60

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      787184      393561   83  Linux
/dev/sda2          787185    40017914    19615365    5  Extended
/dev/sda5        38266893    40017914      875511   82  Linux swap / Solaris
/dev/sda6          787311    38266829    18739759+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *      417690   303451784   151517047+   7  HPFS/NTFS
/dev/sdb2       303451785   606887504   151717860    5  Extended
/dev/sdb3       606887505   625137344     9124920    7  HPFS/NTFS
/dev/sdb5       303451848   440486234    68517193+  83  Linux
/dev/sdb6       594742428   606887504     6072538+  82  Linux swap / Solaris

I can tell just by looking at it that things are screwy, but i can't seem to figure out how to fix them.  I'm also not sure why it calls the hd that came with the machine "b" and the one i added "a", jumpers maybe. 

i also get the "error 15" before a grub menu, and the windows partition didn't mind getting moved too much, i wasn't sure what to expect, but it handled it alright. :guitar:

-S

---

### Post by caljohnsmith on 2008-11-29
How about doing the following from the Live CD:
```
sudo grub
grub> root (hd0,0)
grub> makeactive
grub> setup (hd0)
grub> quit
```
Please post the output of all the above commands, and then do:
```
sudo mount /dev/sda1 /mnt
gksudo gedit /mnt/grub/menu.lst
```
And make sure the "hiddenmenu" line near the top of the file has a pound sign in front of it:
```
#hiddenmenu
```
Also make sure that your Ubuntu entries in that menu.lst either use a "uuid" line similar to:
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
[COLOR="Blue"]uuid		d0b10c15-66ed-4d1c-b7f6-c1fc131636f7[/COLOR]
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d0b10c15-66ed-4d1c-b7f6-c1fc131636f7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet
```
Or if they don't have a uuid line and instead use "root (hdX,Y)", make sure the (hdX,Y) is (hd0,0). Then reboot, make sure your BIOS is set to boot the 20 GB sda drive, and let me know what happens.

---

### Post by stackbaxter on 2008-11-29
> **caljohnsmith said:**
> How about doing the following from the Live CD:
```
sudo grub
grub> root (hd0,0)
grub> makeactive
grub> setup (hd0)
grub> quit
```
Please post the output of all the above commands,

There was no output, it just hard returned; skipped a line.

> **caljohnsmith said:**
>  and then do:
```
sudo mount /dev/sda1 /mnt
gksudo gedit /mnt/grub/menu.lst
```
And make sure the "hiddenmenu" line near the top of the file has a pound sign in front of it:
```
#hiddenmenu
```
Also make sure that your Ubuntu entries in that menu.lst either use a "uuid" line similar to:
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
[COLOR="Blue"]uuid		d0b10c15-66ed-4d1c-b7f6-c1fc131636f7[/COLOR]
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d0b10c15-66ed-4d1c-b7f6-c1fc131636f7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet
```
Or if they don't have a uuid line and instead use "root (hdX,Y)", make sure the (hdX,Y) is (hd0,0). Then reboot, make sure your BIOS is set to boot the 20 GB sda drive, and let me know what happens.

this is the output from the "menu.lst"

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		ef652e09-8623-4e8b-a093-7a832eae3a4b
kernel		/vmlinuz-2.6.27-7-generic root=UUID=b0dcecad-18a3-45b7-98c2-e7eef289ca67 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ef652e09-8623-4e8b-a093-7a832eae3a4b
kernel		/vmlinuz-2.6.27-7-generic root=UUID=b0dcecad-18a3-45b7-98c2-e7eef289ca67 ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ef652e09-8623-4e8b-a093-7a832eae3a4b
kernel		/memtest86+.bin
quiet

and when booted from the 20 gig (sda) still the error 15,

-S

---

### Post by stackbaxter on 2008-11-29
\\:D/
it works! thanks abound!

i did the makeactive bit again and it almost booted but dumped into a shell saying it couldn't find the root.  so i figured i was very close and reinstalled from the live cd manually partitioning the boot at the beginning, root in the middle, and swap at the end, and i think the difference was that i formatted them.  and voila!  

thanks again,

-S

---

