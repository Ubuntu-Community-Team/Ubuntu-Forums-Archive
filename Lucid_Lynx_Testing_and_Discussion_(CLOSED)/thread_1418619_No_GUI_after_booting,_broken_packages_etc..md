---
title: "No GUI after booting, broken packages etc."
date: 2010-02-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Zilioum on 2010-02-28
I think I cocked up pretty bad this time :D I installed Lucid Lynx via ```
update-manager -d
```
The installation went fine until I got an error message about some python package. I ignored that and continued with the installation. I then got the infamous "partial upgrade" message, but that didnt work.
I then rebooted my pc and thats where the fun started:
[LIST]
[*]My first Grub choice is : Ubuntu, with Linux 2.6.31-20-generic
[*]If I choose that one I get the white ubuntu logo on black background for some seconds
[*]If I choose that one I get to > mountall: Could not connect to Plymouth, fsck from util-linux-ng 2.17
[*]I can get to the console though via recovery mode
[*]I tried ```
apt-get/aptitude update, upgrade
``` etc. and ```
dpgk --configure -a
``` Nothing works. I just get a huge list of uninstalled packages which I cant install because the installation aborts at some point because of unmet dependencies.
[*]If I run ```
gdb
``` or ```
starx
``` my 9.10 Ubuntu Desktop shows up, but I can only move my mouse, but not click anything or use my keyboard.
[/LIST]

I suppose that there is something fundamentally wrong. Any ideas? It looks like my old Kernel is still there. Any way to reinstall Lucid from scratch?

Cheers

---

### Post by VMC on 2010-02-28
Of course you can re-install it, but who did you get to where you are now. Was it from an upgrade from 9.10?

the "mountall: Could not connect to Plymouth" means that plymouth is uninstalled.

---

### Post by ranch hand on 2010-02-28
Why on earth are you booting to a 9.10 kernel?

A better choice in recovery is the dpkg option after an upgrade.   I always go there first and run that.  Saves trouble.

---

### Post by nanog on 2010-02-28
You need to do this:

[PHP]aptitude dist-upgrade[/PHP]

upgrade alone does diddly during a "dist" upgrade.

if that does not work see me siggie.

---

### Post by nanog on 2010-02-28
> because of unmet dependencies.

Which ones?

This command or a script that loops through them can solve many problems:

[PHP]sudo apt-get -f install <pkg>[/PHP]

You should also check your sources. Make sure they were all changed to lucid or commented out.

---

### Post by Zilioum on 2010-03-01
Thanks for all your answers. I upgraded from 9.10. When I try ```
dist-upgrade, upgrade, dpgk etc. 
``` I get a huge list of packages from the Linx sources. It also says > Leave following dependencies unresolved: xserver-xorg-video-geode recommends xserver-xorg-video-cyrix and xserver-xorg-video-geode recommends xserver-xorg-video-nsc  Score is 8[/CODE]  If I then start the upgrade the first error is ```
dpkg: error processing *some perl.deb*
```then ```
dpgk-dep:subprocess paste killed by signal (Broken Pipe) 
``` I then get some more errors and it just stops as it does when it has finishing doing an upgrade. I feel like there should be a way to just force upgrade it. I dont think that its really about one of those packages specifically, but rather my whole installation is wrong [QUOTE]Why on earth are you booting to a 9.10 kernel?

---

### Post by ranch hand on 2010-03-01
I hope when you say you ran "dpkg" you mean:
```

dpkg --configure -a

```
and that you ran it several times.  Just hit the up button for the last command and do it again.  Keep that up until it gets no further.

Then you could try;
```

apt-get update

```
and;
```

apt-get dist-upgrade

```
again.

Repeat the "dpkg" song and dance.

If you are sure that the 2.6.32 kernel is installed (it should be the first on that gets listed in a "update-initramfs" sequence) try to boot into recovery and run the "dpkg fix broken packages" option.

If it works and then trys to run updates and fails to connect, when you get out of that try the "root shell with networking" option.  It is good at forcing a connection.

If that works run;
```

apt-get update

```
and;
```

apt-get dist-upgrade

```
Then try the "dpkg" routine again.

Then try the "return to normal boot" option.  After signing in on the text login type "startx" at the prompt and see what happens.

---

### Post by Zilioum on 2010-03-01
My kernel is -.31(see first post). I'm not at my pc right now, but if I remember right dpkg didn't bring me further. I did use the netroot but maybe it was the wrong kernel. How can I get the right one? Startx always gets me to my 9.10th desktop (first post)

---

### Post by ranch hand on 2010-03-01
If you have the correct repos in your /etc/apt/sources.list and run;
```

sudo apt-get update

```
and
```

sudo apt-get dist-upgrade

```
You will get the right kernel as it will be the only one available.

---

### Post by nanog on 2010-03-01
> dpkg: error processing some perl.deb

Hard to trouble shoot without the exact errors. If perl is broken dpkg may not work. You can chroot in and reinstall a working dpkg/apt environment using: 

```
dpkg -i libc6* libdb2* perl*
dpkg -i apt* dpkg* debconf*

```

you may have a broken package and may want to try 

```
dpkg-reconfigure package
``` 

If that does not work and the package is not ESSENTIAL you may want to try cautiously nuking it:

```
dpkg -r --force package
```
```
dpkg --configure -a
```
```
apt-get update && apt-get dist-upgrade
```

Next step would be to use chroot to repair  /var/lib/dpkg/status and/or use dpkg --set-selections. but unless you are willing to make this a learning experience its probably best to reinstall.

---

