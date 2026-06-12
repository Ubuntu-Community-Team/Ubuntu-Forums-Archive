---
title: "Can't use sudo apt upgrade"
date: 2023-12-14
forum: Installation &amp; Upgrades
---

### Post by babouchedlzozokk on 2023-12-14
Hello,
I Recently moved to Ubuntu and fresh installed to my pc. To be sure everything was cleaned and installed, i try to run 'sudo apt update' and for this no problem but when i run 'sudo apt upgrade' i get a strange answer
[PHP]
popoff@PourLaMerePatrie:~$ sudo apt upgrade
[sudo] password for popoff: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-dri : Breaks: libgl1-amber-dri but 21.3.9-0ubuntu1~oibaf~j is to be installed
 libgl1-mesa-dri:i386 : Breaks: libgl1-amber-dri but 21.3.9-0ubuntu1~oibaf~j is to be installed
E: Broken packages
[/PHP]
I really dont understand this behavior and how to fix this problem, already thx for your help

---

### Post by ajgreeny on 2023-12-14
Please run command ```
sudo apt update
``` and show us the full output of the command.

---

### Post by yancek on 2023-12-14
After installing Ubuntu, did you install or try to install additional software and if so, what?  Did you try to install third party software, not from the Ubuntu repositories.  You might read through the page at the link below which discusses this problem and provides some options to try to fix it.

[https://www.baeldung.com/linux/unmet-dependencies-apt-get](https://www.baeldung.com/linux/unmet-dependencies-apt-get)

---

### Post by babouchedlzozokk on 2023-12-14
Here For you:

```
popoff@PourLaMerePatrie:~$ sudo apt update
Hit:1 http://archive.canonical.com/ubuntu jammy InRelease
Hit:2 http://security.ubuntu.com/ubuntu jammy-security InRelease               
Hit:3 http://us.archive.ubuntu.com/ubuntu jammy InRelease                      
Hit:4 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:5 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease
Hit:6 https://apt.draugeros.org strigoi InRelease
Hit:7 https://apt.draugeros.org strigoi-graphics InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
344 packages can be upgraded. Run 'apt list --upgradable' to see them.

```

---

### Post by SeijiSensei on 2023-12-14
Now try running "sudo apt upgrade" again. You must refresh the package lists with "sudo apt update" before doing any upgrades. Otherwise you can have incompatible versions of software on your system.

---

### Post by #&amp;thj^% on 2023-12-14
I see this as a problem:
```
Hit:6 https://apt.draugeros.org strigoi InRelease
Hit:7 https://apt.draugeros.org strigoi-graphics InRelease
```
If you remove those from your sources, then update and upgrade.
EDIT: The bad lines Are:
```
 ## Extra Repos added for Drauger OS
        deb https://apt.draugeros.org strigoi main
        ## Development Repos for Drauger OS
        ## ONLY ENABLE IF YOU ARE WILLING TO DEAL WITH BUGS
        deb https://apt.draugeros.org strigoi-dev main

        deb https://apt.draugeros.org strigoi-graphics main
        deb https://apt.draugeros.org strigoi-graphics-dev main
```
Not a good mix.

---

### Post by babouchedlzozokk on 2023-12-14
Thx everybody,it worked, i can finally do what i want, i hope you will all have a beautiful week

---

