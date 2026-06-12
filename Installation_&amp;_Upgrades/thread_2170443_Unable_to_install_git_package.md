---
title: "Unable to install git package"
date: 2013-08-26
forum: Installation &amp; Upgrades
---

### Post by hema2 on 2013-08-26
Hi Kubuntu Team,
I am new to Kubuntu. I am trying to install git package from terminal using the command sudo apt-get install git                                                                           
When I run this command from terminal I am getting the error unable to locate the package. Can anyone please help me out in solving this error.
Thanks in advance.

---

### Post by steeldriver on 2013-08-26
Hello and welcome to the forums

Let's start with what version of kubuntu you are running - if you're not sure open a terminal and use the commands

```

uname -a

cat /etc/lsb-release

```

---

### Post by SeijiSensei on 2013-08-26
Usually that error means that the installer cannot connect to the repositories.  Have you installed any other software from the command line besides git?  Did that fail as well?

Look in /etc/apt/sources.list and see what server(s) you are using.  Can you ping those servers by name?

Perhaps you just need to run "sudo apt-get update" to tell Ubuntu to get the most recent package lists from from the repositories before running "sudo apt-get install git".

---

### Post by hema2 on 2013-08-27
Hi steeldriver
here are the specifciations:
Distributor ID: Ubuntu
Description:    Ubuntu 13.04
Release:        13.04
Codename:       raring

for kernel version I ran the command uname -r 
 3.8.0-19-generic

---

### Post by hema2 on 2013-08-27
Hi SeijiSensei ,
It is giving me the same error whatever may be the package I am trying to install. "unable to locate package git " I am getting when I tried with the command 
"sudo apt-get install git" . If I run "sudo apt-get update" I am getting errors like " Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/raring-security/Release.gpg) "

---

### Post by steeldriver on 2013-08-27
It sounds like there's a problem with your internet connection, or a proxy that's blocking access to the repositories

---

