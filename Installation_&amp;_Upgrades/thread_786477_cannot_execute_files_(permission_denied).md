---
title: "cannot execute files (permission denied)"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by hemi86 on 2008-05-08
Hi!

If i try to execute a file located on my ntfs partition, i always get a "bash: ./file: Permission denied" error, even though i have the permission to execute it.

ls says:

```

-rwx------ 1 92334 2008-05-07 17:09 file

```

if i copy the file into my home dir, it works...


Any ideas?

Thank you!

---

### Post by Herman on 2008-05-08
```
chmod 770 file
```See if that fixes it.

Regards, Herman :)

---

### Post by hemi86 on 2008-05-08
no, unfortunately not.

the chmod cmd does not even effect the file... still -rwx------

Might it be a problem with the "file-rights-something-related-to-ntfs"?

---

### Post by joselin on 2008-05-08
I think that is probably an issue with perms in the partition. You must start having a look at /etc/fstab.

[This is a howto about that file]("http://www.tuxfiles.org/linuxhelp/fstab.html").

Hope that can help.

---

### Post by lewis1711 on 2008-05-08
I'm not sure if the permission of the directory overwrites the position of the file in that directory, but that could be the issue.

---

### Post by Herman on 2008-05-08
> no, unfortunately not.

the chmod cmd does not even effect the file... still -rwx------

Might it be a problem with the "file-rights-something-related-to-ntfs"? Sorry, I thought you meant you have it copied into your home dir. Is that right? ...and chmod doesn't affect it?

I wonder if it has security attributes set on it from Windows. Are you dual booting? I presume so or you wouldn't be likely to want an NTFS partition in the first place. What if you boot into Windows and run attrib -s -h -r on it then? That would relax any Windows file permissions on it.

---

### Post by hemi86 on 2008-05-08
> **joselin said:**
> I think that is probably an issue with perms in the partition. You must start having a look at /etc/fstab.

[This is a howto about that file]("http://www.tuxfiles.org/linuxhelp/fstab.html").

Hope that can help.

That was the problem! I mounted the partition with wrong parameters.

with this line
```
/dev/sda5  /mnt/data  ntfs-3g  uid=1000,gid=100,umask=0022  0 0

```
everything works!

Thank you very much!!

---

