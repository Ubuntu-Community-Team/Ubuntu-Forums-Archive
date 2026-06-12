---
title: "Automatically Re-installing Packages when upgrading to 64 bit"
date: 2013-08-16
forum: Installation &amp; Upgrades
---

### Post by Deb_Vorndran on 2013-08-16
Hi,

I recently installed Ubuntu 32 bit on my Sony Vaio touchscreen laptop.  (The ASSIST hardware key was vital to successful dual-boot installation.)
 Then I discovered that I accidentally installed the 32 bit version, instead of the 64bit.  

So I have to do a clean install.

In the meantime, I've installed and configured a bunch of packages, and I'd like to not have to figure all of that out all over again.

Is there a way to get a list of all of my installed packages, to make this new clean install as painless as possible?

To make it more complicated, I've often had to use different package managers.  Sometimes I use the ubuntu marketplace tool, sometimes it's apt-get, sometimes it's node-js's npm, sometimes it's a tarball, etc.

Looking on advice to make this upgrade as clean and simple as possible.

Thx!
:-D

---

### Post by MG&amp;TL on 2013-08-16
What I would do is make a copy of the configuration files you have configured, then make a note of all the packages you have installed. Some package managers can do this for you: for instance, see the output of:

```
dpkg -l | awk '{print $2}'
```

This will list all packages manually installed or required from *apt-get* or the Software Centre. I'm afraid I have no idea about the *node.js* package manager, and there is definitely no option to do this for tarballs.

Once that is achieved, make sure you have your configuration file copies and the notes about the packages, then backup and reinstall. As soon as you have reinstalled, reinstall the packages, then copy the configuration files back to their rightful places.

I can't see a way to make it less painful, sorry. Is there a good reason why you need 64-bit?

---

### Post by Frogs Hair on 2013-08-16
See the link , I have not  used this method because I know from repetition what I will install on a new version of Ubuntu . ;)  
[http://www.webupd8.org/2010/03/2-ways-of-reinstalling-all-of-your.html](http://www.webupd8.org/2010/03/2-ways-of-reinstalling-all-of-your.html)

---

### Post by Deb_Vorndran on 2013-08-16
Thanks, I'll use that command.  Luckily, all of the tarballs are still in my Downloads directory, so that won't be too bad.

So, you would keep it on 32 bit, and NOT upgrade to 64 bit?
I guess I don't really know the pros/cons of 32/64 bit, 

I just got this laptop, and I want to be happy with it for at least the next year or so, and it seemed to me that 64 bit was the better choice.
Guess I'll have to research that a bit more too, unless you've got some quick advice.

Thx,
:-D

---

### Post by MG&amp;TL on 2013-08-17
> **Deb_Vorndran said:**
> 
So, you would keep it on 32 bit, and NOT upgrade to 64 bit?
I guess I don't really know the pros/cons of 32/64 bit, 


Well, it depends how much RAM it has. 32-bit operating systems can only support up to a maximum of around 4GB. 64-bit operating do not have this limitation, so you can use all the memory. As far as I know, there is little to no performance difference between the two.

I only have 4GB of actual, physical RAM in the machine I'm currently typing on, and I don't recall ever running out of memory. It depends on what you do with your machine, I suppose.

---

### Post by Mark Phelps on 2013-08-17
I can confirm from my own testing, that using a fairly modern multi-core processor and 4GB of memory, there is no discernable performance improvement between 32-bit and 64-bit.  I determined this by installing BOTH versions on my PC and running benchmarks on each version.

Once you go beyond 4GB, you DO get performance improvements -- that you won't see with 32-bit because of its memory limits.

But even then, it's not anything impressive.

---

