---
title: "Cant install ubuntu.. Please help brother n sister"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by roryrock on 2008-09-09
Everytime I try to install the live cd ubuntu (almost every version, from 7.04 to 8.04) on my acer laptop it always got into busybox (what the hell is that???) I got frustrated :confused: by that thing.
And then I try to install it from alternate cd..(8.04)--> no busybox but it cant install the kernel and suggest me to install it manually, and then it can't install the Grub and Lilo Neither..

Help me please.. 

my laptop spesification :
Acer
amd turion x2 2.0
memory 2 Gb
nvdia 256 mb graphic card
160 GB hdd (Sata)

thanx mate... :guitar:

---

### Post by tangibleorange on 2008-09-09
> **roryrock said:**
> Everytime I try to install the live cd ubuntu (almost every version, from 7.04 to 8.04) on my acer laptop it always got into busybox (what the hell is that???) I got frustrated :confused: by that thing.
And then I try to install it from alternate cd..(8.04)--> no busybox but it cant install the kernel and suggest me to install it manually, and then it can't install the Grub and Lilo Neither..

Help me please.. 

my laptop spesification :
Acer
amd turion x2 2.0
memory 2 Gb
nvdia 256 mb graphic card
160 GB hdd (Sata)

thanx mate... :guitar:

i see your processor is 64-bit compatible. are you trying to install the 32 or 64 bit version of ubuntu?

---

### Post by roryrock on 2008-09-09
Im using 32 bit browe.... not the 64 bit.. cause someone told me that the 64 bit is usefull if u r using an aplication that need more than 4 GB ram. 
Okey.. I'll try to install the 64 bit.. i've 2 download it first.. thnx so much...:)

---

### Post by zvacet on 2008-09-09
First you don´t have to install 64 bit version.Now some questions:

1. did you run [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM")

2. did you burn iso on lower possible speed

3. did you check disc for errors and what was result

> Everytime I try to install the live cd ubuntu (almost every version, from 7.04 to 8.04) on my acer laptop it always got into busybox

4. does this mean that some version worked good and if which one

---

### Post by tangibleorange on 2008-09-10
yeah sorry i didn't mean you had to install the 64-bit version - i was just checking which one you were using so as to try and get a better idea about why there was a kernel panic or whatever.

but yeah - the first step is to burn a new disc at slower speed after md5summing the download, or at least check your current one for errors.

---

### Post by roryrock on 2008-09-11
Got the answer guys... I can get into the OS and install it...
on the boot menu.. 
:guitar::guitar:
press F6 and add --> all_generic_ide

I have install the 8.04 but.. when I intalled the nvdia.. the next time I reboot, it cant get into the xwindow .. now is the nvidia problem that makes me cant meet the love of ubuntu... :confused::confused:

---

### Post by ad_267 on 2008-09-11
How did you install the nvidia drivers and what video card do you have?

You can run "sudo dpkg-reconfigure -phigh xserver-xorg" by booting into recovery mode to reconfigure the x server and get the default drivers back.

---

