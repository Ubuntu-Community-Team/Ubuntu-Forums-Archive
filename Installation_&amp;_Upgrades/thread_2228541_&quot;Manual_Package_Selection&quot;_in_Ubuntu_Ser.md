---
title: "&quot;Manual Package Selection&quot; in Ubuntu Server installation"
date: 2014-06-08
forum: Installation &amp; Upgrades
---

### Post by h.hittini on 2014-06-08
Hello there,

I'm installing Ubuntu Server 13.10 and I need to minimize the installation size and overhead as much as possible  Using manual package selection could be of a great help but I'm not  sure which are the important packages for the system operation and which  are not
  Is there a reference for that?
In addition. in this page [https://help.ubuntu.com/13.10/serverguide/preparing-to-install.html](https://help.ubuntu.com/13.10/serverguide/preparing-to-install.html) the table suggests that there are two versions on Ubuntu Server (e.g. Ubuntu Server and Ubuntu Server Minimal)
How to get the Minimal Server version?

Regards,

---

### Post by bapoumba on 2014-06-08
Just a side note, 13.10 will reach end of life next month. Why not go with 14.04 ?
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by h.hittini on 2014-06-08
> **bapoumba said:**
> Just a side note, 13.10 will reach end of life next month. Why not go with 14.04 ?
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Because I need to use a software and it doesn't support Ubuntu 14.04 yet
And regarding the link you provided, it doesn't answer my question

---

### Post by bapoumba on 2014-06-08
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

---

### Post by deadflowr on 2014-06-08
> **h.hittini said:**
> Because I need to use a software and it doesn't support Ubuntu 14.04 yet
And regarding the link you provided, it doesn't answer my question

You can get the minimal server packages from the mini.iso from that link.
Afaik the kernel's the same for both the desktop and server versions.
(Of course what on earth do I know, you know?)

---

### Post by h.hittini on 2014-06-08
> **bapoumba said:**
> [https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

Using Taskel I found that my system has only two "tasks"; "Basic Ubuntu server" and "OpenSSH server"
I don't need to install extra packages I need to uninstall the unnecessary ones making the difference between [COLOR=#ff0000]Ubuntu server[/COLOR] and [COLOR=#ff0000]Ubuntu server minimal[/COLOR]
These two versions are mentioned here [https://help.ubuntu.com/13.10/serverguide/preparing-to-install.html](https://help.ubuntu.com/13.10/serverguide/preparing-to-install.html)

---

### Post by h.hittini on 2014-06-08
> **deadflowr said:**
> You can get the minimal server packages from the mini.iso from that link.
Afaik the kernel's the same for both the desktop and server versions.
(Of course what on earth do I know, you know?)

I can get Ubuntu Minimal not Ubuntu Server Minimal from there

---

### Post by bapoumba on 2014-06-08
From my first link :
> The Minimal CD will download packages from online archives at installation time instead of providing them on the install CD itself. Downloading packages at install time reduces the size of the install CD to approximately 5 to 30MB depending on architecture (see below), as well as providing only the packages needed for installation. The download time savings achieved by using a Minimal CD can be significant, as only current packages are downloaded, so there is no need to upgrade packages immediately after installation.
With Ubuntu Minimal, you can either end up with a server or a desktop edition, depending on your choices, the main difference being packages are not provided on the CD but are downloaded during the install procedure.

Ubuntu Server 13.10 had you choose which packages you wanted to install using the taskel utility. So you are the only one able to know which ones are installed. 
[https://help.ubuntu.com/13.10/serverguide/installing-from-cd.html](https://help.ubuntu.com/13.10/serverguide/installing-from-cd.html) (next page to the one you linked).

---

