---
title: "apt-get busted after update (jaunty)"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by RebateFX on 2009-03-30
I just ran

sudo apt-get update then sudo apt-get upgrade

After some packages installed, the whole machine locked up. After booting again, nvidia drivers and other things appeared broken so I rebooted into the recovery option in grub, then used the repair menu item which then completed installing the updates.

However it said there is a problem with apt. If I run apt-get update or apt-get upgrade now, it does nothing. No output to the terminal.

So I decided to find a command switch to give me some verbosity and perhaps an error output. man apt-get is blank :/

Is anyone else suffering a broken apt-get? Anyone know how I can fix it? Perhaps reinstalling apt-get somehow?

---

### Post by sgtbug on 2009-03-31
Have you tried running sudo aptitude update, and then upgrade?

---

### Post by RebateFX on 2009-03-31
That gives me a little more info :)

```
jafar@oberon:~$ sudo aptitude update
[sudo] password for jafar: 
aptitude: error while loading shared libraries: /usr/lib/libapt-pkg-libc6.9-6.so.4.7: file too short
jafar@oberon:~$
```

libapt-pkg-libc6.9-6.so.4.7 is corrupt? Next question is how to fix it with a broken apt?

---

### Post by RebateFX on 2009-03-31
BTW, this is the output from an attempt to fix it...

```
jafar@oberon:~$ sudo dpkg --configure -a
dpkg: error processing apt (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up x11-utils (7.4+1build1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing x11-utils (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 apt
 x11-utils
jafar@oberon:~$ 
```

Seems there is more borked than just that. Wine is also destroyed but that is another issue ;)

---

### Post by RebateFX on 2009-03-31
Fixed it by downloading the apt deb from [http://packages.ubuntu.com/jaunty/apt](http://packages.ubuntu.com/jaunty/apt) and installed a new copy with dpkg. That was a little scary. The first time I've ever had to go through any pain to fix Ubuntu. Well, that's alpha for you ;)

---

### Post by | MM | on 2009-03-31
Maybe your disk is on the way out?

---

### Post by RebateFX on 2009-03-31
> **| MM | said:**
> Maybe your disk is on the way out?

I hope the fsck not :D Actually I did test that. This laptop is less than 6 months old so I hope not.

---

### Post by mpcd on 2009-03-31
I'm having a similar problem. Whenever apt crashes it causes filesystem failures so bad that the OS sometimes ends up remounting / as read-only. I've already lost a ton of data out of my home directory and I've barely done anything since installing jaunty a couple of days ago. I have to keep scrounging through /lost+found just to get my bookmarks back.

I'm trying the apt reinstall suggested now.

---

