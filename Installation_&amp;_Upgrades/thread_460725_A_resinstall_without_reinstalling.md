---
title: "A resinstall without reinstalling"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by pcostanza on 2007-05-31
I have a Vista system that was setup to dual boot Vista/Ubuntu.  Each OS on a separate hard drive.  I had to reinstall Vista and I don't want to reinstall Ubuntu but I can't figure out how to work with the boot file to get my menu to choose OS upon boot up.  As you can obviously tell, I'm a newbie.  I was using v7.04.
Is it possible to set the bootloader somehow to keep what I already have or do I have to actually go into a true reinstall?  If so, please let me know how and please remember, I'm a newbie.
Thanks

---

### Post by phidia on 2007-06-01
You should be able to use your ubuntu install cd to re-install grub. The menu item from the cd is "Recover a broken system" from there you need to carefully select the partition you installed ubuntu on, and then select "Re-install GRUB bootloader"

---

### Post by pcostanza on 2007-06-01
Thanks, I'll give that a try.

---

### Post by Rickyboy on 2007-06-01
I have the exact same problem. Two drives and all. reinstalled a fugged up XP and now I can't boot to ubuntu. I have edgy and fiesty cd's here but none of them have a "fix broken install" option.

My ubuntu system partition is 30 gigs and I REALLY don't want to reformat.
I just upgraded adgy to fiesty three days ago.

ANY help would be great.


I HATE MICROSOFT!!!!

---

### Post by pcostanza on 2007-06-01
I don't see that choice either. I tried Super Grub with no luck as well.  I miss my Ubuntu fix.

---

### Post by confused57 on 2007-06-01
> **pcostanza said:**
> I don't see that choice either. I tried Super Grub with no luck as well.  I miss my Ubuntu fix.
You might want to boot the live cd, open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

You might want to use the live cd to install grub to the Ubuntu drive's mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

e.g.:
find /boot/grub/stage1
root (hd1,x)
setup (hd1)
quit

Then boot first to your Ubuntu drive, if you get a grub boot menu, highlight the Ubuntu entry, press "e", then change root from (hd1,x) to (hd0,x), the press "b" to boot...this is temporary, but see if it works.

I'm assuming quite a bit here, but wanted to give you some additional instructions so we won't have to play forum tag, if I happened to guess right, not likely though.

---

### Post by pcostanza on 2007-06-01
Thanks very much. Your link was the jumpstart I needed.
Cheers

---

