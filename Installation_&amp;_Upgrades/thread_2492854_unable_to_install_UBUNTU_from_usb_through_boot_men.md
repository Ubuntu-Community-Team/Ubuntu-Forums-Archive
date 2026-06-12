---
title: "unable to install UBUNTU from usb through boot menu"
date: 2023-11-25
forum: Installation &amp; Upgrades
---

### Post by blurblur on 2023-11-25
Hi,
I have a Dell Latitude 5440 that has windows and I want to turn into a UBUNTU
First I tried using an existing USB I had used before to install UBUNTU with no luck
I thought maybe the USB was corrupt so I downloaded the UBUNTU installation and created a new USB with RUFUS (seemed to work - it was renamed UBUNTU and when I look inside the USB it has the boot, grub etc folders)
I press F12 to get to the boot menu but can't see the USB
I tried indicating it through BIOS (from F2) using efi with no luck
Maybe this is a GRUB issue?

Can anyone point me in the right direction?

---

### Post by Rubi1200 on 2023-11-25
Hi and welcome to the forums :-)

Which version of Ubuntu did you download?

Did you write with Rufus using ISO mode or dd mode?

What make of USB and what size?

---

### Post by yancek on 2023-11-25
More clarification will be needed before you can get help.  What does 'existing usb' mean?  Is that a usb with some older version of Ubuntu on it which you previously used successfully for an install?  Was that install on the same computer?  What does 'no luck' mean.  You need to be a lot more specific about that.  You indicate you thought the usb might be corrupt.  Does that mean the contents or are you using a new/different usb?  Do you have a separate computer to test the usb to see if it boots?  If it does not, then it is likely the usb itself is bad.

---

### Post by ian-weisser on 2023-11-25
On some hardware, not all USB ports are bootable. Try every port.
And try to boot it in a friend's system.

---

