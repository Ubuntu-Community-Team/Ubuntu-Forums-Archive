---
title: "Linux Kernel RC3 Released!!"
date: 2009-07-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by woodbj on 2009-07-14
> Another week, another -rc.

As I mentioned last time, I really wish things would calm down. And to 
_some_ degree they have. In other areas? Not so much.

That said, the single biggest patch here is actually a revert - a removal 
of the Langwell USB OTG driver that wasn't ready and needed infrastructure 
that isn't going to happen in 2.6.31.

But other than that, there's a fair chunk of changes to the 'perf' utility 
(which obviously isn't going to cause kernel regressions), but also to 
things like cifs, video drivers (both of the DVB kind and and for DRM with 
more i915 KMS updates). 

There are also the usual arch updates (although perhaps unusually, it's 
actually more removal than additions - mostly thanks to microblaze taking 
advantage of the generic includes, I suspect).

That said, apart from a few things like that, that are move visible thanks 
to their bulk, _most_ of the changes really are small stuff. A lot of 
one-liners etc. The shortlog (appended) gives a reasonable view.

		Linus

[http://lkml.org/lkml/2009/7/13/380](http://lkml.org/lkml/2009/7/13/380)

---

### Post by buzzmandt on 2009-07-14
Wooohooo, I hope the intel graphics performance is back up to par....

actually, I'll settle for boggie at this point..

---

### Post by taavikko on 2009-07-14
And the linux-meta was just done, should be available in the repos in few hours :)
18:23 EEST at the moment

---

### Post by rudenko_ruslan on 2009-07-14
Using it right now, things are working OK for me:
> ruslan@ruslan-desktop:~$ uname -a
Linux ruslan-desktop 2.6.31-020631rc3-generic #020631rc3 SMP Tue Jul 14 09:43:49 UTC 2009 i686 GNU/Linux
ruslan@ruslan-desktop:~$ 
Downloaded it from there - [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc3/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc3/) :)

---

### Post by taavikko on 2009-07-14
> **rudenko_ruslan said:**
> Using it right now, things are working OK for me:

Downloaded it from there - [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc3/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc3/) :)

who's got the ants in the pants ;)
 
Sometimes the linux-pgk isn't done for some reasons, but this was fast work by the devs.

---

### Post by plun on 2009-07-14
It is also uploaded for Karmic but not released

> linux (2.6.31-3.18) karmic; urgency=low

  [ Andy Whitcroft ]

  * Revert "Add splice-2.6.23.patch from AUFS to export a symbol needed by
    AUFS"
  * Revert "Add put_filp.patch from AUFS to export a symbol needed by AUFS"
  * Revert "Add sec_perm-2.6.24.patch from AUFS - export
    security_inode_permission"
  * clear out left over AUFS files and modifications

  [ Luke Yelavich ]

  * [Config] Enable CONFIG_USB_ISP116X_HCD on sparc
  * SAUCE: Explicitly include header files to allow apparmor to build on
    powerpc
  * [Config] Enable CONFIG_BLK_DEV_IDECD on powerpc

  [ Tim Gardner ]

  * [Config] Dropped ubuntu/misc/wireless/acx
  * [Config] Disabled NDISWRAPPER until the compile issues are fixed.

  [ Upstream ]
[B]
  * Rebased to 2.6.31-rc3[/B]

