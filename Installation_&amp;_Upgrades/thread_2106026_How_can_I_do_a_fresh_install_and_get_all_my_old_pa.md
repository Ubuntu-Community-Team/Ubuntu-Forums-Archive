---
title: "How can I do a fresh install and get all my old packages?"
date: 2013-01-17
forum: Installation &amp; Upgrades
---

### Post by DavidS on 2013-01-17
I'm running Ubuntu 11.10.  I want to install 12.04 (LTS), which I'll probably stick with for the next few years.  I'll be using the same /home partition for both versions.

Every time I have tried to upgrade a Ubuntu distro in the past it has failed in one way or another, so this time I want to do a fresh install on a spare partition, so that if there are any problems I can still boot my 11.10 version.

What I want to know is this: is there a way for me to get 12.04 automatically to install the appropriate versions of all additional software I have previously installed in 11.10?  I thought there was some way of doing this, but I can't seem to find a reference to it.

I have looked at "Sync between computers" in Ubuntu Software Centre, and I have an account, but my computer is referred to by its host name.  Since my new installation will have the same host name as the current one (at least, I would prefer it to in order to save other problems), I suspect that trying to use "Sync between computers" won't work.  And perhaps it doesn't work anyway between two different versions.

What do I need to do to get (broadly) the same software on a new 12.04 installation as I currently have in my 11.10 setup?

Is the only safe way to do it to select everything manually?

David

---

### Post by tgalati4 on 2013-01-17
There's no automated way to do it, without breaking things.  Package names change, packages merge, frameworks change, frameworks get added.  Your best bet is a clean install and a printed list of your existing package load:

```
dpkg --get-selections > installed-software.txt
```

If you were simply migrating to a new machine with the same code base, then you can use the installed-software.txt as an input for dpkg --set-selection.  But with a new distro you risk breakage.

---

### Post by DavidS on 2013-01-17
Thanks for the speedy reply.

I can see the problems that might arise in trying to automate the process - no doubt that's one of the reasons why my previous upgrades seem to have failed.

---

### Post by oldfred on 2013-01-17
I have used the dpkg on my upgrades as I do clean installs. But have manually housecleaned out some packages like OpenOffice when Ubuntu changed to LibreOffice so I did not have both.

       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

    
The issues on upgrades are often related to PPA which may not have new versions. They should be turned off first.

---

### Post by DavidS on 2013-01-20
Thanks for all the advice.

I've now got the new system running as I wanted.

---

