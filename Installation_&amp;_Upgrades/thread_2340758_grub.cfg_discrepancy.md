---
title: "grub.cfg discrepancy"
date: 2016-10-21
forum: Installation &amp; Upgrades
---

### Post by aajax on 2016-10-21
When trying to setup multi-boot, grub.cfg seems to be specifying that the kernel is loaded from the wrong device which seems to result in booting the wrong system.  A snippet from the grub.cfg follows:

*** Begin snippet
```
menuentry 'Ubuntu, with Linux 4.4.0-42-generic (on /dev/sda3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.4.0-42-generic--9a56958b-56cf-4bd4-b1b5-a4adb4def55a' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  9a56958b-56cf-4bd4-b1b5-a4adb4def55a
		else
		  search --no-floppy --fs-uuid --set=root 9a56958b-56cf-4bd4-b1b5-a4adb4def55a
		fi
		linux /boot/vmlinuz-4.4.0-42-generic root=UUID=9de95ca9-5c82-423e-a4dd-a884c2ba39b5 ro quiet splash $vt_handoff
		initrd /boot/initrd.img-4.4.0-42-generic
	}
```
*** End snippet

The partition (/dev/sda3) with UUID=9a56958b-56cf-4bd4-b1b5-a4adb4def55a is the partition that we intend to boot.  However, the partition (/dev/sda2) with UUID=9de95ca9-5c82-423e-a4dd-a884c2ba39b5 appears to be what is really booted.

In the way of explanation consider the following:

There is another minimal Linux system (Debian based) installed on /dev/sdb2 which is used to boot the computer
/dev/sda3 is a clone of /dev/sda2
After restoring the cloned partition the preparation for booting involved -
- Using tune2fs to alter the UUID of /dev/sda3 subsequent to it being restored
- Updated /etc/fstab on /dev/sda3 to mount / to /dev/sda3 using the new UUID
- The boot partition (/dev/sdb2) used to run GRUB2 was booted and update-grub was executed to produce the grub.cfg file from which the snippet was obtained.

It looks like an obvious correction would be to update grub.cfg to specify consistent UUIDs.  However, given that we're advised not to manually update grub.cfg I thought it best to pose the question to this forum with the hope that someone with more knowledge and experience than I have can explain what I did wrong.

---

### Post by oldfred on 2016-10-22
If you use a separate /boot partition that configuration is normal.
One UUID for /boot partition and the other is the main install.

Did you try to use one /boot partition for two installs, that almost always eventually leads to conflicts. 
Better not to use /boot partition for most Desktop installs. Full drive LVM does use a /boot partition.

---

### Post by aajax on 2016-10-22
I'm not sure what you mean by /boot partition?

The computer is BIOS based and has 2 hard drives (sda & sdb).  What I would call the boot partition is /dev/sdb2 (i.e., marked active using an msdos style partition table and MBR).  The drive Linux calls sdb is the one designated as the boot drive in the BIOS.   A minimal DEBIAN system was installed to /dev/sdb2 for the purpose of serving as a boot manager used to select from several possible systems in my multi-boot environment.  The intention being to ultimately have 3 separate Linux systems installed in 3 separate primary partitions on the drive that Linux identifies as sda.  The DEBIAN based system as well as all of the Linux systems mentioned here are installed using the installation option that says DO NOT MESS WITH THE MBR.  In that, the MBR has not been altered.  It is still a standard msdos based MBR.

The Ubuntu 16.04.1 Live CD was used to install a system onto /dev/sda2 (also specifying option to not mess with MBR).  When this was completed the DEBIAN based boot manager is started and update-grub is run.  It correctly finds and adds the Ubuntu system installed on /dev/sda2 to the GRUB2 boot menu.  When the computer is started it boots the DEBIAN boot manager which displays a GRUB2 menu from which either the DEBIAN boot manager or Ubuntu system on /dev/sda2 can be selected for starting.  This all works just as expected and desired.

Subsequent to installing some packages on the Ubuntu system, /dev/sdb2 was cloned using Clonezilla.  That cloned image was then restored to /dev/sda3.  The few steps previously described as preparation were performed.  The boot menu (displayed when starting /dev/sdb2) now includes the system restored to /dev/sda3 and appears to be just what was desired and expected.  However, when I select the system identified as residing on /dev/sda3 from the boot menu the system that is started is the one residing /dev/sda2.  The snippet shown above is the menu entry from grub.cfg for the system that was selected when starting the computer.

