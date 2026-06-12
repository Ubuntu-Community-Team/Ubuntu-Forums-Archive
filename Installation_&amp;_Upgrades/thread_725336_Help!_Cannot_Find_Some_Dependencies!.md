---
title: "Help! Cannot Find Some Dependencies!"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by HaXiT on 2008-03-15
Hello,
I want to make my own version of Ubuntu, and when I am using reconstructor, it says that I am missing: 
libbogl-dev 
libusplash-dev 
dpkg-dev 
fakeroot 

How do I get these?

Thanks 
HaXiT

---

### Post by mikewhatever on 2008-03-15
They should be in the repositories <sudo apt-get install packadge-name>. Good luck with your private Ubuntu.

---

### Post by HaXiT on 2008-03-15
> **mikewhatever said:**
> They should be in the repositories <sudo apt-get install packadge-name>. Good luck with your private Ubuntu.
Yeah, I already did that and it says that it cannot because of you need another package. THen when I try to isntall that it says you need another one !!!

---

### Post by HaXiT on 2008-03-15
> **HaXiT said:**
> Yeah, I already did that and it says that it cannot because of you need another package. THen when I try to isntall that it says you need another one !!!
```
Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libbogl-dev: Depends: libc6-dev but it is not going to be installed
```

Sorry for double post :(

---

### Post by zvacet on 2008-03-15
```
sudo apt-get install libc6-dev
```

---

### Post by HaXiT on 2008-03-15
Broken Package.

---

### Post by Pumalite on 2008-03-15
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

---

### Post by HaXiT on 2008-03-16
Still doesn't work....
If that is all I have to do, it still doesn't work.

---

### Post by Pumalite on 2008-03-16
Try this now:
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade

---

### Post by HaXiT on 2008-03-16
Sorry, but still didn't work :( 

Thanks for all the help so far :)

---

### Post by cjax1 on 2008-03-17
Not to hijack this thread but I just tried getting reconstructor to work tonight but couldn't. Found this thread by doing a search. Got dependencies installed except for libusplash-dev. Terminal says it can't find the package. The readme in reconstructor says reconstructor should work on 6.06. Yeah right. I read somewhere else it was designed for 7.10 or later. I might try it sometime after 8.04 is released but not before.

---

