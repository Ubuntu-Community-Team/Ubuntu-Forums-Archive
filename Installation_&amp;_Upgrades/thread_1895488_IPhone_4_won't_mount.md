---
title: "IPhone 4 won't mount"
date: 2011-12-14
forum: Installation &amp; Upgrades
---

### Post by bob12564 on 2011-12-14
My IPhone 4 connects to my Ubuntu 10.10 computer "out of the box" and synchs instantly with Rhythmbox.

I have a new laptop and I installed Xubuntu 11.10 which is my first experience with Xubuntu.  I attached the IPhone and expected the same instant connection.  It doesn't seem to mount.  I don't get any acknowledgment that it's connected and I can't see it in Thunar.  Rhythmbox doesn't see it.

To make sure it wasn't a version issue, I rebooted from an Ubuntu 11.10 live CD and the Iphone was recognized immediately and was seen in Banshee.

I know that Xubuntu is supposed to be a lighter version of Ubuntu so I'm guessing that there's something that's installed by default in the Gnome version that's missing from the XFCE version.  Can anyone tell me what I need to load?  I saw some posts about IFuse and libimobiledeviceces (or something like that) and I installed them but that didn't help.

Thanks.

---

### Post by bob12564 on 2011-12-26
Further research and I think I've discovered the problem: Thunar.  Other Apple device users indicate that their Ipods, IPads, Iphones, etc. don't mount automatically on XFCE systems.  Thunar is integrated into XFCE.  Gnome systems use the Nautilus file manager which uses GVFS to see remote file systems.  Thunar, from what I've read, is supposed to be using GVFS also, but many Apple users report that it doesn't work.  I tested the theory myself by installing Nautilus and voila!  Nautilus see the Iphone.  Once Nautilus has picked it up, Rhythmbox also sees it.  If you start with Thunar, Rhythmbox won't see it because it isn't mounting.  This is all over my head but at least I can follow what's happening.  Nautilus is more resource intensive than Thunar and many people prefer Thunar because it's lighter.  But at least with Nautilus I can get the Iphone to work.

---

### Post by LewisTM on 2011-12-27
I use XFCE and Thunar. Thunar won't mount my Ipod Touch automatically. At least my Cario-Dock Shortcuts applet will detect and launch it on demand. However, that will only call Thunar' afc:// handler and won't mount it with GVFS for use with Rhythmbox or Banshee.

To connect to my Ipod Touch, I use **Clementine** because it doesn't rely on GVFS. It works like a charm plus it's fast and looks good.

Cheers!

---

### Post by bdalzell on 2012-09-12
Installing nautilus under Xubuntu 12.04  also worked instantly for me with my iphone 4 OS 5.5.1 on Sept 12 2012. Now I can copy my photos, which are in the top level folder DCIM, from my iphone to my linux desktop. However I have NOT tried to copy anything back to the iphone or deleted pictures from the iphone using Nautilus. The last time I copied anything back to it the result was trashing the ios install. Does anyone have experience with this two way traffic?

---

