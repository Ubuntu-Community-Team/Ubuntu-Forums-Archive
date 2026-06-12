---
title: "vlc in jaunty"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jayanramesh on 2009-04-08
Dear Buddies,
How I can install vlc player in Jaunty 64 bit BETA

---

### Post by RedSingularity on 2009-04-08
Look in the Repositories.....the package manager??

---

### Post by jayanramesh on 2009-04-08
Dear shadow121,
There is none in the package manager

---

### Post by coffeecat on 2009-04-08
You need to enable the [medibuntu]("http://www.medibuntu.org/") repository.

[HowTo]("https://help.ubuntu.com/community/Medibuntu").

---

### Post by jayanramesh on 2009-04-08
Dear coffeecat,
I tried but all in vain.Were you able to install vlc in jaunty 64 bit?
Thank you.From synaptic I've got this
"vlc:
  Depends: libqtcore4 (>=4.5.0~+rc1) but 4.4.3-0ubuntu1.2 is to be installed
  Depends: libqtgui4 (>=4.5.0~+rc1) but 4.4.3-0ubuntu1.2 is to be installed
 Depends: libsdl-image1.2 (>=1.2.5) but it is not installable"

---

### Post by taavikko on 2009-04-08
> **coffeecat said:**
> You need to enable the [medibuntu]("http://www.medibuntu.org/") repository.

[HowTo]("https://help.ubuntu.com/community/Medibuntu").

Actually you don't need medibuntu to install VLC, since it's in "multiverse"

Just type "sudo apt-get install vlc" and problem solved.
If it states that there's no VLC, then check your repos.
if you installed without connection to internet, then repos might be commented out in sources.list.

---

### Post by Polygon on 2009-04-08
just make sure universe and multiverse is enabled ( i think it is by default) and just type 'sudo apt-get install vlc'

---

