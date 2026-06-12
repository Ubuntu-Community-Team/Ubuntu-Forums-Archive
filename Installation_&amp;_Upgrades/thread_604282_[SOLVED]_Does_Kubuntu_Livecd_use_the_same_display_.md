---
title: "[SOLVED] Does Kubuntu Livecd use the same display detection settings as Ubuntu?"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by keyboardashtray on 2007-11-06
I wanted to look at KDE and burned the Kubuntu Gutsy LiveCD.

When I tried to load it, after it got past the loading bar, it just brought up a scrambled image. When Ubuntu gets past the load bar, it still runs through some text, so this wasn't even at the desktop yet.

Tried safe graphics mode, same thing.

If the Ubuntu CD works, shouldn't the Kubuntu one?

---

### Post by K.Mandla on 2007-11-06
Usually it should, but there's no guarantee, particularly where the live CD is concerned. 

You could, if you wanted, install *kubuntu-desktop* and give it a test drive that way. Your graphics changes should be set, and it should work fine.

(By the way, before you go downloading the entire kubuntu-desktop package, add that CD you already burned to your sources.list, and it will save you a lot of time. ;) )

---

### Post by keyboardashtray on 2007-11-06
> **K.Mandla said:**
> Usually it should, but there's no guarantee, particularly where the live CD is concerned. 

You could, if you wanted, install *kubuntu-desktop* and give it a test drive that way. Your graphics changes should be set, and it should work fine.

(By the way, before you go downloading the entire kubuntu-desktop package, add that CD you already burned to your sources.list, and it will save you a lot of time. ;) )

I'm curious what you meant, 'particularly where the live CD is concerned'? Does Kubuntu do something different than Ubuntu during that initial startup process, i.e., is this bug-report worthy? I'm just wondering why my Ubuntu and Xubuntu CDs got through it alright.

I did try installing Kubuntu desktop (thanks for the CD/repo tip btw), but I don't know if I got quite the feel of KDE, there was so much clutter (from having all my Gnome stuff there), and I was loathe to really configure much as I just did a clean install of Ubuntu the other day, ditched the Windows partition, got everything the way I like it. I got kind of nervous, my machine was going crazy (not blaming KDE, I checked the system monitor and Nautilus was running at 50 percent CPU for some reason in Kubuntu) so I didn't stay long before I logged back onto Gnome and removed it.

---

### Post by keyboardashtray on 2007-11-11
Well, I'm going to chalk this up to a bad CD or something, unless I hear otherwise. The file passed the md5sum and the CD passed the error check, but a couple times restarting it never made it through, one time mentioned a segmentation fault. (After a few more tries I had eventually made it through, with proper display.)

I burned another CD and managed to install Kubuntu off of it, with no display hitches.

---

