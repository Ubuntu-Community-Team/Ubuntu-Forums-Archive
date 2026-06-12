---
title: "Partition Problems"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by Gr1m3y on 2009-12-10
Hey!!!
So I am having troubles installing Ubuntu 9.10. I got my hands on an old Compaq N200 laptop and wanted to install it from a USB DVD Drive, but I don't have access to the BIOS since it is pass-worded. I however was quite happy to discover that you can install the program that will force it to boot from the DVD-Rom. I started installing and 15% of the way through partitioning the drive, I accidentally bumped the DVD Drive and it completely froze. I should have let it sit but I ended up popping the battery out to let it shutdown and now I can't get on at all, it simply says invalid partition table and asks me to check the hard drive cable. I'm guessing that I will just have to take it a part and reset the BIOS manually so I can't boot from the DVD, but if anyone knows an easier way, or a better way of resetting the BIOS, it would be greatly appreciated. Thanks in advance!!!!

---

### Post by Bucky Ball on 2009-12-10
But if you popped the battery on the motherboard (leave out for at least 30 seconds) it will return your BIOS to the default factory settings ... IE NO password. You should be able to get in there now at least.

---

### Post by Gr1m3y on 2009-12-10
I didn't mean the CMOS battery, I meant the actual battery. Or will that work as well?

---

### Post by Bucky Ball on 2009-12-10
CMOS, don't know what the other battery is.

---

### Post by Gr1m3y on 2009-12-10
The laptop's general battery. Sorry I should have made that more clear. It's not a desktop, it's a small net book. Thanks for the help so far though.

---

### Post by Bucky Ball on 2009-12-10
Got ya. I think you need to disconnect all devices, pull battery out and hold down power button for 30+ seconds to clear things. You might want to check the manual or do some webcrawling.

You need to get back to boot from the liveCD to see what is happening because it sounds like job unfinished as far as partitioning goes. This would have been caused by the premature restart halfway through installing. DO NOT start recabling and swapping things around physically. That will confuse the issue. Just aim for the BIOS and a boot from the external DVD.

---

### Post by Gr1m3y on 2009-12-10
Thanks, I'll try that. I'll have to look for an online PDF of the manual.

---

### Post by JBAlaska on 2009-12-10
Here are some common backdoor pw's:
Award BIOS backdoor passwords:
ALFAROME 	BIOSTAR 	KDD 	ZAAADA
ALLy 	CONCAT 	Lkwpeter 	ZBAAACA
aLLy 	CONDO 	LKWPETER 	ZJAAADC
aLLY 	Condo 	PINT 	01322222
ALLY 	d8on 	pint 	589589
aPAf 	djonet 	SER 	589721
_award 	HLT 	SKY_FOX 	595595
AWARD_SW 	J64 	SYXZ 	598598
AWARD?SW 	J256 	syxz
AWARD SW 	J262 	shift + syxz
AWARD PW 	j332 	TTPTHA
AWKWARD 	j322
awkward 	

 

AMI BIOS backdoor passwords:
AMI
AAAMMMIII
BIOS
PASSWORD
HEWITT RAND
AMI?SW
AMI_SW
LKWPETER
A.M.I.
CONDO

PHOENIX BIOS backdoor passwords:

phoenix, PHOENIX, CMOS, BIOS

MISC. COMMON PASSWORDS
ALFAROME 	LKWPETER
BIOSTAR 	lkwpeter
biostar 	setup
biosstar 	SETUP
CMOS 	Syxz
cmos 	Wodj

OTHER BIOS PASSWORDS BY MANUFACTURER
Manufacturer 	Password
VOBIS & IBM 	merlin
Dell 	Dell
Biostar 	Biostar
**Compaq 	Compaq**
Enox 	xo11nE
Epox 	central
Freetech 	Posterie
IWill 	iwill
Jetway 	spooml
Packard Bell 	bell9
QDI 	QDI
Siemens 	SKY_FOX
TMC 	BIGO
Toshiba 	Toshiba

