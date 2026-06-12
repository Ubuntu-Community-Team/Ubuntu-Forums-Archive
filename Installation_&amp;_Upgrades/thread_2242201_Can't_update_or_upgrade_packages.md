---
title: "Can't update or upgrade packages"
date: 2014-08-31
forum: Installation &amp; Upgrades
---

### Post by daniel.meechan.1u on 2014-08-31
Hi, I'm running 12.04.5 and when I do apt-get update, I get this error:
> 
W: Failed to fetch [http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu/dists/precise/Release](http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu/dists/precise/Release)  Unable to find expected entry 'deb-src/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.


And when I do apt-get upgrade, I get this:
> Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Duplicate sources.list entry [http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu/](http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu/) precise/main amd64 Packages (/var/lib/apt/lists/ftp.osuosl.org_pub_mariadb_repo_5.5_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu/](http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu/) precise/main amd64 Packages (/var/lib/apt/lists/ftp.osuosl.org_pub_mariadb_repo_5.5_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu/](http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu/) precise/main amd64 Packages (/var/lib/apt/lists/ftp.osuosl.org_pub_mariadb_repo_5.5_ubuntu_dists_precise_main_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
I've tried clean and autoremove but to no avail. Any ideas?

---

### Post by ian-weisser on 2014-08-31
'Clean' removes packages. It does not fix your sources.list file.
'Autoremove' removes packages. It does not fix your sources.list file.

One way to fix it:
Open Software Center -> Software Sources.
Uncheck the duplicate entries.

Another way to fix it:
Edit the raw files (in /etc/apt/sources.list or /etc/apt/sources.list.d/ ) in your favorite text editor, using sudo.

---

### Post by ajgreeny on 2014-08-31
Start by running command ```
sudo rm /var/lib/apt/lists/*
```which may clear up one of the problems, then run ```
sudo apt-get update
``` again to refresh the lists just removed.

If there is still a problem lets have a look at the output of ```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d
```to find any duplicate lines in that file, and what extra repos you have enabled.

I have however just noticed a problem in your shown output from the upgrade command with the repeated lines
```
W: Duplicate sources.list entry [http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu/](http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu/)  precise/main amd64 Packages  (/var/lib/apt/lists/ftp.osuosl.org_pub_mariadb_repo_5.5_ubuntu_dists_[COLOR=#ff0000]**p   recise**[/COLOR]_main_binary-amd64_Packages)
```where a space seems to have crept in to the word [COLOR=#ff0000]precise[/COLOR] somehow. I note that you did not use code tags for that output and it is possible that a straight copy into quote tags has caused the space.

It is always worth adding code tags to terminal output that you copy to forum posts. See my signature for a "How-to"

---

