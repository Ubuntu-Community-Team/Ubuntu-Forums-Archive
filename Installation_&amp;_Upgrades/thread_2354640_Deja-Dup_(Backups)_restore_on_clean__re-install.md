---
title: "Deja-Dup (Backups) restore on clean / re-install"
date: 2017-03-04
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2017-03-04
Using LiveDVD ubuntu-16.04.2-desktop-amd64.iso, I reinstalled

 / 

That is to say that the / was both formatted and the / folder-files-directories were cleanly re-installed.
On running Ubuntu's "Backups" to restore my /home, Backups would not, saying there was not enough space. True enough, the reinstall has put /home and /Music etc. in the / -   Yikes! I had commanded Backups to restore to original location.

Then, I thought maybe the new / did not link up with it's old /home. I say this as reboot back to LiveDVD, run GParted shows /sda2 as having no mount point and same for /swap. So I tried to put the mount points back in but on reboot back to hard drive, they seem to be gone or /home shows in the file manager as being "there" as a device. Soooo, what do I have to do to bring the original /home and /swap onto the drive as they were before / was reinstalled? What do I tell "Backups" to restore to?

Why is Backups trying to restore to /  rather than "original locations"? I know this has to do with making a new /, but I don't know how to word a search to find a way to do this myself. Is it possible to tell /sda2 (which is /home) and /sda3 (which is swap partition) to play nice with newly minted /sda1 (which is / or root)?

Backup of all /home and /. files on /home made yesterday.

```
mark@Lexington:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=c30f96a8-29c5-4bce-87d5-e8728c2bbd9b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=27c7ef11-a0a6-4f6b-9be3-812c4aee7442 none            swap    sw 
```


I apologize for not speaking enough computerese to explain this properly. I am the endiest of end users. Thnx for reading.

---