### Post by Zilioum on 2010-03-01
When I start my Pc now I get to the terminal login (tty1). The exact error when running```
apt-get dist-upgrade
``` and any version of ```
dpkg
``` from there is: ```
Errors where encountered while processing: /var/cache/apt/archives/libanyevent-perl_5.240-1_all.deb
```
I want to fix, make it a > learning experience Go big or stay home :D 
Should I still try to fix it via chroot or should I first try to specifically fix that Perl package (the thing is, there is probably a lot more broken)?

---

### Post by Zilioum on 2010-03-01
This is where I am right now: I chrooted into my system from a live cd and tried to following things.

```
apdtitude dist-upgrade
```
gives me this
```

224 packages upgraded, 122 newly installed, 44 to remove and 55 not upgraded.
Need to get 0B/419MB of archives. After unpacking 317MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Extracting templates from packages: 100%
Preconfiguring packages ...
pcilib: Cannot open /proc/bus/pci
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 293100 files and directories currently installed.)
Unpacking libanyevent-perl (from .../libanyevent-perl_5.240-1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libanyevent-perl_5.240-1_all.deb (--unpack):
 trying to overwrite '/usr/share/man/man3/AnyEvent.3pm.gz', which is also in package anyevent-perl 0:1.02-0.2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libanyevent-perl_5.240-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of libevent-execflow-perl:
 libevent-execflow-perl depends on libanyevent-perl; however:
  Package libanyevent-perl is not installed.
dpkg: error processing libevent-execflow-perl (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libevent-execflow-perl
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

root@ubuntu:/# 

```

```
dpgk --configure -a
```
gives me

```

dpkg: dependency problems prevent configuration of libevent-execflow-perl:
 libevent-execflow-perl depends on libanyevent-perl; however:
  Package libanyevent-perl is not installed.
dpkg: error processing libevent-execflow-perl (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libevent-execflow-perl
root@ubuntu:/# 

```

and ```
dpkg -i libc6* libdb2* perl*
dpkg -i apt* dpkg* debconf*
```

didnt work either (also tried it without the *)
```
dpkg: error processing libc6* (--install):
 cannot access archive: No such file or directory
dpkg: error processing libdb2* (--install):
 cannot access archive: No such file or directory
dpkg: error processing perl* (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libc6*
 libdb2*
 perl*

```

I couldn't try out ```
dpkg-reconfigure package
``` and ```
dpkg -r --force package
``` since I didnt know which package to work with.

I think that fixing perl seems crucial in fixing my pc. Any concrete ideas about what I could do?

---

### Post by Zilioum on 2010-03-02
bump

---

### Post by Ibidem on 2010-03-02
Chroot: You missed 
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
etc.

Overall--The problem is with packages, not with booting.  So chroot won't help any, unless your install can't connect to the network.
Try
sudo apt-get install -f -s
to check what would happen if you let apt try to sort it all out (-f means fix, -s means simulate/do a dry run); if that looks like it might work, remove the -s.
If it doesn't work, you will need to reinstall.

---

### Post by nanog on 2010-03-02
It looks like you have one broken package. The very first thing I do in this situation is search launchpad or [debian bts]("http://groups.google.com/group/linux.debian.bugs.dist/topics?pli=1"):

[https://bugs.launchpad.net/ubuntu/+source/libanyevent-perl/+bug/470560](https://bugs.launchpad.net/ubuntu/+source/libanyevent-perl/+bug/470560)
```

sudo dpkg -r --force-remove-reinstreq libanyevent-perl
```

or

```
sudo apt-get remove --force libanyevent-perl

```

dpkg --configure -a
apt-get install 
apt-get upgrade 
apt-get dist-upgrade 

if any of those apt commands breaks try the f flag:

apt-get dist-upgrade -f

---

### Post by Zilioum on 2010-03-02
Its starting to get weird:
When I run ```
apt-get -f install
```
I still get ```
dpkg: error processing /var/cache/apt/archives/libanyevent-perl_5.240-1_all.deb (--unpack):
 trying to overwrite '/usr/share/man/man3/AnyEvent.3pm.gz', which is also in package anyevent-perl 0:1.02-0.2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libanyevent-perl_5.240-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Nanog found this to be a bug (thanks again for all the help to all of you, btw) which can be resolved by removing the libanyevent-perl package.
I tried this by using the commands provided by nanog or with ```
apt-get remove libanyevent-perl
``` but I got this ```
Package libanyevent-perl is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  libevent-execflow-perl: Depends: libanyevent-perl but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

So it seems that the problem occurs when trying to install this package. According to the bug report this package shouldnt be in the repositories anyway. Any ideas how to fix this? Couldnt I just eliminate the software source? Or somehow force it to ignore this error?

Cheers

(I found out that SSH still works, really grateful that now I can just copy/paste the error messages and dont have to copy them by hand anymore :D)

---

### Post by nanog on 2010-03-02
did you run "dpkg --configure -a"

whats the output?  this command should correct dependencies.

it looks like the culprit is libevent-execflow-perl.

By searching at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) you can find its dependencies:

libanyevent-perl
dep: libintl-perl 
dep: perl 

it looks like you can safely nuke libevent-execflow-perl.

unless you have other broken packages or dependencies you will hopefully be good to go.

---

### Post by nanog on 2010-03-02
I googled libevent-execflow-perl and noticed this bug:

[https://bugs.launchpad.net/ubuntu/+source/dvdrip/+bug/527462](https://bugs.launchpad.net/ubuntu/+source/dvdrip/+bug/527462)

I have a feeling dvdrip caused your problem. Uninstall it and comment on the bug.

---

### Post by Zilioum on 2010-03-03
It was dvdrip that caused the problem. I had to remove it, to be able to remove libevent-execflow-perl. I did a dist-upgrade and now my pc runs again :p Thanks a lot! (I will comment on the bug as soon as I get home again). 

Cheers

---

### Post by nanog on 2010-03-03
Make sure to note that this completely crapped out your lucid upgrade.

---

