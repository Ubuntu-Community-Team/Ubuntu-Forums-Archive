---
title: "Dapper GUI install has no options for monitor resolution??"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by tommcd on 2006-06-04
I just did a clean install of Dapper using the GUI install CD. Everything went ok, except the monitor resolution was set at 1024x768. There was no place during the install to choose monitor resolutions??? I then tried:
sudo dpkg-reconfigure xserver-xorg 
I went with the defaults for everything, just selected the monitor resolutions I wanted. After this X was all screwed up and I could not boot to the GUI at all. Tried to reconfigure xorg several times without success.
I the used the text-based install CD, this lets you choose monitor resolutions (just like the Breezy install CD) and everything went ok. I now have 1280x1024 res. on my Samsung 19" LCD.
1) why does the Dapper GUI install CD not have options for monitor resolutions?
2) why did dpkg-reconfigure xserver-xorg not work,? It worked fine in Breezy.
Any advice appreciated, thanks!! Dapper is pretty cool otherwise.

---

### Post by tommcd on 2006-06-04
UM, ok, I think I found the answer to question #2 above. I forgot to stop X (/etc/init.d/gdm stop) or boot to recovery console before I reconfigured xorg (stupid noob mistake).
But why does the Dapper GUI install CD not let you choose monitor resolutions??

---

### Post by jonrkc on 2006-06-06
[QUOTE=tommcd]
But why does the Dapper GUI install CD not let you choose monitor resolutions??[/QUOTE]I downloaded and used the Xubuntu ISO (desktop version) and there's an option you can choose with one of the function keys to select resolution.  *But *when I did that, my monitor (also 1280x1024, and a Princeton) responded with an "out of range" message.  No display.

So I rebooted from the CD and didn't choose anything, and my 1280x1024 resolution was automatically detected.  

I wonder why yours wasn't...?

---

### Post by kornelix on 2006-06-06
My initial install also offered no options for monitor resolution. After first boot, the max. available in preferences was 1024x768. My monitor is 1920x1200. After I installed the proprietary nvidia driver (linux-restricted-modules package) and went through the elaborate and mysterious xserver config stuff, the full resolution was supported.

---

