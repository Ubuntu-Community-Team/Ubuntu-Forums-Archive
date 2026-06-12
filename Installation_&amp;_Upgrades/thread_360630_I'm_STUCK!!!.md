---
title: "I'm STUCK!!!"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by Clouseau on 2007-02-13
I tried to install Brother MFC drivers and such and mistakenly installed drivers for the wrong model. I then installed the drivers for the correct model, but it will not install. This is what I get: (Now I cannot install ANYTHING because it keeps giving me this msg)

luciusl@Planet-LuTru:~$ sudo aptitude install mysql-server
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  libgnomevfs2-dev 
The following packages have been kept back:
  language-pack-en language-pack-gnome-en libgnomevfs2-0 libgnomevfs2-bin 
  libgnomevfs2-common libgnomevfs2-extra libpq4 linux-image-386 
  linux-libc-dev linux-restricted-modules-386 lvm2 
0 packages upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate a file for the mfc8840dlpr package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
luciusl@Planet-LuTru:~$ 



WHAT IS THE ISSUE AND HOW CAN i FIX IT????
THANKS IN ADVANCE FOR THE HELP.
:confused:

---

### Post by Stemp on 2007-02-13
Did you tried : ```
sudo aptitude purge mfc8840dlpr
``` ?

---

### Post by Clouseau on 2007-02-13
I did...and got:

luciusl@Planet-LuTru:~$ sudo aptitude purge mfc8840dlpr
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  libgnomevfs2-dev 
The following packages have been kept back:
  language-pack-en language-pack-gnome-en libgnomevfs2-0 libgnomevfs2-bin 
  libgnomevfs2-common libgnomevfs2-extra libpq4 linux-image-386 
  linux-libc-dev linux-restricted-modules-386 lvm2 
The following packages will be REMOVED:
  mfc8840dlpr{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 12 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing mfc8840dlpr (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Errors were encountered while processing:
 mfc8840dlpr
Aborted (core dumped)
luciusl@Planet-LuTru:~$

---

### Post by Stemp on 2007-02-13
On another thread for a similar problem, benjo316 tell to use aptitude to remove the package.
[http://ubuntuforums.org/showpost.php?p=1959244&postcount=17](http://ubuntuforums.org/showpost.php?p=1959244&postcount=17)

---

### Post by Clouseau on 2007-02-23
I tried that and got:

luciusl@Planet-LuTru:~$ sudo aptitude remove mfc8840dlpr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  gtetrinet libapt-pkg-dev libgnomevfs2-dev libswt3.2-gtk-java 
  libswt3.2-gtk-jni mysql-client-5.0 
The following packages have been kept back:
  apt apt-utils azureus ekiga epiphany-browser foo2zjs initramfs-tools 
  language-pack-en language-pack-gnome-en libcurl3 libcurl3-gnutls 
  libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra 
  libmagick9 libmysqlclient15off libnautilus-extension1 libpq4 
  libwxbase2.6-0 libwxgtk2.6-0 linux-image-386 linux-libc-dev 
  linux-restricted-modules-386 lvm2 mysql-common mysql-server 
  mysql-server-5.0 nautilus nautilus-data popularity-contest python-apt 
  python-imaging python-imaging-sane python-pam slocate synaptic totem-xine 
  tzdata ubuntu-docs update-manager update-notifier x-window-system-core 
The following packages will be REMOVED:
  mfc8840dlpr 
0 packages upgraded, 0 newly installed, 1 to remove and 49 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
dpkg: error processing mfc8840dlpr (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted (core dumped)
luciusl@Planet-LuTru:~$ Errors were encountered while processing:
 mfc8840dlpr

I don't know how to remove this particulare package and it is stopping me from updating my system.

---

### Post by Stemp on 2007-02-23
Just 
```
sudo aptitude
```

---

