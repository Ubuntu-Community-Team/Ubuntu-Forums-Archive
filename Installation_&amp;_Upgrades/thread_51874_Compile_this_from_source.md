---
title: "Compile this from source"
date: 2005-07-25
forum: Installation &amp; Upgrades
---

### Post by tanix on 2005-07-25
Can anyone walk me through on how to compile something from source? There is a prog out there that can convert .abr(photoshop) brushes to .gbr(GIMP) brushes. Here is the [[LINK]](http://the.sunnyspot.org/gimp/tools.html) I'm sure it will work for ubuntu I am just a nOOb so, if someone could help me out....

---

### Post by Natja on 2005-07-25
1/ Download the source code
2/ untar it where you want
3/ ./configure
4/ make
5/ sudo make install

;)

---

### Post by damonw5 on 2005-07-25
[QUOTE=Natja]1/ Download the source code
2/ untar it where you want
3/ ./configure
4/ make
5/ sudo make install

;)[/QUOTE]
 It can be easy, but it can get devilishly complicated if you're new to Linux. If there is any possible way to install that program (or a similar one) in Synaptic with the Universe repositories installed (see [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) ), see if you can do that instead -- it's a lot easier for a n00b! :)

---

### Post by Natja on 2005-07-25
Exactly. Try to find a .deb file, or a .rpm one, that you can convert into .deb with alien (alien package_name.rpm)

To instal a .deb :
sudo dkpg -i package_name.deb

And if you don't find any .deb or .rpm, try to build from source. You need build-essential to do that :
sudo apt-get install build-essential

---

### Post by BitTorrentBuddha on 2006-02-02
how do I install an .rpm?

I'm installing Mindless Automaton, an Apprentice clone for playing MTG, and it's latest [sourceforge release](http://sourceforge.net/project/showfiles.php?group_id=15892&package_id=12756) has the choice of downloading a *.tar.gz or a *.rpm, from what you said, I'm assuming the .rpm will lead to a better time, especially considering the .tar.gz doesn't have a configure script after I uncompressed it...

---

### Post by Gcool on 2006-02-02
You can install the rpm by typing this in console

rpm -i thefilename.rpm

---

### Post by BitTorrentBuddha on 2006-02-02
bash: rpm: command not found

---

### Post by Jason_25 on 2006-02-02
sudo apt-get install rpm && alien

---

### Post by BitTorrentBuddha on 2006-02-02
thanks much :)

---

### Post by towsonu2003 on 2006-02-02
[QUOTE=Natja]1/ Download the source code
2/ untar it where you want
3/ ./configure
4/ make
5/ sudo make install
[/QUOTE]
using checkinstall might be better as it makes uninstallation easier (for example, when you need to update)
sudo apt-get install checkinstall
above commands
change #5 to sudo make checkinstall

---

