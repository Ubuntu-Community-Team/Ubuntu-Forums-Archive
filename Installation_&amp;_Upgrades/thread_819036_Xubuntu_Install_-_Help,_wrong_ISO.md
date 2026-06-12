---
title: "Xubuntu Install - Help, wrong ISO?"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by biggsjm on 2008-06-05
I need to download the iso for xubuntu / alternate install CD. I've downloaded both the standard and alternate CD iso for intel x86 computers (mine is an old P3 550e with the intel i810e chipset)

Problem is, that when I try to load the kernel it says, this is not the version for my hardware, I need a 64-bit process to load this kernel.

WTF?

Is the link broken? Please help. . .trying to get this machine going for my kids.

---

### Post by ibutho on 2008-06-05
This [link]("http://cdimage.ubuntu.com/xubuntu/releases/8.04/release/") on the Ubuntu cdimage site has links for both the 32 bit and 64 bit versions. Is this where you got your isos and are you positive they are the 32 bit versions?

---

### Post by biggsjm on 2008-06-05
Yes. I downloaded the 'PC (Intel x86) alternate install CD' iso.

---

### Post by biggsjm on 2008-06-05
bump

---

### Post by wpshooter on 2008-06-05
How much memory does your machine have ?  Have you checked this and the other machine specs. against the minimum requirements of Xubuntu 8.04.  Perhaps your machine is lacking meeting one or more of the requirements.

P. S. - PIII is getting pretty old for even Xubuntu.

Good luck.

---

### Post by biggsjm on 2008-06-05
> **wpshooter said:**
> How much memory does your machine have ?  Have you checked this and the other machine specs. against the minimum requirements of Xubuntu 8.04.  Perhaps your machine is lacking meeting one or more of the requirements.

P. S. - PIII is getting pretty old for even Xubuntu.

Good luck.
I checked. Its got 64 MB now, which is considered the 'minimum' for xubuntu.

The error message specifically states that I need an i686 process for the version I am trying to install and I have an i386 processor.

---

### Post by oilchangeguy on 2008-06-05
> **biggsjm said:**
> I checked. Its got 64 MB now, which is considered the 'minimum' for xubuntu.

The error message specifically states that I need an i686 process for the version I am trying to install and I have an i386 processor.

it is possible you downloaded the wrong version. mistakes do happen. but the bigger problem is the very low specs of your computer. what are your kids going to do with it? as operating systems continue to evolve older computers are going to be left out. by using the bare min. of ram you're just setting yourself up for a bad linux experience. either obtain more ram, or use an even lesser linux version, damn small linux, or puppy. or even a fresh install of windows 98se.

---

### Post by biggsjm on 2008-06-08
Tux Paint and maybe surf websites like Webkinz. Nothing special. Just don't want them playing on my HTPC or my MacBook Pro.

I'll check out Puppy and DamnSmall. I plan on upgrading the memory to at least 512MB . . . it was an inherited PC, that I figure can get me through until the oldest is in Kindegarten or 1st grade (2 or 3 years), then I was thinking of getting them something a little better.

---

### Post by zvacet on 2008-06-08
Try to install Xubuntu this way.First make swap partition and after that root and home (home is optional but it is good choice if you have enough space).Let your swap be at least double then your ram.Put swap on the end of disc(it is optional too).

---

### Post by avtolle on 2008-06-08
Since you are running 64mb RAM at the moment, I'd make the Swap partition at least 3x Ram, as there's going to be a fair amount of swapping happening under Xubuntu (or many other distros) with that low RAM. Once you upgrade the box to 512, things should become much quicker (and at that point, you would likely be able to shrink the Swap parition).

---

### Post by CREEPING DEATH on 2008-06-08
Xubuntu is going to be a lot for that machine, I'd try Debian-XFCE or just CLI Debian and install XFCE and whatever else you need using Aptitude and Synaptic.  I've run Lenny using the latter technique on a PentiumMMX-233 (NOT a PII!) with only 64 MB RAM and surfed the web and installed Flash on it!  128 MB or 256 MB would make it more than acceptable for a kid's computer.
Make plenty of swap, I set my machine up to have 300 MB (it'll eventually have 128 MB RAM) but it only had a 3.2 GB HDD.

CD

---

