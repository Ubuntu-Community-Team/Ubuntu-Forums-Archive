---
title: "Lucid 10.4 Live CD not running, strange"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2010-08-10
I am failing to boot 10.04 in a particular machine which is currently using 8.04.4. 

The Lucid cd boots, I can get to the menu after a keyboard action at the symbols, and if necessary I can edit the boot string. However, after a short while I see:

Busy Box v1.13.3 (ubuntu 1:1.13.3-1ubuntu11) built in shell (ash)
Enter 'Help' for a list of built in commands
(initramfs) stdin:I/O error
Mount:mounting /dev/loop0 on //filesystem.squashfs failed:no such device
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs


To my inexperienced eyes this looked like maybe a bad CD or a bad read in the drive, so I did some tests (in its normal installed OS of 8.04)  which seem to verify the cd and drive really are ok.

The machine is a Dell Dimension 4100 but the graphics card is non dell, and the CD/dvd drive being used for booting is also non Dell.

8.04.3 live cd runs ok as long as F4 safe graphics is first chosen, (otherwise the display shows out of range video for default graphics). This machine is in use normally with an install of 8.04.4.

9.10 live cd hangs (at maybe a graphics stage?) even if safe graphics is used.

lspci and lsusb (from it normal running in 8.04) are as follows:
------------------------------------------
user1@dell-866:~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
02:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
02:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
02:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
02:0a.0 VGA compatible controller: Matrox Graphics, Inc. MGA 2164W [Millennium II]
02:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0c.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)


user1@dell-866:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 05e3:1205 Genesys Logic, Inc. Afilias Optical Mouse H3003
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 03f0:0411 Hewlett-Packard 
Bus 001 Device 002: ID 05e3:0606 Genesys Logic, Inc. D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 001: ID 0000:0000  

------------------------------------------

Any ideas please?

---

### Post by wookieshaver on 2010-08-10
There are two things that leap to mind and I hesitate to mention them as you seem to be an experienced user: Firstly the disc may need to be downloaded and burned again as I  have been burned on bad images from various sources in the past. Secondly, I might check as it is an ide cd/dvd driver that the jumpers on the drive are set to master or slave appropriately (assuming its on the second ide channel and the main hdd is on the first the cd drive would be set to master). Quite often these drives are set to cable select by default.

---

### Post by candtalan on 2010-08-10
Thanks for the response. Yes the 10.04 CD did not go far enough to do a self check in the target pc, so I did an md5sum check in another machine to verify the CD. Then I used the target PC in its normal 8.04 to copy the CD to image (iso) then checked the iso saved file with md5sum in the target PC. So I concluded that the CD was ok and that the target pc could read it ok. The cd drive is a fairly new modern one so I would expect it to work ok. 

I will certainly check out the jumpers.

---

### Post by candtalan on 2010-08-10
Hey!
The dvd/cd drive was correctly set to master, and the second (older) dvd/cd drive also correclty set to slave, however, I removed the slave drive to continue the test with only the master drive. And - 10.04 worked!

I do not know exactly what was going wrong but it looks as if the presence of both CD drives or maybe just the older drive, was causing a problem.

Tried 9.10 live CD again - it now works, does not hang!

Further thought: The HP original power supply may have been just marginally insufficient to run the machine with its two hard drives and then two dvd drives also, and while it worked ok normally it seems as if the live CDs for 9.10 and particularly 10.04 demanded cd drive activity that just tipped the balance towards dysfunction, maybe in a transient way.

Some time ago I did find a somewhat similar problem, solved by removing one dvd drive, although in that machine, the problem was evident through CD self checks, sometimes ok and sometimes not ok. At least then the CD self checks would run(!)

Well I never. Thanks again for your response, it was a really valuable trigger to check further!

---

### Post by baisong on 2010-09-29
Quote:

The dvd/cd drive was correctly set to master, and the second (older) dvd/cd drive also correclty set to slave, however, I removed the slave drive to continue the test with only the master drive. And - 10.04 worked!

...

Can you explain how you "removed the slave drive?" I'm having the same error with every LiveCD I burn on every computer I try...

---

### Post by candtalan on 2010-09-29
> **baisong said:**
> Quote:

The dvd/cd drive was correctly set to master, and the second (older) dvd/cd drive also correclty set to slave, however, I removed the slave drive to continue the test with only the master drive. And - 10.04 worked!
...
Can you explain how you "removed the slave drive?" I'm having the same error with every LiveCD I burn on every computer I try...

I unplugged the data cable (large flat cable) and also unplugged the power connection plug at the slave. This meant that in particular, the power supply was not being drained also into the slave CD drive.  I probably later removed the unused drive physically from the PC, not sure, but the important part is to stop power going to the drive.

good luck

---

