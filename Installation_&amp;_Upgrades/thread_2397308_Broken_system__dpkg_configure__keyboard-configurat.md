---
title: "Broken system : dpkg configure  keyboard-configuration ERROR"
date: 2018-07-27
forum: Installation &amp; Upgrades
---

### Post by allaf on 2018-07-27
Hi everyone,



Out of nowhere my dpkg system broke on my Ubuntu 18.04.1 LTS. I need help I can't figure out how to fix this.



```
root@xx:/home/alex# apt upgrade        
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libxss1:i386 linux-headers-4.15.0-23 linux-headers-4.15.0-23-generic linux-image-4.15.0-23-generic linux-modules-4.15.0-23-generic linux-modules-extra-4.15.0-23-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 
Setting up keyboard-configuration (1.178ubuntu2.3) ...
git: 'LC_CTYPE=en_US.UTF-8' is not a git command. See 'git --help'.
dpkg: error processing package keyboard-configuration (--configure):
 installed keyboard-configuration package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of console-setup-linux:
 console-setup-linux depends on keyboard-configuration (= 1.178ubuntu2.3); however:
  Package keyboard-configuration is not configured yet.

dpkg: error processing package console-setup-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of console-setup:
 console-setup depends on console-setup-linux | console-setup-freebsd | hurd; however:
  Package console-setup-linux is not configured yet.
  Package console-setup-freebsd is not installed.
  Package hurd is not installed.
 console-setup depends on keyboard-configuration (= 1.178ubuntu2.3); however:
  Package keyboard-configuration is not configured yet.

dpkg: error processing package console-setup (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                                                                                    Errors were encountered while processing:
 keyboard-configuration
 console-setup-linux
 console-setup
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


If I try to reinstall it I get : 

dpkg keyboard-configuration broken 

```
root@xxxx:/home/alex# apt-get install --reinstall keyboard-configuration
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxss1:i386 linux-headers-4.15.0-23 linux-headers-4.15.0-23-generic linux-image-4.15.0-23-generic linux-modules-4.15.0-23-generic linux-modules-extra-4.15.0-23-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for keyboard-configuration:amd64
```

Here is my file : 
```
root@xxxx:/home/alex# cat /etc/default/keyboard
# KEYBOARD CONFIGURATION FILE

# Consult the keyboard(5) manual page.

XKBMODEL="pc105"
XKBLAYOUT="fr"
XKBVARIANT="azerty"
XKBOPTIONS=""

BACKSPACE="guess"
```



I already had that weird error trying to update the distribution and had to erase everything... Reminds me of windows

Thanks for your help.

---

### Post by allaf on 2018-07-27
Same in 2015, no one responded sadly [https://ubuntuforums.org/showthread.php?t=2273523&p=13267363#post13267363](https://ubuntuforums.org/showthread.php?t=2273523&p=13267363#post13267363)

---

### Post by QIII on 2018-07-27
grahammechanical answered you in 2015.

You might want to give people more than an hour or two to answer.

Which release of Ubuntu are you using?  Hurd?  Is Hurd required for you package?  console-setup-freebsd?  freeBSD?

Where did you get the package you are trying to install?

Is [this bug]("https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/1770482") possibly what you are running into?  If it is, you might want to click "Does this bug affect you" to turn up the heat.

---

### Post by allaf on 2018-07-28
Thanks for you response.

> **QIII said:**
> grahammechanical answered you in 2015.

Okay but it was the only I was still stuck as you can see in the thread, but anyway I don't want to sound like a jerk.

> **QIII said:**
> 
You might want to give people more than an hour or two to answer.

Of course, I don't demand anything.

> **QIII said:**
> 
Which release of Ubuntu are you using?  Hurd?  Is Hurd required for you package?  console-setup-freebsd?  freeBSD?

Ubuntu 18.04.1 LTS. should have mentioned that in my first post, I'll edit it.

> **QIII said:**
> 
Where did you get the package you are trying to install?

Nowhere. I just ran apt update; apt upgrade.

> **QIII said:**
> 
Is [this bug]("https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/1770482") possibly what you are running into?  If it is, you might want to click "Does this bug affect you" to turn up the heat.


It does look similar, i'll do that thx.
EDIT : turns out I already did it when I ran into that problem during my release upgrade... :(

---

### Post by QIII on 2018-07-28
The bug I referenced seems to be a possible issue, then.

Please take the time to indicate that you are also affected.  That will turn up the heat.

There may not be much to be done about it until Canonical resolves the bug.  There was another bug with the same/similar package in 2015.  You are just lucky, I guess.  :)

---

### Post by allaf on 2018-09-08
Just happened again !! ](*,)](*,)](*,)](*,)](*,)](*,)](*,)](*,)
Need to reinstall my distro again for this, but it won't be ubuntu this time.

this bug has been reported for months now.... [https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/1770482](https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/1770482)

---

### Post by QIII on 2018-09-09
OK.  Best wishes with whatever distro you choose.

---

### Post by allaf on 2018-09-09
thanks to you guys for the help anyway :)

---

### Post by allaf on 2018-09-09
Same bug reported in 2012  ! [https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/989396](https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/989396)

---

### Post by allaf on 2018-09-27
I didn't use the computer with the broken kubuntu for weeks, it was in hibernate mode, left aside.
But I launched it again and **[COLOR="#008000"]_actually solved the problem by chance_[/COLOR]**, I launched Muon package manager (I never usually never do) and it proposed me to graphically configure the broken package, and install it again !

So basically if you get this error I don't know how to correct it via the terminal, but you just have to launch Muon and it will do the trick apparently.

---

