---
title: "Should I install 64 bit version"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by stchman on 2007-12-11
Hello all, 

I know this has been talked about before but here goes.

I was toying with the idea of installing Ubuntu 64 bit on my PC.  I have been happily running the 32 bit version of Feisty for quite some time, but have always wanted to take advantage of the 64 bit power of my Athlon 64.

I did some reading and it looks like the 64 bit has only a minimal performance increase in some apps while slower in other apps.  Not to mention the PITA of getting some software to play nice in the 64 bit realm.

My question is it worth the hassle and headache to run 64 bit Ubuntu?  Should I wait?

I don't want to run it just to say I do if it is going to make me miserable.

Let me know what everybody thinks.

---

### Post by rsambuca on 2007-12-11
Basically, there is no PITA, so you may as well.  As far as slower?  Perhaps between 2 and 3 percent in some poorly compiled apps, but the number of those apps is few.  30%+ gains in other apps.  

Anyways, this is getting stale.  From your post count you obviously know about the 64bit forum.  The stickies there cover this and many other topics.  I suggest you read them.

---

### Post by Sef on 2007-12-12
> My question is it worth the hassle and headache to run 64 bit Ubuntu? Should I wait?

The biggest problem software to install still is Flash.  It is possible, but a bit of a pain.

---

### Post by PmDematagoda on 2007-12-12
> **Sef said:**
> The biggest problem software to install still is Flash.  It is possible, but a bit of a pain.

This is partly true Sef, with the fact that Ubuntu 7.10 x64 makes this task more reliable and easier, I don't think it would be as much of a pain as it would be in Ubuntu 7.04.

---

### Post by rsambuca on 2007-12-12
> **Sef said:**
> The biggest problem software to install still is Flash.  It is possible, but a bit of a pain.

Where are you getting this from?  This statement is simply incorrect. All you have to do to install flash is:

sudo apt-get install flashplugin-nonfree

How can you call that a problem, or a pain?????

---

### Post by helliewm on 2007-12-12
There are no major issues with 64bit whatsoever. It runs effortlessly for me on my desktop and 2 laptops.

Helen

---

### Post by helix_r on 2007-12-12
W.O.M.M. ("works on my machine") is better than nothing and it sure gives us warm and fuzzy feelings, but it does not really answer the OP's question.

Are there other issues with the 64 bit version of the distro besides flash? I think so, but I can't prove it because it is often very hard to decouple problems with the installation of particular apps and whether or not these problems are caused by the 64 bit distro. Last weekend I tried to get the latest netbeans working but could not, nor could I get frostwire to run. As for flash, even though "it works", I have problems with the crashing of firefox on occasion-- not enough to ditch the distro but enough that it makes me wonder.

Maybe a better approach would be for the OP to describe his most critical applications and then see if people are having problems with those particular apps in 64bit.

---

### Post by Heliologue on 2007-12-12
> **rsambuca said:**
> Where are you getting this from?  This statement is simply incorrect. All you have to do to install flash is:

sudo apt-get install flashplugin-nonfree

How can you call that a problem, or a pain?????

Is nspluginwrapper a dependency of flashplugin-nonfree on x64 systems?  If not, then it's one more package you'd have to install.  But other than that, it's easy.

The only other gotchas I've run into on a x64 system that there are still a very few packages, including some emulators, that don't have 64-bit versions.

---

### Post by rsambuca on 2007-12-12
> **helix_r said:**
> W.O.M.M. ("works on my machine") is better than nothing and it sure gives us warm and fuzzy feelings, but it does not really answer the OP's question.

Are there other issues with the 64 bit version of the distro besides flash? I think so, but I can't prove it because it is often very hard to decouple problems with the installation of particular apps and whether or not these problems are caused by the 64 bit distro. Last weekend I tried to get the latest netbeans working but could not, nor could I get frostwire to run. As for flash, even though "it works", I have problems with the crashing of firefox on occasion-- not enough to ditch the distro but enough that it makes me wonder.

Maybe a better approach would be for the OP to describe his most critical applications and then see if people are having problems with those particular apps in 64bit.

For frostwire, you need to install ia32 version of java:

```
sudo apt-get install ia32-sun-java6-bin
```Then switch to it:
```
sudo update-alternatives --config java
```Frostwire will then run perfectly.

---

### Post by rsambuca on 2007-12-12
> **Heliologue said:**
> Is nspluginwrapper a dependency of flashplugin-nonfree on x64 systems?  If not, then it's one more package you'd have to install.  But other than that, it's easy.


It is all done automatically for you.

Even easier, just go to a website that requires flash and you will be prompted to install it.  Just click OK.

I think a lot of the people here should actually *try* the 64bit version before giving advice as to its "problems".

---

### Post by helix_r on 2007-12-12
> **rsambuca said:**
> For frostwire, you need to install ia32 version of java:

```
sudo apt-get install ia32-sun-java6-bin
```Then switch to it:
```
sudo update-alternatives --config java
```Frostwire will then run perfectly.

Thanks, that's great. It is better than the help on frostwire's website. I appreciate that.

However, didn't that just make "java" now refer to the 32bit JRE? What if there are other things that you want to continue to use with the 64 bit sun-java6-jre?

---

### Post by rsambuca on 2007-12-12
To be honest, I have no idea.  I think frostwire is the only java app I use at the moment.

---

### Post by starryeyedboy on 2007-12-15
hi there guys.

i'm new to linux, and this is my first time using it. i'm running on an intel core 2 duo, so i've been using the x86_64 gutsy and drivers etc from the start.

one issue i had with flash is - there is a new version of flash - and when u actually try to install flash with:
sudo apt-get install flashplugin-nonfree

it doesn't actually install (look at "details" when it finishes.) this thread explains why:
[https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890](https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890)

anyway, it also explains how to fix it. i recommend installing this package:
[http://launchpadlibrarian.net/10804892/flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb](http://launchpadlibrarian.net/10804892/flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb)

works perfectly well, and so easy to do too. 

cheers.

---

