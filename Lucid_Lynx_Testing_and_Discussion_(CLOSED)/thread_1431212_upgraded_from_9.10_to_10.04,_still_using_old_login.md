---
title: "upgraded from 9.10 to 10.04, still using old login screen"
date: 2010-03-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by whoop on 2010-03-16
I upgraded a machine from 9.10 to 10.04 and I still get the same brown login screen.
Any idea in which direction I should look?

---

### Post by kalasoka on 2010-03-16
Oh no - 10.04 LTS is going to release! I just upgraded to 9.10 yesterday. I could have waited for some more days!

---

### Post by uRock on 2010-03-16
Have you installed all of the updates?

---

### Post by whoop on 2010-03-16
> **kalasoka said:**
> Oh no - 10.04 LTS is going to release! I just upgraded to 9.10 yesterday. I could have waited for some more days!

Uhhmm, charming... This is the Lucid Lynx Testing and Discussion forum. I am testing and discussing, I don't know what you are doing :shock:...

---

### Post by whoop on 2010-03-16
> **iRock said:**
> Have you installed all of the updates?

Yes, it was a complete upgrade without any errors. 
It is off course possible that the upgrade process skipped something. Updating now doesn't offer any packages.

The only related thing I can think of is that "quiet splash" was manually removed from /etc/default/grub in 9.10

---

### Post by shafin on 2010-03-16
You can try purging and then reinstalling GDM

---

### Post by MasterNetra on 2010-03-16
> **whoop said:**
> Yes, it was a complete upgrade without any errors. 
It is off course possible that the upgrade process skipped something. Updating now doesn't offer any packages.

The only related thing I can think of is that "quiet splash" was manually removed from /etc/default/grub in 9.10

oh...upgrading from 9.10 to 10.04 was probably not the best idea. I hope this is your testing machine. If you want to run 10.04 you would of been better off with a fresh install or installing it and running it in a VM.

---

### Post by whoop on 2010-03-16
Hhhm, I am under the impression that no one thinks upgrading requires testing ;)

---

### Post by uRock on 2010-03-16
Upgrades have always broke people's systems. I don't think that will change any time soon. I have a dead system right now because I upgraded.

---

### Post by whoop on 2010-03-16
> **iRock said:**
> Upgrades have always broke people's systems. I don't think that will change any time soon. I have a dead system right now because I upgraded.

All the more reason to test it... And because of this, all my production machines have enjoyed successful upgrades for years...

anyhow, I fixed it via removing /var/lib/gdm/.gconf

---

### Post by DeShark on 2010-03-21
I had the same problem too, again upon upgrading (I agree that upgrading needs testing too). Thanks for the fix whoop! Should this be filed as a bug or is it more a case of the old config files being kept (as they probably should be)?

---

### Post by whoop on 2010-03-22
Well, I have been communicating with a developer/maintainer and he claimed that this would only happen if you manually tweaked/changed gdm settings (I can't for the life of me remember that I did that however).

The bug is here:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/539605](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/539605)

but we marked it as invalid, as we assumed I had been tweaking the set-up.
If you are "sure" like me you haven't tweaked any gdm stuff while using 9.10 we should change the status of this bug again.
You are welcome to that yourself or you can reply in this thread (or do nothing at all off-course ;))

cheers...

---

