---
title: "Loading Operating System ... Read Error"
date: 2013-03-11
forum: Installation &amp; Upgrades
---

### Post by bmaster001 on 2013-03-11
Hi,

I have a computer with the following disks:

/dev/sda: SSD disk where I want to install Ubuntu 12.10
/dev/sdb: SSD disk with Windows 7
/dev/sdc: "normal" disk with data

I created a usb boot disk with the ubuntu iso, and installed ubuntu to /dev/sda. Grub was also installed to /dev/sda. Now when I reboot after the installation, I only get the message "Loading Operating System ... Read Error", white letters on black background, right after the bios info. No sign of grub. I guess it's a bios error. With the help of the dutch Ubuntu forums, I tried several things yet:

- when I leave the usb stick inserted while booting from harddisk, it works. 
- that brought me to this topic: [http://ubuntuforums.org/showthread.php?t=1903015](http://ubuntuforums.org/showthread.php?t=1903015). The solution there was to upgrade the bios, so I tried that, but it didn't help
- I recreated the installation stick in different ways (different tools, from within windows or ubuntu): no succes
- I tried to re-install grub with rescatux or from within ubuntu: no luck
- In the bios I changed from AHCI to IDE mode: grub works now, but I can't boot windows anymore because that was installed in ahci mode
- I tried boot-repair ([http://paste.ubuntu.com/5601888/](http://paste.ubuntu.com/5601888/)) which gave me a slightly different error: "error: no such device: 71eeb5f0-bcc6-49a8-b9a4-1fee266b58ec" followed by a "grub rescue" prompt
- boot-repair says "[COLOR=#000000]The boot files of [/COLOR][COLOR=#666666][[/COLOR][COLOR=#000000]The OS now in use - Ubuntu 12.10[/COLOR][COLOR=#666666]][/COLOR][COLOR=#000000] are far from the start of the disk". So I tried reinstalling ubuntu: first a /boot partition and then a root and swap partition. That gave me the original error again.

I'm running out of ideas now :-)  An option would be to leave the stick inserted at all times, but I would prefer a "real" solution. Any help is greatly appreciated!!

PS: If I forgot any important details, just let me know.. I've been messing around with this for a week now, so I could have forgotten something :-)
PPS: I'm' not using a UEFI bios. This is the url for my motherboard drivers: [/COLOR][http://www.gigabyte.com/products/product-page.aspx?pid=4015#bios](http://www.gigabyte.com/products/product-page.aspx?pid=4015#bios). I'm using bios version "FD".
[COLOR=#000000]

Thanks,
Tom[/COLOR]

---

### Post by bmaster001 on 2013-03-11
I know it's not polite to bump your own thread, but I see lots of replies from very smart people in other topics... Is my problem so exotic or difficult that nobody has any ideas? :-)

---

### Post by bmaster001 on 2013-03-12
Come on guys, someone? please? I really want to start using linux again, but this problem drives me crazy :-(

---

### Post by oldfred on 2013-03-12
Normally Boot-Repair just works. And Ubuntu works with AHCI on.
The issues with large drives has been where the boot files are beyond 100GB on drive. Your 120GB SSD with swap is not all that large.
I do have this in my notes and see that Boot-Repair added the ata boot parameter.
 Out of disk error add to grub install disk-module=ata or use Boot-Repair ATA Disk support

But it looks like grub installed in an embedded mode. i just do not know if with the ATA setting if that is how it installs. But I would not think you need that.

Both your flash drive which says gpt in one place and errors in another and your sdc1 seems to have mounting issues. I might run chkdsk from Windows on sdc1. Grub has to search system even though it knows where it is booting from, so perhaps not being able to search sdc1 is causing issues.

      
 Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
Arch suggests gpt for SSD. Only if installing Windows on older system may you want MBR as Windows only boots from gpt with UEFI. 
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

### Post by bmaster001 on 2013-03-12
Thanks for the reply!

I ran chkdisk, but it didn't find any problems on sdc1. 
The boot-repair log I linked to, is from a couple of days ago, and since then I tried reinstalling ubuntu a few times. Maybe it's more helpful if I try a fresh install again, and run boot-repair again? If so, I have some questions:

1) Do I really need the swap space? (I have 8 GB RAM)
2) Is it ok if I create one one big root-partition on the ssd disk? So no seperate /boot partition and things like that?
3) Can you tell me what options you would suggest in boot-repair? 
4) what's the best way to start boot-repair: I can boot to my ubuntu using the supergrub cd and run from there? Or is there a better way?
5) Would you suggest upgrading my bios to uefi?

There's a lot of info in the links you post... but most info is for finetuning ubuntu/linux for use with ssd disks. I think I have to make it boot first , before I can start finetuning... :-)

---

### Post by oldfred on 2013-03-12
You many never use swap with 8GB of RAM, but I still suggest some. Maybe 2GB. Some have said system may boot flaster as it does not have to search for swap, timeout and then work. Also if you want to hibernate swap has to be the size of RAM in GiB or larger than 8GB by 10 or 20%.

Since SSD is only 120GB I would think it should work. My SSD is 60GB but I split it in two so I have two / (root) partitions for different installs. All my data is on rotating drives. And I have an operating system on every drive.

Changing to UEFI now is a huge complications. Windows only boots with UEFI from gpt partitioned drives, so you would have to totally erase & reformat drives. I use gpt for all my new Ubuntu drives, but only have BIOS and do not use them to Boot Windows. In fact my old XP will not even read gpt partitioned drives, so I had to stop using XP. It was more due to the SSD needed the AHCI setting in BIOS to support trim and my XP does not have AHCI drivers.

Are you able to boot with Supergrub? If so reinstall grub from inside your install.

       #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
sudo dp#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

    
I only run Boot-Repair for BootInfo reports, so I am not sure what options your system may need.

---

### Post by bmaster001 on 2013-03-12
I can indeed boot with supergrub. I tried reinstalling grub with:

sudo grub-install &#8211;boot-directory=/boot /dev/sda

and then another time with

sudo dpkg-reconfigure grub-pc

but in both cases the error stays the same :-(

---

### Post by oldfred on 2013-03-12
Grub does not use boot flag. But a few BIOS have to have a boot flag on a primary partition, assumes Windows?
Do you have a boot flag on a primary partition? Error may be from BIOS.

---

### Post by bmaster001 on 2013-03-13
I just retried installing ubuntu using 2GB swap space, and one large partition for root mountpoint. 
There's a bootflag on /dev/sda1 (see screenshot), and one on /dev/sdb1 (the Windows system reserved partition).

---

### Post by oldfred on 2013-03-13
And you still get same errors?

And either Supergrub or an entry from flash drive will boot, but MBR will not? Very Strange.

I would make sure system is in AHCI mode and remove the ATA option.

---

### Post by bmaster001 on 2013-03-13
Yes, same error, and with the supergrub it boots just fine.
AHCI is definately ON because otherwise my Windows won't boot.

About removing the ATA option... how do I do that? I just tried boot-repair and enabled ATA support, which helps nothing. Maybe you mean I should try without enabling the ATA option? However, these are grub options, right? So if somehow the system is unable to load grub, will these options make any difference then? 

PS: new boot-info report: [http://paste.ubuntu.com/5611444/](http://paste.ubuntu.com/5611444/)

EDIT: Boot-repair has an option to repair or reinstall the MBR, so I tried that. Instead of "read error" I then got "operating system not found".  Then boot-repair again to reinstall grub (without ATA checkbox), and now I have the "read error" again. 

Maybe I could try to downgrade my bios version to see if that helps?

---

### Post by oldfred on 2013-03-13
I do not understand why grub is showing an embedded config file. That is for installs to a PBR or where a drive is mis-configured and there is not enough room for core.img right after the MBR. Do you have some DRM software or something else in sectors 1 -34 or whatever core.img now needs?

I would leave the Windows boot loader in sdb, but since sdc is just a data drive, you could experiment with installing grub to sdc and then boot that drive from BIOS. More of a test than a solution.

If booted
       sudo grub-install /dev/sdc

---

### Post by bmaster001 on 2013-03-13
Do you have an example of such software? I don't think I have that... but you never know. Is there way to find out?

I tried installing grub to sdc but I'm afraid it gives the exact same error. So it has nothing to do with the kind of disk, ssd or normal. It looks like it's a problem with the sata controller or something? Or maybe not, because the cdrom is on the same sata controller and with supergrub it boots just fine.

PS: I opened a case with gigabyte two days ago, but of course they have not responded yet...

---

### Post by oldfred on 2013-03-13
It was primarily flexnet which came with a lot of expensive licensed Windows software, which would be on the Windows drive usually sector 34 and grub has a work around for that. Some Dell's or others.
 
In Windows 7, had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, flexnet and a few others write into MBR


I found these in my notes, some are opposite of faster booting which you want with a SSD.
 UEFI or Intel new systems:
Gigabyte GA-X79-UD3 with I7-3820
Needed F6 to set ACPI=Off and nomodeset
pci=nomsi  or  ACPI=Off
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
fixed the problem by adding rootdelay to grub.cfg this allows time for the usb drive to load.

If you get grub menu you can experiment with boot options, but I doubt that Supergrub is adding any of them. I do not know details of Supergrub, but I thought it was just grub2 that searched for installs on a system and directly booted them. Which is all grub2 in MBR should be doing.

some other settings that users have commented on

 changing newer BIOS SATA 6 Gbit/s  from 6 Gbs to a SATA II - 3Gbs 
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker

---

### Post by bmaster001 on 2013-03-14
I don't think I have that kind of software. 
Thanks for the tips about the grub options, but I can't try them because I don't get to the point that I can use F6. My problem occurs before grub is loaded I think...
That description about supergrub sounds about right... that how it behaves here anyway: it searches all disks for bootable operating systems. 

In the bios I don't see anything related to the sata ports or virus protection. I tried some other options but nothing helps :-(

---

### Post by oldfred on 2013-03-14
From a grub menu you can press e and edit the boot line, or add paramaters. From Supergrub I might see if it auto adds some parameter that makes it work?

---

### Post by bmaster001 on 2013-03-15
I see. But am I right when I say that in my case that won't help me much because grub is not loading when I boot from harddisk? It needs to load first, before it can use any options I might add, no? See screenshot for the boot-line of supergrub when it has detected my ubuntu installation...


PS: Gigabyte answered to my ticket: "We don’t guaranty Ubuntu OS on our board. So that here is only a suggestion that you can refer to: https://help.ubuntu.com/community/Boot-Repair"
Very helpfull :-/

---

### Post by oldfred on 2013-03-15
Supergrub is using parameters, so it is more difficult to see the exact command it is using. But matching them up seems to be just the standard version. It is using -17.

Someone in another thread said the first version as installed of the kernel would boot, but all the newer ones from updates would not. And it seemed to be the first had the .efi extension which meant it would work in either secure boot or BIOS and all the newer ones did not have the .efi extension.

---

### Post by bmaster001 on 2013-03-15
Hmm, but my pc doesn't even get to the point of loading a kernel, so I think the boot-problem with newer kernels will be my next problem, if I ever get the current problem fixed :-)

---

