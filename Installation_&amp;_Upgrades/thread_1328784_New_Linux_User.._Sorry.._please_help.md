---
title: "New Linux User.. Sorry.. please help"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by atsig411 on 2009-11-16
I am new to Ubuntu. Trying my first install now. I have a Dell 1650 dual 1.8 2GB RAM. I downloaded Ubuntu 9.10 desktop. I burned the image.

When installing I get to the language select, then the main screen where I chose install Ubuntu. That is the last screen I see after selecting install. Mostly black with very very qucik images of install text. 45 minutes later I have this:

GNU GRUB version 0.97 (640k lower / 2096064 upper memory)

[ Minimal BASH-like line editing is supported. for the first wprd, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename.]

grub>

I'm not used to this and I though I would get a visual screen to begin. Does anyone know what I did wrong?

I have now done this three times with the same result.

---

### Post by cenzorrll on 2009-11-16
are you using the "try ubuntu without installing" or the "install ubuntu" option when you first start up?

i've always had an easier time installing from the "try ubuntu first" one.

---

### Post by wrgb2 on 2009-11-16
What happens if you run the Live Cd?  Choose the option to Run Ubuntu without making any changes to your system - the first option.

---

### Post by atsig411 on 2009-11-16
I'm using the "install ubuntu"

I can try "use Ubuntu without installing" but I thought that would just boot from the CD?

---

### Post by atsig411 on 2009-11-16
when I try "Run Ubuntu without making any changes to your system"

I get this:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of Built-in commands.

(initamfs) _

Does this make any sense?

---

### Post by cenzorrll on 2009-11-16
it does boot from the cd to a usable desktop environment, it has an install icon on the desktop that will take you through the install. it's very easy and straightforward. it should also tell you if anything goes wrong with the installation.

from the looks of it, it seems grub isn't installing correctly from the "install" method.  if this happens while using the livecd, at least you still have a working environment to fix it from.

---

### Post by atsig411 on 2009-11-16
"at least you still have a working environment to fix it from"

I guess it is live but I'm not sure what GRUB is and I am not successfully installing it. any suggestions?

---

### Post by cenzorrll on 2009-11-16
> **atsig411 said:**
> when I try "Run Ubuntu without making any changes to your system"

I get this:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of Built-in commands.

(initamfs) _

Does this make any sense?

hmm, looks like your cd or ISO was corrupted.  i forget how to hash-check, you may want google how to run that to check that your iso is good.  or try burning another disk.

---

### Post by audiomick on 2009-11-16
Hallo. 
It seems to me that Ubuntu isn't making it into the GUI at all.
The built in shell that is referred to is a terminal, which turns up when the GUI can't start.

There is a section in the forum about Dell computers. Try searching there for your model.

There is also a data bank in the Ubuntu Documentation about supported laptops. Try and find that and see if your computer is supposed to work, or is known not to.

---

### Post by atsig411 on 2009-11-16
Sorry I typed it wrong it is a Dell 2650 Server

---

### Post by oldos2er on 2009-11-16
The first thing to do is to run 'Check CD for defects' or md5sum the disc ([https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)).

---

