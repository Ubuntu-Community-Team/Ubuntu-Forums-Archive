---
title: "NTFS partition with encrypted folders"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by mkulon on 2011-05-13
I used Windows XP's encryption to encrypt some folders on an NTFS Hard Drive.

Upon mounting this drive in ubuntu, I can see all folders, and all file names, but I cannot open the contents of the encrypted files, getting "Permission Denied" despite all permissions being -rwxrwxrwx.

Is there a way to open these from linux?  I know the Windows XP login / encryption password.

---

### Post by wilee-nilee on 2011-05-13
> **mkulon said:**
> I used Windows XP's encryption to encrypt some folders on an NTFS Hard Drive.

Upon mounting this drive in ubuntu, I can see all folders, and all file names, but I cannot open the contents of the encrypted files, getting "Permission Denied" despite all permissions being -rwxrwxrwx.

Is there a way to open these from linux?  I know the Windows XP login / encryption password.

Not sure if this is safe but I install nautilus-gksu, this gives you a right click run as admin.

This is Linux admin and I have no clue as to an effect on a windows encryption if it works (**use your own common sense here**). It is great though in the Linux setup as instead of opening nautilus in root you can open individual packages, best thing since sliced bread I think.;)

---

### Post by mkulon on 2011-05-13
This is unrelated to being root.  I get the same behavior regardless of being root or not.  My question boils down to: can linux understand NTFS-encrypted files, and if so, how to open these?

---

### Post by wilee-nilee on 2011-05-13
> **mkulon said:**
> This is unrelated to being root.  I get the same behavior regardless of being root or not.  My question boils down to: can linux understand NTFS-encrypted files, and if so, how to open these?

My mistake I guess you mentioned all permissions.

You may have problems getting help though, even though this may be your computer and your files, it is information on getting to encrypted folders across an OS, technically teetering on info restricted on posting on this forum. I don't care, I just don't know how obviously, and would let you know if I did.

---

