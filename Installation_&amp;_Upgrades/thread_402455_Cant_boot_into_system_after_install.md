---
title: "Cant boot into system after install"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by cucamelsmd15 on 2007-04-05
Ive tried 6.06LTS and 6.10, and Im getting the same error. Kubuntu installation goes fine, nothing to report. I select the disk from the HD menu in my BIOS, and it gives me "Operating System Missing". Ive tried reinstalling 3 times to no avail. Help?

---

### Post by wpshooter on 2007-04-05
You say "I select the disk from the HD menu in my BIOS".  Why are you doing that ?

Do you have multiple hard drives ?  Are you sure that you did not install it on one of your other hard drives ?

---

### Post by cucamelsmd15 on 2007-04-05
> **wpshooter said:**
> You say "I select the disk from the HD menu in my BIOS".  Why are you doing that ?

Do you have multiple hard drives ?  Are you sure that you did not install it on one of your other hard drives ?

Im positive which one its on. I select from the BIOS menu (its set up for me to select by default) because I have 7 HD's:lolflag:

---

### Post by confused57 on 2007-04-05
> **cucamelsmd15 said:**
> Im positive which one its on. I select from the BIOS menu (its set up for me to select by default) because I have 7 HD's:lolflag:

You can try installing grub to the mbr of the drive which has Kubuntu installed, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
have your hard drive boot order the same as it was when you installed Kubuntu, before attempting to install grub to the mbr

An example of how this would work:
```
sudo grub
find /boot/grub/stage1
```
should return something like
```
root (hdx,y)
```
you would then enter:
```
root (hdx,y)
setup (hdx)
quit
```

Then try booting to your Kubuntu drive first, if  you get a grub menu, highlight your Kubuntu entry, press "e", change root from (hdx,y) to root (hd0,y), then press "b" to boot...this chane is temporary, if it works, but it can be made permanent in your /boot/grub/menu.lst.

---

