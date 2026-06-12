---
title: "Software Update Broken??"
date: 2006-07-12
forum: Installation &amp; Upgrades
---

### Post by JustDon on 2006-07-12
When I boot up Ubuntu the automatic update opens and scans my system. I then get this message:

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

I have run the command in the terminal and it does not correct the problem, I get:

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2845kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 75522 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3 (using .../samba_3.0.22-1ubuntu3.1_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas?

---

### Post by gw90se on 2006-07-12
Try correcting it with Aptitude. It fixed my Samba problem after an upgrade.

---

### Post by Jagot on 2006-07-13
Aptitude shouldn't really have an effect in retrieving the packages - more when you want to remove them.  Not sure what the problem is but occasionally there are errors in the repo's, so you might want to try in a day or so to see if it works out.

---

### Post by migo2011 on 2006-07-13
the very same problem here!
help is appreciated!

thanks.

---

### Post by AskHL on 2006-07-13
I have the same problem. gw90se, would you mind explaining how this can be corrected with Aptitude?

---

### Post by Hairback357 on 2006-07-13
I am having the same problem here. Hoping for a fix. :(

---

### Post by carmelo on 2006-07-13
I had similar problem.

the problem is a incorrect link in /etc/rc2.d (S91samba in your case, K05samba in mine)

fix the link and retry.

see [http://www.ubuntuforums.org/showthread.php?t=214848](http://www.ubuntuforums.org/showthread.php?t=214848)

---

### Post by Hairback357 on 2006-07-13
Thank you. That fixed my problem. :)

---

### Post by vbatts on 2006-07-14
similar here, but it wasn't a K0.. whatever,
here was my fix


root@mobile-desktop:/home/vbatts# cd /etc/rc2.d/
root@mobile-desktop:/etc/rc2.d# ls -l
total 0
[...]

lrwxrwxrwx 1 root root  6 2006-06-23 19:04 [COLOR="Red"]S91samba -> /samba[/COLOR]

[...]
root@mobile-desktop:/etc/rc2.d# rm S91samba
root@mobile-desktop:/etc/rc2.d# ln -s S91samba ../s
samba/             scrollkeeper.conf  sgml/              skel/              sudoers
sane.d/            securetty          shadow             sound/             sword.conf
scim/              security/          shadow-            ssh/               sysctl.conf
screenrc           services           shells             ssl/               syslog.conf
root@mobile-desktop:/etc/rc2.d# ln -s S91samba ../samba/
root@mobile-desktop:/etc/rc2.d# apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
Need to get 0B/2845kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 117291 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3 (using .../samba_3.0.22-1ubuntu3.1_i386.deb) ...
 * Stopping Samba daemons...                                                                                          [ ok ]
Unpacking replacement samba ...
Setting up samba (3.0.22-1ubuntu3.1) ...
update-rc.d: warning: /etc/rc3.d/S91samba is not a link to ../init.d/samba or /etc/init.d/samba
 * Starting Samba daemons...                                                                                          [ ok ]




all  better

---

### Post by edahl on 2006-07-14
I've got the exact same problem..!

---

### Post by edahl on 2006-07-14
And we fixed the problem. Got a weird note on some kind of link though.

---

### Post by JustDon on 2006-07-16
OK, I finally got this fixed. I ran this in terminal:  

cd /etc/rc2.d
sudo rm S91samba
sudo ln -s ../init.d/samba S91samba
sudo apt-get install -f

Straightened everything out just fine. Thanks all.

---

