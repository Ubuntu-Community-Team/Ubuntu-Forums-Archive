---
title: "Booting Problem"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by SilentOnee on 2010-07-21
Hi everyone,

I received the Ubuntu CD by mail the other day and tried to install a dual boot with it. I first tried it out by running from the CD and the first problem I had was the screen froze after the splash screen. So I lurked around for a bit and found out that I can press any key on the screen with the keyboard and person to get to a different screen. At this screen I entered "F6" and then entered "nomodeset", this allowed me to pass the splash screen.

Next, I got into Unbuntu but I found out that the keyboard and mouse weren't working, so I lurked again and found out that I have to enter "noacpi" (sorry if I got that wrong, I forgot the name :().
I ran by CD once more and everything worked, so I decided to finally install it next to my Vista.

However, after installing it goes straight to the splash screen, and the freezing happens again. The screen where the keyboard and the person are not showing up so I have no idea how add the "nomodeset" and "noacpi". 

So my question is, how do I get to the screen where I can add both those things? Also, is there a way to add it permanently so I don't have to keep pressing F6? 
Can someone help me please?

---

### Post by davidmohammed on 2010-07-21
press shift when booting - it will display a list of kernels - this is your grub.  Press e to edit.

find the line with quiet splash - add nomodeset and noacpi immediately before quiet splash.

This will allow you to boot.

When you get to the desktop

type in a terminal

sudo nano /etc/default/grub

add your nomodeset noacpi parameters to GRUB_CMDLINE_LINUX

save

sudo update-grub

its worth trying noapic and/or nolapic as alternative boot options.  noacpi is quite drastic since it affects power management and other stuff like fan control.

---

### Post by SilentOnee on 2010-07-23
Thanks for the help davidmohammed, everything works fine!

But I need help saving the 
     /etc/default/grub 
Selecting "Save contents" makes me choose a location to save it in as Save As. But, I have a feeling it's not the right way to do it.

Thanks again! :grin:

---

