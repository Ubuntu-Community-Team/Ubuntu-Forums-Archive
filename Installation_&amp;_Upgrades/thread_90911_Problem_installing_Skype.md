---
title: "Problem installing Skype"
date: 2005-11-16
forum: Installation &amp; Upgrades
---

### Post by skonvolt on 2005-11-16
I use ubuntu 5.10
I download the skype .deb but when I install it, require the libqt3c102-mt .deb 
So, i try to install libqt3c102-mt .deb but the dpkg say "impossible" because is in conflict with libqt3-mt...
On Synaptic, libqt3c102-mt don't exists.. :???: 
Nobody can help me ???

---

### Post by katu on 2005-11-16
had the same problem. google revealed this page:
[http://www.mneylon.com/blog/archives/2005/09/25/skype-on-breezy/](http://www.mneylon.com/blog/archives/2005/09/25/skype-on-breezy/)
also a search in the forums provides this address. 
In short, try to install an older .deb, which you can find there.
cheers,
Katu

---

### Post by skonvolt on 2005-11-16
[QUOTE=katu]had the same problem. google revealed this page:
[http://www.mneylon.com/blog/archives/2005/09/25/skype-on-breezy/](http://www.mneylon.com/blog/archives/2005/09/25/skype-on-breezy/)
also a search in the forums provides this address. 
In short, try to install an older .deb, which you can find there.
cheers,
Katu[/QUOTE]

Thanks a lot !!!!  :p

---

### Post by megamania on 2005-11-16
[https://wiki.ubuntu.com/SkypeHowto?highlight=%28skype%29](https://wiki.ubuntu.com/SkypeHowto?highlight=%28skype%29)

hope that helps!

---

### Post by chris_andrew on 2005-11-16
Add this to your /etc/apt/sources.list, do an update and install the Skype static package, using dselect/ apt or whatever.

This works perfectly.

Chris.

---

