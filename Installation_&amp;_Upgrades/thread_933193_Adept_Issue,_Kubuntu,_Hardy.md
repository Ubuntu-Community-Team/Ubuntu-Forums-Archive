---
title: "Adept Issue, Kubuntu, Hardy"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by petragraphics on 2008-09-29
I tried to open adept to install an update, and got this:
> The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem.
I then went to Konsole and did the above and got the following output:
```
donna@PetraGraphics:~$ apt -setup
The program 'apt' can be found in the following packages:
 * openjdk-6-jdk
 * sun-java5-jdk
 * sun-java6-jdk
Try: sudo apt-get install <selected package>
bash: apt: command not found
donna@PetraGraphics:~$ sudo apt -get install
[sudo] password for donna:
sudo: apt: command not found
donna@PetraGraphics:~$ sudo apt-get install
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc                                ess using it?
donna@PetraGraphics:~$ sudo apt-get install
E: Type '//home\\home' is not known on line 56 in source list /etc/apt/sources.l                                ist
E: The list of sources could not be read.

```

Any idea how I can fix this??

---

### Post by natman on 2008-09-29
The Line
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)

sounds like you have two package managers open? do you. To make sure, quit everything! ( adept, synaptice, there guis all of them ) and log out and back in and try
> sudo adept
and quote back the error if any.
Good Luck

---

### Post by petragraphics on 2008-09-29
```
donna@PetraGraphics:~$ sudo apt-get install
E: Type '//home\\home' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
donna@PetraGraphics:~$ sudo apt-get install
E: Type '//home\\home' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
donna@PetraGraphics:~$ sudo adept
sudo: adept: command not found
```

I tried to change line to read
```
//homedeb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
//home
```
I can not save it unless I am root, which I can not seem to do...how can I edit as root??

---

### Post by natman on 2008-09-29
Okay you are using Kubuntu, what happens when you click "K"->System do you see "adept" at the top? it should be there by default. If not im not sure how togo about fixing that.
Sorry

---

### Post by petragraphics on 2008-09-29
Fixed!!!!!!!!!!!!

Removed line 56, was not supposed 2 b there....

---

### Post by Kevbert on 2008-09-29
Try removing the //home from both the first and last lines.

---

