---
title: "install software"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by aeetes on 2007-02-18
Is there a link to a tutorial that show me how to install software? I want to install the NTFS-3g driver but can't figkure out how it's gets installed.

Also, does this forum support email notication when someone replies to this post? IF so where do i turn it on?

thanks

---

### Post by pebo on 2007-02-18
[Here]("http://www.psychocats.net/ubuntu/installingsoftware") is a tutorial for installing software. 
Regarding the ntfs-3g driver,  [here]("(http://givre.cabspace.com/ntfs-config/)") is a nice tool for setting up ntfs write support. Be aware though that ntfs write support is experimental so be it on your own head!

---

### Post by taurus on 2007-02-18
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)
[http://everythingelse.wordpress.com/2006/07/19/89/](http://everythingelse.wordpress.com/2006/07/19/89/)

---

### Post by solar george on 2007-02-18
You click on the system menu and open synaptic package manager.

enable the universe repositories - 
click on the settings menu and open repositories.

Ensure that the box for "Community Maintained Open Source (universe)" is ticked.
Click close.

Press the reload button to update your list of packages.

Click on search.

Search for ntfs.

Right click on 'ntfs-3g' and select 'Mark for installation'

Press apply to install.

You can search for and install most packages in the same way.

---

### Post by aeetes on 2007-02-19
What do you think about ::

3) On 07/14/2006, project member Szabolcs Szakacsits presented a new version of ntfsmount and libntfs, given the project title ntfs-3g. This version has full read/write capabilities, many bug fixes and improved performance. It has already been downloaded over 66,000 times, tested and regularly used by users with satisfaction over the last three months. Despite of that it is still a strong beta, and will upon (in some way or the other) merge also into the linux-ntfs ntfsprogs package.

Is it any more reliable?

---

### Post by aeetes on 2007-02-19
Thanks!

---

### Post by aeetes on 2007-02-19
Thanks so much; let you know...

---

### Post by aeetes on 2007-02-19
I followed your steps, but when I "highlight" the ntfs-3g I don't have any right click options. I've reload plenty of times.

I'm in the search menu and under the "ALL" (tall rectangular box - is where the ntfs-3g is)

When I click on the "package" menu on the top menu, it's all greged out.

Thanks for any help

---

### Post by solar george on 2007-02-19
Open a terminal.

Type in
```
sudo apt-get install ntfs-3g
```
it will ask you for your password, type it in and it should install the ntfs drivers.

---

### Post by aeetes on 2007-02-19
thanks.

---

