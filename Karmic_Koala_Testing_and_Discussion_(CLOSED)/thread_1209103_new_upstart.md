---
title: "new upstart"
date: 2009-07-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2009-07-09
The new upstart is in...version .6 replacing .3---has anyone got it yet?  It looks like it wants to remove apparmor, apparmor-utils, ubuntu-minimal, upstart-compat-sysv & upstart-logd so I'm going to do some more looking before doing it......

---

### Post by Regenweald on 2009-07-09
safe-upgrade left it behind for me. Will try again in the morning...

---

### Post by BwackNinja on 2009-07-09
I got it, no ill effects. Apparmor module failed to load at boot before anyway. The new version specifically conflicts with/replace upstart-compat-sysv and ubuntu-minimal probably needs to be upgraded to compensate.

---

### Post by autocrosser on 2009-07-09
Have you rebooted with it? Anything looking new/faster/different?

---

### Post by cariboo on 2009-07-09
I upgraded this afternoon after a complete new installation. I've rebooted several times with out anything strange happening. On my previous install apparmor failed to start, so I don't think I missing anything.

---

### Post by autocrosser on 2009-07-09
Good enough for me--I'm in.....

---

### Post by caryb on 2009-07-09
It fixes the 10 sec delay with apparmor failing. 


Cary

---

### Post by wayne_cat on 2009-07-09
from /var/log/apt/term.log after upgrading:

```
removing apparmor ...
 * Unloading AppArmor profiles                                                   * Failure: AppArmor module is not loaded
                                                                         [fail]
invoke-rc.d: initscript apparmor, action "stop" failed.
```That means .... AppAmor was not running?

---

### Post by psyke83 on 2009-07-09
> **wayne_cat said:**
> from /var/log/apt/term.log after upgrading:

```
removing apparmor ...
 * Unloading AppArmor profiles                                                   * Failure: AppArmor module is not loaded
                                                                         [fail]
invoke-rc.d: initscript apparmor, action "stop" failed.
```That means .... AppAmor was not running?

Yep. I don't think that AppArmor has ever been working in Karmic (I always remember seeing the failed status, at least).

---

### Post by autocrosser on 2009-07-09
Yes--I was getting that message for the last couple of weeks during boot (in text mode)--so no great loss--I'll add it back in in a week or so--depends on it's next update.....

---

### Post by wayne_cat on 2009-07-10
> **autocrosser said:**
> Yes--I was getting that message for the last couple of weeks during boot (in text mode)--so no great loss--I'll add it back in in a week or so--depends on it's next update.....

Well ... nobody is shouting "OMG!!! ... THE SHIELDS ARE DOWN!!! ... WE ARE ALMOST DEAD!!!"  .... in a week or so is OK

---

### Post by Regenweald on 2009-07-10
> **wayne_cat said:**
> Well ... nobody is shouting "OMG!!! ... THE SHIELDS ARE DOWN!!! ... WE ARE ALMOST DEAD!!!"  .... 

:P Funny.

---

### Post by ktp on 2009-07-10
> **wayne_cat said:**
> Well ... nobody is shouting "OMG!!! ... THE SHIELDS ARE DOWN!!! ... WE ARE ALMOST DEAD!!!"  .... in a week or so is OK

:lolflag:

---

### Post by autocrosser on 2009-07-10
ALL HANDS TO THE PHASERS & PHOTON TORPEDOS!!!!! The Romulans are trying to board us.........:lolflag:

---

### Post by dino99 on 2009-07-10
another new update: still want to uninstall several packages: have done & no trouble at all

---

### Post by autocrosser on 2009-07-10
Sounds good---looks like we will be seeing the early X start real soon.....:)

update was smooth & the boot looked to be a bit faster..

---

### Post by Vanishing on 2009-07-10
> **autocrosser said:**
> Sounds good---looks like we will be seeing the early X start real soon.....:)

update was smooth & the boot looked to be a bit faster..

On my end, when trying to upgrade, it wants to remove "system-services"&&"startup-tasks", those 2 "big package names" scares me..
lol
im gonna hold back a little.

---

### Post by pferraro on 2009-07-10
> **dino99 said:**
> another new update: still want to uninstall several packages: have done & no trouble at all

