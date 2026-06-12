---
title: "gDesklets Instilation"
date: 2006-10-19
forum: Installation &amp; Upgrades
---

### Post by Tobywuk on 2006-10-19
hey

Im just wondering, is this the application/mod that puts the MAC OSX like link box on the desktop?

I downloaded this from [http://www.gdesklets.org/](http://www.gdesklets.org/)  and it came in a .tar.bz2  folder. i extracted this and there are lots of other folders and files. Im just wondering how to install this? or maby i have the incorrect package/version for ubuntu?

---

### Post by orb9220 on 2006-10-19
Did you install gdesklets and gdesklets-data from synaptic first before you can add widgets to run gdesklet app needs to be installed.

---

### Post by Tobywuk on 2006-10-19
i didn't do anything, just downloaded that file from the website.

Can you give me an easy simple step by step guide to doing it? 

thanks :)

---

### Post by taurus on 2006-10-19
First, make sure you enable both universe & multiverse in /etc/apt/sources.list by removing the # sign in front of the lines that have universe & multiverse in them (Applications -> Accessories -> Terminal)...

```

gksudo gedit /etc/apt/sources.list

```
Save it and from the same terminal, run

```

sudo aptitude update
sudo aptitude install gdesklets gdesklets-data

```

---

