---
title: "Installing new stable tomboy 0.12.0 on hardy"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by sojusnik on 2008-09-24
Hi,

A new version of tomboy 0.12.0 was released some days ago. Is there a possibility to install this program via a .deb package?

The new version is also in the ubuntu packages for intrepid:
[http://packages.ubuntu.com/intrepid/tomboy](http://packages.ubuntu.com/intrepid/tomboy)

I'm using a 64-bit Ubuntu and can't install the .deb file offered there - getting the following error message:

Error: Dependency is not statisfiable: libglib2.0-0

Thanks in advance.

---

### Post by Idefix82 on 2008-09-24
Try
```
sudo apt-get install libglib2.0-0
```

Edit: It would be easier for you though if you could find a repository where the new version is offered. This way you don#t have to care about dependencies.

---

### Post by sojusnik on 2008-09-24
Do you know where I can find an appropriate repository?

After "sudo apt-get install libglib2.0-0" the terminal tells me that "libglib2.0-0" is already the up-to-date version.

---

### Post by Idefix82 on 2008-09-24
No, you just have to google for it. If you don't find one then just execute the command I gave you but you might have to do it for other dependencies as well. I am actually a bit surprised since presumably you have got the older version of tomboy preinstalled. libglib2.0-0 is also a dependency of that.
If you need to install lots of dependencies then a quicker way might be to first install Tomboy from the standard repositories via Synaptic, then delete it again but leave all the packages that were installed along with it and then install the new tomboy.

---

### Post by Knacker on 2008-10-01
[http://www.getdeb.net/release/3223](http://www.getdeb.net/release/3223)

Worked without a hitch for me.

---

### Post by Mr. Spoon on 2008-10-01
I've tried the version currently it the repositories (0.10.0?) and this version, and I receive the same errors regardless when trying to run it.

I removed tomboy and then ran *apt-get build-dep tomboy* to see if I got these errors (sure enough I had some dependencies to download that *apt-get install* didn't satisfy) but with each version I receive the same errors which I placed at [http://pastebin.com/f44a409e7](http://pastebin.com/f44a409e7) . Any one mind helping a brother out?

---

### Post by lindenRathen on 2008-10-14
its probably better to check [http://www.getdeb.net/app/Tomboy](http://www.getdeb.net/app/Tomboy) here - scroll to the bottom and pick your architecture the link above posted by Knacker is for the 32-bit version

thanks for the pointer though seems to be working fine! - just need to sort out tasque/tomboy across my desktop and a laptop....

---

