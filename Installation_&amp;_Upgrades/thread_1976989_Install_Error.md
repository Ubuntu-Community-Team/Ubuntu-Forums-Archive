---
title: "Install Error"
date: 2012-05-09
forum: Installation &amp; Upgrades
---

### Post by Sean Hall on 2012-05-09
When I have finished the install, this error comes up:
[IMG]http://screensnapr.com/e/OOquCi.jpg[/IMG]
And when I try to boot it, an error comes up.

I am limited as I do not know much about Ubuntu. Any help would be appreciated.

Thank you,
Sean.

---

### Post by darkod on 2012-05-09
First of all, that is a wubi install inside windows.

It's always recommended to install proper dual boot of ubuntu and windows, on separate partitions. Wubi works sort of as virtual machine inside windows.

I don't work with wubi, and don't know about that error.

What you could try is running the wubi.exe with right-click, Run As Administrator so it can run it with maximum permissions. Sometimes it needs that in vista/7.

---

### Post by Sean Hall on 2012-05-09
It is running in Admin mode, as well as I can not run the disc on start up.

---

### Post by jadtech on 2012-05-09
also if you are trying to do a wubi install  just reboot  and  the install should finish and boot, I  used the wubi installer twice with win7 both times  when it was complete rather then a reboot message I got an error I just  rebooted and all went  good ..

---

### Post by Sean Hall on 2012-05-09
When It reboots, nothing happens. It just login's in like it ussaly would do.

---

### Post by darkod on 2012-05-09
> **Sean Hall said:**
> It is running in Admin mode, as well as I can not run the disc on start up.

I don't get it. Are you installing wubi just because you can't boot with the cd to do the proper install?

In that case you better see what's the problem with booting with the cd, and not install wubi which works in a different way.

Did you set cd-rom before hdd in BIOS boot order?
Are you sure the cd is burned correctly from the image, not the image file as a file on the cd?
Did you burn it on low speed to make sure there are no errors, like 8x or 10x?
Did you try downloading new image in case that one got corrupted during download?

---

### Post by Sean Hall on 2012-05-09
If the download was corrupted it Win rar would not allow it to be opened, I can not boot up the CD from start up even when I try at the boot menu. I have two copys one on USB other on Disc, both Fail.

---

### Post by darkod on 2012-05-09
If they were created from the same image that sounds like bad image.

I can't see why you mention winrar, did you use it to confirm it would open the ISO? Or you extracted the ISO onto the usb?

It needs a boot sector to boot. You can't create it by simply extracting the files.

---

### Post by Sean Hall on 2012-05-09
> **darkod said:**
> If they were created from the same image that sounds like bad image.

I can't see why you mention winrar, did you use it to confirm it would open the ISO? Or you extracted the ISO onto the usb?

It needs a boot sector to boot. You can't create it by simply extracting the files.

I've just burned it using a ISO burner. Thanks for the advise and I hope it will work.

---

### Post by Sean Hall on 2012-05-09
It's working now, Thanks for your help. It is much appreciated.

---

