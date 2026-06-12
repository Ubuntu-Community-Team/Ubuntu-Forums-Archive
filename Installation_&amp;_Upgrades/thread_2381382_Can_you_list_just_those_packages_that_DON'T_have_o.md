---
title: "Can you list just those packages that DON'T have other packages depending on them?"
date: 2017-12-30
forum: Installation &amp; Upgrades
---

### Post by raphaell2 on 2017-12-30
Hi everyone.

I'm currently using Xubuntu 17.10.

I was wondering if there's a way to automatically list only the "top level" packages installed on your system. By "top level" packages, I mean those packages that *don't* have any other packages depending on them - such as major metapackages, main packages of major software apps you're using, and so on - so that, if you installed all of them somewhere, all the other packages you need would be automatically installed as well. Could that, perhaps, be done through some modification of the dpkg -l command? 

(I'm posting this question in the Installation & Upgrades forum because I think such a list might come in handy when you're installing a new version.)

---

### Post by oldfred on 2017-12-30
The full dpkg list works for reinstall. It just will not reinstall anything already installed.
Nor will it reinstall obsolete packages, but may reinstall old kernels if in list so best to review. 
Since it includes all the lower level packages, it is a long list.

       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade
#IF you get this error:
dpkg: warning: package not in database
sudo apt-get install dselect
sudo dselect 
   -> Update
   -> Install 
   [http://askubuntu.com/questions/17823/how-to-list-all-installed-packages](http://askubuntu.com/questions/17823/how-to-list-all-installed-packages) 
   and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings' 

Top level only - no depends (not for reinstall)
sudo apt-get install aptitude
aptitude --disable-columns -F '%p' search '~i!~M!~R(~i)' > toplevel 
or
aptitude search '?installed ?not(?reverse-depends(?installed))'

---

### Post by raphaell2 on 2017-12-31
> aptitude --disable-columns -F '%p' search '~i!~M!~R(~i)' > toplevel

Thanks, that works best for my purposes. And then I can use tr to replace all the line breaks in the resulting file with blank spaces, and use the results of that with a simple sudo apt-get install command. But why do you say it's not for reinstall?

---

### Post by oldfred on 2017-12-31
The format for reinstall with dpkg includes the install as second item.

```
a11y-profile-manager-indicator            install
account-plugin-facebook                install
account-plugin-flickr                install

```

So if you want to edit, then it should work.

I have seen this it just read a list. It is for installing the default manifest which also has a second entry.
```
a11y-profile-manager	0.1.10-0ubuntu3
a11y-profile-manager-indicator	0.1.10-0ubuntu3
account-plugin-facebook	0.12+16.04.20160126-0ubuntu1

```
[http://releases.ubuntu.com/xenial/ubuntu-16.04.3-desktop-amd64.manifest](http://releases.ubuntu.com/xenial/ubuntu-16.04.3-desktop-amd64.manifest) Then to install that manifest  by using first name:
dpkg-query -W --showformat='${Package} ${Version}\n' > casper/filesystem.manifest
apt-get install -y $(awk '{print $1}' filesystem.manifest)

---

### Post by raphaell2 on 2017-12-31
Thank you!

---

