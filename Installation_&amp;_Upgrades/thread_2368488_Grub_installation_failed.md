---
title: "Grub installation failed"
date: 2017-08-11
forum: Installation &amp; Upgrades
---

### Post by Malign on 2017-08-11
Good day all
Im trying to do a clean install of ubuntu studio 16.04.2 onto an HP Pavillion 17 notebook. I receive the error:

 "Grub installation failed
the grub-efi-amd64-signed package failed to install into /target/"

i have manually created partitions, changed between legacy and uefi, tried manually installing grub in several flavours, tried re-writing the iso to several dvds, and memory sticks, did some sudo things in the console i didnt understand. 

bottom line is dont ask what partition i like or whatever. all i want is a clean linux install with no dual boot. please assume i am not a tech guru, just an artist who is battling.

if anyone could link to an install guide that works, or is willing to tell me how to get this onto my pc, that would be awesome. i wil, kick my bios ass just tell me where

plz help

tails

---

### Post by TheFu on 2017-08-11
Either wait for oldfred to respond or search for the issues with many (most?) HP model UEFI implementations to find what manual steps are needed.

BTW, you should complain to HP - loudly for
a) not following the standard
b) not supporting Linux (much)

As far as I know.

---

### Post by oldfred on 2017-08-11
Stop switching from UEFI to Legacy or vice versa.
You need to have partitioning and supporting partitions match how you boot installer & install.
If dual booting with Windows pre-installed then system is UEFI and you should only work with UEFI boot of flash drive & UEFI boot of system.

HP violates UEFI spec that says NOT to use description as part of UEFI boot. And only valid description is "Windows Boot Manager". We have many work arounds, some better than others depending on configuration.

If installing in UEFI mode, you need to use gpt partitioning and must have the ESP - efi system partition (FAT32). That is where all install's boot loaders are installed with UEFI. But only one ESP per device or drive.

What video does this system have? 
Are you dual booting?

 [URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
      [/URL]
 UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 
    [URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL] Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
Also shows Windows 10 screens or similar to Windows 8
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)
UEFI install,windows 8 with Something Else screen shots, similar for newer versions of Ubuntu
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html) 

    
See also link in my signature below.

       escape + F9 for boot menu, F10 for bios setup
[http://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453](http://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453)
[http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook](http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook) 
    
[https://ubuntuforums.org/showthread.php?t=2247186](https://ubuntuforums.org/showthread.php?t=2247186)
 Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114)
Rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

---

### Post by Malign on 2017-08-11
no dual boot, just ubuntu, and the laptop has an nvidia gforce sticker on it. I will try work through the links provided and let u know if and what worked. thanks so far will let u know how i fared

---

### Post by Malign on 2017-08-11
assuming i dont care what settings are needed, what is the best (easiest to make it work) bios settings and OS settings to use? I dont mind googling the how, i just need a direction and a bit of a run up

---

### Post by Malign on 2017-08-11
the story so far:

in bios disabled legacy support

in gparted 
set up the fat32 boot esp partition
set up the ext4 partition
set up an 8gb linux swap partition

installed using following
install 3rd party software
left all multimedia packages enabled
used something else option
set path in the ext4 partition to /

still get the grub issue...

---

### Post by Malign on 2017-08-11
the story continues

did all of above except one extra step:

in gparted used create partition table, set as gpt.

still get the grub issue...

edit:
tried all of above, except set device for boot loader installation to /dev/sda1

still no luck

---

### Post by Malign on 2017-08-11
worked through your links, still no luck. besides tossing the Linux disk, what are my options?

---

### Post by Malign on 2017-08-11
ok got it to work :D
was using ubuntu studio 16.04.2 but this does not work at all
I downloaded ubunto 16.04.1 LTS, and without doing anything other than a straight install and it worked. 

new question: is it possible to install sofware from the studio disk? 

thanks

---

### Post by TheFu on 2017-08-11
Use a repo.  Any compatible repo can be used, just beware that when you add a repo, you are effectively trusting them with root on your system.  If you install a desktop, you can install almost any server package, for example and vice versa - within the limitations of the hardware involved.

Also, just because some software installs, that doesn't mean the more complex solution are setup to work across the board.  I've never looked at Ubuntu Studio, but expect they setup complex things for audio handling that the other distros do not attempt.  Some manual config may be needed.

Glad you got it working!

---

