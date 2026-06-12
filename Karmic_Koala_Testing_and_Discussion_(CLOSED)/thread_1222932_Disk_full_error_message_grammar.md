---
title: "Disk full error message grammar"
date: 2009-07-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by durand on 2009-07-25
Does anyone else get the weird quotes with the disk full error message? I don't think it's my font because I'm using the ubuntu default. Screenshot attached.

I just want to make sure before posting a bug report.

---

### Post by twisted_steel on 2009-07-25
It looks like the initial quote is set in the translation files for gnome-settings-daemon.

Check out line #742
[http://git.gnome.org/cgit/gnome-settings-daemon/tree/po/en_GB.po](http://git.gnome.org/cgit/gnome-settings-daemon/tree/po/en_GB.po)

The actual quotes around the disk name are set in the language files.  If you look at Finnish (fi), it uses double quotes.  Several of the other languages - Spanish (es), German (de), etc - use chevrons instead.

---

### Post by durand on 2009-07-25
Interesting, I'll contact the GB translator then.
Thanks!

---

### Post by durand on 2009-07-25
Okay, bugged. It's here if anyone cares: [http://bugzilla.gnome.org/show_bug.cgi?id=589729](http://bugzilla.gnome.org/show_bug.cgi?id=589729)

---

### Post by mpt on 2009-07-26
> **durand said:**
> Okay, bugged. It's here if anyone cares: [http://bugzilla.gnome.org/show_bug.cgi?id=589729](http://bugzilla.gnome.org/show_bug.cgi?id=589729)

Since that bug report has been marked as obsolete, you should retest in Karmic if/when it is using DeviceKit-disks. If you have a similar problem, [report a bug on the devicekit-disks package]("https://bugs.launchpad.net/ubuntu/+source/devicekit-disks").

See also [my design for a more informative warning]("http://live.gnome.org/LowDiskSpaceWarning").

---

### Post by chrisccoulson on 2009-07-26
> **mpt said:**
> Since that bug report has been marked as obsolete, you should retest in Karmic if/when it is using DeviceKit-disks. If you have a similar problem, [report a bug on the devicekit-disks package]("https://bugs.launchpad.net/ubuntu/+source/devicekit-disks").

See also [my design for a more informative warning]("http://live.gnome.org/LowDiskSpaceWarning").

mpt - I've already implemented your design in Karmic (which is why the upstream report was closed as obsolete)

---

### Post by durand on 2009-07-26
> **chrisccoulson said:**
> mpt - I've already implemented your design in Karmic (which is why the upstream report was closed as obsolete)

When was it implemented? And how exactly would I test it?

---

### Post by chrisccoulson on 2009-07-26
It's in the latest version of gnome-settings-daemon in Karmic (2.27.4-0ubuntu1). And to test it, you can tweak the GConf keys in /apps/gnome_settings_daemon/plugins/housekeeping

---

### Post by durand on 2009-07-26
Ok, I'm not really sure what values to change but I'd only asked because I haven't seen any updates gnome-settings-daemon in the last two days.

Hmm, the error just popped up as I was typing so it was closed before I had a chance to properly look at it though it did still look like the old version..

---

### Post by wayne_cat on 2009-07-26
The last gnome-settings-daemon update was 2.27.4-0ubuntu1 - 07.24.2007

---

### Post by durand on 2009-07-26
Which was before I posted my screenshot and I was fully up to date :S

---

### Post by chrisccoulson on 2009-07-26
> **durand said:**
> Which was before I posted my screenshot and I was fully up to date :S

Up-to-date according to which mirror? What version of gnome-settings-daemon do you have? You can't have the latest version, otherwise the warning would look like the attached screenshot

---

### Post by durand on 2009-07-26
I'm using the GB mirror.

> The last gnome-settings-daemon update was 2.27.4-0ubuntu1 - 07.24.2007

Thats the latest version according to synaptic and its the same one as I have. (except that it was released in 2009 :P)

I'm sure it will appear at some point.

---

### Post by wayne_cat on 2009-07-26
> **durand said:**
> I'm using the GB mirror.



Thats the latest version according to synaptic and its the same one as I have. (except that it was released in 2009 :P)

I'm sure it will appear at some point.

silly me ... to stupid to copy & paste :D

---

### Post by chrisccoulson on 2009-07-26
> **durand said:**
> I'm using the GB mirror.



Thats the latest version according to synaptic and its the same one as I have. (except that it was released in 2009 :P)

I'm sure it will appear at some point.

Have you logged out since you updated to it?

---

### Post by durand on 2009-07-26
I think so. I'll try again.

---

### Post by chrisccoulson on 2009-07-26
You can't have logged out after you upgraded, as you wouldn't see the dialog in your screenshot - that code has been completely removed from the new version (including the use of libnotify from this plugin), so it would be impossible for it to appear now with the new version.

---

### Post by durand on 2009-07-26
You were right. I guess I updated a while after the package came out..The new error message looks great!

---

### Post by chrisccoulson on 2009-07-26
Thanks, that's good:)

---

### Post by zekopeko on 2009-07-26
What is the space remaining threshold on this warning?

---

### Post by chrisccoulson on 2009-07-26
> **zekopeko said:**
> What is the space remaining threshold on this warning?

It's configurable. By default, it will show if there is less than 5% free space AND the free space is less than 2GB.

It will also show again if the free space decreases by a further 1% (by default) after the last warning, but not more often than every 10 minutes (configurable too)

---

### Post by mpt on 2009-07-28
> **chrisccoulson said:**
> mpt - I've already implemented your design in Karmic (which is why the upstream report was closed as obsolete)

Cool, thank you!

---

