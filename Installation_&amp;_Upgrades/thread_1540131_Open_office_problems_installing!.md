---
title: "Open office problems installing!"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by _Smiler_ on 2010-07-27
First of all, I'd like to apologise for my long-winded post and I hope someone has the patience to help me out. I'm trying to learn how to solve my own ubuntu problems, but this I just can't get this one. I've tried to post *exactly* what I've been doing, in case the headers and open office errors are linked. I don't know how to bring up the error I got for linux-headers as I didn't take note, but if someone lets me know how I'll get it. 

This problem started on my last installation when I upgraded from Lucid to Maverick. I encountered various problems including this open-office one. There was a problem with ca-certificates-java which wouldn't go away, so I just gave up and reinstalled Karmic fresh. (I burned a Lucid disc for both i386 and AMD64 (I have the latter system) but I kept getting an input output error while installing both) So, I used my Karmic disc and upgraded straight to Lucid after installing all the updates through Update Manager. I've run into similar problems in this install, this time it's not ca-certificates and open-office but linux-headers and open-office. During the upgrade, it said it couldn't install linux-headers-2.6.32-24, and remained at 2.6.31-22 and 2.6.31-22 generic. (I notice in the description for this generic header that it's for x86/x86_64 systems; I have i386 system installed. I don't want to uninstall this though as ubuntu installed it itself and didn't mention it in an error, plus I can't find a i386 equivelant in the synaptic list) So, one by one like stepping stones I installed 2.6.32-21, 2.6.32-21-386, 2.6.32-22, 2.6.32-22-386, 2.6.32-23, 2.6.32-24 and finally 2.6.32-24-386. 2.6.32-24-generic also seems to be installed (this was one of the problem packages) but I don't know whether I did this or ubuntu. The open-office problem remains though. It is identical to [this guy's]("http://ubuntuforums.org/showthread.php?t=644015") problem. 

Here's the error I get if I try to install open-office.org package in synaptic: ```
E: /var/cache/apt/archives/openoffice.org-gcj_1%3a3.2.0-7ubuntu4.1_i386.deb: subprocess new post-removal script returned error exit status 2
```

And this happens whenever I use apt-get to install or remove:
```
toes@wosies:~$ sudo apt-get remove checkgmail
[sudo] password for toes: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libhsqldb-java-gcj libgtk2-sexy-perl libcrypt-ssleay-perl bsh-gcj
  libgtk2-trayicon-perl libcrypt-simple-perl bsh libcrypt-blowfish-perl
  libjline-java libxml-simple-perl libsexymm2 libemail-mime-encodings-perl
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  checkgmail openoffice.org-gcj
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 13.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 215201 files and directories currently installed.)
Removing openoffice.org-gcj ...
gcj-dbtool-4.4: symbol lookup error: /usr/lib/libgcj.so.10: undefined symbol: _ZN3gnu4java8security3der3DER17CONSTRUCTED_VALUE
dpkg: error processing openoffice.org-gcj (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing checkgmail ...
Processing triggers for man-db ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Errors were encountered while processing:
 openoffice.org-gcj
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have java installed I think - youtube works anyway, I don't know how else to check :oops:

Thanks to anyone who helps!

---

