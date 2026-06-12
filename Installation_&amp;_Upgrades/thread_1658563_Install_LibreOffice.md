---
title: "Install LibreOffice"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by nsivin on 2011-01-02
I want to try LibreOffice. When I go to the Synaptic Package Manager and search for it, it turns up in the left column only. It has no context menu, nor do any of the buttons in the left column work. Searching does not put it into the right column. In other words, there does not seem to be any way to install it. Any suggestions?

I may decide to uninstall OpenOffice before this installation.

---

### Post by Spencer Caplan on 2011-01-02
Libreoffice isn't finalize in the main Ubuntu repositories so it won't show up in Synaptic by default. You can though add the PPA to your system to get it. This should work, but I have yet to test it. Let me know if there are any issues.

echo 'deb [http://download.tuxfamily.org/gericom/libreoffice](http://download.tuxfamily.org/gericom/libreoffice) /' | sudo tee -a /etc/apt/sources.list

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 890E7A26

sudo apt-get update 

sudo apt-get install libreoffice3* lobasis3.3*

---

### Post by fabricator4 on 2011-01-02
> **nsivin said:**
> I may decide to uninstall OpenOffice before this installation.

You might want to hang on to Open Office for a while.  The current version of LibreOffice is a release candidate only, and is not intended for production use.  This is why it's not distributed at the moment.

You can read more about LibreOffice and download it [from here]("http://www.documentfoundation.org/download/").

Libre Office is a fork of Open Office that has a way to go.  If they were to make it easier for Microsoft users to migrate to Linux it would probably be a good thing.  I don't know if that is their intention.

Chris

---

### Post by zeroseven0183 on 2011-01-02
You can install LibreOffice via PPA:
```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update && sudo apt-get install libreoffice
```

Mind you, the PPA removes OpenOffice. And if you think LibreOffice looks like Windows 95-ish, install libreoffice-gtk.

Just a note, this version is still RC.

---

