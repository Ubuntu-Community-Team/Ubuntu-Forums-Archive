---
title: "Boot-repair error"
date: 2014-03-03
forum: Installation &amp; Upgrades
---

### Post by aeronutt on 2014-03-03
When I attempt to run boot-repair, I get the following:

[IMG]http://i.imgur.com/pa2UnNg.jpg[/IMG]

Everything else seems fine. (I run boot-repair sometimes after installing an additional OS to set my default OS).

gdisk reveals:


> 
[~] $ sudo gdisk /dev/sda
[sudo] password for zzz: 
GPT fdisk (gdisk) version 0.8.7

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): p
Disk /dev/sda: 488397168 sectors, 232.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): xxxyyyzzz
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 488397134
Partitions will be aligned on 2048-sector boundaries
Total free space is 4225 sectors (2.1 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1026047   500.0 MiB   0700  EFI System Partition
   2         1026048         9218047   3.9 GiB     8200  
   3         9218048        33794219   11.7 GiB    8300  
   4        33796096        58372095   11.7 GiB    8300  
   5        58372096        82948095   11.7 GiB    8300  
   6        82948096       488396799   193.3 GiB   8300  

Command (? for help): 


Thoughts?

---

### Post by oldfred on 2014-03-03
You are showing an efi partition which is for UEFI boot.

But you must be trying to convert or Boot into BIOS boot mode as that requires a bios_grub partition for grub to install correctly for BIOS boot. Boot-Repair cannot create that partition, you must have it first. But you should not need it.

But if system is UEFI, you should not be booting in BIOS mode.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by aeronutt on 2014-03-03
I'm not intentionally trying to boot into BIOS or convert to BIOS.  Does boot-repair not work with UEFI boot? Documentation states that it does. All I'm trying to do is use boot-repair to reinstall GRUB (and point to a different OS as default boot).

---

### Post by oldfred on 2014-03-03
In UEFI menu you will get two options to boot Ubuntu flash drive. One should say UEFI and the other not UEFI, but may not be clear that it is BIOS/Legacy/CSM type boot.

 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Another user with a Verbatim flash drive said he had these choices.
1. UEFI: VerbatimStoreNGo
2. VerbatimStoreNGo

---

### Post by aeronutt on 2014-03-03
Maybe my first and second posts are confusing. I'm not having a problem installing an OS (I'm not even trying to install an OS). I'm currently successfully booting ubuntu 13.10 using UEFI.  The description of my problem is simple; when I run boot-repair from Ubuntu 13.10 installed on my SSD, I get the error message that I posted in my first post. My SSD is configured as I posted running "gdisk", which shows no issues. I have no other known problems.

It appears boot-repair is expecting something configured in a way that nothing else expects.

---

### Post by oldfred on 2014-03-03
That can only occur if you boot Boot-Repair in BIOS mode as to correctly install grub-pc(BIOS) you have to have the bios_grub partition.
You should not get that info message if booted in UEFI and are not trying to convert to BIOS mode.

---

### Post by aeronutt on 2014-03-03
First, thanks for your help!  I must be doing something simple wrong.  Here are my boot settings. I read this as I'm booting in UEFI secure mode:

[IMG]http://i.imgur.com/NhQuUp9.jpg[/IMG]
[IMG]http://i.imgur.com/FquXC0D.jpg[/IMG]

And here are the boot-repair options that I'm using (I don't change anything here other than unselecting everything under 'other')

[IMG]http://i.imgur.com/l6eZ5E0.jpg[/IMG]
[IMG]http://i.imgur.com/bejqcek.jpg[/IMG]
[IMG]http://i.imgur.com/xCHmpQi.jpg[/IMG]
[IMG]http://i.imgur.com/3kYOYmp.jpg[/IMG]

---

### Post by oldfred on 2014-03-03
Please attached screen shots, not post in line. You can easily attach with paper clip icon in Advanced Editor.
Not all users have high speed Internet and screen shots inline slow download a lot.

