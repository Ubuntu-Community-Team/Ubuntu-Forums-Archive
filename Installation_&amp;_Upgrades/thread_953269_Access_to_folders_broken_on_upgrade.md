---
title: "Access to folders broken on upgrade"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by jaklumen on 2008-10-20
I got the $HOME/.dmrc file is being ignored error at the login screen when I upgraded to Intrepid.

I followed these instructions at [this site here]("http://mihirknows.blogspot.com/2008/06/homedmrc-file-is-being-ignored-solved.html")
(I replaced 'xx' with my username as indicated):

```
sudo chmod 644 /home/xx/.dmrc
sudo chown xx/home/xx/.dmrc
sudo chmod -R 700 /home/xx
sudo chown -R xx/home/xx

```

The first three commands worked without a hitch, but got the following error

chown: missing operand after `jaklumen/home/jaklumen'

on the fourth.

I cannot access Home folders from the "Places" menu on the taskbar, but only if I click on a mounted secondary drive on the Desktop.  I'm fairly certain if I could properly execute chown on the fourth command, it would fix it, but I'm really not a coder and I don't really know how to do it.

Any help would sure be appreciated.  When I was out in the Google jungle looking for solutions, so to speak, it seemed the .dmrc error was pretty common when upgrading.  The Blogger post I linked to seemed to have the most complete solution, but I couldn't get it all to work.

---

### Post by dave.com on 2008-10-20
Line 2 looks more like the code for your "error on line 4" syntax:

```
sudo chown xx/home/xx/.dmrc

```

I may be wrong but chown usually goes like this```
# chown xxx:yyy /home/xxx
``` where xxx is user name and yyy is group name thus you can make user is owned by user - eg.```
#chown dave:dave /home/dave
#chown dave:dave /home/dave/.dmrc
#chmod 644 /home/dave/.dmrc
```

Is root owned by root: ```
# ls -la /bin/su
``` This should return "# -rws-xr-x  1 root (the '1' before root indicates the number of links to this file). To set default root permissions: ```
#chown root:root /bin/su
#chmod 4755 /bin/su
```  
A checklist: ```
#ls -l /bin/su 
#ls -l /etc/group
#ls -l /etc/passwd
```

If you ever need to add read and execute permissions to root (if that has changed for any reason): ```
#chmod a+rx /
or
#chmod 755 /
```

All this info used to be posted in the Gentoo archives, so visit the Gentoo site and give a thank you to some forum Mod there if you find it usefull.

---

### Post by jaklumen on 2008-10-20
> **dave.com said:**
> Is root owned by root: ```
# ls -la /bin/su
``` This should return "# -rws-xr-x  1 root (the '1' before root indicates the number of links to this file).

Yes.

> To set default root permissions: ```
#chown root:root /bin/su
#chmod 4755 /bin/su
```

I get the following error message: chown: changing ownership of `/bin/su': Operation not permitted
  
> A checklist: ```
#ls -l /bin/su 
#ls -l /etc/group
#ls -l /etc/passwd
```

Returns
-rwsr-xr-x 1 root root 31012 2008-06-09 11:10 /bin/su
-rw-r--r-- 1 root root 1390 2008-10-18 17:25 /etc/group
-rw-r--r-- 1 root root 1932 2008-10-18 17:25 /etc/passwd

in that respective order.

> If you ever need to add read and execute permissions to root (if that has changed for any reason): ```
#chmod a+rx /
or
#chmod 755 /
```

Get the following error message:
chmod: changing permissions of `/': Operation not permitted

---

### Post by jaklumen on 2008-10-23
Anyone?  Still need a little more help.

---

### Post by jaklumen on 2008-10-30
C'mon... this really isn't exactly intuitive here.

---

