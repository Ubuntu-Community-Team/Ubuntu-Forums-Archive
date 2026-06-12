---
title: "Unable to log in, gdm hangs and restarts"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zeimusu on 2010-04-07
I'm having problems logging in today, after an update. 

Gdm allows me to click my name, but then hangs, won't accept keyboard or mouse input, and shortly after gdm restarts. Is anyone else seeing anything similar. I can log in on tty1

Is there anything I can to to bypass gdm, some kind of automatic login that I can set up?

These are reported [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/557245](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/557245)

---

### Post by spotdog14 on 2010-04-07
I am kind of having the same problem except I can put my password in and it attempts to login but just restarts me right to the login page.

---

### Post by CryptoPaul on 2010-04-07
This looks similar to a bug that has affected users with the nvidia-96 driver enabled...

[http://ubuntuforums.org/showthread.php?t=1443520](http://ubuntuforums.org/showthread.php?t=1443520)

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/553200](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/553200)

---

### Post by spotdog14 on 2010-04-07
> **CryptoPaul said:**
> This looks similar to a bug that has affected users with the nvidia-96 driver enabled...

[http://ubuntuforums.org/showthread.php?t=1443520](http://ubuntuforums.org/showthread.php?t=1443520)

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/553200](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/553200)
For some reason I cannot startx manually after I stop GDM, all I get is a black screen with my cursor in the middle.

---

### Post by zeimusu on 2010-04-07
Thanks CryptoPaul, that's my bug.

---

### Post by Norradj on 2010-04-07
I got the same problem/bug.
However, if I boot in recover mode, then log in and then "startx" it works fine.

---

### Post by spotdog14 on 2010-04-08
> **spotdog14 said:**
> For some reason I cannot startx manually after I stop GDM, all I get is a black screen with my cursor in the middle.
Bump, anyone have any clue what my problem might be? I cannot seem to get x to start again after killing gdm. 

How do you update from the command line anyways?

---

### Post by dannyboy79 on 2010-04-08
> **spotdog14 said:**
> Bump, anyone have any clue what my problem might be? I cannot seem to get x to start again after killing gdm. 

How do you update from the command line anyways?
i've been hit with this bug also, can't use gdm to login, it just loops back to itself after hitting enter after I enter my password. so i go to tty1, stop gdm, then just issue startx W/OUT using sudo. 

if you still can't start x for whatever reason, then do update and upgrade packages, jsut run this:

sudo apt-get update && sudo apt-get upgrade

---

### Post by ranch hand on 2010-04-08
> **spotdog14 said:**
> Bump, anyone have any clue what my problem might be? I cannot seem to get x to start again after killing gdm. 

How do you update from the command line anyways?

Boot to recovery mode and you can probably log in there  with "startx".  If not try the "dpkg fix broken packages option".  If there is a problem with that not being able to connect try the "root with networking" option and update there using; ```
 apt-get update 
``` and then; [code] apt-get upgrade [code]

---

