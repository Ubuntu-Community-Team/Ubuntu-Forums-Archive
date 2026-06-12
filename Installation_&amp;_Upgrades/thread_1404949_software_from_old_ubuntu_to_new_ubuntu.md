---
title: "software from old ubuntu to new ubuntu"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by amit@nitttrchd.ac.in on 2010-02-12
I am using ubuntu 9.04 at my desktop with many software installed from reposiiries, now planning for ubuntu 10.04 in my laptop and with the help of aptoncd can i installed all my software from this version to new vesrion and any issue of ext3 or ext4 please help  also pls inform how to embed video in presntation of open office rather than linking and any shortcut to insert many images in document instaed doing one by one

---

### Post by jerrrys on 2010-02-13
this worked for me (for the most part) when going to 1oo4

[ATTACH]146965[/ATTACH]

---

### Post by oldfred on 2010-02-13
agree with jerrrys

sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, this tip won't work.

[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

Extra install stuff
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by presence1960 on 2010-02-13
> **jerrrys said:**
> this worked for me (for the most part) when going to 1oo4



+1 

I use that and it works great! many thanks to lovinglinux for posting that. I have that post bookmarked and a copy in a text file- don't want to take any chances on losing that gem.

---

