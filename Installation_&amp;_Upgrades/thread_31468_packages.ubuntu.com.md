---
title: "packages.ubuntu.com"
date: 2005-05-03
forum: Installation &amp; Upgrades
---

### Post by sprucio on 2005-05-03
I noticed that the default site where Ubuntu downloads is NOT from packages.ubuntu.com.

It seems like that site resembles Debian's packages more than Ubuntu. So where does this site come from if it's not the main repository by Ubuntu? Does Ubuntu developers work on this site?

---

### Post by az on 2005-05-03
As debian's package site, there is a daemon which updates frequently it's package list from the archives and builds the packages' pages.

---

### Post by sprucio on 2005-05-03
My question was really to ask if the default Ubuntu repository is different than pacakages.ubuntu.com.

---

### Post by sprucio on 2005-05-05
Is anybody using packages.ubuntu.com?

---

### Post by nad on 2005-05-05
The actual location of the packages is archive.ubuntu.com .

---

### Post by sprucio on 2005-05-05
Oops my mistake.

So it would appear that packages.ubuntu.com and archive.ubuntu.com are associated.

When I search for the package "ttf-xfree86-nonfree," I don't get anything if I use apt-cache search but using that Web search feature, I see the package.

Do I need to edit something in /etc/apt/sources.list?

---

### Post by nad on 2005-05-05
Yes. You need to edit your sources list to include that package location. Universe, non-free I'm not certain. The package location is noted in your search.

---

### Post by sprucio on 2005-05-05
Can you tell me where I can read more about how ubuntu structures their /etc/apt/sources.list file?

I had to add some entries in Debian as well but I would like to know the full options for Ubuntu.

---

### Post by sprucio on 2005-05-05
Anyone?

---

### Post by nad on 2005-05-05
man sources.list

---

### Post by sprucio on 2005-05-05
Got it.

---

