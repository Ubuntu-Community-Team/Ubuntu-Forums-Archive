---
title: "Installing Ubuntu Server 22.04 - boot-menu-choice will modified to a Linux menu"
date: 2022-03-13
forum: Installation &amp; Upgrades
---

### Post by lsepolis123 on 2022-03-13
I have a very old HP PC of 2009, installed Windows 10 and Windows 11(bypass restrictions) Home  OSs 
As a dual boot setup...

Installing Ubuntu Server 22.04 --- with the aim to make a local NextCloud.com File and Media Server, in the end as a Triple-Boot Setup, by doing this the startup the boot-menu-choice will be modified relatively as now is Windows kind:... to a Linux boot-choice-menu?



[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290144&stc=1[/IMG]

---

### Post by grahammechanical on 2022-03-13
Microsoft's boot loaders do not recognise Linux operating systems. Whereas, the Linux boot loader (Grub) does recognise Windows operating systems. To dual or triple boot Linux with Windows your motherboard will have to load the Grub boot loader which will present you with a boot menu listing Linux, Windows 10 and Windows 11.

Things can go wrong. Ubuntu and Windows have to be installed in the same mode (UEFI). The Ubuntu installer has to be loaded in UEFI mode then Ubuntu will be installed in UEFI mode and then the dual or triple boot will work.

Furthermore, Windows fast startup has to be turned off. Fast startup is a form of hibernation and the Linux boot loader (Grub) cannot load hibernated Windows operating systems. Windows updates turn hibernation back on. So, watch out for that.

There are other things to watch out for that others may advise on.

Regards

---

### Post by lsepolis123 on 2022-03-14
"
Ubuntu and Windows have to be installed in the same mode (UEFI)
"

My PC is BIOS only of year 2008-2009, Can install Ubuntu or Ubuntu Server...? what max version??

---

### Post by guiverc on 2022-03-14
> **lsepolis123 said:**
> 
My PC is BIOS only of year 2008-2009, Can install Ubuntu or Ubuntu Server...? what max version??

I'm replying to your on a 2009 dell box which is running Ubuntu *jammy* (what will be Ubuntu 22.04 LTS Desktop on release).  My box pre-dates intel's *i-serie*s CPUs, being a Core2 era cpu.

I use boxes as old as 2006 regularly for QA-testing Ubuntu *jammy* (ie. 22.04).

ps:  I'm using LXQt currently or Lubuntu, but it's a Ubuntu Desktop install with other desktops including LXQt/Lubuntu, Xfce/Xubuntu, Ubun..... installed

---

### Post by lsepolis123 on 2022-03-14
So, may Not be this a problem of installing of Ubuntu Server 22.04 LTS to this 2009 PC&#8230; correct?

is any way if in my dual boot system, after installed Ubuntu Or Ubuntu Server as triple boot, to have the latter Linux OS removed from system and fall back to dual boot&#8230;? As is now&#8230; Windows 10 + 11 dual boot

---

### Post by guiverc on 2022-03-14
My 2009 dell PC is dual boot; my OSes on it are Ubuntu *jammy* and Ubuntu *focal*.  ie. I have two Ubuntu systems installed.

Up until a few days ago, the 2006 HP machine I mentioned had 6 OSes installed on it  (*too many I felt, so I clean installed my last to it which is why they're now gone*).  But I use that box for QA-testing (ie. *Quality Assurance*) and a common QA *testcase* is to "*Install Alongside*", ie. you already have an OS installed; so the testcase is to *shrink *the installed OS creating disk space & the new install is placed into the created space. So from a single OS, the space was shrunk many times putting 5 other OSes installed on it too. In my case they were all variations of Ubuntu:  Xubuntu 20.04.4 twice, Ubuntu-MATE (20.04.4 + *i forget)*, Lubuntu (20.04.4 + *jammy*).  I regularly add, replace & even remove OSes in completing QA-test installs, so yes almost anything is possible.

**HOWEVER*, ***it's easy to make a mistake, so ensure you have good backups.  In my case the 2006 HP system I use is only used for *Quality Assurance*, thus it contains no information I care about. Yes I regularly re-install OSes on systems I do care about (ie. *using a system I have my own data on for QA too; doing this weekly*), however I know that even if I make a horrific mistake & destroy everything on the disk, it's only time I lose in needing to re-create what's on the disk as I have copies of *almost* everything on other boxes (ie. backups).

I've *never* made a serious mistake doing an actual install; but I'm doing many of them each week! however I'm also writing ISOs to thumb-drives many times per week, and I've overwritten a HDD containing backups in error, wiped a 11TB disk array....   ie. we all make mistakes, so ensure you have good backups.

---

### Post by lsepolis123 on 2022-03-14
1
So, in an MBR / BIOS HDD
How many primary and logical partitions can create?
2
Also, if in a triple boot system, last OS is Linux Ubuntu Server 22.04, if had deleted the Ubuntu Linux Server partition, the on startup boot menu should return to like was with two OS 10 + 11&#8230;? Or, needed extra action for this?

---

### Post by oldfred on 2022-03-14
With MBR(msdos) you can have 4 primary partitions.
One primary can be an extended partition which acts as a container for as many logical partitions as you want.

Windows only boots from a primary NTFS partition with the boot flag. Multiple installs of Windows typically only boot from one boot partition, and that install updates BCD to include boot of both systems. If primary partition you can have all Windows boot files in each NTFS partition.

Since BIOS only boots from MBR, and most of grub is actually in the Linux partition, you have to reinstall Windows boot loader to MBR before deleting a Linux partition. Or you just get grub rescue or grub>. 
Always have a Windows repair disk or Windows installer with repair console to reinstall Windows boot loader.

Since grub only boots working Windows, you often have to temporarily reinstall Windows boot loader, fix Windows or turn off fast start up and then restore grub to MBR. Windows updates often turn fast start up back on. Windows 7 with BIOS did not have fast start up, so issue was a lot less common.

With UEFI, you can always boot either Windows or Ubuntu/grub from UEFI boot menu, so reinstalling boot loaders is not required. Newer versions of Windows then work better from UEFI with gpt partitioning.

Old BIOS boot info:
To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth + words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/](http://www.multibooters.com/)

---

### Post by lsepolis123 on 2022-03-15
[COLOR=#313131][FONT=-apple-system][FONT=Verdana]You say:
[/FONT]&#8220;
Since BIOS only boots from MBR, and most of grub is actually in the Linux partition, you have to reinstall Windows boot loader to MBR before deleting a Linux partition[/FONT][/COLOR]
&#8221;

how to reinstall boot-loader to MBR&#8230;? Is OK the below: &#8230;? Setup w10, w11, Ubuntu 22.04 &#8212; in case remove Ubuntu&#8230;

these are ok to follow&#8230;?
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/repair-the-boot-menu-on-a-dual-boot-pc?view=windows-11](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/repair-the-boot-menu-on-a-dual-boot-pc?view=windows-11)

[https://neosmart.net/wiki/repair-dual-boot-configuration/#Repair_Windows_10on_a_dual-boot_system](https://neosmart.net/wiki/repair-dual-boot-configuration/#Repair_Windows_10on_a_dual-boot_system)

---

### Post by oldfred on 2022-03-15
Do not really know Windows repairs.
Since you want old BIOS/MBR, you need to find old Windows repair instructions.

Microsoft has required vendors to install in UEFI boot mode to gpt partitioned drives since 2012 and release of Windows 8. So almost all hardware is now UEFI and only a few still install in the old BIOS/MBR mode.

---

### Post by lsepolis123 on 2022-04-08
Ubuntu Studio 22.04 or Ubuntu 22.04 are able to do the job of Ubuntu Server 22.04, even unlike Server version have GUI... can they? Or better install Server version? 
That's wanted to have Server and Ubuntu GUI, ... in this very old PC..., well...?

---

### Post by oldfred on 2022-04-08
I do not have a server install.

But have seen where you can install server, a gui and then any apps you want.
You just do not install the desktop from any standard Ubuntu which then includes many default apps.

If you choose the desktop you also get the apps.
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

[https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

---

### Post by lsepolis123 on 2022-04-08
I prefer install Ubuntu Studio OS from the beginning, rather install 1_UbuntuServer and after install 2_Desktop.gui,...

Can I, like this, have server running in Ubuntu Studio 22.04...?

This will be for me - 1 user - or for family, only - 5 users... File Sharing, or Experimental for record videos for my YouTube channel... well...?

Ubuntu Studio can installed on 2009 PC &#128421; 64-bit, Windows 10/11 dual boot, Core 2 quad, ddr2 8gb, 1TB hdd...?

---

### Post by TheFu on 2022-04-08
If you want a desktop OS, then install a desktop OS.  You can install any server packages that you like.  Desktops have different integrations for networking and app-to-app connections than servers.  Most non-experts wouldn't like a pure server.

Also, if you plan to have nextcloud, I'd strongly suggest that server be compartmentalized through either a VM or a Linux Container, since the entire stack has specific dependencies which will likely conflict with many other server needs.  Keep each separate now, to avoid terrible conflicts later.

Nextcloud isn't a good media server. For that, check out jellyfin or miniDLNA.  Also, media servers that aren't running 16+ hrs a day are pretty useless.  Best not to dualboot at all.  With a C2Q, you can run Windows inside a virtual machine. Full screen and nearly all Windows applications will work just fine, except video editing 1080p+ resolutions and some Windows games.  I do office productivity and finance software inside a Windows VM and that works perfectly.  Before I moved my TV recording to Linux, I ran Win7 Media Center in a virtual machine - for recording only, not playback.

For recording videos, I use external hardware devices, so the computer isn't involved.  That's either an HDMI recording device that does in-line recording for the video sent to a monitor or using a normal Canon camera with local storage.  Then I use OBS to mux the camera video and the screen capture video into a single video for sharing.  Alas, that is a completely separate thread.

---

### Post by lsepolis123 on 2022-04-08
Now i thinking, only need file server...
Nextcloud.com can run on Ubuntu Studio OS 22.04...?
Ubuntu Studio can be installed on 2009 PC &#128421; 64-bit, Windows 10/11 dual boot, Core 2 quad, ddr2 8gb, 1TB hdd...?

---

### Post by TheFu on 2022-04-08
Nextcloud can run on almost any Linux and all flavors of Ubuntu.  The artificial desktop/server separation for programs that MSFT has inflicted doesn't happen on Linux, though if you want a desktop, start by installing a desktop release. Starting from a base server is usually too difficult for anyone not almost an expert.

I don't know why any Ubuntu flavor can't be installed on any computer capable of running Win7 or later.  Linux isn't Windows.  There is some bloat, and most of that will be self-inflicted by which DE you choose.  Gnome and Studio are likely the most bloated, but they will run.  Whether you will be happy with the performance depends on details not provided.  A 2009 PC certainly didn't get shipped with Win10.

---

### Post by lsepolis123 on 2022-04-09
I changed graphic card around 2016-2017, and installed Windows10, and in 2022 installed Windows11, using bypass techniques to create a bootable DVD w11 bypass restrictions,... Ubuntu installation should be as, boot from Ubuntu Studio OS 22.04 DVD and install it,... unallocated partition better create during Ubuntu installation or create in Windows 10...?

http://leonidassavvides.com/blog/2022/03/07/create-windows-11-installation-iso-dvd-that-bypass-restrictions-for-incredibly-old-bios-pcs-not-support-usb-booting-only-support-dvd-boot/

---

### Post by oldfred on 2022-04-09
You want to use Windows to shrink the NTFS partition and reboot so it can run chkdsk which is required after any resize.
You cannot create Linux partitions in Windows.

You can partition in advance with gparted or create partitions with the installer.

If you installed Windows in UEFI boot mode which you should have, be sure to install Ubuntu in UEFI mode.
How you boot install media - UEFI or BIOS, is then how it installs. It will use the existing ESP - efi system partition.

---

### Post by TheFu on 2022-04-09
In 2009, EFI was Apple only.  Not for Windows. I'd bet this is a legacy install if the system really is from 2009.  

And this probably needs to be said clearly.  22.04 is NOT released and someone new to Ubuntu shouldn't be installing it pre-release.  I won't be installing any flavor of 22.04 until mid-June at the earliest. I've learned that there are early bugs and issues which aren't known. As someone new to Ubuntu, I assume this based on the questions being asked, then it wouldn't be a good idea to be an early adopter for any release.

---

### Post by lsepolis123 on 2022-04-10
Please note i listen that ubuntu flavors are currently in beta
I do Not plan install Ubuntu Studio OS 22.04 now, but - will install end of April 2022
My Very old experimental pc supports Ubuntu Studio 22.04? 
VERY OLD PC OF the 2008 – 2009 year:
Product: HP Pavilion Elite M9372.Gr Desktop PC 2008-2009
Operating System: dual boot Microsoft Windows 10 (64-Bit) Home/Windows 11 Home
PC is Intel Core 2 Quad 64-bit / RAM 8GB DDR2 / DVD DRIVE / Graphics NVIDIA GeForce GT 730 2GB

If plan use GUI as well Server functionality ONLY ONE AT A TIME, IS OK... TRIBLE BOOT Or run in VirtualBox? 

As of Linux education i give Linux Foundation centos exam but scored 49% (pass 75% i think required)

---

### Post by lsepolis123 on 2022-04-10
Ubuntu 22.04
Release Candidate: April 14, 2022
With the final release of Ubuntu 22.04 LTS on April 21, 2022

This is valid for All flavours like Ubuntu Studio...?

Ubuntu Studio 22.04 has the same System Requirements as below 21.10...?

https://ubuntustudio.org/download/
System Requirements
CPU:
RAM:
Drive Space:

Required:
Intel Core 2 Duo equivalent
2GB
16GB	

Recommended:
Intel Core i5 equivalent or better
8GB
64GB, more for audio/video work

===

---

