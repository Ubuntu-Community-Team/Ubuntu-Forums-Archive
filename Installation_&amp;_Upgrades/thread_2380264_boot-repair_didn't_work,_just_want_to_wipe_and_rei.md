---
title: "boot-repair didn't work, just want to wipe and reinstall from USB"
date: 2017-12-15
forum: Installation &amp; Upgrades
---

### Post by clone29 on 2017-12-15
So, the background is this: I'm a new Linux user (3-4months now, love it :) ) and I chose to encrypt my system (overwriting free space). Ran great for awhile, I think I just cluttered it up messing around learning about it. Yesterday I tried something on a whim, and it didn't work out. I ran sudo nautilus and when the file manager opened, I right-clicked Computer > Properties > Permissions and mucked around where I shouldn't have lol. Completely messed it up. 

So I'm attempting to reformat and reinstall 16.04.03 from a live USB. I still want it encrypted in the same way as before, so I'm selecting those options during install. Choosing to "Clear disk and reinstall" (sorry might not be exact, but hopefully you recognize it) rather than "Do something else" (or whatever). I also ran boot-repair, and came back with this - [http://paste.ubuntu.com/26187216/](http://paste.ubuntu.com/26187216/)

I don't know what I'm doing. I appreciate the help.

---

### Post by Hodor on 2017-12-15
If it's not a dual boot and you don't want to save / recover anything, erase everything and install Ubuntu is the way to go.
If you have another os on the machine you want to keep (e.g. Windows), or some data to recover you should not choose that.
Hope that helps.

---

### Post by Darth4212 on 2017-12-15
Your best bet would be to find a separate computer and install Ubuntu on a external USB and run through the install process and  when you reach the point where it tells you to make partitions, wipe all of the current existing partitions and it should install perfectly fine.

---

