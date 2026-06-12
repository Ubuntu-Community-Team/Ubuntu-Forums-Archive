---
title: "broken package, cant uninstall or reinstall"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by hoehaver on 2006-07-13
i have been having problems with samba, and wine. but im not worried about wine right now. samba is broken and when i try to fix it by running the command sudo apt-get install -f it gives me this  
john@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  samba
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 7250kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 115215 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--remove):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
john@ubuntu:~$


and when i try to uninstall it, it gives me this.
E: samba: subprocess pre-removal script returned error exit status 102
any ideas??? i really need some help. i cant upgrade because of this. i mean upgrade anything, i try to deselect samba but it wont let me.

---

### Post by hoehaver on 2006-07-13
i just tryed this in hopes that i could deselect the "samba" download  
john@ubuntu:~$ sudo apt-get upgrade -d
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.22-1ubuntu3) but 3.0.22-1ubuntu3.1 is installed
E: Unmet dependencies. Try using -f.
john@ubuntu:~$

unmet dependencies..hm...can someone help??

---

### Post by carmelo on 2006-07-13
I had the same problem

Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--remove):
subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

in /etc/rc2.d i found a dangling symlink K09samba -> /samba (bad link)
i modified it by hand linking to the correct location:
$ cd /etc/rc2.d
$ sudo rm K09samba
$ sudo ln -s ../init.d/samba K09samba

and i retry the update with success
$ sudo apt-get install -f

bye
Carmelo

---

### Post by hoehaver on 2006-07-13
thank you very much, my problem is sloved...thank you again

---

### Post by Sionide on 2006-07-15
Thanks for the advice, I had this problem too..

Apart from I had "invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba" instead. Your fix worked when I substituted S91samba in...

---

### Post by cre8ivgil on 2006-07-16
Thanks a lot Carmelo, had the same problem and got it fixed in a couple minutes with your advice.

---

### Post by fredsea on 2006-07-17
Gee, I hate to clog this thread, but I was going nuts over this broken package, and *shazam* it's fixed! Sooooo many thanks Carmelo. I realized how good Ubuntu is, when it installed without a glitch (as opposed to most any other distribution), but I had not experienced how great the community is!:D

---

### Post by JNik on 2006-07-20
Thanks carmelo. I had the same problem.

---

### Post by az on 2006-07-20
[https://launchpad.net/distros/ubuntu/+source/samba/+bug/48082](https://launchpad.net/distros/ubuntu/+source/samba/+bug/48082)

---

### Post by ztirffritz on 2006-07-20
Seems to have worked for me too, but I want to know how you figured out what was wrong.

---

### Post by Hacknslash on 2006-07-30
I to would like to know how you worked out what was wrong......

---

### Post by psmffp on 2006-08-07
Most awesome thread. Thank you so much.............

---

### Post by srt4play on 2006-08-12
I had this problem too. Thanks carmelo for the helpful post.

---

### Post by Jon@bayleys.org.uk on 2006-10-28
Still works as of 29/10/06 Thanks mate.

---

### Post by figgles on 2006-12-02
FYI -- fixed my problem, too. Thanks!

---

### Post by lamadredelsapo on 2007-01-12
It worked for me too!

---

### Post by jmagsho on 2007-02-07
Carmelo,

Thanks for the info.  This had me pulling my hair out earlier this evening.   Very much appreciated!

---

