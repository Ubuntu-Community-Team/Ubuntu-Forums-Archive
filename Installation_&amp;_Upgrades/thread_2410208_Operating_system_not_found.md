---
title: "Operating system not found"
date: 2019-01-12
forum: Installation &amp; Upgrades
---

### Post by peachjy on 2019-01-12
Hi, I'm new user of ubuntu. I've installed ubuntu on my old laptop (Lenovo ThinkPad Edge E125) today, and I can still see "Operating system not found" message on black screen.

I used Windows 10 before(now I formatted my entire hard drive to ext4 to use ubuntu).

I installed Ubuntu 18.04.1 via USB.

On the first try, I failed to install because of the error:grub bootloader, so I read guide and fixed it.

Second try, I installed it successfully after reading guide on the blog by Korean user.

The option was : Something else(the last one, I installed it in Korean, so its name can be different)

I don't think this was not the problem, I successfully installed ubuntu on my desktop after reading this.

So, I erased everything and made some partitions(/, /boot, /home, swap) written in the guide.

And It performed installation successfully, but after the restart, I got error:Operating system not found.

I've also googled this, but I cannot get any solutions for me.

Is there anything you should know, please reply. I'll answer it immediately after the reading.

Thank you for reading, please help.

---

### Post by peachjy on 2019-01-12
Oh, I forgot to tell you:It is 64bit version

---

### Post by yancek on 2019-01-12
To install Ubuntu with the usb, you had to change to boot priority to boot the usb first.  Did you remove the  usb and set the hard drive to first boot priority.  If you have done that then we will need more information in order to help so with the Ubuntu usb, go to the site below and use the 2nd option on that page to download boot reepair using the ppa which is explained on that page.  Once you have downloaded it, run it per instructions on that page and make sure you do NOT try to make any repairs but select the Create BootInfo Summary option.  When it finishes it will give you a link which you can post here to get help.

---

### Post by peachjy on 2019-01-13
> **yancek said:**
> To install Ubuntu with the usb, you had to change to boot priority to boot the usb first.  Did you remove the  usb and set the hard drive to first boot priority.  If you have done that then we will need more information in order to help so with the Ubuntu usb, go to the site below and use the 2nd option on that page to download boot reepair using the ppa which is explained on that page.  Once you have downloaded it, run it per instructions on that page and make sure you do NOT try to make any repairs but select the Create BootInfo Summary option.  When it finishes it will give you a link which you can post here to get help.

Yup, I did change boot priority, and thank you, I'll try it as soon as I got home.

---

### Post by peachjy on 2019-01-13
Thank you so much, I finally fixed it!

---

