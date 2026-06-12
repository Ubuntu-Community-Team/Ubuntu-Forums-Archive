---
title: "Unetbootin or anything else not working?"
date: 2016-06-03
forum: Installation &amp; Upgrades
---

### Post by D3E on 2016-06-03
so i installed ubuntu 16.04 lts on my windows 8 machine and it wont load. I do the advanced restart and come to choosing windows 8 or unetbootin, when i choose unetbootin the pc goes quiet, no cpu light or image to my monitor. After 30 seconds the pc does a shutdown and when i turn it back on it prompts me to the OS selection screen again. I have also tried installing ubuntu via a CD and a usb drive. Both of them have not worked. It`s like my pc doesn`t want to change anything :(. I think it might be a problem with my bios however when i tap my F2 or delete buttons the pc ignores it and still goes to my windows 8 login screen.


Any help on what i should do or find out?

(yes its a 64 bit machine and i ran a 64 bit iso file)

---

### Post by yancek on 2016-06-03
Windows 8 and newer use UEFI to boot.  Did you boot and try to install Ubuntu UEFI?  The Ubuntu documentation below explains how and what is required.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you are seeing 'unetbootin' on boot then what you have done is a 'frugal' install.  That means putting the Live CD of Ubuntu on a partition on a hard drive rather than putting it on a flash drive as it is usually used.  Not sure how that would work with UEFI.  If you used unetbootin to put Ubuntu on a flash drive you should post some specifics on what "have not worked' means as that is no use to anyone trying to help.  Unetbootin has been around for years and is very stable and almost always works.  Did you verify the integrity of your download of the Ubuntu iso?

---

