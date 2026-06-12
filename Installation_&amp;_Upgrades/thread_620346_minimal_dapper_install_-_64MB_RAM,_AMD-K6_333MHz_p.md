---
title: "minimal dapper install - 64MB RAM, AMD-K6 333MHz processor system"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by bill_dotson on 2007-11-22
I have just installed a mini ISO version of Ubuntu dapper on an old 333MHz system with 64MB RAM.  It has nothing but the very minimal install (CLI, the whole bit).  What do I do to install a minimalist GUI?  What sources do I need to add to get the xorg stuff?  I also need the repository for icewm, firefox, vsftpd (for secure FTP server.. this PC does not have many other uses) Thanks.  I didnt have the time to search google, nothing came up on the first page.  Thanks again.

---

### Post by mikewhatever on 2007-11-22
Try this [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by rsambuca on 2007-11-22
Have a read through[ this page]("https://help.ubuntu.com/community/Installation/LowMemorySystems").  It gives you all the commands you need to enter a basic system with GUI, browser, etc.

Also, is[ this other profile]("http://ubuntuforums.org/member.php?u=236704") you as well?

---

### Post by bill_dotson on 2007-11-22
haha I guess so.  I couldnt remeber the password or the specific name.  haha.  Making a new one was easier  I will check those links

---

### Post by bill_dotson on 2007-11-22
I tried those, but I get dependency errors for x-window-system-core and icewm.  If I just try to install xorg it says it has no installation candidate.  :(

---

### Post by rsambuca on 2007-11-22
Then you haven't set up your sources.list properly.  xorg is in the repos.

[https://help.ubuntu.com/community/Installation/LowMemorySystems#head-02ceff7e858ff9de1fdd38eb9e241a87f7d6cf60](https://help.ubuntu.com/community/Installation/LowMemorySystems#head-02ceff7e858ff9de1fdd38eb9e241a87f7d6cf60)

---

### Post by bill_dotson on 2007-11-22
pretty sure I did it right.  It returned a broken packages error.

---

### Post by rsambuca on 2007-11-22
First check your repos using

sudo nano /etc/apt/sources.list

Take out the #'s in front of the repos.  The sudo apt-get update && sudo apt-get upgrade.

---

### Post by bill_dotson on 2007-11-24
check my repos and uncomment everything with a single #?  Some of those repos are restricted unsupported ones I do believe (it says that..)  Also, do I add these exact lines 

"deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe"

or just have the dapper universe ones uncommented?

Thanks

---

### Post by rsambuca on 2007-11-24
Don't add anything, especially not Feisty repos if you are trying to install Dapper!!!

---

### Post by bill_dotson on 2007-11-26
ok, well I commented out all the oens that had single #s at the beginning and still nothing.  No x-server-window-core or whatever, xorg, etc.

---

