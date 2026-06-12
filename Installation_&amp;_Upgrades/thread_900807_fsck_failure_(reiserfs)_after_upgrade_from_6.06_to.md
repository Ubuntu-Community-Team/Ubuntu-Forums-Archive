---
title: "fsck failure (reiserfs) after upgrade from 6.06 to 8.04.1"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by mkupfer on 2008-08-25
I upgraded a Dell Latitude from 6.06 to 8.04.1 over the weekend using the Update Manager.

On the first boot into 8.04.1 I got dropped into a maintenance shell with 

[INDENT]...
/dev/sda5: clean, ...
fsck died with exit status 8
  * File system check failed.
A log is being saved in /var/log/fsck/checkfs if that location is writable.
Please repair the file system manually.
  * A maintenance shell will now be started.
CONTROL-D will terminate this shell and resume system boot.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bask: dircolors: command not found
bash: Command: command not found
bash: The: command not found[/INDENT]

The log had an error message referring to a particular UUID, something about not being able to open or find that partition.  (Sorry about the lack of precision here, my notes are vague on the exact error message.)  Looking at /etc/fstab, I saw that the UUID corresponded to an old, unused reiserfs partition.  I commented out that entry and was able to finish the initial boot, and then reboot okay.

Looking at the entry more carefully, I saw that the fs_passno field was 2.  The corresponding field (for that entry) is 2 in fstab.edgy and fstab.pre-uuid.

I find this puzzling--why was this partition a problem for 8.04.1 when it wasn't a problem for 6.06?  

I tried changing fs_passno to 0 and uncommenting the fstab line.  That worked okay (I could reboot okay).

Even more puzzling, I tried changing fs_passno back to 2, and now it boots just fine.

Is there anything worth doing about this, or should I just chalk it up to cosmic rays and move on?

---

