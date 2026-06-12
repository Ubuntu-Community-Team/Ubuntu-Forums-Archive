---
title: "apt-get / dpkg problems"
date: 2005-11-02
forum: Installation &amp; Upgrades
---

### Post by baked on 2005-11-02
Ok, this may or may not be in the right forum section but here goes.  I went to uninstall wine today and using apt.  When I run the command 'apt-get remove wine'  it comes out with this....

root@laptizzle:/home/baked# apt-get remove wine
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  wine
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 56.8MB disk space will be freed.
Do you want to continue [Y/n]? y
E: Sub-process /usr/bin/dpkg exited unexpectedly

I have been a debian user for a long time and have tried all the tricks in the book.  I have looked it up on google, in ubuntu, and other linux forums but can not solve the problem.  I can not even install anything at this point using apt-get. 

I've tried everything everyone has said to do and nothing helps, I've searched for packages that were not installed right and nothing is listed.  I'm pretty much at a stump....

If anyone has concured this problem please let me know how you did it.  I really do not want to have to do a freaking re-install to fix this.  

Thanks for any help,

Tommy.

---

### Post by heimo on 2005-11-02
Well... not knowing what tricks you tried, it's quite hard to know if this will help, but I'd try to remove (or move) /var/lib/dpkg/info/wine* files, apt-get --purge remove wine, reinstall wine and once again remove (I tend to do this to make sure everything works fine again). Did you already try this?

---

### Post by baked on 2005-11-03
I have tried the purge option for apt-get and it does the same thing.  If i try and resinstall wine it does the same thing, in fact, If i try and install anything it has that error.  I've tried dpkg --configure -a to try and fix any mis installed item but that has no luck.  Here is what I get....

baked@laptizzle:~$ sudo dpkg --configure -a
Password:
Bus error

If i try and install anything it does the same thing and quits with a bus error.  I'm pretty lost at what to do, but lots of people have the same problem as I and I can't seem to find a solution....

---

### Post by az on 2005-11-03
That is the first time in a long time that I have seen that error.

Try

sudo dpkg --clear-avail
sudo apt-get update
sudo dpkg --configure -a


If that still fails, well, do you have hardware problems?

---

### Post by baked on 2005-11-03
Azz, your the man....

I appreciate the help a lot.  I'm guessing that first command clears the database of files that dpkg collects.  I found that it had to be the database of deb files installed because i tried to uninstall files just before I checked this thread and it did not see wine or gaim or any other program installed.  But once again thanks for the help.....

I searched like 20 million web sites with people having this problem and your the first person to come up with a fix.  You saved me a reinstall!  

P.S.  Ubuntu rocks!

Thanks, 

Tommy.

---

