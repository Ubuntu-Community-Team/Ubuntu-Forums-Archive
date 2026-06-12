---
title: "[SOLVED] trouble with install on a flash drive"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by Matrimforever on 2008-08-15
Hi,

I have a couple questions about Ubuntu 8.04 on a flash drive:
1)How do you, or how can you make it so its portable? Meaning, how can i use Ubuntu on any computer, or is that how it works already? I have it installed on the flash drive already, so I've gotten that far...
2)If it is set up that way, why does it not work on my Vista comp? I changed the boot sequence to have the flash drive boot first, but it just skips it and goes on to load Vista.
3)On the original computer I had it installed on, the computer hangs after it finds the boot image on the flash drive. What could cause that? Does it mean that the comp may not be able to boot that way? 

Thanks guys,
Matrim - new to Ubuntu and flash drive linux, but not Linux in general :)

---

### Post by Pumalite on 2008-08-15
You may find your answers here:
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

---

### Post by Matrimforever on 2008-08-15
Thanks for the links.

About how long does it take for a flash drive to boot up? I can't tell cuz mine always hangs after boot record is found...

---

### Post by Matrimforever on 2008-08-15
> **Matrimforever said:**
> Hi,

3)On the original computer I had it installed on, the computer hangs after it finds the boot image on the flash drive. What could cause that? Does it mean that the comp may not be able to boot that way? 


Still can't get it boot from USB. The image is found, then it hangs. What could be wrong?

---

### Post by Pumalite on 2008-08-15
Whar is your exact error message?

---

### Post by Matrimforever on 2008-08-15
There isn't one. After I install everything, it attempts to reboot. It hangs on the reboot message: "Searching for Boot Record from USB RMD-FDD..OK"

So it finds the boot record, but then it just hangs there.

---

### Post by Pumalite on 2008-08-15
Where did you install Grub?

---

### Post by Matrimforever on 2008-08-15
Under 'Advanced' I selected to have the bootloader put on the flash drive, but no mention of GRUB. I assumed the 'bootloader' was GRUB.

---

### Post by Pumalite on 2008-08-15
Post your flash drive's menu.lst

---

### Post by Matrimforever on 2008-08-15
Now THAT i don't know how to do :)

---

### Post by Matrimforever on 2008-08-15
Do I use LiveCD to boot up, then get into the flash drive that way?

I have no idea:(

---

### Post by Matrimforever on 2008-08-16
Okay, so I was able to boot up using the LiveCD and check flash drive. There are a few files with menu.1st. Here is the main one? : 
```


title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f4558e42-234a-47d7-8fe9-5e2cd0883bd5 ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f4558e42-234a-47d7-8fe9-5e2cd0883bd5 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1

```

This was on the grub-menu.lst file: 
title  memtest86+
root   (hd0,0)
kernel /boot/memtest86+.bin

---

### Post by Pumalite on 2008-08-16
Edit menu.lst of the Flash Drive and change 'groot' and 'root' to (hd0,0)

---

### Post by Matrimforever on 2008-08-16
Won't let me save the changes due to permissions?

I could open a terminal under superuser but i dont know a password for the LiveCD.

---

### Post by Pumalite on 2008-08-16
sudo chmod 777 /media/???...

---

### Post by Matrimforever on 2008-08-16
Okay, now what? Reboot...and pray? :popcorn:

---

### Post by Matrimforever on 2008-08-16
Well crud, I didn't pray hard enough. It still hangs ](*,)

---

### Post by Pumalite on 2008-08-16
Read carefully the link I gave you.

---

### Post by Matrimforever on 2008-08-16
I've read that, that's where all my new questions came from :P.

Can you at least tell me where to look for groot? It wasn't in the same folder that menu.1st was found.

---

### Post by Pumalite on 2008-08-16
It's there. It's not menu.1st. It's menu.lst

---

### Post by Matrimforever on 2008-08-16
Ok, one last question before i throw my drive away:
When changing the root to hd0...if it's on my flash drive, shouldn't it be like sdb0 or something?

Okay I lied..one more: If you see the groot in the above code I posted it has a # in front of it. I'm assuming I need remove that? And there are 3 or 4 places where root is, am I to change all to hd0,0?

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f4558e42-234a-47d7-8fe9-5e2cd0883bd5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
 groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash xforcevesa

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f4558e42-234a-47d7-8fe9-5e2cd0883bd5 ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)

