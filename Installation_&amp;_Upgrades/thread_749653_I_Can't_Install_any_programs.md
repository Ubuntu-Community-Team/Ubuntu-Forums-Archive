---
title: "I Can't Install any programs"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by tishoyy on 2008-04-08
hi all, I'm new Linux user and I have many problems. I've tried to install few programs like xmms1.2 and skype but i can't. when i start with ./configure it shows me this 

configure: error: C compiler cannot create executables

I even can't install any libraries when i write down ./configure for the libraries it shows me this error

configure: error: can not guess host type; you must specify one

What is this? Where am I wrong? PLEASE HELP ME !!!

THANKS in advance !!!!!

---

### Post by nealmohanp on 2008-04-08
For most apps just open the terminal and type

sudo apt-get install **application name**

nOTE: replace application name with the application such as skype

Or try Automatix. Just google it.

---

### Post by Peter09 on 2008-04-08
Or go to System->Administration->Synaptic

There are 1000's of apps in there, just tick the box and they will automagically install. 

Make sure you have your repositories enabled first though.

PC

---

### Post by Pumalite on 2008-04-08
Don't use Automatix:
[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)
[http://ubuntuforums.org/announcement.php?f=13/](http://ubuntuforums.org/announcement.php?f=13/)
[http://ubuntuforums.org/showthread.php?t=519872](http://ubuntuforums.org/showthread.php?t=519872)
[http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

Install build-essential
sudo aptitude install build-essential
(just in case)

---

### Post by tishoyy on 2008-04-08
Peter09 I've heard about Synaptic but I don't have it in my package

---

### Post by Peter09 on 2008-04-08
What package have you?

PC

---

### Post by nealmohanp on 2008-04-08
yikes didnt know that.

---

### Post by ibutho on 2008-04-08
For the "configure: error: C compiler cannot create executables", you need to install build-essential using the apt-get, aptitude or synaptic (add/remove programs). This is a metapackage that will install other packages that are necessary for development and to compile packages from source. I do agree with others, that its probably easier to install prebuilt packages from the Ubuntu repositories using the packaging tools I mentioned earlier.

---

### Post by Pumalite on 2008-04-08
Keep this in mind too:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by tishoyy on 2008-04-08
the version is 7.10 in one CD

---

### Post by Pumalite on 2008-04-08
If you have it installed:
System>Administration>Synaptic Package Manager

---

### Post by tishoyy on 2008-04-08
also I've tried with "sudo apt-get install build-essential " but there is another error 

/var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)

---

### Post by Peter09 on 2008-04-08
The error is due to having another instance of the package manager open (probably).
If you are running Ubuntu with Gnome then I am sure that you will have Synaptic in the menu. Check again that you are looking in the right place.

PC

---

### Post by tishoyy on 2008-04-08
no sorry I'm with Kubuntu 7.10 with KDE and I found somethin called Adept installer and I think it is like Synaptic. is it?

---

### Post by Peter09 on 2008-04-08
Yes, thats ok.

In KDE the package manager is in the menu system somewhere, but not running that package I cannot advise. You need to look through the administration menu's.

PC

---

### Post by Pumalite on 2008-04-08
This might help:
[http://www.bellevuelinux.org/kdesu.html](http://www.bellevuelinux.org/kdesu.html)

---