[https://lists.ubuntu.com/archives/karmic-changes/2009-July/004058.html](https://lists.ubuntu.com/archives/karmic-changes/2009-July/004058.html)


---

### Post by taavikko on 2009-07-14
> **plun said:**
> It is also uploaded for Karmic but not released

It is already done: [https://edge.launchpad.net/ubuntu/karmic/+queue?queue_state=3&queue_text=](https://edge.launchpad.net/ubuntu/karmic/+queue?queue_state=3&queue_text=)

Is available in the repos when next time it updates (usually once every hour)

---

### Post by plun on 2009-07-14
> **taavikko said:**
> It is already done: [https://edge.launchpad.net/ubuntu/karmic/+queue?queue_state=3&queue_text=](https://edge.launchpad.net/ubuntu/karmic/+queue?queue_state=3&queue_text=)

Is available in the repos when next time it updates (usually once every hour)

Yup, available for manual install...;)

---

### Post by taavikko on 2009-07-14
> **plun said:**
> Yup, available for manual install...;)

Yep, thats why I just got linux-libc-dev-2.6.31-2.17 through the repos...
```
Current status: 2 updates [+2], 398 new [+6].
Reading package lists... Done                
Building dependency tree                     
Reading state information... Done            
Reading extended state information           
Initializing package states... Done          
The following packages will be upgraded:     
  linux-libc-dev upstart                     
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1237kB of archives. After unpacking 0B will be used.       
Do you want to continue? [Y/n/?] y 
```

But then again...
```
Message: 6
Date: Tue, 14 Jul 2009 16:00:26 -0000
From: Andy Whitcroft <apw@canonical.com>
Subject: [ubuntu/karmic] linux 2.6.31-3.19 (Accepted)
To: karmic-changes@lists.ubuntu.com
Message-ID:
       <20090714160026.13564.92178.launchpad@cocoplum.canonical.com>
Content-Type: text/plain; charset="utf-8"

linux (2.6.31-3.19) karmic; urgency=low

 [ Andy Whitcroft ]

 * Revert "[Config] Disabled NDISWRAPPER"
 * ndiswrapper -- fix i386 compilation failures on cmpxchg8b
 * AUFS -- export various core functions
 * AUFS -- export various core functions -- fixes
 * AUFS -- core filesystem
 * AUFS -- track changes in v2.6.31
 * [Config] Enable AUFS
 * droppped 'iwl3945: do not send scan command if channel count zero' as it
   is already upstream but failed to auto-drop on rebase.

 [ Eric Paris ]

 * SAUCE: fsnotify: use def_bool in kconfig instead of letting the user
   choose
 * SAUCE: inotify: check filename before dropping repeat events
 * SAUCE: fsnotify: fix inotify tail drop check with path entries
```

---

### Post by plun on 2009-07-14
> **taavikko said:**
> 

But then again...


Huh !....  I dont get it... works just fine for me...???

---

### Post by jppr on 2009-07-14
just updated new kernel and linux-meta

---

### Post by dino99 on 2009-07-14
hey,

apparmor still failed

---

### Post by caryb on 2009-07-14
It works on my machine but I would have thought they would have fixed the no DVD found error in the new kernel.


Cary

---

### Post by wayne_cat on 2009-07-14
> **caryb said:**
> It works on my machine but I would have thought they would have fixed the no DVD found error in the new kernel.


Cary

it works on your machine? ... my apparmor is still whining 

```
root@macbook:~# /etc/init.d/apparmor start
 * Starting AppArmor 
 * Loading AppArmor module...                                [fail] 
root@macbook:~# /etc/init.d/apparmor status
apparmor module is loaded.
apparmor filesystem is not mounted.
root@macbook:~# 

```

---

### Post by caryb on 2009-07-14
Sorry I meant the kernel is working!


Cary

---

### Post by wayne_cat on 2009-07-14
> **caryb said:**
> Sorry I meant the kernel is working!


Cary

lame excuse ... you just don't want to tell us how you fixed it. :biggrin:

My laptop seems to run cooler with this kernel ... or maybe one of the other fixes? ... can't hear the fans at the moment.

---

### Post by KhaaL on 2009-07-15
Can anyone report if the X-Fi cards are working now under this kernel?

---

### Post by dino99 on 2009-07-15
with this new kernel, apps don't find sun-java

---

### Post by caryb on 2009-07-15
> **dino99 said:**
> with this new kernel, apps don't find sun-java

Sounds strange that a kernel could do this! But must confess something has changed to kill my sun java as well

Cary

---

### Post by taavikko on 2009-07-15
> **dino99 said:**
> with this new kernel, apps don't find sun-java

> **caryb said:**
> Sounds strange that a kernel could do this! But must confess something has changed to kill my sun java as well

Cary

working correctly here.
Though, tested only firefox and java-plugin.

Shouldn't have anything to do with kernel?

---

### Post by linux6994 on 2009-07-15
I installed the kernel last night and all is working fine java, cdma mobile broadband card etc except that upon boot the video selection asks for video mode, a space bar does the trick.

Linux dad-laptop 2.6.31-020631rc3-generic #020631rc3 SMP Tue Jul 14 09:43:49 UTC 2009 i686 GNU/Linux

---