root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f4558e42-234a-47d7-8fe9-5e2cd0883bd5 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1

```

---

### Post by Pumalite on 2008-08-16
Leave # in front of 'groot'. All 'root' must be changed to (hd0,0)

---

### Post by Herman on 2008-08-17
Some computers are able to boot a USB device and other computers just can't. 
It depends on features built into the motherboard and BIOS. 
Normally, computers that are capable of booting a USB have a boot menu in their BIOS that you can access by pressing the F12 key in an early stages of booting. [How I boot from my BIOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#How_I_boot_from_my_BIOS_with_my_F12_key") with my F12 key (or F8 key in most PCs).

The most common mistake almost everyone makes if they aren't used to installing in a USB is they allow GRUB to be installed to the MBR of their first hard disk, which most often means their computer's internal hard drive. You need to make sure GRUB is installed to MBR in the USB. My computers normally start numbering any USB devices after all the hard disks, but some computers BIOSes make the USB drive number 1 instead, just to make things even more interesting. 
       
Try to determine if it's the computer or the USB that has a problem.
You might try to boot your USB in some different computer and see if it will work. 
Try booting some other bootable USB in the computer you have and see if some other bootable USB can boot.

Try making yourself a [Super Grub Disk]("http://www.supergrubdisk.org/") and you will have a choice of two ways you can use it.
One way is to use the Super Grub Disk menus and find a way to boot your USB.
Another way is to press your 'c' key from a menu in Super Grub Disk for [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and then try to boot Ubuntu from there. There are three different ways we can use GRUB to boot Linux: [Direct (kernel) Boot]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot."), [Configfile Boot]("http://users.bigpond.net.au/hermanzone/p15.htm#Second_method_configfile_boot"), or [Chainloader Boot]("http://users.bigpond.net.au/hermanzone/p15.htm#Third_method_chainloader_boot").

Booting from (or trying to boot from Grub's command line is not only one of the best and surest ways to boot (it has the advantage of tab completion), but also since GRUB's command line interface provides feedback in the form of error messages, it is also the best way of troubleshooting why you can't boot.

I have a brand new Toshiba laptop here with Windows Vista in it I'm setting up for a friend and I tried to boot a Gutsy Gibbon USB to make a partimage backup of the partitions while they're new and clean, and make a 'dd' backup of the entire MBR. 
My Gutsy USB would only half boot and then stop. The latest Hardy Heron 8.04.1 'Desktop' Live CD did the job though. That took some time to boot and after booting I saw a message that it had to download some special drivers from the internet. I probably didn't have the internet connected earlier or else Gutsy Gibbon might not have been quite modern enough for the brand new hardware. Make sure you're running the very latest Ubuntu 8.04.1  Maybe your nice new modern hardware is a little ahead of its time and Linux hasn't quite caught up with it yet. 

Another possibility too, maybe you need to run a file system check, that's another idea that might do the trick for you, [Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem").

Regards, Herman :)

---

### Post by Matrimforever on 2008-08-17
Hi Herman,

I've tried to boot in different comps, same thing happens: finds the boot record then hangs(both are able use an usb to boot). I've also tried 2 different flash drives, each doing the same thing.

With respect to MBR, I'm almost positive I put in on the right drive. It should be sdb because thats where it was installed to, but now I've been told it should be hd0, so I'm a little confused.

It must be just whats on the drive, because everything else looks okay. You want me to list my choices when selecting where the bootloader goes?

---

### Post by Green Tree Python on 2008-08-17
I installed 8.04 on a 2GB flash drive, by downloading the iso image then burning the iso to a CD. Then i copied the files to the flash drive. It works great.

Good luck,

GTP

---

### Post by Matrimforever on 2008-08-17
That's all you did? Copy paste from CD? In Windows?

---

### Post by Matrimforever on 2008-08-17
> **Matrimforever said:**
> Hi Herman,

You want me to list my choices when selecting where the bootloader goes?

Do I even need a bootloader, if i tell the bios to boot from usb?

---

### Post by Herman on 2008-08-17
> Do I even need a bootloader, if i tell the bios to boot from usb? 	 Yes, you do need a boot loader somewhere.
If you didn't have a boot loader in the USB you could boot with GRUB from a CD or a floppy disk. or if you had GRUB in an internal hard disk you could boot Ubuntu directly from that, but you need a boot loader somewhere.
> That's all you did? Copy paste from CD? In Windows? 	Well, you *can* copy and paste the files from a CD into a partition and boot it as  Live CD, and you can install Ubuntu with it too, you would need a boot loader to boot it, but it will work if you do it right.
Here's a how-to about that, [Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux").
The only trouble with that is it behaves exactly like a live CD, that is, you can't save any files or settings in it for longer then one session. Every time you reboot it forgets everything.

If you want to do something along the same lines, you can do a [Pendrive Linux]("http://www.pendrivelinux.com/") type of installation in your USB, which involves making an extre partition and naming the file system in it 'casper-rw'. There are special boot options fro booting the kernel and there's a specail initrd.img you download, it is claimed to reduce the number of writes to the flash memory and so is supposed to make the flash memory last longer. 

The simplest way to do it is just to install to the USB by running the Ubuntu installer the same way you install to any other hard disk. 
One advantage of that is obvious, it's fast and simple and saves a lot of work. 
Another advantage is, if you plug another USB flash memory in beside it it can access the other USB drive in the normal way, so you can use it as a rescue disk especailly if the other USB disk is an external hard disk drive with lots of GB of room for files. 
If you are travelling light and rough, you might have a bank of other flash memory sticks plugged into the same hub and your Ubuntu USB will be able to use a lot more space that way. They'll all fit in your pocket.
A possible disadvantage of the simple installation in a USB flash memory is that some people claim it will shorten the life of the flash memory. I don't know if that's true or not yet because so far none of my USB flash memory sticks have worn out yet. Maybe I'm not using them enough because I have hard drive installations I can use most of the time. Only two people have reported their flash memories have worn out and neither of those can clearly attribute it to having Ubuntu installed in them, it could be that the sticks were just old and/or of poor quality.

The easiest way to install Ubuntu is to install it in an internal hard disk though. That's what it's mainly made for. 
> I've tried to boot in different comps, same thing happens: finds the boot record then hangs(both are able use an usb to boot). I've also tried 2 different flash drives, each doing the same thing.

> With respect to MBR, I'm almost positive I put in on the right drive. It should be sdb because thats where it was installed to, but now I've been told it should be hd0, so I'm a little confused.It's normally the last hard disk in my computers, so if the computer only has one hard disk, /dev/sda then the USB will be /dev/sdb or hard disk number 2. Hwowever, some computers do things the other way around. You sometimes need to play around and to test your computer to see which way your computer is going to do it, (number the disks).
/dev/sda is the Linux equivalent of GRUB's (hd0), meaning hard disk number 1.
/dev/sdb is the Linux equivalent of GRUB's (hd1), meaning hard disk number 2.
Your flash memory should be one of those if your computer only has one hard disk. If you're watching when you go through the partitioning disks part of the installation the installer tells you which hard drive it considers to be /dev/sda and which is /dev/sdb. Most people don't realize at that stage that information will be important later on when it's time to install the boot loader and by then they can't remember.
> It must be just whats on the drive, because everything else looks okay. You want me to list my choices when selecting where the bootloader goes?No, that shouldn't be necessary.
Just tell me what happens when you get any GRUB disk, [Super Grub Disk]("http://www.supergrubdisk.org/") is normally the easiest, and press your 'c' key for [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and do a [Direct (kernel) Boot]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot.").
What error messages do you get then or what happens?

---

### Post by Matrimforever on 2008-08-18
Again, thanks for the help. It is much appreciated.

After connecting my hard drive with windows on it, and having no other ubuntu, I attempted to boot into Vista. Low and behold, GRUB shows up and throws an error 21(not sure what it is, but it hangs there). 

So I'll download your suggestion on GRUB and see what it does and report back.

---

### Post by Green Tree Python on 2008-08-19
Thats all i did, and yes i used Windows. I havent that the chance to make the switch yet. You save the GRUB to the flash drive along with the install files. As always make sure the flash drive is at least 2GB.

Good luck,

GTP

---

### Post by Matrimforever on 2008-08-27
> **Herman said:**
> 
No, that shouldn't be necessary.
Just tell me what happens when you get any GRUB disk, [Super Grub Disk]("http://www.supergrubdisk.org/") is normally the easiest, and press your 'c' key for [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and do a [Direct (kernel) Boot]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot.").
What error messages do you get then or what happens?

Okay I took a break for a bit, and now am back. I really want to get this running so if you will bare with me I'd appreciate it. I ran supergrub disk, but it never found the usb flash drive, so I'm reinstalling it on to the flash drive...

---

### Post by Matrimforever on 2008-08-27
Im at the end of the installation instructions and under Advanced it gives you a choice of boot loader option. Which one should i choose?? I have 1 win vista hard drive and 1 flash drive with which i have ubuntu installed. Do I put it under the flash drive or hard drive? This is where i think i went wrong in the first place so plz reply :/

---

### Post by Matrimforever on 2008-08-27
Quote:
Originally Posted by Herman > 
No, that shouldn't be necessary.
Just tell me what happens when you get any GRUB disk, Super Grub Disk is normally the easiest, and press your 'c' key for GRUB's Command Line Interface and do a Direct (kernel) Boot.
What error messages do you get then or what happens?

I have supergrub running, and it doesn't even recognize the flash disk as a partition/drive, so it wont let me do a direct boot, because it can't find it to boot to!

---

### Post by Herman on 2008-08-28
> Im at the end of the installation instructions and under Advanced it gives you a choice of boot loader option. Which one should i choose?? I have 1 win vista hard drive and 1 flash drive with which i have ubuntu installed. Do I put it under the flash drive or hard drive? This is where i think i went wrong in the first place so plz reply :/You would install Ubuntu's GRUB to MBR in the flash memory stick.
Sorry for the lateness of my reply.
> I have supergrub running, and it doesn't even recognize the flash disk as a partition/drive, so it wont let me do a direct boot, because it can't find it to boot to! Does your computer even recognize your USB flash memory stick as a device you can boot? Try booting the flash memory directly from your BIOS boot menu, [How I boot from my BIOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#How_I_boot_from_my_BIOS_with_my_F12_key") with my F12 key (or F8 key in most PCs).
If you can't boot it directly from your BIOS, chances are you might not have a suitable computer for USB booting. Try a different computer.

---

### Post by Matrimforever on 2008-08-28
> **Herman said:**
> You would install Ubuntu's GRUB to MBR in the flash memory stick.
Sorry for the lateness of my reply.
 Does your computer even recognize your USB flash memory stick as a device you can boot? Try booting the flash memory directly from your BIOS boot menu, [How I boot from my BIOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#How_I_boot_from_my_BIOS_with_my_F12_key") with my F12 key (or F8 key in most PCs).
If you can't boot it directly from your BIOS, chances are you might not have a suitable computer for USB booting. Try a different computer.

Thanks again for the replies and being patient with me. The computer does recognize it as: USB RMD-FDD:USB 2.0 Flash Disk. 

So I'm wondering why supergrub can't see it? It sees the other hard drive easy enough.

I booted directly into the drive(for me it f11) but once again after:
'Searching for Boot Record from USB RMD-FDD..OK'
it hangs there:(.

ps. ive tried it in a laptop as well with the same results :(
So I think:
1. I've installed the wrong ubuntu for a flash drive
2. Something goes wrong with my installation...every time
3. I need to install it on an internal hard drive :( (the whole purpose to have it in a jump drive was to be portable.)
4. I need to do what is says here: [http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)

The only thing I can think of is that it is hanging because of GRUB, but I reinstalled several times and it still hangs there.

---

### Post by Matrimforever on 2008-08-28
Would it have anything to do with permissions? 
When i boot with the LiveCD and try to change anything on the usb that has Ubuntu on it wont let me unless I do it in terminal...

---

### Post by Matrimforever on 2008-08-28
Sorry if I'm sort of spamming questions here.
I did try it in a laptop that was not tried before, and GRUB actually loaded, but threw a error 23. Maybe if i can fix that, it will load properly on the desktop. But how to fix...

---

### Post by Herman on 2008-08-29
If you typed something into your /boot/grub/menu.lst file in Ubuntu in your flash memory drive then maybe you typed a letter 'O' instead of a number '0' (zero) somewhere in your booting stanza. [Grub error 23]("http://users.bigpond.net.au/hermanzone/p15.htm#23").

Just keep trying, you'll get there eventually.

It is generally much, much easier to just install Ubuntu in an internal hard drive in your computer, and better too. :)

---

### Post by Matrimforever on 2008-08-29
Yes, but its not as portable either :(. I'm going to look at the menu.lst again, but I'm fairly certain it says hd0 and not hdO. If thats the case what's next on the list to check? :)

---

### Post by Herman on 2008-08-29
> what's next on the list to check?
Well, really we should have started with the output from 'sudo fdisk -lu', 
```
sudo fdisk -lu
``` if you can run the Ubuntu Live CD and run that command in the terminal and post the output here it might help.

---

### Post by Matrimforever on 2008-08-29
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x15ce15cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   102402047    51200000    7  HPFS/NTFS
/dev/sda2       102402048   184322047    40960000    7  HPFS/NTFS
/dev/sda3       184322048   312578047    64128000    7  HPFS/NTFS

Disk /dev/sdc: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d9f12

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    14924384     7462161   83  Linux
/dev/sdc2        14924385    15695504      385560    5  Extended
/dev/sdc5        14924448    15695504      385528+  82  Linux swap / Solaris

```

