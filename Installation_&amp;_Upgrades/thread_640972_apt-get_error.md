---
title: "apt-get error"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by BrOSs on 2007-12-14
dany@:~$ sudo apt-get install firefox
sudo: unable to lookup  via gethostbyname()

-----------
when I'm trying to install firefox or any app there is that error!..

if u need any additional info in order to help me pls let me know x)

thks..

---

### Post by yabbadabbadont on 2007-12-14
Does the following resemble anything that you have done?

[https://answers.launchpad.net/ubuntu/+question/2583](https://answers.launchpad.net/ubuntu/+question/2583)

---

### Post by PmDematagoda on 2007-12-14
Post the results of:-

```
sudo apt-get update
```
and
```

cat /etc/apt/sources.list
```

And would you post what you use to connect to the internet and how you connect to the internet.

---

### Post by BrOSs on 2007-12-14
dany@:~$ sudo apt-get update
sudo: unable to lookup  via gethostbyname()
dany@:~$ cat /etc/apt/sources.list

deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) dapper-backports main restricted univ                                       erse multiverse
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) dapper-backports main restricted                                        universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

----------

I'm connected by ethernet. Is an adsl services.. from Mexico.

---

### Post by taurus on 2007-12-14
Did you by any chance change the name of your machine lately?

---

### Post by BrOSs on 2007-12-15
No I didn't.. =/

---

### Post by BrOSs on 2007-12-15
I already post my terminal log..

thks x)

---

### Post by BrOSs on 2007-12-15
when I try to use any sudo command there is this error message--

sudo: unable to lookup  via gethostbyname()

---

### Post by taurus on 2007-12-15
Can you post

```
cat /etc/hostname
cat /etc/hosts
```

---

### Post by BrOSs on 2007-12-16
dany@:~$ cat /etc/hostname
-laptop
dany@:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       -laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
dany@:~$              

hope that helps

---

### Post by yabbadabbadont on 2007-12-17
Edit both files and remove the "-" (dash) from in front of "laptop".  It isn't a valid character in a hostname.  (at least it causes a lot of trouble)  You will need to start your editor with sudo in order to have permission to save your changes.  Once you have finished with your edits, you will need to logout and reboot.

---

### Post by BrOSs on 2007-12-17
man!.. i can't use sudo! any command is allowed.. so, it won't works

=/

---

### Post by yabbadabbadont on 2007-12-17
:lol:

Sorry about that.  I completely forgot about that being the initial issue...  :oops:

Reboot into failsafe mode.  You will then be able to edit the files.  If you are not familiar with a command line editor, I would suggest that you use "nano".

If Ubuntu is the only OS on your machine, you will probably need to hit the Escape key at the grub prompt to see the menu.

---

### Post by aysiu on 2007-12-17
> **yabbadabbadont said:**
> :lol:

Sorry about that.  I completely forgot about that being the initial issue...  :oops:

Reboot into failsafe mode.  You will then be able to edit the files.  If you are not familiar with a command line editor, I would suggest that you use "nano".

If Ubuntu is the only OS on your machine, you will probably need to hit the Escape key at the grub prompt to see the menu.
*failsafe mode* is probably called *recovery mode* in your boot menu.

This will log you in as root.

When you get to the command prompt, type ```
nano -B /etc/hosts
``` make the change, press Control-X, Y, Enter. Then type ```
reboot
```

---

### Post by BrOSs on 2007-12-17
thks man.. I'll try
this is not the only OS.. winXP too

---

### Post by yabbadabbadont on 2007-12-17
> **aysiu said:**
> *failsafe mode* is probably called *recovery mode* in your boot menu.

This will log you in as root.

When you get to the command prompt, type ```
sudo nano -B /etc/hosts
``` make the change, press Control-X, Y, Enter. Then type ```
reboot
```

I guess I should have checked menu.lst for the correct wording.  :D

By the way, he can't use sudo....  you made the same mistake that I did.  :lol:

Edit: He also needs to edit his /etc/hostname file too.  Not just /etc/hosts.

---

### Post by aysiu on 2007-12-17
> **yabbadabbadont said:**
> I guess I should have checked menu.lst for the correct wording.  :D

By the way, he can't use sudo....  you made the same mistake that I did.  :lol:

Edit: He also needs to edit his /etc/hostname file too.  Not just /etc/hosts.
Sorry. I've corrected the post.

Actually, I believe if you're logged in as root, *sudo* should work. But if you're logged in as root, you also don't need *sudo* anyway.

---

### Post by yabbadabbadont on 2007-12-17
> **aysiu said:**
> Actually, I believe if you're logged in as root, *sudo* should work. But if you're logged in as root, you also don't need *sudo* anyway.

I think that you are correct on that.  I too usually include the sudo just because the novices are used to seeing it before admin type commands.

---

### Post by BrOSs on 2007-12-17
thks 4all.. hahaha the dash was the real problem!
man.. u rocks, thks so much x)

---

### Post by BrOSs on 2007-12-18
the questions is already answer.. 
thks for the ones who insterested in this topic.

readulater x)

---

