---
title: "Dual boot two Ubuntu versions"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by chloraldo on 2009-11-22
Hi all

I would like to dual boot two Ubuntu versions (Jaunty/Karmic). For both Ubuntu versions I want to use the same home directory so that I can access the same files from both versions.

Is that possible? How?

Thanks

---

### Post by audiomick on 2009-11-22
If you already have your /home on a separate Partition, I think this is possible. You just have to mount the existing /home partition in the new install without formatting.
If you don't have it separate already, you will have to juggle. It would involve copying /home out to another location (external HD) creating a new partition, copying /home contents into it, and remounting the new partition in the system at /home. It might mean having to re-install the old system as well as the new. Don't ask me for details, I'm sorry.

---

### Post by chloraldo on 2009-11-22
> **audiomick said:**
> If you already have your /home on a separate Partition, I think this is possible.

Thanks for your reply. My home folder has its own partition, so that should work.

Will there not be conflicts with hidden files in the home folder that are used by both versions?

---

### Post by ajgreeny on 2009-11-22
There may well be conflicts between the different versions of applications so I strongly advise you not to do things that way.

Let each ubuntu version have its own home folder or partition and then put all your documents and music and videos etc etc in to a separate partition for data.  Mount that data partition in each install using by adding a line to the /etc/fstab file of each in this form:-
```
# /dev/sda2
UUID=7a49a256-2471-45cc-9933-78b8a5bbcfe9 /mnt/data ext3 defaults,relatime 0 2
```You need not bother with your equivalent of the commented line # /dev/sda2, but I find it helps me know what the extra line is for.  Obviously use your own UUID and mountpont for the partition, but if you do it this way, make sure that the mountpoint folder is owned by you and you have read/write permissions, or you will have difficulty using it properly.  If you want an icon on the desktop, mount the partition to a subfolder of /media, not /mnt, as I show.  This is my setup and I don't want the icon but use links to the data folders from one version or distro to the other.

Incidentally to do this it will be easiest to have the same username for both versions, probably the same password would be less confusing too.  If you have different usernames you will possibly run into difficulties with ownership of files at some point.

---

### Post by raymondh on 2009-11-22
> **ajgreeny said:**
> there may well be conflicts between the different versions of applications so i strongly advise you not to do things that way.

Let each ubuntu version have its own home folder or partition and then put all your documents and music and videos etc etc in to a separate partition for data.  

+1

---

### Post by presence1960 on 2009-11-22
> **ajgreeny said:**
> There may well be conflicts between the different versions of applications so I strongly advise you not to do things that way.

Let each ubuntu version have its own home folder or partition and then put all your documents and music and videos etc etc in to a separate partition for data.  

+1

Also Hi to Raymond!

---

### Post by phillw on 2009-11-22
Thanks for the heads up on that one - I'm about to make a 'play' area for Lucid. So, I'll also make a data area for shared documents / music etc.

Cheers,

Phill.

---

