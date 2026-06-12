---
title: "Failed Ubuntu 7.10 Installation on HP Compaq 6715b Notebook"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by Coderoid on 2008-05-08
Hi guys,

Last night i finally finished backing up my Windows files on DVD discs and i was all smiles as i added Ubuntu stickers to my HP notebook. I inserted the Ubuntu disc and rebooted, and this is what ensured...

The Ubuntu disc loads and i select the first option to install Ubuntu, and it then starts booting. It goes well until a screen where its starting daemons, then it just stops when loading boot scripts and the disc goes quiet. I left it for over an hour and tried again, but same thing happens. What puzzles me is that i do have that Ubuntu running on that same notebook in VMWare. Only, i wanted to install it as my main OS and reformat the entire drive.

Please advise; my specs are:

HP Compaq 6715b Notebook

Display = ATI Radeon X1250 Series
Chip Type = ATI Radeon X1200 Series (0x791F)
DAC Type = Internal DAC (400MHz)
Memory Size = 128MB
Adapter String = ATI Radeon X1250
Bios Information = BK-ATI VER010.038.000.004.023883

CPU = AMD Turion 64x2 1.9GHz TL-58
RAM = 2 Gigs
Hard Disk Drive = Fujitsu MHW2120BH
DVD Drive = TSST corp CD/DVDW TS-L632D

I am not afraid to muck with it until it works, i just need to be shown the right way to do it...

Regards,

Lloyd Dube

---

### Post by housam on 2008-05-08
Try to reformat the HDD manually using Gparted tool ( on the live CD ),then create the needed partitions ( one for the root - ext3 format with the sign ( / ) and the second for the swap and the third for storage your data - ext3 format with the sign( /home ). 
after that start the installation and when it comes to partitioning choose the manual one and assign the partitions you already created manually.

---

### Post by Pumalite on 2008-05-08
Vista or XP?
Maybe you need to fix Windows MBR with Super Grub first. With Vista, use the Vista partitioner.

---

### Post by Coderoid on 2008-05-08
@@housam, thanks for the response! please help me understand though :) how do i select to use Gparted when the disc starts? 

@@Pumalite, basically what was happening was, i wanted to install over XP rather than dual boot. Is it a bad idea to format c: first in windows to clear all data, or will that just reformat in NTFS and get me nowhere?

Thanks again, and Best Regards,

Lloyd Dube

---

### Post by Pumalite on 2008-05-08
In that case, I'd get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
Burn to disk and boot from it. Delete everything in your hard drive. From the free space, make 3 'New' partitions:
10 GB for '/'
2 GB for /swap
The rest for /home. Install Ubuntu, go Manual and pick the partitions already prepared. The installer will do the rest.

---

### Post by Coderoid on 2008-05-08
@@Pumalite, thanks for the tip. I will post back on progress.

---

### Post by wpshooter on 2008-05-08
> **Coderoid said:**
> @@Pumalite, thanks for the tip. I will post back on progress.

Coderoid:

I would get [www.killdisk.com](www.killdisk.com) and WIPE the hard drive COMPLETELY clean and then attempt to install Ubuntu.

Partitions should be as follows:

1) / = root
2) /home = home (for data,etc.)
3) swap = for possible shortfall of memory

Make sure you check the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu.

Good luck.

---

### Post by owend on 2008-05-08
I had very similar problem; I found that 7.10 wouldn't install - kept freezing like you. I have a laptop with AMD64 processor, which I think is the problem: do you get a quick "biosbug 81 found" message?

Download 8.04, the AMD desktop version! I'm using it now. Minor glitches on driver for scanner and power management, but I've migrated from Vista (although 8.04 set up a dualboot with no problems!)

Good luck.

---

### Post by Coderoid on 2008-05-08
@@wpshooter - thanks, i did check the Ubuntu disk's integrity last night and it turned out fine. I will look into killdisk and let you know how things go. quick quesstion - does using killdisk to wipe the hard drive ensure that the Ubuntu disk will cleanly load its boot files in the MBR? Am new to this, so some questions may sound silly :)

