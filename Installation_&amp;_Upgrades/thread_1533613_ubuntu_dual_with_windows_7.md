---
title: "ubuntu dual with windows 7 ?"
date: 2010-07-18
forum: Installation &amp; Upgrades
---

### Post by AM_SOS on 2010-07-18
hello there,
some time ago i had tried to install 9.10 as dual boot with windows 7. the whole thing got messed up and i just couldn't get the boot menu that appears at the beginning to list both the operating systems side by side.
i wonder if someone can shed more light on installing ubuntu with windows 7.
also i heard something about laptop makers like toshiba and asus not providing any kind of support for ubuntu. does this mean that if i buy a new laptop such as the toshiba T 235, i will have difficulty in installing ubuntu as dual boot with windows 7 ?
thanks!

---

### Post by Bluesan on 2010-07-18
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu)

---

### Post by AM_SOS on 2010-07-19
thanks for the link.
but one of my friends mentioned facing some problems while trying to install ubuntu as dual boot with windows 7. it seems that 7 uses some kind of separate 1 GB partition as a boot loader.
while installing ubuntu after having made a clean install of 7, it seems the grub mechanism was messed up, and the system would not boot into 7.
it would appear that all this is happening because of some fresh changes in the way the 7 installation works, as compared to XP.
i would appreciate others coming in on this and sharing their experiences of installing ubuntu 10.04 as dual boot with windows 7.
thanks!

---

### Post by Bluesan on 2010-07-19
I currently dual boot Win 7 and Lucid, and I used the instructions documented in the link I provided. It worked fine. And yes, as explained in the documentation, Win 7 is handled differently than XP.

---

### Post by oldfred on 2010-07-19
Some more links. The differences in screens between Kamic and Lucid are minor.

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu)
Alternate install example win 10.04:
[http://members.iinet.net.au/~herman546/p2.html](http://members.iinet.net.au/~herman546/p2.html)

Older but similar:
Dual Boot win/Ubuntu
[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

---

### Post by Nick_Jinn on 2010-07-19
You may have to go into the bios and change the boot/load order BEFORE you can even boot from CD.

However, I have dual booted the two and it works great.

---

### Post by gansvv on 2010-07-19
Not a problem. Both Win7 and the Lynx are comfortable living on the same machine. :)
That said, it is easier if you install Windows first and then Lynx, so that Grub or Lilo can take over and help manage the boot order.



> **AM_SOS said:**
> thanks for the link.
but one of my friends mentioned facing some problems while trying to install ubuntu as dual boot with windows 7. it seems that 7 uses some kind of separate 1 GB partition as a boot loader.
while installing ubuntu after having made a clean install of 7, it seems the grub mechanism was messed up, and the system would not boot into 7.
it would appear that all this is happening because of some fresh changes in the way the 7 installation works, as compared to XP.
i would appreciate others coming in on this and sharing their experiences of installing ubuntu 10.04 as dual boot with windows 7.
thanks!

---

### Post by andrew.46 on 2010-07-23
Hi AM_SOS,

Things may be a little less complicated if you run win 7 as a virtual machine. I attach a screenshot of my own setup using virtualbox_ose...

Andrew

---

