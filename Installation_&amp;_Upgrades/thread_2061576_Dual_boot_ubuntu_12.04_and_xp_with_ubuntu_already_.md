---
title: "Dual boot ubuntu 12.04 and xp with ubuntu already installed"
date: 2012-09-22
forum: Installation &amp; Upgrades
---

### Post by geomatic on 2012-09-22
Hello, my first post here-I hope it helps.

I am trying to dual boot Ubuntu 12.04(64-bit) and xp with Ubuntu already installed. It seems like older versions of Ubuntu allowed partitioning through the windows* live cd and a "run without install" selection. I have tried and have found no way to partition the hard drive.
So I tried to install xp (32 bit-home edition) and it ran into an error during the install that caused it to stop.

Now I am at a loss. Can I install my xp first without error? Is it because my HD is not configured for it.
Or can I set up a dual boot without having to re-install Ubuntu?

I want to learn this stuff because I plan on later installing windows 7 as the dual boot (it is a long story-I need the xp to download the windows 7 disk so I can later set up dual boot with 7)(what a hassle I know).



*ubuntu (edit)

---

### Post by undecidable on 2012-09-22
With Wz XP, I think you usually need to install it first.  The simplest solution is usually to install Wz first, then install Ubuntu.  Ubuntu will see Wz is there and guide you to where to install itself without upsetting XP.

---

### Post by Bucky Ball on 2012-09-22
This should get you going:

[http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8T9fl5QRAgAbQQ36At.?p=install%20windows%20after%20ubuntu&fr2=sb-top&fr=altavista&rd=r1]("http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8T9fl5QRAgAbQQ36At.?p=install%20windows%20after%20ubuntu&fr2=sb-top&fr=altavista&rd=r1")

Plenty of links there explaining how.

---

### Post by jerrrys on 2012-09-22
Hi geomatic

check it out

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Dual+boot+xp+with+ubuntu+already+installed&as_qdr=all&sa=Google+Search&lang=en]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Dual+boot+xp+with+ubuntu+already+installed&as_qdr=all&sa=Google+Search&lang=en")

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=install+windows+after+ubuntu&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=install+windows+after+ubuntu&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)  :)

---

### Post by oldfred on 2012-09-23
Windows will require a primary partition (sda1 thru sda4) formated NTFS with the boot flag. Most suggest it should be first, but does not have to be. Some have had issues with letting Windows find unallocated and create its own primary partition with the boot flag after an extended partition. It has been known to not correctly rewrite partition table.

Make sure you have a current copy of the Ubuntu liveCD so you can make repairs to the MBR as Windows will put its boot loader into the MBR.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/WindowsDualBoot#Installing_Windows_After_Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing_Windows_After_Ubuntu)

---

