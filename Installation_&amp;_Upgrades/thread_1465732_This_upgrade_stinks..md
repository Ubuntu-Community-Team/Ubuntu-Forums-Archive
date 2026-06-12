---
title: "This upgrade stinks."
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by GreenMeanie on 2010-04-29
We need to run a POLL on failed upgrades.
I had a fresh version of 9.10 and did the upgrade through update manager and now everything stutters and there is no Nvidia drivers working.

An upgrade shouldn't be so painful.

---

### Post by phillw on 2010-04-29
> **GreenMeanie said:**
> We need to run a POLL on failed upgrades.
I had a fresh version of 9.10 and did the upgrade through update manager and now everything stutters and there is no Nvidia drivers working.

An upgrade shouldn't be so painful.

Well, it could be as simple as the servers are over-loaded and something timed out. TBH, why everyone and their dog wants to upgrade at the zero hour is beyond me. I've had 10.04 since the RC of alpha1, I'm not even looking to do an upgrade of my 9.10 system until the servers have had their nervous breakdown & I am assured of a decent link to them (like in a couple of days time).

As to Nvidia and 10.04 if you do a google 
> 
+10.04 nvidia lucid +ubuntuforums +*YOURCARD*

you should hit on results from the testing area.

Hope that helps,

Phill.

---

### Post by finlost on 2010-04-29
I am running Ubuntu 9.10 on two different machines.  One is a dual boot with Vista and the other is pure Ubuntu.  

Semi-related question:  Is it recommended to do a fresh install over an upgrade to get to 10.04?  It seems in the past that fresh install has been the preferred method.

---

### Post by jerenept on 2010-04-29
Fresh installs and upgrades have their pros and cons. 
Pros of fresh install: 1 clean, fresh system, usually faster performance than upgrade.
Cons: you have to reinstall all your programs (I assume you're backing up your files!!)

Pros of upgrade: More convenient for most users, all your programs are still there.
Cons: said to be buggy. saw no evidence of this however, in my experience.
These are the ones i know of. I am sure there are more

---

### Post by phillw on 2010-04-29
> **finlost said:**
> I am running Ubuntu 9.10 on two different machines.  One is a dual boot with Vista and the other is pure Ubuntu.  

Semi-related question:  Is it recommended to do a fresh install over an upgrade to get to 10.04?  It seems in the past that fresh install has been the preferred method.

^^ see above ^^ I'm not even going to try to do upgrade my 9.10 for a couple of days. As 9.10 brought in ext4 & grub2, you should be fine doing the upgrade. If you're bored in the mean time if you have not already made a seperate /home, now is a real good time to do it. That way any upgrade cannot harm your data [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) is good place.

I did an upgrade with LAMP on my system, then upgraded to grub2 and ext4 file system from 9.04 --> 9.10 the secret, it appears, is to have backups; only when you do not have backups do things go wrong.

Regards,

Phill.

---

