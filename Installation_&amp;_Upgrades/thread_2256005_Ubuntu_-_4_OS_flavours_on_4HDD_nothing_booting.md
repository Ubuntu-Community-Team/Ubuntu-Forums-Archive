---
title: "Ubuntu - 4 OS flavours on 4HDD nothing booting"
date: 2014-12-09
forum: Installation &amp; Upgrades
---

### Post by Andrew_Dennison on 2014-12-09
I have a machine with 4 hard drives each with a separate installed Ubuntu OS on each. 

What I am trying to get setup...
 
sdb - Ubuntu 13.04
sdc - Ubuntu 12.04
sdd - Ubuntu 11.10
sde - Ubuntu 14.04

After failing to install 11.10 to sdd, I installed another copy of 14.04 in its place and used KVM for 11.10. Not ideal. We need the older Ubuntu versions to support software and code developed on them historically for comparisons while we attempt the updating of said code to work with the latest software on Ubuntu 14.04. S what I now have looks like...

sda - usb drive
sdb - Ubuntu 13.04
sdc - Ubuntu 12.04
sdd - Ubuntu 14.04
sde - Ubuntu 14.04

after installing Ubuntu 14.04 the OS wouldn't boot. I ran boot repair as a live-USB and followed the instructions it gave me in the terminal...

sudo chroot "/mnt/boot-sav/sdb1" dpkg --configure -a
...wait...
sudo chroot "/mnt/boot-sav/sdb1" apt-get install -fy
...wait...
sudo chroot "/mnt/boot-sav/sdb1" apt-get purge -y --force-yes grub*-common shim-signed Linux-signed Linux-signed*
...wait...
sudo chroot "/mnt/boot-sav/sdb1" apt-get install -y --force-yes grub-efiamd64-signed shim-signed Linux-signed-generic
...wait...

response

