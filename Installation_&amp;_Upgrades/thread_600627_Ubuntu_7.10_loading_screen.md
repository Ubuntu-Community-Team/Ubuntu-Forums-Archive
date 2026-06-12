---
title: "Ubuntu 7.10 loading screen"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by lord.toan on 2007-11-02
I didn't see any answers to this problem that helped in the forums, so I'm going to post what problem I'm having and hopefully someone can help me out.

I just made a boot disk for Ubuntu 7.10.  I'm on Windows XP, and wanted to get a Linux distribution, so a friend of mine suggested Ubuntu.  I made the boot disk, and took about an hour to fix my D: drive (it works fine now, i've tested it with other disks so that's not the problem)

I start up my computer, the Ubuntu opening comes up.  I select Start or Install Ubuntu, and it just sits on that screen... It seems to be loading, but I've left it running for at least an hour at one point and it just sat on that screen.  My friend said to go in and change "splash" to "nosplash" in the boot options, so I did, and it's still giving me the same problem.  I even tried it in Safe Graphics Mode with the "nosplash" change and got nothing.  Does anyone know how to fix this and/or has had this problem before?

---

### Post by dabang on 2007-11-02
When you boot with no splash - where does Ubuntu stop, what does the screen say?
You may also try booting with the "noapic" or - but this I'd second - "acpi=off" option and see if it works.

---

### Post by Therion on 2007-11-02
Assuming you just want to give Ubuntu a test-drive from the LiveCD:

Boot your PC using the Ubuntu LiveCD.
From the GRUB menu hit "Escape" (you'll only have a few seconds to do this).
Select "**Recovery Mode**" (you'll wind up at a system prompt).
From the system prompt type in:
```
 nano /boot/grub/menu.lst
```
Scroll down to the bottom of the page using the arrow key, past all the # signs until you come to the first line that starts with Kernel.  This will be a long line of code that runs off the end of your display.  Use the arrow keys to scroll to the end of that line where you'll find where it says **-ro -splash -quiet**
Remove the word splash.
Ctrl+X to save, confirm the overwrite and boot from there.

This should get you to the desktop where you can test out the LiveCD and start the install process if you choose to do so.  Once you've installed, though, you'll need to RE-edit menu.lst since you'll no longer be booting from the LiveCD.

---

### Post by lord.toan on 2007-11-03
It doesn't say anything... I press enter where it says "Start or Install Ubuntu" and it just freezes there.

I'm thinking it may have to do with the fact that I downloaded the program through HTML and burned it at 32x...

Would that affect this kind of problem?

I'm going to try your solutions as well though, then try to dual boot it with windows, which it's already started doing, and I'm having errors with "vzlinux" now. But I'll get to that problem when I get to it..

---

### Post by lord.toan on 2007-11-03
When I press esc, it comes up with boot:

if i type in nano /boot/grub/menu.lst, i get an error saying nano is not found.

booting with noapic and acpi=off gives me the same problem I've been having.  I have a feeling it has to do with the way I burned the CD.  I may try out another distribution instead.

I was using a live cd of kubuntu, which is nice, but i can't figure out how to dual boot it from windows.

I'll keep tryin with that and if I can't figure it out, I'll just try another version that has a dual boot installer.

In the meantime, if anyone can figure something out to make this work for me I'd appreciate it.

---

