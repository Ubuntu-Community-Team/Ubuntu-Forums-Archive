---
title: "Problem installing ubuntu on desktop"
date: 2012-06-24
forum: Installation &amp; Upgrades
---

### Post by horgh64 on 2012-06-24
RAID volume 0, both hard drives formatted, installing via CD, it got close to the end and it came up saying:

Executing 'grub-install/dev/mapper' failed.
This error is a fatal one, which is great!

Wat?

---

### Post by darkod on 2012-06-24
You install on fakeraid with the alternate cd, not the liveCD. The liveCD often fails in the grub2 install step.

Also, with fakeraid the bootloader goes to the MBR of the raid device, like /dev/mapper/blahblah_Volume0 or similar, without having a partition designator like Volume0p5.

You can try installing with the alternate cd, or just adding the grub2 to the MBR of the array from live mode.

---

### Post by horgh64 on 2012-06-25
What alternate cd? Where is it available?
It honestly would have been nice to know before.

---

### Post by darkod on 2012-06-25
Select the image you want from the list of all images, alternate 32bit or 64bit:
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

> 
**Alternate install CD**

  The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:
  
[LIST]
[*]setting up automated deployments;
[*]upgrading from older installations without network access;
[*][COLOR=Red]LVM and/or RAID partitioning; [/COLOR]
[*]installs on systems with less than about 384MiB of RAM (although note that low-memory systems may not be able to run a full desktop environment reasonably).
[/LIST]
   In the event that you encounter a bug using the alternate installer, please file a bug on the [debian-installer]("https://bugs.launchpad.net/ubuntu/+source/debian-installer/+filebug") package. 
  There are two images available, each for a different type of computer:
  [PC (Intel x86) alternate install CD]("http://releases.ubuntu.com/precise/ubuntu-12.04-alternate-i386.iso")  For almost all PCs. This includes most machines with Intel/AMD/etc type processors and almost all computers that run Microsoft Windows, as well as newer Apple Macintosh systems based on Intel processors. Choose this if you are at all unsure.[64-bit PC (AMD64) alternate install CD]("http://releases.ubuntu.com/precise/ubuntu-12.04-alternate-amd64.iso")  Choose this to take full advantage of computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon, Core 2). If you have a non-64-bit processor made by AMD, or if you need full support for 32-bit code, use the Intel x86 images instead.  A full list of available files, including [BitTorrent]("https://help.ubuntu.com/community/BitTorrent") files, can be found below.
  If you need help burning these images to disk, see the  [CD Burning Guide]("https://help.ubuntu.com/community/BurningIsoHowto").

---

