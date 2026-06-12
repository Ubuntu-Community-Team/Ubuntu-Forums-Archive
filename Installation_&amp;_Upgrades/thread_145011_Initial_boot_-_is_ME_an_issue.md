---
title: "Initial boot - is ME an issue"
date: 2006-03-15
forum: Installation &amp; Upgrades
---

### Post by backintheday on 2006-03-15
Downloaded and burned to cd ubuntu-5.10-install-i386.iso, but cannot get the initial boot to come up.  I've tried some of the tricks I've read here, but none have worked...this includes booting from cd first, removing jumper from hd, but no luck.  Is ME the reason or is there some trick to get this boot???

Thanks!:confused:

---

### Post by LoclynGrey on 2006-03-15
ME?

Maybe detail how you installed, on to wot drive(s), are you dual booting?
the more info of your set up the better we can assist

---

### Post by backintheday on 2006-03-15
Not sure all the info you need...Dell Pentium 4, 60G Hard Drive (single), 256MB RAM running Windows ME and I am not wanting to dual boot.  I came across this site from PCWorld article I read “Make an Old PC Into a Linux-Based File and Print Server” and did as it said “pop the CD into the old PC, and start it up…”

[http://www.pcworld.com/reviews/article/0,aid,124162,pg,10,00.asp](http://www.pcworld.com/reviews/article/0,aid,124162,pg,10,00.asp)

Let me know if you need any other info…thanks again!

---

### Post by LoclynGrey on 2006-04-14
If you want to dual boot, it might pay to read the forum posts first as you will find many people have set up a dual boot with windows.
Type Dual boot in the search window.

in a quick nutshell, you need to partition your windows os first making room on the drive for linux. then when installing ubuntu u dont erase all the drive but make it install on the partition thats free. Then you modify your grub boot loader   so that you can manually select windows or Ubuntu.

---

### Post by RRS on 2006-04-15
Since you don't intend to dual boot partitioning, etc. is unnecessary. Simply follow the onscreen prompts from the install disc to replace Windows with Ubuntu.

However it doesn't sound like you're able to get that far yet, so first:

If you've reset your bios to se the CD drive as the first boot device then you may have a bad disc.

Since most of the download sites are pretty reliable, perhaps you burned it too fast? When burning an ISO image anything faster then 4x is not recomended.

Double check these items and let us know if you have any more problems.

---

### Post by Kapre on 2006-04-15
[QUOTE=backintheday]Downloaded and burned to cd ubuntu-5.10-install-i386.iso, but cannot get the initial boot to come up.  I've tried some of the tricks I've read here, but none have worked...this includes booting from cd first, removing jumper from hd, but no luck.  Is ME the reason or is there some trick to get this boot???

Thanks!:confused:[/QUOTE]

backintheday - did you check your d/l? Did you check it's MD5Sum? How did you burn the ISO? Did you specify in your recording program to burn the image? Try to burn it on a slower speed.If you have checked and followed all this questions, your CD should boot properly.

K

---

