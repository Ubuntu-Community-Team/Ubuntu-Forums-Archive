---
title: "LiveUSB taking forever to install 10.10"
date: 2010-12-12
forum: Installation &amp; Upgrades
---

### Post by misterman73 on 2010-12-12
Ahh, square one. We meet again.

As predicted by the thread I made earlier today, I'm back with more Ubuntu install woes.

I am currently trying to install 10.10 off a LiveUSB. It's been "installing" for about three hours or so. I see a lot of "RF change in progress" and something about handshakes.

On another thread where the poster had similar problems, he was told to type 

Code:
sudo fdisk -lu

into the terminal. I did the same thing, but was completely puzzled by the results.
Now, I would like to copy past the results here, but I cant, because the connection speed on the install computer is 19.2 mbps. Firefox wont load jack.

**SO.** Hand typed, with love.

Disk /dev/sda: 750.2 GB, 750156374016 bytes
225 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector Size (logical/physical) 512 bytes / 512 bytes
I/O size (minimum/optimal) 512 bytes / 512 bytes
Disk Identifier 0x000bb83e

Device Boot                      Start                   End          Blocks      Id               System
/dev/sda1                       2048           1440573439 720285696    83              Linux
/dev/sda2              1440575486         1465147391  12285953     5              Extended
/dev/sda3              1440575488         1465147391  12285952     82   Linux swap / Solaris

Disk /dev/sdb: 8036 MB, 8036285952 bytes
225 heads, 63 sectors/track, 977 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot           Start              End           Blocks           Id          System
/dev/sdb1     *        44            15679439      7839698          b                W95 FAT32

Please help me before I put my fist through the monitor or do something rash like buy **another** copy of windows.

---

### Post by sikander3786 on 2010-12-12
That fdisk output seems pretty ok.

How was the USB created? Did you check the MD5SUM of downloaded image?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

How to create Live USB:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

Or better try with some other USB device.

Where on the installation screen does it get stuck? Any errors are reported then?

---

### Post by misterman73 on 2010-12-12
OK, so, I'm in. Turns out that it doesnt accept user name changes. Like I changed it from eddy to Eddy and it wouldnt give me a check mark.

Anyway, now Ubuntu is booting off my harddrive. There are still a couple problems, however.

1) It says I'm connected to my wireless internet, but I only get internet access for a few seconds before it stops receiving information. 

2) Every once in a while, the screen flashes black and then immediately comes back.

3) When I boot up, before it even reaches the Ubuntu screen, these words are plastered up on a blank screen twice:

modprobe: FATAL: Could not load /lib/modules/2.6.35-22-generic/modules.dep: No such file or directory.

modprobe: FATAL: Could not load /lib/modules/2.6.35-22-generic/modules.dep: No such file or directory.

What did I break?

---