boot successfully repaired 
[http://paste.ubuntu.com/9439016/](http://paste.ubuntu.com/9439016/)
do not forget to make BIOS boot on sdd1/EFI/Ubuntu/shimx64.efi file (how do I do this?)

I restart the PC and now no grub loads and no OS will boot using f9 to select drive to boot from..

sdb and sdc give 
error: file `/boot/grub/i386-pc/normal.mod` not found  
grub rescue>

sdd and sde give a black screen and flashing cursor

How do I get this system running again, I can see all the system files and drives when I run from a live-USB. I have a full hd backup for 11.10 of files but 12.04 and 13.04 have none as I wasn't trying to change those drives so the last backup is too old.

---

### Post by Darth Riker on 2014-12-09
Just a query: any reason you are starting a new thread on this compared to your previous thread? [http://ubuntuforums.org/showthread.php?t=2255884](http://ubuntuforums.org/showthread.php?t=2255884)

---

### Post by Andrew_Dennison on 2014-12-09
yes all 4 os no longer work not just one. Problems changed. Much worse. Unfortunately I had started boot repair before I was recommended not too.

---

### Post by grahammechanical on 2014-12-09
Did you build this machine by taking hard drives from other machines and did these hard drives already have version of Ubuntu installed on them? Does this machine have UEFI boot system and not a BIOS boot system? I see,

sdb = 13.04 but without EFI boot files
sdc = 12.04.5 but without EFI boot files
sdd = 14.04.1 with EFI boot files
sde = 14.04.1 with EFI boot files.

I do not have a UEFI boot system. So, I have no personal experience. But it is my understanding that we cannot mix and match BIOS boot and EFI boot methods. We have to set the machine to either boot in EFI mode or what is called legacy mode. In EFI mode only Ubuntu on sdd and sde will be available to load. In legacy mode only Ubuntu on sdb and sdc will be available to load.

I am guessing that the two versions of Ubuntu 14.04.1 (sdd & sdc) were the only installs done with this motherboard. Or a motherboard with EFI boot system. I am guessing the Ubuntu 12.04.5 (sdc) and 13.04 (sdb) were installed on machines with BIOS boot and the two drives have been transferred in this machine with UEFI boot system.

I am further guessing that the machine has been set to boot in legacy mode (BIOS) but that neither sdb nor sdc have the first boot priority. So, the repaired Grub (EFI mode) in either sdd or sde is not being detected. Or loaded.

Please make sure that the boot mode is set to EFI and that the boot priority is set to either sdd or sde. Boot Repair recommends sdd.

> Please [COLOR=#AA22FF]**do **[/COLOR]not forget to make your BIOS boot on sdd1/EFI/ubuntu/shimx64.efi file!

That statement is just another way of saying sdd should have boot priority.

> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.[FONT=inherit][/FONT]
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[FONT=inherit][/FONT][/FONT]

[*=left]if Ubuntu is the only operating system on your computer, then it does not matter whether you install Ubuntu in EFI mode or not.
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by oldfred on 2014-12-09
Other thread closed.

Boot-Repair is fine, as long as with multiple drives you do not use auto fix. And it is the best way to document what is where. And it will only fix or try to fix current versions, do not run on obsolete versions as it may uninstall something that then cannot be reinstalled.

You can mix UEFI & BIOS, but it makes things difficult. Grub can only offer to boot systems installed in the same boot mode as it is. But you should be able to boot from UEFI boot menu or perhaps one time boot key.

And you want grub installed to MBR of same drive as install for BIOS installs. Boot-Repair can do that in its advanced mode or you can manually do that from live installer.
Also best to have efi partition on every UEFI boot drive and install grub to that efi partition. But I was not able to do that during install with my system. 

The normal not found is usually trying to boot a BIOS install when system is in UEFI mode or boot an UEFI install when system is in BIOS mode. Or it is wrong version of grub.

You show this:
```
 efibootmgr -v
BootCurrent: 000B
Timeout: 0 seconds
BootOrder: 0000,0002,0001,0004,000B,0005,0006,0007,0008,0009
Boot0000* [COLOR=#ff0000]ubuntu[/COLOR]    HD(1,800,100000,6be5dd5c-8f08-4bb0-800f-8434481501ef)File(EFIubuntu[COLOR=#ff0000]shimx64.efi[/COLOR])
Boot0001* USB Floppy/CD    Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0500000001)AMBO
Boot0002* [COLOR=#ff0000]grub[/COLOR]    HD(1,800,100000,0fcd177e-7809-4ece-8cf1-ef519089204e)File(EFIgrub[COLOR=#ff0000]grubx64.efi[/COLOR])
```

From UEFI menu and boot choices you should see ubuntu and grub. It looks like they are different UEFI installs. Shim is used for secure boot but will work with secure boot off. 
Make sure system is set for UEFI boot and try each of those settings to boot. 
One time boot key should also give those options.

If you have UEFI set for BIOS/CSM/Legacy boot then you may be able to boot the grub in sdb. That looks like it would boot in BIOS mode the old install in sdb1.

---

### Post by Andrew_Dennison on 2014-12-09
The system I am working with is a hp z820 workstation with four hard drive slots. It was previously running Ubuntu as
sda - Ubuntu 13.04
sdb - Ubuntu 12.04
sdc - Ubuntu 11.10

The first sda having boot priority I believe.

We backed up the hd for Ubuntu 11.10 and then installed Ubuntu 14.04 on this with no problem.
We then a few months later found the need to roll back to Ubuntu 11.10, with a reinstall, to test software and applications written for this version that we had backed up previously.
 and that's where all the fun began...
This did not work but the other OS's still booted fine

After many attempts to get Ubuntu 11.10 to install and boot, I just re-installed Ubuntu 14.04 to drive 3 but this now didn't boot either.
We added another SSD to the system as drive 4 for Ubuntu 14.04 and this booted fine. 

I then tried using the boot repair live-USB with recommended options and this made things worse
I tried again and this time it asked me to open the terminal and input commands as shown in the first post 

now nothing will boot no grub and using f9 to select boot drive... 

sdb + sdc give 
error: file '/boot/grub/i386-pc/normal.mod' not found. 
grub rescue>

sdd + sde give
 black screens and flashing cursors

---

### Post by oldfred on 2014-12-09
We cannot work on all systems at once. Pick one drive that has a current version of Ubuntu either the BIOS or UEFI installs as they are totally different issues.

HP UEFI has been modified by HP to only boot Windows. So in UEFI mode we have to create work arounds.
It seems like the version of grub in MBR of sdb & sdc does not match install it is trying to boot.
Black screen is usually video driver issue.

What video card/chip do you have?
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

If you do not get grub menu, in BIOS hold shift key from BIOS screen. If UEFI press escape key at UEFI/BIOS screen (perhaps several times).

In fact it may be easier just to unplug all but one of the 14.04 drives and get it working before plugging in other drives.
How have you installed. Something else or one of the auto install options. With multiple drives only Something Else should be used.

---

### Post by Darth Riker on 2014-12-09
> **oldfred said:**
>  ... In fact it may be easier just to unplug all but one of the 14.04 drives and get it working ...

I agree with this. Probably worth doing before trying anything else.

Would it be possible to physically disconnect the drives so you only have one HDD connected to the machine?

That way you can see if its possible to boot to each drive with only that drive connected.

---

