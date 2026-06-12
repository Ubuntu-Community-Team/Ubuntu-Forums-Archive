---
title: "ubuntu 11.04 fails to boot with a raid 0 setup"
date: 2011-08-12
forum: Installation &amp; Upgrades
---

### Post by stukad on 2011-08-12
Got a wierd problem trying to install ubuntu, or actually boot ubuntu 11.04 on a "hardware" ssd raid 0 setup. It just won't boot after POST. Tried installing it on one partition. Tried diffrent partitions such as /boot /root /swap... no luck. Even tried softraid and putting the /boot dir on a physical disc without any success.

Funny thing is when i gave linux mint 11 a try. It worked flawlessy on a hardware raid 0 setup. 

So my question basicly is, what is it that linux mint 11 has that ubuntu 11.04 misses when it comes to running em on raid setups?

Comp: Asus Sabertooth P67 | i5-2500K @ 3.33 (Corsair H60) | Asus GTX560 1GB OC | Tagan piperock 900W | 8GB Corsair Vengeance @ 1600MHz | SSD: 2 x Corsair Force GT 60GB @ raid 0 | Linux Mint 11

---

### Post by psusi on 2011-08-12
Unless you have an expensive add in raid card not listed in your signature, then you don't have hardware raid.  Your motherboard has fakeraid, which you can not mix with software raid.  Last time I checked, Mint did not work with fakeraids.  You will need to be much more specific about how you installed Ubuntu and what didn't work for any chance of figuring out what is wrong.

See [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto) for more info.

---

### Post by stukad on 2011-08-12
> **psusi said:**
> Unless you have an expensive add in raid card not listed in your signature, then you don't have hardware raid.  Your motherboard has fakeraid, which you can not mix with software raid.  Last time I checked, Mint did not work with fakeraids.  You will need to be much more specific about how you installed Ubuntu and what didn't work for any chance of figuring out what is wrong.

See [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto) for more info.

Hence the "hardware" raid...

Okey some more info about the install:

**Attempt 1:** Ubuntu desktop 64bit

a) sata controller set to "raid mode" 
b) raid arrey created via bios raid menu (ctrl-l)
c) Booting of a usbstick, runs ubuntu desktop 64 bit install on the entire newly created raid drive. (use entire drive as option)
d) Installation runs smooth without any problems
e) last step to complete: reboot and remove the usb stick
f) after the power on self test the startup fails and won't boot.
g) Tried all available boot devices (bootorder in bios) same problem

**Attempt 2:** Ubuntu alternate CD

a) deleted the "hardware" raid in bios and changed back the sata controller
b) [https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html) - to the line
c) This step by step also fails to boot after the power on selftest

**Attempt 3:** Ubuntu alternate CD

a) same conf as Attempt 2.
b) [http://www.youtube.com/watch?v=-x2rZe2Z9as](http://www.youtube.com/watch?v=-x2rZe2Z9as)
c) This step by step also fails to boot after the power on selftest


**Attempt 4:** Linux Mint 11

a) sata controller set to "raid mode" 
b) raid arrey created via bios raid menu (ctrl-l)
c) Booting of a usbstick, runs Linux Minst 64 bit install on the entire newly created raid drive. (use entire drive as option)
d) Installation runs smooth without any problems
f) *Smiles* It boots and and works flawlessy with mindblowing drive read speeds: 

[IMG]http://data.fuskbugg.se/skalman02/4e45ad690c7db_ssd.png[/IMG]

**So why on earth does mint boot and ubuntu not?**

---

### Post by stukad on 2011-08-14
Noone knows huh?

---

### Post by YesWeCan on 2011-08-14
Trying to understand what you are trying to do...

There are 3 types of RAID:
1) Windows software RAID, aka fakeraid. This is the one you configure in your bios and then install a driver in Windows.

2) linux software RAID. Does not use Windows RAID facilities.

3) Hardware RAID - usually a PCI card that manages an array independently of bios and OS.

Which are you trying to use?

---

### Post by stukad on 2011-08-14
linux software raid i guess..

Simply enable a raid 0 arrey in bios. And install ubuntu on it.

This works out of the box with linux Mint. When i try ubuntu it just won't boot.

---

### Post by YesWeCan on 2011-08-14
I think you are trying to do a combination of 1 & 2. I'm not sure why Mint appears to be working. Unless you want to use Windows on a RAID I'd recommend you stick strictly to 2. The  Ubuntu will install ok.

To do this, disable all RAID options in your bios. Then boot Ubuntu and run
[COLOR="Navy"]sudo apt-get install dmraid
sudo dmraid -Er /dev/sdx[/COLOR] (x=a,b,c...)
to delete the Windows RAID superblocks on your disks.

Then try installing Ubuntu as a RAID, probably best to use the alternate CD for this.

---

### Post by stukad on 2011-08-14
> **YesWeCan said:**
> I think you are trying to do a combination of 1 & 2. I'm not sure why Mint appears to be working. Unless you want to use Windows on a RAID I'd recommend you stick strictly to 2. The  Ubuntu will install ok.

To do this, disable all RAID options in your bios. Then boot Ubuntu and run
[COLOR="Navy"]sudo apt-get install dmraid
sudo dmraid -Er /dev/sdx[/COLOR] (x=a,b,c...)
to delete the Windows RAID superblocks on your disks.

Then try installing Ubuntu as a RAID, probably best to use the alternate CD for this.



Never used windows on any of my drives. So I don't see why option 2 suddenly would start to work. Gonna give it a new try tho

---

