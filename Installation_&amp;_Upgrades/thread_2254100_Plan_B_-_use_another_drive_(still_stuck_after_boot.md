---
title: "Plan B - use another drive (still stuck after boot-repair (lenovo y500 dual boot))"
date: 2014-11-25
forum: Installation &amp; Upgrades
---

### Post by Jonathan_Strong on 2014-11-25
hey guys,

I have been trying to get this going for hours now and don't know where to turn. 

I installed ubuntu 14.10 alongside my existing windows 8.1 install. Installation went through fine, but I could not boot after install. I get to the grub menu but when I try to boot ubuntu, either normal or recovery mode, it never finishes loading. 

After lots of attempts at fixing this, I have been able to boot the computer using the grub console. here is an image of the commands I used from a tutorial I found (essentially setting the root, kernal and initrd manually): [http://i.imgur.com/nyUwzYa.jpg](http://i.imgur.com/nyUwzYa.jpg)

Once I was in, I ran boot-repair. here's my rundown: [http://paste.ubuntu.com/9226708/](http://paste.ubuntu.com/9226708/). also the message I got was this:[INDENT]Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/9226708/](http://paste.ubuntu.com/9226708/)


In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sdb2/EFI/ubuntu/shimx64.efi file!

The  boot files of [The OS now in use - Ubuntu 14.10] are far from the start  of the disk. Your BIOS may not detect them. You may want to retry after  creating a /boot partition (EXT4, >200MB, start of the disk). This  can be performed via tools such as gParted. Then select this partition  via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

You may want to retry after activating the [Backup and rename Windows EFI files] option.
[/INDENT]

I shutdown, tried to boot, and got hung up again. Here is a screenshot of what happened. [http://imgur.com/4hpQdIo](http://imgur.com/4hpQdIo)

boot-repair suggests I need a efi partition at the beginning of the disk. here is a screenshot of all the various partitions that came with my laptop. they are all windows so I'm guessing I would need to use windows partition tools to create some space at the beginning of the disk. 

[http://i.imgur.com/IzG5sBX.png](http://i.imgur.com/IzG5sBX.png)

boot-repair also says to make sure bios is using sdb2/EFI/ubuntu/shimx64.efi. I looked closely at bios settings and did not see anything for selecting a specific file. 

so ... pretty exhausted after trying so many things. would greatly appreciate help from you guys. Please let me know any additional info you need to diagnose. thanks.

---

### Post by yancek on 2014-11-25
I don't use UEFI myself so not sure this will help.  One thing I can see which might be a problem is that you have 2 EFI partitions, sdb2 and sdb3 and sdb2 looks like it has the correct files.  At the end of the boot repair it also indicates that you should use sdb2.  There are also a number of messages indicating ntfs partitions are in an unsafe state.  That usually means your windows is hibernated and not fully shutdown.  You could try shutting windows down properly and rebooting to see what happens.  You don't actually indicate whether you can boot windows??  I'm not sure what you could do about the two efi partitions but perhaps someone else will have a suggestion.

---

### Post by Jonathan_Strong on 2014-11-25
I have been able to boot windows successfully since this, also I have a full backup so I'm good if this ends in disaster. I'm not sure why windows seems to be hibernating except may have something to do with the factory settings. 

was on IRC and did smartctl as a diagnostic - here are the results: [http://paste.ubuntu.com/9233651/](http://paste.ubuntu.com/9233651/). The verdict there was I need to replace my HDD whether or not that's the issue based on this readout. My plan at the moment is to replace a second graphics card in a bay on the laptop with an SSD, install ubuntu there and leave the current one in place for time being.

---

### Post by oldfred on 2014-11-25
I think Lenovo's have a vendor efi partition. But it is not flagged as efi, just has some vendor efi files. Not sure how they access it or if they change it to the efi partition when in Vendor maintenance. But as long as not shown as efi, it is ok.

If you are able to get to grub menu, then you are booting are are past most of the Boot issues. You may need boot paramater on Linux line like nomodeset.
What video card/chip does your system have? If Intel then nomodeset does not usually work, but some of the Intel specific ones may.
A lot of Lenovo models seem to have brightness set to 0 or system is working, you just cannot see it.
Also if an Ultrabook you have dual video. Can you set which video mode you boot in?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)


 Lenovo s440
[http://ubuntuforums.org/showthread.php?t=2189531](http://ubuntuforums.org/showthread.php?t=2189531)
Lenovo Yoga 11s (Intel i5/Intel HD 4000)
Needed this: acpi_backlight=vendor 
[http://ubuntuforums.org/showthread.php?t=2188199](http://ubuntuforums.org/showthread.php?t=2188199)
[http://ubuntuforums.org/showthread.php?t=1911972](http://ubuntuforums.org/showthread.php?t=1911972)&


 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)
screen brightness was 0 during installation, use f12
Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
[http://ubuntuforums.org/showthread.php?t=1543006&p=12710212#post12710212](http://ubuntuforums.org/showthread.php?t=1543006&p=12710212#post12710212)
See post #29 on removing Battery to get it to reset &  boot Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)
Lenovo Ideapad Y500 LiveUSB Problem, also brightness
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)

---

### Post by Jonathan_Strong on 2014-11-25
I do have dual graphics cards on this laptop. have not tried to change graphics settings in bios - what would I change to if I can find it? 

I did try nomodeset in a previous iteration but will try again now that I've run boot-repair and see.

---

### Post by Jonathan_Strong on 2014-11-25
update - got same error w/ nomodeset

[http://imgur.com/zn484wY](http://imgur.com/zn484wY)

---

### Post by oldfred on 2014-11-25
Some systems are muxless? or auto switch. Others do have settings in UEFI/BIOS.

If booting with Intel, nomodeset does not work and you need one of the Intel settings and may need added settings also.

But error seems to be related to hard drive/partition error.
Do you have UEFI/BIOS set for AHCI and Intel SRT turned off also?
Someone with Lenovo mentioned this, sound like it may lock drive?
 Lenovo Active Protection System&#8482; &#8211; for hard drive



I might run this from live installer.
       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb8
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb8

---

### Post by Jonathan_Strong on 2014-11-25
If I could switch tracks on you guys: I've decided to try another approach. given that my hard drive is having issues, I'm going to install an SSD in an empty bay on the laptop and install ubuntu as the only os on that drive. I'll leave the other one for now and potentially replace that drive later. for now I can use it for storage. 

that brings up a new question which is - how do I go about removing my current ubuntu installation and/or grub? is that necessary? could I just delete the ubuntu partion?

---

### Post by oldfred on 2014-11-25
Can you boot from the drive bay. Some systems do not make it a full drive, but just a data drive.

To fully house clean Ubuntu on UEFI system, requires you to reset UEFI to boot Windows by default. Remove ubuntu folder in the efi partition and then remove the saved in NVRAM UEFI entries for ubuntu. Then you can reformat ext4 & swap partitions. Often better to use gparted to remove Linux partitions as then it is clear what they are. If resizing NTFS, use Windows own tools or reformat as NTFS data partition.

If a separate SSD, I prefer to make it that system fully can boot with just that drive. That then includes an efi partition on SSD with ubuntu's boot files in it, not in the efi folder on the hard drive which probably would be the default. 
You have to use Something Else to have the option on where to install grub2's boot loader and that would be the SSD which may be sdb or sdc or sdf? 
I prefer to partition in advance as gparted is a bit easier to use for partitioning, but you still have to use Something Else to tell installer which partition is /, which is /home (if separate). If swap created in advance it will auto find it.

       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by Jonathan_Strong on 2014-11-25
good point about system limits on the bay ... I don't think that is an issue but can't find anything authoritative. if that is I'll just switch out the main hd and convert that to usb I guess. it's going to crash sometime soon anyway. thanks for heads up on needing to add efi to the ssd drive. I think the only way this will work as a 'dual boot' is to actually choose the boot device each time I want to load one or the other through the system. But that's not hard on my computer because there's a one key recovery button that brings up the menu quickly.

---

