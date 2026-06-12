---
title: "Installing Ubuntu only on new laptop with UEFI"
date: 2015-01-24
forum: Installation &amp; Upgrades
---

### Post by bardu on 2015-01-24
My old laptop gave up and I'm going to buy a new one to install Ubuntu only.

All newer machines appear to have UEFI and Windows 8.1 pre-installed. I did some research on installing Ubuntu on such machines but all seem to talk about dual boot.

Is there an instruction available for installing Ubuntu only?

---

### Post by oldfred on 2015-01-24
Depends a lot on brand, but you probably have to do a work around as many only boot the "Windows" UEFI entry by description.

It can be just a default install of / and swap, but usually better to have either /home or /mnt/data partition(s) and keep / (root) at 25GB.

See links in my signature for more general info.

One example but many others.
 [SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

Best to make full backup of Windows & efi partition. Many users come back and want Windows for one game or application. Or later want to sell system and have to have Windows. 
One user posted he buys system with hard drive to save a bit, but immediately removes it and adds SSD. Then later puts hard drive back to sell system with never used Windows, so no worries about his data.

---

### Post by bardu on 2015-01-24
I don't care about the brand, it just has to work. Some people say Toshiba is very Linux friendly, any experience with them?

---

### Post by lisati on 2015-01-24
I'm currently using my second Toshiba laptop. It's about 6-7 years old, and it's beginning to get a bit tired. I haven't had any Ubuntu-related issues with it or its predecessor.

---

### Post by bardu on 2015-01-24
Back then there was no UEFI, my question was more meant in this context. But thanks anyway.

---

### Post by mörgæs on 2015-01-25
[https://system76.com/](https://system76.com/)

---

### Post by oldfred on 2015-01-25
Some of the workarounds on Toshibas.

 Toshiba shows BCD entry
[http://ubuntuforums.org/showthread.php?t=2259331](http://ubuntuforums.org/showthread.php?t=2259331)
Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)
[http://ubuntuforums.org/showthread.php?t=2261061](http://ubuntuforums.org/showthread.php?t=2261061)
[SOLVED] Trouble installing Xubuntu 14.04 on Toshiba Satellite P55-A (UEFI) - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Toshiba Satellite supergrub to boot to fix things
[http://ubuntuforums.org/showthread.php?t=2240884](http://ubuntuforums.org/showthread.php?t=2240884)
TRIPLE BOOT (with Win 8.1, Linux Mint 17, Ubuntu 14.04) ON A UEFI-BASED SYSTEM - Toshiba Satellite C55T - rEFInd
[http://ubuntuforums.org/showthread.php?t=2240742](http://ubuntuforums.org/showthread.php?t=2240742)

---

### Post by sudodus on 2015-01-25
> **bardu said:**
> I don't care about the brand, it just has to work. Some people say Toshiba is very Linux friendly, any experience with them?

I bought [this Toshiba]("http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/") in April 2013. It has UEFI and it is easy to enter the UEFI menu and switch between UEFI mode and CSM (which emulated old BIOS). It is easy to create dual boot in UEFI mode with Windows. And it 'works as usual' in CSM mode.

But I have read some reports about brand new Toshibas that are unfriendly to linux. If you intend to buy a computer locally, I suggest that you bring an Ubuntu desktop USB pendrive and try to boot into a live session.
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

---

### Post by bardu on 2015-01-25
Thanks guys, will try a Toshiba Satellite Laptop (S50-B-020).

---

### Post by bardu on 2015-01-26
Just to wrap this up: I got a Toshiba Satellite S50-b, the only thing I had to do was disabling **secure boot** and the installation worked flawless from USB.

---

### Post by sudodus on 2015-01-26
I'm glad that your new Toshiba works well for you :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by mörgæs on 2015-01-26
- and add a post to the [compatibility list]("http://ubuntuforums.org/showthread.php?t=1543006").

---

### Post by bardu on 2015-01-26
Done.

---