My guess is that the problem is caused by something in the /boot directory that has been restored to /dev/sda3 which needs to be updated to reflect that it no longer resides on the original partition but my hacking has yet to discover what that is.

---

### Post by Dennis N on 2016-10-22
> It looks like an obvious correction would be to update grub.cfg to specify consistent UUIDs

Suggestion:

Boot to the grub menu, select the OS that doesn't boot correctly, then 'e' to edit. change the last UUID at: root=UUID=9de95... to be identical with the others. then continue the boot and see if it boots to the right OS. (this is a temporary change and will revert the next boot up).

If it boots correctly, make a custom menu entry with this fix so it won't get modified by any future update-grub. See:
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
if you don't know how to do this.

Sorry, at the moment don't know why your update-grub would create this. Never seen it happen.

That's all.

---

### Post by oldfred on 2016-10-22
If you clone a partition, it also then has the same UUID. Intended for restoring to same place.
Do you now have duplicate UUIDs?
Post this:
sudo blkid

Edit:
With multiple installs, may be better to see all the details:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by aajax on 2016-10-22
Yes!  After restoration of the image to a different location you end up with 2 partitions with the same UUID.  That is the reason for what is described as preparation.  The command tune2fs is used to generate a new UUID for the cloned partition.  That new UUID is then used to replace the old one in /etc/fstab.

Thanks!  Will give Dennis N suggestion a try.

Dennis N suggested > Boot to the grub menu, select the OS that doesn't boot correctly, then 'e' to edit. change the last UUID ...

which I did and it was successful.  Thanks for the help!

I also did a bit more research of my own and it looks to me like there is no alternative but to manually edit grub.cfg.  Consider the following:

I think it is correct to point out that since /dev/sdb2 is used to boot the computer and therefore execute GRUB2 that the grub.cfg files located in the /boot/grub directory on both /dev/sda2 & /dev/sda3 are NOT involved (i.e., used) during this particular boot process.  Also, it is necessary to be able to boot /dev/sda3 in order to use the update-grub command for the purpose of making a new grub.cfg file on /dev/sda3.  In that we're confronted with the so-called deadly embrace.

I found what I think is pretty conclusive evidence that grub.cfg (on /dev/sda3) must be corrected manually.  According to some additional research that I undertook the update-grub command invokes a command named ***os-prober*** for the purpose of finding other operating systems located on the subject computer.  When ***os-prober*** finds another Linux system it invokes a command called ***linux-boot-prober*** to gather information needed to generate the menu entries in grub.cfg.  I experimented by running both ***os-prober*** and ***linux-boot-prober***.  The ***os-prober*** command returns a very brief indication for each OS found that identifies what kind of OS it thinks is present.  I then ran ***linux-boot-prober*** and sure enough it returned an extensive amount of information that contained the erroneous UUID.  I then undertook to manually update grub.cfg on /dev/sda3 by replacing all occurrences of the erroneous UUID with the correct UUID and then ran the ***linux-boot-prober*** again.  Sure enough the output now contains the correct UUID.

I've attached a file with the output from ***linux-boot-prober*** when run with grub.cfg contains the correct UUID.

One of my design objectives is to end up with each partition that contains a boot-able OS being self contained.  By this I mean it doesn't need anything else to be booted.  This is why I've done the Linux installation is such a manner that they DO NOT update the MBR.  My intention is to be able to use the msdos style MBR & partition table in the manner it is intended to be used where I can set any of my system partitions active and boot that particular system.  Because of this I really don't want to run update-grub on the actual booted system/s because that will add all of the other system partitions to the respective grub.cfg where I only want it to reference the single system where it is located.  While this is probably not a particularly important behavior it definitely looks like grub2 does not allow such unless the grub.cfg file is manually maintained.

I sort of think that is where I stand, which is now working as desired, but I'd still be grateful for being corrected about any of my findings that are in error.

---

### Post by Dennis N on 2016-10-22
Glad to learn that worked. 

A couple of comments:

