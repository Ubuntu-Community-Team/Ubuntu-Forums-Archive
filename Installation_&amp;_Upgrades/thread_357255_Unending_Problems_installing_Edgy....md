---
title: "Unending Problems installing Edgy..."
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by Relasz on 2007-02-09
Ok, so yes, I am kind of new to the Linux scene, but if stuff like this keeps happening I know I'm not going to be here long. Last night, I couldn't get the CD to load - yes, ok, I resolved it down to a hardware issue with my CD burner, and fixed it. After hours trying to figure out what was wrong and finally fixing the issue, I get the installer going. First try, everything installs ok, I boot into an Error 22. Not even the Windows Boot CD recovery fixed it, and there was nothing I could do to get back into windows, so I formatted my primary system NTFS partition for Ubuntu. I go back to the installer and start installing again, and for once it actually does. I get into Ubuntu, but have a few problems with display drivers, so I check up on the official troubleshooting wiki, only to have the installation break thanks to one of the guides on there. I can't get back into Ubuntu at all, it crashes everytime before it starts, and me being new to Linux, I don't know how to get back in to restore backups and fix everything especially when I don't know exactly what the problem is. So, I reinstall Ubuntu, boot up, Error 22. Again. Again. Again.

Seriously, I'm at loss for words here, I was referred to this particular distro and told it was 'User friendly'. I could mouth off against Linux here, but I choose not to for the fact it's free.

I really would like to get into this as my main OS, but if stuff like this keeps up and I'm formatting every second day... then all I'd have to say is Vista here I come.

The question is, how do I stop it from Error 22ing every time I reinstall.

---

### Post by x64Jimbo on 2007-02-09
Have you tried installing with the Alternate Install CD? It's designed to work around a lot of the problems that happen when installing with the LiveCD on some kinds of computers.

---

### Post by mikewhatever on 2007-02-09
Hi Relasz, 
I am sorry you've been having problems with Ubuntu, and it was a good decision to post here. Try and find a little more patience, just enough to let people help you.
What's the situation at the moment? Is Ubuntu installed, or have you formated again?

---

### Post by sevencapitalsins on 2007-02-09
Error 22: if i'm not mistaken, it means that you have a bad partition table (i suppose it's an error related to GRUB).

Have you installed GRUB on the master boot record (MBR)? Or did you try installing it somewhere else?

Anyway, that is a serious problem, because if your pc can't read its partition table he can't find where the programs are and hangs.

(now someone will wag his finger at me yelling "you're impure!" but i tried to keep it simple)

Now, I suggest you to try booting from the liveCD, and try to read the content of your partitions. If you succeed in reading, maybe it's only a grub error, and editing the /boot/grub/menu.lst file could save you from endless buddhist-like reinstallations.

You can find easily instructions on how to write a grub menu file, GIYF they say. Google...

If you can't read absolutely nothing... then try something else: Fedora, Mandriva, Debian...

Or revert back to MS :) the choice is yours, i've already made mine (kubuntu+beryl, graphics and fancy and eyecandy, love 'em)

I hope this was useful :)

---

