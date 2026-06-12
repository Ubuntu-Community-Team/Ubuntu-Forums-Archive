---
title: "stuck at &quot;who are you&quot; page while installing 11.04"
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by vasukoh on 2011-09-12
Yesterday, I bought an assembled PC AMD 880 g chipset motherboard with AMD 1090 t Processor with logitech Keyboard and Mouse, i am trying to install UBUNTU 11.04 OS but the installation is getting stuck at last step "who are you", the forward tab is not turning grey and status bar showing "Ready when you are" 80-90% and stucks there. I tried several times and also un-check the "download files while installation option" but still no luck.

Please guide at the earliest, it really urgent.....:(:(

---

### Post by An Sanct on 2011-09-12
Have you answered the other questions, that where there before?

Do you have connection to internet and is the machine plugged in (you cannot install without power...)

---

### Post by blackbird34 on 2011-09-12
is the cd clean? i had that, turned out there was a big blob on the cd, when i cleaned it off, it was fine =D
have yoiu tried with a different live cd ? another 11.04, a 10.10, a fedora etc....
good luck

---

### Post by Quackers on 2011-09-12
Have you used a capital letter in the username? No capitals allowed there.

---

### Post by vasukoh on 2011-09-12
Yes i have answered all the other questions.....my internet connection is working fine.....(512 kbps)....and obviously the machine is plugged in....

I am installing from USB(Pendrive)....i created it with the help of Universal USB installer 1.8.6.3, unable to get pass the "who you are" step, forward does not turns to grey....what to do...?

I already know that Capitals are not allowed in the username....

Any other suggestions....please respond at the earliest....

---

### Post by Quackers on 2011-09-12
Have you used any odd characters in the username or a space? Have you entered and confirmed a password?

---

### Post by vasukoh on 2011-09-12
No i have not used any special characters or space in the username and i chose log in automatically option......but i do not think this has anything to do with this freezing problem.....Any other suggestion...please...?

---

### Post by Quackers on 2011-09-12
Have you checked the md5sum of the downloaded iso file?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that checks out you should check the cd/usb for errors.
At the first purple screen when booting from the usb press any key, then choose your language and on the next screen select the "check for errors" menu item.
See if any errors are found. One error is too many.

---

### Post by vasukoh on 2011-09-13
I have checked the MD5sum of the downloaded file but still no luck....no errors found in the USb as well....i also format USB and recreated it.....there is no option like "check for errors" on the screen next to choosing language.....i think u have never installed ubuntu 11.04...by urself ever.....please suggest me something else...

---

### Post by vasukoh on 2011-09-13
the iso image i am using is...."ubuntu-11.04-desktop-amd64.iso"....for your reference....please help...:(...:(

---

### Post by SavageWolf on 2011-09-13
Can we see a screenshot of the page thing?

---

### Post by Quackers on 2011-09-13
These are the instructions I gave you earlier but from the Ubuntu site

[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

If you don't get these screens it seeme there is a problem with your cd/usb.

---

### Post by vasukoh on 2011-09-13
these screens are not for ubuntu 11.04, these are rom older version....check this one this is for newer version....

[http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/](http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/)

Please check this one before sending any reply.....

I am stucking at the last screen......who are ....the forward tab in that is not allowing me to go further and it stucks on the same for a very long time....no option but to restart.....

---

### Post by vasukoh on 2011-09-13
Savage wolf: you can also give a look at [http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/](http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/)

the last screen shot is the one where i am stucking.....please help at the earliest.....

---

### Post by coffeecat on 2011-09-13
@vasukoh, I just noticed this in your first post.

> **vasukoh said:**
> the forward tab is not turning grey

It doesn't turn grey; it turns orange when it's ready to be clicked. Has the Forward button turned orange and, if so, have you tried clicking it?

By the way, Quackers gave you good advice to do a CD integrity check. It doesn't matter that the screenshot in his link is from an earlier version of Ubuntu. When you first boot up with the 11.04 live CD, a purple screen appears with two small icons at the bottom. Tap the space bar and a text menu appears similar to the one in that screenshot. You can select a disk integrity check from that menu.

---

