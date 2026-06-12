---
title: "problem with NTFS permissions in 11.04"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by Kais3rvlc on 2011-05-03
Hi all,

First at all sorry if this is not the place to ask about this, but as it is related with the new version, i think it is.

I don't remember to have done anything special in 10.10 to use/execute scripts from a NTFS partition, but now, after upgrading (from the live cd) to the 11.04, i have no way of changing permissions to the files in the NTFS partition.

I have read that this is due some changes that have been done in the way ubuntu works with NTFS partition.

In fact, if i try a chmod no error message is returned, but nothing happens and permissions are not changed. Same thing if i do it from gnome, if i click on execution permission (for instance) it lasts a second and automatically undo the change.

Any solution different to use the NTFS config tool is welcome.

BTW, NTFS config tool basically gives 777 permissions to every file in the NTFS partition, right?

---

### Post by Nerotriple6 on 2011-05-03
Hello.

I don't think it is possible to execute files on NTFS. I may be wrong but least I don't think there is an easy way.
Have you tried to move the files from the NTFS system into EXT4 or whatever you are using? Maybe it will work if you do that, mark as executable and move them back?
The only use I've found for NTFS lately is for music. :P:P

---

### Post by Kais3rvlc on 2011-05-03
Hi and thanks for the answer

The reason for having a NTFS partition is because is a shared unit between Windows and Linux. If i had only Linux... NTFS would probably go to hell :p

I also tried that, If i mark the files in the EXT4 the permissions are changed but they are gone when i move the files back to the NTFS partition. Is like if the NTFS partition had fixed permissions, 600.

---

### Post by dino99 on 2011-05-03
there is no trouble to read/write files from/to windows/ubuntu

from synaptic, check that ntfs-3g & ntfsprogs are installed

mountmanager is an easy way to set rights

---

### Post by Nerotriple6 on 2011-05-03
I also used to have a shared volume with Windows. Now I don't use Windows anymore at all... :P:P:P
So it didn't work. I'm not surprised. Linux doesn't like NTFS... However I went on Google and you may be able to fix it by mounting the volume in a certain way described [here]("http://askubuntu.com/questions/18052/exe-file-permission-fail/18053#18053").

No problem and good luck.

---

### Post by Kais3rvlc on 2011-05-03
hi all :)

I know that i could use a mount and its options to get it done :)

What shocked me was the change in the policy of working with NTFS partitions. I agree with Nerotriple6, ubuntu never liked NTFS so much.

On the other hand i have both ntfs3g and ntfs progs installed and it doesn't work like it used to, ill give a try mount manager

---

### Post by Morbius1 on 2011-05-03
Is this a wine issue or are you talking about executing anything in general?

---

### Post by Kais3rvlc on 2011-05-03
anything in general

---

### Post by oldfred on 2011-05-03
I have used a shared NTFS partition since 6.06, and yes the automounted NTFS do not seem to work the same.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

I prefer to manually edit fstab with defaults and it works fine for me. Morbius1 has some alternative settings that may work better for many users.

---

### Post by Kais3rvlc on 2011-05-03
thanks, ill take a look in a while :)

---

### Post by Kais3rvlc on 2011-05-03
I checked it out, but at the end you have more or less the same problem, you can mount it with the umask you want... but the permissions are static, you cannot change them

---

### Post by Morbius1 on 2011-05-03
If you are attempting to mount an NTFS partition such that you can selectively change a given file's permission it won't work. All files inherit the ownership and permissions of the mounted partition itself. Chmod or chown will not work on NTFS since there are no Linux ownership or permission bits to set. You can set it so all files are executable or all files are not executable.

---

