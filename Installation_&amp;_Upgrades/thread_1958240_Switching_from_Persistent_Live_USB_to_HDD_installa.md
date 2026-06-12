---
title: "Switching from Persistent Live USB to HDD installation but..."
date: 2012-04-13
forum: Installation &amp; Upgrades
---

### Post by SketchMan3 on 2012-04-13
**Is there a user friendly way to keep all of the applications, files, settings, etc... that I've accumulated on the persistent live usb over the past year?**

I've been running off an 8gb (but only using 4 gigs of that space, ya know) live usb of ubuntu 10.10 for the past year because my hard drive burned out and I was feeling adventurous. It was supposed to be temporary, but it grew on me until I'd all but filled up the entire disc with my creative endeavors, and using it as heavily as I'd use a traditional desktop setup.

[SIZE=1]It's been fun, but not being able to update anything (tried it once, before I realized it was filling up space that I'd never be able to recover) has hampered me a bit. Also, quite often I'd put too much of a strain on FireFox, and cause it to freeze my computer, requiring a hard reset. 

Over time I noticed every time I had to hard reset it, I'd lose a bit of storage. Found out my logs, crash logs, apt cache, thumbnails, etc... were filling up the memory. I cleared all that, optimized it not to fill up those things past a certain point. It worked for a while, but now, with (apparently) none of those things taking up space, I keep losing storage anyway. I assume it's my USB drive dying, so I'm ready to move on back to hard drive.[/SIZE]

[B]So, is there a fast and easy way to install Ubuntu onto a hard disk from a Persistent Live USB, along with the applications, settings, and personal files that I have stored on that USB? Or, if not, is there an automated way to make a list of all the applications that I have installed so I can reinstall them (I deleted all the cached packages for space)?

[/B]I'm ping-ponging between 5mb and 25mb, as I lose space and delete or move items to an external storage device to recover that space. I'm running out of things to delete, lol.

---

### Post by SketchMan3 on 2012-04-15
I'd really appreciate it if somebody would chime in.

---

### Post by Herman on 2012-04-15
There is a program called simple backup and another called simple restore I tried out a long time ago that worked well.
EDIT: I can't guarantee it will work well with a persistence install though, I only use those for their Live CD Installers.

 Normally I prefer to just do things the old fashioned, manual way. I just copy and paste my user files to the new installation. There are options in Firefox and some other programs for 'exporting' and 'importing' bookmarks or the like.

For your software maybe this link will help, [Linux Get List of Installed Software for Reinstallation / Restore All the Software Programs]("http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html") - nixcraft.

If you're changing to a new installation that's the same architecture (i386/amd64) and same version of Ubuntu you can copy the contents of /var/cache/apt/archives/ across and that will probably save you a lot of downloading time, as the .deb files are stored in there.

---

### Post by SketchMan3 on 2012-04-15
> **Herman said:**
> There is a program called simple backup and another called simple restore I tried out a long time ago that worked well.
EDIT: I can't guarantee it will work well with a persistence install though, I only use those for their Live CD Installers.

 Normally I prefer to just do things the old fashioned, manual way. I just copy and paste my user files to the new installation. There are options in Firefox and some other programs for 'exporting' and 'importing' bookmarks or the like.

For your software maybe this link will help, [Linux Get List of Installed Software for Reinstallation / Restore All the Software Programs]("http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html") - nixcraft.

If you're changing to a new installation that's the same architecture (i386/amd64) and same version of Ubuntu you can copy the contents of /var/cache/apt/archives/ across and that will probably save you a lot of downloading time, as the .deb files are stored in there.
Thanks so much! That looks just like what I need. And yes, it is the same architecture and same version. However, I already deleted all my apt archives to save disk space, lol. Thanks for the response.

---

