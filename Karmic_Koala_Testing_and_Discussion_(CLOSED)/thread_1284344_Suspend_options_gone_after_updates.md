---
title: "Suspend options gone after updates"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Muflon on 2009-10-06
Hi

After installing today's updates including 2.6.31-12, I no longer have the suspend options on my laptop.

Has anyone else experienced this?

Muflon

---

### Post by hvbakel on 2009-10-06
Yes, I'm having the same problems here after a reboot. I've setup my laptop to suspend on lid close, but I haven't tested yet if that is affected as well.

---

### Post by tekstr1der on 2009-10-06
I am thinking it has to do with the dbus api change noted here:

```
devicekit-power (011-1) unstable; urgency=low

  [ Michael Biebl ]
  * New upstream release.
  * debian/control
    - Add Recommends on pm-utils and policykit-1.

  [ Martin Pitt ]
  * debian/control:  This version changes the internal D-BUS API. Make library
    and daemon break each other for versions prior to 011, to avoid partial
    upgrades.

```

The corresponding g-p-m changes:
```
gnome-power-manager (2.28.0-0ubuntu3) karmic; urgency=low

  * debian/control: Bump dk-power dependencies to >= 011 to ensure that we are
    using the renamed DK-P D-Bus properties.

```

have not yet hit the repos. Looking at .xsession-errors, it's a mess of devkit errors pertaining to g-p-m. All should be well again when updated to 2.28.0-ubuntu3

---

### Post by Muflon on 2009-10-06
> **tekstr1der said:**
> 

have not yet hit the repos. Looking at .xsession-errors, it's a mess of devkit errors pertaining to g-p-m. All should be well again when updated to 2.28.0-ubuntu3

Thanks tekstr1der.  

I am reassured by your comment, although your reasoning was way above my head. :)

---

### Post by tekstr1der on 2009-10-06
Well, looks like there is more to it. After g-p-m updated package, I am still missing gui options for suspend. I am guessing that gnome-session also needs updating for the new dbus api usage.

@Muflon - Are you not able to suspend your system at all or are you simply not seeing the option to suspend in the shutdown menu? For me, suspend still works as expected via hotkey or event such as lid-closed.

---

### Post by leonardo_neo on 2009-10-07
I am experiencing the same problem after update.

---

### Post by Muflon on 2009-10-07
> **tekstr1der said:**
> 
@Muflon - Are you not able to suspend your system at all or are you simply not seeing the option to suspend in the shutdown menu? For me, suspend still works as expected via hotkey or event such as lid-closed.

My suspend options have completely gone from the system menu and the power management screen drop downs.

Muflon

---

### Post by mudi on 2009-10-07
The options are missing on my Acer Aspire One when I use the shut down menu, but if I use the suspend keystroke (Fn+F4 on mine) it suspends.

---

### Post by tjeremiah on 2009-10-07
Same problem here.

---

### Post by tekstr1der on 2009-10-07
Filed: [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/445500](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/445500)

I'm hoping this breakage is so obvious that a fix is already in the works and my report is not necessary.

---

### Post by tekstr1der on 2009-10-07
Fixed with a quickness! Never had a response like that to a bug before. Thanks to Chris Coulson:

> Chris Coulson  wrote 34 minutes ago:  	  #2

This likely needs rebuilding against latest dk-power and the build-depends bumping
Changed in gnome-session (Ubuntu):
assignee: 	nobody &#8594; Chris Coulson (chrisccoulson)
importance: 	Undecided &#8594; Medium
status: 	New &#8594; In Progress
Chris Coulson wrote 7 minutes ago: 	#3

**This is fixed now**
Changed in gnome-session (Ubuntu):
status: 	In Progress &#8594; Fix Released 

And it's currently being built:

```
gnome-session (2.28.0-0ubuntu4) karmic; urgency=low

  * No-change upload to dynamically link against libdevkit-power-gobject again
    (previous version had static linkage due to a missing dependency).

```

Should be in the repos soon!

---

### Post by tekstr1der on 2009-10-07
Confirmed this is fixed with the updated gnome-session package.

@Muflon - Did this fix your issues as well?

---

### Post by Muflon on 2009-10-07
> **tekstr1der said:**
> Confirmed this is fixed with the updated gnome-session package.

@Muflon - Did this fix your issues as well?

Yes everything is back to normal after the 105Mb of updates today.

@tekstr1der Thanks for all the help mate!

---

### Post by Luke has no name on 2009-10-07
I just did a dist-upgrade on Karmic and I didn't get any fix for this issue.

I do use the iu.edu mirror INSTEAD of us.archives.ubuntu.com; I don't know if the mirrors lag behind on uploads.

---

### Post by ozorba on 2009-10-09
And my laptop goes into suspension but I get a blank screen when it is turned back on.

---

