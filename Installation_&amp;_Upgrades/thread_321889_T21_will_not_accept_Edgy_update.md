---
title: "T21 will not accept Edgy update"
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by catalina on 2006-12-19
I have exhausted all the threads and need some help.  I have 6.03 installed and am trying to update to 6.10.  Have tried all the update options listed (gksu..., cdrom/cdromupgrade) and am not able to perform update/install on my laptop (ibm t21, 256 megs ram, plenty of hd).

When I insert the cdrom it loads the gui with all the options and from there i get a blank screen whatever option i try.  I also have compaq e500 and installed 6.10 without a problem using the same cd, so I know it isn't the image.

Any suggestions would be welcomed!

Dean Anderson
Sault Ste. Marie, Canada.

---

### Post by po0f on 2006-12-19
catalina,

Is there anything stopping you from a fresh install instead of the update?  Edgy installed fine on my T22.  (The only reason I suggest this is because I find that fresh installs are a smoother process than an upgrade.)

---

### Post by catalina on 2006-12-19
I have tried to do a complete reinstall but as soon as I get past the gui the screen blanks out and i cannot install, udate, get edgy on at all!  I cannot even run the live cd, but I can on my other laptop.  I have tried all of the forum update suggestions and have had no success.  I have installed ubuntu on other systems and this has me puzzled.

I have installed the gnome interface (i was using kde) and am wondering if the install of gnome has anything to do with my inability to upgrade/install.

---

### Post by catalina on 2006-12-20
I solved my problem.  I was browsing throught the posts and found that I needed to install the i386 installation of Edgy.  I had thought it was my bios so I upgraded it (ibm.com, which is probably a good idea to do anyway if you are wanting to upgrade to the maximum in ram) then I downloaded the i386 version, installed it and am off to the races!

There is hope for all the ibm t-series users.  Hopefully they will put a sticky somewhere to save yourself some time and frustration.  Hopefully this helps!

Dean.

---

### Post by po0f on 2006-12-20
catalina,

You were trying to install what version of Ubuntu initially? x86_64?  :)

---

### Post by catalina on 2006-12-21
Hi Po0f,

Originally I was trying the default, supposedly dummy proof install for those not knowing which installation to choose.  It was just the one that I navigated to through the ubuntu download menu.

I was browsing all the posts and found quite a number of ibm t series users having this same frustration so i thought I would try to salvage some users.  When I tried to use the generic distro download it would give the appearance that I didn't have enough ram showing an eeprom error.

I also found out that you need to install a 386 package in synaptics in order to get certain pcmcia cards going (dlink dwl-650+).  I am a little concerned because it has been difficult to get edgy going on this machine (i have 5 of them for our corporate customers at our motel).  Breezy and dapper would work out of the box but edgy...make me a little edgy!!

Dean.

---

