---
title: "Cannot install Ubuntu &gt; No HDD/partition detected"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by minmingdotnet on 2008-08-07
Apparently I cannot install any Linux on my machine. My machine is Kohjinsha SC. I tried Ubuntu, GPart, SuSe, and all are unable to detect my hard disk. 

I tried pci=nomsi and some apci options but it still does not work. Any ideas? I don't understand why XP and Vista can see the hdd no problems but current Linux kernel cannot work. 

Thanks.

---

### Post by f37u5g0d on 2008-08-07
I heard a wild rumor that windows vista will not allow you to dual boot after service pack one.  Do you have service pack one for vista installed on that computer?

---

### Post by tommcd on 2008-08-07
Is this your computer:
[http://jkkmobile.blogspot.com/2007/10/linpus-linux-lite-demo-on-kohjinsha-sh6.html](http://jkkmobile.blogspot.com/2007/10/linpus-linux-lite-demo-on-kohjinsha-sh6.html)
Anyway, can you bootup the Ubuntu live CD, open a terminal (applications > accessories > terminal) and run "sudo lspci -v". Post the output here, and put it inside code tags ```

``` so it is easier to read. 
You may have to adjust some BIOS settings to get the install CD to recognize your hard drive.

EDIT: You could also try
 "acpi=off"
"acpi=force pci=noacpi"
"hda=noprobe"
as boot options, but post the specs of your system first.

---

### Post by minmingdotnet on 2008-08-11
That's not my computer. This is the one: [http://jkkmobile.blogspot.com/2008/07/kohjinsha-sc3-umpc-last-impressions.html](http://jkkmobile.blogspot.com/2008/07/kohjinsha-sc3-umpc-last-impressions.html)

This is the specs of my computer. Thanks!

```

00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 06)
	Subsystem: Inventec Corporation Unknown device 0032
	Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 06) (prog-if 00 [VGA controller])
	Subsystem: Inventec Corporation Unknown device 0032
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at e880 [size=8]
	Memory at d0000000 (32-bit, non-prefetchable) [size=128M]
	Memory at dff60000 (32-bit, non-prefetchable) [size=128K]
	Capabilities: [d0] Power Management version 2
	Capabilities: [b0] Vendor Specific Information
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 06)
	Subsystem: Inventec Corporation Unknown device 0032
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dff5c000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: cfc00000-cfcfffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [90] Subsystem: Inventec Corporation Unknown device 0032
	Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [90] Subsystem: Inventec Corporation Unknown device 0032
	Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 06) (prog-if 00 [UHCI])
	Subsystem: Inventec Corporation Unknown device 0032
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at e480 [size=32]

00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 06) (prog-if 00 [UHCI])
	Subsystem: Inventec Corporation Unknown device 0032
	Flags: bus master, fast devsel, latency 0, IRQ 17
	I/O ports at e080 [size=32]

00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 06) (prog-if 00 [UHCI])
	Subsystem: Inventec Corporation Unknown device 0032
	Flags: bus master, fast devsel, latency 0, IRQ 18
	I/O ports at ef00 [size=32]

00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 06) (prog-if 20 [EHCI])
	Subsystem: Inventec Corporation Unknown device 0032
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at dff5bc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 06)
	Subsystem: Inventec Corporation Unknown device 0032
	Flags: fast devsel

00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 06) (prog-if 80 [Master])
	Subsystem: Inventec Corporation Unknown device 0032
	Flags: fast devsel
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]



```

---

### Post by castroneves on 2008-08-11
I am having a similar problem, bought some new hardware, the motherboard being
Asus M2R32-MVP with AMD 580X chipset

Windows installed aok, Fedora Installed aok, on deciding I didnt really like fedora I went to put ubuntu on but no matter what I try it will not detect my HDD :@....out of curiosity I installed gparted in fedora and sure enough that picked up the HDD. Is this a simple case of ubuntu not containing the SATA drivers for this chipset, or am I doing something wrong here?

---

### Post by minmingdotnet on 2008-08-11
Well, my case is that gparted, ubuntu 8.04, suse 10/11, acronis home image (which its bootable recovery uses linux i think) all did not detect my harddisk.

---

### Post by minmingdotnet on 2008-08-12
anyone have any ideas how to solve my problem?
thanks.

---

### Post by WulfenMortys on 2008-08-13
I'm having the same problem - installation refuses to detect any hard drives whatsoever.

Any assistance would be appreciated! :D

Thank you.

---

### Post by minmingdotnet on 2008-08-14
i tried a few boot options but still cannot detect my hdd. there is nothing to tweak in my bios. my bios is very limited. any ideas?

---

### Post by all-linux on 2008-08-15
Hi, I have exactly the same issue with my Kohjinsha SC3.
I was using the Ubuntu installer/Live CD as well as Wubi.
Same thing. During Ubuntu start, no HDD is found.
As described above, the BIOS of this device is very...very limited, so nothing to tweak around. Any ideas?

---

### Post by tommcd on 2008-08-16
Just to let you guys kow I have not abandoned this thread. I have been googleing the crap out of my laptop for your PC and it's chipset:
[http://www.pocketables.net/2008/07/review-kohjinsh.html](http://www.pocketables.net/2008/07/review-kohjinsh.html)
As you can see it uses the Intel SCH US15W (Poulsbo) chipset, which I believe is a chipset designed for UMPCs with the Atom CPU. I have not been able to find much about it. I can only assume it is new, so there is not much info available. It is all Intel hardware though, so perhaps you would have more luck with a newer kernel, like on Ubuntu 8.10 Intrepid Ibex.

Regarding the ASUS-M2R32-MVP, If you google [Asus-M2R32-MVP linux] at [http://www.google.com/linux](http://www.google.com/linux), you will find a lot of threads with the same problems. This guy says Ubuntu, but not Suse, worked on that motherboard:
[http://forums.opensuse.org/archives/sf-archives/install-boot/338265-asus-m2r32-mvp.html](http://forums.opensuse.org/archives/sf-archives/install-boot/338265-asus-m2r32-mvp.html)

However, I don't see the motherboard listed here for linux compatibility:
[http://linux-tested.com/results_servera.html#asus](http://linux-tested.com/results_servera.html#asus)

If you go to the Asus support website for the M2R32-MVP, you will se that they have chipset and audio drivers for linux:
[http://support.asus.com/download/download.aspx?SLanguage=en-us](http://support.asus.com/download/download.aspx?SLanguage=en-us)
Scroll down the page to find them. However, they are SATA and RAID drivers, but for Suse and Red Hat. So they may not work in Ubuntu, plus, I'm not sure how you could install them if you can't even install the OS.
Again, all I can suggest is try Ubuntu 8.10 for the newer kernel just to see if it will work.

---

### Post by all-linux on 2008-08-16
OK, last night I went over to the Fedora camp and downloaded V.9 and V.10-alpha LiveCD's. With V.9 I got the same issue, no harddrive detected. Using V.10-alpha (2.6.27-0.166.rc0 / i686) ... bang there is the 60GB drive including all partitions created using Vista SP1 (also showing correct partition size and types). 

Seems we are just a bit early, installing Linux on this new devices.

So, now I will look for the Ubuntu alpha (last post was talking about 8.10) and try the same thing again.

I'll let you know if it worked.

---

### Post by all-linux on 2008-08-22
I used the ubuntu/Intrepid alpha 4 LiveCD as well as the Installer CD. Both LiveCD and Installer CD detected the Disk and allowed to partition it. After I installed Intrepid Alpha 4 and chose to boot ubuntu using grub, the system hangs. I tried several boot/kernel parameters, but even the debug level does not print any information.

I will try Alpha 5 as soon as it will be released.

---

### Post by loboris on 2008-08-27
Ubuntu Gutsy (7.10) installs and runs fine on Kohjinsha SC3. Audio works if linux-ume is installed. Video driver is VESA, so no Compiz and 3D.

---

### Post by hanzenegger on 2008-08-30
> **loboris said:**
> Ubuntu Gutsy (7.10) installs and runs fine on Kohjinsha SC3. Audio works if linux-ume is installed. Video driver is VESA, so no Compiz and 3D.

Hi loboris,

I was running into the same problem on my SC3 with Hardy. Thank you for the tip. 7.10 installs fine, but for me it still hangs at boot-up, right after grub loads the kernel, just like Interpid alpha does.

I tried installing grub to both the mbr and the boot partition, but that makes no difference.

Did you get this problem too? How did you solve it?

---

### Post by Sangdrax on 2008-09-01
Hello all. 
I have a Kohjinsha SC3. I installed Ubuntu Hardy 8.04. I used the LiveCD, but before installation, open a terminal and write: 

# sudo modprobe ide-generic

With that the installation will detect the hard drive. 

The problem is that after installation and reboot, the kernel linux loading freezes. I tried other distros, like OpenSUSE 10 (the last one). The problem was the same. 

To solve the problem I had to run a virtual machine in my Desktop PC, install Suse. Download a kernel source, compile the kernel with support for the chip from Toshiba SC.... Sorry, I don't remember the full name, but it was under "Devices" hard drive sectin. In the "make menuconfig" command. That way, Suse started properly. 

Using gOS 3 gadgets, which is a distro based in Ubuntu didn't work, it froze during the boot and strange color symbols appeared on the screen. 

This evening I will try the same using Ubuntu 8.10 (Hardy Ivex Alpha 4). 


One last question: anyone that could boot with the LiveCD of Ubuntu 8.10 of Ubuntu 7, did you detect the ethernet ? I think it uses the ASIX chipset, the module loads perfectly, but eth0 doesn't appear. 

I hope to hear some answers.

---

### Post by minmingdotnet on 2008-09-04
Wow. There are actually so many people trying to install Linux on SC3. I already gave up and decided to re-visit this thread. 

In the end, I decided to install on a USB drive, but Ubuntu somehow refuse to work. I then install OpenSUSE 11. But wireless driver seem to be unavailable. Did anyone get the wireless to work properly?

I am interested in the Ubuntu 7.10 installation. Does it boot up fine?

---

### Post by all-linux on 2008-09-05
As mentioned above, 7.10 installs fine, but hangs at boot-up.

---

### Post by all-linux on 2008-09-08
This weekend I tried alpha-5, but same issue.
I still think it's grub making problems, not the kernel. I could even boot ubuntu installed on the harddisk, but the procedure to do this is very strange.
1. Boot from the installer CD
2. Select - Boot from first harddisk
3. In Grub menu select - Boot recovery option (single)
Then it boots ubuntu, therefore I doubt the kernel itself is having problems.
Anyone with another idea/proposal?

---

### Post by omegamusic on 2008-10-20
Hi, I was having this problem too...
If you run the liveCD then open a terminal and type

sudo modprobe ide-generic

you should have no problems...
except of course where i'm up to now which is Ubuntu won't boot. :(

---

### Post by tommcd on 2008-10-21
> **Sangdrax said:**
> Hello all. 
I have a Kohjinsha SC3. I installed Ubuntu Hardy 8.04. I used the LiveCD, but before installation, open a terminal and write: 

# sudo modprobe ide-generic

With that the installation will detect the hard drive. 

The problem is that after installation and reboot, the kernel linux loading freezes. I tried other distros, like OpenSUSE 10 (the last one). The problem was the same. 


If you have managed to install Ubuntu by opening a terminal and running **sudo modprobe ide-generic**, and then when you try to boot it just hangs, then you probably need the ide-generic module loaded at bootup. To do this, boot from the Ubuntu live CD, mount your Ubuntu partition, and edit the **/etc/modules** file. Add ide-generic to the file, and save and exit. Then when you boot Ubuntu from the hard drive the module should load on bootup and allow you to boot. See this:
[https://help.ubuntu.com/community/Loadable_Modules?highlight=(modules)|(add](https://help.ubuntu.com/community/Loadable_Modules?highlight=(modules)|(add))
So boot from the live CD. Lets say Ubuntu is on /dev/sda1. Open a terminal and run:
```
sudo mount /dev/sda1 /mnt
gksudo gedit /mnt/etc/modules
```
Then just add ide-generic to the bottom of the file, and save and exit. Then unmount your Ubuntu partition:
```
sudo umount /dev/sda1
```
Then reboot and (hopefully) the kernel module ide-generic should load on bootup and allow Ubuntu to boot.

---

### Post by qwertymodo on 2008-10-21
Just curious, is the HDD in question a SATA interface?  I had this same problem with my custom-built desktop and a SATA CD-ROM.  If that's the problem at least you can boot your live CD, I spent about 2 weeks where even the live disk wouldn't load ANYTHING, I couldn't even check the disk for errors.  I used the all_generic_ide boot flag in grub (highlight the boot option you normally use, hit 'e', highlight the entry that has kernel in it, hit 'e' again, type 'all generic_ide' without the quotes at the end, ok, ok, boot).  Sounds like basically the same as above, just a different way of doing it.  Or if you say that 8.10 works you could just wait for the stable version in a just over a week (October 30th I believe).

At least Ubuntu can run SATAs with a boot flag... XP I had to slipstream SP3 into the installation :P

---

### Post by minmingdotnet on 2008-11-04
Have anyone tried the recent 8.10 ?

---

### Post by FourthCoffee on 2009-06-16
> **tommcd said:**
> If you have managed to install Ubuntu by opening a terminal and running **sudo modprobe ide-generic**, and then when you try to boot it just hangs, then you probably need the ide-generic module loaded at bootup. To do this, boot from the Ubuntu live CD, mount your Ubuntu partition, and edit the **/etc/modules** file. Add ide-generic to the file, and save and exit. Then when you boot Ubuntu from the hard drive the module should load on bootup and allow you to boot. See this:
[https://help.ubuntu.com/community/Loadable_Modules?highlight=(modules)|(add](https://help.ubuntu.com/community/Loadable_Modules?highlight=(modules)|(add))
So boot from the live CD. Lets say Ubuntu is on /dev/sda1. Open a terminal and run:
```
sudo mount /dev/sda1 /mnt
gksudo gedit /mnt/etc/modules
```
Then just add ide-generic to the bottom of the file, and save and exit. Then unmount your Ubuntu partition:
```
sudo umount /dev/sda1
```
Then reboot and (hopefully) the kernel module ide-generic should load on bootup and allow Ubuntu to boot.

Dam, mine still does not show my hard drives.:(

---

### Post by joeradtke on 2009-06-16
I have the same problem.  the install disc doesn't recognized my hard drive.  I can run from the live cd, but the partitioner says no device detected.  I have tried two hard drives a Western Digital Green 1tb and Seatech Barracuda 1.5tb.  I  can load windows which I have no use for and only did to add more data to the troublshooting.  I have tried the various no apic, etc. options to no avail.  I tried the sudo modprobe ide-generic which didn't help -- my drive is SATA though.  Is there a modprobe command for SATA.  I tried sudo modprobe sata-generic but it didn't recognize it.  My install cd's (both 7.04 and 8.04 work on any other computer).

This is a homebuilt computer with an ASUS p6t deluxe v2 motherboard and pentium i7 processor.  I am using a PATA pioneer optical drive, as when I used a SATA optical drive, I got the Busybox problem.
There don't seem to be any obvious bios options to try.  

I have also tried the jumper in the memory to slow it down which didn't help.  The hard drive is recognized in the bios and obviously by windows as it uses it without a whimper.

Help???

---

### Post by tommcd on 2009-06-17
> **joeradtke said:**
>  My install cd's (both 7.04 and 8.04 work on any other computer).

This is a homebuilt computer with an ASUS p6t deluxe v2 motherboard and pentium i7 processor.  I am using a PATA pioneer optical drive, as when I used a SATA optical drive, I got the Busybox problem.
There don't seem to be any obvious bios options to try.  

According to this:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131365](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131365)
your motherboard uses the Intel X58 / ICH10R chipset. This is a relatively new chipset. Ubuntu 7.04 is way too old  for it's kernel to support this. Also, 7.04 is no longer supported. If 8.04 does not recognize your hard drive controller, you would probably have better luck using the newest version, Ubuntu 9.04, since it has a much more recent kernel.

---

### Post by SFODA551 on 2009-06-17
I am running into (I think) the same difficulties in recognizing the hard drive. I am a new user to Linux and to anything beyond GUI interface.

I followed all of the procedures for installing both 8.04 and the newer version. Plus, after my downloads didn't work I ordered a copy from On-disk to ensure that it wasn't a download/copy issue. But in each case after the kernel started loading it would display the following:

ATA3.00: STATUS{DRDY ERR}
ATA3.00: BUFFER I/O ERROR ON DEVICE SDA LOGICAL BLOCK 61049616
ATA3.00: BMDMA2 STAT 0x686c1009 cmd 25/00:08:68:59:1c/00:00:1d:00:00/e0 tag 0 dma 4096

Followed by three of following and then it would cycle again. The only change is the number on the end of the logical block.

ATA3.00: STATUS{DRDY ERR}
ATA3.00: EXCEPTION Emask 0x0 Sact 0x0 SER 0 0x0 Act0 0X0
ATA3.00: BMDMA2 STAT 0x686c1009 cmd 25/00:08:68:59:1c/00:00:1d:00:00/e0 tag 0 dma 4096

Eventually (after about 5 minutes of this jibberish - I am ignorant of what the code means) it does recognize the disk and boots up in the disk version. But, it stops when it gets to partitioning the hard drive. It does not find the hard drive at all.

This was a brand new machine that I purchased hoping to use Linux and get away from MS. So it has not been partitioned or monkeyed with by any other OS.

The following are my hardware specs. If I am using this system, is it too new for the 8.04 and others? I was hoping to use the 8.04 because it appears (from what I can read) to have a lot of bugs worked out of it.

Also, if I went to another linux software would I run into these issues as well?




Mother board: ECS RC410-M LGA775 DDR2 PCIe x16 SATA HP       

Processor: INTEL PENTIUM 4 520 2.8GHZ LGA775 CPU

Hard Drive: 80GB SATA150 7200RPM

Video Card: ATI Radeon HD3450 256MB DDR2 DVI / VGA

DVDRW BURNER DVD/R/RW READER / WRITER

REALTEK 10/100Mbps FAST ETHERNET CARD ADAPTER (LAN)

---

### Post by C0NSTANTIN on 2009-06-17
i think the new kernel is having problem recognizing SATA2 ... i googled up till i got blisters on my fingers ..

i installed xubuntu 9.04  from live cd ... clean install ... updated

next thing i saw when i booted was that 

> [12.060011] ata2: SRST failed ERRNO=-16
[22.068010] ata2: SRST failed ERRNO=-16
....

Alert! /dev/disk/my-uuid/<the id of my hdd> dropping down to a shell
... 
kind of error ...

---

### Post by joeradtke on 2009-06-17
Thank you TOMMCD.  That solved it for me.  I could kick myself.

---

### Post by C0NSTANTIN on 2009-06-18
if you have data still stored onto ext4 lost partitions ... here's what i did to recover them ...


> recovering the /home partition
-download and install the craked [piracy fan .. srry] version of [www.PTDD.com's](www.PTDD.com's) Partition Table Doctor 3.0
-the program will see ext4 file system as ext3 file system

recovering the data from the newly recovered partition
-download and install the craked [again .. srry] version of ...srry... this one's freeware :p
[http://www.data-recovery-software.net/Linux_Recovery.shtml](http://www.data-recovery-software.net/Linux_Recovery.shtml)
-again ... the program will see ext4 file system as ext3 file system
-run a scan first then recover

this worked for me.

so now i recovered all my 17GB of data... 

next step ... reinstalling xubuntu 9.04

planning on formating all partition tables ... making sure there isn't a trace of bad code not letting live CD xubuntu finding the HDD's uuid ...

---

### Post by Volume on 2009-07-08
I too am having a problem installing 8.04 due to the non-detection of my hard drives.  I have 4 new SATA- WD 500 Gb HDs in my new system build, and they are not detected at all in the graphical installer for 8.04.  

I am about to try 9.04 and will let all know how it works!

Steve

---

### Post by Volume on 2009-07-08
It worked!  Using the 9.04-alternate install worked.  It is worth noting that I also had the ICH10 chipset mobo, and the jump from 8.04 to 9.04 worked

---

### Post by themoddingden on 2009-07-09
Hi;
Is there a work around for the 750 chipset yet?
The only distro that installs on this is a beta of supergamer.
I tried 64bit and 32 bit beta and final of 9.04.
It will not see my sata drive at all.
my board is an xfx with the 8200 onboard
1gig ram
was a xfx 8600gt xxx now an evga 9800gt
wd 320 sata
lg dvd+/- burner
onboard sound and nic
any help would be great.

---

### Post by tommcd on 2009-07-10
> **themoddingden said:**
> Hi;
Is there a work around for the 750 chipset yet?
The only distro that installs on this is a beta of supergamer.
I tried 64bit and 32 bit beta and final of 9.04.
It will not see my sata drive at all.
my board is an xfx with the 8200 onboard

What motherboard is this exactly (make & model #). If Ubuntu 9.04 will not see your hard drive, when the Ubuntu CD boots up, hit F6 and enter:
```
all_generic_ide
```
and hit enter. This will force the IDE driver when Ubuntu loads up. 
If that does not work, you could try Ubuntu 9.10 alpha2:
[http://cdimage.ubuntu.com/releases/karmic/alpha-2/](http://cdimage.ubuntu.com/releases/karmic/alpha-2/)
This will have a newer kernel that may work with your motherboard chipset. Keep in mind that this is alpha software, so some bugs and problems are to be expected.

---

### Post by themoddingden on 2010-01-25
hi tom;
ok here the infio:
  
XFX GeForce 8200 AMD SOCKET 940 DDR2 (Edit)

Product Code: MI-A78S-8209

---

