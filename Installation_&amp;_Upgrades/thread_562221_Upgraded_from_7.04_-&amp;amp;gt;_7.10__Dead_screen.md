---
title: "Upgraded from 7.04 -&amp;amp;gt; 7.10 | Dead screen."
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by dmf86 on 2007-09-28
Hi there. I need some help from a more expert person than i am... I've installed 7.04 (which, sometimes, seems to configure the right way for my graphics card, but other times don't...) and upgraded it to 7.10. As soon as the upgrade is finished and the PC rebooted, i got a unreadable screen, full of "rain" and currupted graphics... Any solutions? My graphics card is ATI Radeon 9200.

Thanks.

---

### Post by forestpixie on 2007-09-28
i'd reconfigure xserver so you could at least get into the pc - then you can look for the reestricted driver thing in there - I believe that it's not in the same place - look in either preferences or admin - I think it's in Appearance now - can't remember quite where it all is in gutsy off hand
```

sudo dpkg-reconfigure xserver-xorg
```

answer questions best you can

---

### Post by dmf86 on 2007-09-28
Thanks for the quick reply. I've removed ubuntu since that problem made my PC unusable but i'll try in a few hours install it and using your solution. Thanks, in a few hours i'll report the situation.

---

### Post by wpshooter on 2007-09-28
I have one machine at home that is using an ATI Radeon 9200 card and it works better than any other Ubuntu video setup I have.

I will check when I get home and let you know how I have it setup.

---

### Post by dmf86 on 2007-09-28
Thanks, that will be awesome! :) 

An update: I'm ATM using the live CD (7.10 Beta) to write this. When it booted, i got the same graphic errors that i reported before. But, choosing "Start in safe graphics mode", it worked! If that helps with the solution... 1 more question, how i start Ubuntu in safe graphics mode after i install it? Thanks.

---

### Post by lisati on 2007-09-28
I too had a blank screen after upgrade to 7.10, starting on the older kernel allowed me to get in and tinker with the video settings - also with one of the ATI series of drivers. In my situation, there seemed to be less activity when letting grub default to the newer kernel. I'm beginning to suspect that the boot process is hanging somewhere with no errors showing- because(it doesn't mean that there aren't any I'm doing a bit of research just in case. I'll keep the team posted if I find something that could help in this discussion.

---

### Post by dmf86 on 2007-09-28
I don't get a "blank/black screen". I get the Ubuntu colors but all messed up... I've now installed the 7.04 but i'm afraid to upgrade to 7.10 and mess it up again...

---

### Post by dmf86 on 2007-09-29
Well, it seems that i "solved" the problem. I've updated from 7.04 to 7.10 using "update-manager -d", rebooted and reached the problem again. So i've rebooted again, pressed "ESC" in GRUB, started in Recovery mode, and used the "sudo dpkg-reconfigure xserver-xorg". I left all the default options except the driver, which i selected "VESA". After this, rebooted and started Ubuntu normally, and all seems fine, except that i don't have 3D rendering now... I'm looking for a way to get taht back. :) Thanks for the help and if you can help me a bit more with the driver issue... ;)

---

### Post by dmf86 on 2007-10-05
Ok, this problem seems impossible to solve. I can only work with the VESA driver. But that way i lose all the 3D rendering, dispite the fact that the rest is running fine. So i've tried again with ATI driver, RADEON driver and it kept the artifact screen and such. But this time, i've taken a SS, in which the desktop appears good! So that makes me wonder if the problem can be @ the monitor? Any thoughts? Thanks.

---

