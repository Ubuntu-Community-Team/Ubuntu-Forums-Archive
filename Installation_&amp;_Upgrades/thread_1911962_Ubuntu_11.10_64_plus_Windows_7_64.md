---
title: "Ubuntu 11.10 64 plus Windows 7 64"
date: 2012-01-19
forum: Installation &amp; Upgrades
---

### Post by Blackylol on 2012-01-19
I'll install Ubuntu and windows in the same hard drive, fresh install and both of them x64, or should I use x32 for ubuntu? will it work no problems?

should i install windows then ubuntu? i'll divide the drive

I also heard about incompatibilities of Ubuntu with high end PCs not recognizing the hard drive, maybe a bios setting... the board will be an asus p8z68 or p8h67 with intel i7 sandy bridge processor and nvidia graphics.

anyone has these and tested them?


Thanks in advance!

---

### Post by saneearth on 2012-01-19
Install Windows first, then Ubuntu. Grub installs and will pick up the Windows installation. If you do it the other way around you won't be able to boot into Ubuntu. I have used 64bit Ubuntu for some time and have had no issues. I don't think you have to worry about your hardware. You could always run the Live disk and check it out. I have a higher end PC and nvidia graphics and everything works great. The Live CD should give you and indication, though not of your final video performance once you install the nVidia drivers. You will still get an indication of other Hardware compatibility.

---

### Post by OrangeCrate on 2012-01-19
Adding...

[http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Dual-Booting_Windows_and_Ubuntu)

---

### Post by oldfred on 2012-01-19
If you have an i7 system the motherboard probably is UEFI/BIOS. That means it will use BIOS or UEFI depending on how you install. Not sure how either Windows or Ubuntu knows if in UEFI or BIOS mode.

System seems to look in efi partition and if not found revert to BIOS/MBR booting.

How large is hard drive? An install of Ubuntu onto an empty drive somewhat over 1TB will default to gpt not MBR. You really only have to have gpt if your drive is over 2TiB or about 2.2TB. Windows 64 bit (32bit does not work) will only work on a gpt drive if you have UEFI.

But I am now using gpt on all Ubuntu only drives with BIOS. And on my new SSD left a 300MB partition for future use as an efi partition if I move SSD to a new UEFI system. The efi partition has to be the first partition.

---

### Post by Blackylol on 2012-01-20
Thanks for answers

I'll test this on saturday, so i guess if the drive is less than 1 tb it will work fine, I'm like 7 years outdated so I'll have to play with those settings on bios if needed, will be my first time using an UEFI bios.

---

