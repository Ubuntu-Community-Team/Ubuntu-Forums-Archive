---
title: "Natty netbook upgrade hides unity"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by eadwacer on 2011-05-01
I was running Ubuntu 10.4 netbook version (with Gnome) on my Dell Inspiron 910 and yesterday it told me there was an upgrade available, to Natty. I followed the links, did the download, and left it to install overnight.

When I got up today, it said it had a problem, because an application was using a file it needed. I thought I had closed everything before I started the process. I acknowledged the message, and proceeded to restart.

I ended up with the standard 10.4 Ubuntu screen, but with no tool bars, status bars, or anything. Just the wallpaper. Keyring login came up and I signed in, wireless said it was connected. So it looks like things are working, just no UI as such. Poked all the screen edges with the mouse, but nothing popped out.

Ctrl><Alt><Del> brought up the logout screen, and if I clicked on Help, I could ultimately get Firefox to run. (Note: the Help screen talks about Gnome, but it had the new popout scroll bars).

If I hold down <Shift> on startup, I get the GRUB menu. I am running linux generic 2.6.38-8 , but I am not sure where to go from there. Running dpkg didn't help. 

Any ideas?

---

### Post by eadwacer on 2011-05-01
NOW the safe graphics mode tells me that I don't have the hardware for Unity (it couldn't have checked before?) and that I have to select Ubuntu Classic at login. Now I have to figure out how to turn off autologin.

---

### Post by garvinrick4 on 2011-05-01
> If I hold down <Shift> on startup, I get the GRUB menu. I am  running linux generic 2.6.38-8 , but I am not sure where to go from  there. Running dpkg didn't help. That kernel is from 11.04 natty you must have did 2 dist-upgrades to get from 10.04 to 11.04 or you can go directly form 10.04 to 11.04 if so I have not seen it nor heard of it.
If you are running Gnome with Unity interface in 11.04 it is run by compiz and just maybe your computer cannot handle that. Is it an older model? In login box click on your user name and
should be some buttons on bottom, use classic ubuntu to get the gnome desktop you are used to. In 11.04 it is now called Ubuntu for the Gnome Unity interface and Gnome Classic for the Gnome interface. Change to classic ubuntu and log back in.

---

### Post by eadwacer on 2011-05-01
So that was it -- my iron's too old. 
1. I went through <Shift> on bootup to get to GRUB, 
2. opened it in safe graphics mode and told it to run once
3. It gave me the the classic screen, and I went into System/Administration/Login Screen
4. I chose Ubuntu Classic (left autologonon)
5. Power cycled, got GRUB again, and told it to just run linux
6. It Just Works...now...and I have my old Ubuntu Back -- only it's Natty now.

This is an example of the power of the 'confessional' style of debugging. You grab the programmer next to you, or your SIGOther, or the wall, and tell your tale. Before too long, you've figured it out.

---

### Post by eadwacer on 2011-05-01
Yep. Too old. Thanks.

> **garvinrick4 said:**
> That kernel is from 11.04 natty you must have did 2 dist-upgrades to get from 10.04 to 11.04 or you can go directly form 10.04 to 11.04 if so I have not seen it nor heard of it.
If you are running Gnome with Unity interface in 11.04 it is run by compiz and just maybe your computer cannot handle that. Is it an older model? In login box click on your user name and
should be some buttons on bottom, use classic ubuntu to get the gnome desktop you are used to. In 11.04 it is now called Ubuntu for the Gnome Unity interface and Gnome Classic for the Gnome interface. Change to classic ubuntu and log back in.

---