The way things are, the grub.cfg on sdb2 will need to be updated or edited whenever the OS on sda2 or sda3 upgrades its kernel in order to boot that newer kernel. Also, a new kernel installed in sdb2 will always create a new grub.cfg on sdb2 wiping out any modifications. This can all get annoying after a while.

But there is a way to avoid any manual editing - make custom menu entries for all OSes you are booting following the guide I linked to, being sure to use the suggestion for "maintainance fee menu entries" in that guide. I do it that way and never have to edit anything concerning the grub menus. 

The MBR is only written when you install the OS or if grub is installed or reinstalled (this is different from the update-grub process, which is to update the menu). To keep booting to OS #1 after OS #2 is installed, you can do either of two things:

1) reinstall grub of OS #1 to MBR after OS #2 is installed. Easy to do on BIOS systems.
2) specify install grub of OS #2 to the partition the OS is on instead of the MBR.

---

### Post by oldfred on 2016-10-23
Like Dennis N's custom menu, you can create an entry that boots a partition not a kernel.
With Debian based Linux, it creates a link to newest kernal, so your custom entry is to boot the link.

Grub2 is larger than the old grub legacy. And grub2 does not like to be installed to a PBR or partition boot sector. It just does not fit and has to convert to blocklists and will complain about that. Blocklists are just addresses so if any part of grub moves on drive even a fsck then  you break grub.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen) 
    
If you install grub, it remembers where you installed it. With more than one install best to make sure other installs do not overwrite main working version.
       #to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643) 
    
If you do not want grub installed from live installer:
       sudo ubiquity -b
