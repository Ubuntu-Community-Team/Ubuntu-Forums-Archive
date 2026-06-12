---
title: "Will in Ndiswrapper be preinstalled with ubuntu 9.10?"
date: 2009-05-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mcds2 on 2009-05-12
Will as the title says ndiswrapper be preinstalled with the next release of ubuntu. if not could it be put in with the new os so that wireless drivers can be installed easier. please respond!

---

### Post by mcds2 on 2009-05-13
Please reply!

---

### Post by 73ckn797 on 2009-05-13
You can install a graphical tool via Synaptic to install wireless drivers. Look for "ndisgtk". It works great for my needs in 9.04. More info if requested.

---

### Post by taavikko on 2009-05-13
> **mcds2 said:**
> Please reply!

This is just speculation, but I highly doubt that it will be installed/included by default.

---

### Post by SKLP on 2009-05-13
Since ubuntu has a restricted drivers policy, one might argue that in certain cases, jockey should recommend and be able to install ndiswrapped-based drivers too. (for those cards where no other driver is available, or it is the most functional driver)

---

### Post by cariboo on 2009-05-14
I don't think we will ever see ndiswrapper installed by default, as more and more wireless adapters are detected with every release. Ndiswrapper and Ndisgtk are included on the LiveCD, I just checked the copy of Jaunty I received in the mail, it is still there. So you aren't stuck if you do need it.

---

### Post by Gina on 2009-05-14
**EDIT:-** I thought NDISWrapper wasn't included in the distro on CD and that's really what my rant below refers to.  Not too sure about it being installed by default - depends how big it is (must go and look) - but if it were installed it would make it much easier for new users coming from other operating systems and having an unsupported wireless adapter.
----------------------------------------------------------------------------------
Well I think it should!  I have a couple of friends who would LOVE to run Ubuntu but they only have wireless connection to the router and without an internet connection they can't download such things.  OK I know it's possible to download Ndiswrapper with another system and transfer it but that takes a fair amount of technical knowledge.  This is a real stumbling block and IMO needs looking into.

Admittedly, this is a fall-back method and we should have Linux drivers for all hardware but we all know here that hardware manufacturers refuse to co-operate and only want to support MS and Apple.

One friend has a top end system and recent hardware.  He has problems with wireless and also graphics and sound - those cards are also not supported OOTB.  Now if he had a way of using the Windows driver for wireless he could get connected and then install at least the graphics driver (nvidia).  I'm not sure what the soundcard problem is but if the other things could be sorted out the sound could follow (I'm in daily contact and could go through things with him).  He isn't prepared to buy a long cable and run it all over the house to get a wired connection.  His last comment on the subject was that he had so much trouble trying to get Ubuntu to work that he's staying with the dreaded MS offerings - W7 RC installed fine and everything worked OOTB.

---

### Post by xebian on 2009-05-14
```

/pool/main/n/ndiswrapper/ndiswrapper-common_1.54-2ubuntu1_all.deb
/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.54-2ubuntu1_amd64.deb


```

---

### Post by Kevbert on 2009-05-14
ndiswrapper (.deb) is normally supplied with the installation CD in the path stated by xebian. ndisgtk (.deb) can also be found on the CD in the /pool/main/n/ndisgtk directory. I believe you need to install ndiswrapper in order to install ndisgtk (but I may be wrong).

---

### Post by mcds2 on 2009-05-14
Would Ndiswrapper only show up for the live CD cause i used the wubi installer!  i'll try the live CD and report back !

---

### Post by mcds2 on 2009-05-14
is it safe to install ubuntu on the live CD without making any major changes to my PC.  Would using the live CD affect my windows xp bootloader?  i found it on the live CD and was able to browse the internet but is there anyway of getting that package in the wubi installer?

---

### Post by cariboo on 2009-05-15
Ndiswrapper may not be included in the alpha's, I recall someone swearing up and down that it wasn't on one of the Jaunty apha's.

---

