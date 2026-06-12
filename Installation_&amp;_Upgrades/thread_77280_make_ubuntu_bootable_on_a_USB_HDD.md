---
title: "make ubuntu bootable on a USB HDD"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by ky4623 on 2005-10-16
hi
i want to make ubuntu bootable on a usd hdd, so i can used it on any laptop that supports usb boot. my usb hdd is 250gb. i read some of the posts and saw a possible solution:

1) Install from CD
2) After installation, leave CD in drive and reboot with the parameter rescue
3) Pick your language and country
4) Wait for hardware detection to complete(was quite long on my system, seemed stuck for a while)
5) hostname: Ubuntu <enter>
6) Device to mount as root file system: /dev/discs/disc0/part2 (this may be different on your system. I have a boot partition in part1)
7) My system appears stuck here with a blue screen saying "Ubuntu Installer rescue mode"
8) Ctrl-Alt-F2 <enter>
9) mount -tproc proc /target/proc
10) chroot /target
11) su (optional, gives you a few niceties in term of shell)
12) If you have a boot partition: mount /dev/sda1 /boot
13) Add ehci_hcd on a line of /etc/mkinitrd/modules
14) Increase parameter DELAY in /etc/mkinitrd/mkinitrd.conf. I put 10 seconds and it worked.
14b) find the version of your kernel:
ls /lib/modules
15) create the initrd file:
mkinitrd -o /boot/initrd.img-<your kernel version here>-usb <your kernel version here>
16) Edit /boot/grub/menu.lst so that the initrd loaded by the default kernel is the one we've just generated.
initrd /initrd.img-<your kernel version here>-usb
initrd /initrd.img-2.6.10-5-386-usb
17) If you have mounted a boot partition: umount /boot
18) Exit from chroot: exit
19) umount /target
20) reboot

