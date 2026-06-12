---
title: "Additional Drivers"
date: 2012-11-07
forum: Installation &amp; Upgrades
---

### Post by CardCaptor on 2012-11-07
[B][SIZE=3][COLOR=RoyalBlue]Hi i've upgrade[SIZE=3]d from [SIZE=3]the lts to the current version a[SIZE=3]nd it uninstalled the additional drivers.

[SIZE=3]I went to the software center and re intall them. 

[SIZE=3]The problem is that i can't find the icon now to open the additional drivers. 

I went to system configuration and it's not there. I use the unity [SIZE=3]search bar and type additional drivers and they dont pop up.

[SIZE=3]I don[SIZE=3]'t know what to do.[/SIZE][/SIZE]
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/COLOR][/SIZE][/B]

---

### Post by grahammechanical on 2012-11-07
So, you are on 12.10, are you? go to System Settings>Software Sources and there you will find an Additional Drivers tab. You should find a choice of drivers there.

Regards.

---

### Post by Mark Phelps on 2012-11-07
Just because Additional Drivers are available in one Ubuntu release doesn't mean they will also be available in other releases.

For example, Ubuntu 12.10 brings with it a new X-server, version 1.13 -- and AMD decided NOT to update their Linux driver (which would be available under Additional Drivers) for their hd 2x/3x/4x chipsets for this new X-server version.  So if you have one of these video chipsets, Additional Drivers will NOT offer you video drivers in Ubuntu 12.10.

---

### Post by CardCaptor on 2012-11-08
> **grahammechanical said:**
> So, you are on 12.10, are you? go to System Settings>Software Sources and there you will find an Additional Drivers tab. You should find a choice of drivers there.

Regards.

[COLOR="RoyalBlue"][SIZE="3"]**Thanks to you i finally find it, but there's nothing there to install.**[/SIZE][/COLOR]

---

### Post by CardCaptor on 2012-11-08
> **Mark Phelps said:**
> Just because Additional Drivers are available in one Ubuntu release doesn't mean they will also be available in other releases.

For example, Ubuntu 12.10 brings with it a new X-server, version 1.13 -- and AMD decided NOT to update their Linux driver (which would be available under Additional Drivers) for their hd 2x/3x/4x chipsets for this new X-server version.  So if you have one of these video chipsets, Additional Drivers will NOT offer you video drivers in Ubuntu 12.10.

[SIZE="3"][COLOR="RoyalBlue"]**Thanks i finally find the additional drivers section but there's nothing to install. It seems that Intel HD Graphics still isn´t in the new x-server :)**[/COLOR][/SIZE]

---

### Post by Mark Phelps on 2012-11-08
> **CardCaptor said:**
> [SIZE="3"][COLOR="RoyalBlue"]**Thanks i finally find the additional drivers section but there's nothing to install. It seems that Intel HD Graphics still isn´t in the new x-server :)**[/COLOR][/SIZE]
That's because Intel drivers are installed automatically during setup.  Only AMD and Nvidia video drivers are offered in Additional Drivers.

---