This is because the updated apparmor packages build failed:
[https://launchpad.net/ubuntu/karmic/+source/apparmor/2.3+1289-0ubuntu15](https://launchpad.net/ubuntu/karmic/+source/apparmor/2.3+1289-0ubuntu15)

---

### Post by descendent87 on 2009-07-10
> **Vanishing said:**
> On my end, when trying to upgrade, it wants to remove "system-services"&&"startup-tasks", those 2 "big package names" scares me..
lol
im gonna hold back a little.
yeah those are the same 2 that are stopping me from upgrading just yet, give it another day or so and if there still there then I'll take a chance

---

### Post by inportb on 2009-07-10
> **Vanishing said:**
> On my end, when trying to upgrade, it wants to remove "system-services"&&"startup-tasks", those 2 "big package names" scares me..
lol
im gonna hold back a little.

lol I just said *screw it* and went ahead... then rebooted to a fully working system ):P

---

### Post by WelshDragon on 2009-07-10
> **Vanishing said:**
> On my end, when trying to upgrade, it wants to remove "system-services"&&"startup-tasks", those 2 "big package names" scares me..
lol
im gonna hold back a little.
Conflicts were added to those packages as they're now included in upstart. It's fine to upgrade upstart and remove them.

---

### Post by inportb on 2009-07-10
> **WelshDragon said:**
> Conflicts were added to those packages as they're now included in upstart. It's fine to upgrade upstart and remove them.

It's good to know that I haven't killed anything.

---

### Post by zika on 2009-07-10
But this looks more than dangerous than I am prepared to tolerate ... :
```
$ sudo aptitude dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  apparmor libio-compress-zlib-perl upstart-logd 
The following packages will be REMOVED:
  startup-tasks{a} system-services{a} upstart-compat-sysv{a} 
The following packages will be upgraded:
  libcompress-raw-zlib-perl upstart 
2 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 574kB of archives. After unpacking 389kB will be used.
The following packages have unmet dependencies:
  upstart-logd: Depends: upstart (= 0.3.10-2) but 0.6.0-3 is to be installed.
  apparmor: Depends: upstart-compat-sysv (>= 0.3.9-6) but it is not installable or
                     sysvinit (>= 2.86.ds1-56ubuntu3) but it is not installable
  libio-compress-zlib-perl: Depends: libcompress-raw-zlib-perl (< 2.015.~) but 2.020-0ubuntu1 is to be installed.
The following actions will resolve these dependencies:

Remove the following packages:
friendly-recovery
ubuntu-minimal
upstart
upstart-logd

Install the following packages:
sysvinit [2.86.ds1-61ubuntu13 (karmic)]

Keep the following packages at their current version:
libcompress-raw-zlib-perl [2.015-2 (now)]

Leave the following dependencies unresolved:
ubuntu-standard recommends friendly-recovery
Score is 175

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.

```

---

### Post by descendent87 on 2009-07-10
> **WelshDragon said:**
> Conflicts were added to those packages as they're now included in upstart. It's fine to upgrade upstart and remove them.

Thanks for that, went ahead with the update then restarted and all is good.

---

### Post by dino99 on 2009-07-10
take care:

it's better to never dist-upgade on such alpha & beta release

---

### Post by zika on 2009-07-10
> **dino99 said:**
> take care:

it's better to never dist-upgade on such alpha & beta release+1
I always use **sudo aptitude update && sudo aptitude safe-upgrade** this was just for "test" purposes to see what is holding upgrade ...

---

### Post by Craigy90 on 2009-07-10
> **dino99 said:**
> take care:

it's better to never dist-upgade on such alpha & beta release

Can you point me to where you get that idea?

It was my understanding that dist-upgrade is fine when using pre-release stuff. After all, apt-get upgrade doesn't install new packages at all (if my understanding is correct), and that is something that happens frequently in alphas.

I'm not saying you're wrong, just more info please.

---

### Post by MacUntu on 2009-07-10
The recommended way is to use the update manager. You can find that information multiple times in the mailing list archives.

---

### Post by Regenweald on 2009-07-10
I've been using safe-upgrade from the start and it was keeping back upstart, but based on the feedback in this thread i used synaptic to update it and booted fine afterwards. A little research goes a long way in the alpha cycle.

---

### Post by zika on 2009-07-10
> **Regenweald said:**
> I've been using safe-upgrade from the start and it was keeping back upstart, but based on the feedback in this thread i used synaptic to update it and booted fine afterwards. A little research goes a long way in the alpha cycle.
Yes, conflicts were introduced in order to get those old packages removed. I've done it (almost) by hand and everything (except my problem with not-functioning AltF1 and AltF2 [http://ubuntuforums.org/showthread.php?t=1209519](http://ubuntuforums.org/showthread.php?t=1209519)) is OK. Thank You all for advice ...
The only thing that remains unresolved is: do I need AppArmor ... it had to be removed but now I see that new version of libapparmor-perl was installed through update ... Should I reinstall AppArmor (which always fail to load with 2.6.31 kernel of any kind) ...?

