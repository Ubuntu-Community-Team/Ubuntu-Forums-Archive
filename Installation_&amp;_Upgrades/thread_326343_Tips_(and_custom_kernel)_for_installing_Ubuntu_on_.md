---
title: "Tips (and custom kernel) for installing Ubuntu on Core 2 Duo systems"
date: 2006-12-27
forum: Installation &amp; Upgrades
---

### Post by xtknight on 2006-12-27
**_What you Need_**
[list][*]Alternative boot/install media device (one other than a PATA drive/ethernet if you're using the unsupported JMicron PATA controller/ethernet, or other unsupported boot devices, common with C2D setups): A USB CDROM drive will work


[*]Custom kernel: after you boot into your installed Dapper system, you will need to install the custom kernel to enable PATA drive and ethernet support for your C2D system[/list]

**Note: If you have a new NVIDIA card (6xxx, 7xxx), boot Dapper into safe graphics mode when installing to avoid graphics corruption.  You can install the nvidia driver later on.**

**_Details_**

I feel that Ubuntu is losing a big user base (especially among gamers/enthusiasts) due to lack of support for many C2D mobos.  OpenSUSE 10.2 works without issue.

Installing Ubuntu on a Core 2 Duo system is sure to be a frustrating process.  For me, my ethernet controller wasn't detected, nor my IDE (CD/DVD) drives.  I effectively had no installation media since none of it could be detected.  Dapper was able to see my SATA hard disks, but Edgy was not able to detect my ethernet, IDE or SATA disks.

What I did was to boot Dapper off a USB CDROM drive (don't forget to take out all the CDROMs in your IDE drives to prevent confusing the BIOS or Ubuntu).  I was able to install Dapper onto my system, but upon boot neither my ethernet or PATA/IDE drives were detected.

I then (with working Windows or Debian installs) manually downloaded all the dependencies for compiling a kernel and put them on a USB hard disk for easy access (although Dapper could access my SATA drives, so I didn't need the USB hard disk).

**_New kernels_**
[list][*]**32-bit kernel (2006-12-27, UNTESTED, compiled under Debian, 2.6.19.1 w/ JMicron/ICH8 support, P4 optimized, SMP, DVB support completely disabled)**

[kernel-image-2.6.19.1_c2d_i386.deb]("http://xtknight.atothosting.com/ubuntu/dapper/i386/kernel-image-2.6.19.1_c2d_i386.deb")
[kernel-headers-2.6.19.1_c2d_i386.deb]("http://xtknight.atothosting.com/ubuntu/dapper/i386/kernel-headers-2.6.19.1_c2d_i386.deb")


[*]**32-bit kernel (*2006-12-28 update*, compiled under Edgy, 2.6.19.1 w/ more PATA/SATA/Ethernet support, SMP, optimizations, erroneous DVB support disabled)**

[linux-image-2.6.19.1_c2d_i386.deb]("http://xtknight.atothosting.com/ubuntu/dapper/i386/20061228/linux-image-2.6.19.1_c2d_i386.deb")
[linux-headers-2.6.19.1_c2d_i386.deb]("http://xtknight.atothosting.com/ubuntu/dapper/i386/20061228/linux-headers-2.6.19.1_c2d_i386.deb")


[*]**64-bit kernel (2006-12-27, compiled under Dapper, 2.6.19.1 w/ JMicron/ICH8/Marvell Ethernet support, EM64T optimized, SMP, DVB support completely disabled)**

[kernel-image-2.6.19.1_c2d_amd64.deb]("http://xtknight.atothosting.com/ubuntu/dapper/amd64/kernel-image-2.6.19.1_c2d_amd64.deb")
[kernel-headers-2.6.19.1_c2d_amd64.deb]("http://xtknight.atothosting.com/ubuntu/dapper/amd64/kernel-headers-2.6.19.1_c2d_amd64.deb")


[*]**64-bit kernel (*2006-12-28 update*, compiled under Edgy, 2.6.19.1 w/ more PATA/SATA/Ethernet support, SMP, optimizations, erroneous DVB support disabled)**

[linux-image-2.6.19.1_c2d_amd64.deb]("http://xtknight.atothosting.com/ubuntu/dapper/amd64/20061228/linux-image-2.6.19.1_c2d_amd64.deb")
[linux-headers-2.6.19.1_c2d_amd64.deb]("http://xtknight.atothosting.com/ubuntu/dapper/amd64/20061228/linux-headers-2.6.19.1_c2d_amd64.deb")[/list]

I cannot guarantee that the 32-bit kernel will work.  I actually compiled it under Debian but using a 64-bit Ubuntu config, so I have no idea whether or not it'll work.  My hunch is that it will, but it definitely only installs on 32-bit systems.  The 64-bit kernel works great.  After installing it onto my crippled Dapper, I instantly had ethernet access and I could access all of my IDE drives.  The only thing is, the boot splash screen doesn't seem to work (though it never has for my custom kernels).  These are just intended to get you off the ground and to allow you ethernet support.  After that, you can recompile the kernel to your needs.

Stability thus far has been perfect with both the old and new kernels.  I believe that Dapper will install correctly under either the Intel ICH8's AHCI or PATA emulation mode.

As for Edgy, I'm not sure how to make it work.  I would have to modify the debian-installer kernel.  Hosting the custom package would be difficult as well since its in the magnitude of 700MB.

If the demand is high enough I will spend more time compiling the kernels to you guys' needs.  Please let me know if you have a C2D and are having a tough time installing Ubuntu.  Also list your motherboard, BIOS version, CPU, and IDE controllers.

_**My specs:**_

Gigabyte GA-965P-DS3
Intel Core 2 Duo E6300
JMicron JBM36x PATA controller
Intel 965P Express chipset (ICH8 south bridge)

The following commands will give you the needed info:

$ sudo lshw | grep Motherboard -A 2
```
       description: Motherboard
       product: 965P-DS3
       vendor: Gigabyte Technology Co., Ltd.
```

$ sudo lshw | grep Motherboard -A 20 | grep firmware -A 5
```
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F7 (10/12/2006)
          size: 128KB
```

$ sudo lshw | grep *-cpu -A 2
```
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
```

$ lspci | grep IDE
```
0000:00:1f.2 IDE interface: Intel Corporation: Unknown device 2820 (rev 02)
0000:00:1f.5 IDE interface: Intel Corporation: Unknown device 2825 (rev 02)
0000:03:00.1 IDE interface: Unknown device 197b:2363 (rev 02)
```

$ lspci | grep Unknown
```
0000:00:00.0 Host bridge: Intel Corporation: Unknown device 29a0 (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation: Unknown device 29a1 (rev 02)
0000:00:1a.0 USB Controller: Intel Corporation: Unknown device 2834 (rev 02)
0000:00:1a.1 USB Controller: Intel Corporation: Unknown device 2835 (rev 02)
0000:00:1a.7 USB Controller: Intel Corporation: Unknown device 283a (rev 02)
0000:00:1b.0 0403: Intel Corporation: Unknown device 284b (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation: Unknown device 283f (rev 02)
0000:00:1c.3 PCI bridge: Intel Corporation: Unknown device 2845 (rev 02)
0000:00:1c.4 PCI bridge: Intel Corporation: Unknown device 2847 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation: Unknown device 2830 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation: Unknown device 2831 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation: Unknown device 2832 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation: Unknown device 2836 (rev 02)
0000:00:1f.0 ISA bridge: Intel Corporation: Unknown device 2810 (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation: Unknown device 2820 (rev 02)
0000:00:1f.3 SMBus: Intel Corporation: Unknown device 283e (rev 02)
0000:00:1f.5 IDE interface: Intel Corporation: Unknown device 2825 (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0092 (rev a1)
0000:03:00.0 0106: Unknown device 197b:2363 (rev 02)
0000:03:00.1 IDE interface: Unknown device 197b:2363 (rev 02)
0000:04:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4364 (rev 12)
```

I will maintain a list of motherboards that work using this method.

**_KNOWN, SUPPORTED MOTHERBOARDS_**

[LIST]
[*]Gigabyte GA-965P-DS3 rev 2.0, BIOS F7
[/LIST]

**_OLD KERNELS_**
...

---

### Post by xtknight on 2006-12-27
To get Edgy, just upgrade after installing Dapper.  The custom kernel is preserved.

---

### Post by jolt256 on 2006-12-27
Your 32-bit kernel didn't work for me (same motherboard, FWIW). It complained about not being able to find some files in /lib - my guess is that it's because ReiserFS is built as a module. There were also some errors that looked related to RAID, but I'm not sure what triggered them.

---

### Post by xtknight on 2006-12-28
> **jolt256 said:**
> Your 32-bit kernel didn't work for me (same motherboard, FWIW). It complained about not being able to find some files in /lib - my guess is that it's because ReiserFS is built as a module. There were also some errors that looked related to RAID, but I'm not sure what triggered them.

Hmm..I'm not sure how ReiserFS would cause that but I'm just using the default Dapper/Edgy config file for the kernels.  I have compiled a new 32-bit kernel based off Edgy with more PATA support enabled.

---

### Post by Chello on 2007-01-07
Hallo, it didnt work for me on an Gigabyte DS4 Mobo where Ubuntu is installed on an PATA HDD connected @ the JMicron Controller. When i compile my own 2.6.19 Kernel it boot but i didnt see the hdds the are connected @ the SATA ports. With the default 2.6.17 from the ubuntu DVD it boot and me see the SATA drives but sensors didnt work (new I2C chip).

---

### Post by dabl on 2007-01-07
Good thing I didn't see this before I installed Edgy on my C2 Extreme -- I'm a noob from Win-World and might have been scared off! :shock: 

My hardware: Intel D975XBX mobo, EVGA GeForce 7900 GS PCI Express 16X, 1 Maxtor 200GB PATA/IDE drive with a Win XP partition/installation, 1 WD 150GB SATA drive.

I installed Kubuntu 6.10 from the ISO image (CD).  I wanted the Grub bootloader and all of Linux to go on the faster SATA drive, so the IDE drive could potentially be removed/replaced later without a big system disruption.  I learned the installer on this Linux distro WILL NOT willingly do that with the existing Win XP installed on the IDE drive -- I lost a lot of time re-trying all possible ways to make it behave (changing drive sequence in BIOS, changing "Active" partition settings, etc. etc.).  Ultimately I gave up and lived with it installing the bootloader to the IDE drive, which I guess means I'll be keeping it in the system (!). It's a good place for data backups. If I ever feel the need for a weekend project, I'll pull the IDE drive and re-install everything on the SATA drive like I want it. I subsequently have installed the new Nvidia drivers and the basic system works great -- all my noobie experiments bogging it down with unneeded packages don't seem to bother anything.

Issues: USB device auto-detection seems to be about halfway implemented.  Digital cameras work, but take the SD card out and put it in a USB card reader, and it's no-go. Printer and scanner work fine.  Motorola Razr phone is hopeless, I guess -- good thing that Win XP partition is still available!

Overall, I'm delighted with my Edgy system, and I won't use that XP any more than I absolutely have to.  Open Office apps are excellent substitutes for my old MS Office, gimp is just as good as PaintShop Pro for my purposes, Amarok is wonderful, digiKam is excellent. I can almost feel Microsoft's control of my PC fading away!

:mrgreen:

---

### Post by Cagnazzo on 2007-01-08
Hey everyone. I'm an Ubuntu noob and I'm not sure that this is the right place for this, but I was wondering if anyone had any clue if Dapper 6.06 would be compatible with the Asus P5N-E nForce 650i mobo and the 8800GTS video card? I meant to get Windows, but because I messed up somewhere along the way, I'm going to use Dapper as a standby until I can get Windows XP. *Hides in a corner* I would assume that because the 8800GTS is DX10, that there would not be any compatible Linux drivers for it.

EDIT: Nevermind, I found out about the 8-series drivers for Ubuntu, and henceforth feel like an idiot. :|

---

### Post by seravitae on 2007-01-27
I have the same CPU (same speed) and the same motherboard as the original poster. The 32 bit kernel seems to have something wrong with it, that or I am doing something wrong. If anyone can tell me why this is occuring and how to rectify it i'd much appreciate it. I'm on edgy, of course.

root@eureka:/home/seravitae# dpkg -i linux-headers-2.6.19.1_c2d_i386.deb && dpkg -i linux-image-2.6.19.1_c2d_i386.deb
(Reading database ... 114140 files and directories currently installed.)
Preparing to replace linux-headers-2.6.19.1 c2d (using linux-headers-2.6.19.1_c2d_i386.deb) ...
Unpacking replacement linux-headers-2.6.19.1 ...
Setting up linux-headers-2.6.19.1 (c2d) ...

(Reading database ... 114140 files and directories currently installed.)
Unpacking linux-image-2.6.19.1 (from linux-image-2.6.19.1_c2d_i386.deb) ...
Done.
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing linux-image-2.6.19.1_c2d_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./lib/modules/2.6.19.1/kernel/drivers/hwmon/adm1021.ko')
Running postrm hook /sbin/update-grub .
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.17-10-386
Found kernel: /boot/vmlinuz-2.6.17-10-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 linux-image-2.6.19.1_c2d_i386.deb
root@eureka:/home/seravitae#

---

### Post by usererror on 2007-01-28
what's the difference between the first 32bit duo core image and the one with the 'headers' in the name?  I have a duo core laptop (Latitude D620) and I feel the battery runs out much faster in Ubuntu than it does in Windows.  Could this be due to the fact that i am running the generic kernel?  Thanks in advance :D

could i just download the new kernel and compile it for duo core support?

---

### Post by xtknight on 2007-02-04
**Chello:** Sorry, I won't be able to fix the problem without additional information

**Cagnazzo:** That's an nForce 650 chipset right?  You will need to create another thread for that issue.  (And, I have no idea.)

**seravitae:** odd error.  Maybe adm1021 is in use when you're trying to do that.  I have no idea how to fix it.  Google for "dpkg-deb (subprocess): short read in buffer_copy" maybe or ask on IRC in #linux, #debian, or #ubuntu irc.freenode.net.

**usererror:** headers contains the source code for the kernel.  image is the binary.

Your battery may be running out because clock modulation is not being used in Linux?  Most kernels will work for the Core 2 Duo, it's a matter of getting it working for Core 2 Duo motherboards.  Just select 'core 2 duo' for system architecture for the `make menuconfig` step at compile then enable any modules you need for your motherboard.

---

### Post by seravitae on 2007-02-10
Alright, after googling I discovered it was often caused by flaky web servers not sending the file right, so i forced a wget and watched it carefully. I've downloaded the file at least 4 times and 3 times got the same error when dpkg-deb'ing. This time it went through fine! However, upon bootup, the standard kernel halts at "Uncompressing linux..." (or more appropriately the ubuntu logo loading screen) and the '-recovery' kernel loads fine until it hits USB and then freezes soon after.

I've tried the 32 bit kernel on edgy several times now and can confirm with the same chipset and cpu as you, that it does not work. With the stalling that is occuring (and the fact that i compiled my own kernel recently with marvell's sh**y drivers, and had it stall near the same place) i have a feeling this is all the NIC's fault. 

Can you please give me a rundown of what drivers(versions, where you obtained it, etc) or options you are using that are highly relevant for this NIC?

---

### Post by seravitae on 2007-02-10
After finding an indentical machine to mine in the local area I headed over there and the kernel worked perfectly. We selectively deduced the core issue which was that my SATA drives were on the purple channel and his was on the 6 yellow channels. I moved my drive over to the yellow channels (other chipset/controller) and the kernel works perfectly now.

---

### Post by seravitae on 2007-02-11
fixed.

---

### Post by sdman on 2007-03-18
xtknight thanks alot ! Im a first time linux user and Im really happy with what I have dealt with so far. I have learned alot the past 3 days setting things up so they are stable.   The os was running terribly slow but after I installed the kernel you offered to us C2D'ers..it is like a whole new system. It is fast as hell now. No more slow boot time with errors either. All the programs launch quickly..Im very happy with the way it turned out. Im here to stay , cheers!

 btw My hard drive's and dvd burner are set up as follows ide slot master nec dvd burning / slave 160 gig used for free space/ Sata 2 port wdc 80gig(this is what drive I use to boot with and have the os installed on it).

---

### Post by ravemjr on 2007-03-18
I've installed the kernel...but I still haven't internet...I'm using a Marvel 88E8056 NIC, and it's detected(both of them). Do I still ned to install the drivers afterwards? Or is it supposed to run no problem now?

---

### Post by sdman on 2007-03-18
Have you tried System>>Preferences>>Networking then highlight your connection the click properties and you can configure your connection specifications from there. Just make sure when you are done to make sure the box is checked next to your connection. That will enable your connection.

---

