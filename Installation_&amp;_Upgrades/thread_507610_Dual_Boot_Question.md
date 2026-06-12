---
title: "Dual Boot Question"
date: 2007-07-23
forum: Installation &amp; Upgrades
---

### Post by pinoyskull on 2007-07-23
I have an existing Feisty Fawn installation, is there a chance that I can dual boot WinXP without redoing Feisty? Could someone point me to a guide?

Thanks

---

### Post by Wim Sturkenboom on 2007-07-23
Yes you can install windows afterwards. Unfortunately I don't have a link at hand, so you have to do the search for that yourself. Or wait for a friendly person to come along.

---

### Post by pinoyskull on 2007-07-23
ill try to search and at the same time wait for responses here :) thanks

---

### Post by pinoyskull on 2007-07-23
since my harddrive (80gb) is formatted as an ext3, i guess the 1st thing to do is resizing it?

---

### Post by KIAaze on 2007-07-23
Yes, resizing is probably the first thing to do.
I doubt that Windows allows you to do it. ^^

But, most importantly, _**you should back up your MBR before**_:
[http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/]("http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/")
[http://en.wikipedia.org/wiki/Mbr#Unix-like_systems]("http://en.wikipedia.org/wiki/Mbr#Unix-like_systems")

That way, theoretically, you could install Windows on another partition and then restore the MBR.
I have never done it, but I think it should work.

Whatever method you use, it's a sure way to be able to reboot into Ubuntu if there are any problems (unless you formatted the Ubuntu partition of course).

In case of big problems: [http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

---

### Post by pinoyskull on 2007-07-23
> **KIAaze said:**
> Yes, resizing is probably the first thing to do.
I doubt that Windows allows you to do it. ^^

don't have windows yet, i installed ubuntu first

---

### Post by upthelum on 2007-07-23
I've always been told to install windows first as ubuntu will set up the boot grub but apparently installing windows second could wipe mess with the grub and you may not be able to boot into both os's.

---

### Post by KIAaze on 2007-07-23
> don't have windows yet, i installed ubuntu first
That's what I mean: the windows installation process won't offer you any resizing/partitioning options as far as I know, and there certainly isn't any ext3 resizing in it.

All you can do is probably choose on which partition, you want to install Windows.

So you'll have to resize first either with the Ubuntu Live CD or the GParted Live CD.

Windows is known to destroy the MBR and impose itself as the only OS on the PC. :mad:
That's why it's usually always installed first.

None of those problems exist with GNU/Linux distros. :)
They all play friendly and you can easily install 5 or more of them (record is about 200 or so I think (edit: nope, but there's 145. see below. ;) )).
They can even share the same /home directory (and maybe even the programs (in /usr), but I don't know exactly how to do that.).

edit:
For fun:
[How to install and boot 145 operating systems in a PC]("http://www.justlinux.com/forum/showthread.php?t=147959")
[A grub menu booting 100+ systems of Dos, Windows, Linux, BSD and Solaris]("http://www.justlinux.com/forum/showthread.php?t=143973")
:D

---

### Post by pinoyskull on 2007-07-23
ok i've successfully done the 1st part of the problem, i resized my ext3 partition using ubuntu live cd and allocated 20gb (more than enough for me) of free space for windows xp to use

the next step would be installing windows xp, now i know xp will kill grub during installation, what step should i do or what files to backup in order to restore grub after xp's installation?

---

### Post by KIAaze on 2007-07-23
20MB?
I don't think that's enough for Windows.
You'll need a t least 2 or 3 GB. Even 5GB counting all the updates you'll have to get after that.
I suppose you meant GB. ^^

> 
the next step would be installing windows xp, now i know xp will kill grub during installation, what step should i do or what files to backup in order to restore grub after xp's installation?

As I said, you'll need to **back up the MBR (Master Boot Record)**.
Theoretically, Windows shouldn't touch your Ubuntu partition. So all Grub program files should be safe.

However, you might want to **back up /boot/grub/menu.lst**.

edit:
Official WinXP system requirements:
[1.5 gigabytes (GB) of available hard disk space]("http://www.microsoft.com/windowsxp/pro/upgrading/sysreqs.mspx")

---

### Post by pinoyskull on 2007-07-23
sorry for the typo its 20gb :)


is it a good idea to use Super Grub Disk to restore grub after windows installation?
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by Wim Sturkenboom on 2007-07-23
Installing windows first is easier. When installing Windows, it will replace the bootloader in the MBR with it's own version without even looking at other OSes.
Hence one has to 'fix' grub afterwards and next add a Windows entry to it. It also seems to be possible (don't ask how) to configure Windows so it can load Linux.

---

### Post by manndani on 2007-07-23
If you look at this thread (compliments to "Catlett") 
[http://tinyurl.com/2kmugw](http://tinyurl.com/2kmugw)
Great instructions for re-doing grub from the live CD, really good instructions & easy to follow.
I've used it and I'm greatly in "Catletts" debt, saved me a heap of hassle.
Thank you.

---

