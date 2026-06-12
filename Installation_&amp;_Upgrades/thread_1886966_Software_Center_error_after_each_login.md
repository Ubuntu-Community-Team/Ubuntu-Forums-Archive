---
title: "Software Center error after each login"
date: 2011-11-25
forum: Installation &amp; Upgrades
---

### Post by kurtkurtosis on 2011-11-25
I am totally new to Linux and when I log into Ubuntu 11.10 I am greeted by the message that the Software Center has some problems.

I am using a SuperMicro X9SCM server board with a GeForce 9400 GT graphics card whose driver I cannot get initialized as well. That was actually another post I intended but I am not sure whether that is related.

In any case, I believe the error relates to either updating the software or to installing the graphics driver. 

- Specifically I am asked to repair the software catalog but that fails.
 - Items cannot be installed or removed until the package catalog repaired. Do you want to repair it now?

THIS create an infinite loop as the repair apparently errors out.

ALSO: Package operation failed. The operation of removal of a software package, InstallArchives() failed: (Reading database... 5%)

I am clueless as Linux seems like a different world to me.

Any help would be appreciate such as looking at error logs, although I am not sure where to begin looking.

THX

---

### Post by hansdown on 2011-11-26
Welcome to the forum, kurtkurtosis.

Not sure, if I can help, but have you installed any "paid apps"?

---

### Post by kurtkurtosis on 2011-11-26
No I haven't.

In any case, I haven't done only a few things such as installing dropbox, some restricted video codecs, and probably a few other things.

In any case. Where I am is that I can not install any software as this cause an error with the software.

So I just reinstalled 11.10 for the 2nd time as this only takes about 10 minutes or so.

However, I will have to see whether Linux is really for me given the problems...at least I can say, I gave it a try.

---

### Post by hansdown on 2011-11-26
> **kurtkurtosis said:**
> No I haven't.

In any case, I haven't done only a few things such as installing dropbox, some restricted video codecs, and probably a few other things.

In any case. Where I am is that I can not install any software as this cause an error with the software.

So I just reinstalled 11.10 for the 2nd time as this only takes about 10 minutes or so.

However, I will have to see whether Linux is really for me given the problems...at least I can say, I gave it a try.

Thanks for posting back, kurtkurtosis.

Also, thankyou for your polite comments.

I'm still trying , to learn the software center, so I was hoping someone would jump in.

---

### Post by raja.genupula on 2011-11-26
Hi man , I hope you're doing .
provide me output of ```
sudo apt-get update
```

and try install something from terminal with this command
sudo apt-get install <app_name>

report here , what you got .

Thank you.

---

### Post by mörgæs on 2011-11-26
If you are new, I would recommend Xubuntu rather than Ubuntu. 


For restoring Software Centre, you could try to boot the computer and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```


Please post the error messages, if any.

---

### Post by kurtkurtosis on 2011-11-26
I decided to reinstall 11.10 and both the software center & NVIDIA driver are now finally installing.

I found some good links on using rsnapshot so I can hopefully always restore to a previous working condition of the operating system.

THX.

---

### Post by mörgæs on 2011-11-26
Good, please mark the thread 'solved'.

---

### Post by kurtkurtosis on 2011-11-26
-> please mark the thread 'solved'.

Unclear to me on how to do that even after searching for HELP. THX

---

### Post by mörgæs on 2011-11-27
Look in Thread Tools.

---

