---
title: "Installing individual .deb packages ??"
date: 2004-11-04
forum: Installation &amp; Upgrades
---

### Post by troutrou on 2004-11-04
I apologize in advance for my ignorance... but I only know RPM (Mandrake) and don't have a cluuuuue about the system Ubuntu uses.

My understanding is that it uses the same system as "Debian", which use .deb files, which basically look like RPM files except there are called DEB ?

My problem: I searched "Grisbi" in Synaptci, I found it, but it's version 0.5.0, that's buggy. Latest version is 0.5.2.  
Lgged on [www.grisbi.org](www.grisbi.org) , was lucky and found a ".deb" file, whic I guess is what I now need to use from now on.  I downloaded it into my home folder, but now....how to install it ???!!!!

I tried to load it into Synaptic, but I can't file an "open file" command anywhere, it will only add either a URL or a CD-ROM, not a local file ! :o(

So I tried to just double-click on the file in Nautilus, like I would do with an RPM in Mandrake, but it doesn't seem to work, I get an error message (see screen shot below).  Sorry it'sin French, I guess basically it says : "Cannot display the file,  error whilst launching the application".

A bit like it was not understanding that it's a .deb file, and thought it was a picture or whatever instead...

Thanks for any help...

Vince

<SCREEN SHOT REMOVED>

---

### Post by az on 2004-11-04
Open a terminal and do
sudo dpkg -i gr*.deb

---

### Post by troutrou on 2004-11-04
[QUOTE=azz]Open a terminal and do
sudo dpkg -i gr*.deb[/QUOTE]

Wow, did that, 5 seconds later my brand new, updated Grisbi came to life ! :o)
And it also appears nicely in Synaptic as well !! :o)

Thanks for the help :o)

I guess that now I have switched for Ubuntu, and am unlikely to come back to Mandrake, I will have to learn the ins and outs of Debian.  
Now if someone could tell me how Debian stores SCSI devices information... maybe I could get Sane to detect my AGFA Snapscan 1236s !! :o(

Sane says to put the 'device', or a symlink to it, into /dev/scanner, but I don't have that folder in /dev on ubuntu.  But I have it in Mandrake 9.2, and the scanner worked first time there...  So I guess a link to the device would suffice but... what file (where) must I link to  !???? :o(

Debian forum help ! :o(


Vince, a problem a day...

---

