---
title: "Problem installing 9.10"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by mkilagan on 2009-12-03
Hi! Newbie here.

I tried to install Ubuntu 9.10 via LiveCD, but encountered a problem re: hard drive. When I got to Step 4 of the process (disk partition), my hard drive wasn't shown. In fact, there were no drives shown at all. Here's a photo I took of my screen:

[http://img6.imageshack.us/img6/3469/img7205s.jpg](http://img6.imageshack.us/img6/3469/img7205s.jpg)

Am using a 320GB SATA II drive (NTFS), OS = Windows Vista Home Basic. When I bought the desktop unit it already had Vista on it and 2 partitions (C:/ = 150GB; D:/ = 170GB). Previously tried hooking up a portable HDD using NTFS while on LiveCD (Maxtor OneTouch Mini 4; 160GB), and that HDD didn't show up on the computer either. But I didn't have a problem with portable HDDs using FAT32.

Need your help, thanks!

---

### Post by earthpigg on 2009-12-03
what happens if you boot into live cd mode and then go to system -> admin -> partition editor?

do you see your partitions there?

the answer will help us narrow down the problem...

---

### Post by mkilagan on 2009-12-03
> **earthpigg said:**
> what happens if you boot into live cd mode and then go to system -> admin -> partition editor?

do you see your partitions there?

the answer will help us narrow down the problem...

Yes, the partitions were shown by GParted; don't know why it shows up there, but not during installation... here's the screenshot:

[http://img249.imageshack.us/i/partition.png/](http://img249.imageshack.us/i/partition.png/)

---

### Post by darkod on 2009-12-03
Make sure you do NOT have any raid options enabled in BIOS, boot with the ubuntu cd with Try Ubuntu and in terminal execute:
sudo apt-get remove dmraid

That should sort it out. Sometimes a hard drive comes with settings of raid setup and the installer does not see it in this case. The above command usually helps unless your problem is different. Try that first.

---

### Post by mkilagan on 2009-12-03
> **darkod said:**
> Make sure you do NOT have any raid options enabled in BIOS, boot with the ubuntu cd with Try Ubuntu and in terminal execute:
sudo apt-get remove dmraid

That should sort it out. Sometimes a hard drive comes with settings of raid setup and the installer does not see it in this case. The above command usually helps unless your problem is different. Try that first.

Tried it out; problem solved. Installing Karmic Koala now. Thank you so much!

---

