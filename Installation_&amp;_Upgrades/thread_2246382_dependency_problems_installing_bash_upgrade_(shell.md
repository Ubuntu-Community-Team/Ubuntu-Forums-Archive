---
title: "dependency problems installing bash upgrade (shellshock patch)"
date: 2014-09-30
forum: Installation &amp; Upgrades
---

### Post by Mad Cow on 2014-09-30
Hi,

I can't seem to find help through search, but apologies if I've missed something obvious. I don't know much about linux, but need to patch an ubuntu machine.  I can't get passed dependency problems. I'm running: 3.2.0-36-generic #57-Ubuntu SMP Tue Jan 8 21:44:52 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Here's what I've tried:
apt-get clean
apt-get autoclean
apt-get install --only-upgrade bash (getting Unmet dependencies)
apt-get -f install (Errors were encountered while processing: libssl-dev)
apt-get install --only-upgrade bash (getting Unmet dependencies)

I can't figure out what to do next? 

I think I have enough space left:
Filesystem                   1K-blocks     Used Available Use% Mounted on
/dev/mapper/myMachineName-root  29681532 15117856  13055940  54% /
udev                           1016764        4   1016760   1% /dev
tmpfs                           410340      252    410088   1% /run
none                              5120        0      5120   0% /run/lock
none                           1025840        0   1025840   0% /run/shm
/dev/sda1                       233191   147896     72854  67% /boot

Many thanks in advance.


---------------
```
root@myMachineName:/boot# apt-get install --only-upgrade bash
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.6) but 1.0.1-4ubuntu5.17 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@myMachineName:/boot#
root@myMachineName:/boot#
root@myMachineName:/boot#
root@myMachineName:/boot# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libssl-dev
The following packages will be upgraded:
  libssl-dev
1 upgraded, 0 newly installed, 0 to remove and 226 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,574 kB of archives.
After this operation, 108 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of libssl-dev:
 libssl-dev depends on libssl1.0.0 (= 1.0.1-4ubuntu5.6); however:
  Version of libssl1.0.0 on system is 1.0.1-4ubuntu5.17.
dpkg: error processing libssl-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 libssl-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@myMachineName:/boot# apt-get clean
root@myMachineName:/boot# sudo apt-get autoclean
Reading package lists... Done
Building dependency tree
Reading state information... Done
root@myMachineName:/boot#
root@myMachineName:/boot# apt-get install --only-upgrade bash
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.6) but 1.0.1-4ubuntu5.17 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@myMachineName:/boot#
root@myMachineName:/boot# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libssl-dev
The following packages will be upgraded:
  libssl-dev
1 upgraded, 0 newly installed, 0 to remove and 226 not upgraded.
1 not fully installed or removed.
Need to get 1,574 kB of archives.
After this operation, 108 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main libssl-dev amd64 1.0.1-4ubuntu5.17 [1,574 kB]
Fetched 1,574 kB in 0s (2,937 kB/s)
dpkg: dependency problems prevent configuration of libssl-dev:
 libssl-dev depends on libssl1.0.0 (= 1.0.1-4ubuntu5.6); however:
  Version of libssl1.0.0 on system is 1.0.1-4ubuntu5.17.
dpkg: error processing libssl-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 libssl-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@myMachineName:/boot#
```

---

### Post by Mad Cow on 2014-09-30
I had a crack at: apt-get dist-upgrade but no joy

root@[COLOR=#000000]myMachineName[/COLOR]:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.6) but 1.0.1-4ubuntu5.17 is installed
E: Unmet dependencies. Try using -f.
root@[COLOR=#000000]myMachineName[/COLOR]:~#

---

### Post by ubfan1 on 2014-09-30
I don't see that you have ever run sudo apt-get update
anywhere.  I am also not confident that just the bash package will be sufficient, so try letting the machine decide what to install -- Use the GUI software updater if you want to more easily select packages (but I find many I unselect still get downloaded).

---

### Post by ian-weisser on 2014-09-30
Here's the problem:

> **Mad Cow said:**
> libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.6) but 1.0.1-4ubuntu5.17 is to be installed

At some point in the past, somebody with admin privileges told the system to install an obsolete version of the libssl-dev package.
Sensibly, libssl-dev depends upon a specific version of libssl.

Well, the world has moved on, and now the version of libssl is not the same anymore. That's causing libssl-dev to fail to install.
Whoever tried to install it in the past didn't notice that the original install had failed.
And apt is slightly clever: It remembers what it failed to install, and next time it runs it tries again.
It may have been trying for a long time. If so, that's bad - perhaps no security updates for a long time.

> **Mad Cow said:**
> 1 upgraded, 0 newly installed, 0 to remove and **226 not upgraded**.
Yeah, seems to have been a while. Not too long, though.


apt-get clean/autoclean won't help with this issue. It's not an old package taking up cache space.
apt-get install (-f, etc.) won't help until you uninstall the conflicting package.


What to try:

1) Ubfan1 is right: Your dpkg database seems out of date. Refresh the database:
```
apt-get update
```

2) Try uninstalling libssl-dev
```
apt-get remove libssl-dev
```

