---
title: "Please help can't install linux standard base"
date: 2013-10-11
forum: Installation &amp; Upgrades
---

### Post by Nate12341999 on 2013-10-11
I have downloaded lsb_4.0-0ubuntu8.tar.gz and i have tried all the "read me" instructions and none of them worked!, I've looked online and still no instructions. Please if anyone has downloaded LSB 4.0 successfully please tell me how you did it or if you found instructions that you know have worked link them.

Thanks 

-Nate

---

### Post by heir4c on 2013-10-12
What version of Ubuntu you use? (and is it the desktop or server version) And why you want install that package? What version of that package is on your system?
Open UbuntuSoftwareCenter and type in the search-field: lsb-   (with the - behind lsb, than you see all packages with lsb)
If you want the .deb file you can download it from: [http://packages.ubuntu.com/en/lucid/lsb](http://packages.ubuntu.com/en/lucid/lsb) (scroll down and click on "all".)
But better is to use synaptic to install that packages. (You can install synaptic via UbuntuSoftwareCenter or via terminal)
 Also it can be give conflicts with your system, so be careful.

---

### Post by Lars Noodén on 2013-10-12
I see the packae lsb-base - Linux Standard Base 4.1 init script functionality - in the repository.  Is that what you want?  If so, open up the Software Center or Synaptic and use that.  Whenever possible, it is best to install using the package manager.  Not only is it easier to install but it will also manage dependencies and updates, including security updates.

---

