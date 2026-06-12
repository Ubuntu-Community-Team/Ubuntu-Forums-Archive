---
title: "cant install new ubuntu - &quot;installer error...&quot;"
date: 2016-08-29
forum: Installation &amp; Upgrades
---

### Post by bobfromct on 2016-08-29
Hi Im a LONG time centos user now interested in ubuntu. Unfortunately I  can't install no matter what.

Burned a dvd - choose install - gets to enter user - then crashes installer error
went with minimal install - hung indefinitely on configuring landscape manager @ 15%
Tried using the live cd - then install same "installer error"
tried again with the mini network manual install - the install seemed to think i was uefi - somehow grub did not get installed and I was  left with a initramfs prompt

I believ I was installing the 16 version 

This is is  a basic dell latitude laptop

PLEASE tell me what I need to do to get this installed - I've installed hundreds of times with centos

The main error was "installer error copying files"

The cd can be read, I've used a USB stick. the sdd hard drive can be written to 

HELP!!

---

### Post by oldfred on 2016-08-29
What model Dell?
UEFI or BIOS install?
Is drive gpt partitioned?
If UEFI do you have an ESP on sda?
If BIOS are you installing grub boot loader to same drive?
Using one of the auto install options, or Something Else?

Post this:
sudo parted -l

---

### Post by ajgreeny on 2016-08-30
Did you check the md5sum of the iso file you downloaded?
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Can you run the live OS rather than go straight to the install option; it may give some clue to the DVD being either a bad burn or burned from a bad iso.

You can also check the install medium from one of the first menus you see when you boot to the DVD; try doing that and if any errors are shown you will need to check the iso and if necessary, download again preferably using a torrent client.

---

### Post by bobfromct on 2016-08-30
Thanks for the reply
its a dell latitude e6410
using sata  sdd 3 drive (ive also tried with plain sata same results)
has bios
no gpt parted - Ive let the previous installs use the entire disk
One manual install I did - most successful, I told the install to use the mbr, then it booted into grub, I selected ubuntu and then it went to black screen. The manual install was very time-consuming

i can't get the parted -l because ive never got a working install. Are you suggesting I run parted by itself and repartition? I can do that but don't think it will help

I use mini.iso to do a manual network install
one time it hung @15% installing landscape...
same as above but grub had the boot partition wrong

I installed with burned dvd, usb created by yumi
did the main gui install fails at the point of entering your user id "installer error... bad cd or disk.."
I did the live cd - install, same as above
Ive tried sdd drive and regular sata - same errors

closest Ive got was the manual network install and I think I could repeat it and possibly get it to work but Im expecting just a basic system - no windows. Id like the gui install. Ubnutu looks beautiful from the live cd and I extremely impressed how it picks up my wireless..

any Ideas Ill try...

---

### Post by bobfromct on 2016-08-30
ok - ill try that as a double check. Ive got to get to work, will reply  later tonight

thanks

---

### Post by oldfred on 2016-08-30
If you also have nVidia, then you may have video issues.
And usually nomodeset works until you install proprietary driver for your model nVidia card/chip.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 


       # Usually nVidia or AMD work with this:
nomodeset
nouveau.modeset=0  
    

You can run parted from live installer in live mode.

Most desktops do not need separate /boot partition. Full drive LVM with encryption does use a /boot partition.

I prefer to partition in advance with gparted. Install then seems a lot faster.

---

### Post by bobfromct on 2016-08-30
ok - thanks - Ill try all that tonight

---

