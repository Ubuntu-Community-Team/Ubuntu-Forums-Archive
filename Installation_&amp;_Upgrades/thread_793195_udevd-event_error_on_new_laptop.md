---
title: "udevd-event error on new laptop"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by ndstate on 2008-05-13
Hello,

I am trying to install 8.04 on a new Toshiba laptop with 2 hdds.  When I attempt to boot from the live cd I get the following errors:

```
udevd-event[1567]: run_program: '/sbin/modprobe' abnormal exit

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```


... I am also now getting some errors about

```
[0.000000] usb 3-2 not accepting address 3, error -110
[0.000000] usb 3-2: new high speed USB device using ehci_hcd and address 4
[0.000000] usb 3-2 not accepting address 4, error -110
[0.000000] usb 3-2: new high speed USB device using ehci_hcd and address 5
[0.000000] usb 3-2 not accepting address 5, error -110
```

I have looked around at some other posts and there seems to be a problem with Toshiba laptops?

I would like to install Ubuntu on the same hard drive as Vista.

Any ideas on how I can get this to boot and install?

Also, I have tried adding ```
acpi=off -- irqpoll -- noapic
``` to the boot line, but that doesnt help.

Any ideas?

Thanks!


Edit: I am attempting to install the 64bit ubuntu.  Laptop: Intel® Core&#8482;2 Duo mobile processor T8100, Intel® GM965 chipset with 4 gigs of ram ... [http://www.bestbuy.com/site/olspage.jsp?skuId=8770582&productCategoryId=abcat0502003&type=product&tab=1&id=1203815723071#productdetail](http://www.bestbuy.com/site/olspage.jsp?skuId=8770582&productCategoryId=abcat0502003&type=product&tab=1&id=1203815723071#productdetail)

Edit2:  Also some other errors after it sits for a bit:

```

[42.304451] sda: sda1 sda2
[42.639229] sd 0:0:0:0 [sda] Attached SCSI disk
[42.639310] sd 1:0:0:0 [sdb] 390721968 512-byte hardware sectors (200050 MB)
[42.639362] sd 1:0:0:0 [sdb] Write Protect is off
[42.639405] sd 1:0:0:0 [sdb] Mode Sense: 00 3a 00 00
[42.639460] sd 1:0:0:0 [sdb] Write cache: enabled, read cache: enabled doen't support DPO or UFA

``` ... etc.

---

### Post by dstew on 2008-05-13
Are you sure the installation disk is OK? Did you check the CD for errors (menu item)?

---

### Post by ndstate on 2008-05-13
Hello,

When I check it for errors I run into pretty much the same problems

Let me try again on another computer.

Thanks!

---

### Post by ndstate on 2008-05-13
Hello again,

Ok I ran the error checking option and it came up with no problems.  Also, I can boot fine from the other computer.

Any additional help would be appreciated.

Thanks

---

### Post by dstew on 2008-05-14
I think the problem is with the Live CD driver interacting with your USB system. You can turn of the Live CD USB driver with the kernel parameter **nousb**. You add this to the kernel line by pressing F6 at the opening menu. Once you have installed, the USB system should work OK, it is just the installer disk that is having the problem.

---

### Post by ndstate on 2008-05-14
Hello,

