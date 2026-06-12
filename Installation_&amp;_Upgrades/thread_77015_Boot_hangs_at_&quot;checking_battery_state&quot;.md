---
title: "Boot hangs at &quot;checking battery state&quot;"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by J-Doe on 2005-10-16
I' finally got my new laptop and figured that I should propably install kubuntu as a secondary OS. I installed Breezy, everything went just fine. Then I uncommented all the reps in sources list (as I used to do with hoary) and ran upgrade and dist-upgrade.
The problem is now that I can't boot at all anymore cause boot process hangs at "checking battery state"...I also tried without powercable and it hangs as well to "loading laptop mode".

I tried booting with secondary kernel (can't remember what's it called :) ) and updated everything again. I just can't start X server from there cause it gives an error saying that I have no proper nvidia drivers... I installed those to again but now change

What can I do? :)

I'm thankfull for your answers...

---

### Post by malacoda on 2005-10-16
I was experiencing the same problem, except on a PC.

Initial install would go well, but once I installed the nVidia drivers via the Adept Pkg manager my system would hang up each time I booted right after finishing 'Checking Battery Status'.

After a bit of research am input from others, I came to suspect the nVidia drivers I was using from the repositories had a bug that locked up X11 (or xserver or what ever you want to call it...).

I decided to install from source by following tseliot's how-to:
[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia]("http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia")

Before you do though I recommend installing Mozilla Firefox first.  When I tried downloading the driver he recommends (from the nVidia website) my desktop would become corrupt (due to not having the video driver installed yet) if I used Konqeror.

Installing the driver per this how-to resolved my 'boot hang' issue.

---