ps. i get a new error now on the laptop(i guess something on my desktop wont let me use grub correctly): Error 17: unable to mount partition

---

### Post by Herman on 2008-08-29
:) Okay, your fdisk output looks alright. The only unusual thing I noticed about it is that you have a number 1 hard disk (your computer's internal hard disk), and a number 3 hard disk, (your flash memory stick), but no number 2 hard disk. At least not according to Linux.

I wonder what GRUB thinks your flash memory MBR is?

Try booting your Ubuntu CD and doing 'sudo grub', (for a grub shell).
```
sudo grub
```
Then, enter a 'find' command, such as,
```
find /vmlinuz
```
or 
```
find /boot/grub/stage2
```
Those should return an answer like '(hd1,0)', or (hd2,0) or something similar. :)

---

### Post by Matrimforever on 2008-08-29
Okay that returns (hd1,0)

this is my menu.lst again:
```

//snip
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

//snip
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=dfda6251-3150-4fa9-813c-959bdd002458 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=dfda6251-3150-4fa9-813c-959bdd002458 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1
``` Does that look right?

---

### Post by Herman on 2008-08-29
That should be okay, (normally), now, with your Ubuntu Live CD running, open a GRUB shell in your terminal again,
```
sudo grub
```Now we're going to re-install GRUB to MBR in your USB flash memory disk again just to make sure,
```
root (hd1,0)
```
```
setup (hd1)
```now we'll install GRUB to your Ubuntu boot sector as well to make doubly sure,
```
setup (hd1,0)
```Please note any error messages you may see.
It is normal to see an error message when installing GRUB to a partition boot sector, something about not being able to install stage1_5, ignore that one. If you can't install GRUB to MBR in the flash memory though, I'll be interested to know why not.

