---
title: "iPod touch mounts, but appears empty in Rhythmbox"
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by grooverunner on 2010-11-22
Hello,
My iPod touch was working fine in 10.04 and since the upgrade to Maverick, I cannot see the songs in it in Rhythmbox or Banshee. In Rhythmbox it appears empty and crashes Rhythmbox when I try to right click it to see the properties. In Banshee the songs appear as 'other'. Trying to read it in GTKPod yields the following error: iPod Database failed: Error during parsing of file /home/user/.gvfs/user's iPod/iTunes_Control/iTunes.

I tried re-installing the gstreamer plugins, and also libimobiledevice to no avail. Also tried re-installing the ipod plugin for Rhythmbox and nothing there either.

Also, i am able to actually play the music on the iPod via Nautilus so it is not a mounting problem. 

It is an iPod Touch 2.0.

Any thoughts?

---

### Post by morganevans on 2010-11-24
I've had the same problem with a 3rd Gen Shuffle.  Banshee won't even show the podcasts I've transferred using iTunes (although gtkpod and Rhythmbox will and can even delete them)

Nothing seems to correctly transfer music to the ipod in a state where the device will play it.  The file appears to copy to the device (with extension intact) but disconnecting then reconnecting the device shows no tracks (in Rhythmbox which is as far as I've tested) which indicates something isn't being updated in the iPod DB.  Either that or the latest firmware updates (when restoring an ipod from iTunes) have locked out some devices in Linux.

Then again, I'm using 10.10 which seems random at best when it comes to external storage support.  I could mount my Samsung GT-S3370 as mass storage in 10.04, but no longer.  It's just as shame Ubuntu's philosophy shift has changed from the "it works" attitude to "let's be different and make everyone else's life more complicated!"  In fact, I've tried and hate Unity (it's just so broken) and have removed UbuntuOne and the indicator applets from my Gnome desktop and I'd disable the god-awful notification system if I knew how.  I like a desktop to be a workbench - clean, efficient and free of annoyances.

---

### Post by morganevans on 2010-11-24
To be honest, I'm starting to think the worst - it's an firmware issue.  The file iTunesStats, which when deleted allows mounting in gtkpod, keeps re-appearing every time I plug in the device.

gtkpod reports any podcasts uploaded to the device as orphaned after a reconnect so either the firmware doesn't like what Linux apps are doing (most likely) or all three apps I've tried using (gtkpod, banshee and rhythmbox) are failing to update the databases properly (unlikely unless it's a shared library issue)  Looks like I'll be going for a non-Apple media player.

---

