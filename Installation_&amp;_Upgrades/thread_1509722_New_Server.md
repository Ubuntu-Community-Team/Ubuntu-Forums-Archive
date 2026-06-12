---
title: "New Server"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by Spoony_Man on 2010-06-14
I'm currently running Lucid Server of an old machine with a few extra HDDs in as a file/media server... I have managed to procure a faster machine (as my current one is only a 2.0GHz with 256MB RAM) is there any easy way to save all my settings/software/configuration and move it all to the new machine?

I will be using a fresh install on the new machine and my current plan to ensure I have the right packages is:

- make an a list of installed packages:
```
dpkg --get-selections > installed-software
```
- then this command use on the new box
```
dpkg --set-selections < installed-software
```

But I'm not really sure where to start for software configurations... I was thinking of copying/pasting the contents of /etc/ but I'm not sure how well this will work?

Any help suggestions on easier/better ways to do this would be much appreciated.

---

### Post by amauk on 2010-06-14
have a look at clonezilla
it's a livecd designed to clone a system across different hardware

I've not used it personally,
but I'm sure others here have

---

### Post by Spoony_Man on 2010-06-14
I've looked at the Clonezilla website, and it appears (correct me if I'm wrong) that Clonezilla is for backup/restoration... I don't think this will work in my case as I am changing machine and all the hardware will be different.

---

### Post by amauk on 2010-06-14
different hardware shouldn't matter
(all drivers are in linux anyways)

You can make it easier by re-using your existing disk drive(s), in which case just put the old disks in the new case and boot off of them
but I'm guessing you want to use new drives

You just need to clone your partition,
then restore the disk image on a new drive

I'd advise putting your old disk in the new machine (as well as your new disk)
then booting to clonezilla, and cloning old disk to new disk

As I said, I've never actually done this myself
but I don't see any reason for it not to work

You may have to let grub know about the change
but that's about the only config change you should need to make

---

### Post by amauk on 2010-06-14
see here
[http://ubuntuforums.org/showthread.php?t=1074358](http://ubuntuforums.org/showthread.php?t=1074358)

---

### Post by Spoony_Man on 2010-06-15
> **amauk said:**
> You can make it easier by re-using your existing disk drive(s)

Sweet!

Thanks very much for your help, I presumed that moving the HDD would cause problems... Clearly ubuntu = win.

---

### Post by amauk on 2010-06-15
you may need to reinstall grub
but the OS itself will move between different hardware no issues

---

### Post by Spoony_Man on 2010-06-15
I've moved the HDD with ubuntu on it to the new machine and have an interesting problem...

When I boot from cold I receive the following error:

DISKBOOT FAILURE, INSERT SYSTEM DISK AN PRESS ENTER

However if I go into the BIOS and restart (without making any changes) grub loads correctly and the system boots. I have tried reinstalling/updating grub with no success :(

---

### Post by amauk on 2010-06-15
This should solve it

this will show you how to reinstall grub
(the "9.10 and beyond" bit)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Spoony_Man on 2010-06-16
I've tried everything suggested to reinstall grub with no luck. I think it's a bios problem since it appears the HDD isn't being detected... Although as soon as I manually tell the BIOS to detect the HDD it finds it!

---

### Post by Spoony_Man on 2010-06-16
I've sorted the problem now. I THINK that it was because I was using an IDE cable with two plugs and only 1 HDD, by adding the second drive the bios found both drives and it booted properly...

---