If that doesn't work, try
```
apt-mark auto libssl-dev
apt-get remove libssl-dev
```

If it still doesn't uninstall, then let us know. Do not proceed to 3) or 4) if uninstall fails. We have bigger, meaner tools that can be used if needed.

3) Do a normal upgrade. The bash patch is included if you have the precise-security repo enabled. 220 packages may take a few minutes.
```
apt-get upgrade
```

4) Finally, there's probably a few kernel updates among the blocked updates.
```
apt-get dist-upgrade
```

---

### Post by Mad Cow on 2014-10-01
Hi thank you for the details, this is all good stuff. I appear to be gaining information now.

I did run: *apt-get update *which threw out a number of lines to the console and seemed successful.

I then followed steps 1, 2 and 2a

Would I be right in saying that python-dev may be part of the problem (Full details below)?
*python2.7-dev : Depends: libssl-dev but it is not going to be installed*


I know that python is being used by the main tool on the system, but I don't know why python-dev would be in use?  
*root@myMachine:~# python*
*Python 2.7.3 (default, Apr 20 2012, 22:39:59)*
*[GCC 4.6.3] on linux2*



I do have a virtual snapshot of this machine, so I can afford to take some risks, in the belief that I can roll-back.

Any guidance on a next step? thanks

----------------------------------
```
root@myMachineName:~# apt-get remove libssl-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 python2.7-dev : Depends: libssl-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@myMachineName:~#
root@myMachineName:~# apt-get install libssl-dev=1.0.1-4ubuntu5.17
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  libssl-dev
1 upgraded, 0 newly installed, 0 to remove and 226 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,574 kB of archives.
After this operation, 108 kB of additional disk space will be used.
dpkg: dependency problems prevent configuration of libssl-dev:
 libssl-dev depends on libssl1.0.0 (= 1.0.1-4ubuntu5.6); however:
  Version of libssl1.0.0 on system is 1.0.1-4ubuntu5.17.
dpkg: error processing libssl-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 libssl-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@myMachineName:~# apt-mark auto libssl-dev
libssl-dev was already set to automatically installed.
root@myMachineName:~# apt-get remove libssl-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 python2.7-dev : Depends: libssl-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by ian-weisser on 2014-10-01
Okay, so python2.7-dev is why libssl-dev was installed.
Work your way up that chain of dependencies. Uninstall python2.7-dev. Very few packages depend upon it.

Er, I wouldn't try to reinstall libssl-dev until your package manager is working properly. That action is putting obstacles in your way. I also wouldn't try to install it manually nor to specify a version - whatever requires it will pull it in automatically. Specifying a version in the past is one possible cause of the problem.
'install -f' hasn't helped much because you seem to have conflicting packages, neither of which is apparently marked 'auto'. -f can resolve many automatically-created problems, but often cannot resolve a human-created situation. That's sometimes a good time try 'aptitude'.

But none of that yet,
I suspect we can clear the conflict by uninstalling python2.7-dev, and perhaps whatever requires it (if anything).

---

### Post by Mad Cow on 2014-10-01
Hi thanks again for the continued help, it's invaluable.

I'm unable to uninstall it and seem to be in a circular dependency, although I think I'm possibly misunderstanding the situation? (I googled the apt-get command so may have the wrong one) I also tried with and without the "--purge" option.

```
root@myMachineName:~# apt-get remove python2.7-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.6) but 1.0.1-4ubuntu5.17 is to be installed
 python-dev : Depends: python2.7-dev (>= 2.7.3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@myMachineName:~# apt-get -f remove python-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.6) but 1.0.1-4ubuntu5.17 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@myMachineName:~#
root@myMachineName:~# apt-get -f remove libssl-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 python2.7-dev : Depends: libssl-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@myMachineName:~#
```

---

### Post by ian-weisser on 2014-10-01
'purge' won't help. It's not a way to force removal; it merely removes config files in /etc (which 'remove' doesn't do). 
'-f' won't help. It's not a way to force removal; it merely tries to deconflict problems with automatically-installed packages.

Try:
```
apt-get remove libssl-dev python2.7-dev
```

If that works, then your problem should be solved. Try a normal test upgrade to see if those 200+ updates install.


If that still doesn't work, then we'll try dpkg next. Let's see the result of the following four commands. None need to be run as root:
```
apt cache policy libssl-dev python2.7-dev
dpkg --audit
dpkg --get-selections | grep libssl-dev
dpkg --get-selections | grep python2.7-dev
```

Do you have any files in /etc/apt/preferences.d/ ?
If so, please show us the complete contents of each file in that directory.

---

### Post by Mad Cow on 2014-10-02
Ah haa.

That' has cracked it thank you. Chaining the remove commands got me out of the circle.  I ended up using:
*apt-get remove libssl-dev python2.7-dev python-dev*

Which was successful.  I was then able to run the update for bash:
*apt-get install --only-upgrade bash*

I'm not quite sure I'm safe now, but you have allowed me to make some progress on my own. I'll need to go make some coffee while I wait for the "apt-get upgrade"!

Many thanks ian-weisser for the excellent help.

---

### Post by Impavidus on 2014-10-02
> **ian-weisser said:**
> At some point in the past, somebody with admin privileges told the system to install an obsolete version of the libssl-dev package.
Sensibly, libssl-dev depends upon a specific version of libssl.

Well, the world has moved on, and now the version of libssl is not the same anymore. That's causing libssl-dev to fail to install.
Whoever tried to install it in the past didn't notice that the original install had failed.
And apt is slightly clever: It remembers what it failed to install, and next time it runs it tries again.
It may have been trying for a long time. If so, that's bad - perhaps no security updates for a long time.
What I think is that at some point libssl was upgraded (because of the heartbleed bug?) without upgrading libssl-dev. This would have broken the package manager, something only noticed now when trying to upgrade bash (because of the shellshock bug). Only upgrading packages directly affected by high-publicity bugs is not going to keep your system safe. As you see, it can even break the package manager and block further upgrades. With 226 packages not up to date, you must have missed some more security patches.

Best to install all updates. If your internet access is slow (if you have the time to make coffee whilst upgrading bash only, it must be), you could try creating a download script using synaptic, using a different computer to download the upgraded packages and transferring them to your computer by usb drive.

---

### Post by ian-weisser on 2014-10-02
I think Impavidus' advice is excellent.
I agree that upgrading to fix only high-visibility vulns is not a safe way to work.

---

### Post by Mad Cow on 2014-10-03
Hi guys. Very good advice. I (believe i) have updated all of the packages now, it did take a while! 

I haven't touched the box in years! It was setup for me as a favour as we're pretty much a windows only department, then the primary app was installed by a contractor.

Now I know I can upgrade things without breaking the box, I have more confidence to do it again.

I'm going to practice my new knowledge on my neglected raspberry pi at home!

Many thanks for the sound advice!

Cheers

---

