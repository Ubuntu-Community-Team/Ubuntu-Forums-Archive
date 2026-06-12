---
title: "How do you set the location of Grub in 10.10?"
date: 2011-03-03
forum: Installation &amp; Upgrades
---

### Post by Farstanley on 2011-03-03
I know there has to be an option to set the location of grub. It's been on various distros over the last decade and I've read articles that say it's available although horribly difficult to find but I really would like to pin this one down. In Maverick Meerkat 10.10 we can apparently only chose between putting it in the MBR and the Ubuntu boot partition but I can't work out how.
Has anyone anyone seen this elusive option ?
It's for an Ubuntu installation after Windows and I want to put Grub in the Ubuntu boot directory Not on the MBR because I am going to use a Windows based boot manager and it would avoid any boot loaders walking over each other to take over the MBR.
Thank you

---

### Post by Quackers on 2011-03-03
I think the option appears only when manual partitioning is chosen.

---

### Post by Farstanley on 2011-03-03
I only ever used manual partitioning and I haven't seen it yet

---

### Post by Quackers on 2011-03-03
From memory it's at the bottom of the screen.

---

### Post by psusi on 2011-03-03
Yep, drop down list at the bottom of the manual partitioning screen to choose which drive to install it on.  Installing to a partition is not an option.

---

### Post by Hakunka-Matata on 2011-03-03
> **Farstanley said:**
> I know there has to be an option to set the location of grub. It's been on various distros over the last decade and I've read articles that say it's available although horribly difficult to find but I really would like to pin this one down. In Maverick Meerkat 10.10 we can apparently only chose between putting it in the MBR and the Ubuntu boot partition but I can't work out how.
Has anyone anyone seen this elusive option ?
[COLOR="Red"]It's for an Ubuntu installation after Windows and I want to put Grub in the Ubuntu boot directory Not on the MBR because I am going to use a Windows based boot manager and it would avoid any boot loaders walking over each other to take over the MBR.[/COLOR]
Thank you

Do you even need Grub if you're going to use a "Windows based boot manager"?

---

### Post by Farstanley on 2011-03-04
Good point I would rather leave it out but 10.10 doesn't give that option

---

### Post by psusi on 2011-03-04
> **Farstanley said:**
> Good point I would rather leave it out but 10.10 doesn't give that option

Yea, I've got a bug filed about that.  You used to be able to not install it at all, but that option was lost in 10.10.

---

