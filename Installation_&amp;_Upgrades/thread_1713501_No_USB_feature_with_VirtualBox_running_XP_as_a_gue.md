---
title: "No USB feature with VirtualBox running XP as a guest"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by thefazz.machine on 2011-03-24
Sorry this is a last resort. I tried adding myself to the group vboxusers but it did not help.

I then read that the reason that i don't have any sub capability when i'm running XP as guest OS using VirtualBox is that I have a open source version of the program.

So I uninstalled the one I got through software center and downloaded and installed one from VirtualBox website. It installs but does not tell me where to find it in the menu so I don't know how to launch the program. It also doesn't show up as an "installed software" when I search for it in software center.

Can I get some help please? Thanks. I'm running ubunto 10.10 btw

---

### Post by .:PiXi²:. on 2011-03-24
Does it show up when you run "VirtualBox" in a terminal?

---

### Post by howefield on 2011-03-24
You are best with the virtualbox.org downloaded deb package, but remember that there are no longer two versions of VirtualBox.

There is one version, to which you can add the closed source features that were previously part of the PUEL version, (including USB support) by adding an extension pack downloadable via the VirtualBox website.

Download the current version which corresponds with your Ubuntu version from the website, plus the extension pack.

---

### Post by thefazz.machine on 2011-03-24
> **.:PiXi²:. said:**
> Does it show up when you run "VirtualBox" in a terminal?

Bravo, I had no idea how to find it because it wasn't in any of the menus. Is there any way to insert it into the menu?


> **howefield said:**
> You are best with the virtualbox.org downloaded deb package, but remember that there are no longer two versions of VirtualBox.

There is one version, to which you can add the closed source features that were previously part of the PUEL version, (including USB support) by adding an extension pack downloadable via the VirtualBox website.

Download the current version which corresponds with your Ubuntu version from the website, plus the extension pack.

Cheers

---

### Post by thefazz.machine on 2011-03-24
Works, thanks guys. I  enabled USB in virtualbox options, added myself to group vboxusers and also had to click on devices tab on the guest xp window and manually click on the usb that i want mounted.

Cheers

---

