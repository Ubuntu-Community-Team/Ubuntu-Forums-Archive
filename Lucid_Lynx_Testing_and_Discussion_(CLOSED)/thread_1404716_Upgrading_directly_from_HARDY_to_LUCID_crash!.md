---
title: "Upgrading directly from HARDY to LUCID: crash!"
date: 2010-02-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by putxi on 2010-02-11
Hello,

I've been running Hardy on my Desktop for long, and I decided to upgrade the OS version using upgrade manager gui. It offered me to upgrade to LUCID 10.04 LTS, directly.

I did so, and during the installation some incidences appeared on one or two packets that could not be well installed (my fault not to take notes of that !!!), and also some config files that offered me whether to mantain old or overwrite with new - but i had no idea of what was the optimal (no option with backup of old file was available).

So, process finished and all seemed to work the same.
But after restarting the system, I've not been able to launch it again.

After lots of messages, it get stucked with this message, aprox.:
"error init: ureadahead*-other main process (1085) terminated with status 4." 

I've tried to start from GRUB manager, using different versions on recovery mode, but it doesn't work: other messages appear, and finally stucked with these msg's (depending):

- "udev[624]: SYSFS{}= will be removed in a future udev version, please use ATTR{}=" (and something else ...)

or

- "/dev/sda6/ has been mounted 32 times. Check forced."

I go back to start without grub, and other msg:
- "/dev/sda1: clean 255036/" (was longer ...)

