---
title: "Installed Ubuntu, Now i cannot load Vista!!!!!"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by Sjorge3442 on 2008-11-23
Hello. I am new here and also new to ubuntu. I had a random urge to install it when i saw some sweet videos of the OS.

Any way. 

So I went through the Ubuntu installation process and had the automatic partioner split my drive and Ubuntu finished installing. Now i CANNOT load Vista and i would like to. When i choose Vista(Longhorn) at start up, a disk check comes up and freezes at 7%. I also cannot mount my vista partition from ubuntu. 

How do i fix this. I have read somewhere else that the auto partitioner for ubuntu screws up vistas part of the drive and their is something called ntfsfix? 

So if someone could PLEASE tell me how to go through fixing this problem i would greatly appreciate it. Remember. I know NOTHING about linux based OS so if you could tell me step by step that would be great. 

Thanks a lot
Steve

---

### Post by Sjorge3442 on 2008-11-23
come on..... no one can help?

---

### Post by caljohnsmith on 2008-11-23
If you use gparted to resize Vista, it usually temporarily breaks Vista until you use a Vista Recovery CD to fix Vista again. The reason is because Vista (unlike any other OS I know of) maintains its own HDD partition table outside of the main one in the HDD's MBR (Master Boot Record); so if you use something like gparted to repartition, it updates the MBR with the new partition table, but gparted knows nothing about Vista's own partition table. That then usually makes Vista unbootable until you can fix Vista's partition table with a Vista Install/Recovery CD.

If you don't have a Vista Install CD, you can instead download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/") and use that. Just choose the "Vista Repair" option, and if all goes well, you should be set. Let me know how it goes.

---

### Post by Sjorge3442 on 2008-11-23
thanks a lot!!! I am currently out and have no dvd's with me but i will definetly be downloading and using it. I have a recovery cd from HP but i have no option to "repair" after it loads, it just gives me the option to reformatte. Not trying tod o that. 

Thanks again. I will be sure to let you konw how i make out.

Steve

---

### Post by Sjorge3442 on 2008-11-23
ok now i have one problem. The link doesnt work......

---

### Post by steveneddy on 2008-11-23
> **Sjorge3442 said:**
> ok now i have one problem. The link doesnt work......

Works great here.

Here's the two links:

32 bit:

[http://neosmart.net:6969/torrent.html?info_hash=c7411cffb5b0c27b28d0ec080af55ea0016f7b7b](http://neosmart.net:6969/torrent.html?info_hash=c7411cffb5b0c27b28d0ec080af55ea0016f7b7b)

64 bit:

[http://neosmart.net:6969/torrent.html?info_hash=fbf47dd7d63708ea2e7acac1709747c5f7eb94b5](http://neosmart.net:6969/torrent.html?info_hash=fbf47dd7d63708ea2e7acac1709747c5f7eb94b5)


Good Luck.

---

### Post by Sjorge3442 on 2008-11-23
ahhh Im not going to be able to acess it because my school blocks torrent websites....looks like i have to wait until thanksgiving.

---

