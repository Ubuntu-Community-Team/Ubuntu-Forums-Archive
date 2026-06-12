---
title: "Live CD not working for me"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by Homesrfan on 2007-01-30
I'm a total n00b at this so hang with me.

Anyways, I have setup a Live CD and to make sure I did it right I popped in the CD and it came up with 'Ubuntu Browser' thing showing a little about it and that I should boot with the CD in the CD tray. When I tried to do this, I got 'ISOLINUX Debian...' and then some version number and a little more text. This was on the classic black screen with white text. What have I done wrong? This is not the first time that this has happened. I first tried Fedora and this worked too.

Thanks a lot, and try not get TOO technical with me. I'm just a kid. ;)

---

### Post by K.Mandla on 2007-01-30
Hi and welcome. You should get a text menu after the "ISOLINUX DEBIAN" message, asking you if you want to start up or install Ubuntu, or if you want to check the CD, etc.

Do you see any of that?

What kind of computer are you using?

---

### Post by jso2897 on 2007-01-30
Yeah. I got the same thing, but it basically asked whether I wanted to reformat from fat32 to linux format and how much of the disc i wanted to format for linux (if i wanted dual-boot) and whether to install Ubuntu as a boot , and then i proceeded from there. Are you not getting this? Be aware that if this box already had Windows on it, Linux will require that the portion of the disc it occupies be reformatted from fat32 to the Linux standard. If, of course, you want to go Linux all the way, you choose the option of reformatting the whole disc.

---

### Post by Homesrfan on 2007-01-31
But all I am seeing is just ISOLINUX DEBIAN 3. something. Then a date. And that's it.

I'm running a Gateway DX200.
Windows XP Service Pack 2

Intel Pentium 4 CPU 3.06 GHz
3.07 GHz, 504 MB of RAM

---

### Post by Homesrfan on 2007-01-31
I have successfully booted the same CD up in an OOLLDDD computer I have. So it's definitely not the CD.

---

### Post by Homesrfan on 2007-02-01
Can someone please help me?
If I completely reformat do you think that this will help?

---

### Post by usererror on 2007-02-01
> **Homesrfan said:**
> Can someone please help me?
If I completely reformat do you think that this will help?

for what it's worth, i don't think reformatting your hard drive is worth it yet.  do you have a spare hard drive laying around you could put in for testing?  i guess it's possible that maybe the MBR or partition table is possibly messed up some how?  just throwing out ideas here. :(

---

### Post by lyceum on 2007-02-01
> **Homesrfan said:**
> I have successfully booted the same CD up in an OOLLDDD computer I have. So it's definitely not the CD.

Just because it works in one PC does not mean it is not the disk. Try to run a disk check (third option down when starting up). YOu may need to re-burn at a slower speed, but then I don't know what speed you burnt at :)

---

### Post by Homesrfan on 2007-02-01
> **lyceum said:**
> Just because it works in one PC does not mean it is not the disk. Try to run a disk check (third option down when starting up). YOu may need to re-burn at a slower speed, but then I don't know what speed you burnt at :)

I used almost the slowest you can burn and it didn't work.

---

### Post by usererror on 2007-02-02
have you tried using that CDrom from the old computer in the computer you want to install ubuntu on???

---

### Post by Homesrfan on 2007-02-02
> **usererror said:**
> have you tried using that CDrom from the old computer in the computer you want to install ubuntu on???

Yes I used the same CD.
And I don't have a spare hard drive.

---

### Post by Ludwik on 2007-05-09
I have the same problem. I've used Ubuntu since version 5.04, and I installed it on dozen other computers. But yesterday I tried to install it on my friend's PC and all I get is:

```

ISOLINUX 3.11 Debian-2007-03-12
```

On the black screen. And that's all. Nothing after that and nothing before. 
I tried with many different CDs:

Official Ubuntu 7.04 CD from ShipIt
Official Ubuntu 6.06 CD from ShipIt
Ubuntu 6.10 CD-R that I burned myself
Official Kubuntu 6.06 CD from ShipIt
Ubuntu 7.04 Beta CD-R that I burned myself

All those CDs works perfectly well on all other computer. On this one the result is always the same - black screen with this one line.

Any ideas?

---