---

### Post by Matrimforever on 2008-08-29
Okay I ran everything, and other than the 'failed' stage1_5 it 'succeeded' on both counts. No other error messages.

---

### Post by Herman on 2008-08-29
Good okay then, now we should be able to boot your USB flash memory from your Super Grub Disk CD either at the USB disk's Master Boot Record or at the first sector of your Ubuntu partition.
Boot your Super Grub Disk CD and press your 'C' key from a menu so you'll have [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").
Type the following commands,
```
root (hd1)
```
```
chainloader +1
```
```
boot
```Does GRUB in your flash memory stick appear and boot Ubuntu for you?
If not, what error message do you get?

...and if that one doesn't work, try this instead,
```
root (hd1,0)
```
```
chainloader +1
```
```
boot
```That should boot Ubuntu's GRUB from the boot sector, and Ubuntu's GRUB sould boot Ubuntu. If not, what error messages do you see, or what happens?

---

### Post by Matrimforever on 2008-08-30
> **Herman said:**
> 
If not, what error message do you get?
```
root (hd1)
```

Error: Filesystem type unknown using whole disk
> 
```
chainloader +1
```

Error: Invalid or unsupported executable found

> 
...and if that one doesn't work, try this instead,
```
root (hd1,0)
```
Filesystem type is ext2fs, partition type 0x83
> 
```
chainloader +1
```

