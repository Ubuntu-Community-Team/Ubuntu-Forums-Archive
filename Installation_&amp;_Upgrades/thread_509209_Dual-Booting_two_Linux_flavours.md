---
title: "Dual-Booting two Linux flavours"
date: 2007-07-25
forum: Installation &amp; Upgrades
---

### Post by BigSilly on 2007-07-25
I'm currently running both Windows XP and Ubuntu 7.04 on my desktop. I have a fairly small 80Gb HD, made up of 40Gb for XP, a 20Gb FAT32 spare partition that I use to share files, and a 20Gb partition that I use for Ubuntu.

What I want to do in the future is put PCLOS where my Ubuntu is now, and put the next Ubuntu (7.10) where my XP is, giving me a solely Linux desktop setup. My plan being for Ubuntu to be the main family OS, leaving me PCLOS to play around with.

I understand this can be quite tricky to do compared to dual booting Windows and Linux. Is this true? Are there any simple guides, preferably shying away from the command line since I'm a bit of a noob, that I might find useful somewhere? Have you performed this procedure yourself? If you have any hints and tips please let me know.

Your help much appreciated.

---

### Post by Wim Sturkenboom on 2007-07-25
I installed Slackware 10.2 and next installed Ubuntu 6.06. The Ubuntu install automatically picked Slackware up, so I don't think that you have to worry.
Even a quadruple boot (WinXP, Slackware 10.2 (2x) and Ubuntu) worked (Ubuntu installed last).

Hint:
do NOT share the home directory as data files might be incompatible or interfere with each other (e.g. KDE versus Gnome)

---

### Post by BigSilly on 2007-07-25
Ah I see, thanks for that. 

That's excellent. I'd heard it could be a complicated procedure, but it flummoxed me just how. I would have expected whichever boot loader installed second would pick up all the OS's on the drive, whether Linux or not. I don't intend to share home directories or anything like that. I wanted them to be completely separate so I could play around with PCLOS at my leisure without upsetting the family's Ubuntu setup.

Again, thanks for setting my mind at rest. :)

---

### Post by Wim Sturkenboom on 2007-07-25
Please note that my experience was only with Ubuntu as the last distro. As far as I know, one has to do it manually in slackware and older redhat versions (except for the windows detection).

---

