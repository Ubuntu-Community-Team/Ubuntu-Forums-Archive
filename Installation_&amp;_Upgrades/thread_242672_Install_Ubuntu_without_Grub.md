---
title: "Install Ubuntu without Grub"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by pwiesen on 2006-08-24
I use Fedora as my main Linux distro but saved some space on hdb to try out other distro's in a dual-boot.  I want to give Ubuntu a go, but don't need Grub installed as I can simply modify the exisiting Grub from within Fedora.  The install CD GUI didn't seem to have any options for Grub, am I missing something here? Is there a way to install Ubuntu without Grub.
:confused:

---

### Post by K.Mandla on 2006-08-24
I know if you escape out of the installation near the end, you should get the option of installing LILO instead of Grub.

But I don't know if you can skip "around" all the bootloaders. It's worth a try.

---

### Post by pwiesen on 2006-08-25
Thanks for the reponse.

That kind of sucks :mad:  Not a very dynamic installer, is it?  Can anyone else offer any suggestions.[-o<

---

### Post by carontis on 2006-08-25
I know there are many other (third parts) Linux Loaders free, try to look to [http://www.softpedia.com]("http://www.softpedia.com") in the Linux section. I don't know what could be the best, 'cause I don't use any of them,  but they have also instructions and all needed to show you how they are.

---

### Post by cmmgmg on 2006-08-25
> **pwiesen said:**
> 
That kind of sucks :mad:  Not a very dynamic installer, is it? 
Yes, major sucking for any dual/multibooting... Some suggested the use of the **alternate **ubuntu cd which allows, among other things, to install the grub to the partition itself, which could then be taken over by your usual bootloader.

Why they didn't make this not so unusual possibility an option in the normal dvd is unknown, and quite an annoyance. Other distros (eg SuSE, Mandriva,...) simply allows this option in an advanced install panel that doesn't get much noticed to newcomers, and thus doesn't distract them (this is to answer anybody who would try to blindly defend ubuntu's developers' decision).

---