regards,

Lloyd Dube

---

### Post by wpshooter on 2008-05-08
> **Coderoid said:**
> @@wpshooter - thanks, i did check the Ubuntu disk's integrity last night and it turned out fine. I will look into killdisk and let you know how things go. quick quesstion - does using killdisk to wipe the hard drive ensure that the Ubuntu disk will cleanly load its boot files in the MBR? Am new to this, so some questions may sound silly :)

regards,

Lloyd Dube

Not silly at all.

When you WIPE the drive there will be NOTHING on it to worry about.  So just make sure that you have CD drive as first bootable device in BIOS, put that Ubuntu baby in there and boot to it and install.

Good luck.

---

### Post by Coderoid on 2008-05-08
@@owend - i hope the processor has nothing to do with this, as im not ready to get a new notebook now $$ :)

I did not get the Bios bug...

Ciao

Lloyd Dube

---

### Post by Coderoid on 2008-05-08
@@wpshooter haha, thanks...i was actually beginning to wonder if i shouldnt go into the CMOS setup and configure my cd drive as the primary boot device...

will let you know tomorrow if i have any luck or not :)

---

### Post by Coderoid on 2008-05-09
Hi guys,

Here's an update on my situation: last night i wiped out my disk with KillDisk (i dont want to dual boot) and rebooted from the Ubuntu 7.10 i386 Disk. Here are the messages i got; please bear with me if they are long...

==================================================================

Loading Linux kernel					[0k]
Setting preliminary keymap				[OK]
Preparing restricted drivers				[OK]

(...and so on, all other messages returning [OK] status)

THEN:

Loading hardware drivers - Error receiving uevent message: nospace or buffer available - could not initialize

var/lib/acpi-support/system-Product-Name; No such file or directory

var/lib/acpi-support/System-Manufacturer; No such file or directory

var/lib/acpi-support/System-version; No such file or directory

var/lib/acpi-support/bios-version; No such file or directory

* Saving VESA State					[OK]
* Loading ACPI Modules					[OK]
* Starting ACPI Services				[OK]
* Starting System Log Daemon				[OK]
* Starting kernel log daemon				[OK]
* Starting system message bus dbus			[OK]
* Starting Network Connection Manager Network Manager	[OK]
* Starting Network Events DispatcherNetwork Manager Dispatcher[OK]
* Starting system tools backends system-tools-backends	[OK]
* Starting hardware abstraction layer hald		[OK]
* Starting Common Unix Printing System: cupsd		[OK]
* Starting powernowd...					[OK]
* Starting ConsoleKit daemon console-kit-daemon		[OK]
* Starting Avahi mDNS/DNS-SD Daemon avahi-daemon	[OK]
* Starting DHCP D-Bus daemon dhcdbd			[OK]
* Starting Bluetooth Services				[OK]
* Starting Gnome Display Manager			[OK]
* Starting deferred execution scheduler atd		[OK]
* Starting periodic command scheduler crond		[OK]
* Checking battery state				[OK]
* Running local boot scripts				[OK]

(and the prompt flashes here for ever)

==================================================================

I have no idea what this is about - surely if VMware could provide  an acceptable vm for Ubuntu on this notebook, then the actual hardware would suffice?

Please advise,

Thanks,

Lloyd Dube

---

### Post by wpshooter on 2008-05-09
Lloyd:

There is some type of NO-ACPI parameter that can be input at the beginning of the install to cure these types of problems.  I have never had to use it myself, so I can not give you an exact info on how it is used.  Perhaps someones else can advise you or a quick search on ACPI will let you find the answer.

---

### Post by Coderoid on 2008-05-09
@@wpshooter - how do i get to the boot: prompt when the Live Disk runs? I found out how i can pass Live Acpi=NOACPI at that prompt but i just need to get there!

Thanks :)

Lloyd Dube

---

### Post by wpshooter on 2008-05-09
I "think" that you just press the F4 key at the boot menu.

No, I think it might be F6.  Should be something that is listed on the boot menu.

---

### Post by Pumalite on 2008-05-09
This might help:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

