---
title: "GRUB Err 21 : Cant boot without my USB drive turned ON !!!"
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by Xenus98 on 2005-10-18
Hi all,

So here is my actual problem, and not the last one for sure... ;)

I managed to do this on my laptop. I have Windows XP on my internal HDD.
I did installed Ubuntu on my EXTERNAL USB HDD.
Then, rebooting, it was impossible to boot Ubuntu as GRUB could not find the USB drive.

For sure, GRUB was installed on my internal HDD.

I managed to use mkinitramfs to create a new initrd boot image and make finally the things work OK.

Only one bad point left, it's not possible to boot WindowsXP anymore without the External Usb drive connected...  I guess Grub is missing some file when the USB drive is not turn on. I have actually only one NTFS partition on my internal drive. I am looking for the easiest solution. 

I am actually looking after GAG boot loader solution, but it' need me to install lilo on the USB Ubuntu drive partition, getting ride of GRUB...

Any solution with GRUB ? It's so look like not so much is missing to make it work with GRUB... 

Any help is welcome.


Good luck.

---

### Post by CrunchyDoodle on 2005-10-18
I am an ubuntu novice trying to get my USB drive to boot ubuntu while leaving my notebook internal drive unmodified, even with GRUB. I am getting there, but still have a problem you may have solved. I now know I need to use mkinitramfs to create a new initrd boot image with /dev/sda1 in it so my USB drive will get mounted during GRUB's kernel command. I will be studying how to do that today. It seems to me that during the install, that should have been done for me. Maybe that's a bug.

To keep GRUB off my XP drive, it is easier to just remove the XP drive from the notebook and install ubuntu on the USB drive. I have the BIOS boot order as Removable Media, CD-ROM, Hard Drive. So if I can get an initrd image with /dev/sda1 in it, I'll have a totally stand-alone ubuntu bootable USB drive, just like that commercial product I've seen.

There is another message thread in this forum on this subject from yesterday.

Bye.    :cool:

---

### Post by Xenus98 on 2005-10-18
Hi !

Listen found a GREAT solution for my problem and may be yours a bit... :)
So, if you remember, having GRUB on my internal HDD, if my external USB HDD containing ubuntu was not turn on, then GRUB was not able to load completly...

Here is the great solution, the idea is to dump the boot sector where GRUB is (as GRUB can load my linux USB HDD correctly when the HDD is there) into a FILE !
Then, restoring the standard boot loader of Windows XP, to ask him to load the GRUB boot loader when needed ! !! ! !  

How to ?
Dump the boot sector of GRUB (once it is correctly working) :

=> "dd if=/dev/hda of=/boot/ubuntu_boot_sector.bin bs=512 count=1"

if value is the source drive
of value is the destination file you want to dump the boot sector in

find a way to bring this file (by email, or by a usb key...) to your NTFS Windows XP file system. Mean, bring on the C: drive...

Once it is on C: (example : C:\ubuntu_boot_sector.bin)
edit your boot.ini file from within WindowsXP : My computer / Properties / Advance panel / Start configuration... something like this - last button choice / then on the new pop up panel click edit boot.ini ...

A notepad window should open with the boot.ini file in it.

Add the following line : 

C:\ubuntu_boot_sector.bin="Start Linux Ubuntu"

And that is all ! ! ! ! No Linux partition on my Internal HDD ! ! 
It's even funny, because the boot loader of windowsXP can boot the boot loader of ubuntu... that can then... also boot the windows XP boot loader again... and again...and again... depending on your GRUB menu options... ;)

And if my HDD usb drive is not online, the boot loader of WinXP doesnt care at all ! :) :)

Et voilà !

hope it's help some people !
I have Ubuntu on my external USB HDD  booting via window XP boot loader !! :)

Thanks the internet for all the different infos I found out to make this possible.
:razz: :smile: :D

---

### Post by skoal on 2005-10-18
"*I guess Grub is missing some file when the USB drive is not turn on*."

I believe that's the case here. I might have an "easier" solution (if possible to do so).  

**Problem**:

Even though grub was installed in your MBR on internal drive, it still needs to find the 'stage1_5' and 'stage2' files. I believe 'stage1' (which is exactly 512 bytes = the size of MBR) needs to know where those other stage files are.  Those are under the /boot/grub path.  *Therefore, if you've installed the /boot partition on the USB drive, Grub probably pukes error doohickeys all over your screen because it can't find those other stage files on your USB drive*.
[B]
Possible Solution[/B]:

Create a seperate /boot partition on your *internal* hdd.  You only need ~32MB if using an ext3 filesystem.

* That solution can be tricky in actual implementation of an existing installation though. Why? The /boot partition (sometimes) needs to fall under the 8GB limit for some older BIOSs, so you would need it at the beginning before all other partitions.  *That shouldn't be a problem in most cases*. It should just be a simple matter of resizing the *last* partition on your internal hdd, making room for at least ~32MB.

example:

hdd - MBR
hda1 - NTFS (XP), 30 GB
hda2 - /boot, 32 MB, ext3

and usbdd has whatever Ubuntu partitions on there...

usbdd1 - / 
usbdd2 - /home
et cetera...

You would need gparted (recommended over others) to try this.  It handles NTFS resizes quite well per my understanding.  You could always resize that last partition on your hdd if this doesn't solve your problem too. *Please understand what gparted does first and the associated risks (if any)*...

\\//_

---

