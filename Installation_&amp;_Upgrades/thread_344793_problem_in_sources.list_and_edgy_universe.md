---
title: "problem in sources.list and edgy universe"
date: 2007-01-23
forum: Installation &amp; Upgrades
---

### Post by djcaston on 2007-01-23
I'm having several problems with my update files. When I open add/remove programs, I get this message:

Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

When trying to open synaptic, I get this message:

An error occured

The following details are provided:

E: Malformed line 3 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

---

### Post by taurus on 2007-01-23
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list.d/edgy-universe.list
```
Look at line 3 to see what's wrong with it.  Otherwise, post your /etc/apt/sources.list.d/edgy-universe.list here.

---

### Post by djcaston on 2007-01-23
im not sure. heres the list

# automatically added by gnome-app-install on 2006-11-18 19:24:49.673409
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates universe

---

### Post by carl.alv on 2007-03-26
I have the same problem, but when I go to /etc/apt/sources.list.d/ I find the directory empty, what does this means?

---

### Post by taurus on 2007-03-26
> **carl.alv said:**
> I have the same problem, but when I go to /etc/apt/sources.list.d/ I find the directory empty, what does this means?

What is the exact error message and what is the output of this command from a terminal?

```
ls -la /etc/apt/sources.list.d/
```

---

### Post by carl.alv on 2007-03-26
It says:

```
 ls -la /etc/apt/sources.list.d/
total 8
drwxr-xr-x 2 root root 4096 2006-09-28 01:44 .
drwxr-xr-x 4 root root 4096 2007-03-26 09:30 ..

```

---

### Post by carl.alv on 2007-03-26
I forgot to say that my error message is exacly the same as cjcaston's :)

---

### Post by carl.alv on 2007-03-26
I forgot to say that my error message is exacly the same as djcaston's :)

---

### Post by taurus on 2007-03-26
Run this command from a terminal and post the output here.

```
sudo aptitude update
```

---

### Post by carl.alv on 2007-03-26
This is the output:

```

E: Malformed line 3 in source list /etc/apt/sources.list (dist parse)
E: Malformed line 3 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

```

---

### Post by taurus on 2007-03-26
Your error message is related to /etc/apt/sources.list, not /etc/apt/sources.list.d/edgy-universe.list.  There is something wrong with line 3 in there so you can either post your /etc/apt/sources.list here or just place a # in front of line 3 to comment it out.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by carl.alv on 2007-03-26
And this is how sources.list looks like:

```



deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025)]/ edgy


## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://fr.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://fr.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://fr.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://fr.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

# deb http://security.ubuntu.com/ubuntu edgy-security universe
deb http://archive.ubuntu.com/ubuntu/ edgy universe main multiverse restricted
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe


```

I thank you in advance for any help you could give me

---

### Post by taurus on 2007-03-26
Nothing much (repos) on that list.  Why don't you edit it

```
sudo cp /etc/apt/sources.list  /etc/apt/sources.list.bak
gksudo gedit /etc/apt/sources.list
```
and remove everything in there.  Then, paste these lines to it.

```

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu edgy universe
deb-src http://archive.ubuntu.com/ubuntu edgy universe

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu edgy multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy multiverse

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu edgy-commercial main 

```
Save the new list and run those two commands from a terminal again.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by carl.alv on 2007-03-26
It worked!!! thanks a lot Taurus!!!!!!

---

### Post by taurus on 2007-03-26
You're welcome.

---

