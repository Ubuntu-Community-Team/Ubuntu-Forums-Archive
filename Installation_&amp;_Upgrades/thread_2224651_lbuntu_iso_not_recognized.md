---
title: "lbuntu iso not recognized"
date: 2014-05-17
forum: Installation &amp; Upgrades
---

### Post by s9032g@comcast.net on 2014-05-17
I have decided to switch from Ubuntu 14.04 to Lbuntu 14.04. I downloaded and burned an iso. It looks like this:
/media/steven/Lubuntu 14.04 LTS i386/boot
/media/steven/Lubuntu 14.04 LTS i386/casper
/media/steven/Lubuntu 14.04 LTS i386/dists
/media/steven/Lubuntu 14.04 LTS i386/install
/media/steven/Lubuntu 14.04 LTS i386/isolinux
/media/steven/Lubuntu 14.04 LTS i386/pics
/media/steven/Lubuntu 14.04 LTS i386/pool
/media/steven/Lubuntu 14.04 LTS i386/preseed
/media/steven/Lubuntu 14.04 LTS i386/ubuntu
/media/steven/Lubuntu 14.04 LTS i386/.disk
/media/steven/Lubuntu 14.04 LTS i386/autorun.inf
/media/steven/Lubuntu 14.04 LTS i386/md5sum.txt
/media/steven/Lubuntu 14.04 LTS i386/README.diskdefines
/media/steven/Lubuntu 14.04 LTS i386/wubi.exe

I set my bios to boot only from the iso DVD however I gett the message, "no operating system found". I erased the DVD and burned it agai9n with the same result. I have been successful in the past with isos.

---

### Post by sudodus on 2014-05-17
Some questions and tips:

Did you check the md5sum?

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Does your computer boot from another CD/DVD disk in the same DVD drive?
Does this CD/DVD disk boot in another computer?

Try to burn the disk with the slowest speed possible.

If you computer can boot from USB, make a USB boot drive and try to boot that way

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

-o-

It is an i386 (32-bit) system. Is the computer running a BIOS or UEFI system? You need a 64-bit system with UEFI.

---

### Post by s9032g@comcast.net on 2014-05-18
I decided to use a fresh DVD and a different iso burner (although the first one I used had worked fine many times). SUCCESS

---

### Post by Rex Bouwense on 2014-05-18
Excellent.  The tips that were provided by sudodus should be engraved in gold because the great majority of all installation problems can be traced to one of them.

---

