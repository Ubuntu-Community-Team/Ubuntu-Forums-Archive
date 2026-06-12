---
title: "Power outage in the middle of upgrade"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by warhammerkid on 2008-05-06
My computer lost power in the middle of the upgrade to 8.04 from 7.10 (Kubuntu) and everything says I'm still on 7.10, but some of the packages have been upgraded. What is the proper way to get my system to 8.04 from this point?

---

### Post by Pumalite on 2008-05-06
Let's check your apt-get first. Do:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

---

### Post by warhammerkid on 2008-05-06
That worked perfectly. Thanks so much.

---

### Post by Pumalite on 2008-05-06
You are welcome. Good luck.

---

### Post by RJARRRPCGP on 2008-05-06
> **warhammerkid said:**
> My computer lost power in the middle of the upgrade to 8.04 from 7.10 (Kubuntu) and everything says I'm still on 7.10, but some of the packages have been upgraded. What is the proper way to get my system to 8.04 from this point?

Just reformat and reinstall.  Sorry. :( 

That sux.

(Declare a loss)

---

