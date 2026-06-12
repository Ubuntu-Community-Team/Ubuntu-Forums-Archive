---
title: "LiveCD boots into screen corruption"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by Apewall on 2007-01-26
Just downloaded both the alternative CD and LiveCD.  Trying to install Ubuntu on my MSI laptop, problem is that I have screen corruption when the liveCD boots, also I tried installing with the alternative CD and then my installed ubuntu's display is corrupt.

I'm new to ubuntu but have been using linux awhile, any suggestions?

laptop has a mobility Radeon x1600 to note.

AMD64 system with Amd64 version of 6.10 Edgy ubuntu.

---

### Post by casaschi on 2007-01-26
> **Apewall said:**
> Just downloaded both the alternative CD and LiveCD.  Trying to install Ubuntu on my MSI laptop, problem is that I have screen corruption when the liveCD boots, also I tried installing with the alternative CD and then my installed ubuntu's display is corrupt.

I'm new to ubuntu but have been using linux awhile, any suggestions?

laptop has a mobility Radeon x1600 to note.

AMD64 system with Amd64 version of 6.10 Edgy ubuntu.

Not sure if I understand what "screen corruption" is, but I solved a similar problem by typing "vga=791" (remove quotes) or "vga=771" at the boot: prompt of the live CD

---

### Post by Apewall on 2007-01-26
I'm referring to screen corruption as in the screen displays garbage that isn't remotely close to what the desktop should look like.

I've tried using the vga= boot options but they yielded no results, same problem.

---

### Post by Apewall on 2007-01-28
I tried working with xorg.conf resolutions/refresh rate etc, as well as various boot options but none have seemed to work, I could probably install from the standard terminal but I'm not understanding why exactly the screen is having these problems, its using the VESA driver by default.

Posting an image:
[img]http://img.photobucket.com/albums/v312/Apewall/100_0161.jpg[/img]

---

### Post by Apewall on 2007-02-09
To update on this post, Dapper Drake 6.06 works fine - both LiveCD and install.

But trying to install 6.10 or update to it from 6.06 results in the above garbled screen.  I've tried changing my video driver in xorg also with the same results.

---

### Post by gapplewagen on 2007-03-09
A friend of mine is having this same problem on his MSI 1039 (ATI Mobility X1600) when installing KUbuntu.  He's bringing it over tonight so we can mess with it.  I'll post any results here.  I also plan on trying to boot into Feisty and see what happens.

---

### Post by zvacet on 2007-03-09
```
sudo dpkg-reconfigure xserver-xorg
```
choose vesa driver and see if that corect your problem.

---

### Post by brickheadbs on 2007-03-10
[FONT="Verdana"][SIZE="4"]Screen corruption. That's the term I've been trying to find to explain what I've got going on. Similar thing is happening on my **nVidia GeForce 6600**. It looks similar to how the card will look if you way overclock the video memory (don't know if anyone else has done that?). I haven't really been able to find any others with nVidia cards having this problem. Either I'm special or I'm "special" because I haven't been searching right.[/SIZE][/FONT]

---

