---
title: "Unable to locate libgtk1.2"
date: 2010-12-16
forum: Installation &amp; Upgrades
---

### Post by Anomaly26 on 2010-12-16
Hello all!

I'm a fairly new user to Ubuntu, and though it is currently just a temporary solution for a crashed Windows drive, I want to learn as much about it as I can while I have it.

Thus far, I know a number of fairly basic commands; sudo, gedit, cd, ls, but not much beyond that.

I've been attempting to install the demo to a game called Darwinia for some time now, but when I attempt to extract the .sh archive downloaded from the company site, I'm given this message.

```
root@Molly:~/Downloads# ./darwinia-demo2-1.3.0.sh
Verifying archive integrity... All good.
Uncompressing Darwinia demo2 1.3.0.......................................................................
/home/wordweaver/.setup6782: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```
I've gone through a number of threads where users have encountered similar problems, and in almost all cases, they were resolved by using apt-get to locate the file under an abbreviated name; libgtk1.2.  However, when I attempt this, I get the following.

```

root@Molly:~/Downloads# sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgtk1.2
```I've also tried using a custom script that is used with the command 'getlibs', and it returns with this.

```
root@Molly:~/Downloads# getlibs libgtk-1.2.so.0
libgtk-1.2.so.0: libgtk1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libgtk1.2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgtk1.2 has no installation candidate
```This would imply that there is a newer version of this file somewhere, but if there is a way to locate it easily, I haven't encountered it yet.  Any suggestions are plenty welcome.

Thanks for your time :D

---

