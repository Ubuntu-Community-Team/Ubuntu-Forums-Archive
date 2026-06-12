---
title: "Videos only run as Root?????   This sux."
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by myke on 2007-10-23
A while back I posted about my upgrade problem with Gutsy.  Everything upgraded fine but all videos, no matter what format (.avi .mpeg .wma, etc.) would cause whatever program I used to open them to freeze immediately (kaffeine, totem, mplayer).   Could NOT figure out what was causing it.

Still can't.

However, I did discover that after giving my root id login access for into Gnome that all videos work for the root ID.  Not a problem.  Smooth as silk.  So I thought maybe I messed up something with my other ID. Some setting.  Not that I had did much as it was a fresh upgrade.   So I created a new user.  Hey, guess what?  That user can't open any videos either.   

SO WHY CAN ONLY THE ROOT USER RUN VIDS AND NO NORMAL USER ID CAN????

I really have to agree that Ubuntu upgrades really suck.  I've been around faithfully since Breezy and every single upgrade has always been a mess and led to a fresh install.

---

### Post by ruibernardo on 2007-10-24
Hi myke,

I'm guessing here, but if you executed files with sudo, their configuration files might be owned by root now. If it is the case, search for files owned by root in your personal folder inside ~/.vlc or ~/.gstreamer-0.10 and the others.

---

### Post by myke on 2007-10-24
Thanks for the response.  I tried that but to no avail.  I did pull up the 'group' file from the 'etc' folder and discovered my user id was on none of the groups.   I added myself to all necessary groups and logged out, restarted my system.  Still nothing.   And I discovered all of my music files won't open either in my id.  Only in root.  Same as the videos, doesn't matter what program, it just freezes and has to be forced to shut off.

I'm to the point of doing a clean install .... again.

---

### Post by pguedes on 2008-06-02
> **myke said:**
> Thanks for the response.  I tried that but to no avail.  I did pull up the 'group' file from the 'etc' folder and discovered my user id was on none of the groups.   I added myself to all necessary groups and logged out, restarted my system.  Still nothing.   And I discovered all of my music files won't open either in my id.  Only in root.  Same as the videos, doesn't matter what program, it just freezes and has to be forced to shut off.

I'm to the point of doing a clean install .... again.

SOLVED!!!!

If your VLC Player only runs on ROOT, Simply do this:

-Go do /home/root/.vlc

Copy "vlcrc", and "plugins-04041e.dat"(this one inside the Cache Subdirectory), to your regular user's .vlc Directories. Replace the existing files if necessary.

It worked Like a Charm to ME!

Note to Newbies: .vlc is a hidden directory

I Had this problem after changing the Main interface preferences to WXWigets.

---

