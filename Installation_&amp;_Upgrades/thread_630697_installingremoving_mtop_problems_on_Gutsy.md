---
title: "installing/removing mtop problems on Gutsy"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by Red.Heron on 2007-12-03
Fun little problem here... I run Gutsy on AMD64 and I had a need to run mtop to test some web pages I'm writing.


Since I didn't have mtop, I went to install it, got an error with sudo, so I logged in as root and tried again:

```

root@localhost:~# apt-get install mtop
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  mtop
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
Need to get 51.7kB of archives.
After unpacking 229kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com gutsy/universe mtop 0.6.6-1.2 [51.7kB]
Fetched 51.7kB in 0s (61.5kB/s)
Preconfiguring packages ...
Selecting previously deselected package mtop.
(Reading database ... 260687 files and directories currently installed.)
Unpacking mtop (from .../mtop_0.6.6-1.2_all.deb) ...
Setting up mtop (0.6.6-1.2) ...
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
dpkg: error processing mtop (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mtop
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@localhost:~# apt-get remove mtop
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  mtop
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 229kB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 260699 files and directories currently installed.)
Removing mtop ...
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
root@localhost:~# 

```This doesn't look right to me, but I don't know how to fix it, being a non-programming novice Ubuntu user. Any ideas what I should do or whom to contact?

(And no, my computer's name is not "localhost", I changed it to preserve privacy.)

---

### Post by maxlock on 2008-02-06
just hit this problem myself. for future google'rs here goes

 As the root user you need to clear the password for the root mysql user then install mtop, then set it back...

 1. $ sudo bash
 (naughty way to get a root shell)

 2. # /usr/bin/mysqladmin -u root -p password ''
 (that's two single quotes, then put your mysql root password in)

 3. # apt-get install mtop
 (install mtop)

 4. # /usr/bin/mysqladmin -u root -p password 'mypassword'
 (set the mysql root user password back to 'mypassword')

 -Max.

---

### Post by kanubis on 2008-03-17
maxlock, the google feeding is appreciated.  I had hoped to find a way to either clear the postinstall error condition, or fix the package postinstaller to use skip logging in.  I actually installed mtop to use remotely anyway.

There's no reason to need a root shell to do those steps though, only the apt-get step even needs sudo.  

Really I hope the package can be fixed, there's no reason to require passwordless root especially since the man page for mtop itself likes a passwordless mysqltop user and gives the commands to install that user.

---

