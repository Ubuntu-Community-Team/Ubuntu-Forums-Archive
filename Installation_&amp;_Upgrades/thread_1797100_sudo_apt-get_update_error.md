---
title: "sudo apt-get update error"
date: 2011-07-04
forum: Installation &amp; Upgrades
---

### Post by angry_beavers on 2011-07-04
I pulled a stupid when trying to install VLC through the terminal and added the ppa source for a different version of ubuntu. Now when I do a sudo apt-get update I come up with the error:

W: Failed to fetch [http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

Also in the midst of the long list i found:

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
  404  Not Found

I tried to look in /etc/apt/sources.list for the source to remove it but I couldn't find it. Where is it located and how can I undo what I did?

---

### Post by arnaudj on 2011-07-04
try this: ?

[http://ubuntugenius.wordpress.com/2009/11/01/wfailed-to-fetch-error-when-upgrading-ubuntu-try-this/](http://ubuntugenius.wordpress.com/2009/11/01/wfailed-to-fetch-error-when-upgrading-ubuntu-try-this/)

---

### Post by ajgreeny on 2011-07-04
> **arnaudj said:**
> try this: ?

[http://ubuntugenius.wordpress.com/2009/11/01/wfailed-to-fetch-error-when-upgrading-ubuntu-try-this/](http://ubuntugenius.wordpress.com/2009/11/01/wfailed-to-fetch-error-when-upgrading-ubuntu-try-this/)
I doubt this will help if the ppa was the wrong one.

I think you will find the appropriate sources list entry in **/etc/apt/sources.list.d/*<****nameofppa****>*.list**, and possibly also **/etc/apt/sources.list.d/*<****nameofppa****>*.list.save** so either delete those files, or simply disable the repositories in **System-> Administration ->Software Sources**.

---

### Post by angry_beavers on 2011-07-04
> **ajgreeny said:**
> I doubt this will help if the ppa was the wrong one.

I think you will find the appropriate sources list entry in **/etc/apt/sources.list.d/*<****nameofppa****>*.list**, and possibly also **/etc/apt/sources.list.d/*<****nameofppa****>*.list.save** so either delete those files, or simply disable the repositories in **System-> Administration ->Software Sources**.

Managed to locate the file and use "sudo rm"

appreciate all the help

---

