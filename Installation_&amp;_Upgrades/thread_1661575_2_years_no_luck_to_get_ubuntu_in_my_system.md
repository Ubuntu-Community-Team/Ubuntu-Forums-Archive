---
title: "2 years no luck to get ubuntu in my system"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by gajuambi on 2011-01-06
*_**[COLOR=Navy]2 years no luck to get ubuntu in my system[/COLOR]**_*
I took raid out of my system just to get ubuntu but n ogo.
Issue start date: june 2009 to till now
Issue: Unable to install ubuntu
hardware profile
--------------------------
Asus p5nd motherboard
 nvidia chipset
sata emulation set to sata not raid.
seagate 2*250gb drives
earlier  these drives were in raid but in the beginning from feb 2009 i disabled  raid and using the 2nd 250gb as a back up for the first primary drive.
asus driver cd has the linux drivers but it is not seeng the drives when booted from linux
Used the gigabyte motherboard as well when i was using raid.:confused:
Troubleshooting:

1.Tried  booting form the ubuntu 10.10 but checks out the requirements section  fie stating that it has the required 2.disk space but in the next  section it won't detect the both of my 250 GB seagate sata disks.
3.The seatools which is a windows based diagnostic tool for their product is also not detecting its own harddisks.
4.tried changing the sata emulation to every possible option like sata, raid and other such settings in the bios but no go.
5.tried the wubi installer from the disc inside windows but no go.
6.tried debian again today but it is unable to see the existing partitions in the disk.
7.tried  suse linux and it says that the parted is unable to modify the disk  where i want to dual boot but it does detect the drives.
8.tried booting from norton ghost and it just shows error for the disk that i want to dual boot.
9.tried every dos disk tools from hiren's boot cd 13 but no go.
10.trying with Redhat enterprise linux 5.3 and but no go.
11.Try sudo apt-get remove dmraid but no go,
12.Reinstalled  my windows 7 (the c drive was 132 gb filled with my favourite  customized applications and windows and games but i gave all that up for  nothing) ultimate and installed win 7 ultimate x64 N edition but no go. 
:confused:    [http://ambitech.blogspot.com/2011/01/ubuntu-1010-not-detecting-sata-drives.html](http://ambitech.blogspot.com/2011/01/ubuntu-1010-not-detecting-sata-drives.html)

---

### Post by anystupidname1 on 2011-01-06
1) Is a BIOS firmware update available?
2) What is the raid controller firmware version? Is there an update?
3) What is the actual RAID controller chip and version?

I've seen problems like this with "fake raid" before.

---

### Post by presence1960 on 2011-01-06
To fix it first turn off raid in your bios.  Then load up the ubuntu live CD/USB and open gparted.  If you get a drive with a funny name like nvidia_ahahdhjdfsjkf then you have mounted a raid drive that you don't want.

To get rid of it, Open a terminal and type ```
dmraid -E -r /dev/name_of_your_disk
```

Where "name_of_your_disk" is sda, sdb, etc. If both your disks are affected run the command twice-once for each disk.

Sometimes even though RAID is removed some meta-data remains on the disk. If this is the case this will clear that up.

---

