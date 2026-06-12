---
title: "ubuntu failed to boot after an incompleted upgrade"
date: 2017-10-06
forum: Installation &amp; Upgrades
---

### Post by shakib95 on 2017-10-06
[COLOR=#111111][FONT=Ubuntu]Hi <3
I tried to upgrade Ubuntu from 15.10 to 16.04 version using software updater!! for some reason my laptop turned off ( battery ran out of power ) and the upgrade process would not be completed ... after that i turned it on and the screen became black with an error :

[/FONT][/COLOR]```
 [COLOR=#111111][FONT=Ubuntu]fsck from util-linux 2.26.2
 /dev/sda5: recovering journal
 /dev/sda5: clean , 374456/2842624 files , 4163852/11340031 blocks[/FONT][/COLOR]
```[COLOR=#111111][FONT=Ubuntu]

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu][FONT=inherit]sorry my English is not so good :( please help me to fix this <3 Thanks[/FONT]
[/FONT][/COLOR]

---

### Post by Autodave on 2017-10-06
Hopefully some one else will have some ideas for you. However, I do not.  What I would like to suggest though:

  	 	 	 	   Every 2 years, a long term service release is made. These LTSs have a service life of 5 years: security and software updates are available for 5 years after the release.  The last LTS was 16.04. 16 stands for the year of the release, 04 stands for the month (April). The next LTS will be 18.04. Releases in the interim will be 6 month releases and only supported until the next release.

I stick with only the LTSs and even then I usually wait a month after their release before installing them. Further, I do not upgrade to them but completely install the new release after copying all files that I need to save to an external HD.

If that were my machine, I would download and install one of the 16.04 releases.

---

### Post by shakib95 on 2017-10-07
Thank you bro for your suggestion <3

finally if have find the answer thanks to askubuntu :x

here the answer link for people who may search for the answer of similar questions : [https://askubuntu.com/questions/864265/software-updater-says-an-unhandlable-error-occured](https://askubuntu.com/questions/864265/software-updater-says-an-unhandlable-error-occured)

---

### Post by ian-weisser on 2017-10-07
Power loss during a release-upgrade is the *worst possible time* and will often result in both filesystem corruption and a broken package management system. That's why your system warned you specifically to NOT release-upgrade while on battery. 

Those warnings are there for a reason. Listen to them.

Your 'error' is simply fsck telling you that it *already fixed* your filesystem corruption.

Your next step is to fix your broken package system. Boot into recovery mode and run 'apt install --fix-broken'.

If your problem is already solved, then please mark the thread [Solved]

---

### Post by shakib95 on 2017-10-07
> **ian-weisser said:**
> Power loss during a release-upgrade is the *worst possible time* and will often result in both filesystem corruption and a broken package management system. That's why your system warned you specifically to NOT release-upgrade while on battery. 

Those warnings are there for a reason. Listen to them.

Your 'error' is simply fsck telling you that it *already fixed* your filesystem corruption.

Your next step is to fix your broken package system. Boot into recovery mode and run 'apt install --fix-broken'.

If your problem is already solved, then please mark the thread [Solved]

yes that was my fault not listening to those warnings :(

hopefully my ubuntu run well right now but it is very very slow !! the animations are just like slowmotion :( and about 19 packages are broken !!
when i run software updater it says you should first solve broken packages then you can upgrade :(
how can i fix the broken packages? please help <3

---

### Post by ian-weisser on 2017-10-07
Re-read Post #4 for how to fix the broken packages.

---

### Post by shakib95 on 2017-10-07
> **ian-weisser said:**
> Re-read Post #4 for how to fix the broken packages.

sorry for that i didnt read your post carefully.
I tried " apt install --fix-broken " that you said but it gives me some error :

```
Reading package lists ... Error!
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Couldn't create temporary file to work with /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial_inrelease -  mkstemp (30: Read-only file system)
E: the package lists or status file could not be parsed or opened.
```

how can i fix this? Thanks <3

---

### Post by ian-weisser on 2017-10-07
Read that error message carefully.
Why is your file system read-only?

---

### Post by shakib95 on 2017-10-08
> **ian-weisser said:**
> Read that error message carefully.
Why is your file system read-only?

I remount file system as read write then try this " apt install --fix-broken "

after that it says "after this operation , 946 kb disk space will be freed. Do you want to continue? " i said yes

then it shows an error :
```
W: No sandbox user '_apt' on the system , can not frop privileges
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

