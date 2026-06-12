---
title: "new /home partition but the system can't see my settings"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by ubukool on 2007-10-25
Hi there,

Can anyone please help?  I followed the psychocats tutorial for moving my /home folder to a new partition and it boots fine.  When it first booted, I got the default Ubuntu desktop, not my prefered wallpaper and other personal settings and the programs can't see my preference settings - for example, my bookmarks don't show up in Firefox, neither do the plugins I installed.  I tried

sudo chmod -R 755  /home 

to make all my files readable, but the system is still not 'reading' them and setting my personal preferences.  The settings are definitely in my /home folder because I checked after I copied them across to the new partition.

Any ideas?  Any help would be greatly appreciated.

Thanks!

:)

---

### Post by ubukool on 2007-10-25
I'm bumping this, please help

---

### Post by ubukool on 2007-10-26
Hi,

I managed to solve the problem by manually copying the .folders from my old /home folder (which is now called home_backup) to my new /home directory on a separate partition.  I've got my bookmarks  back on Firefox!  It must have been that the command I used to copy the contents of /home to the new location didn't copy everything, although it looked like it had.

This is just a note to help anyone who is having a similar problem.

---

