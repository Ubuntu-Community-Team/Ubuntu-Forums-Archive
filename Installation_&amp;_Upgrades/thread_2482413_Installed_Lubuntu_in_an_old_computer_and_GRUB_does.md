---
title: "Installed Lubuntu in an old computer and GRUB does not load windows XP anymore"
date: 2022-12-30
forum: Installation &amp; Upgrades
---

### Post by idillus2 on 2022-12-30
Hi,

I have just recently dusted my dad´s old Asus eeePC. I wanted to give it a second life so I decided to install Lubuntu. The PC has now two OS, Windows XP and Lubuntu. They are managed by GRUB2. When I select Windows XP, the OS does not load. I get a black screen and it never loads. I did check the GRUB configuration and it seems OK to me. I can access the Windows files from Lubuntu. It seems that I may have missed something when installing Grub. Here is the pastebin

[https://pastebin.ubuntu.com/p/dy5VYs6zG4/](https://pastebin.ubuntu.com/p/dy5VYs6zG4/)

I do hope you can help me. 

Thanks a lot.

---

### Post by tea for one on 2022-12-30
[COLOR="#0000FF"]Line 46[/COLOR] - Operating System:  Ubuntu 18.04.6 LTS

Lubuntu 18.04 reached End of Life in April 2021 and does not receive security updates.
Mainstream support for Windows XP ended in April 2009 and extended support ended in April 2014 

You should really consider using a supported 32-bit release
Plenty of info on the internet but here is one to get you started [https://itsfoss.com/32-bit-linux-distributions/](https://itsfoss.com/32-bit-linux-distributions/)

---

### Post by yancek on 2022-12-30
If you check the grub.cfg file on Lubuntu and the entry for XP is a correct chainloader entry, the problem is likely a corrupted boot file on XP.  You can't do anything to repair that from Lubuntu or any Linux and will need some windows boot repair disk.

---

### Post by ubfan1 on 2022-12-30
What model eeePC ?  I have a 2013 one that's full 64 bit UEFI, and your disk, even though with MSDOS partitioning for legacy WinXP does have a small EFI partition. You might not be limited to 32 bit Oses, and consider dumping XP and changing the disk to use gpt.

---

### Post by guiverc on 2022-12-30
You can use `ubuntu-support-status` to confirm what packages of a 18.04 system (inc. Lubuntu) still get security fixes/patches.

I talked about it [here on Lubuntu's discourse/forum]("https://discourse.lubuntu.me/t/lubuntu-18-04-lts-end-of-life-30-april-2021/2466/7").

Links 
- [https://lubuntu.me/bionic-eol/](https://lubuntu.me/bionic-eol/)
- [https://discourse.lubuntu.me/t/lubuntu-18-04-lts-end-of-life-30-april-2021/2466](https://discourse.lubuntu.me/t/lubuntu-18-04-lts-end-of-life-30-april-2021/2466)
- [https://fridge.ubuntu.com/2021/09/17/ubuntu-18-04-6-lts-released/](https://fridge.ubuntu.com/2021/09/17/ubuntu-18-04-6-lts-released/)  (no mention of any *flavor* as they'd all reached EOL)
- [https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/](https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/)  (*flavors are mentioned with EOL April 2021 or 3 years after initial release of 18.04*)

If your asus eepc has a intel atom n270 CPU (or equiv.) it'll be x86 (32bit only).

Be aware all *i386* builds end in April 2023 for *bionic* or 18.04; as 18.04 moves to ESM, with leading indications being *i386* is not included. Canonical still have time to change that decision but I doubt that will happen.

I used an eeepc in my QA ("*Quality Assurance*") of Ubuntu releases up to 19.04 (ie. `asus eepc 1000HE (intel atom n270, 1gb, intel mobile 945gse integrated), wireless RT2790`), but given the device is limited to *i386* (in Debian/Ubuntu terms, ie. 32-bit x86) I'd not install Ubuntu (*how I see Lubuntu 18.04 LTS now*) anymore and just use Debian.  I also do some QA with Debian too, and know it runs fine too (*mine in fact has Debian on it now!*). 

If however, you don't intend on using that device beyond April 2023, I'd likely not bother a re-install.

 I won't comment on XP, as the only XP I saw on eeePCs did not include/use any ESP (EFI System Partition) your layout has, nor did Lubuntu 18.04 create/use one either at install in QA (*though it could be made to use it* *if forced, but your device maybe amd64 capable & newer maybe?*).

---

