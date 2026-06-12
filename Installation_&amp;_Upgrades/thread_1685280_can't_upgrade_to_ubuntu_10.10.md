---
title: "can't upgrade to ubuntu 10.10"
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by True_Snake on 2011-02-10
I've tried some different way's to upgrade my 10.04 to 10.10
but I get the same problem all the time, it starts ok but when he 
starts to calculate changes he quits and claims there is a problem with my apt dependencies
I already checked my apt to look for broken packages or anything but I don't find any problem there.
Could this be caused because I'm still running amarok14 which I compiled manually or does this have nothing to do with it.
Anyway I hope someone can help me out with this and if you need some more info just ask.

all help greatly appreciated
I'm still kinda noob in linux

---

### Post by zvacet on 2011-02-10
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by True_Snake on 2011-02-10
you got a good point but that is not the problem,
my apt is perfectly up to date I've done these commands before doing the release upgrade.
And I checked again a minute ago :)
I also tried in different ways; in my terminal by command "sudo do-release-upgrade", with my update manager and by downloading ubuntu 10.10 and try to upgrade offline by cd.
Nothing works
I get the same problem every time again:


Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

thx for the advice thought but my problem is the release upgrade to maverick 10.10

---

### Post by True_Snake on 2011-02-11
update of the situation I've being trying some other things
and by this destroyed my complete install, like I said still a noob:)
But since I had to reinstall I directly installed Ubuntu 10.10
and so is this thread actually solved.

---

### Post by jack_123 on 2011-02-11
I have exactly the same problem! I dont know what to do. I dont want to go through the hassle of doing the install again.

---

### Post by eb0b on 2011-03-03
Same issue here has anything else been brought up about this?

---

### Post by swapnilnarendra on 2011-03-03
I am using Ubuntu Netbook Remix 10.10 (or rather I shud say I was using 10.10). For a past few days I was getting the same kind of error while upgrading and when I finished the upgrade, it killed my computer. 

I re-installed 10.04 again and tried to upgrade and to my surprise it gave me the same error again. So I am downloading the 10.10 now and as soon as it is downloaded I am going to re-install it one more time.

Is it an issue with the upgrade or what ?

Here is the link for the thread which I started:
[http://ubuntuforums.org/showthread.php?p=10513323#post10513323](http://ubuntuforums.org/showthread.php?p=10513323#post10513323)

---

