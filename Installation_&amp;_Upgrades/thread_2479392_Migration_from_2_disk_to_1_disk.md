---
title: "Migration from 2 disk to 1 disk"
date: 2022-09-23
forum: Installation &amp; Upgrades
---

### Post by zkab on 2022-09-23
My computer runs Ubuntu 22.04 LTS and has 2 disks where Ubuntu is on Disk1 and /home is on Disk2.
```
~$ df -h gives following ...

Filesystem                     Size  Used Avail Use% Mounted on

/dev/nvme0n1p2                 228G   28G  189G  13% /
/dev/nvme0n1p1                 511M  5,3M  506M   2% /boot/efi
/dev/nvme1n1p1                 229G   57G  161G  27% /home
```

I will replace this old computer with a new one but the new computer has only one disk.
Which is the best way to migrate from old -> new?

---

### Post by TheFu on 2022-09-23
Backup and restore using your normal backup and restore capabilities.  I just hope you weren't using images for backups.

---

### Post by oldfred on 2022-09-23
+1 on TheFu's suggestion.

Total new install & restore from backup.
Backup at minimum is /home & list of installed apps, to make it easy to reinstall them. Setting are in /home.
Unless you also have server apps, then you also may need those folders in you backup.

TheFu has previously posted many threads on backup procedures.

---

### Post by zkab on 2022-10-03
I was thinking of following ...

1. Install a Ubuntu 22.04 LTS from scratch on the new computer
2. Use Aptik to migrate

Will it work 100% ?
Have no experience of Aptik

---

### Post by TheFu on 2022-10-03
Aptik used to be reasonable, but last time I looked a few years ago, it had died as a project. Is it reborn?  I probably tried to use aptik around 5-6 yrs ago and it didn't work.  There is no 100% solution for any restore, since things change with every package update.  As admins, we need to be flexible, so we can be smart about handling a few issues at restore time.  The ways to make backup/restore bonehead just aren't flexible and introduce all sorts of worse things into a system ... like not patching for months, which isn't good for anyone outside the OpSec security teams who need systems to hack.

BTW, blindly restoring files from /etc/ WILL create a system that cannot boot.  Files in /etc/ need to be selectively restored and some need to be merged between the old and new configs.  

On a desktop, it is probably best to backup /etc/ just for reference and only do the config merge when you actually see issues later.  

On a server, there will be specific files that the admin will recognize as customized for the system which need to be put back or merged.
When a desktop install has some server processes setup, say an internal website or media center, then those specific parts in /etc/ need to be addressed BEFORE feeding the list of packages into APT in the fresh system.

No backup+restore process should be assumed to work, until after it has actually be used to restore successfully.  As with everything, practice builds confidence and skill.  Restoring an OS **is** a skill worth practicing.

---

### Post by zkab on 2022-10-03
Thanks for your input ... really appreciate you professional answer.
I think I will go the safe way ...

1. Install Ubuntu 22.04 LTS from an iso-file to the new computer.
2. Install packages as I need them and check with configureation from the old computer (will keep it as reference)

My concern is /home ... the old computer has /home on second disk but the new computer has only one disk.
Can I just copy the contents from old /home to the new /home without running into trouble?

---

### Post by TheFu on 2022-10-03
> **zkab said:**
>  Can I just copy the contents from old /home to the new /home without running into trouble?

95% yes.  But settings for some programs do change over time, especially over 2+ yrs of development.

Let me be very clear - I do what you've planned with HOME directories.  Actually, everything under $HOME is relative, so whether that be /home/john or /home/jon or /home/j-daddy ... doesn't matter.  Put the files in the same relative location to $HOME, which is normally different for each human username.

Then, if you notice issues with 1-3 programs over the next few weeks, you can create a new userid, which will have a new, fresh $HOME, login using that user and see if the problems don't end.  They usually will.  So, then you'll know that the old settings were in conflict with the new config settings and can look at just those programs more closely.  I've had this happen a few times with Mozilla programs (firefox and thunderbird).  Once it was because I block all IPv6 and they didn't think anyone would still be doing that, so things broke.  By the time I noticed it, there was already a workaround that didn't include enabling IPv6, which I still don't do.  I just don't think I can secure it, so I don't want it even in the network stack.

---

### Post by zkab on 2022-10-04
OK ... thanks
I will follow your guidelines.

---

