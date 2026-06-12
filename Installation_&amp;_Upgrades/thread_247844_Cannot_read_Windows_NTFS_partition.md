---
title: "Cannot read Windows NTFS partition"
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by linuts on 2006-08-31
Hi to all, Well i managed to install Ubuntu 6.06 with no dramas...I used the default install I.E. just a "swap" and "/" partitions.

Grub works o.k. can boot into both Windows XP and Linux...I even got Automatix downloaded and working:D .

I have installed Ubuntu on to its own HDD (hdb) and put GRUB into the MBR. But i cannot view my Windows disk when using Ubuntu.. the Installer has put it in an odd (to me) place.../tmp/disks-conf-hda1
and when i browse that folder the disk is locked...I.E. it says i do not have the right permmisions to view it...even though i do a "sudo"

Is there a way i can view my XP drive without having to do a reinstall??

Cheers
linuts

---

### Post by Iowan on 2006-08-31
Somewhere around here is a HowTo on unmounting/re-mounting NTFS partitions via **fstab**.  I'll see if I can find it...

---

### Post by Jason.TJ.Johnson on 2006-08-31
I'm interested in this as well. Thanks for looking.

---

### Post by tommyg on 2006-08-31
i think i got it...

Open the disk management tool:
System --> Administration --> Disks

Disable the current instance of your NTFS partition.

Open a terminal and edit /etc/fstab:
sudo nano /etc/fstab

remove the line that mounts your NTFS filesystem and replace it with:

```
/dev/hda1     /mount/point/you/want     ntfs     user,umask=0222     0     0
```

( obviously, "/dev/hda1" should be replaced with whatever disk/partition your ntfs filesystem is on.  also, substitute the mount point you wish for "/mount/point/you/want" )

Save your change... ^o
Exit nano... ^x

go back to System --> Administration --> Disks.  The mount point you put in fstab should be listed as the access path.  You should disable the partition again and then re-enable it.  Then you should have read-only access to your NTFS partition at the mount point you entered in fstab.

Hope this helps... it worked for me.  And i hope y'all can follow my hastily-typed ( and perhaps half-assed ) instructions . ;)

---

### Post by Jason.TJ.Johnson on 2006-08-31
Worked for me like a charm...

One word I'd like to add though, the path should not contain any spaces.
(I ran into that problem.)

But thanks a lot for your help!

---

### Post by tommyg on 2006-08-31
> **Jason.TJ.Johnson said:**
> Worked for me like a charm...

One word I'd like to add though, the path should not contain any spaces.
(I ran into that problem.)

But thanks a lot for your help!It might work if your fstab entry looked like:

```
/dev/hda1     "/path/to your/mount/point"     ntfs     user,umask=0222     0     0
```

maybe... i haven't tried it.  someone correct me if i'm wrong ;)

---

### Post by Jason.TJ.Johnson on 2006-08-31
> **tommyg said:**
> It might work if your fstab entry looked like:

```
/dev/hda1     "/path/to your/mount/point"     ntfs     user,umask=0222     0     0
```

maybe... i haven't tried it.  someone correct me if i'm wrong ;)
Well my mount point ended with "NTFS HDD" and if I disabled the mount it wouldn't re-enable. Also, when I browsed (without disabling first" it would tell me something along the lines of "cannot find folder: NTFS" and would not include the "HDD" portion which made me think that removing the space between them to end up like "NTFSHDD" would solve it, and it did...

---

### Post by linuts on 2006-08-31
Thanks for the replies.... i checked my fstab and there is no mention of any Windows drive (hda or hda1).... i am wondering if this is because i put Ubuntu on a second drive and the Grub in the MBR of my 1st drive (C:)

when i look at System--->Administration--->Disks there is an icon that says "Local Disk" and its the same size as my Windows disk...but wont let me browse or open the disk...says i dont have enough permissions and only "root" can open it.

The strange thing is that when i installed Ubuntu i was only asked for a user name and password... nothing for an admin or Root password....as such when i try to login as Root i cannot as i dont have a password.

My Installation was from a Live cd...I.E. booted from the Live cd  
then when Ubuntu was loaded used the Install from the desktop shortcut.

cheers
linuts

---

### Post by linuts on 2006-08-31
O.K. I can now read my XP disk...:p  I put this in my fstab....

/dev/hda1     /mount/point/you/want     ntfs     user,umask=0222     0     0

then i did an system update and rebooted... thank you to all who helped.:D 

cheers
linuts

---

