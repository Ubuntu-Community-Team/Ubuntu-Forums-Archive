---
title: "[Resolved] [Server] ThinkCentre M55P - UEFI - Install - No Operating system found"
date: 2017-02-04
forum: Installation &amp; Upgrades
---

### Post by wpearsall on 2017-02-04
Hi guys,

I bought a cheap Lenovo ThinkCentre M55P to install a server on. 

I've installed the server, and it comes up with no operating system found. - the live CD worked fine FYI.

Now, i've read quite a bit online, and seen that the bios looks for "Red Hat Lunux" or "Microsoft windows" on the boot record.
I've changed the disk to a MBR /Dos disk from UEFI.

still nothing.

Anyone able to help / guide on this?

I've read about renaming grub to microsoft windows, but wasnt sure how / didnt quite understand the process...

from reading it looks like this is a bios issue, which will only boot windows.

I have seen a fair few posts on the forum refering to the M55p think centre, so know that it's possible to get working...

Edit :
Problem was with partitioning,  thanks to oldfred below for the help.

---

### Post by oldfred on 2017-02-04
If Booting in BIOS/MBR it should just work.

But better to have gpt partitioning as then you can configure to either BIOS or UEFI if you have correct supporting partitions.
UEFI must have the ESP - efi system partition and BIOS must have bios_grub partition. I actually add both to all new or reformatted drives, including larger flash drives, but with smaller ESP.

If the ESP is sda1 (as that is defaults):
  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 

I make these the first two partitions on all my installs.
      
 Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)

---

### Post by wpearsall on 2017-02-04
Right.  So,  I went into gparted and converted the drive to ms-dos on the live cd. 

Should I boot up live cd, gparted and then convert back to  gpt, create a 300mb partition fat 32 partition. Boot flag. A blank 2mb partition,  A 500mb swap partition  and ext 4 root (/) taking the remaining space partition then boot  back into install?

Or

Run terminal of 
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 

Before install? 

Or would I need a different partition structure?

I'm quite shocked that this 2006 machine has been such an issue.  I've a newer hp machine which was no trouble what so ever...  But reading it,  the boot string not being windows is the issue.  

I have read somebody circumventing by running from a USB Pen...  Which seams a little pointless to me when I've got a hdd to use.  

I'll try and read all the post in your sig too, don't think I've seen that before but just had a glance.  

Cheers

---

### Post by oldfred on 2017-02-05
IF a 2006 machine it is doubtful that it has UEFI.
If an Intel motherboard it may have very old EFI.
And Intel is one that seems to require a partition with the boot flag. At least newer desktop motherboards with gpt booting in BIOS mode had to have the ESP (or partition with boot flag), just to let it boot.
Grub does not use boot flag. 

No idea then if any newer UEFI v2 commands work or not.

I did put gpt partitioning on my 2006 laptop, and BIOS still booted ok. Not even sure all really old systems would then work with gpt.

Just checked specs, please confirm.
But if core2 duo that is same as my desktop build in 2006. Back then I used 32 bit Ubuntu. But in 2009 converted to 64 bit Ubuntu and in 2011 converted Ubuntu boot drive to gpt.

---

### Post by wpearsall on 2017-02-06
Hi yes, core 2 duo. 

Im just formatting now with the specified partitions.   My acer laptop installed no issues, and had the swap area as sda1 bootable flagged.  Installed automatically.  Im guessing this may be the issue as ive seen lots of threads saying make sure the primary isnt sda1. Only approx half hr left to install (will gimme chance to locate my desktop live cd)

---

### Post by wpearsall on 2017-02-06
Ok. To confirm: this worked.
1. 298mb Primary partition,  unmounted,  fat32, boot flag
2. 2.1mb unformatted,  unmounted partition 
3. 502mb swap area 
4. 78.1gb ext4 root mount /

All partitions are primary partitions.  

After seeing my acer laptop has installed with the following  in tempted to try pulling the drive and checking the following as this is what my acer has :
1. Primary swap area 500mb boot flag 
2. Logical ext 4 root mount 

From reading the biggest issue is putting the main root partition on sda1, so I'm thinking this was my (or even the installers as automatic creation created / ext4 as sda1 too)  error.  

Note that with the lenovo m55p I didn't have to name it to Microsoft Windows, despite reading that it did need that... 

Root is now sda4, to which my numerous external drives can be plugged into and mounted (just gotta configure it all now)

---

### Post by oldfred on 2017-02-06
Usually best not to use all 4 primary MBR partitions, but use one of them as the extended partition, so you can use logical partitions. 
With gpt there are no extended or logical partitions, just one type essentially all primary.

You can put boot flag on any partition, but better not on swap. Only if Windows or syslinux boot loaders would location of boot flag matter. Grub does not use boot flag at all.

Only if drives will be permanently installed/mounted should you use fstab. As if you unplug drive, boot will complain when loading fstab about missing drive.

       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[URL="https://wiki.archlinux.org/index.php/Fstab"]https://wiki.archlinux.org/index.php/Fstab

[/URL]
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead. 
But I prefer to mount in /mnt/ not /media where automounts normally are. But that is more a personal choice.

[URL="https://wiki.archlinux.org/index.php/Fstab"]
[/URL]

---

### Post by wpearsall on 2017-02-06
I plan to place a couple of external hdd inside the case (remove the 5inch dvd, floppy etc)  and add an extra sata.

I've just looked back on my work and realised I haven't actively done anything on Linux since 2011. 

I'm  updating my old samba pc "nas" 466mhz, as it isn't fast enough now with video streaming etc from stored files.  

I'm  sure I'll be back on the forum later in the week with a few more requests (transition from pptpd to openvpn and http to https) but I wanna have a bag to resolve the errors I get so I understand how the errors occurred and thus learn from my mistakes (or learn new practices ie a default partition table like above)

---

