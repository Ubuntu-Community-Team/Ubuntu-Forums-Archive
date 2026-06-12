---
title: "system settings not working"
date: 2011-11-27
forum: Installation &amp; Upgrades
---

### Post by uhuru53 on 2011-11-27
I created a UBUNTU 11.10 bootable persistent USB on a 8GB pendrive.

After a while my settings are no more saved, I cannot change the desktop or the clock settings anymore.

So I suppose that system settings should be saved somewhere in some file.

Probably that file is read only, don't you think so?
Who could help me in finding which file the system settings are saved to?
And then, how is it possible to change read only flag?

Many thanks.

---

### Post by uhuru53 on 2011-11-30
Hello, is aybody out there?

hi

I am using ubuntu 11.10 persisten live installation on a 8GB
pendrive.

I cannot change system settings anymore.
I cannot change desktop picture neither clock settings neither
keyboward settings.

So I suppose that system settings should be saved somewhere in some file.

Probably that file is read only, don't you think so?
Who could help me in finding which file the system settings are saved to?
And then, how is it possible to change read only flag?

Many thanks.

---

### Post by efflandt on 2011-11-30
How big is your persistent data file (casper-rw) and how much RAM do you have? The casper-rw file is actually an ext2 file system that is loop mounted.

How often or why do you keep changing system settings?

Certain things that happen during boot cannot be updated or changed (like kernel or video drivers unless you remaster the original iso) because much of that happens from a fixed squashfs file before persistent data is mounted.

You might try configuring a different user in the live system (than "ubuntu") with password and see what happens for that user.

---

### Post by uhuru53 on 2011-12-02
> **efflandt said:**
> How big is your persistent data file (casper-rw) and how much RAM do you have? 

My RAM is 1GB, my casper-rw is... I don't know, how could I find it?

> **efflandt said:**
> 
The casper-rw file is actually an ext2 file system that is loop mounted.

How often or why do you keep changing system settings?




I try every day to change system settings, but I never change them since I cannot change them. This is my problem: I CANNOT change system settings.


> **efflandt said:**
> 
Certain things that happen during boot cannot be updated or changed (like kernel or video drivers unless you remaster the original iso) because much of that happens from a fixed squashfs file before persistent data is mounted.

You might try configuring a different user in the live system (than "ubuntu") with password and see what happens for that user.

I did it. I could create a new user, I set it up as administrator and then I logged in as the new user. Eventually I could change desktop and other settings! Unfortunately I lost all Firefox settings :-(
But I sync them again.
Many thanks.

---

