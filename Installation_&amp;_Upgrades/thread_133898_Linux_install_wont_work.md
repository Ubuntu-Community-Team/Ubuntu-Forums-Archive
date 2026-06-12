---
title: "Linux install wont work"
date: 2006-02-20
forum: Installation &amp; Upgrades
---

### Post by suplexx on 2006-02-20
Hi,

   This is my first attempt at installing linux on a PC. I have installed a distro of linux on an xbox before, but nothing other than that. First off the system specs are:

duron 1.8 ghz
256 mb ram
13.5 gb hd
CD-RW
s3 trio 32/64

 I downloaded the latest install image and burned at 8x ( the lowest my cd burner can go ). I checked the md5sum ( turned out OK ). I checked the cd-rom integrity ( turned out OK ). Everything goes fine, and goes to the base install. About 75% in it says 
"**UNABLE TO INSTALL *INITRD* TOOLS**".
I tried booting with linux acpi=off but it did not work. Can anyone point me in the right direction?

---

### Post by suplexx on 2006-02-21
Anyone? I cannot seem to get around the error.

---

### Post by atpat on 2006-02-21
I've been trying to install the AMD64 version and have had similar problems of it crashing out during the base installation.

I'm shooting in the dark, but using "noapic nolapic" seemed to make things more stable.  It had real problems with my D-link wireless card, so I took it out and skipped the networking step.  I read about enabling "SMP" but couldn't find anywhere how to do this :???: , apart from using a different ISO which doesn't seem to exist on any of the download sites :mad: .  Anyway, so I guessed with "linux smp=true noapic nolapic" and it got past the base installation into Stage Two :) .  Unfortunately something went wrong with this too :-| .  Now I seem to have Linux, but just a command line: it doesn't boot to the GUI.

You might try those switches and see if it makes any difference.  My next trick is to try installing from the DVD instead of the CD.

---

### Post by suplexx on 2006-02-21
Well after installing over and over I seemed to get passed the problem, but then when booting I get "grub loading... ERROR 15". So I tried using the livecd. Everything goes well and it boots up fine, there is just no video. It's pitch black. And I can't alt+f2 or f3. I'm starting to think of windows again :mad:.

---

### Post by suplexx on 2006-02-21
Argh..
I am so frustrated. Is it possibly the video card? It is very old and I could not find drivers for it on even windows xp. I plan to switch to linux because of all the BSOD's and such but I do not know if I should use ubuntu. It has had a lot of problems with my hardware thus far.

---

### Post by atpat on 2006-02-22
[QUOTE=suplexx]Argh..
I am so frustrated. Is it possibly the video card? It is very old and I could not find drivers for it on even windows xp. I plan to switch to linux because of all the BSOD's and such but I do not know if I should use ubuntu. It has had a lot of problems with my hardware thus far.[/QUOTE]

I've heard that adding the switch "vga=711" helps under such circumstances.  Presumably this limits the video output to some low-resolution mode which any hardware should be able to handle.  Try that: "linux vga=711" (plus any other switches you used before).

---