[http://askubuntu.com/questions/838450/how-can-ubiquity-be-forced-not-to-install-grub/838527#838527](http://askubuntu.com/questions/838450/how-can-ubiquity-be-forced-not-to-install-grub/838527#838527)

---

### Post by aajax on 2016-10-23
Oh yes!  I get the point about kernel updates that in this case are being performed on a different partition|filesystem than the one being used to boot the computer.  Will definitely pursue the custom menu entries.  If I understand correctly this should also allow me to avoid the need to run update-grub on the system being used for a boot manager.  Sounds good.

Oldfred says > If you install grub, it remembers where you installed it.

The only way I've been able to figure how to install GRUB2 is by installing a complete Linux system.  Is there another way?

My operational (i.e., multi-boot) systems tend to be very dynamic because I do a lot of experimentation.  This experimentation has a way of causing unintended effects that are sometimes difficult to diagnose and/or repair.  My answer to that is "if it hurts don't do it".  This means that I quickly give up and restore the partition to a previously cloned image that was known to be working well in the past.  Depending on circumstances unknown before hand the image I choose to restore may have come from a different partition than the one being restored.  In order to avoid such events from impacting other of the multi-boot systems on the same computer I want to avoid the situation where there are any inter-dependencies between them.  The idea that one might depend on the other for booting is probably the worst possible case.  That is why I have a dedicated system installed which is used as nothing but a boot manager.  Since that system is only used to boot the computer it is very static and will become even more static if I don't have to ever run update-grub on it.  That system will only be updated if and when necessary, which means only if GRUB2 stops working which I hope to be very infrequently.

My hope has been that such a static system will be less susceptible to the issues associated with installing GRUB2 in the partition boot sector rather than the MBR.  However, my design will permit me to change to using the MBR on that disk, which is different from the one used for the multi-boot systems, if such problems arise.  My understanding is that the GRUB2 installed on each of my operational systems sits there essentially unused except during updates as pointed out by Dennis N.  However, I have strong resistance to the idea of having inter-dependencies between the multi-boot systems installed on the drive, which is not used for booting the computer.

---

### Post by Dennis N on 2016-10-23
> The only way I've been able to figure how to install GRUB2 is by installing a complete Linux system. Is there another way?

Easy to install when using BIOS installations.
```

sudo grub-install /dev/sda
```

if sda is the disk the system boots at startup.

Then computer will boot at startup to grub on the OS from which you installed grub.

---

### Post by Dennis N on 2016-10-23
> I want to avoid the situation where there are any inter-dependencies between them. The idea that one might depend on the other for booting is probably the worst possible case.

Don't your two OSes on sda depend on your system on sdb which boots them? For emergencies, should your OS on sdb fail to boot, you could have grub installed to the MBR of sda from one of those two and have an alternate way to boot up.

---

### Post by oldfred on 2016-10-23
I have installed grub in UEFI mode only to flash drive, just to use its loopmount feature to directly boot ISOs.

And in BIOS mode, I have installed grub to FAT32, NTFS (careful on /boot vs \Boot cannot have both grub's & Windows as Windows is not case sensitive) and Linux formatted partitions. But you have to manually maintain your own grub.cfg as without full install you do not have the other parts of grub with settings & programs to update it.

But I typically only use grub from my main working install, turn off os-prober and only add entries I want in 40_custom as in link on Cavsfan's details for custom grub that is maintenance free. I also learned from user Ranch-Hand, who was installing the dailies regularly and did not want to mess with grub but still be able to boot the new daily install. Cavfan just documented it very nicely.

---

### Post by Dennis N on 2016-10-23
oldfred:

Cavsfan doesn't seem to use UUIDs in his menu entries from what I can see in that guide. Am I wrong about that? I want mine to use UUIDs, so have always used the guide at:

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

Also, rather than putting them all into one file, I use separate files for each os - easier to reorder, disable and enable that way.

---

### Post by oldfred on 2016-10-23
I typically do not use UUIDs as when you reformat & reinstall UUID changes. So my reinstall of 16.10 still worked using /dev/sdb9 but would not have worked with UUID. And with UEFI/gpt, GUID changes also which in some cases can be important.

I even have gotten confused on internal drive as first configuration I had DVD on SATA1 which made 2nd drive as hd2 in grub but still sdb in Ubuntu.

But device also has changed on me for external drives.
So no one good solution. 

I now use configfile in 40_custom, so then I only have to edit text file. I always was forgetting to run the grub update after edition 40_custom.
UEFI now uses a configfile also to find full grub.cfg. It uses both a set root by device & then search by UUID.

I assume you could use UUID instead, but have not and maybe should for my now standard ISO partitions that will not be reformatted. 
```
menuentry 'Live ISOs' {
configfile (hd2,4)/iso/livecdimage.cfg
} 

```

---

### Post by aajax on 2016-10-24
Dennis N says > Easy to install when using BIOS installations. ...
So after you have the system running you install the software you need to start it.  Not what I was thinking but why not?

Dennis N says > Don't your two OSes on sda depend on your system on sdb which boots them?

Yes, but that one is not one of the interchangeable multi-boot systems that I'm experimenting with and therefore causing to get messed up.  I hope the system used for only booting doesn't change (or changes very minimally) and just keeps working.  I also have Super GRUB Disk and System Recovery Disk to help with real emergencies.

Oldfred says > I typically do not use UUIDs

I think my experience here is providing a pretty good explanation for why not.  I'll definitely be trying it your way.  I think UUIDs solved a problem that could theoretically arise when making changes to the partitions on a disk that might affect the drive name deduced by Linux but when thinking back to my days before the UUID technique even existed I don't recall anything being as big a hassle as I'm now experiencing with these UUIDs.

---

### Post by aajax on 2016-10-26
I'm trying to implement some of the ideas described in the article on [MaintenanceFreeCustomGrub2Screen]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen").  To start I just want to add menuentry in the file /etc/grub.d/40_custom.  The code I came up with is as follows:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
#
menuentry "System A on sda2" {
    set root=(hd0,2)
        linux /vmlinuz root=/dev/sda2 ro quiet splash $vt_handoff
        initrd /initrd.img
}
#
menuentry "System B on sda3" {
    set root=(hd0,3)
        linux /vmlinuz root=/dev/sda3 ro quiet splash $vt_handoff
        initrd /initrd.img
}
```

I've tried it both with and without the $vt_handoff variable, which I admittedly don't know what it might be intending to do.  I get the same result either way which is that the system seems to boot up but with both the keyboard and mouse disabled.  Not too useful but I suppose we could call it "close but no cigar".

---

### Post by oldfred on 2016-10-26
If not standard Ubuntu, you often have to check to see if system has special boot parameters and include those.

But I usually find USB ports not working is a BIOS/UEFI setting or two even to enable USB  and/or USB keyboard & mouse.
What video card/chip?

---

