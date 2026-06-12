---
title: "Can we finally solve &quot;errno 5 errors&quot; during ..buntu installs???"
date: 2012-11-07
forum: Installation &amp; Upgrades
---

### Post by davidafranklin on 2012-11-07
Hello,

There are many people complaining of always the same error message when trying to install a **...buntu based Linux distro.** 

I have the same issue, I tried to install from scrach lubuntu 12.10, Zorin 6, Ubuntu 12.10, Mint Cinnamon, from both USB and DVD, trying both  to first run the live then install and install directly, both using the entire drive or only part of it, both using regular install or alternate.

**IT IS ALWAYS THE SAME ERROR MESSAGE**. It seems that many many people trying to help do not understand what the problem as the recommendations never seem to work.

Has anybody finally found what the issue is so we **can have a fix that works every time for everybody?** 

Thanks
David

---

### Post by davidafranklin on 2012-11-07
After lots of frustrations and trials, I tried a non ..buntu distro (Fedora 17), it worked perfectly (install via USB).

Until a fix is found, this is a solution...

---

### Post by ibjsb4 on 2012-11-07
If you have found a solution please mark your thread solved.

---

### Post by davidafranklin on 2012-11-08
the problem is not fixed,
it is just a temp solution to run Linux in the meantime.

---

### Post by darkod on 2012-11-08
It sounds more hardware related. Look here for example:
[http://superuser.com/questions/465136/error-number-5-input-output-error-while-installing-linux](http://superuser.com/questions/465136/error-number-5-input-output-error-while-installing-linux)

At the end, it turned out a faulty BIOS.

Not all linux distros "talk" to the hardware in the same way, so the results might be different. Fedora for example is not debian based. You can try that --no-migration-assistant option mentined in one of the answers, if you want to see if it helps you install ubuntu.

---

### Post by davidafranklin on 2012-11-08
i tried "ubiquity --no-migration-assistant", did not work or me. Looking for Bios updates will make it too much work for the average linux user so people will tend to go to other distros. What we need is to find a way to install it like Fedora for example.

---

### Post by darkod on 2012-11-08
Then simply use Fedora. You can't expect the software to solve your hardware issue, if this really is a hardware issue.

I guess you will have to stick with a software that tolerates it, especially if you don't want to get into troubleshooting too much.

---

### Post by davidafranklin on 2012-11-08
> **darkod said:**
> Then simply use Fedora. You can't expect the software to solve your hardware issue, if this really is a hardware issue.

I guess you will have to stick with a software that tolerates it, especially if you don't want to get into troubleshooting too much.

what does not make sense is that i used to have Lubuntu 12.04 and was even ale to have lubuntu 12.10 in that machine. I tried another distro (buntu based) an this i when I started getting all these errors. now< i cannot even go back to lubuntu 12.10

---

