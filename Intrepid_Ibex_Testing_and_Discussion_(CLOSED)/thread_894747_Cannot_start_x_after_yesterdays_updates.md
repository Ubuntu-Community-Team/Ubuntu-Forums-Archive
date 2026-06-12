---
title: "Cannot start x after yesterdays updates"
date: 2008-08-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by danbuter on 2008-08-19
I get fatal server error: cannot create lock file in /tmp/.tX0-lock.
Also, error in locking authority file /home/username/.Xauthority

Anyone else having this problem? I have ubuntu, xubuntu, and kubuntu all installed, with gdm as main startx.

---

### Post by plun on 2008-08-19
Yup, my /home was also broken and I lost all permissions.

Restarted and choosed another kernel from the GRUB menu and everything was OK again.... cannot reproduce this error.

---

### Post by ccw on 2008-08-19
> **danbuter said:**
> I get fatal server error: cannot create lock file in /tmp/.tX0-lock.
Also, error in locking authority file /home/username/.Xauthority

Anyone else having this problem? I have ubuntu, xubuntu, and kubuntu all installed, with gdm as main startx.

Yeah, it seems like everything got mounted read only. After 2 reboots, it came back.

No clue what happened.

---

### Post by plun on 2008-08-19
> **ccw said:**
> Yeah, it seems like everything got mounted read only. After 2 reboots, it came back.

No clue what happened.

Yup... it was really strange.

Impossible to find any clues also within logfiles, at least with my knowledge.

But everything must have been read-only.....

---

### Post by ccw on 2008-08-19
The only update I see that might have done it is devmapper.

---

### Post by Nullack on 2008-08-19
> **plun said:**
> Yup, my /home was also broken and I lost all permissions.

Restarted and choosed another kernel from the GRUB menu and everything was OK again.... cannot reproduce this error.

Mate werent you on kernel next though? This is important to this situation

---

### Post by plun on 2008-08-19
> **Nullack said:**
> Mate werent you on kernel next though? This is important to this situation

Yup, but it must have been something else.
And I couldn't reproduce it.

Next time a connect with SSH from another PC and check the logfiles.

It was also a "bump" for 2.6.26-5 and all modules on Sunday/Monday

---

### Post by BwackNinja on 2008-08-19
hmmm... I've been greeted with a nice blue screen telling me X could not start a few times, I looked through the logs and found a backtrace for wacom (which happened inconsistantly), I created a new xorg.conf (I was using my old cluttered one) and I still get the problem sometimes, with a completely fine Xorg.0.log. I have to remount "/" read-write and restart gdm, then everythings fine.

Of all things, I hate inconsistant problems.

---

### Post by ccw on 2008-08-19
> **plun said:**
> 

It was also a "bump" for 2.6.26-5 and all modules on Sunday/Monday

I *think* I installed that and rebooted previously. I'll confirm with the last logs in the morning.

---

### Post by RAOF on 2008-08-19
I'm guessing at least one of you is hitting at least one of [these](https://bugs.edge.launchpad.net/ubuntu/+source/sysvinit/+bug/255562) [bugs](https://bugs.edge.launchpad.net/ubuntu/+source/sysvinit/+bug/255563). :)

---

### Post by ronacc on 2008-08-19
so the workaround would be wait awhile to let fsck finish and then reboot ?

---

### Post by RAOF on 2008-08-19
Yup, if it's / being fsck'd.  If it's just /home, then you can wait for it to finish then remount r/w.

---

### Post by ccw on 2008-08-20
> **ccw said:**
> I *think* I installed that and rebooted previously. I'll confirm with the last logs in the morning.

I rebooted monday morning: I'm pretty sure that was for the kernel.

---