If you can still boot from the dvd, USB or floppy, try this [Tool](http://www.cgsecurity.org/wiki/CmosPwd)

---

### Post by Gr1m3y on 2009-12-11
I've tried some of those backdoors but to no avail. It's a PhoenixBIOS. I go into the BIOS and it says "PhoenixBIOS Setup Utility", I don't know if that will help. I will maybe try to look some more backdoors up. I would really prefer to avoid taking it apart. It has a whole bunch of torque screws, which are a pain to get out.

---

### Post by Bucky Ball on 2009-12-11
One more time. Battery out, plug out, all devices out, hold power button down for 30+ seconds. No dismantling involved.

---

### Post by Gr1m3y on 2009-12-11
Well, I ended up taking it a part,, and am quite glad to say that it's in working condition again. The BIOS is reset and I can now access the boot order, however, I have bad news! I am still getting the message about the media test failure and the invalid partition table. It refuses to boot from the USB DVD drive. Any ideas? I may just look around for another laptop hard drive and switch them. I may have to dismantle it again, but hey, the good news is that I will be a master laptop dismantler by the end!

---

### Post by cholericfun on 2009-12-11
that doesnt sound right...
try out that usbDVD player on another computer to see it its acting up.

and while youre at it you can put a 9.10 liveCD in that computer and an empty usb-stick and go to system-liveusb creator (or whatever its called) and make a bootable USB for yourself (as an alternative to CD)

---

### Post by Gr1m3y on 2009-12-11
I shouldn't say that it's a USB drive, its just a wire that you can plug into a hard drive or disk drive and goes to USB. The other thing is that I have a USB stick with an older version of Ubuntu installed, and it won't boot from that either. Computers can certainly be frustrating, although at least it's giving me something to do.

---

### Post by cholericfun on 2009-12-11
wires?
even more confused now ;)

so you have a USB stick and you wire it up to hd?
ok i guess you know what youre doing. 

OK, anyhow, what i dont get is your BIOS complaing bout partition tables.
if you boot from a liveCD (-USB whatever) then BIOS will just call there and not touch the HD. thats how people fix their HD errors.
maybe some other options to wire this monster up?

---

### Post by Gr1m3y on 2009-12-11
The other option is to attempt a network install. I mean a SATA/IDE to USB 2.0 Adapter, and the USB stick is completely separate. I wasn't really thinking. Anyway, I have tried both a media boot, and a CD Drive boot, and they both give me identical messages. Man oh live I wish that they had a simple hard drive reset button:D. Also, I know a fair bit about computers, but I wouldn't say that I know what I'm talking about;).

Edit: Does anyone know if there is a way to change your partitions when you only have access to your BIOS? Maybe over a network some how?

---

### Post by darkod on 2009-12-12
> **Gr1m3y said:**
> The other option is to attempt a network install. I mean a SATA/IDE to USB 2.0 Adapter, and the USB stick is completely separate. I wasn't really thinking. Anyway, I have tried both a media boot, and a CD Drive boot, and they both give me identical messages. Man oh live I wish that they had a simple hard drive reset button:D. Also, I know a fair bit about computers, but I wouldn't say that I know what I'm talking about;).

Edit: Does anyone know if there is a way to change your partitions when you only have access to your BIOS? Maybe over a network some how?

It seems your first task is to make it boot from the LiveCD or LiveUSB. In the Try Ubuntu option it will allow to open Gparted and delete all partitions on the drive. Not sure if there is any procedure to recreate partition table but I guess it will ask itself if it detects a problem. After deleting all partitions you can even try crating one and at the point it should ask you to create new partition table if the current one is messed up.

---

### Post by Gr1m3y on 2009-12-12
The problem is that it won't boot from the CD or USB at all. I think that I'll have to look into and install over the network, or maybe there's a partition manager that can work over networks. Something to look into I guess.

---

### Post by darkod on 2009-12-12
> **Gr1m3y said:**
> The problem is that it won't boot from the CD or USB at all. I think that I'll have to look into and install over the network, or maybe there's a partition manager that can work over networks. Something to look into I guess.

The thing is, even if you start network install in the current situation it might not see your hdd at all with messed up partition table. Deleting partitions with Gparted would hopefully sort that out.
Alternatively, take out the hdd and connect it to another computer using those USB adapters or similar, format it there and create new partition table. Then a network install should be fine.

---

### Post by Gr1m3y on 2009-12-12
That's a good idea. I'll give that a try. The only problem is that I haven't done a network install before, but maybe if I'm lucky, it will realize that there is nothing on the hard drive and it will actually let me boot to the disk, or I could install it on the computer I use to format it maybe. Thanks for the idea! My Dad suggested the exact same thing as I read this:D. Thanks a lot, hopefully it works!!!

Edit: So, I used my adapter to install Ubuntu from a disk onto the laptops hard drive, it worked perfectly! I was even able to boot it, but I put it back into the other lap top and got the same message. Media test failure, check cable. Invalid Partition table! Any ideas?

So I took it apart again today, reset the BIOS again, unplugged the hard drive and the cable that connected it to the motherboard, and still no go. I get the exact same message. My guess is that the motherboard is fried and there's not much that I can do. If one of you guys think of something that might work, it would be greatly appreciated, other than that, I think that I'll just give up and maybe buy myself a netbook if I can find one on sale sometime. Thanks for all your help!

---

