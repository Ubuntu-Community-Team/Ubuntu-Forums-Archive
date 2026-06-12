---
title: "Can´t install Ubuntu from live usb"
date: 2011-03-10
forum: Installation &amp; Upgrades
---

### Post by Liborek on 2011-03-10
Hi, I have a problem with installing Ubuntu from a USB flash drive. I have Acer TimelineX 3820TG. I have Windows 7 Home from Acer and I installed Mandriva OS from USB(from USB because this Acer doen't have a DVD drive). It was OK, but I want reinstall Windows 7 and so I did. Now I have Windows 7 Professional and it wrote over Mandriva's GRUB. 

It wasn't a big problem. For a while I was just using Windows 7 but now I am thinking that I need some OS with Linux and I am thinking about Ubuntu. So I create with original apps from Ubuntu live usb flash drive. System boots and I can work with it. When I click on Install Ubuntu 10.10, I choose language, then on next window I click Forward but it just show waiting cursor and nothing happens (I try it with Fedora and it is same). It doesn't freeze so I can end install and I can take screenshot (when I was taking the screen, cursor was shown as waiting, not normal as in picture, it's weird).* [Window when I stopped with install]("http://img853.imageshack.us/i/screenshot1k.png/")*

I think there is some problem with "Disk and Volumes" and so. But I used chkdsk from Windows 7 on boot and it said everything is all right. I tried utility in Ubuntu to check filesystem and it is all right too. *[Screen with volumes, disk and other things.]("http://img251.imageshack.us/i/screenshotvq.png/")*

---

### Post by Dutch70 on 2011-03-10
Welcome to UF Liborek,

Uncheck download updates while installing & install third party software. You can always do that after the install. There may be a problem with the download mirror.

According to the thread currently above yours, that's more than likely the problem.
[http://ubuntuforums.org/showthread.php?t=1703902]("http://ubuntuforums.org/showthread.php?t=1703902")

---

### Post by Liborek on 2011-03-10
Hi Dutch70,
I know that on screen there are checked the options but I tried with unchecked too.

---

### Post by Hedgehog1 on 2011-03-10
Liborek,

I have a feeling you are out of partitions (and a little futzing **<Technical term: Futzing>** may need to be done).

Please boot off of the USB, select 'try' and then:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```
Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS

---

### Post by Liborek on 2011-03-10
Hi Hedge,
```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x50255024

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1658    13312000   27  Unknown
/dev/sda2   *        1658        1671      102400    7  HPFS/NTFS
/dev/sda3            1671       37571   288371419+   7  HPFS/NTFS
/dev/sda4           37571       77826   323343361    f  W95 Ext'd (LBA)
/dev/sda5           40077       77826   303215616    7  HPFS/NTFS

Disk /dev/sdb: 4011 MB, 4011851776 bytes
88 heads, 24 sectors/track, 3710 cylinders
Units = cylinders of 2112 * 512 = 1081344 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           4        3711     3913792    c  W95 FAT32 (LBA)

```Thank you for help

---

### Post by Hedgehog1 on 2011-03-10
```
   Device Boot  Start    End      Blocks   Id  System
/dev/sda1           1  1658    13312000   27  Unknown
/dev/sda2   *    1658  1671      102400    7  HPFS/NTFS
/dev/sda3        1671 37571   288371419+   7  HPFS/NTFS
[B][COLOR="Red"]/dev/sda4       37571 77826   323343361    f  W95 Ext'd (LBA)
  /dev/sda5     [COLOR="DeepSkyBlue"]40077[/COLOR] 77826   303215616    7  HPFS/NTFS[/COLOR][/B]
```

**_Yes indeed _**- you are allowed 4 primary partitions on any 1 disk (always **sda1**-**sda4**) and they are all taken.  **sda5** lives inside extended partition **sda4**.

So, you have a few decisions to make.

**sda5** could be shrunk down, and a new **sda6** for Ubuntu and **sda7** added for SWAP inside the **sda4** extended partition:

```
   Device Boot  Start    End      Blocks   Id  System
/dev/sda1           1  1658    13312000   27  Unknown
/dev/sda2   *    1658  1671      102400    7  HPFS/NTFS
/dev/sda3        1671 37571   288371419+   7  HPFS/NTFS
[COLOR="Red"][B]/dev/sda4       37571 77826   323343361    f  W95 Ext'd (LBA)
  /dev/sda5     [COLOR="DeepSkyBlue"]37572[/COLOR] 60000                7  HPFS/NTFS
  /dev/sda6     60001 75000                   ext4 (Linux/Ubuntu)
  /dev/sda7     75001 77825                   Linux Swap[/B][/COLOR]
```

What do you think?

***The Hedge***

:KS

---

### Post by Liborek on 2011-03-10
Yes, I think that would be great. I just want to have 1 partion for W7 (it´s sda3), 1 partion with data (NTFS, it´s sda4) and next partion with Ubuntu. But there are partions for recovery and system reserved and these are sda1 and sda2. So I must do what you wrote, right? Could you help me how I can do that?

---

### Post by Dutch70 on 2011-03-10
> **Liborek said:**
> Yes, I think that would be great. I just want to have 1 partion for W7 (it´s sda3), 1 partion with data ***(NTFS, it´s sda4)*** and next partion with Ubuntu. But there are partions for recovery and system reserved and these are sda1 and sda2. So I must do what you wrote, right? Could you help me how I can do that?

Actually your NTFS/data partition is sda5.

You'll have to shrink sda5 to leave enough room for Ubuntu. That will leave unallocated space. Then you create 2 new logical partitions, formatted to ext4. They will be called sda6 & sda7. One of them will be a for swap, and one for "/" (root).

On a side note. Ubuntu will be able to read/write to your ntfs partitions. (sda3 & sda5)

---

### Post by Liborek on 2011-03-10
Dutch70: I am sorry u are right. My data are on sd5. 

Next, I understand what you want for me to do but I dont know how can I do that. I see screen from disk utility as I posted in first topic and I dont know how can I changed it to what you wrote. I was trying and now I have two ext4 manually created in disk utility but problem is not solved. I cant proced with installation. I know that there is some disk manager during the installation of system but I cant get to it. [URL="http://img340.imageshack.us/i/screenshotaq.png/"]Now in disk utility I have this. 
[/URL]

---

### Post by Liborek on 2011-03-10
One more thing, I dont know if it helps but when I was trying install before (not now, now I cant get this error after I changed that volumes) [I get this error]("http://img683.imageshack.us/i/screenshot2iw.png/") after I click on Forward (I dont wrote it before because I dont notice it, It was in top bar just next to "Wired network connection".

Edit: After clicking on Report problem, it shows that there was problem with reporting.

---

### Post by Dutch70 on 2011-03-10
> **Liborek said:**
> Dutch70: I am sorry u are right. My data are on sd5. 

Next, I understand what you want for me to do but I dont know how can I do that. I see screen from disk utility as I posted in first topic and I dont know how can I changed it to what you wrote. I was trying and now I have two ext4 manually created in disk utility but problem is not solved. I cant proced with installation. I know that there is some disk manager during the installation of system but I cant get to it. [URL="http://img340.imageshack.us/i/screenshotaq.png/"]Now in disk utility I have this. 
[/URL]

I have personally never used disk utility to partition a disk. There is a program specially made for that called Gparted. It's under >system>admin>gparted.(if it's not there, install it from software center) Open it and take a good sized picture of it, save it to your desktop & use the paper clip in the toolbar of your next post to "attach" it.

---

### Post by Liborek on 2011-03-11
I have problem with GParted, It will crash everytime when It's starting (in bottom bar, there is "Searching /dev/sda partions" and after little time it disappear and in top bar there is crash report and when I choose report it says something that it cant be reported.

---

### Post by Dutch70 on 2011-03-12
> **Liborek said:**
> I have problem with GParted, It will crash everytime when It's starting (in bottom bar, there is "Searching /dev/sda partions" and after little time it disappear and in top bar there is crash report and when I choose report it says something that it cant be reported.

It is also Gparted that is crashing on you during install. My only suggestions are, to remove & reinstall Gparted when you are running your live cd/usb. You may also need to purge it. I believe the command is

```
sudo apt-get purge gparted
```

Just use sofware center or synaptic to remove & re-install.

Your other option is to create another live cd/usb.

---

### Post by Liborek on 2011-03-14
Thanks for your help but I can´t solve it so I decided to virtualized Ubuntu under W7.

---

### Post by Dutch70 on 2011-03-14
> **Liborek said:**
> Thanks for your help but I can´t solve it so I decided to virtualized Ubuntu under W7.

Sorry to hear that, maybe you'll have better luck with 11.04 when it comes out next month.

---

