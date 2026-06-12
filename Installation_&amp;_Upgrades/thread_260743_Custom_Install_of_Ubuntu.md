---
title: "Custom Install of Ubuntu"
date: 2006-09-19
forum: Installation &amp; Upgrades
---

### Post by niteblind on 2006-09-19
Hi,

I have been reading today about customising the install of ubtuntu. Most of it is going miles over my head so i though i would ask here.

I want to customise the installer so that the colours of the text and backgrounds are different. At present I do not want to do anything else so using a preseed file does not seem the way to go (i could be wrong tho). Is it possible to "tweak" the default install file if so what is it called cos i cannot find out.

cheers in advance
niteblind

---

### Post by Dinerty on 2006-09-19
[http://www.ubuntuforums.org/showthread.php?t=50054&highlight=spice+boot+text](http://www.ubuntuforums.org/showthread.php?t=50054&highlight=spice+boot+text)

This guide shows you how to change your default boot text colour, you can also 

[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

Shows you about USplash (Boot up image)

If you want to change your login screen (gdm) then

```
sudo gdmsetup
```

Get new ones from [http://www.gnome-look.org/index.php?xcontentmode=150](http://www.gnome-look.org/index.php?xcontentmode=150)

---

### Post by niteblind on 2006-09-19
thanks for the response but the link is to change the boot screens which is not what i asked. I want to change the install screens

---

### Post by zxee on 2006-09-19
There is a guide in the community docs here: [https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)
I'm not sure if it addresses the specific issue you're asking about-might be a start though.

---

### Post by niteblind on 2006-09-19
i was reading this article earlier the bit I cannot get my head around is what commands to use when preseeding is involved is there somewhere that lists all the possible questioon/answer combos and how to use them?

niteblind

---

### Post by niteblind on 2006-09-20
does anyone know how i find a list of the questions/variables that can be changed through a preseed file? I cannot seem to find a good howto for this as the artucle above kinda stops at that point.

cheers
niteblind

---

