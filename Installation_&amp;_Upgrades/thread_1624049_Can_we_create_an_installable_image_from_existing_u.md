---
title: "Can we create an installable image from existing ubuntu installation ?"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by ved.antani on 2010-11-17
I  installed ubuntu 10.10 on my laptop and configured a lot(mainly setup  git, heroku, rails etc), installed and setup lot of things on it to suit  my needs. Now I want to move this setup to another machine and want to  avoid all the setup again. Is there a way I can create an installer out  of my existing ubuntu installation/partition which I can reuse for other machines?

---

### Post by oldfred on 2010-11-17
Welcome to the forums.

I think what you want are these but I have not used them.

[http://clonezilla.org/](http://clonezilla.org/)
[U]
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[/U] 

When I want to copy my config from my desktop to my portable I exported a list of installed applications and listed history from command line and copied history into a bash file. I then run my bash file and include the reimport of all installed apps. 

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

 dpkg --get-selections | grep -v deinstall > ubuntu-files
or
 dpkg --get-selections > ubuntu-files

---

### Post by sikander3786 on 2010-11-17
The link posted by **oldfred** is giving 404 error here.

[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

You can use remastersys to create a custom installation disc until the install size is less than 4GB. Here is another good guide for that.

[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

---

