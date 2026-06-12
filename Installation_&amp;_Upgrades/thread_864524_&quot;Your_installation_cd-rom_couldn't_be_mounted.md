---
title: "&quot;Your installation cd-rom couldn't be mounted&quot; Hardy 8.04 installation"
date: 2008-07-19
forum: Installation &amp; Upgrades
---

### Post by chiron80 on 2008-07-19
I'm trying to install Hardy (8.04) on an older (Gateway) Pentium III 550 (9 years old). It currently has Feisty running just fine (although a bit slow). I want to wipe and install clean (for a variety of reasons).

In any case, I'm using the Alternate install CD, trying to get a Command-line only installation. The problem I'm having is that after selecting the language and detecting my keyboard, the installation is complaining that "Your installation cd-rom couldn't be mounted".

I know the problem is not the CD itself for two reasons:
1) The computer just booted from the CD fine.
2) In Feisty, I'm able to mount and read the CD with no trouble.

After encountering that error, I've tried a number of things found on different forum posts, to no avail (ide=nodma, for example). I'd like to avoid borrowing an extra CD drive from work and cracking open the case to swap in a new CD.

I also tried entering a command prompt (from the installation menu), and looked for "hda" (which is the CD drive) in /dev and it *was not there*. This makes me think that the problem is related to the configuration of my hard drives/CD drives:
My CD drives are plugged directly in to the first IDE port on my motherboard. My hard drives (all three) are plugged in to an expansion PCI card. When I do an "ls hd*" at the command prompt, all I see are "hde" "hdg" and "hdh" (which are three hard drives), but no "hda".

Any suggestions how I can get the CD drives working for installation?

Let me know if more information is needed.

- Ben

---

### Post by Sef on 2008-07-19
> I'm trying to install Hardy (8.04) on an older (Gateway) Pentium III 550 (9 years old). It currently has Feisty running just fine (although a bit slow). I want to wipe and install clean (for a variety of reasons).

How much ram do you have?

---

### Post by chiron80 on 2008-07-20
> **Sef said:**
> How much ram do you have?

The computer is maxed out with 768MB of RAM (three sticks of 256MB).

---

### Post by AlbinoClock on 2008-08-30
I had this same problem and couldn't find an answer. On a whim I opened and closed the CD drive then tried again. It worked. I have no idea why, but this seems to do it.

---

### Post by kandjar on 2008-09-04
I also encounter the same kind of issue, at first I added ide=nodma to the boot prompt without success... However on a second attempt, I placed it at the beginning of the boot param line and it worked.

I hope this will help.

---

