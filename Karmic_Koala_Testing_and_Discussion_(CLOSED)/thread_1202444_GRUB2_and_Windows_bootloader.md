---
title: "GRUB2 and Windows bootloader"
date: 2009-07-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bedbug on 2009-07-02
my root partition (/) is  /dev/sda5

df -Ph -text4
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              12G  2.6G  8.3G  24% /

I followed this guide: [https://wiki.ubuntu.com/KernelTeam/Grub2Testing](https://wiki.ubuntu.com/KernelTeam/Grub2Testing)
to update grub to grub2

I did sudo grub-install --force /dev/sda5
      sudo grub-setup --force /dev/sda5

and I copied  grub.bin to windows by
sudo dd if=/dev/sda5 of=grub.bin bs=446 count=1
sudo cp grub.bin /mnt/grub.bin 


Note : 
        I have mounted my windows /dev/sda1 in /mnt)
        My c:\boot.ini contains
[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
c:\grub.bin="GRUB"


after reboot I have got (since windows failed to understand grub 2 menu 
format ) 

grub>

in that i have to type 

grub> kernel (hd0,4)/boot/grub/core.img
grub> boot

to get my grub2 :p

Is their any other easiest way to accomplish this ?!

---

### Post by yelo3 on 2009-07-02
I think you have to install grub2 in /dev/sda, not in a partition

---

### Post by bedbug on 2009-07-02
I need/like to boot Linux using Windows bootloader

so  i have installed grub2 in /dev/sda5 (My root partition) and modified C:\boot.ini to suit my need.

all that I ask : _what I have to to make windows bootloader to understand the GRUB2 menu format ?_

---

### Post by dino99 on 2009-07-02
why don't you use the standard installation:

grub2 use grub on jaunty
os-prober find the others os

There is no problem: i use & boot on 3 hdd randomly (security if one hdd fail) , grub2 work with uuid: check fstab & mtab first (verify that last number (dump) in fstab fill the rules (1 boot partition, 2 swap & 0 for ntfs & others)

In my case, for windows i've added map fonction to jump from one hdd to an other automatically, and ended with chainloader +1.

That it):P

---

### Post by bedbug on 2009-07-02
it is simply  - **how to boot GRUB2 from BOOT.INI **

---

### Post by seeker5528 on 2009-07-02
> **bedbug said:**
> it is simply  - **how to boot GRUB2 from BOOT.INI **

I expect it is no different than it was in the past with earlier versions of Grub...... keeping in mind the process boils down to this simple list.

[list]Use 'dd' to create an image from the bootsector of the partition where you installed grub.[/list]

[list]Copy the created image to the root of your windows partition.[/list]

[list]Create an entry in boot.ini that points to that image.[/list]

Any complication outside of this would be booting from something where you can create the image, mounting your windows partition, etc....

[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)

If you have knowledge of command line stuff, ntfs-3g, etc... any live CD should do.

If you have less knowledge of these things you might prefer [RIP](http://rip.7bf.de/current/), which has a boot option to boot directly to X Windows, and in the X session has a menu option to mount/unmount partitions. Making it pretty simple to mount your windows partition, open a terminal window, use 'of=/mnt/*yourwindowspartition*/linux.bin' as the out file argument when creating the image.

Later, Seeker

---

### Post by bedbug on 2009-07-02
I _expect_ it is no different than it was in the past with earlier versions of Grub -** IT IS NOT SO**

I tried everything. I was successful only by typing at grub prompt the following: 

grub> root (hd0,4)
grub> kernel /boot/grub/core.img
grub> boot

REF: [http://grub.enbug.org/TestingOnX86](http://grub.enbug.org/TestingOnX86) (loading GRUB 2 by GRUB Legacy)

---

### Post by bedbug on 2009-07-03
I have created a _/boot/grub/menu.lst _contains

default         0
timeout		0
title		Chainload into GRUB 2
uuid		898110ac-93b3-44ab-866f-ae95ffdceaeb
kernel		/boot/grub/core.img

Now Grub2 works from boot.ini

---

### Post by seeker5528 on 2009-07-03
If you had to create a menu.lst file, then it sounds like Grub 2 is not working from boot.ini, grub-legacy is, which in turn is chain loading grub 2.

What happens if you copy the core.img file to your windows partition, then create an entry in boot.ini for it?

Later, Seeker

---

### Post by bedbug on 2009-07-06
**Another Solution: **

1._ backup MBR_
sudo dd if=/dev/sda of=~/mbr.img bs=512 count=1

2. _install GRUB2 _in MBR (/dev/sda)  & _modify boot.ini_
follow the guides : [https://wiki.ubuntu.com/KernelTeam/Grub2Testing](https://wiki.ubuntu.com/KernelTeam/Grub2Testing)
                   [http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)

3. _restore MBR_
sudo dd if=~/mbr.img of=/dev/sda bs=512 count=1

---

### Post by the.lost.one on 2009-10-16
> **bedbug said:**
> I have created a _/boot/grub/menu.lst _contains

default         0
timeout        0
title        Chainload into GRUB 2
uuid        898110ac-93b3-44ab-866f-ae95ffdceaeb
kernel        /boot/grub/core.img

Now Grub2 works from boot.ini


whats the uuid? how do i get mine?

did you also edited your boot.ini for this solution? how?

---

### Post by adder1972 on 2009-10-16
Here's how to identify the UUID of your partitions or disks:

ls -la /dev/disk/by-uuid

---

