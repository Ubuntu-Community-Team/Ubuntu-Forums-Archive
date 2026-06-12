---
title: "How to force an uninstall with NO prompting?"
date: 2012-10-02
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2012-10-02
I am trying to UNinstall the useless GRUB packages from the CLOUD version of Ubuntu.  These are not needed when doing a PV-GRUB based instance launch in AWS (a lovingly handcrafted /boot/grub/menu.lst is all that is needed).  I would not have bothered with this except for the fact that now there is an update to a GRUB package that is causing a prompt that freezes my automated customization script.

If a prompt happens when no one is there to read it ... did it make a sound?  Well, I don't know.  But it freezes the whole procedure.

So I decided to just remove all the GRUB packages.  But even THIS won't let me do it (under automation).

I think we need a special install system to make packaging work under automation.

On a hunch I tried removing /boot/grub in advance.  But even that didn't help (the question it prompted was do I want to remove files in /boot/grub ... obviously it doesn't check to see if there are any).

Any ideas?

---

