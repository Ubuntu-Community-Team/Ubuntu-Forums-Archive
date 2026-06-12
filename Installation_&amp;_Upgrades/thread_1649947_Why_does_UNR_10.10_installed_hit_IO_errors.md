---
title: "Why does UNR 10.10 installed hit I/O errors?"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by Disabled20240622 on 2010-12-20
I've been trying to put UNR 10.10 on my ASUS EEE 901, the installer can't get very far at all before it crashes saying there was an I/O error, I've tried multiple USB sticks and installing to one SSD, then the other, so I'm sure it's a false positive.

I'm running Fedora 14 now, and whilst it has plenty of positives over Ubuntu (like the DPI setting works for my netbook). I'm just running into hell trying to get all the nonfree packages I need to be able to use this thing.

Please help me get ubuntu back.

Regards,
Alan.

---

### Post by Quackers on 2010-12-20
I would recommend checking the MD5SUM of the downloaded iso file, if you haven't already.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
If that checks out you should tap the F6 key during boot and some options should come up. One of those is to "check the cd for errors". See if that comes up with anything.
If the MD5sum checks out, but the cd/usb image does not you could try burning the image again at a slower speed.

---

### Post by PhantmKllr on 2010-12-20
Are you sure that your download of Ubuntu wasn't corrupted? If so, then try different USB ports (if any).

---

### Post by Disabled20240622 on 2010-12-22
I was seeing this error with desktop and netbook versions, the desktop ISO was fine, the netbook ISO was faulty, so I downloaded a good copy and tried with that.

Trying to hit F6 when it starts, I can get to the bit which claims F6 will give me more options. But nothing at all happens when I hit F6.

Since my netbook has 2 SSDs (4GB and 16GB) I like to install LVM to the live system before installing, so that I can install to a single 19GB logical volume with 1GB swap. I've done this and set up grub2 to cope many times now.
So far on 10.10 I've been unable to install LVM, looks as if a lot of LVMs dependencies aren't met any more.

Gparted also won't start (hits an assert). I don't think 10.10 is a wise move, maybe I'll wait for 11.04. I'll continue fighting Fedora till then.

---

### Post by TerrorBite on 2010-12-23
I'm seeing exactly the same thing on my HP Mini. The installer takes a very long time to move between pages, then when it gets to the timezone/copying files screen, it errors out saying there was an I/O error. I've tried installing off 2 different flash drives, identical results. I might just have to redownload the iso and see if that helps.

I'm running the 10.10 desktop live as I type this, waiting for the installer to progress (which it isn't), and I've noticed a lot of crash reports popping up. All in all, it seems quite unstable for some reason.

Edit: Returning to my Windows install, I just downloaded md5summer (from [http://www.md5summer.org](http://www.md5summer.org) ) and verified that the md5sum for the iso I downloaded does NOT match. I'm downloading again in the hope that I get an uncorrupted version, otherwise I may have to choose a different mirror site. (I downloaded from my local mirror at mirror.optusnet.com.au)

---

