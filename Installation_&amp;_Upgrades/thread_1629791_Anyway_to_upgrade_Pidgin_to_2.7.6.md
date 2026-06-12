---
title: "Anyway to upgrade Pidgin to 2.7.6?"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by ProgressiveAudio on 2010-11-24
I've been able to get it to 2.7.5, but that's all.

---

### Post by ProgressiveAudio on 2010-11-25
I guess that's a no.

---

### Post by howefield on 2010-11-25
The Pidgin PPA packages generally take a few days to catch up with the source releases, you will most likely get updated packages over the next few days.

The alternative is install from source.

---

### Post by opodaniel on 2010-11-25
Hope it will be soon, since the 2.7.6 version is ready from 21 nov, and the msn omega.contacts.msn.com problem is annoying. 
Meanwhile we can replace the omega.contacts.msn.com with a working one from here : [http://files.andreineculau.com/projects/pidgin/omega.contacts.msn.com.txt](http://files.andreineculau.com/projects/pidgin/omega.contacts.msn.com.txt).
The only problem is that the version 2.7.5 will change the certificate after a while and will have to repeat the procedure.

---

### Post by opodaniel on 2010-11-26
Got a way to install the latest 2.7.7 Pidgin. Here is the source of the info [yeeyan.org]("http://article.yeeyan.org/view/187683/153165")
> 1. &#19979;&#36733;&#24182;&#23433;&#35013;&#36825;&#20010; deb &#21253;&#65288;THIS.deb&#65289;&#65292;&#23427;&#20250;&#20026;&#20320;&#28155;&#21152; GetDeb &#24211;&#12290;
  
2. &#36816;&#34892;&#19979;&#38754;&#36825;&#26465;&#21629;&#20196;&#26469;&#26356;&#26032;&#20320;&#30340;&#36719;&#20214;&#28304;&#65306;
&#12288;&#12288;sudo apt-get update
  
3. &#21319;&#32423; Pidgin&#65306;
&#12288;&#12288;sudo apt-get upgrade
1- add getdeb.net repository  by installing this deb [http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1~getdeb1_all.deb](http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1~getdeb1_all.deb)
2- sudo apt-get update to check for new package
3- sudo apt-get upgrade to install latest updates

I got updates on several package beside pidgin : vlc, vuze,filezilla, gimp. 
I am newbie so don't know to much about the getdeb.net site, so proceed with care.

---

### Post by ProgressiveAudio on 2010-11-28
Thanks for the help guys.

---

