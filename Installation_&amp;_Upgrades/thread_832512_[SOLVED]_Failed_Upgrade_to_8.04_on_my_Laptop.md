---
title: "[SOLVED] Failed Upgrade to 8.04 on my Laptop"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by alice_jane on 2008-06-17
I have a Compaq Evo N1050v laptop that I've been running ubuntu 7.04 on without any problems. I decided to upgrade to ubuntu 8.04. About 20% of the way through installation the computer froze completely - no error messages or anything, but just totally frozen. After leaving it overnight I rebooted. It starts up alright, but I am unable to perform any updates/every window I open (firefox/terminal/etc) lacks the close/minimize buttons in the upper right corner. My questions are:
1. Did I irreversibly f*%$ up my laptop?
2. Can I "undo" whatever happened and go back to my functioning 7.04 laptop? 
3. If I can't go back, how should I go about salvaging my upgrade?

---

### Post by lost09 on 2008-06-17
I can't solve your problem, but as I am struggling with the update process myself, I can perhaps offer a point of consideration. That is, updating is supported only if one updates in sequence, which means the proper procedure is to go through, in your case, 7.10.[ Here's what I'm talking about.]("https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion") 

I hope this helps.

---

### Post by alice_jane on 2008-06-17
Thanks, I'll try that... I should have known that skipping a version wasn't a good idea.

---

### Post by Victormd on 2008-06-17
> **alice_jane said:**
> 1. Did I irreversibly f*%$ up my laptop?
Not sure how to answer this, but some packages might have been updated and are not fully compatible with 7.04 and from the looks of it, your repositories have been corrupted as well.

> **alice_jane said:**
> 2. Can I "undo" whatever happened and go back to my functioning 7.04 laptop?

If you were trying to update using the update manager, I would go to the terminal and type
```
sudo apt-get update
```
and see what the output looks like. If it has any reference to Hardy, the problem is with your repositories and that's an easy one (not necessarily ONLY with, but also).

If nothing abnormal happens, type
```
sudo apt-get upgrade
```
to try to force an upgrade to the packages (or a fix/downgrade)
then
```
sudo apt-get autoremove
```
and
```
sudo apt-get install -f
```
and this should clean any broken packages.

> **alice_jane said:**
> 3. If I can't go back, how should I go about salvaging my upgrade?
**[COLOR="Red"]Backup all your data and do a fresh install of Hardy or your previous version.[/COLOR]** I know that a lot of people have been experiencing problems upgrading directly (specially jumping a version) and after a fresh install, the system is fine.
(I would probably do this last alternative)...

---

### Post by lost09 on 2008-06-17
Speaking of salvaging upgrades, do you know what to do if the upgrade process has been aborted (due to failed internet connection)? The problem I'm having is that the Upgrade Manager no longer offers me the "8.04 is now available" option, despite the fact that I'm still stuck on 7.10. Also, and I don't mean to muscle in on the thread here, but when I tried "sudo apt-get update", I received this unfriendly message: 

GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

and I have no idea what to do about it. *sigh*

---

### Post by Victormd on 2008-06-17
The signature problem is because your repositories were probably corrupted during the partial upgrade.

you can go through the terminal:
```
sudo apt-get dist-upgrade
```
or
```
sudo update-manager -d
```

A word of advice... backup all your data, have a hardy live CD available and be ready to do a fresh install... :)
Not very many people have been successful in upgrading directly (as far as I know)...

---

### Post by Victormd on 2008-06-17
You can also try the same command I gave to alice_jane, also in the terminal, type
```
sudo apt-get install -f
```

---

### Post by lost09 on 2008-06-18
I'll try those this evening (on a lab comp at the moment); but I received the same error message prior to my first attempt at upgrading.

---

### Post by alice_jane on 2008-06-18
Thank you all so much! It worked and my laptop is now working just fine (Running ubuntu 8.04)

---

### Post by lost09 on 2008-06-18
Congrats; I'm envious.

---

