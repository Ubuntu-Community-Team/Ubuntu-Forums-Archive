---
title: "Creating USB installer stick"
date: 2012-12-30
forum: Installation &amp; Upgrades
---

### Post by The Cog on 2012-12-30
Well, it looks like ubuntu QA is down to its normal standards. I decided to try 12.10 64-bit (I'm running 12.04 32-bit). But it cannot create the USB installer - it goes through copying files, asks for a password to install the bootloader then crashes.

So anyway, I took a long shot and just used dd to write the CD image directly to the stick like this:
```
sudo dd if=iso/xubuntu-12.10-desktop-amd64.iso of=/dev/sdf
``` and I was pleasantly surprised to find that the stick happily booted into the installer program.

Excited that maybe I'd found a more reliable way to make installers etc, I then used dd to write a systemrescuecd image to the stick. This did not boot.

So I was wondering, why does the xubuntu CD image boots from the stick and why doesn't the systemrescue CD image?. Why don't all CD images just work when burned to a stick? There must be a difference in the way they're treated somehow. Can anyone kindly point me to material that explains the differences?

---

### Post by Cheesemill on 2012-12-30
It's because some ISO files are what is known as hybrid ISOs, these are designed to allow you to boot directly from the image on the USB instead of having to use the files from a standard ISO along with a separate bootloader.

I've used the dd method to create USBs for some time now, it's been possible since 11.10 with Ubuntu media.

[http://wiki.geteasypeasy.com/Hybrid_ISO/IMG_format#How_the_Hybrid_ISO.2FIMG_works](http://wiki.geteasypeasy.com/Hybrid_ISO/IMG_format#How_the_Hybrid_ISO.2FIMG_works)
[https://lists.ubuntu.com/archives/ubuntu-devel/2011-June/033495.html](https://lists.ubuntu.com/archives/ubuntu-devel/2011-June/033495.html)

If you want more technical details a quick google for 'hybrid iso' should give you all the information you need.

---

### Post by gnush on 2012-12-30
Indeed. If I'm not mistaken, this works with Windows images aswell due to the included bootloader.

If you want a GUI alternative, then Unetbootin is a good choice.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Cheesemill on 2012-12-30
> **gnush said:**
> Indeed. If I'm not mistaken, this works with Windows images aswell due to the included bootloader.
It doesn't work with Windows images as they aren't hybrid ISO's. To  create a bootable Windows USB you have to extract the files from the ISO  and then install a bootloader separately.
> If you want a GUI alternative, then Unetbootin is a good choice.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
Unetbootin uses the same method as the Startup Disc Creator, it doesn't make use of the hybrid ISO functionality.

---

### Post by gnush on 2012-12-30
> **Cheesemill said:**
> It doesn't work with Windows images as they aren't hybrid ISO's. To  create a bootable Windows USB you have to extract the files from the ISO  and then install a bootloader separately.

Oh, I thought using dd was the same as extracting the files. Now that I've read a bit about hybrid ISO's and dd, I can see that it's not the same at all.

Thanks for the correction.

---

### Post by The Cog on 2012-12-30
Thank you for those links. Just a few good starting points was what I needed. I am getting a much better feel for what's going on, and am now following links to read about GPT partition tables, unetbootin and the like. I think I'll know a lot more about the boot process by the time I've finished.

---