FORTUNATLY, I had a live cd of 7.10 (gutsy), and booting from CD i can acess HD data :-) 
It's still there!
But some files, i can not read (says i've not read permissions????)

I've just downloaded the 9.10 CD, and will continue trial&error with this ...

BUT, any information on ..

- What could has happened?
- How to proceed?
- Why the upgrade mng offered me to jump from hardy to lucid, but looking at ubuntu's web, it recomends only update to 9.10 from a 9.04 version ...? 
It should be even harder from 8 to 10, shouldn't it ???

Well, sorry for that "heavy brick".
Thanks in advance for any suggestion!

And, let's go on with more attempts to resurection ...

Regards,
jordi

---

### Post by darkod on 2010-02-11
Double check your sources and which options you have enabled. You don't want updates under development to be offered to you.
Lucid is still under development, it will be released in April, hence the version number 10.04 (2010 April). No wonder it broke down, but I have no idea how you ended up upgrading to Lucid.

---

### Post by putxi on 2010-02-11
Thanks darkod!

It's amazing, but the upgrade mng gui just offered me to "push this button to 10.04" ...
Shall i report that to someone, and how?

However, i've a 9.10 cd now, and booting from the cd i can "see" the data.

But there are some files i can not access: it says i've no permission!
How can i get this permission booting from cd ???
I'd like to backup some data.

Even better: can I install 9.10, or downgrade the faulty 10.04 to 9.10, without losing the data ???

I'd better go to bed now (2am), hope tomorrow can see further with your help ...

Good night!
jordi

---

### Post by Sef on 2010-02-11
Moved to Lucid subforum.

---

### Post by ranch hand on 2010-02-12
I have been testing that upgrade as I run Hardy too.  Solid OS.  Love it.

I do not recommend this upgrade at any time with a system that you intend to keep using for another several years.  Hardy is an ext3 OS.  10.04 is made for ext4.

If I were you I would shrink the partition you have "upgraded" and put 9.10 on a ext4 partition (or better yet 2 partitons.  Grab your data off the old Hardy and put it there.

I would then run in a chroot from 9.10;
```

dpkg --configure -a

```
probably will not help.

Boot, if possible, to recovery and run the dpkg option there.  That may well help some.

See this thread;

[http://ubuntuforums.org/showthread.php?t=1400787](http://ubuntuforums.org/showthread.php?t=1400787)

That may help some.

Testing for this upgrade only started the 4th of this month.  I keep installing 8.04.4 (I hope your Hardy was updated just before you tried this) and trying it out about once a week.

If you can get the bugger to take upgrades in chroot you will probably come out all right in the end.

If you can get rid of java and Firefox you will have a better chance but it is slim at this time.

Another thing that you should learn is that Update Mangler is not all that great on a stable OS (or you wouldn't be here now) and should not be used on an unstable OS.  Learn to use apt or aptitude and synaptic and stay away, in the future, from that awful app.

Good luck.  I will, and I am sure a lot of others, will follow this thread with great interest.

---

### Post by nanog on 2010-02-12
i suspect that you must have changed a flag in  /etc/update-manager/release-upgrades at some point. you should not have been offered the option to upgrade to 10.04. 

If you are feeling daring you can just fix your upgrade by chrooting in with a live cd:

[http://ubuntuforums.org/showpost.php?p=8628383&postcount=2](http://ubuntuforums.org/showpost.php?p=8628383&postcount=2)

If the update gets stuck:


Repair broken upgrade

dpkg --configure -a

Repair broken package

sudo dpkg-reconfigure <package name>

Fix install

sudo apt-get -f install <package name>

---

### Post by cariboo on 2010-02-12
Just a small correction the -f in apt-get stands for fix broken:

```
sudo apt-get -f install
```

will find missing dependencies and other errors.

---

### Post by phillw on 2010-02-12
> **ranch hand said:**
> 
If you can get rid of ....  and Firefox you will have a better chance......

Good luck.  I will, and I am sure a lot of others, will follow this thread with great interest.

Someone's ears must have been burning ... Hot off the release notes ..

> add missing Replace: firefox-3.0 for the firefox-branding package
    (LP: #518747). This fixes a upgrade issues from hardy to lucid.

It and several other issues are addressed in > firefox (3.6+nobinonly-0ubuntu2) lucid; urgency=low

Should be in the repos either now, or very soon !!

The full details are available here --> [https://launchpad.net/ubuntu/lucid/+source/firefox/3.6+nobinonly-0ubuntu2](https://launchpad.net/ubuntu/lucid/+source/firefox/3.6+nobinonly-0ubuntu2)

Regards,

Phill.

---

### Post by ranch hand on 2010-02-12
That will go a long says to making it work.  There are a couple of other things but that is a biggy.

It is about time for me to try it again.  Maybe tomorrow or Monday.  Will just have to see.

---

### Post by putxi on 2010-02-12
Hi all!

Thanks very much for your interest and help.
At the moment, i'm doing backup of all data (using live cd ubuntu 9.10): finally managed to access to some files (randomly) i was not allowed saying i had no permission. With "sudo nautilus" it's been ok :-)

THEN, i'll try your suggestions with apt and dkpg to recover the system through chroot ... which i have never done before (chrooting) ... and i'm trying to figure out with your info, nanog.
Btw, nanog: i've a doubt and will summite it to the thread you linked.

AND, i'll report the results to give you feedback. ;)

HOWEVER, wether it works or not, i'll format hd from scratch and install 9.10 from "zero".

Oh, nanog, i've not modified any flag of the update manager, for sure, i almost just use ubuntu as a "normal user" ...
but really wishing to get time to jump into roots of this system (i've worked for years on embedded systems, firmware, electronics, rtos, hdl, ... and so on ..., and the temptation is soooooooo huge !!! :P)

It's a pleasure to find people like you, ready to help.

Salut, ("health" in catalan, my mother-tongue)
jordi

---

### Post by putxi on 2010-02-13
Hi,

After doing a reliable backup, i've started trying the recovery through chroot.

I don't no what's going on with FLASHPLUGIN-NONFREE, but it seems it all spins around it.

Here's what i've done and results: (some translated by me)


**>> sudo apt-get update**
(...)
95% FATAL -> could not set non-blocking flag Bad file descriptor.
(...)
Subprocess http returen error code (100)

**>> dpkg --configure -a**
error processing flashplugin-nonfree (--configure)
The packet is in deep inconsistency state - reinstall must be done before trying config
Errors found processing: flashplugin-nonfree

**>> sudo apt-get -f install flashplugin-nonfree**
sudo: unable to resolve host ubuntu
(...)
Following packets have dependencies to match:
flashplugin-nonfree: depends on: flashplugin-installer, but it's not installed.
(...)

**>> sudo apt-get -f install**
sudo: unable to resolve host ubuntu
(...)
sh: cannot create /dev/null: Permission denied.
sh: cannot create /dev/null: Permission denied.
dpkg-preconfigure: can not open stdin again.
(...)
E: Sub-process /usr/bin/dpkg returned an error code (1)

**>> sudo apt-get update**
sudo: unable to resolve host ubuntu
(...)
95% FATAL -> could not set non-blocking flag Bad file descriptor.
(...)
Subprocess http returen error code (100)

**>> dpkg --configure -a**
(and again the bash appears: no error message)
>>


THEN, i try to restart the system to see if it's had any effect ...

*** Booting in "normal mode": KO
It ends with ...
/dev/sda1 has been mounted 39 time without being checked, check forced.

*** Booting via GRUB, 2.6.32-12-generic (recovery): KO
same message !!!


SOOOOOOO ...,

I'm gonna clean everything and start from zero with 9.10 ...

What do you thing?
Anybody interested in any more attempt to get feedback ???

I'll wait for a while  (half day) before formating ;)

AGAIN, thanks for everything!

Regards,
jordi

---

### Post by texaswriter on 2010-02-13
> **putxi said:**
> Hello,

I've been running Hardy on my Desktop for long, and I decided to upgrade the OS version using upgrade manager gui. It offered me to upgrade to LUCID 10.04 LTS, directly.

I did so, and during the installation some incidences appeared on one or two packets that could not be well installed (my fault not to take notes of that !!!), and also some config files that offered me whether to mantain old or overwrite with new - but i had no idea of what was the optimal (no option with backup of old file was available).

So, process finished and all seemed to work the same.
But after restarting the system, I've not been able to launch it again.

After lots of messages, it get stucked with this message, aprox.:
"error init: ureadahead*-other main process (1085) terminated with status 4." 

I've tried to start from GRUB manager, using different versions on recovery mode, but it doesn't work: other messages appear, and finally stucked with these msg's (depending):

- "udev[624]: SYSFS{}= will be removed in a future udev version, please use ATTR{}=" (and something else ...)

or

- "/dev/sda6/ has been mounted 32 times. Check forced."

I go back to start without grub, and other msg:
- "/dev/sda1: clean 255036/" (was longer ...)

FORTUNATLY, I had a live cd of 7.10 (gutsy), and booting from CD i can acess HD data :-) 
It's still there!
But some files, i can not read (says i've not read permissions????)

I've just downloaded the 9.10 CD, and will continue trial&error with this ...

BUT, any information on ..

- What could has happened?
- How to proceed?
- Why the upgrade mng offered me to jump from hardy to lucid, but looking at ubuntu's web, it recomends only update to 9.10 from a 9.04 version ...? 
It should be even harder from 8 to 10, shouldn't it ???

Well, sorry for that "heavy brick".
Thanks in advance for any suggestion!

And, let's go on with more attempts to resurection ...

Regards,
jordi

Usually with Debian-based upgrades, you have to do step updates. I imagine, to be safe, upgrading each step up would be the best bet. There might be a quicker solution though. I doubt you can go from an LTS to an alpha or beta. That seem extreme.

---

### Post by ranch hand on 2010-02-13
> **texaswriter said:**
> Usually with Debian-based upgrades, you have to do step updates. I imagine, to be safe, upgrading each step up would be the best bet. There might be a quicker solution though. I doubt you can go from an LTS to an alpha or beta. That seem extreme.
With Ubuntu you are supposed to be able to go from LTS to  LTS.  It will work when we have a new LTS.  We do not have one right now.  We have an alpha 2 of the new LTS and the testing for the upgrade just started on 2-4-10.

The OPs Update Mangler gave him the option of upgrading and he did.

I have been testing this and his trouble wit the flash stuff is a problem.  If he gets past that then Firefox is the next thing he will have trouble with.

Both 8.04 and 10.04 are being worked on to get this to work.  It will get there.  I am over writing both my test 8.04>10.04 installations and waiting for the 25th and A3 before trying it again.  One will have Firefox and the flash stuff.  The other will have them removed before the upgrade.

One on the big problems with the 9.04>9.10 upgrades was leaving grub0.97 on with grub1.97beta4.  Caused all kinds of stupid problems no matter which you decided to go with.  The 8.04>10.04 upgrade does not do this.  It very well installs grub1.98 on the upgrade.

I, personally, am amazed at the partial success of these early upgrade tests.  I admit to a certain doubt as to the possibility of doing it.  Now I can see that it is going to work.

While I am testing this upgrade I will not be doing it to my install of 8.04 (my secure business OS).  I will be doing a clean install of 10.04 and transferring data.  I want ext4 not ext3.  I also want to make sure I get rid of all the "trash and useless clutter" that has accumulated on my install.

Now, after doing that, I may well, for the fun of it, run the upgrade on my original installation, but only after waiting a couple months to make sure the new one is as stable and great as I believe it will be.

---

### Post by nanog on 2010-02-13
jordi,

it looks like your hard drive is being checked via fsck (this may indicate a hard drive problem and the fsck often causes problems with boot in development). you should run a full disk check off the live cd. be sure to not chroot and mount your drive!

Commands:

```
sudo fdisk -l
``` 

find your drive in the list 

```
sudo fsck -C -R -A -a  /yourhardrivedesignation
```

you can solve your flash problem by removing it while chrooted. it may be that a broken flash package is causing your problem. did you by chance install flash from a non-ubuntu source?

```
sudo dpkg -r -P flashplugin-nonfree
```
 or 
```
sudo apt-get remove --purge  flashplugin-nonfree
```

if this does not work the other option would be to manually edit /var/lib/dpkg and manually remove the installed files. this is actually alot easier than it seems. i'll help if its an issue.

---

### Post by nanog on 2010-02-13
dupe.

---

### Post by nanog on 2010-02-13
> I doubt you can go from an LTS to an alpha or beta.

although its not supported officially ubuntu is now designed to do exactly this from 8.04 on. in my experience non-sequential upgrades work fairly well. i completely bypassed jaunty on most of the intel systems i administer or run. 

if you take the time to learn dpkg you can do *anything* to your ubuntu install. heck, one the old fashioned ways to fix an accidental root deletion (remove -are -f \.)  was to run a shell script that uses dpkg to restore your entire root from a list of installed packages!

---

### Post by texaswriter on 2010-02-14
> **nanog said:**
> although its not supported officially ubuntu is now designed to do exactly this from 8.04 on. in my experience non-sequential upgrades work fairly well. i completely bypassed jaunty on most of the intel systems i administer or run. 

if you take the time to learn dpkg you can do *anything* to your ubuntu install. heck, one the old fashioned ways to fix an accidental root deletion (remove -are -f \.)  was to run a shell script that uses dpkg to restore your entire root from a list of installed packages!

Heh, amazing. 

I would assume the user must have added the Lucid repositories to there package manager. Would that cause it to want to upgrade?

---

### Post by putxi on 2010-02-15
Thanks, **nanog**!

> **nanog said:**
> 

you should run a full disk [COLOR="Red"]check off the live cd[/COLOR]. be sure to not chroot and mount your drive!

Commands:

```
sudo fdisk -l
``` 

find your drive in the list 

```
sudo fsck -C -R -A -a  /yourhardrivedesignation
```


You mean without using the live cd menu option, but booting from live cd and doing it from its console?
Otherwise i don't know how to get a console?

Hope all this error message are due to new installation, and not 'cos of hd damage ...


> **nanog said:**
> 
did you by chance install flash from a non-ubuntu source?


Probably ... Sometimes i've installed packets suggested by firefox when trying to access some web ... 
BETTER if i first look at ubuntu's repository, isn't it? I will, from now on.

Gonna try your suggestions ... it seems DPKG is a very interesting low.level tool ..., complex, but full of possibilities ... :p
I'll keep an eye on this ... for future frights! 


But i don't want to restore the old system: i prefer to start from scratch ... with 9.10 and make some cleaning from the hd (too long adding rubish ...).

Regards,
jordi

---

### Post by putxi on 2010-02-15
> **nanog said:**
> 
```
sudo fsck -C -R -A -a  /yourhardrivedesignation
```


I can't manage to start the check ...
The command responds:

```
fsck from until-linux-ng 2.16
```

????

Btw, my hd designator is the traditional /dev/sda ...

Regards,
jordi

---

