---
title: "Installed Karmic, but no taskbar. Need to install video driver. Help w/ Terminal PLZ!"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by killabee44 on 2009-11-20
Hi all,

I did a fresh install of Kubuntu Karmic on an IBM T42. Its an older machine and I remember that when I once installed Jaunty on it I had to also install the third party video drivers.

Well, this time I can't even see the taskbar or the kmenu. The video is really bad when I click on anything so I can't see it.

I need to install the video driver, but the only way I have available to me is with the terminal. Can you guys help me out with that? 

PS. The IBM T42 uses a Radon 7500 32mb video card.

Thanks!

---

### Post by killabee44 on 2009-11-20
Ok, I found this thread:

[http://kubuntuforums.net/forums/index.php?topic=3107466.15]("http://kubuntuforums.net/forums/index.php?topic=3107466.15")

That at least helped me find a temporary way to bring back the plasma and see the taskbar, etc.

"Open any program (or Right-click somewhere on your desktop to bring up the context menu, so you can select "Desktop Settings", or anything with a titlebar). Then you can  right-click on the currently garbled titlebar, and select "configure Window Behavior", once there you can try Kwin effects, which will bring back your plasma"

I don't know how permanent this will be. I will try it for a while. 

They posted another fix in that thread that involved creating a xorg.conf. I tried that but it led to my machine only being able to boot into a command prompt.

---

### Post by efflandt on 2009-11-21
You likely need to install **xorg-driver-fglrx**.  I had issues with an older PC with both Ubuntu and Xubuntu 9.10 with ATI video.  Without that Xubuntu would work initially, but could not run X once it did updates (could only log into xterm or console).  If you tried to log into Xfce it would fail and loop back to login prompt.

Ubuntu would not even get that far.  On the first boot of a new system would start to load gnome and then lock up solid (no cursor movement and no Ctrl-Alt-Fn access to console).  But fortunately it had a **Failsafe GNOME** login which worked fine with X.  Once I installed xorg-driver-fglrx, I was able to reboot and log into regular gnome.

And I tried Xubuntu again, and if I installed the fglrx package before any updates, it worked after the updates.  Although, both 9.10 version were slow on the old PC.  So it looks like Jaunty would be best for that (it worked fine when installed before trying the 9.10 versions).

I am not familiar with Kubuntu, so I am not sure if it has a failsafe way to boot into KDE.  And I am not really familiar with apt.  But if you have a network connection I imagine the command from xterm or console would be **apt-get install xorg-driver-fglrx** (see man apt-get).

---

### Post by Mark Phelps on 2009-11-21
If you force the installation of the fglrx driver, you will most likely have NO VIDEO!  That's because there is no fglrx driver that works with your card and Karmic.

The other link post pointed to configuration setting you can adjust with the Radeon open source driver -- which is the only driver that will work in your setup.

---

### Post by killabee44 on 2009-11-21
Thanks for your replies guys,

Well, Mark you were right about the fglrx driver. Did not work. I tried the xorg.conf in the link I posted but no video at all either. I guess it might work if I make modifications to the xorg.conf (maybe?). Im kind of lost as to what to change. 

Right now I have no acceleration with this card and resolution is only at 1024X768 and that's the max it will go.

I will do research first though to see what worked for others with this card. If anyone has other input please let me know. THanks all for your help.

---

