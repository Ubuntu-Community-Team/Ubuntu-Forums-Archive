---
title: "Cannot install - dpkg is ******."
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by Holder on 2007-09-09
Hello,
when i was trying to install (anything), he did this error:

> holder@holder-laptop:~$ sudo apt-get install git-core automake build-essential intltool libtool python-pyrex python2.5-dev xsltproc
Password:
Sorry, try again.
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git-core is already the newest version.
automake is already the newest version.
build-essential is already the newest version.
intltool is already the newest version.
libtool is already the newest version.
python-pyrex is already the newest version.
python2.5-dev is already the newest version.
xsltproc is already the newest version.
The following packages were automatically installed and are no longer required:
  module-assistant xserver-xorg-dev cvsps libnet-domain-tld-perl
  libnet-ip-perl libnet-dns-perl libdigest-hmac-perl libemail-valid-perl
  libsvn-perl dh-make
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up runit (1.6.0-1) ...
grep: /etc/inittab: No such file or directory
grep: /etc/inittab: No such file or directory
Adding SV inittab entry...
cp: cannot stat `/etc/inittab': No such file or directory
dpkg: error processing runit (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 runit
E: Sub-process /usr/bin/dpkg returned an error code (1)




Then i removed dpkg file (like an idiot) and now this error appears:

> holder@holder-laptop:~$ sudo apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gimp is already the newest version.
The following packages were automatically installed and are no longer required:
  module-assistant xserver-xorg-dev cvsps libnet-domain-tld-perl
  libnet-ip-perl libnet-dns-perl libdigest-hmac-perl libemail-valid-perl
  libsvn-perl dh-make
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)
holder@holder-laptop:~$ 



Thanks =\

---

### Post by earobinson on 2007-09-09
long shot in the dark what about ```
sudo aptitude install gimp
```

---

### Post by Holder on 2007-09-09
> **earobinson said:**
> long shot in the dark what about ```
sudo aptitude install gimp
```

Dude, i know i can use it ALSO, but i wanna fix my apt-get..

---

### Post by Holder on 2007-09-10
Bump..?
Anyone?

---

### Post by JBAlaska on 2007-09-10
Have you tried using synaptic and serching for apt, that should do it. If not get it from your distro CD

---

### Post by earobinson on 2007-09-10
```
sudo aptitude install apt-get
```? I think there is allso a repair option, ill check when im back on my box

---

### Post by Holder on 2007-09-13
I have tried to install the package from the ubuntu CD, but to install it i need to remove completeley the dpkg first, and it's a problem becouse if i will remove it, every package i have installed with the apt-get command will be deleted (it's like 90% of my computer =\)

Also, I have tried this command:

> holder@holder-laptop:~$ sudo aptitude install apt-get
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package matching "apt-get".  However, the following
packages contain "apt-get" in their description:
  newbiedoc gnome-apt xen-headers-2.6.19-4-generic 
  xen-headers-2.6.19-4-server adept-updater libcmdparse2-ruby1.8 aptitude 
  xen-headers-2.6.19-4 cron-apt debarchiver apt jablicator libcmdparse-ruby 
  posixtestsuite r-base libcmdparse2-ruby apt-build debdelta grep-dctrl 
  aptoncd auto-apt apt-move 
The following packages are unused and will be REMOVED:
  git-core git-doc liberror-perl rcs 
0 packages upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 8995kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)
A package failed to install.  Trying to recover:
sh: dpkg: not found


It doesn't work..

Any ideas exept for Reinstalling ubuntu =\?

---

### Post by Holder on 2007-09-14
Okay guys, i have the dpkg!
Now the error is diferent (when i DO got the dpkg file!)

when i'm trying to install gimp for exemple:

> holder@holder-laptop:~$ sudo apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gimp is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up runit (1.6.0-1) ...
grep: /etc/inittab: No such file or directory
grep: /etc/inittab: No such file or directory
Adding SV inittab entry...
cp: cannot stat `/etc/inittab': No such file or directory
dpkg: error processing runit (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 runit
E: Sub-process /usr/bin/dpkg returned an error code (1)

When i'm trying those commands:

> holder@holder-laptop:~$ sudo dpkg --configure -a
Password:
Setting up runit (1.6.0-1) ...
grep: /etc/inittab: No such file or directory
grep: /etc/inittab: No such file or directory
Adding SV inittab entry...
cp: cannot stat `/etc/inittab': No such file or directory
dpkg: error processing runit (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 runit



or this one:

> 
holder@holder-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up runit (1.6.0-1) ...
grep: /etc/inittab: No such file or directory
grep: /etc/inittab: No such file or directory
Adding SV inittab entry...
cp: cannot stat `/etc/inittab': No such file or directory
dpkg: error processing runit (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 runit
E: Sub-process /usr/bin/dpkg returned an error code (1)


it's the same!

Thanks,
Holder.

---

### Post by matt1606 on 2007-09-20
Hi!

I've had the same problem. Just removed "runit" and everything got back to normal.

---

### Post by alinpopa on 2008-02-06
Same here. Like someone said, remove runit and everything is ok.

---

