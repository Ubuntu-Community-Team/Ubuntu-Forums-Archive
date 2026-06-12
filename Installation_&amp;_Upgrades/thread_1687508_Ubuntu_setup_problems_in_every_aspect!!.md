---
title: "Ubuntu setup problems in every aspect!!"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by chaitanya_lu on 2011-02-14
First of all, I am an absolute beginner in world of Ubuntu. I have no idea about command terminal, etc. But I am good at Windows.
 
My problems begin with the setup itself.
 
1) I have three partitions on my hard disk. All NTFS. One contains the Windows 7 and other contains the Recovery data. Third partition is a 99mb partition which contains some BIOS data therefore it is of no use. I fear that repartitioning the partition with recovery data (and also my other data) will not allow me to use the option again. I installed Ubuntu 9.04 inside windows from the Live CD therefore.
 
2) When I boot into Ubuntu, it does not detect or show the second partition(with recovery data) at all as if it doesn't exist. I therefore cannot access the data.
 
3) I have been unable to connect via WiFi. It seems that the drivers for my WiFi adapter are absent. I cannot connect to the internet in any other way.
 
4) Ubuntu runs in the lowest graphic mode despite the fact that my laptop has a switchable graphics option (Intel Media Accelerator HD and the ATI Radeon 5650 1Gb).
 
Intel i3 370M @ 2.4Ghz
3Gb DDR3 RAM
Ati Radeon 5650
Atheros Wifi with bluetooth
500gb HDD
I guess that is more than enough to run any OS.
 
Expecting a quick response. I really want to use Ubuntu with all the capabilities.

---

### Post by mörgæs on 2011-02-15
Hi, welcome to the fora.

Ubuntu 9.04 is obsolete, so let's not spend time on this one. How does Ubuntu 10.04 and/or 10.10 run in a live boot?

---

### Post by Rubi1200 on 2011-02-15
When you say "inside Windows" do you mean with Wubi?

---

### Post by chaitanya_lu on 2011-02-16
Hi!!

I have problems with the setup of ubuntu and also with the drivers.

I have Ubuntu 9.04 Live CD. I installed Ubuntu inside Windows so that I could get a good feel before I make partitions for it.

1) When I installed it and booted Ubuntu, I wasn't able to connect to the internet via WiFi as that's the only way I can access internet. It seems that the OS doesn't detect my WiFi Adapter because when I click the 'network' type logo, it only has VPN as the option and no wireless option. Even if I did install the WiFi Settings for the network, the WiFi won't connect. I have Atheros AR9285 WiFi adapter. I have tried other threads but I have not been able to do it. It should be noted that my bluetooth, sound works just fine.

2) Ubuntu doesn't run in extra visual effects mode. It says it cannot be enabled. My laptop has an ATI Radeon 5650 1gb which is switchable with the
Intel Graphics Media Accelerator HD with minimum graphic memory of 32 MB which can increase upto about 700Mbs.

3) I have four partitions in my HDD. They are c: NTFS (Conatins Windows 7), D: NTFS (Contains all my other data with RECOVERY data as well), 
E: FAT32 (Contains some bios related data) and a SYSTEM partition. Whenever I boot into Ubuntu, it doesn't show the D: partition. What's the problem?

    I thought all this was due to the older verion of Ubuntu (10.10 has been released). Therefore I downloaded ubuntu 10.10 iso. Now I have found that it doesn't
contain any exe file (wubi.exe) so that I could install Ubuntu 10.10 within Windows. I downloaded that as well (wubi.exe for Ubuntu10.10). But it returns some error
of 'cannot download metalink and thus download'.

Please help me out. I really wan't to try out Ubuntu. I am a beginner in Ubuntu but I know Windows quite well.

My Config: 
HP dv6 3057tx Laptop
Intel i3 370M
ATI Radeon 5650 1gb switchable.
500Gb HDD
Atheros AR9285 Wifi adapter.

Sorry for the long post but I thought giving details would be good

---

### Post by bcbc on 2011-02-16
for the wireless...
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10022021](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10022021)

If you download the desktop .iso for 10.10 it will have wubi.exe on it. Not the dvd or alternate iso.

---

### Post by chaitanya_lu on 2011-02-16
but the download file is named ubuntu10.10-desktop-amd64.iso
I am using intel i3. Will that not cause problems?? AMD64 confuses me??

---

### Post by bcbc on 2011-02-16
the naming is not very smart. it should say 64bit, not amd64. You can download the 32bit if you like - that will work as well.

---

