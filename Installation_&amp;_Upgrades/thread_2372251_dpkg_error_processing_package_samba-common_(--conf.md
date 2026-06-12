---
title: "dpkg: error processing package samba-common (--configure):"
date: 2017-09-22
forum: Installation &amp; Upgrades
---

### Post by someoe on 2017-09-22
Ubuntu 16.04 LTS (Xenial)

4.10.0-36-generic

when i type ```
sudo apt-get install -f
``` i get this output :

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up samba-common (2:4.3.11+dfsg-0ubuntu0.16.04.11) ...
dpkg: error processing package samba-common (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of samba-common-bin:
 samba-common-bin depends on samba-common (= 2:4.3.11+dfsg-0ubuntu0.16.04.11); however:
  Package samba-common is not configured yet.

dpkg: error processing package samba-common-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 2:4.3.11+dfsg-0ubuntu0.16.04.11); however:
  Package samba-common is not configured yet.
 samba depends on samba-common-bin (= 2:4.3.11+dfsg-0ubuntu0.16.04.11); however:
  Package samba-common-bin is not configured yet.

dpkg: error processing package samba (--configure):
 dependency problems - leaving unconfigured
Setting up unattended-upgrades (0.90ubuntu0.8) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                     dpkg: error processing package unattended-upgrades (--configure):
 subprocess installed post-installation script returned error exit status 10
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of winbind:
 winbind depends on samba (= 2:4.3.11+dfsg-0ubuntu0.16.04.11); however:
  Package samba is not configured yet.

dpkg: error processing package winbind (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up grub-pc (2.02~beta2-36ubuntu3.13) ...
dpkg: error processing package grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 10
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of grub-gfxpayload-lists:
 grub-gfxpayload-lists depends on grub-pc (>= 1.99~20101210-1ubuntu2); however:
  Package grub-pc is not configured yet.

dpkg: error processing package grub-gfxpayload-lists (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 samba-common
 samba-common-bin
 samba
 unattended-upgrades
 winbind
 grub-pc
 grub-gfxpayload-lists
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

and then when i try to remove one of them (samba-common) with the command ```
sudo apt-get remove samba-common
``` i get this another output (because it's too long output) :

[https://paste.ubuntu.com/25596136/](https://paste.ubuntu.com/25596136/)

and i have no idea how to fix this problem.[URL="https://paste.ubuntu.com/25596136/"]


[/URL][URL="https://paste.ubuntu.com/25596136/"]

[/URL]

---

### Post by ian-weisser on 2017-09-23
Looks like your dpkg database has been completely deleted.
If so, that's mighty bad. It means that the system can no longer install or remove packages.

Do you want to solve the problem and learn a bit?
Or do you simply want the fastest answer to a working system?

---

### Post by ajgreeny on 2017-09-23
Have you been doing anything in **/var/lib/dpkg/info/** that might have removed the thousands of files that normally sit in that folder?

---

### Post by someoe on 2017-09-23
i found in my /var/lib/dpkg/info 1,232 items but he missing packages from the output is 1852.

and if i have been messing around with the system files i will tel you yes i did it :

i wanted to remove Java because i had installed Java in my system and for some reason i have moved to root nautilus and removed all the files with the name java amnd accidentally removed another file and i didn't realize what i had done except after deleting the file, and you know that root nautilus removes the files without undo.

and this all happend after mounting and updating and fix missing packages from a live cd because my Ubuntu was in login loop and i fixed it by booting into a live cd and mounting my files then download the missing packages and update and upgrade

i there anyway to check if Ubuntu system files or configuration files is missing and try to restore them?

---

### Post by someoe on 2017-09-23
my xsession-errors :

```

openConnection: connect: No such file or directory
cannot connect to brltty at :0
upstart: unity-gtk-module main process (1273) terminated with status 71

```

my xsession-errors.old :

```

openConnection: connect: No such file or directory
cannot connect to brltty at :0
upstart: unity-gtk-module main process (3827) terminated with status 71
upstart: update-notifier-crash (/var/crash/unattended-upgrades.0.crash) main process (11728) terminated with status 1
upstart: bamfdaemon main process (3988) killed by TERM signal
upstart: indicator-bluetooth main process (4084) killed by TERM signal
upstart: indicator-power main process (4087) killed by TERM signal
upstart: indicator-datetime main process (4088) killed by TERM signal
upstart: indicator-printers main process (4095) killed by TERM signal
upstart: indicator-session main process (4096) killed by TERM signal
upstart: indicator-application main process (4146) killed by TERM signal
upstart: indicator-application pre-stop process (17098) killed by TERM signal
upstart: gnome-session (Unity) pre-stop process (17099) killed by TERM signal
upstart: window-stack-bridge main process (3854) killed by HUP signal
upstart: hud main process (4017) killed by HUP signal
upstart: unity-settings-daemon main process (4019) killed by HUP signal
upstart: gnome-session (Unity) main process (4026) killed by HUP signal
upstart: unity-panel-service main process (4032) killed by HUP signal
upstart: indicator-messages main process (4080) killed by HUP signal
upstart: indicator-keyboard main process (4091) killed by HUP signal
upstart: indicator-sound main process (4092) killed by HUP signal
upstart: gpg-agent post-stop process (17100) killed by HUP signal
upstart: job gnome-session (Unity) failed to stop
upstart: Disconnected from notified D-Bus bus

```

my history.log (i don't know where is the old history this is what i found):
[https://paste.ubuntu.com/25599366/](https://paste.ubuntu.com/25599366/)

---

### Post by someoe on 2017-09-23
news :

"program problem detected" when i report the problem i get this massege "It seems you have modified the contents of "/etc/apt/apt.conf.d/10periodic".  Would you like to add the contents of it to your bug report?" and there's (no) and (yes) options, and i have selected (yes)

---

### Post by ian-weisser on 2017-09-23
> **someoe said:**
> i there anyway to check if Ubuntu system files or configuration files is missing and try to restore them?

No, because those files come from packages. dpkg maintains the list of those system files in a database...that is now incomplete.

More importantly, 'missing system files' does not seem to be the underlying problem. The partially-deleted dpkg database seems to be the essential problem.

One solution is to back up your data and reinstall.
Another solution is to determine the list of packages with missing dpkg database entries, and use apt to reinstall those packages.

---

### Post by someoe on 2017-09-23
i had tried to remove Java and install it again and that's what happend :

1- removed it with ```
sudo apt-get remove java-commom
```

and 2- tried to install with it synaptic with the package (default-jre) and i got this error message :

```

E: java-common: subprocess installed post-installation script returned error exit status 1
E: openjdk-8-jre-headless: 60.9756:dependency problems - leaving unconfigured
E: default-jre-headless: dependency problems - leaving unconfigured
E: openjdk-8-jre: 65.8537:dependency problems - leaving unconfigured
E: default-jre: dependency problems - leaving unconfigured
E: ca-certificates-java: dependency problems - leaving unconfigured

```

and then i checked it and i found that the package is installed .... but it doesn't work like other package and from this error i can't install any package without error message like the one above.

---

### Post by ian-weisser on 2017-09-24
That's expected behavior. You have a broken apt.

---

### Post by someoe on 2017-09-24
i have followed all answer in this question and and i got the same : [https://askubuntu.com/questions/118749/package-system-is-broken-how-to-fix-it](https://askubuntu.com/questions/118749/package-system-is-broken-how-to-fix-it)

is there any GOOD fix or i have reinstall Ubuntu

---

### Post by ian-weisser on 2017-09-24
That askubuntu thread won't help you. The way you broke apt is different from the way they broke apt, so how to fix is different.
(Their problem was incompatible packages, one trying to overwrite the other. None of the proposed solutions is a useful fix)

There are three ways to fix the problem - each has it's pain points.
1) Reinstall.
2) Use dpkg to uninstall all the affected packages. Then use apt to reinstall them.
3) Manually download all the affected packages, then use apt --force to reinstall them.

---

### Post by someoe on 2017-09-24
finally i will reinstall Ubuntu and i want you to tell me how to avoid this kind of problems in the future? :D

---

### Post by ian-weisser on 2017-09-24
Avoiding this kind of problem is easy: Do not delete files from the apt database.
In over a decade, none of my machines have ever has this kind of of problem.

---

### Post by ajgreeny on 2017-09-25
> **ian-weisser said:**
> Avoiding this kind of problem is easy: Do not delete files from the apt database.
In over a decade, none of my machines have ever has this kind of of problem.
In fact do not delete or edit anything at all from the root filesystem unless there is 
[LIST=1]
[*]a very good reason for doing so
[*]you know exactly what you're doing and why
[*]there is no alternative answer to your problem
[*]you have a way to reverse anything you have done
[*]
[/LIST]
There is a very good reason for a user being unable to work on the filesystem files and folders; that being that you, as user, can completely kill your OS if you do something silly.

It may be theoretically possible for you to right the wrongs you have now made for yourself but I believe it will be far quicker and more certain of success for you to re-install.

---

