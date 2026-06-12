---
title: "diff caja mtp usb"
date: 2017-07-14
forum: MINT
---

### Post by Kevin McCready on 2017-07-14
I need to compare two directories. 1. the SD card on my mobile phone 2. a directory on my computer.

I've plugged my mobile phone into the computer via a usb cable, but I can't access my mobile phone via the terminal. I can only access it via the file manager (caja) on my computer.

I don't think the file manager on my computer does diff

In caja the phone is listed as:
mtp://[usb:002,003]/SD%20card

My system is:
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=18
DISTRIB_CODENAME=sarah
DISTRIB_DESCRIPTION="Linux Mint 18 Sarah"
NAME="Linux Mint"
VERSION="18 (Sarah)"
ID=linuxmint
ID_LIKE=ubuntu
PRETTY_NAME="Linux Mint 18"
VERSION_ID="18"
HOME_URL="http://www.linuxmint.com/"
SUPPORT_URL="http://forums.linuxmint.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/linuxmint/"
UBUNTU_CODENAME=xenial

---

### Post by #&amp;thj^% on 2017-07-14
I used this back with caja 1.12...so I don't know if it still works with the newer caja version:  [http://www.giuspen.com/software/cajapyext/meld-compare.py](http://www.giuspen.com/software/cajapyext/meld-compare.py)

---

### Post by Kevin McCready on 2017-07-15
Thanks for that. I don't have the skills to do that. I'm a bit reluctant to try to fiddle with the code.

---

### Post by #&amp;thj^% on 2017-07-15
Well "Meld" seems to work in caja also, Please note this on a Arch DE ATM, but i don't see why there be any difference with Ubuntu Mate and Caja.
Just an Example here and yes I'm using caja here.:)
Info on Meld: [http://meldmerge.org/help/folder-mode.html](http://meldmerge.org/help/folder-mode.html)

---

### Post by Kevin McCready on 2017-07-16
Thanks for the meld tip. Unfortunately it doesn't play nice with the phone. When I select folder and click on android it doesn't allow me to drill down into the sd card or any folders on the sd card. If I select file comparison it can see the files on the sd card, but when I click on them it doesn't load them for comparison.

---

