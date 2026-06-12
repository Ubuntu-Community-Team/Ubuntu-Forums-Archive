---
title: "First login has access denied for everything"
date: 2005-08-07
forum: Installation &amp; Upgrades
---

### Post by eviljester on 2005-08-07
OK, I installed Ubuntu 5.0.4. just now on a machine with the following specs:

AMD 64 processor
2 hard drives - 1 SATA master and 1 IDE slave
Pre-existing Windows XP on SATA master and pre-existing Fedora 2 on IDE slave (/hda2 IIRC) + pre-existing remains (ie. no system files or critical files) of a Windows 2000 on the same IDE slave (hda1 IIRC)

During the install, I had Ubuntu format the Fedora 2's system partition and turned it to a "/tmp" partition. Ubuntu itself formatted the hda1 partition to make it it's root.

The install went fine, though Ubuntu had me manually correct the former Fedora's /home partition which was riddled with inode and free block errors. When it was done, it booted nicely.

I got the Ubuntu login screen along with the drum sound. When I tried to log in with my user name and password, it immediately terminated the session. The log file said that gnome had tried to create a ".gnome2" directory, but was denied permission. I tried logging in with the other settings (same result) and finally the terminal and found that it was also read-only (typing "nano", for example, got me the permission denied message).

From what I remember from my meagre 2 years of Linux experience, it seems to me that the partitions have been mounted read-only. Could this be true and if yes, what should I do next?

---

### Post by roland on 2005-08-07
[QUOTE=eviljester]OK, I installed Ubuntu 5.0.4. just now on a machine with the following specs:

AMD 64 processor
2 hard drives - 1 SATA master and 1 IDE slave
Pre-existing Windows XP on SATA master and pre-existing Fedora 2 on IDE slave (/hda2 IIRC) + pre-existing remains (ie. no system files or critical files) of a Windows 2000 on the same IDE slave (hda1 IIRC)

During the install, I had Ubuntu format the Fedora 2's system partition and turned it to a "/tmp" partition. Ubuntu itself formatted the hda1 partition to make it it's root.

The install went fine, though Ubuntu had me manually correct the former Fedora's /home partition which was riddled with inode and free block errors. When it was done, it booted nicely.

I got the Ubuntu login screen along with the drum sound. When I tried to log in with my user name and password, it immediately terminated the session. The log file said that gnome had tried to create a ".gnome2" directory, but was denied permission. I tried logging in with the other settings (same result) and finally the terminal and found that it was also read-only (typing "nano", for example, got me the permission denied message).

From what I remember from my meagre 2 years of Linux experience, it seems to me that the partitions have been mounted read-only. Could this be true and if yes, what should I do next?[/QUOTE]
 You could try to log in as root, and check the permissions on the /home directory, by typing ls -l in a terminal. If the permissions of the directories there show up normally, so for example the dir "eviljester" has permissions drwx------, then the partitions could really be mounted read-only. Time to check the /etc/fstab file, by opening it in a text editor. (back up the file first!!) There should be a line like this:

```
/dev/hda1      /      defaults      0  0
```

You should check if the "defaults" on that line really are "defaults", and there is no "ro" before or after the word "defaults". If "ro" is there, you should remove it and save the file. Like you may have guessed, ro means read-only.

That is all I can think of, I hope it works. Gnome takes drastic measures if something doesn't go like it should....

---

### Post by eviljester on 2005-08-07
Well, as I rebooted, I got a glimpse of the kernel being mounted as "ro", so it seems you were right. So I logged in with the terminal as root and checked out /etc/fstab and behold: hda1 was being mounted as "errors=remount ro"... OK, so I deleted the "errors=remount ro" part and rebooted.

It's still read-only. Could the "errors=remount" be the key, as in the partition's filesystem has errors? At least that's what a quick googling told me.

When I installed Ubuntu, it formatted the damn hda1 itself, so if there are any errors, I can see only one culprit. :)

Thoughts?

---

### Post by roland on 2005-08-07
[QUOTE=eviljester]
It's still read-only. Could the "errors=remount" be the key, as in the partition's filesystem has errors? At least that's what a quick googling told me.[/QUOTE]

I also think that your partition contains some errors.. You could try to run fsck (**f**ile **s**ystem **c**hec**k**) to check the fs for any errors. In this case it is just [font=courier]fsck /dev/hda1[/font], but please read the manpage on this ([font=courier]man fsck[/font] in a terminal).

---

### Post by Gezzer on 2005-08-07
[QUOTE=][/QUOTE]
 if this is a new install it maybe worth reinstalling using the custom partition option

delete the partitions u have already
then set the 1st partition to swap @ the size of your installed memory (primary)
then the rest to / (primary)

then follow the rest of the install instructions ...

---

### Post by roland on 2005-08-07
[QUOTE=Gezzer]if this is a new install it maybe worth reinstalling using the custom partition option[/QUOTE]

I was actually thinking of that, although I waited to tell. I first wanted to hear how my first post worked out, and use this advice if nothing else worked. Your solution always works out fine, of course :)

---

### Post by eviljester on 2005-08-09
[QUOTE=Gezzer]if this is a new install it maybe worth reinstalling using the custom partition option

delete the partitions u have already
then set the 1st partition to swap @ the size of your installed memory (primary)
then the rest to / (primary)

then follow the rest of the install instructions ...[/QUOTE]

Hmm.. I tried that and now the second partition (with kernel) is read-only. It seems that wherever I put the / partition, it becomes faulty. So now I suspect it's installed in a faulty way. I probably have to post a log file of the install process, right? (*cough* I can't seem to remember how you get that log *ahem*)

ROLAND: I'd like to run fsck on kernel, but I'd need to do it before it is mounted. However, don't I need to mount kernel anyay before I can even run fsck?

Here's an obligatory stupid smiley:  ](*,)

---

### Post by roland on 2005-08-09
[QUOTE=eviljester]Hmm.. I tried that and now the second partition (with kernel) is read-only. It seems that wherever I put the / partition, it becomes faulty. So now I suspect it's installed in a faulty way. I probably have to post a log file of the install process, right? (*cough* I can't seem to remember how you get that log *ahem*)

ROLAND: I'd like to run fsck on kernel, but I'd need to do it before it is mounted. However, don't I need to mount kernel anyay before I can even run fsck?

Here's an obligatory stupid smiley:  ](*,)[/QUOTE]

I forgot about that the partition to check must be unmounted. I actually have no idea what could have happened, maybe you can post your [font=courier]/var/log/messages[/font] logfile, please note that it could be a (very) large file.

---