---

### Post by Craigy90 on 2009-07-10
> **MacUntu said:**
> The recommended way is to use the update manager. You can find that information multiple times in the mailing list archives.

You mean like this? [https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-July/000586.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-July/000586.html)

It says

>   5. Run an upgrade:

       sudo apt-get dist-upgrade


which implies that this is the standard way to do an upgrade. If that is wrong, please show me where it is recommended to use the update manager.

---

### Post by autocrosser on 2009-07-10
Just so everyone knows---Martin & Colin are doing the upstart upgrades--I am very sure that we would get advance notice if the move was going to b0rk someone's system....I have all the packages that people are talking about removed during the upgrade & have found no problems.....Apparmor is currently removed & I am looking for the upgrade for it--as noted earlier, apparmor has not been working as of late anyway.....

---

### Post by Starks on 2009-07-10
New upstart kills init-rc and prevents booting.

---

### Post by xebian on 2009-07-10
> **wayne_cat said:**
> from /var/log/apt/term.log after upgrading:

```
removing apparmor ...
 * Unloading AppArmor profiles                                                   * Failure: AppArmor module is not loaded
                                                                         [fail]
invoke-rc.d: initscript apparmor, action "stop" failed.
```That means .... AppAmor was not running?

This is funny.  How can you "fail" to stop a non-running process?  Or 'fail' to unload a not-loaded module?

What is even more disturbing is what PID was it trying to stop?

---

### Post by MacUntu on 2009-07-10
> **Craigy90 said:**
> which implies that this is the standard way to do an upgrade. If that is wrong
It is, because that doesn't imply anything other than using 'sudo apt-get dist-upgrade' is _one_ way to do an upgrade (and I'm sure a fair amount of users here - including me - upgrade that way). 

