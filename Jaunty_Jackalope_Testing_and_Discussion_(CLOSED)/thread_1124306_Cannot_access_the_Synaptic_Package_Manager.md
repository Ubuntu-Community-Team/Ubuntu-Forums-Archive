---
title: "Cannot access the Synaptic Package Manager"
date: 2009-04-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by GARoss on 2009-04-13
I'm getting this error;

[B]An error occurred
The following details are provided:
E: The package turboprint needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.[/B]

which is probably caused because I didn't un-install an expired turboprint software properly (just deleted folders). The main problem is I cannot access the Synaptic Package Manager without the error message & once the error message is closed, Synaptic Package Manager closes too. I did download the turboprint debian installer & it error when trying the re-install. 
Any ideas how to fix this?
Thanks

---

### Post by Kevbert on 2009-04-13
Please try the following commands in terminal
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f
```
If Synaptic downloaded a .deb file have a look in /var/cache/apt/archives to see if the file is there. Just double click on it to try to re-install it. It may be that you need to rebuild your [COLOR="Red"][package status file]("http://ubuntuforums.org/showthread.php?p=6042686#post6042686")[/COLOR].

---

### Post by GARoss on 2009-04-13
> **Kevbert said:**
> Please try the following commands in terminal
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f
```
If Synaptic downloaded a .deb file have a look in /var/cache/apt/archives to see if the file is there. Just double click on it to try to re-install it. It may be that you need to rebuild your [COLOR="Red"][package status file]("http://ubuntuforums.org/showthread.php?p=6042686#post6042686")[/COLOR].
Thanks. 
Just before I saw your post I tried System/Update Manager which offered a "partial update" & in the process finished the un-install & update as well. After a reboot the error was gone!

---

### Post by drs305 on 2009-04-13
Try this if you are still having problems. It will attempt to modify your *status* file. If the status-old file doesn't contain reference to the offending package, replacing the current file with the backup (status-old) may be all it takes:
```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-backup
sudo mv /var/lib/dpkg/status-old /var/log/dpkg/status

```
Run your commands again. If it doesn't work, return the files as they were:
```

sudo cp /var/lib/dpkg/status-backup /var/lib/dpkg/status

```

If you are still having the problem, removing the entry from the status file may fix things:
```

gksudo gedit /var/lib/dpkg/status

```
Find the section for the package you are having difficulties with. The section should start with "Package: XXX" with XXX being the package name. Remove the entire section, save the file, and try your update again.

If this doesn't work, restore the original file:
```

sudo cp /var/lib/dpkg/status-backup /var/lib/dpkg/status

```

---

