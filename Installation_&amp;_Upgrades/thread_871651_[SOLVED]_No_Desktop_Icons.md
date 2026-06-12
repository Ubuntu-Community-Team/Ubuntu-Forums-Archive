---
title: "[SOLVED] No Desktop Icons"
date: 2008-07-27
forum: Installation &amp; Upgrades
---

### Post by greenco on 2008-07-27
Last night I partitioned my hard drive and installed Ubuntu 8.04. and everything seemed to be working great. I shut down the system and went to bed. This morning when I booted up, the desktop came up but there are no icons on it. I could not select anything, so I am running it from the Live CD. I can see both of the drives so the data is still there. How can I get the system to boot up to a usable desktop?

It looks like it is trying to boot off of the wrong partition.

---

### Post by coffeecat on 2008-07-27
> **greenco said:**
> I could not select anything, so I am running it from the Live CD.

Let's get this right. Could you select anything from the Places menu, or was it just the bare desktop that was concerning you? Or were the desktop panels not there either? And/or were the icons missing from the panels? (The panels are the thin strips top and bottom.) You said that last night everything was working OK, so were there icons on the desktop last night?

In case you don't know this already, the default Ubuntu Gnome desktop is very minimalist with no icons. If you want icons, open a terminal and:

```
gconf-editor
```Now navigate to apps > nautilus > desktop and select the icons you want to be visible.

Of course, if your panels are missing or devoid of icons too, there's a problem. Perhaps you could clarify exactly what's wrong.

---

### Post by buixuanduong1983 on 2008-07-27
I also had this problem (not realy a problem) before. I had 1 ext3 partition for Ubuntu itself, and 1 ntfs one for data. That time when I installed Ubuntu I forgot to map my data partition to /media/data (when prompted for mapping / and swap). Then, when boot up, I got an empty desktop, but all other function still working as expected. But if I map /media/data to data partition then I have the icon of data on desktop. I think this is only an icon, you can create it (I myself not yet know how to create it, since it look not like a normal shortcut to a folder, but created automatically when we assigned a mount when installing). If anyone know please tell us, otherwise you can re-install Ubuntu and map it when prompt.

Hope this help.

---

### Post by greenco on 2008-07-27
coffeecat, When I boot without using the Live CD, I hear the bootup music and then the desktop screen (with the heron on it) appears. There is absolutely nothing else on the screen. I have moved the mouse pointer all around hoping to hit upon a link. If I press the "F1" key the help screen appears.

The panels are also missing.

Yes the icons were there and they all worked.

---

### Post by coffeecat on 2008-07-27
OK, I understand. You're getting the wallpaper and absolutely nothing else. Yes, something's gone wrong.

Try this: with the empty desktop, press Alt-F2. If nothing happens, then read no further. If you get a 'Run Application' window, type 'gnome-panel' (no quotes) into the command field and press return. If this brings up the panels then try, for good measure, 'nautilus' next. It won't do any harm. It just restarts nautilus if it's stopped. Nautilus, by the way, covers a lot of the functions of the desktop, not just the file browser. The 'nautilus' command should also bring up a nautilus file browser window.

If that works, it doesn't necessarily mean it will 'stick', so you need to reboot to see what happens next time. Let's take it from there.

---

### Post by greenco on 2008-07-27
coffeecat, the " Alt-F2 " keys did not do anything.

I am about ready to do another install from the Live CD. I just wish I knew more about what I am doing.

---

### Post by coffeecat on 2008-07-27
> **greenco said:**
> coffeecat, the " Alt-F2 " keys did not do anything.

Sorry I couldn't think of anything else to try.

> **greenco said:**
> I am about ready to do another install from the Live CD.

A wise choice. Although whatever has gone wrong is probably fixable, it could easily take longer trying to find out exactly what is wrong and then finding a fix, than doing a re-install.

I hope the re-install goes OK. Good luck!

---

### Post by greenco on 2008-07-27
Thanks for your help!

I will try to install it again.

---

### Post by greenco on 2008-07-27
The new install worked!!!
I now have my hard drive partitioned with two partitions and I can start installing my programs.

Thanks to all that have helped me!!!

---

