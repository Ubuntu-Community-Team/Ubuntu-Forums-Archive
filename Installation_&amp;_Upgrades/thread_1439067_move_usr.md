---
title: "move usr"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by Linux Lover II on 2010-03-25
Is it possible to move the usr to another folder/partition?

Thanks in advance!

---

### Post by srs5694 on 2010-03-25
It's not practical to rename /usr to another name; too much stuff is coded to look in there.

You can, however, move the contents to another (empty) partition:


[list=1]
[*]Prepare the destination partition. (I'll assume you know how to do this.) Let's call it /dev/sdb1; change as necessary in the following commands.
[*]Type "sudo mount /dev/sdb1 /mnt" (or use another mount point).
[*]Type "cd /usr".
[*]Type "sudo tar cpf - ./ | (cd /mnt; sudo tar xvf -)". This command will take a while to complete. You'll see the filenames as they're copied.
[*]Inspect the contents of /mnt and /usr. They should be identical, with the possible exception of the lost+found directory (which is present on some filesystems but not others).
[*]Shut down and reboot into an emergency disc. Open a shell.
[*]Mount your root (/) filesystem somewhere convenient in the emergency disc's system. Let's say it's /mnt/foo. The following commands may need a "sudo" added to their starts, depending on the emergency system you use.
[*]Type "mv /mnt/foo/usr /mnt/foo/usr-old"
[*]Type "mkdir /mnt/foo/usr"
[*]Edit /mnt/foo/etc/fstab and add an entry for your new partition. It might look like "/dev/sdb1  /usr  ext3  defaults  0 2", but you should adjust the entry as necessary. You might need to change the filesystem type or want to use different mount options, for instance. You can also change /dev/sdb1 to a UUID specification (as Ubuntu uses on its automatically-created /etc/fstab entries). This isn't required, but it could make some automated administration tools behave more predictably.
[*]Reboot.
[*]If the system comes up and you can log in, chances are everything is fine. Still, you should give it a thorough test to be sure everything in /usr is working right. I'd do this by using the system normally for a day or two.
[*]Once you're satisfied everything's working, delete /usr-old.
[/list]


If the system doesn't reboot cleanly, then you'll have to reboot back into the emergency disc to figure out what went wrong. Maybe you've got permissions problems on /usr or not all of the files were copied correctly. Mistyping the tar commands can cause all sorts of problems. In a worst-case scenario, you can comment out your new /etc/fstab entry, delete the empty /usr directory, and rename /usr-old back to /usr to get back to a working system.

---

