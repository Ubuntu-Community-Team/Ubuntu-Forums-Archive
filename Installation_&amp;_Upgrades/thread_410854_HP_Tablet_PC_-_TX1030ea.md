---
title: "HP Tablet PC - TX1030ea"
date: 2007-04-16
forum: Installation &amp; Upgrades
---

### Post by johnbradbury on 2007-04-16
Okay I'm trying to install Ubuntu 7.04 (also tried the older versions 6.06 and 6.10) onto a HP tx1000 tablet PC (specs below) and I'm having trouble getting past first boot.

The system boots in the GUI installer, lets me setup the paritions, enter keyboard and user setting, goes through the base installation, and then runs package installation. I get a message saying the installation is complete. After this the PC is rebooted and I get a series of events being logged in text mode on the screen (I assume this is various services being started).

Then I get "Superblock last write time is in the future. FIXED"
It appear to get past this and starts to scan /sda3 (I assume this is a chkdsk type thing?), it's at this point that the system freezes. It doesn't fail at a particular point, sometimes it can be 10% others 33%.

I'm assuming that /sda3 is the third partition on the first drive? If this is the case it's a HP Recovery partition. One thing to note is that I am able to install Ubuntu to this latop in a VMware session under Windows, the only difference being the HDD and Display drivers.



PC SPECS

HP tx1000ea Tablet PC
AMD Turion 64 X2 TL-52, 2048MB Ram, NVIDIA GeForce Go 6150,
120gb Sata HHD, Lightscribe Super Multi DVD Writer, 12.1&#8221; WXGA High-Definition HP BrightView Widescreen,
Nvidia Ethernet 10/100BT, Realtek High Definition Audio, Motorola SM56 Data Fax Modem, Broadcom Wireless LAN.

---

### Post by mac.ryan on 2007-04-16
> **johnbradbury said:**
> I'm assuming that /sda3 is the third partition on the first drive? If this is the case it's a HP Recovery partition.

I am far from being an expert in such things, but your analysis makes sense to me and googleing around I found out that recovery partitions can make problems at boot time, because of some characteristics of theirs (e.g. deliberate mis-identification of the file system).

In [this article]("http://209.85.135.104/search?q=cache:wHx__F480UUJ:www.thinkwiki.org/wiki/Installing_Ubuntu_5.04_on_a_ThinkPad_T43_%281875%29+hiding+partition+ubuntu+boot&hl=en&ct=clnk&cd=8") (based on an IBM machine, though) they suggest to modify the type of partition setting it to another type and then modify the /boot/grub/menu.lst file in order to keep it hidden from Windows. If you choose to try this option (but I would first try the other one further down...), you can refer to the code here below: I adapted the modification in the original article for your system. Please take into consideration only the bold lines, the other lines are just a 'facsimile' to show you where to add the bold ones. The partition is 2 and not 3 because grub starts counting partitions from zero... However this is only the last stage of the how-to, you have to read the entire article first!

```

title           Microsoft Windows XP Professional (/dev/hda1)
**hide (hd0,2)**
rootnoverify            (hd0,0)
chainloader     +1

title           Windows Rescue/Service (dev/hda2)
**unhide (hd0,2)**
rootnoverify            (hd0,1)
chainloader     +1

```**However, on my opinion the problem could also be solved by preventing that partition to be mounted (and/or checked) at boot-up... after all it is not a place where you want to go and get or put files, isn't it?**

In my limited understanding of GNU/Linux, this should be achievable by modifying the /etc/fstab file. Look for the lines referring to the sda3 partition. At the end of one of them you will find two digits: the second should currently be set to a positive value, while you wish to _set it to 0_ (no fsck at boot). If you don't want to mount that partition at all, just comment the line (adding ## in front of it) so it will be ignored.

Let us know if this helped!

PS: you can edit the files on your ubuntu installation either running from the liveCD and mounting that partition, either by[ installing ext2/ext3 drivers]("http://www.fs-driver.org/") for windows and accessing those files from within windows.

---

### Post by bulldog on 2007-04-16
If you can boot the live cd,can you provide us with the output of the following command?
```
sudo fdisk -l
```
So we can see what is on this particular partition.

---

### Post by beniwtv on 2007-04-17
I also own a HP laptop, and did get the same problems.

