---
title: "Ubuntu 13.10 freezes after large (&gt;1 gb) file transfers to usb stick"
date: 2014-03-02
forum: Installation &amp; Upgrades
---

### Post by puzz2 on 2014-03-02
Hello everybody,
i know this problem has been discussed already, but i couldn't find any satisfactory solution for my situation.
As the title says my Saucy regularly freezes AFTER having copied large files to (any) usb stick. The operation completes succesfully, no corrupted files, but the system stucks and i have to choke it (Dell inspiron 5521, Ubuntu 13.10).
/var/log/syslog gives no useful info.

If i do it via nautilus it just freezes at the end of the process, so i tried to cp and rsync the file via terminal (ctrl-alt-f1),
and what i noticed is:
-after the copy the terminal is fully operative in both cases, but when i switch back to graphic interface with ctrl-alt-f7 it stucks there -> choke.
-rsync log file seems corrupted (a bunch of \00s in the middle of the file)
-after 50% the transfer speed drops from ~50MB/s to ~5MB/s, this is not my primary issue but could be related (?).

I tried adding "pci=acpi" to my grub boot options like [http://ubuntuforums.org/showthread.php?t=1867460](http://ubuntuforums.org/showthread.php?t=1867460) suggested, but no difference

what could i do to find the source of the problem, and maybe solve it?
Sorry for my english, thanks in advance for your help, i usually manage to solve my linux issues reading older threads, but this time...

---

### Post by ubfan1 on 2014-03-02
Is the stick USB2 or USB3?  I have seen problems with USB3, but never USB2.  When you check the file, do you use a hashcheck like md5sum to ensure there was no corruption?

---

### Post by puzz2 on 2014-03-03
USB2, and the port either 2 or 3, but i suspect it is a more general I/O issue, since it just happened while downloading via torrent. Anyway an usb transfer is certain to freeze. Yes, i checked the file with md5sum.
Thanks for your answer

---

