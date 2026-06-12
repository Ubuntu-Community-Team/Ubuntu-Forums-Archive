---
title: "installation hangs in between"
date: 2011-10-03
forum: Installation &amp; Upgrades
---

### Post by jamesbon on 2011-10-03
I am trying to install Ubuntu 11.04 and I have wasted more than 4 hours.
The installer window does not proceeds after showing a message on screen

Preparing to Install Ubuntu (with nice GUI of course)

and there is a circle which keeps on rotating (I have clicked Forward button)
but more than an hour and I am unable to do so.
I repeated this process  many many times with USB and with a CD.Can some one suggest what else can I try?

---

### Post by Rubi1200 on 2011-10-03
Hi,
please post the specifications for the computer, especially RAM and graphics card.

Also, are you connected to the Internet during installation?

What other operating systems are currently on the computer?

---

### Post by presence1960 on 2011-10-03
let's start with the obvious first. Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso? If your iso is no good the installer will not work. Also provide the info Rubi1200 asked for. There can be any number of reasons your installer is not working ranging from the iso to hardware.

---

### Post by jamesbon on 2011-10-05
Hi,
thanks for the replies.It was hanging due to a hardware failure.A Dell Inspiron 1440 laptop with 3.5 GB RAM and 320 GB hard disc.

1) Windows
2) Ubuntu 9.04 
3) Ubuntu 10.04 
on different partitions were installed.
Before this my grub was showing error.

grub error:> no file system found.
So I decided to re install grub.When sudo grub command failed from a live CD.I decided to format my laptop and this problem happened during that new installation.It took me almost more than 12 hours to format the laptop.But finally it worked.
I had to format entire 320 GB hard disc first with a Ubuntu 10.04 ISO and then I did a format with Ubuntu 11.04 ISO so that I can have one copy of Ubuntu on my laptop.
I erased entire disc and now there is only one Ubuntu 11.04 copy but to install this I had to spend more than 24 hours.
But now every thing is working.

---

### Post by Ashwin Surana on 2011-10-05
Hey jamesbon,
                
                 I would recommend you to format your hard disk with "Hiren's boot cd".. I also had the same problem before... Formatting with Hiren's boot cd is easy as well as good when you have multiple OS installed in your PC/LAPTOP .Hiren's boot cd is available free on net! :)

---

