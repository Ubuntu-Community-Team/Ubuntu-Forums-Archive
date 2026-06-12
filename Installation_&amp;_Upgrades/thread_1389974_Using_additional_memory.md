---
title: "Using additional memory"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by Jasperthecat on 2010-01-25
I have an ACER laptop 2GB memory running 9.10

I can upgrade the memory to 4GB

Please point me in the direction of what I need to do to my Ubuntu to utilise this additional memory 

Thanks 

=^..^=

---

### Post by earthpigg on 2010-01-25
if you have 64bit ubuntu installed, you will need to do nothing aside from putting the RAM in properly and turning your computer back on.

---

### Post by Jasperthecat on 2010-01-25
Thanks 

It's a 32 bit version 

=^..^=

---

### Post by presence1960 on 2010-01-25
> **Jasperthecat said:**
> Thanks 

It's a 32 bit version 

=^..^=

Then only 3.2 to 3.5 GB will be recognized. That is not an Ubuntu thing, it is a 32 bit OS thing. The same applies to windows 32 bit. 32 bit does not have the ability to recognize 4 GB of RAM.

---

### Post by earthpigg on 2010-01-25
> **presence1960 said:**
> Then only 3.2 to 3.5 GB will be recognized. That is not an Ubuntu thing, it is a 32 bit OS thing. The same applies to windows 32 bit. 32 bit does not have the ability to recognize 4 GB of RAM.

you ***could*** install the 32bit server kernel, but that ***may*** bring you additional issues to deal with.

the ideal long term solution would be to install 64bit ubuntu. this will require a fresh install.

you can put the additional ram in right now, and 'survive' with only being able to use ~3gb until you get time to do a fresh install. it won't hurt anything.

---

### Post by darkod on 2010-01-25
Also take into account that if you have onboard video which is quite standard for laptops today, part of the ram is first allocated to the video card. If you set this amount to be 256MB for example, that leaves 3.75GB out of the 4GB.
A 32bit OS can usually address 3.5GB approx, so you're not losing that much. Maybe it would be better to wait for the 10.04 LTS in April and then do a clean install of 64bit 10.04 which is always better than distro upgrade. Just an idea.

PS. By 'onboard video' I actually meant shared video memory. Of course the video is onboard in laptop (with exceptions).

---

### Post by raymondh on 2010-01-25
Earthpigg hinted that you could use the PAE enabled kernel but that "may" bring you more issues.  Nevertheless, if you want to read further ....

[http://ubuntuforums.org/showthread.php?t=855511](http://ubuntuforums.org/showthread.php?t=855511)

Good luck.  Make sure you have a working/tested back-up of your files.

Raymond

---

### Post by Jasperthecat on 2010-01-25
Thanks for the info

I'll stay with the 32 bit option for the moment

I put in the extra 2GB and booted the current image but got a message that the video system had reverted to low resolution - it gave me some options to fix the problem but this didn't work 

What should I try next? - apart from rebuilding from CD!

=^..^=

---

### Post by earthpigg on 2010-01-26
> **Jasperthecat said:**
> Thanks for the info

I'll stay with the 32 bit option for the moment

I put in the extra 2GB and booted the current image but got a message that the video system had reverted to low resolution - it gave me some options to fix the problem but this didn't work 

What should I try next? - apart from rebuilding from CD!

=^..^=

can you give us more exact details on the message, please?

and, to rule out faulty ram... take the existing 2gb ram stick out, leaving only the new one. a 2gb stick is a 2gb stick (assuming they are both the same type... ddr2, 240 pin, 800mhz, etc). if one works fine, and the other causes errors, it is very likely that it's that ***particular*** stick that is faulty.

---

### Post by Jasperthecat on 2010-01-26
earthpigg

Thanks for ideas

New 2GB memory works fine with 9.1 

Also ran memtest - no problems

With 4GB onboard (this time sticks were swapped around) I got this message 

Ubuntu is running in low graphics mode.  You may need to update your configuration to solve this 

(EE) NV(0)  No Valid FB address in PCI config space

(EE) Screens found but none have usable configurations


It then offered me some options to repair / modify the screen configs but I couldn't get any improvement


BTW Another message on the text mode boot up screen before the above was shown 

usplash: Setting mode 1152 x 864 - fail

usplash: using 1024 x 768

Hope this helps (us both)


=^..^=




 

(EE) NV(0) No valid

---

