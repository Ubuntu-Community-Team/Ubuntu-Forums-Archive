---
title: "How do i uninstall ubuntu while windows is installed within it?"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by canadac57 on 2010-01-26
I had ubuntu installed and i installed windows inside it. 
How do I uninstall ubuntu without reinstalling windows? 
It is booting using gimp if that's any help.

_________________
_Jason Harding
[EMAIL="JasonHarding@katechengines.com"]JasonHarding@katechengines.com[/EMAIL]
[JasonHarding@yahoo.com](http://nhakhoanhantam.com)

---

### Post by lisati on 2010-01-26
:confused:
That's a new one on me, Windows installed within Ubuntu and booting with gimp. Unless, of course, you're talking about a virtual machine or booting with grub.

---

### Post by raymondh on 2010-01-26
I, as well, am confused and am inclined to think windows is virtualized as guest.  

raymond

---

### Post by canadac57 on 2010-01-26
yes in a virtual machine within windows

---

### Post by kansasnoob on 2010-01-26
I built a house on a hill.

How do I remove the hill without moving the house?

---

### Post by JackRock on 2010-01-26
I found this easiest by installing VirtualBox, creating a virtual machine, and installing XP (also tried with Lucy Lucid Ubuntu and Windows Server 2008 on separate VMs).  Works quite well.

---

### Post by raymondh on 2010-01-26
If ubuntu is the HOST and windows is the GUEST ... and you want to remove the host whilst retaining the guest ... hmmmm, kansasnoob has a point, sorry :(

if windows is the HOST and Ubuntu is the GUEST .... just delete Ubuntu.

Sorry, cannot find any info here for you:

[http://technet.microsoft.com/en-us/library/bb740920.aspx](http://technet.microsoft.com/en-us/library/bb740920.aspx)

Raymond

---

### Post by JackRock on 2010-01-26
DOH!  Can't believe I misread this post, utterly.  

No, you can't remove the host OS without removing the virtual OS.  One is built on the other.

---

### Post by adam814 on 2010-01-27
Depends on what virtualization software you're running.  If it's VirtualBox I know there's an option to "Export Appliance" in OVF format.  I've heard VMWare also does so.  You can move your appliance to another drive and install whatever OS you want, then install VirtualBox and import your appliance again from wherever you saved it.

---

