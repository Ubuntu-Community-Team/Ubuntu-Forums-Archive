---
title: "should I upgrade from 8.10 to 9.10..  Radeon Xpress 200M vid card..."
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by switch10 on 2009-12-07
I have the ati radeon xpress 200m video card, and I have been worried about not having 3d graphics so I haven't upgraded past ubuntu 8.10.  I recently tried out the live cd of Karmic, and I have to say I really like it.  no probs with the graphics card at all.  Compiz actually works!!  this is great!!  I can also run dual head monitors very easily (not at the same time though, same as 8.10)!!  

What problems might I run into with this card?  Are all the compiz options usable with this card?  

Any suggestions before I upgrade?

---

### Post by zvacet on 2009-12-07
I have no experience with that graphic card,but if it work wit hlive CD it should work when you install.Remember that you can not skip versions when you upgrade so it should look like this Intrepid>Jaunty>Karmic.If you have separate home partition you can do fresh install of Karmic.If you want to make separate home follow [this]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") guide.

---

### Post by community nerd on 2009-12-07
9.10 sucks. Do 9.04

---

### Post by bnr on 2009-12-20
I wouldn't go so far as to say that 9.10 sucks, but it introduces a number
of major changes. So, for now a lot of stuff has been dropped including 3d 
support with the proprietary driver for this card (ATI Radeon Xpress 200M). 

I have been struggling with it myself, even building all the packages from 
the ATIs' "binary installer" at the terminal and nothing works. 

The problem seems to be that the most recent version of Xorg is incompatible 
with the Binary driver from ATI. As far as I know ATI has abandoned Linux
support of this card.

For 3D support you need to use the Open Source Driver (ati or radeon) and 
make sure that you have the mesa packages installed as well. 
Read this; [https://wiki.ubuntu.com/X/Troubleshooting/...]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-nvidia%20and%20reinstall%20-nv%20from%20scratch")

---

### Post by switch10 on 2009-12-20
> **bnr said:**
> I wouldn't go so far as to say that 9.10 sucks, but it introduces a number
of major changes. So, for now a lot of stuff has been dropped including 3d 
support with the proprietary driver for this card (ATI Radeon Xpress 200M). 

I have been struggling with it myself, even building all the packages from 
the ATIs' "binary installer" at the terminal and nothing works. 

The problem seems to be that the most recent version of Xorg is incompatible 
with the Binary driver from ATI. As far as I know ATI has abandoned Linux
support of this card.

For 3D support you need to use the Open Source Driver (ati or radeon) and 
make sure that you have the mesa packages installed as well. 
Read this; [https://wiki.ubuntu.com/X/Troubleshooting/...]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-nvidia%20and%20reinstall%20-nv%20from%20scratch")

Yeah I remember hearing that ATI had stopped supporting these cards.  The crazy thing is my card worked by default with the 9.10 live CD.  I remember working hard to get this card to work with 8.04 and 8.10.  I installed 9.10 shortly after I made this original post, and I couldn't be happier.  Everything works great.  

Thanks for the responses everyone. 

Dave

---

