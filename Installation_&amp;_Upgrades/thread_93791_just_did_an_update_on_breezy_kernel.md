---
title: "just did an update on breezy kernel"
date: 2005-11-22
forum: Installation &amp; Upgrades
---

### Post by daniel49 on 2005-11-22
And so now I show a couple entries in grub for  Breezy 2.6.12-10-386 and
2.6.12-9-386

And the original Hoary hedgehog installation from cd 2.6.10-5-386

plus windows xp


Question #1:
So once I am satisfied the latest and greatest is behaving I would want to remove these other entries other then xp.
How do I specifically do that?

Also question 2: I assume say I installed java while it was hoary and updated to breezy and then removed Hoary from my machine as per question one that would not affect java or any other programs I installed earlier would it?

thanks Dan

---

### Post by ranf on 2005-11-22
[QUOTE=daniel49]
Question #1:
So once I am satisfied the latest and greatest is behaving I would want to remove these other entries other then xp.
How do I specifically do that?
[/QUOTE]
Answer #1:
Just the way you usually add/remove packages:
- synaptic
- apt-get
- aptitude
- dselect
and there are some more for KDE AFAIK.

---

### Post by narcolept on 2005-11-22
If you wish to do it manually, I believe ubnutu/kubuntu are the same as debian, in that you would edit /boot/grub/menu.lst and you can remove the kernels you don't wish to see from there.  If you wish to remove them entirely, go with the above poster and apt-get remove them rather than manually trying to remove kernels and their accessories.  You can also change your default kernel in /boot/grub/menu.lst, by specifying the default (just remember the first one is 0 though, not 1)

---