> **Craigy90 said:**
> please show me where it is recommended to use the update manager.
As a start:  [http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Desktops%20%28Recommended%29")

Sure, that's for upgrading from one version of Ubuntu to a newer one but the reason for preferring update-manager over the command-line way (apt-get, aptitude) stays the same: update-manager can be made smarter when there are "problematic updates" that apt and aptitude can't handle properly (sorry if that sounds vague, but you'll find that info if you search through the mailing lists - which I won't do for you :P).

But I just realized you weren't talking about update-manager vs. apt(itude) but about 'apt-get dist-upgrade' vs. 'aptitude safe-upgrade' - can't help you there as I've never used aptitude. :oops:

> **Starks said:**
> New upstart kills init-rc and prevents booting.

Edit: Working fine here.

---

### Post by Starks on 2009-07-10
I fixed the init-rc error by reinstalling the new upstart, but the  necessary scripts needed to start my system were still not present.

I had to chroot to downgrade upstart, reinstall system-services, and  reinstall startup-tasks in order to boot again.

---

### Post by Reiger on 2009-07-10
> **xebian said:**
> This is funny.  How can you "fail" to stop a non-running process?  Or 'fail' to unload a not-loaded module?

What is even more disturbing is what PID was it trying to stop?

Well try this:
```

kill `pidof apparmor`

```
when you don't have apparmor running. Likewise modprobe -r won't enjoy being fed a module that isn't loaded.

Basically the killing part complains about not having something to kill and thus *fails to kill something* and thus stops with an error code.

---

### Post by Starks on 2009-07-10
I don't think the 0.6 packages are safe to install yet. I'll wait a day or two before trying again. Maybe it's missing a few updated helper packages.

---

### Post by garba on 2009-07-10
is upstart now doing something useful or it's still behaving like a wrapper for the the old init system from the 80's?

---

### Post by ronacc on 2009-07-10
I did a normal upgrade and rebooted then dist upgraded to bring in upstart and rebooted , checking bootchart shows nochange in boot time 18 sec before and after . BTW I'm using the RC kernel and no problems .

---

### Post by wayne_cat on 2009-07-10
I did a dist-upgrade and the system works flawless.

---

### Post by buzzmandt on 2009-07-10
> **wayne_cat said:**
> I did a dist-upgrade and the system works flawless.

same here, just did it and no probs at all

---

### Post by autocrosser on 2009-07-10
Apparmor is now updated to work with upstart...downloading & will reboot soon-will post any differences....

---

### Post by autocrosser on 2009-07-10
nothing abnormal---AppArmor is still not working.......

Setting up apparmor (2.3.1+1403-0ubuntu1) ... 
Installing new version of config file /etc/apparmor/rc.apparmor.functions ... 
Installing new version of config file /etc/apparmor.d/tunables/ntpd ... 
Installing new version of config file /etc/apparmor.d/abstractions/audio ... 
Installing new version of config file /etc/apparmor.d/abstractions/base ... 
Installing new version of config file /etc/apparmor.d/abstractions/gnome ... 
Installing new version of config file /etc/apparmor.d/abstractions/nameservice ... 
Installing new version of config file /etc/apparmor.d/abstractions/python ... 
Installing new version of config file /etc/apparmor.d/abstractions/wutmp ... 
Installing new version of config file /etc/apparmor.d/abstractions/xad ... 
Installing new version of config file /etc/init.d/apparmor ... 
 * Starting AppArmor 
 * Mounting securityfs on /sys/kernel/security... 
   ...done. 
 * Loading AppArmor module... 
   ...fail! 
invoke-rc.d: initscript apparmor, action "start" failed. 
 * Starting AppArmor 
 * Loading AppArmor module... 
   ...fail! 
invoke-rc.d: initscript apparmor, action "reload" failed.

---

### Post by pferraro on 2009-07-10
> **autocrosser said:**
> nothing abnormal---AppArmor is still not working.......

Setting up apparmor (2.3.1+1403-0ubuntu1) ... 
Installing new version of config file /etc/apparmor/rc.apparmor.functions ... 
Installing new version of config file /etc/apparmor.d/tunables/ntpd ... 
Installing new version of config file /etc/apparmor.d/abstractions/audio ... 
Installing new version of config file /etc/apparmor.d/abstractions/base ... 
Installing new version of config file /etc/apparmor.d/abstractions/gnome ... 
Installing new version of config file /etc/apparmor.d/abstractions/nameservice ... 
Installing new version of config file /etc/apparmor.d/abstractions/python ... 
Installing new version of config file /etc/apparmor.d/abstractions/wutmp ... 
Installing new version of config file /etc/apparmor.d/abstractions/xad ... 
Installing new version of config file /etc/init.d/apparmor ... 
 * Starting AppArmor 
 * Mounting securityfs on /sys/kernel/security... 
   ...done. 
 * Loading AppArmor module... 
   ...fail! 
invoke-rc.d: initscript apparmor, action "start" failed. 
 * Starting AppArmor 
 * Loading AppArmor module... 
   ...fail! 
invoke-rc.d: initscript apparmor, action "reload" failed.

Apparmor is re-enabled in the incoming kernel update:
[https://launchpad.net/ubuntu/karmic/+source/linux/2.6.31-2.17](https://launchpad.net/ubuntu/karmic/+source/linux/2.6.31-2.17)

---

### Post by autocrosser on 2009-07-10
Sounds good---looking forward to "Shields up!!!"

---

### Post by ghindo on 2009-07-10
New Upstart is working fine for me!  Not sure if AppArmor is working or not, but it boots up fine. :popcorn:

---

### Post by inportb on 2009-07-11
So like, what does it *do*? ;)

---

### Post by taavikko on 2009-07-11
> **inportb said:**
> So like, what does it *do*? ;)

So like, "man upstart" is good place to find out ;)

---

### Post by inportb on 2009-07-11
> **taavikko said:**
> So like, "man upstart" is good place to find out ;)

So like, I don't think *man* shows the changelog. Besides, I'd like to know what changes matter to you, not all changes. ;)

---

### Post by taavikko on 2009-07-11
> **inportb said:**
> So like, I don't think *man* shows the changelog. Besides, I'd like to know what changes matter to you, not all changes.

So then, one would like, use the command "aptitude changelog package" to see the changes :)

---

### Post by plun on 2009-07-11
> **inportb said:**
> So like, I don't think *man* shows the changelog. Besides, I'd like to know what changes matter to you, not all changes. ;)


[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)


):P

---

### Post by autocrosser on 2009-07-11
Thanks Plun!!!! ;)

---

