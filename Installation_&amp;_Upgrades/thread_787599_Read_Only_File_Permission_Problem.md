---
title: "Read Only File Permission Problem"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by king vash on 2008-05-09
I was playing with the chmod command and messed up my sudoers so it said sudo is in mode 777 instead of 440 

so i ran 
```
chmod 440 /etc/sudoers
```
in the emergence console. I can boot and log in but i got an error about being read only so i went back to emergence console and played around some more. the end result is i cana't boot because my entire drive is read-only with no exacutablity to anyone (including root).

what should i do?

I've found that my harddrive is mounted in errors=remount-ro mode, using the ls -l /dev/sd*

---

### Post by Aearenda on 2008-05-09
What actually happens when you try to boot in recovery mode? 
Does it show an error message? 
Is this a long-standing system that is worth recovering or is a reinstallation no big deal?

If you have to it should be possible to recover it using a CD boot and some careful command-line work to restore the permissions, but you will need to go through several stages with help from the forums and it will take a while. Reinstallation will be less complex unless you have data that is not backed up.

---

### Post by king vash on 2008-05-09
I have some critical files that i would like to recover (to my second harddrive), can i do this from the live cd or will it be more complicated than that?

I would like to restore the os as completely as possible, package list, files, settings... bookmarks. 
I don't know how much a reinstall would do, reformat and loss all data, or keep data but delete programs, or not change anything but refresh files.
Any advice on how to preceed would be nice.


KNOWLEDGE ---

My computer won't boot normally
Can boot with recovery mode
all permissions are set to -rw-rw-rw (think that's right)
Drive is loaded into errors=readonly mode
My other partition on the drive will load, and can write and read from the drive

---

### Post by Aearenda on 2008-05-09
That sounds recoverable, but I wont have the time to work out the steps with you until tomorrow afternoon - that is, about 30 hours from the time of posting this reply. 

You should be able to access your files from a liveCD by mounting the partition and using sudo.

I recommend you begin by copying essential files and the contents of /home to another safe place, before doing *anything* else.

Reinstallation affects things depending on which partition they are in. This is why many people recommend a separate partition for /home.

After reinstalling it will be reasonably straightforward to restore /home with all your settings and files.

If anyone else is confident with how to do this and wants to jump in and give a hand while I am away, that would be great.

---

### Post by Aearenda on 2008-05-11
OK, I'm back - so to begin: reboot the computer into recovery mode, and get into the command line. 
Do this:
```
ls -l /
```
and post the complete result, please.

---