The problem is not your SATA controller. Nor the video. I dunno why the HP locks up in console mode.

On my HP happens exactly the same. It will lock up in console mode. I don't know why, but in GUI mode it works OK.

So, to fix (which is easy), do this (once the system is installed):

On the boot menu, scroll down to Ubuntu recovery mode and press 'b'.

Scroll down to the kernel line, and hit 'e'. Remove the "ro single", and put in instead "rw quiet init=/bin/bash".

Then hit enter to go back and type 'b' to boot ubuntu.

When the console comes up, type in:

```
umount /
```

And then

```
fschk -fy /dev/sda3
```


Wait until it's finished (the computer should not freeze during this, but if it does, reboot and try again succeed).

When it's finished,  reboot by pressing <ctrl-alt-del> (there's no other way at this point), and your Ubuntu should boot.

After this, you will have to disable the partition checking. I will tell you once Ubuntu boots.

---

### Post by Spuds on 2007-04-26
I actually have the HP tx1115nr model... and when I try to install any of the last few versions of Ubuntu (AMD64) it fails.... right after "setting up interfaces     [ok]"

Anyone else have this problem or a workaround?  Perhaps I shouldn't be using the AMD64 version?  Was that a bad assumption on my part?

Spuds

---

### Post by mac.ryan on 2007-04-26
> **beniwtv said:**
> And then

```
fschk -fy /dev/sda3
```
Wait until it's finished (the computer should not freeze during this, but if it does, reboot and try again succeed).

....have you tried then to see if the windows recovery partition still works, then? Those detected as "errors" are not errors in fact, but "weird sectors" put there for some (partially) misterious reason by the computer vendor. I am just wondering if "fixing" those will eventually "break" the windows recovery procedure... ?

---

### Post by mac.ryan on 2007-04-26
Almost OT...

> **Spuds said:**
> Perhaps I shouldn't be using the AMD64 version?

i don't know if your problem is linked to the 64 bit version, but I would recommend to read the stickies at the top of the 64 bit forum here: 64 bits give a very modest advantage in everyday use of the computer and have a number of significant limitations (no virtual machines, no wine, need to wrap most of proprietary software to run in 32 bit...). "Special" installation even for common things like the Flash player.

Installing a 64 offers you a chance to learn a lot, yet it is a real time-thief...

---

### Post by beniwtv on 2007-04-30
> **mac.ryan said:**
> ....have you tried then to see if the windows recovery partition still works, then? Those detected as "errors" are not errors in fact, but "weird sectors" put there for some (partially) misterious reason by the computer vendor. I am just wondering if "fixing" those will eventually "break" the windows recovery procedure... ?

We won't touch the recovery partition. We only check the Linux partition. The reason for this is after installing Ubuntu and rebooting, on the first boot it will check the Linux partition.

This will freeze the computer, so we need to do it manually from recovery mode, which freezes as well when booting the kernel, so this is why the modified boot parameters.

I can't tell yet why this happens, but I suspect it's something with the Nvidia card in those laptops, which seems to not like the text resolution.

In fact, in console mode you can be certain it will freeze at some point.

---

### Post by farbird on 2007-05-15
i'd had this problem as well..

i kept rebooting it and let it do the scan..
there was this time it completed and everything was smooth after that..
apparently, this only happens for the 64bits distro..
32bit didnt have this problem

do add this line into your grub settings

click escape before it boots..

edit the line which have the "uuid=xxxxxx" text..
append to the same line with these codes " noapic vga=0x317"
it should get it up to the gfx login screen.

> **johnbradbury said:**
> Okay I'm trying to install Ubuntu 7.04 (also tried the older versions 6.06 and 6.10) onto a HP tx1000 tablet PC (specs below) and I'm having trouble getting past first boot.

The system boots in the GUI installer, lets me setup the paritions, enter keyboard and user setting, goes through the base installation, and then runs package installation. I get a message saying the installation is complete. After this the PC is rebooted and I get a series of events being logged in text mode on the screen (I assume this is various services being started).

Then I get "Superblock last write time is in the future. FIXED"
It appear to get past this and starts to scan /sda3 (I assume this is a chkdsk type thing?), it's at this point that the system freezes. It doesn't fail at a particular point, sometimes it can be 10% others 33%.

