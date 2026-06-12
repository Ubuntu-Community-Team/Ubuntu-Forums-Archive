---
title: "Ubuntu 12.10 installation problem, can't boot into Ubuntu"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by cikaRadule on 2012-10-22
Hi guys,

first I would like to say hello to all of you. 
I've been following this forum for quite some time while I was lurning to get to know Ubuntu that I've choosen as an OS in my new workplace. Thank you all for that...

But now I have a problem that I'm failing to find solution for on this forum.
I was very satisfied with Ubuntu at work so I decided to install it at my home laptop, but... I have dell with SSD inside and external HDD (that used to be inside) in a rack connected via usb 3.0 ports.
When I tried to install Ubuntu (ubuntu-12.10-desktop-amd64.iso download passed md5 check) I have failed, installation would not start while external HDD was connected. When I disconect it install went without any glitch... When installation started I connected external HDD back on, so that Ubuntu can be aware of it's existance.
And now when I choose Ubuntu in grub menu only black screen appears, CPU is working like crazy (I base that conclusion on ventilation fan that very soon starts to work in highest speed).
I can boot into Windows 7 without any problems.
Have tried to install Ubuntu 12.04, but result is the same...

Can somebody give me any suggestion please...? I would love to have Ubuntu as my primary OS, but if I would have to disconect HDD when booting and connect it back on when Ubuntu is up and running, guess I will have to get back on Windows :/

---

### Post by mag1strate on 2012-10-22
Try installing the OS without connecting the external at all and make sure the boot options in your bios is saying that you are booting from the SSD (which is where I assume you are installing the OS). I have an external HDD connected at all times with my desktop with no trouble, but you have a USB 3.0.

---

### Post by mag1strate on 2012-10-22
Also, have you tried installing with the HDD on a USB 2.0 slot?

---

### Post by cikaRadule on 2012-10-22
Hi, thanks for your suggestions.

Only way I'm able to install Ubuntu was when external HDD is disconnected, and than everything works fine. Even when I connect HDD when Ubuntu is up and running everything is fine.
SSD is set as primary boot option in BIOS by default.

But, now when I move HDD to usb 2.0 everything works fine! :)
Thanks for that idea...

How much do I lose at performance if I keep external HDD connected on 2.0 insted of 3.0?

---

### Post by cikaRadule on 2012-10-22
Ok, to answer that part about performance :
USB 3.0 - read / write / access : 111MBs / 84MBs / 8msec
USB 2.0 - read / write / access : 26MBs / 23MBs / 8msec

It would be very helpful if somebody have any idea / suggestion where I could continue with search for solution.
I will try on my own to find out an answer, and if I do - will post it here...

---

