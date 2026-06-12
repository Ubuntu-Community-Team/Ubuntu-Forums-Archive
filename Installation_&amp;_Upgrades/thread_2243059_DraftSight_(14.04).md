---
title: "DraftSight (14.04)"
date: 2014-09-06
forum: Installation &amp; Upgrades
---

### Post by psyclone on 2014-09-06
Hi,
I "believe" I've installed Draftsight on my system, through using the following command,

I've down the following;

Install through "software center" (the installation completed, but I couldn't get it to run)
I then used: sudo dpkg -i --force-architecture draftSight.deb (after making "downloads" my current drive. the installation completed again, but still couldn't get it to run)

What am I doing wrong?

---

### Post by ibjsb4 on 2014-09-06
I first tried Archive Manager (file-roller) and it did not correctly install.  I then tried dpkg and got this:
```
sudo dpkg -i draftSight.deb
Selecting previously unselected package draftsight.
(Reading database ... 130388 files and directories currently installed.)
Preparing to unpack draftSight.deb ...
access control disabled, clients can connect from any host
access control disabled, clients can connect from any host
/var/lib/dpkg/tmp.ci/preinst: line 18: /var/lib/dpkg/tmp.ci/ShowLicense: No such file or directory
access control enabled, only authorized clients can connect
access control enabled, only authorized clients can connect
dpkg: error processing archive draftSight.deb (--install):
 subprocess new pre-installation script returned error exit status 127
Errors were encountered while processing:
 draftSight.deb
```
I then noticed the small print. "Standalone license. Activation required"

Did you do this?

I really don't want to create a DraftSight account so I can dig deeper.  So looks like thats all the help I can be.

Good luck

---

### Post by psyclone on 2014-09-07
Thanks for you post,

(correction, last post: [COLOR=#000000]I've down the following; =>TO:  [/COLOR][COLOR=#000000]I've done the following)[/COLOR]

[COLOR=#000000]Your correct, you have to create an account. But. That's only, after you've downloaded, installed and have the running program. I know this because I've ran draftsight on ubuntu 12.04. So the activation is required but after installation has occurred, but not before. 

In terminal I ran your suggested command: 

[/COLOR]sudo dpkg -i draftSight.deb

And I receive the following;


> 


e1-desktop@e1desktop:~$ cd /home/e1-desktop/Downloads
e1-desktop@e1desktop:~/Downloads$ sudo dpkg -i draftSight.deb
(Reading database ... 268577 files and directories currently installed.)
Preparing to unpack draftSight.deb ...
access control disabled, clients can connect from any host
access control disabled, clients can connect from any host


(ShowLicense:3975): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
* (I get this message 30 times)


access control enabled, only authorized clients can connect
access control enabled, only authorized clients can connect
Unpacking draftsight (2014.5.60) over (2014.5.60) ...
Setting up draftsight (2014.5.60) ...
e1-desktop@e1desktop:~/Downloads$ 




Does this help?

---

