---
title: "Munin will not install correctly"
date: 2012-03-27
forum: Installation &amp; Upgrades
---

### Post by OliverHaslam on 2012-03-27
I installed Munin for monitoring a server and then promptly broke it by trying to change some settings.

Being a Mac/Windows kinds guy I tried removing and re-installing it in the hope it would give me some default config files to try.

Now it will not properly re-install, offering various symlink and Apache errors. I've pasted a wall of text below.

```
oli@kirk:/etc/apache2$ sudo apt-get install munin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
munin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
oli@kirk:/etc/apache2$ sudo apt-get remove munin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  munin
0 upgraded, 0 newly installed, 1 to remove and 11 not upgraded.
After this operation, 758 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 153455 files and directories currently installed.)
Removing munin ...
Processing triggers for man-db ...
oli@kirk:/etc/apache2$ sudo apt-get install munin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  munin
0 upgraded, 1 newly installed, 0 to remove and 11 not upgraded.
Need to get 0 B/152 kB of archives.
After this operation, 758 kB of additional disk space will be used.
Selecting previously deselected package munin.
(Reading database ... 153403 files and directories currently installed.)
Unpacking munin (from .../munin_1.4.5-3ubuntu4_all.deb) ...
Processing triggers for man-db ...
Setting up munin (1.4.5-3ubuntu4) ...
ln: creating symbolic link `/etc/apache2/conf.d/munin': File exists
dpkg: error processing munin (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 munin
E: Sub-process /usr/bin/dpkg returned an error code (1)
oli@kirk:/etc/apache2$ 

```

Any ideas? I just want to start afresh.

Cheers.

---

### Post by winh8r on 2012-03-27
You could try removing it like this:

```
sudo apt-get remove munin --purge
```

which will remove it and all the config files to allow you a clean reinstall.

Alternatively, navigate to the remaining files and remove them manually.

Hope this helps.

---

### Post by OliverHaslam on 2012-03-29
> **winh8r said:**
> You could try removing it like this:

```
sudo apt-get remove munin --purge
```

which will remove it and all the config files to allow you a clean reinstall.

Alternatively, navigate to the remaining files and remove them manually.

Hope this helps.

Thanks, I'd tried deleting the files manually but I must have missed some. Purge seems to have done the trick.

Cheers.

---

### Post by winh8r on 2012-03-29
no worries , glad it helped a bit.

---