Your UEFI settings look correct, If you want secure boot.
You may need to check efi or the efi partition option as it looks like you only have BIOS type entries.
Boot-Repair will convert a UEFI boot to BIOS and vice versa. But it totally un-installs grub & re-installs correct version. 
grub-pc for BIOS boot, but a bios_grub partition must exists
grub-efi for UEFI boot, but an efi partition must exist
And with secure boot in it includes the addition of signed version of grub & kernels.
Boot-Repair is really just running chroots & grub install commands, it cannot create partitions, so will complain if a required partition is missing for grub reinstall. If you just reinstall grub yourself, it tries and fails if correct partitions do not exist as it assumes you know you need that partition.

Post link to BootInfo report.

---

### Post by aeronutt on 2014-07-19
Reviving this thread...I need to do a clean install of 14.04, and would really like to get this issue figured out/fixed before I do that install.  Any one have ideas/thoughts?

---

### Post by oldfred on 2014-07-19
First step is how you boot install flash drive. 
If you boot it in UEFI mode it will install in UEFI mode.
If you boot it in BIOS mode it will install in BIOS mode.

Review these again:
       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

    
Other Dell - most versions seen similar with just different options based on what hardware your model has.
 Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)
Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell 17R Brightness
[http://ubuntuforums.org/showthread.php?t=2195650](http://ubuntuforums.org/showthread.php?t=2195650)
[http://ubuntuforums.org/showthread.php?t=2204287](http://ubuntuforums.org/showthread.php?t=2204287)

---

### Post by aeronutt on 2014-07-19
Thanks, but I'm not trying to install. Install, boot, etc all works fine.
But, boot-repair does NOT work. From first post:

[IMG]http://i.imgur.com/pa2UnNg.jpg[/IMG]

This makes me believe something is amiss.

---

### Post by oldfred on 2014-07-19
That is Boot-Repair saying that it is booted in BIOS Mode and to install a BIOS verison of grub needs the bios_grub partition.
I only have an old BIOS system but use gpt on all new drives. So I now add both an efi partition at beginning of drive for future use and a bios_grub partition for grub to install correctly to MBR and boot in BIOS mode.

You do need to be consistent. New systems allow you boot boot from UEFI/BIOS menu in either UEFI or BIOS mode. And they are not really compatible. Once you start booting in one mode you cannot convert to the other. Or from grub menu you can only boot systems installed in same boot mode.

If Windows is installed in UEFI mode, you do not need nor want the bios_grub partition unless you have a UEFI system that only installs in BIOS mode. Then Boot-Repair can convert a BIOS install of grub/Ubuntu to UEFI by uninstalling grub-pc for BIOS and installing the correct grub-efi version.

---

### Post by aeronutt on 2014-07-19
> **oldfred said:**
> That is Boot-Repair saying that it is booted in BIOS Mode and to install a BIOS verison of grub needs the bios_grub partition.
....

That's interesting, because my "bios" screens say I'm booting in UEFI, non-legacy.

Is there another way to tell how I booted  (UEFI or BIOS) other than using boot-repair?

---

### Post by aeronutt on 2014-07-19
FYI, I just ran this comand:
> [ -d /sys/firmware/efi ] && echo "Installed in EFI mode" || echo "Installed in Legacy mode" 

and it returned:

> Installed in EFI mode


---

### Post by LostFarmer on 2014-07-19
are you running 'boot-repair' from the installed linux or from a booted cd/usb device ?  to help you we need to see the boot-repair generated Bootinfo report as requested by oldfred.

---

### Post by aeronutt on 2014-07-20
I'm running boot-repair from installed linux.

Here's the bootinfo report:
[http://paste.ubuntu.com/7824340/]("http://paste.ubuntu.com/7824340/")

---

### Post by oldfred on 2014-07-20
You show no Windows install and sdb is Intel SRT which Linux sees as RAID.
Is this an Ultrabook. Lots of extra info on issues with Ultrabooks in link in my signature.

You also have efi boot files in sda1, but it is shown as a data partition not the efi or ESP boot partition. You need to use gparted and add the boot flag to sda1.

       Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
HP Envy  Windows 7 with MBR & SRT
[http://askubuntu.com/questions/159645/dual-boot-installation-of-ubuntu-12-04-lts-on-hp-ultrabook-envy-4-1002tx](http://askubuntu.com/questions/159645/dual-boot-installation-of-ubuntu-12-04-lts-on-hp-ultrabook-envy-4-1002tx)

---

### Post by aeronutt on 2014-07-20
It's a Dell Inspiron 15z. I don't remember it being marketed/sold as an ultrabook. It believe it does have an internal SSD on the mother board.

So change the flag on /dev/sd1 from "msftdata" to "boot" ?

[IMG]http://i.imgur.com/vlptHt9.png[/IMG]

---

### Post by LostFarmer on 2014-07-20
"So change the flag on /dev/sd1 from "msftdata" to "boot" ?"   yes, that is what mine has, only boot flag.

---

### Post by oldfred on 2014-07-20
The msftdata says it is a gpt(GUID) data partition not a gpt ESP or efi boot partition.

There now is a newer code as originally there was only one data partition type. Now Linux has its own GUID type.

 Change type code  to 8300 with dual booting with Windows on gpt
[http://www.rodsbooks.com/linux-fs-code/index.html](http://www.rodsbooks.com/linux-fs-code/index.html)
      
 [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

### Post by aeronutt on 2014-07-22
FYI, I do NOT have windows loaded.  Currently, I only have one OS loaded, 14.04.

So update. I made the recommended chage of "mfstdata" to "boot",  I loaded 14.04, and boot-repair now runs longer before it says it has an error. :)

Near the end of it's work (immediately at the start of the 'unhide boot menu' portion of boot-repair), it pops up:
[IMG]http://i.imgur.com/Tf3KkAM.png[/IMG]

I'm running boot-repair with the following options:
[IMG]http://i.imgur.com/yBJwt0i.png[/IMG]
[IMG]http://i.imgur.com/9BjUI5b.png[/IMG]

(I also tried 'update grub to its most recent version', and got the same popup)

Here's the boot-repair report:
[http://paste.ubuntu.com/7835445/](http://paste.ubuntu.com/7835445/)

Pretty frustrating...I'm about to scrub my whole SSD and just go back to BIOS!

---

### Post by oldfred on 2014-07-22
Please attach screen shots with paperclip icon in Advanced editor. Not everyone has high speed Internet and it can lock up system.

Boot-Repair often works to reinstall grub, but picks up a minor error and shows that.

But you have Intel SRT, see details in link in my signature on Ultrabooks which have that as standard.

Most found they can just turn on AHCI in UEFI and grub then correctly installs. The Intel SRT is seen as RAID and the desktop does not have the RAID drivers for grub to install to RAID, but with Intel SRT you do not want it installed to the RAID anyway.

You did not mention model computer? Some older installs, new 14.04 should be even better, but some new systems need even newer kernel, support software & video drivers.
 Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

Info on all Dell, not just precision models.
Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

 Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)
Dell 14z used Dell Recovery and Refind
[http://ubuntuforums.org/showthread.php?t=2125397](http://ubuntuforums.org/showthread.php?t=2125397)
[http://ubuntuforums.org/showthread.php?t=2179297](http://ubuntuforums.org/showthread.php?t=2179297)
 HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
Do not understand why flash cache is required, just install to SSD?
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)

---

### Post by aeronutt on 2014-07-22
"SATA Operation" is already set as AHCI
Model is Dell Inspiron 15z 5523, about 8 months old.

How do I find out what error boot-repair is finding?

---

### Post by oldfred on 2014-07-22
If you look at the BootInfo report in detail.

This will say grub installed correctly as exit code is 0.
 Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

But something throws an error so result is often this. But grub installed correctly and it should boot. I am always seeing the wrong grub version, but that may be because some package names have changed and Boot-Repair is not updated for 14.04. It used to use just grub-efi, but now it is grub-efi-amd64-signed for secure boot or grub-efi-amd64.

     
Wrong GRUB version detected.
Installing for x86_64-efi platform.
Installation finished. No error reported.

An error occurred during the repair.

---