### Post by inportb on 2009-07-11
> **plun said:**
> [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

So... *This release does not have a changelog.*

---

### Post by taavikko on 2009-07-11
> **inportb said:**
> So... *This release does not have a changelog.*

```
upstart (0.6.0-3) karmic; urgency=low

  * Add Conflicts on older Upstart packages to make update-manager's
    job easier.

 -- Scott James Remnant <scott@ubuntu.com>  Fri, 10 Jul 2009 10:11:21 +0100

upstart (0.6.0-2) karmic; urgency=low

  * Bump D-Bus build dependency to ensure we get the container abandonment
    patches, and the GIT version bump.
  * Actually ship /lib/init/upstart-job

 -- Scott James Remnant <scott@ubuntu.com>  Thu, 09 Jul 2009 17:29:59 +0100

upstart (0.6.0-1) karmic; urgency=low

  * New upstream release ("How appropriate, you fight like a cow")
    - my customary changes list since pointless, it's basically a
      complete rewrite.
    - Handles /bin/sh symlink disappearing.  LP: #65024.
    - Boot parameters may be passed to init scripts.  LP: #74664.
    - reboot implies --force during shutdown.  LP: #388738.
    - reboot no longer iterates /proc/ide.  LP: #92685.
    - much improved documentation.  LP: #60429, #72058, #388715.

  * Merge the various upstart packages into a single package, it makes
    little sense to have it all spread out.

```

---

### Post by inportb on 2009-07-11
In other words, there are no user-oriented changes yet? Or you don't know which changes matter to you ;)

---

### Post by taavikko on 2009-07-11
> **inportb said:**
> In other words, there are no user-oriented changes yet? Or you don't know which changes matter to you ;)

Like the version 0.6.0-1 says, basically complete rewrite.

haven't check what the changes really are, and actually they really doesn't matter to me that much.

I'm just waiting for on-demand loading of services...

---

### Post by inportb on 2009-07-11
Well, foundational updates are cool :p

---

### Post by autocrosser on 2009-07-11
> **taavikko said:**
> Like the version 0.6.0-1 says, basically complete rewrite.

haven't check what the changes really are, and actually they really doesn't matter to me that much.

I'm just waiting for on-demand loading of services...


YES--I want the user-services---guess that we'll have to wait til 0.7 for that......

---

### Post by garba on 2009-07-11
so basically nothing has changed with this new release, oh well

---

### Post by jpeddicord on 2009-07-11
"How appropriate, you fight like a cow" -- definitely one of the more creative release names.

---

### Post by psyke83 on 2009-07-11
> **jacobmp92 said:**
> "How appropriate, you fight like a cow" -- definitely one of the more creative release names.

Wow, somebody's going to be hearing from the [LucasArts]("http://www.lucasarts.com/games/monkeyisland/") legal department... ;)

---

### Post by pferraro on 2009-07-12
> **garba said:**
> so basically nothing has changed with this new release, oh well

Huh?
[https://launchpad.net/upstart/+announcement/3170](https://launchpad.net/upstart/+announcement/3170)

---

### Post by jpeddicord on 2009-07-12
Looks like mostly control refinements with initctl and some new dbus toys. Still don't see very many system services using it, but I guess that will come with time.

---

### Post by MacUntu on 2009-07-12
> **jacobmp92 said:**
> but I guess that will come with time.

I heard that before - some releases ago. :P

---

### Post by jpeddicord on 2009-07-12
> **MacUntu said:**
> I heard that before - some releases ago. :P

"In a quick change of events, Upstart 1.0 will have the release codename 'Duke Nukem Forever.'"


...somebody should definitely suggest that.

---

### Post by garba on 2009-07-12
> **pferraro said:**
> Huh?
[https://launchpad.net/upstart/+announcement/3170](https://launchpad.net/upstart/+announcement/3170)

ok this is nice but the point is as long as upstart works in system V compatibilty mode, as it always has till now (i.e. inkove the /etc/rc script which, in turn, spawns the other processes), we shall not benefit from these features at all, that's it...

---

### Post by autocrosser on 2009-07-12
> **jacobmp92 said:**
> "In a quick change of events, Upstart 1.0 will have the release codename 'Duke Nukem Forever.'"


...somebody should definitely suggest that.

:lolflag:  Or it could be "UT3"

---

### Post by MacUntu on 2009-07-12
I guess (as upstart works event-driven) it's not easy to just replace scripts bit by bit?

---

### Post by pferraro on 2009-07-12
> **MacUntu said:**
> I guess (as upstart works event-driven) it's not easy to just replace scripts bit by bit?

I recall someone trying this already (using upstart 0.5) - and with some pretty impressive results:
[http://ubuntuforums.org/showthread.php?t=727224](http://ubuntuforums.org/showthread.php?t=727224)

---

### Post by MacUntu on 2009-07-12
Nice, thanks for the link. :)

---

### Post by tekstr1der on 2009-07-12
Against my better judgment I took the plunge on new upstart with an aptitude dist-upgrade. Now I cannot boot into 2.6.31-2. I get the following:

init: rc-sysinit main process (1101) killed by INT signal

This is a new one for me. Got to recovery mode terminal with networking on 2.6.30 and made sure all updates were applied. Should I try to reverse the process and downgrade upstart?

---

### Post by Starks on 2009-07-12
My boot times are looking better these days.

Here's a bootchart.

---

### Post by inportb on 2009-07-13
Well, here comes another upstart update...

---

