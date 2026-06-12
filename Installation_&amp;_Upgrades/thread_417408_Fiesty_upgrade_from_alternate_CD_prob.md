---
title: "Fiesty upgrade from alternate CD prob"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by locoHost on 2007-04-21
I have a Fiesty alternate CD in my drive. Trying to upgrade. I open terminal...

mark@d6games:~$ cd /cdrom
mark@d6games:/cdrom$ ls
cdromupgrade  doc      isolinux    pics  preseed             ubuntu
dists         install  md5sum.txt  pool  README.diskdefines
mark@d6games:/cdrom$ cdromupgrade
bash: cdromupgrade: command not found
mark@d6games:/cdrom$ sh cdromupgrade
Could not find the upgrade application archive, exiting
mark@d6games:/cdrom$ 

You can see the files on my CD and the commands I typed. What am I doing wrong?

Thanks guys :-)

Mark

---

### Post by mhansen on 2007-04-21
Now, I've never upgraded from a cdrom, so keep that in mind.  This is my first run with Ubuntu.  :)


However, I'm pretty sure you'll have to sudo that command, AND anytime a directory isn't in your path, you'll have to run it as such:  ./command, which tells it to look in the current directory.

So, try sudo ./cdromupgrade and see how that works...


Regards,
Mike

---

### Post by GeDaMo on 2007-04-21
You have to do ```
gksu sh /cdrom/cdromupgrade
```(it needs the full directory name)

---

