---
title: "Install Disk shows black screen after selecting grub option"
date: 2013-06-23
forum: Installation &amp; Upgrades
---

### Post by mtotho on 2013-06-23
edit: SOLVED

Set "Secure Boot" to "Disabled" in bios. fixes issue.

So I am finally posting here after 2 days of searching and troubleshooting.


I just got my Asus Transformer Book TX300 and am trying to set up dual boot with the latest ubuntu or any other linux distro such as mint 15 cinnamon 64 with windows 8.
Specs:
Intel® Core&#8482; i7 3517U Processor (1.9ghz)
Integrated Intel® HD Graphics 4000
Mobile Intel UM77 Express


So I put the image on a USB boot disk, I can boot to it and I get the grub menu: "Try before installing", "Install Now" , etc. No matter which option I select, the menu is immediately followed by a black screen where nothing happens regardless how long I wait. To be sure I tried the USB in my laptop that has had linux on it for the past 8 months - It booted to the usb and I saw animation instantly after selecting an option. In order to rule out the USB I even burnt it to a disk and I saw the exact same issues.

I also tried linux mint installer, and I got the exact same issue. here are some of the grub flags I tried:

-remove quiet splash and replaced with "nomodeset"
-remove quiet splash and replaced with "i915.modeset=0"
-remove quiet splash and replaced with "i915.modeset=1"
-remove quiet splash and replaced with same as above and "driver=intel"
-remove quiet splash and replaced with all the combinations of above and "text -verbose"


Absolutely the same exact thing happened with all of them - no indication that the anything is happening, just black screen (when i tried with the dvd, I could hear the disk rev up briefly, then stop)


There are no options in the bios that seem interesting.


Anyone have any suggestions? I suspect its something to do with my chipset/graphics. Unfortunately my laptop is too new and I haven't found much on it specifically related to linux except this [http://www.linlap.com/asus_transformer_book_tx300](http://www.linlap.com/asus_transformer_book_tx300) which says nothing of installation issues.

---

### Post by mtotho on 2013-06-23
I finally solved the issue. Silly ME.

I set the "Secure Boot" Option in bios to "Disabled" and that fixed the issue.

---

