---
title: "Release name all messed up"
date: 2009-04-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sgtbug on 2009-04-20
Hi guys

A friend of mine told me to use mintmenu, which i did not like really.. So after i removed it.. this is what it shows in 'sudo lsb_release -a'

> Distributor ID:	LinuxMint
Description:	Linux Mint 7 Gloria - Main Edition
Release:	7
Codename:	Gloria


How can I get it back to the original Ubuntu branding?

---

### Post by lithorus on 2009-04-20
Delete or move the /etc/issue and /etc/issue.net and try re-installing the "base-files" package.

---

### Post by sgtbug on 2009-04-20
do i need to restart after that? bcz it did not work.. :(

---

### Post by sgtbug on 2009-04-20
this worked:

Open base-files package in archive manager.
extract the text based files in the etc folder of the archive, inside the data archive..
replace existing texts in etc directory..

but it now says, no lsb modules available..

```

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.04
Release:	9.04
Codename:	jaunty

```

btw.. thanks a lot for the idea lithorus.. my repo manager works alright now.. :D

---