but i have a question, does the install here include installing GRUB or LILO on the first hdd(the hdd inside the laptop)? if so this will not work for me. i saw a  bootable ubuntu hdd online
[http://www.zinside.com/index.php?main_page=product_info&products_id=46&language=en](http://www.zinside.com/index.php?main_page=product_info&products_id=46&language=en)
but cant figure how they did it. 
tnx

---

### Post by CrunchyDoodle on 2005-10-17
I'm trying to do pretty much the same thing and have not been successful yet. My approach is a little different than yours.

I have a fairly modern notebook with XP I do not wish to disturb, but be able to run ubuntu when I want to. What has come closest so far is to use an external USB 2.0 drive and install ubuntu on it with the option of NOT placing the GRUB loader on the notebook internal drive, but on the USB drive. The installation process went well. The failure was when I tried to boot off the USB drive. I received this error message:

   Booting 'Ubuntu, kernel 2.6.12-9-386'

root  (hd1,0)
   Filesystem type unknown, partition type 0x7
kernel /boot/vmlinuz-2.6.12-9-386  root=/dev/sda1 ro quiet splash

Error 17: Cannot mount selected partition

Being a Linux and ubuntu novice (I did systems and embedded programming in SunOS and SCO/UNIX some years ago), I'm not too sure how to interpret this error message. I will be researching that today.

And yes, that bootable ubuntu USB drive is fascinating. I guess someone has got it to work the way we want.

Bye.    :cool:

---

### Post by CrunchyDoodle on 2005-10-17
Well, I've made a little progress. After studying the GRUB manual, I changed the first line of the GRUB script to 'root (hd0,0)', This was after reading that GRUB can be fooled by what the BIOS boot ordering is. Since I did the installation by booting to a ubuntu CD, the meaning of hd0 and hd1 become reversed when I boot from the USB drive. It becomes hd0 in GRUB's eyes. 

Now it gets to where it's trying to execute the kernel command, and doesn't find the /dev/sda1 SCSI drive to mount on /root. It's true, when I get to a shell and look, there are no SCSI drives in /dev at all. So, what is the name of the USB drive right now in this context? It's not /dev/hda or /dev/hda1, and /dev/hdb is the DVD drive. There are no other hard drives showing. Do I need to create something? My ignorance is gigantic here.

Bye.   :cool:

---

### Post by Xenus98 on 2005-10-17
To Ky4623 :

I managed to do this on my laptop. I have Windows XP on my internal HDD.
I did installed Ubuntu on my EXTERNAL USB HDD.
Then, rebooting, it was impossible to boot Ubuntu.

For sure, GRUB was installed on my internal HDD.

The list of step that you wrote are good, but there were made for the previous version of ubuntu. There are some changes...

Do not use mkinitrd (and anyway you will not find it on your installed drive).
The fact is to use mkinitramfs ! It is already installed and just waiting for you !The process is quite the same. Give it a try, I did it like this !

Only one bad point that I am working on it (should be not so hard to solve), it's not possible to boot WindowsXP anymore without the External Usb drive connected... :( I guess Grub is missing some file when the USB drive is not turn on. I am working on this point. Any help is welcome.


Good luck.

---

### Post by CrunchyDoodle on 2005-10-18
Well, a little more progress. I can now boot into ubuntu as a multi-user tty system. I think the fact that I didn't actually finish the installation (like many others, it fails to re-boot properly after removing the installtion CD where it would then be installing more packages). What I did to get this far was use some of the advice I've been reading in various threads in this forum. I used mkinitramfs to add usb-storage and ehci_hcd to the modules list. This allowed /dev/sda1 to exist in the booter RAM-based file system that boots the real ubuntu system.

Now I need to figure out how to complete the installation as it would have automatically. It did bring back some strange memories when I saw that very familiar UNIX prompt and blinking cursor. It was also kind of scary to use vi to edit and actually remember how after 12 years.

At least with my notebook, I can boot XP on the internal drive by simply turning off or unplugging the USB drive. And when I do plug it in and turn it on, it directly boots into ubuntu because GRUB is only on the USB drive and I've set the BIOS for the right boot order to use USB first.

Bye.    :cool:

---

### Post by CrunchyDoodle on 2005-10-18
[COLOR="Purple"][SIZE="7"]**Success!**[/SIZE][/COLOR]   :D 

I now have a totally stand-alone ubuntu booting USB hard drive with a full installation. I'm guessing it's a lot like that commercial product.

What I did in the end was take the hard drive out of the USB 2.0 enclosure and put it directly inside my notebook, and then perform a full standard installation. I then used mkinitramfs to add USB drive support (ehci_hcd, usb-storage). I then edited the GRUB menu to use /dev/sda1 instead of /dev/hda1. I did a shutdown and replaced the original XP drive and put the ubuntu drive back in its enclosure. I'm now able to boot ubuntu by just plugging in the USB drive and rebooting. To go back to XP, I power down and unplug the USB drive and power back up.

I'll supply more details tomorrow.

Bye.    :cool:

---

### Post by thtan on 2005-10-19
Wow, this sound really really interesting. Keep the posts coming!

---

### Post by CrunchyDoodle on 2005-10-19
I squished another bug.   :smile:  This one took me some time in reading man pages on mounting file systems. The problem was with the file /etc/fstab (I think that was the directory) that lists what the boot script should mount when ubuntu is finally up. It still listed /dev/hda1 and /dev/hda5, which were there during the initial installation, but are now /dev/sda1 and /dev/sda5. What is so wierd is that the system worked well and was very stable. Only when I looked with 'df' or 'mount' did I see the wrong device called out. It was also fooling the GUI disk manager which had the information from the XP disk (the real /dev/hda1 now) mixed up with the ubuntu disk (/dev/sda1 now).

I'll give it another day to catch any more bugs and write up a complete report on what I did for those who want to try this kind of thing.   :smile: 

Bye.    :cool:

---

### Post by row1 on 2005-10-19
look forward to reading your report.
After a few hours
I got Kubuntu 5.10 installed on my USB hard drive in my shuttle ST20G5
fixed the boot loader
fixed it hanging on starting hotplug sub system

It then booted into a shell (no KDE!), was able to log in.

On next boot hangs on Checking Battery State!!!!

---

### Post by leezer3 on 2005-10-19
[QUOTE=Xenus98]Only one bad point that I am working on it (should be not so hard to solve), it's not possible to boot WindowsXP anymore without the External Usb drive connected... :( I guess Grub is missing some file when the USB drive is not turn on. I am working on this point. Any help is welcome.
Good luck.[/QUOTE]

Hiya,
Your problem is that GRUB stores all of it's files & config in the Linux partition. The best way I've found to get around this is to create a bootloader partition on the permanant drive, which only needs to be about 20mb or so, and install GRUB on this.

Cheers

-Leezer-

---

### Post by CrunchyDoodle on 2005-10-21
This is my final report on my successful installation of ubuntu 5.10 Breezy Badger on a USB external hard drive.

My goal was to be able to easily run ubuntu Linux on my new notebook without disturbing the original XP internal hard drive. By disturbing, I mean I did not want any  special OS loader installed, or preventing XP from booting and running normally. After several less effective attempts, this is what I finally did that worked the best and satisfies my original requirements.

By the way, my new notebook is a Compal EFL30, a customizable machine sold by mwave, Chembook and some others who build them to order and stick their name on it. It has an Intel 915PM chipset with discrete nVidia 6400 Go VGA chip, and mine has a 2GHz Pentium M 760 CPU. The BIOS is set for a booting order of CD-ROM, Removable Media (USB floppy or hard drive) and then internal Hard Drive.

I started by removing the original XP hard drive and putting in the new hard drive that will be my ubuntu drive in an external USB enclosure. The new drive is a Samsung MP0402H (40GB, 5400RPM, ATA-133, 9.5mm) and the enclosure is an MGE ENWB-25B-SS (USB 2.0 Aluminum 2.5" hard drive enclosure). The enclosure has a funky dual USB plug on one end of the included cable to take power from two USB ports (5V, 1A total). 

I then performed a standard installation of ubuntu 5.10, followed by some updates with Synaptic Package Manager. This went with no hitches and was pretty quick too. Now comes the fun part.   ;) 

In order to be able to boot from an external hard drive, the RAM file system image that is used during the 2nd stage of the boot-up cycle must support a USB external drive, which it originally would not. For this, I added some modules to the image with mkinitramfs by first adding some module names to /etc/mkinitramfs/modules:

# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
#
# This might be good choices:
#
# raid1
# sd_mod
sd_mod
ehci-hcd
usb-storage
scsi_mod

I did all my editing by launching a terminal and issuing the command 'sudo -s' (become superuser) followed by my password, and then 'scite /etc/mkinitramfs/modules'. I could have used gedit instead. My choice of what to add was based on my reading of what others had done and my own judgement of what might work. I then made a back-up copy of the original image with 'cp initrd.img-2.6.12-9-386 initrd.img-2.6.12-9-386.saveme'. I built the new image with 'mkinitramfs -o /boot/initrd.img-2.6.12-9-386'. This will over-write the original image with a new one that contains the new needed modules.

Next came fixing up what GRUB was going to do when it boots the system. To get GRUB to properly address the external USB hard drive, I edited /boot/grub/menu.list to address a SCSI drive and not the original IDE drive:


## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

I again made a back-up copy and edited the original /dev/hda1 reference to /dev/sda1 as shown above. Now, when I put the Samsung drive into the USB enclosure, it will be addressed properly during boot.

The last thing that needs fixing I didn't figure out until later. The file /etc/fstab has a list of devices to initially mount when the boot script runs. Of course, the original version will be wrong. Again, make a back-up and edit this file to look like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1	/Windows	ntfs	defaults	0	0

The important lines to note are the ones that mount the root (/) and swap. They need to reference /dev/sda1 and /dev/sda5 as shown above. I added the last line to mount my original internal XP hard drive as a read-only device available in the /Windows directory of the ubuntu hard drive. I created the /Windows directory with 'mkdir /Windows'. Lastly, perform a shutdown and power off. 

Now, I pulled out the Samsung drive and put it into its USB enclosure. I then put the original XP drive back in the notebook. I plugged in the USB drive and powered up my notebook. That's it. It all worked as I wanted it to.    :D 

Bye.     :cool:

---

### Post by Xenus98 on 2005-10-22
Hi !

Listen found a GREAT solution for my problem and may be usefull a bit...
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
It's even funny, because the boot loader of windowsXP can boot the boot loader of ubuntu... that can then... also boot the windows XP boot loader again... and again...and again... depending on your GRUB menu options...

And if my HDD usb drive is not online, the boot loader of WinXP doesnt care at all !

Et voilà !

hope it's help some people !
I have Ubuntu on my external USB HDD booting via window XP boot loader !!

Thanks the internet for all the different infos I found out to make this possible.

---

### Post by Sankukai Monkey on 2005-10-26
I too am having huge probs getting Ubuntu onto my old Shuttle SV24 ! Enough ram, space on disc as I vaped Win but it keeps hanging at a variety of different stages of install and it's driving me nuts ! One time it's "Updating Security components.." next time it dies installing additional packages.

MD5 on the iso is fine, think I'm going to try burning it on a really good quality CD-R with another burning tool at slowest speed poss...then change out my cd drive for another old faithful sitting in my pile o' bits.

Argh...I will NOT be foiled ?!?!?

---

### Post by GrendelS on 2007-08-25
Hello everyone,
at work I use a Samsung X20 balin notebook ([http://notebook.samsung.de/article.asp?artid=37CCFA5A-D527-4219-9CCB-A9228AF1F32C](http://notebook.samsung.de/article.asp?artid=37CCFA5A-D527-4219-9CCB-A9228AF1F32C)) with WindowsXP. We're using lots of instable or just badly written software (read Outlook), so technical errors are a daily nuisance. I'd love to install Ubuntu on an external Seagate 160GB drive to show off with a stable operating system, but so far, I haven't been even successful with booting the liveCD on the notebook itself. After the bootscreen and startup sound, the screen remains black, eventually, the cd drive and hard drive stop to work and nothing happens for half an hour.

I've looked though the forums and found various threads with work arounds that didn't work for me 
[http://ubuntuforums.org/showthread.php?t=448712&highlight=samsung+x20](http://ubuntuforums.org/showthread.php?t=448712&highlight=samsung+x20)  boot without external hard drive / boot option acpi=off / lowering screen resolution
Should I try with the alternate iso?
best regards,

Grendel

---

