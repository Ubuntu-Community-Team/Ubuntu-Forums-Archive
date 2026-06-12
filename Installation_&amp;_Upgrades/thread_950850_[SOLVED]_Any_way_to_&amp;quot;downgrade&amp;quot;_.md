---
title: "[SOLVED] Any way to &amp;quot;downgrade&amp;quot; to 32-bit ubuntu?"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by CJ Master on 2008-10-17
Hai.

Basically: I want 32 bit ubuntu, not the current 64-bit it's running. First off, practically nothing wants to run on it. Second off, that includes java, which I really need.

Before finally going to 64-bit ubuntu, i tried to install 32bit but I kept getting an error... something like "error fd0 in logical block something".

Is it just not possible to run 32bit ubuntu on a 64bit machine?

---

### Post by Therion on 2008-10-17
In order to truly downgrade from 64-bit to 32-bit you'd need to reinstall from the ground up.

Since you already have 64-bit installed though, why don't you tell me what it is that's not running for you.  I've been running on a 64-bit distro for ages and I've never had any real problem.

Have you installed **ubuntu-restricted-extras** from Synaptic yet?  That might solve some of your problems.

Post back though, and let me know specifically what issues you're having.  Unless of course you're determined to revert back to 32-bit; in which case you'll just need to reinstall.

---

### Post by CJ Master on 2008-10-17
Hey,

Well generally whats not running for me are a lot of programs on Add/Remove Programs, whenever I click on some it says its not avalible for AMD64.

I just installed it, but java still doesn't work. Do I need to restart or something?

---

### Post by Therion on 2008-10-17
Okay I'm a little confused because when you go to the Add/Remove Programs section, you're only being shown applications available in the repos.  You don't HAVE to have a 64-bit compile to run on a 64-bit distro, it's backwards compatible with 32-bit releases.

Give me a specific example of something you can't install from Add/Remove.  Anything.  Just give me the name of an application that won't install for you from Add/Remove.

As for installing Java, use cut and paste with the following line of code:```
sudo apt-get install openjdk-6-jre
```Now open and Terminal and "paste" that information in and press return. Enter your password and then approve the license agreement to install Java.

---

### Post by CJ Master on 2008-10-17
Here's one, "Sun Java 6.0 Plugin"

Oh thanks, I'll give that a try once update manager is finished.

---

### Post by CJ Master on 2008-10-17
It doesn't seem to think it needs to be installed, it shows i already have it.

---

### Post by steveneddy on 2008-10-17
A total reinstall will be in order to get 32 bits instead of 64 bits.

---

### Post by Therion on 2008-10-17
> **CJ Master said:**
> It doesn't seem to think it needs to be installed, it shows i already have it.What is?

Did you use the command line I gave you and if so did Java install?

Java is one thing you do need a 64-bit release for.

---

### Post by CJ Master on 2008-10-17
Yea, it thinks I already have it... here I'll what it says here.

```
cjmaster@cjmaster-desktop:~$ sudo apt-get install openjdk-6-jre
[sudo] password for cjmaster: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openjdk-6-jre is already the newest version.
The following packages were automatically installed and are no longer required:
  icedtea6-plugin
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
cjmaster@cjmaster-desktop:~$ 

```

---

### Post by Therion on 2008-10-17
Okay, so... Java is installed.  Is it not working?

---

### Post by CJ Master on 2008-10-17
Nope. Went to two sites that I KNEW used java... it is compatible with FF3 right?

---

### Post by CJ Master on 2008-10-18
Well I'm off for the night, lemme know if you find some way to get java working and to run those other pesky apps!

---

### Post by steveneddy on 2008-10-18
Try [this thread]("http://ubuntuforums.org/showpost.php?p=4782823&postcount=1") and some of the links in my sig.

That should get you going.

I've been using 64 bit Ubuntu since Feisty, so I know it works OK.

Try lurking around on the 64 bit users forums for more tips and how to's.

---

### Post by CJ Master on 2008-10-20
Ah good, icedtea works now (although admitidly painfully slow and lots of sound problems)

...But still, how can I get the games/upgrades that are greyed out?

---

### Post by CJ Master on 2008-10-22
I will now add a post intending to bump but disguising itself as a legidamant post. -----no you didn't hear that. Carry on. Shoo, shoo!

...Lol. =] anyways why is it greyed out in the first place? I thought 64-bit computing was supposed to be completely backwards compatable?

And if I do choose to downgrade, does that mean there will be other ubuntu programs I wont be able to access? If so, are they important/numerous?

---

