---
title: "Only root Can Read NTFS Partition (Solved)"
date: 2005-11-08
forum: Installation &amp; Upgrades
---

### Post by Ubuntist on 2005-11-08
I have an NTFS partition which contains Windows XP; here's the relevant fstab line:

/dev/hdc1       /media/hdc1     ntfs    defaults        0       0

The trouble is that /media/hdc1 can only be read by root.  For a normal user, it's "Permission denied," which isn't surprising since the permissions of hdc1 are

dr-x------  1 root root 12288 2005-11-08 10:17 hdc1

While logged in as root, I've tried chmod 644 and chmod 444, but the result is

chmod: changing permissions of `hdc1': Read-only file system

How can I read hdc1 when logged in as a normal user?

Another puzzle: /media also contains a directory called windows, which is empty.  Where did this come from?

---

### Post by adwait on 2005-11-08
try adding the word "user" after "defaults".

---

### Post by shinygerbil on 2005-11-08
Or you can add the option umask=0000 to the end of the line :)

Steve

---

### Post by Pablo_Escobar on 2005-11-08
[QUOTE=shinygerbil]Or you can add the option umask=0000 to the end of the line :)

Steve[/QUOTE]
With NTFS it's umask=0222 :)
umask=0000 is for the FAT ones :D

make it look like:
/dev/hdc1     /media/hdc1     ntfs    nls=utf8,umask=0222 0       0

---

### Post by earobinson on 2005-11-08
nm

---

### Post by Ubuntist on 2005-11-09
Thanks to all -- I can now read the NTFS partition as a non-root user.

Now a similar problem with the FAT32 partition I've created specifically for exchange of files between XP and Ubuntu.  Its fstab entry was originally

  /dev/hdc7       /exc            vfat    default  0       0

but that wouldn't let me write to it from Ubuntu as a non-root user.  Then I tried

  /dev/hdc7       /exc            vfat    nls=utf8,umask=0000  0       0

but that doesn't work either.  In fact, it causes an error message during boot-up.  What would be the correct fstab entry?

---

### Post by Pablo_Escobar on 2005-11-09
Try :

/dev/hdc7       /exc  vfat    iocharset=utf8,umask=000


PS. It's a good custom to keep mounted partitions in /media, but that's entirely up to You :)

---

### Post by Ubuntist on 2005-11-09
OK, I've tried

/dev/hdc7       /media/exc      vfat    iocharset=utf8,umask=000  0       0

but still no joy -- error message and /media/exc is not to be found anywhere.  Any other suggestions?

---

### Post by Pablo_Escobar on 2005-11-09
Did you create /media/exc directory ?

If not "sudo mkdir /media/exc".
then "sudo umount -a"
then "sudo mount -a"
and see if it's ok.

---

### Post by Ubuntist on 2005-11-09
No, there is no /media/exc.

"sudo mkdir /media/exc" works fine and creates /media/exc.

When I try "sudo umount -a", the result is

umount:  /dev:  device is busy
umount:  /home:  device is busy
umount:  /:  device is busy

---

### Post by Pablo_Escobar on 2005-11-09
That's normal, umount doesn't unmount devices which are in use.
Now just "sudo mount -a" and You should be set :)

---

### Post by Ubuntist on 2005-11-09
Good -- the primary problem is solved.  /media/exc is available and writeable from Ubuntu.  And thanks for teaching me the umount/mount trick -- it's a lot quicker than rebooting!

During boot-up, however, there is an error message like this:

FAT: utf8 is not a recommended character set for FAT systems

and then it goes on to say something about how file names will be case sensitive.  Anything I can do about that?

I don't know if it's relevant, but during boot-up, I also get a message saying:

[4294867.607000] drivers/usb/input/hid-cor.c: usb_submit_urb(ctrl) failed

Is that anything to worry about?

---

### Post by Ubuntist on 2005-11-09
I think I've answered my own question -- I've deleted the "iocharset=utf8" part of the fstab entry for the FAT32 partition, and the warning about the character set disappears.

Thanks for all the patient help, Pablo -- you're a star!

---

