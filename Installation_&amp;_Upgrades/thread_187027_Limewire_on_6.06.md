---
title: "Limewire on 6.06"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by Amar_ze on 2006-06-02
I am new with Ubuntu, also new on forum so please have that in mind.I am trying to install Limewire but on their site I find only .rpm.Any chances for Limewire on 6.06?Thanks in advance

---

### Post by Travisty on 2006-06-02
You can instal limewire from the .RPM. First you'll need to download a program called alien from the repositiries.

[COLOR="Red"]sudo apt-get install alien[/COLOR]

This will give you the program that will convert the RPM to a DEB

Download the RPM from Limewire.com. Browse to where you downloaded the file to and run: (The * is the name of the file) 

[COLOR="Red"]sudo alien *.rpm[/COLOR]

This should create a DEB that ou can install using [COLOR="Red"]sudo dpkg -i *.deb[/COLOR]

(Again the * is the name of the file)

Let me know how it goes

---

### Post by Amar_ze on 2006-06-02
All Okay now.Thanks :)

---

### Post by Travisty on 2006-06-02
Glad to help! That's what we are here for. :)

---