I'm assuming that /sda3 is the third partition on the first drive? If this is the case it's a HP Recovery partition. One thing to note is that I am able to install Ubuntu to this latop in a VMware session under Windows, the only difference being the HDD and Display drivers.



PC SPECS

HP tx1000ea Tablet PC
AMD Turion 64 X2 TL-52, 2048MB Ram, NVIDIA GeForce Go 6150,
120gb Sata HHD, Lightscribe Super Multi DVD Writer, 12.1” WXGA High-Definition HP BrightView Widescreen,
Nvidia Ethernet 10/100BT, Realtek High Definition Audio, Motorola SM56 Data Fax Modem, Broadcom Wireless LAN.

---

### Post by farbird on 2007-05-15
to get your wifi broadcom working, try this

sudo apt-get install bcm43xx*

sudo gedit /etc/iftab

change the interface name of the wifi interface to "wlan0"
it may be eth0 or eth1 initially [ check to ensure which is the wifi one ]

sudo gedit /etc/network/interfaces
remove all lines which make references to the old "ethx" that has been replaced above to "wlan0"

now in console, do this

sudo rmmod bcm43xx
sudo modprobe bcm43xx

this should get it working...
if the rmmod doesnt work, just reboot the laptop....

if still cannot work... post reply here

---

### Post by tinalee on 2007-05-30
Hello...

I am new here and I have a question about the HP Pavilion tx1115nr Entertainment Notebook PC.  I just bought it and I can't get the touch screen to work.  I am afraid i was sold the one that doesn't have that option.  Do you know if my model comes with that feature/option?  if not, can I upload something to activate it or is there another model that comes with it already installed??

anything would help me....thanks!

Tina

---

### Post by smkaplan on 2007-06-06
> **tinalee said:**
> Hello...

I am new here and I have a question about the HP Pavilion tx1115nr Entertainment Notebook PC.  I just bought it and I can't get the touch screen to work.  I am afraid i was sold the one that doesn't have that option.  Do you know if my model comes with that feature/option?  if not, can I upload something to activate it or is there another model that comes with it already installed??

anything would help me....thanks!

Tina

I believe the tx111x are convertible, with no touch screen.
The tx112x are the touch screen models.

If they are not at the major retailers yet you can order one directly from hp (I got mine at sam's club.)  More info is available from hp: [http://h71036.www7.hp.com/hho/cache/447013-0-0-225-121.html?jumpid=reg_R1002_USEN]("http://h71036.www7.hp.com/hho/cache/447013-0-0-225-121.html?jumpid=reg_R1002_USEN")

---

### Post by Cuppa-Chino on 2007-06-07
> **mac.ryan said:**
> Almost OT...



i don't know if your problem is linked to the 64 bit version, but I would recommend to read the stickies at the top of the 64 bit forum here: 64 bits give a very modest advantage in everyday use of the computer and have a number of significant limitations (no virtual machines, no wine, need to wrap most of proprietary software to run in 32 bit...). "Special" installation even for common things like the Flash player.

Installing a 64 offers you a chance to learn a lot, yet it is a real time-thief...

I agree in principle that 64bit makes life harder but with the help of the forum I have flash, java, etc etc all running

---

### Post by santosraymond on 2007-10-10
hi all,

i'm a noob as well but i thought i'd share this with everyone. i followed these instructions to get amd64 live cd working on my hp pavilion tx1320ca, i got this from the ubuntu site. "Often when installing Ubuntu i386 on an AMD64 board you will have to hit F6 and enter the following paramaters irqpoll pci=noacpi noapic nolapic acpi=off to get The Ubuntu i386 Alternate or LiveCD to Boot correctly." because originally i can't get the amd64 livecd to boot properly on this machine, it seems to hang when loading the drivers. i know the instructions are for i386 but it seemed logical that the problem when loading had something to do with acpi, so i tried it on the amd64 cd.

anyway, that's not my issue, my issue is after i loaded the 64bit version of kubuntu, i can't seem to get adobe flash installed. it's giving me an error saying that the software is not built for 64 bit o/s. just wondering if anybody has found a workaround to get it installed ? anyway, i will check the other postings on the site as well.

thanks,
raymond

---

