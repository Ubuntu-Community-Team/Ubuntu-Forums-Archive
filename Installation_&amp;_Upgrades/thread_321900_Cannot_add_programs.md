---
title: "Cannot add programs"
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by chejose on 2006-12-19
For the past couple of days I have trying to finish my first linux instalation... frustrated, but not giving up!

My internet connection is fine. Browser works 100%
But when I try to add programs using the graphical install/remove, it first wants to update, but after 1/2 hour does nothing.

When I try using sudo apt-get update, it hangs on the security connection as follows:

jose@jose-desktop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.c

I suspect that the problem has something to do with the sources.list (pure guess) and I put it below:

jose@jose-desktop:~$ cat /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse
jose@jose-desktop:~$ 

Hopefully that will give someone a lead. Please answer assuming that I don't know anything about Linux yet (true).

---

### Post by TheWizzard on 2006-12-19
to install a new program you need to type
```
sudo aptitude install gimp
```
to install the gimp (as for an example).

---

### Post by lamego on 2006-12-19
> 0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.c
You must have a problem with your dns config or you have specified a proxy for the upgrades, archive.ubuntu.com should not resolve to 1.0.0.0 as seen in your message..

---

### Post by chejose on 2006-12-19
Yes, I tried using aptitude to install a program, but the result was negative:

jose@jose-desktop:~$ sudo aptitude install mozilla-thunderbird
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be installed:
  mozilla-thunderbird 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.7MB of archives. After unpacking 30.3MB will be used.
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  mozilla-thunderbird 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": yes
Writing extended state information... Done
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main mozilla-thunderbird 1.5.0.7-0ubuntu1
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
jose@jose-desktop:~$ 

The connection timed out, but not because of the internet connection... I am using it to send this!

I appreciate suggestions as to what the problem may be, but I am too new to Linux to know the solution. Hopefully someone can offer posible solutions.

---

### Post by TheWizzard on 2006-12-21
sometimes a repo is not available or very busy. you can try commenting out this repo and (if needed) add another repo.

---