Unfortunately that did not fix the overall problem of coming to the screen with ```
udevd-event[1567]: run_program: '/sbin/modprobe' abnormal exit

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

Any other ideas?

Thanks

---

### Post by dstew on 2008-05-14
This may be a kernel bug related to Seagate drives. Try the kernel parameter **all_generic_ide**. See [this bug thread]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/154591").

---

### Post by gerson1024 on 2008-05-19
I have the same problem with my laptop, Toshiba Satellite A305 Series, i tried with nousb and all_generic_ide writing them together after quit splash screen, but it keeps repeating the same error, can you help me please , or give some ideas about what should i change in the boot line of the live cd, in order to run Ubuntu 8.04 on my laptop.
thanks

---

### Post by keinea on 2008-05-19
I am also experiencing the same problem getting Ubuntu 8.04 Desktop LiveCD to load properly on my Toshiba A305 S6825 Laptop.  

The LiveCD is known to be okay, since I've previously used it in the installation of a second desktop PC.

The boot process ends up at the BusyBox (initramfs) command line prompt. I've  tried the F6 acpi=off   noapic   nolapic and even the edd=on, boot options.  Also enter the all_generic_ide, with no luck.

I've taken some screen shots of the install events and saved them into PDF files.  They include screen captures of the dmesg, some of the /proc file content, CMOS hardware settings and even screen captures from device manager in the Vista Home Edition partition.

The PDF documents are archived into a tar package and can be downloaded from my web site:


    http://www.keinea.com/linuxarchive/Toshiba_A305_LaptopInfo.tar.gz


I'm at a loss on what to try next.  Any suggestions would be greatly appreciated.

Sincerely,
keinea

---

### Post by dstew on 2008-05-19
Have you tried the Alternate Install CD?

---

### Post by keinea on 2008-05-19
Reference to the last question posted --- I haven't tried the 8.04 Alternate CD yet ... I have used an alternate Dapper CD, when installing ubuntu on an older Pentium II platform.  Which did install successfully.

:) But I have solved the problem with the 8.04 LiveCD not launching into the GUI environment .... This may only apply for certain PC's, but those of you that have the Toshiba Satellite A305 - S6825 .... I went into CMOS (press F2 during initial boot up), then selected Advanced ---> Built-in LAN ENABLED and changed this too DISABLED.  

This at least got me up to the Desktop, and as far as I can tell all the default applications appear to work, except for the ones requiring a network connection.  But I won't know if I'll be able to resolve the network driver issue, until I actually get it installed on my hard drive.

As for launching the CD, once I disabled the on-board NIC, I didn't make any changes to the boot command line.  Just selected the top default "Try CD First" option, and everything launched okay.

But FIRST ... now that I've gotten this far ... I'll need to get hold of a utility that will reduce the size the Vista partition, and also create a backup image of the Vista OS. Since I didn't receive any install CD's for this laptop and if I ever decide to get rid of it, the next user might demand the other OS.

Quess I need to start searching topics on the Hardy Heron drivers for the  "Realtek RTL8102E Family PCI-E Fast Ethernet NIC (NDIS 6.0)".  That's if I can believe what the Vista device manager was calling it.

Cheers,
keinea

---

### Post by dstew on 2008-05-19
Vista itself has a utility that will reduce its own partition size, in the volume management tools I think. And, check the System --> Administration --> Hardware Drivers window for a driver for your NIC.

---

### Post by jklm988 on 2008-05-19
Agree with your view, to support you[&#32654;&#23481;&#38498;](http://www.snownes.com/xwzx.asp) [&#32654;&#23481;&#21152;&#30431;](http://www.snownes.com/xwzx.asp)

---

### Post by gerson1024 on 2008-05-19
I have the same laptop, and the same errors, it seems to be an kernel bug, i have tried and alternate cd, can you give us some help.

---

### Post by keinea on 2008-05-20
Vista accesses the network okay with the NIC interface enabled in the  BIOs, so that does confirm the network interface is good.

I just need to find out what kind of driver support Linux has for this particular NIC interface.  I'm  hoping that I'll be able to keep the NIC interface disabled so I can install Ubuntu from the LiveCD, then once Ubuntu is up and running on it's own partitions, I'll be able to then re-enable the NIC interface, and with luck, go online to do the upgrades. This laptop does have a wireless interface, but I currently don't have a wireless router, so that option is on the back burner for the time being.

The step I need to do before proceeding though, is to get hold of a recovery utility to backup this drive as it currently sits.  

Then I'll reduce the partition size for the current Vista partitions.  I'm currently showing a 1.6 GB EISA Configuration partition???  and a second NTFS 235 GB system partition.  Being a first time Vista user, I'm not that familiar with the computer management features, but it does appear to have an option to shrink the volumes.  Does anyone have any experience using this utility for resizing Vista? (but first I need the backup).

It may take me a few days to work this out, but I'll keep you all posted on the progress (or lack of it)....


Cheers,

keith

8-)

---

### Post by keinea on 2008-05-20
Just an update --- I came across this bug report which looks like they have or are working on the Realtek RTL8102E driver issue. Which is the same interface used in my Toshiba Satellite A305 S6825 laptop.  Per the report, it looks like the wireless interface does work, which should allow for the online upgrades.

So anyone with a Realtek RTL8102 chipset in their computer might want to check this report out ..... hope this helps.


TITLE:
Ubuntu 8.04 LiveCD fails to boot when RTL8102E Lan Chip is enabled ---


URL:
https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225749



Cheers,
Keith

8)

---

### Post by egor08 on 2008-05-20
> ...Being a first time Vista user, I'm not that familiar with the computer management features, but it does appear to have an option to shrink the volumes. Does anyone have any experience using this utility for resizing Vista?
I have used vista to resize my partition a couple of times. Never had any problems. First few steps of the following tutorial will explain how to do that. [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by keinea on 2008-05-23
Toshiba A305 S6825 Laptop -- 
Intel Core 2 Duo CPU, T5550 @ 1.83 GHz, 1.83 GHz – CPU Speed , 3GB RAM

On-board Network Interfaces (which is where the problem lies):
Intel PRO/Wireless 3945ABG Network Connection 
Realtek RTL1802E Family PCI-E Ethernet NIC (NDIS 6.0)

Console CLI results --  uname -a
Linux ubuntu2 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux


Dual-boot configuration: Ubuntu 8.04 Hardy Heron and Vista Home Premium --

After removing all the unnecessary applications on my Vista partition, and tuning down the performance features (virtual ram, and turning off System Recovery, cleaning & defragging), I was able to get the space used to about 15 GB.  The Vista Disk Management tool would still only reduce the partition down to a minimum of 130 MB,  so I decided to use a copy of gparted LiveCD version 03.4-7 to resize the NTFS partition to 50 GB.  I also used the gparted to delete the OEM EISA 1.5 GB recovery partition.  

The glitch with doing it this way is that it breaks Vista, and it will no longer boot.  So I had to use the OEM Recovery CD to boot up the system and run through the "System Recovery Options" to get the NTFS partition detected again, and to initiate a "Startup Repair".  This is why I always recommend having a good backup of your drive,  just in case certain recovery steps don't work.  Before even starting these install procedures, I created a full backup of the drive using my copy of Acronis True Image 11, which has worked well for me in the past. 	


Once I got Vista running again at 50 GB, I proceeded with the Ubuntu install.  I disabled the on-board network interfaces in BIOs due to the BusyBox issue, then booted the system up with the Ubuntu LiveCD. The installation proceeded without a glitch.  

I manually  partitioned the hard drive, and this is how it's currently configured:

/dev/sda
	sda1	swap		1570 MB    (originally space used by OEM EISA)
	sda2	NTFS		52427 MB
	sda3	/		24996 MB	
	sda5	/home		50001 MB
	sda6	/usr		8003 MB
	sda7	/var		3997 MB
	sda8	/storage	109059 MB

 
:icon_frown:Now to the problem --- 

When I re-enable the on-board network, Ubuntu fails to boot and instead launches to the BusBox command line prompt.   

Since I have no external connectivity when I can launch into the Ubuntu partition, Is there any files that I could copy from another Ubuntu 8.04 Desktop (via a USB stick), that would satisfy the hardware issue with the Realtek RTL1802E NIC????

When I get this resolved, I'll post back with my steps taken ....

Cheers
Keith

---

### Post by dstew on 2008-05-23
Try booting with the **irqpoll** kernel parameter. Leave the NIC enabled, and at the grub menu press 'e' to edit the menu item. Select the kernel line with the up/down arrow keys, press 'e' again to edit the line. Type the word irqpoll at the end of the line, press 'enter', then 'b' to boot.

---

### Post by keinea on 2008-05-24
> **dstew said:**
> Try booting with the **irqpoll** kernel parameter. Leave the NIC enabled, and at the grub menu press 'e' to edit the menu item. Select the kernel line with the up/down arrow keys, press 'e' again to edit the line. Type the word irqpoll at the end of the line, press 'enter', then 'b' to boot.

I modified the Grub kernel line to reflect the following;
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=4626d57c-956a-4282-93e2-9697bad1bdf0 ro quiet splash irqpoll

Not much happens for about a minute (except for splash) ... then it faults to the BusyBox (initramfs) command line prompt again.

BusyBox uses a built-in ash shell, so there's not much there in the way of utilities for viewing detected hardware.  For example lspci is not available.

It was worth a try though.  I'll just have to use the Vista partition to access the Internet for the time being.

Cheers,
Keith
:icon_frown:

---

### Post by dstew on 2008-05-24
Remove quiet splash from the kernel line to see what the error is. The BusyBox is the default exit when the kernel cannot run, but before it gets to BusyBox the kernel will post errors. Maybe you can get a clue from the errors as to what the problem is.

---

### Post by keinea on 2008-05-24
> **dstew said:**
> Remove quiet splash from the kernel line to see what the error is. The BusyBox is the default exit when the kernel cannot run, but before it gets to BusyBox the kernel will post errors. Maybe you can get a clue from the errors as to what the problem is.

I did do that, and the messages look very similar to the examples posted at:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225749](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225749)

Looks like there is a fix to this problem, but I'm not sure exactly how to go about applying it to my laptop.  I have submitted a request to 'bugs.launchpad.net', referencing this particular bug.

I have also installed all the applications that I want to use, by using the APTonCD that I created from my main desktop computer.  I just need a network connection now.  

I'm getting close.


Cheers,
Keith
8)

---

### Post by keinea on 2008-05-24
Update --- 
I now have network connectivity on my Toshiba Satellite A305 S6825 laptop.

I downloaded and installed two new "2.6.24-18.32ubuntu6" kernel header and image packages.  

For more details, see the launchpad bug report at: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225749](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225749)

Once installed, I rebooted the system and re-enabled the "Built-in LAN" in CMOS. Then launched into Ubuntu Hardy again .... everything A OK.

I believe the only devices I still need to confirm, is the on-board web cam and the wireless network interface.


Cheers all and thanks,
Keith
8)

---

### Post by gabgren on 2008-05-25
well ... i just posted this thread: [http://ubuntuforums.org/showthread.php?t=806435](http://ubuntuforums.org/showthread.php?t=806435)

my problem seems to be the same ! i got this "busybox" dialog

---

### Post by egor08 on 2008-05-26
> **keinea said:**
> Update --- 
I now have network connectivity on my Toshiba Satellite A305 S6825 laptop.

I downloaded and installed two new "2.6.24-18.32ubuntu6" kernel header and image packages.  

For more details, see the launchpad bug report at: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225749](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225749)

Once installed, I rebooted the system and re-enabled the "Built-in LAN" in CMOS. Then launched into Ubuntu Hardy again .... everything A OK.

I believe the only devices I still need to confirm, is the on-board web cam and the wireless network interface.


Cheers all and thanks,
Keith
8)
I have the same laptop. The wireless works out of the box. 
Webcam works with Ekiga and Skype, however It is not recognized 
by easycam or easycam2, so it might not work with other applications.

Another problem I had with this laptop is that the sound would stop
working after the hibernation. Do you have the same problem?

I tried a couple of things to fix this, but the only thing that worked
is the script that unloads the sound drivers from the memory when ubuntu
is about to hibernate. Here is the link:

[http://www.fak3r.com/2008/02/25/howto-sound-after-hibernate-in-linux-gustylenny/](http://www.fak3r.com/2008/02/25/howto-sound-after-hibernate-in-linux-gustylenny/)

---

### Post by keinea on 2008-05-27
> **egor08 said:**
> I have the same laptop. The wireless works out of the box. 
Webcam works with Ekiga and Skype, however It is not recognized 
by easycam or easycam2, so it might not work with other applications.

Another problem I had with this laptop is that the sound would stop
working after the hibernation. Do you have the same problem?

I tried a couple of things to fix this, but the only thing that worked
is the script that unloads the sound drivers from the memory when ubuntu
is about to hibernate. Here is the link:

[http://www.fak3r.com/2008/02/25/howto-sound-after-hibernate-in-linux-gustylenny/](http://www.fak3r.com/2008/02/25/howto-sound-after-hibernate-in-linux-gustylenny/)


I just got my broken audio issue solved, and so far this evening I haven't encountered any audio problems after coming out of hibernation mode.  

You may want to take a look at my last entry posted to the [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225749](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225749)

Basically there were four packages that I had to install to fix the network interface issue and my broken audio. The audio issue wasn't really a bug, it was due to not downloading and installing the last two packages during the initial upgrade process.

To summarize, my wired NIC is working, the media apps are working, the Compiz/Fusion 3D Cubed effects are working.  My Toshiba Satellite A305 S6825, appears to be ready for prime time and show-and-tell.

If anything new crops up, I'll send a post back this way.


Cheers,
Keith
8)

---

### Post by wmtabada on 2009-05-17
Re: udevd-event error on new laptop

I also have the same problem with my new MSI Wind Notebook. The error is something like this:

udevd-event [1447] : run_program 'sbin/modprobe' abnormal exit.

The notebook has no built-in CD drive so I used an externel Asus DVD/CD drive via USB port. Can somebody help me too in solving this problem. Thank you.

---

### Post by binneypl on 2009-06-11
> **dstew said:**
> This may be a kernel bug related to Seagate drives. Try the kernel parameter **all_generic_ide**. See [this bug thread]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/154591").

Many thanks indeed for that; **all_generic_ide** got one boot to work for me, but
ultimately I can't use this release (see [http://ubuntuforums.org/showthread.php?t=1134107]("http://ubuntuforums.org/showthread.php?t=1134107")).

---

### Post by Francewhoa on 2010-03-11
Same here. **The following worked for me** [http://ubuntuforums.org/showthread.php?p=8952609#post8952609](http://ubuntuforums.org/showthread.php?p=8952609#post8952609)

---

