---
title: "grub doesn't load kernel; troublesome ASUS UEFI noobinstall clashing &gt;.&lt;"
date: 2014-01-25
forum: Installation &amp; Upgrades
---

### Post by Aubree on 2014-01-25
Hiya,

I have an ASUS X55C, and I've been trying unsuccessfully to grace it with a working install of Kubuntu. After two weeks of muddling about in confusion, I think it high-time to ask for assistance from a more enlightened forumer. I made the Kubuntu 13.10 amd64 iso on a USB drive using dd, but upon booting from the HD I'm stuck at grub.

My Boot Info: [http://paste.ubuntu.com/6818138/](http://paste.ubuntu.com/6818138/)

So sorry if my plea for assistance is out-of-place or has already been answered in painstaking detail. Hopefully with your collective knowledge, I can redeem myself for wasting so much time toying with it before admitting my ignorance and asking for help...  :oops:

~Aubree

---

### Post by fantab on 2014-01-25
Are you dual booting with Windows? There are Windows boot files in EFI System Partition.
Check in your UEFI boot settings to see which HDD or OS is set to boot first.... but since you are booting to GRUB, I think you are on the right track.

Run the Boot-Repair and apply 'Recommended Repair'... post the post Repair bootinfo summary.

---

### Post by Aubree on 2014-01-26
No, Windows 8 was wiped off. I think there may be residual filesystem artifacts though...
 
The grub I booted to was ver. 2.00-19ubuntu2, either from an earlier attempt to install vanilla Ubuntu (or maybe kubuntu would have that label too).

I did as you asked. The result: [http://paste.ubuntu.com/6823120/](http://paste.ubuntu.com/6823120/)

Thanks for caring about my vague, inane software difficulties! :)

---

### Post by oldfred on 2014-01-26
Since you only have Kubuntu, you may not normally get grub menu.
If you hold shift key from UEFI boot do you get grub menu? Or with some UEFI you need to use escape key.

It looks like Asus uses escape key for UEFI boot menu, so that may be an issue getting to grub menu.

Different model but often settings are common by vendor.

 ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
      
 Asus x55u UEFI change to BIOS
[http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html](http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html)


There was this bug.

 UEFI install broken when GRUB_DISTRIBUTOR!=Ubuntu (e.g. Kubuntu/UbuntuStudio) Mostly fixed in Saucy & Trusty
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1242417](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1242417)

---

