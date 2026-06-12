---
title: "Ubuntu 17.04 Running extremely slow after installation"
date: 2017-04-21
forum: Installation &amp; Upgrades
---

### Post by spencermat on 2017-04-21
Hello all, I have been messing around with different linux distros lately and was trying to install the newest version of Ubuntu. To install I have to use the options nomodeset, EDD = on, and nolapic. After I installation though ubuntu runs ridiculously slow. Like so slow I can't get the mouse even to a button. There is a screen up that says Ubuntu 17.04 has experienced an internal error. I have reinstalled and the same thing happens. I assume that it is some kind of drivers that I need to install but it is so slow that I can't do that. Any advice? I have a new laptop with ample disk space and ram as well as an i7 so I know its not my laptop. I am dual booting with windows 10 and windows 10 works perfectly fine
Thanks

---

### Post by RobGoss on 2017-04-22
Hello and welcome to the forum, It's hard to say what might be the problem not knowing what specs you have, care to share that information with us.

---

### Post by Doug S on 2017-04-22
> **RobGoss said:**
> Hello and welcome to the forum, It's hard to say what might be the problem not know what specs you have, care to share that information with us.+1. we need more information about your computer brand, specific i7 model number and such.

Meanwhile what do you get for:```
grep MHz /proc/cpuinfo
```

---

### Post by Bucky Ball on 2017-04-22
OP says tons of disk space and RAM and an i7. Non-specific but enough to go on. 

@OP: Welcome. Please confirm how much RAM you have and, yes, as mentioned, whether this is Ubuntu solo or you are dual-booting with another OS. Also, did you upgrade this from 16.10 via the internet? Was there anything on the partition you installed to via to installing? 

Have you tried installing the correct driver for your video card? Update the machine via a terminal or with Software Updater then check in Additional Drivers. Do you see a driver there for your card? You need to know what GPU you're using, of course. Whether you do or don't, and if you can manage to open a terminal, please post the output of this command.

```
sudo lshw -C video 
```

On the screen saying 'Internal Error', you should be able to get to the details of that error. Post here. On the other hand, it could just be the apport bug which gives error messages when you have no errors and can safely ignore.

When you boot, you are actually getting to a desktop? If so, and you can get to a terminal, update the machine. May help and give more clues.

```
sudo apt update
sudo apt full-upgrade
```

---

### Post by claudius-ellsel on 2017-04-28
Edit: Nevermind. Sorry, did not read carefully enough.

---

### Post by simon332 on 2017-04-29
I have an app running Java that uses nearly all the CPU. Didn't happen on 16.10. I guess I was a bit trigger happy and I'm looking for downgrade instructions now.

Doesn't use any more memory or anything. Earlier versions of Ubuntu (like about 14.04) used to leak memory in Java but it seems this is CPU related, not memory.

I have two PC both with dual boot. One is a ten year old macbook with lubuntu 17.04 32 bit, 3gb ram and the lxde desktop. Other is a similar age desktop (Compaq Presario 5085AN) with ubuntu 17.04 64 bit, 4gb ram and in both cases the upgrade from 16.10 to 17.04 has been a major downgrade.

Hope that's a bit more helpful. Non java apps seem fine so far.

---

### Post by LastDino on 2017-04-29
> **simon332 said:**
> I have an app running Java that uses nearly all the CPU. Didn't happen on 16.10. I guess I was a bit trigger happy and I'm looking for downgrade instructions now.

Doesn't use any more memory or anything. Earlier versions of Ubuntu (like about 14.04) used to leak memory in Java but it seems this is CPU related, not memory.

I have two PC both with dual boot. One is a ten year old macbook with lubuntu 17.04 32 bit, 3gb ram and the lxde desktop. Other is a similar age desktop (Compaq Presario 5085AN) with ubuntu 17.04 64 bit, 4gb ram and in both cases the upgrade from 16.10 to 17.04 has been a major downgrade.

Hope that's a bit more helpful. Non java apps seem fine so far.

I'm bit confused here, but shouldn't you make different thread for your problem? 

Especially since we follow one thread one problem per person.

---

### Post by simon332 on 2017-04-29
> **LastDino said:**
> I'm bit confused here, but shouldn't you make different thread for your problem? 
I'm assuming it's the same problem.

---

### Post by LastDino on 2017-04-29
> **simon332 said:**
> I'm assuming it's the same problem.

No can do brother, not allowed to hijack other peoples thread even if problem seems the same. Make different one, if someone responding finds it to be same, they will help both of you in your respective threads.

Cheers!

---

### Post by Bucky Ball on 2017-04-29
> **LastDino said:**
> I'm bit confused here, but shouldn't you make different thread for your problem? 

^^^
This. 

Hijacking threads not allowed here. Confusing and unfair to original poster. Similar is not same and your hardware specs would almost certainly not be the same, among other things.

This is the original poster's problem and circumstances.

> To install I have to use the options nomodeset, EDD = on, and nolapic. After I installation though ubuntu runs ridiculously slow. Like so slow I can't get the mouse even to a button. There is a screen up that says Ubuntu 17.04 has experienced an internal error.

Your issue.

> I have an app running Java that uses nearly all the CPU.

Not sure how these two are in any way related.

---

### Post by simon332 on 2017-04-29
Ok, I'll start a new thread.

---

### Post by simon332 on 2017-05-08
To the OP: Can you try running with a 4.8 kernel? It seemed to resolve my issues.

---