Error: Invalid or unsupported executable found

As a side question:

1. On my desktop, the USB shows up in the bios and boot menu, but with Supergrub it does not. On my laptop with Supergrub it shows up. Why if it is detected on the desktop, would it not show up in  SuperGrub?

2. What's next? :popcorn:

---

### Post by Herman on 2008-08-30
> 1. On my desktop, the USB shows up in the bios and boot menu, but with Supergrub it does not. On my laptop with Supergrub it shows up. Why if it is detected on the desktop, would it not show up in SuperGrub?I don't know, it depends on the BIOS in the computer. 
> 2. What's next? We will try to boot the kernel directly from Super Grub Disk's GRUB. That will bypass the flash drive's MBR and GRUB in Ubuntu in the flash memory too, and just boot the kernel by symlinks, (shortcuts). That should boot it if there is something wrong with GRUB in the flash memory stick or with the memory stick's MBR.

Boot your Super Grub Disk CD, and press your 'c' key from a menu to change into  [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") again.
This time type the following comands,
```
root (hd1,0)
```
```
kernel /vmlinuz root=/dev/sdc1
```
```
initrd /initrd.img
```
```
boot
```

---

### Post by Matrimforever on 2008-08-30
> **Herman said:**
> Good okay then, now we should be able to boot your USB flash memory from your Super Grub Disk CD either at the USB disk's Master Boot Record or at the first sector of your Ubuntu partition.
Boot your Super Grub Disk CD and press your 'C' key from a menu so you'll have [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").
Type the following commands,
```
root (hd1)
```
```
chainloader +1
```
```
boot
```Does GRUB in your flash memory stick appear and boot Ubuntu for you?
If not, what error message do you get?

...and if that one doesn't work, try this instead,
```
root (hd1,0)
```
```
chainloader +1
```
```
boot
```That should boot Ubuntu's GRUB from the boot sector, and Ubuntu's GRUB sould boot Ubuntu. If not, what error messages do you see, or what happens?

> **Herman said:**
> I don't know, it depends on the BIOS in the computer. 
 We will try to boot the kernel directly from Super Grub Disk's GRUB. That will bypass the flash drive's MBR and GRUB in Ubuntu in the flash memory too, and just boot the kernel by symlinks, (shortcuts). That should boot it if there is something wrong with GRUB in the flash memory stick or with the memory stick's MBR.

Boot your Super Grub Disk CD, and press your 'c' key from a menu to change into  [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") again.
This time type the following comands,
```
root (hd1,0)
```
```
kernel /vmlinuz root=/dev/sdc1
```
```
initrd /initrd.img
```
```
boot
```

Okay we have success!! There were a few errors, such as not reading a memory address correctly, or two, but essentially it booted up into the login screen.

Does this mean im stuck using supergrub? or is there a way to fix it so i can take it with me and/or use it without a CD everytime?

---

### Post by Herman on 2008-08-30
> There were a few errors, such as not reading a memory address correctly, or two, but essentially it booted up into the login screen.
Flash memory uses some extra tricks to fool the operating system into thinking it's dealing with a hard disk, while at the same time juggling the data around for 'wear levelling'. (so the flash memory doesn't wear out just in one or two cells which might happen to get written to frequently.
It could be that there's a problem with the way your particular flash memory is working.
It could be that GRUB and Linux have the problem. GRUB and Linux can work on an amazing variety of different kinds of hardware, but maybe you were unlucky enough to find something it doesn't work in very well.

Is your memory stick very new or very old? 
Is it a well known brand?
> Does this mean im stuck using supergrub? or is there a way to fix it so i can take it with me and/or use it without a CD everytime?Time will tell.
I don't know, it looks like you will need to keep using a GRUB CD of some kind for now. If you want you can make your own customized GRUB floppy disk or CD. [How to make your own personalized GRUB CD-RW]("http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD").

It might be a good idea to try running a file system check from your Ubuntu Live CD.
You just open a terminal and type a command like this one,
```
sudo e2fsck C0 -p -v -f /dev/sdc1
```[Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem")
A file system check might help and won't hurt, aprat from possibly wasting a few minutes of yout time. Usually it's a good idea to run a file system check anyway, so it won't really be a waste of time.

Apart from that, at least you know that your computer can do it and you know how to do it, maybe try with a different flash memory and see if it's the memory stick that is the problem.

---

### Post by Matrimforever on 2008-08-31
> **Herman said:**
> 

Is your memory stick very new or very old? 
Is it a well known brand?

I tried 2 different ones with the same amount of memory. One is a new Sandisk Cruzer Micro so that should be fine.
> 
I don't know, it looks like you will need to keep using a GRUB CD of some kind for now. If you want you can make your own customized GRUB floppy disk or CD. 
I don't suppose I could have supergrub on the flashdisk im running eh?

> It might be a good idea to try running a file system check from your Ubuntu Live CD.

I'll do that, thanks for all the help. I'm still sad I can't get it to work in my desktop, but I do know that it works with other comps. 

ps. now that its up and running I'll need help with setting up wireless internet on the laptop, can you direct me to where I can go for that? :popcorn:

---

### Post by Herman on 2008-08-31
> I tried 2 different ones with the same amount of memory. One is a new Sandisk Cruzer Micro so that should be fine. I have two of those, both 8.0 GB, they work okay for me. One has Ubuntu installed in it and I haven't had any problems with it except Ubuntu seems to run very slowly in it. The other is just for data.
I have other USBs that Ubuntu runs much faster in. Maybe the SanDisk Cruzer USBs will last longer instead though, maybe it's doing more 'wear levelling' in the background or something like that. They're supposed to be pretty good, (at least according to their own documentation). :)
> I don't suppose I could have supergrub on the flashdisk im running eh?Yes, you can, and it's a great idea, providing your computer can boot either the MBR or a boot sector in the USB in order to boot [Super Grub for USB]("http://www.supergrubdisk.org/index.php?pid=7").
[How to Make your Super Grub USB Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Super_Grub_USB_Disk").
I think the easiest way for you would be to make some space at the end of the disk for a partition for Super Grub Disk, since Linux partitions are easy to resize from the end. It doesn't make any difference at all where a partition is located on a disc, it will still work the same. I don't understand why your computer failed to boot the USB either by the MBR or a boot sector, but you might learn more by experimenting, and Super Grub Disk for USB should help you to do that. :)
You had 'Error: Invalid or unsupported executable found' for both the MBR and a boot sector, even though you just installed GRUB to both of those. I wonder what the exact problem is there? Definitely keep experimenting and you should be able to pin-point the source of your trouble.
I'll keep helping you if you want.

Maybe it only needs a common file system check. 
Maybe the stage2 file of GRUB (the one that does most of the work), is corrupted somehow. You can try deleting it, (you can boot directly with Super Grub Disk's GRUB (stage2), and the grub-install command in Ubuntu will give you a new stage2 file in Ubuntu. That's the way to fix it if you have a corrupted stage2 and a file system check doesn't fix it.

> ps. now that its up and running I'll need help with setting up wireless internet on the laptop, can you direct me to where I can go for that? A command for finding out what network card(s) you have would be,
```
sudo lshw -C network
```Armed with that information you can go and search for threads in the [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") section of Ubuntu Web Forums or everywhere in the forums. I have a laptop with wireless networking, I had it working in a previous version of Ubuntu but I never use wireless networking, just ethernet so I haven't bothered to learn very much about it. There are some other people here who are experts on networking. :)

---

### Post by Matrimforever on 2008-08-31
Having some issues with my other USB from A-data(do you think my desktop can't read that high a flash drive to boot it up?). Got this error after running supergrub and booting:
```

Kernel panic: not syncing VFS: Unable to mount root fs on unknown block(0,0)
```

Also, with filesystem check wouldn't let me use the 'CO' part but it did without it, and I guess it ran ok.

---

### Post by Herman on 2008-09-01
> Also, with filesystem check wouldn't let me use the 'CO' part but it did without it, and I guess it ran ok. 	That's 'C0' (C zero), not 'CO' C Owe'. 
The 'C0' part is just to give you a progress bar so you can watch the file system check's progress, the file system check will run just as well without it.
> Having some issues with my other USB from A-data(do you think my desktop can't read that high a flash drive to boot it up?). Got this error after running supergrub and booting:
 	Code:
 	Kernel panic: not syncing VFS: Unable to mount root fs on unknown block(0,0) 
Check to make sure your 'root=/dev/sdc1' part of the kernel booting line is correct. Sometimes that can change, especially if you have different USB devices plugged in. In Ubuntu we use the file system UUID number there instead of the old '/dev/sdx,y' notation, but if you're booting from the command line, it would be some extra typing and you'd need to have the file system UUID copied dwon on a peice of paper, (unless you have a photographic memory, in which case you don't really need a computer). :)

---

### Post by Matrimforever on 2008-09-04
> **Herman said:**
> 

I think the easiest way for you would be to make some space at the end of the disk for a partition for Super Grub Disk, since Linux partitions are easy to resize from the end. It doesn't make any difference at all where a partition is located on a disc, it will still work the same. 


Can you help me with the repartioning? Is it possible to do without the LiveCD? I went ahead and put Ubu on my desktop with no problems(karma considered what pain i had with flash drive i guess), but can't find where to do it now.

ps. the partition to handle supergrub would be type fat32?

---

### Post by Matrimforever on 2008-09-04
Actually, i didnt have the repartioner installed, so got that in, and then repartioned , but not sure what filetype to use? Also, do I just copy the boot folder into the new partition? Then what?

---

### Post by Herman on 2008-09-04
> Actually, i didnt have the repartioner installed, so got that in, and then repartioned ,
:) Good.
>  but not sure what filetype to use?  Just about any file system will work, I prefer ext2, which is the same as ext3 but without the journal, so it saves a wee bit of disc space.
> Also, do I just copy the boot folder into the new partition? Then what?Yes, you copy the boot folder into the new partition, then you install GRUB to the USB disk's MBR, and/or to the boot sector of the new partition.
That's about the only operation that some people seem to find a little bit tricky, but there's no tricks in it really, as long as we use GRUB's 'find' command to check which disc/partition is which before we install Super Grub's GRUB it's easy. [How to Make your Super Grub USB Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Super_Grub_USB_Disk"). Also see: [How To: Make GRUB Thumb Driv]("http://kubuntuforums.net/forums/index.php?topic=3081748.0")e by Qqmike at Kubuntu Web Forums.

Later, you can add your own special booting stanza to the /boot/grub/menu.lst file in Super Grub Disc for USB for booting your Ubuntu in USB.

---

### Post by Matrimforever on 2008-09-05
I wanted to report that all is well with my USB, I still can't get sgd to work right, but i changed the menu.lst again for kicks and giggles since the laptop might sort the drives differently than the desktop to hd0 instead of hd1(like puma suggested earlier) and all is right with the world. I dunno what will happen if i use another computer, but for now i'm gold. 

I wanted to thank Herman and pumalite for their contributions as this must have been a long and tedious thread. Hopefully this has been solved and we can all move on to live long and fruitful lives. :lolflag:):P

---

