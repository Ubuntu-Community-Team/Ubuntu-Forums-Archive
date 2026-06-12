---
title: "Reinstall Ubuntu without formatting the partition?"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by Starlight on 2006-10-28
Hi :)

When I tried to upgrade Ubuntu today, something went wrong, and my Ubuntu is totally unusable now... But I still have my personal files, emails, bookmarks and some other stuff there. Is it possible to reinstall the Ubuntu system from the CD, but without formatting the partition, so that it would keep my home directory without deleting anything there? Or do I have to backup the home directory on my Windows partition and then copy it to Ubuntu after I reinstall it?

---

### Post by DaveBorealis on 2006-10-28
> **Starlight said:**
> Is it possible to reinstall the Ubuntu system from the CD, but without formatting the partition
This is possible.  Just go with the partitions already on the disk during installation.
> Or do I have to backup the home directory on my Windows partition and then copy it to Ubuntu after I reinstall it?
If your home directory is on the same partition as root ('/'), then yes, you'll lose your info reinstalling.

Either way, I would definitely load the live CD, mount the partition with your home directory, and backup/save anything of value.  You can mount a memory stick and save it there (my first choice), or perhaps save it to the Windows NTFS partition, but I'm not sure if this is possible other than by opening things such as text files and resaving them as text files in Windows.  (Anyone know if Linux can RELYABLY mount and save to NTFS nowadays?)

---

### Post by Starlight on 2006-10-28
I don't have any NTFS partition... my Windows partition is FAT32... and I don't really have anything else where I could backup my home directory, so I'll just pack it and copy to the Windows partition. I don't have any separate partitions for root and for home...

does it mean that it will delete my home directory even if I don't format the partition?

---

