---
title: "General &quot;how it works&quot; question.  Drive auto-detect"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by sonicsmooth on 2007-10-29
How does or doesn't ubuntu and/or the kernel detect what IDE drives are on the system?

I ask because I originally installed ubuntu with the cdrom as secondary IDE master.  Then I removed it for a while, and now it's on primary IDE slave.  Somehow (I think) ubuntu recognized it and put an icon in my computer folder (or whatever you call it -- the "My Computer" equivalent for ubuntu).  However there was a second icon also claiming to be the cdrom drive, but it was more generic "cdrom" rather than "dvd +rw drive".  I believe one of them acutally mounted the cdrom with data in it, but none mounted a DVD properly; I was unable to view a standard DVD even with the libdvdcss2 libraries installed and all the latest xine, mplayer, etc.  For some reason xine is tring to read /dev/hda1 (see my other post on this).

After moving the drive, I looked at my fstab and it was still pointing to the old location for auto-mounting /media/cdrom.  I wouldn't expect this to change, since it was originally just written by the main installation.

I lookd at my /dev/dvd and /dev/cdrom links and they were still pointing to /dev/hdd (secondary IDE slave).  I kinda half expect these to change automatically because it's such a low level thing, I think the kernel or "'ubuntu" or something should "just fix it so it works".  I don't believe this is technically difficult, but rather an architectural/philosophical thing.

So it looks like some parts of the OS recognized the location and identity of the drive, yet other parts were stil looking at these stale links.

Does ldconfig somehow manage/mangle these links?  I ran it blindly and it didn't change anything.  I changed them manually instead to point properly to /dev/hdb.

How do "other OSes" automagically manage these drives while completely hiding the exact details from the user?

As someone who just wants to use the computer (I'm making a home media server with Mythtv, etc., and *every single little thing* poses another 30-120 minute delay while I google it and *try* to figure it out). Ironically/surprisingly, all my drivers are working fine, so it really does just come down to usability architecture.  Normally the explanation for why Linux is annoying/hard to use is that the drivers aren't there from the manufacturers, but now that I do have the drivers, I seem to be having infinite problems with things like soft links, libraries, where-things-are-pointing, selecting what options to use with mplayer, etc. etc.  Why does Ubuntu, which is the most friendly linux I've ever used in the past 10 years, still by necessity expose these little details to me, including things like /dev/dvd links pointing to the right place?  Couldn't they properly be hidden away like other user-friendlier OSes?

Thanks
Michael

---

