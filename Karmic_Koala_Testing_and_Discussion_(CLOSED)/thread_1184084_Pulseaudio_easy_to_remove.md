---
title: "Pulseaudio easy to remove?"
date: 2009-06-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by crys on 2009-06-10
Hi,

I currently have jaunty on my laptop but I consider upgrading to KK. The only thing that prevents me from doing so is Pulseaudio. In jaunty it was easy to simply deinstall it without having another huge bunch of packages getting removed.
So, how do the dependencies on pulseaudio look in KK? Is it simple to remove it?
Please no discussion about the advantages of pulse. I simply don't want it on my system. Got me sleepless nights in the past when skype and ekiga didn't work due to that.

Thanks
Chris

---

### Post by psyke83 on 2009-06-10
Karmic Koala isn't released yet. Until it is, the main purpose is to test the system you are presented with, and removing PulseAudio will impair your ability to test what the developers need you to test.

---

### Post by crys on 2009-06-10
This wasn't the question (I thought this would happen...). Again, is it easy to remove?

---

### Post by VastOne on 2009-06-10
> **crys said:**
> This wasn't the question (I thought this would happen...). Again, is it easy to remove?

Then would it not be wise to set it up and test your own queries and report that back to the masses?

---

### Post by crys on 2009-06-10
No, it wouldn't. Since if pulse would not get removed easily then I would have a useless system. Hence the question.

---

### Post by super.rad on 2009-06-10
If you want a system without pulse then why not switch to a distro that doesn't use it by default (debian and arch don't use it) instead of upgrading

---

### Post by psyke83 on 2009-06-10
> **crys said:**
> This wasn't the question (I thought this would happen...). Again, is it easy to remove?

Even when you ask the wrong question, it's always good to have the right answer.

Anyway: 

```
conn@inspiron:~$ sudo apt-get remove pulseaudio
[sudo] password for conn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf
  pulseaudio-module-hal pulseaudio-module-x11 ubuntu-desktop
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
After this operation, 4112kB disk space will be freed.
Do you want to continue [Y/n]? ^C
```

Note: if you are dist-upgrading from Jaunty rather than installing from scratch, you should *not* remove PulseAudio until you have finished the upgrade (because the ubuntu-desktop metapackage may need to pull in new dependencies). You will also encounter problems if further updates to the Karmic ubuntu-desktop metapackage pull in new packages.

---

### Post by VastOne on 2009-06-10
> **crys said:**
> No, it wouldn't. Since if pulse would not get removed easily then I would have a useless system. Hence the question.

This was exactly psyke83's point. You obviously have experience in removing it in Jaunty, why not use that to your advantage and report back the results? I always try to find my own solutions before I ask for help and on a test sandbox platform, these type of trials and results will help many. Just a thought.

---

### Post by crys on 2009-06-10
Thanks a lot, psyke83. That is exactly the kind of information I was interested in.

---

### Post by VastOne on 2009-06-10
> **psyke83 said:**
> Even when you ask the wrong question, it's always good to have the right answer.

Anyway: 

```
conn@inspiron:~$ sudo apt-get remove pulseaudio
[sudo] password for conn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf
  pulseaudio-module-hal pulseaudio-module-x11 ubuntu-desktop
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
After this operation, 4112kB disk space will be freed.
Do you want to continue [Y/n]? ^C
```

Well said....;)

---

### Post by Kow on 2009-06-13
Haha nice. Yea it's either Y/N/^C. Y = Yes, N = No, ^C = H*** NO!

---

