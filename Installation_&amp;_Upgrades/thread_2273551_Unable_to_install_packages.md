---
title: "Unable to install packages"
date: 2015-04-13
forum: Installation &amp; Upgrades
---

### Post by Mark_Jaffe on 2015-04-13
Running Trusty 14.04.1, when I try to install I get message:


mjaffe@mjaffe-ThinkCentre-M51:~/Development$ sudo apt-get install git-core
[sudo] password for mjaffe: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Looking at the (edited) process list, I see some likely suspects:

[SIZE=1][FONT=courier new]root      1051     1  0 Apr11 ?        00:00:00 anacron -s[/FONT][/SIZE]
[SIZE=1][FONT=courier new]
[/FONT][/SIZE]
[SIZE=1][FONT=courier new]root      1848  1051  0 Apr11 ?        00:00:00 /bin/sh -c run-parts --report /etc/cron.daily[/FONT][/SIZE]
[SIZE=1][FONT=courier new]root      1849  1848  0 Apr11 ?        00:00:00 run-parts --report /etc/cron.daily[/FONT][/SIZE]
[SIZE=1][FONT=courier new]root      1859  1849  0 Apr11 ?        00:00:00 /bin/sh /etc/cron.daily/apt[/FONT][/SIZE]
[SIZE=1][FONT=courier new]
[/FONT][/SIZE]
[SIZE=1][FONT=courier new]root      2483  1859  0 Apr11 ?        00:07:01 /usr/bin/python3 /usr/bin/unattended-upgrade[/FONT][/SIZE]
[SIZE=1][FONT=courier new]root      2935  2483  1 Apr11 ?        00:58:41 /usr/bin/python3 /usr/bin/unattended-upgrade[/FONT][/SIZE]
[SIZE=1][FONT=courier new]
[/FONT][/SIZE]
[SIZE=1][FONT=courier new]root     15980  2935  0 Apr11 ?        00:00:00 /usr/bin/dpkg --status-fd 8 --configure emacsen-common:all emacs23-common:all libc-dev-bin:i386 linux-libc-dev:i386 libc6-dev:i386 libc6-dbg:i386 emacs23-bin-common:i386 libfreetype6[/FONT][/SIZE]
[SIZE=1][FONT=courier new]root     15981 15980  0 Apr11 ?        00:00:00 /bin/sh /var/lib/dpkg/info/emacsen-common.postinst configure 1.4.22ubuntu1[/FONT][/SIZE]
[SIZE=1][FONT=courier new]root     15985 15981  0 Apr11 ?        00:00:00 /usr/bin/perl -w /usr/lib/emacsen-common/emacs-package-install --postinst emacsen-common[/FONT][/SIZE]
[SIZE=1][FONT=courier new]root     15988 15985  0 Apr11 ?        00:00:00 [emacs-package-i] <defunct>[/FONT][/SIZE]
[SIZE=1][FONT=courier new]root     15995 15985  0 Apr11 ?        00:00:00 /bin/sh /usr/lib/emacsen-common/packages/install/emacsen-common xemacs21[/FONT][/SIZE]
[SIZE=1][FONT=courier new]root     15999 15995  0 Apr11 ?        00:00:00 xemacs21 --no-init-file --no-site-file -batch -f batch-byte-compile /etc/xemacs21/site-start.d/00debian-vars.el /usr/share/xemacs21/site-lisp/debian-startup.el[/FONT][/SIZE]

root@mjaffe-ThinkCentre-M51:~# uptime
 19:17:22 up 2 days,  5:09,  1 user,  load average: 0.00, 0.05, 0.06

What can I do to fix this?

---

### Post by Bashing-om on 2015-04-13
Mark_Jaffe; Hi !

In this case :
> 
E: Unable to lock the administration directory (/var/lib/dpkg/), [color=red]is another process using it[/color]?

Does it apply that another instance of the package manager is open ? Only one may be active at any given time - apt, dpkg, synaptic, Software Center;  any of them running in another console ?.
Close all out and back out of everything and reboot the system

does apt behave after the reboot as expected ?

[INDENT][INDENT][INDENT]could be as simple as
[/INDENT][/INDENT][/INDENT]

---

### Post by Mark_Jaffe on 2015-04-14
The update is being controlled by cron

---

### Post by Mark_Jaffe on 2015-04-14
After reboot I had to do dpkg --configure -a
Now it is OK

---

### Post by Mark_Jaffe on 2015-04-14
No, actually. Not OK. Problems with 'dpkg --configure -a' 
Errors were encountered while processing:
 emacsen-common
 xemacs21-support
 emacs23-common
 xemacs21-mule
 xemacs21
 emacs23-bin-common
 xemacs21-bin
 emacs23

How does this get fixed?

---

### Post by Bashing-om on 2015-04-14
Mark_Jaffe; Hey ;

I would consider re-configuring 'emacs' or perhaps better might be to RE-install emacs.
Remember to update/upgrade prior to the repair.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

