---
title: "[Solved] Dependency hell in fresh install of 16.04"
date: 2016-04-19
forum: Installation &amp; Upgrades
---

### Post by rbfx4x on 2016-04-19
Is there something I can do or just wait a few days until final release?  
Some packages install no problems. Others like vlc, skype, nvidia drivers etc... refuse. 
An example below.... 

jafar@malygos:~$ sudo apt install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 vlc : Depends: libgles1-mesa (>= 7.8.1) but it is not going to be installed or
                libgles1
       Depends: libgles2-mesa (>= 7.8.1) but it is not going to be installed or
                libgles2
E: Unable to correct problems, you have held broken packages.

---

### Post by mc4man on 2016-04-19
If a fresh install did you go sudo apt update first?

---

### Post by rbfx4x on 2016-04-19
Yes of course

---

### Post by grahammechanical on 2016-04-19
Both libgles1-mesa & libgles2-mesa are in the xenial repositories (but not installed by default) and they are at version 11.2. In fact the oldest version of these libraries is version 8.0 and that with Ubuntu 12.04. So, even 12.04 meets the dependency requirement of greater than or equal to version 7.8

So, the question is this: Is the Universe repository enabled? Software & Updates>Community maintained free & open source software (universe). I doubt if this is the cause of the problem. It is the best that I offer.

Of course, it is not relevant to any problem installing Nvidia drivers. Are you using Additional Drivers to do that? As for Skype, well I think that is an entirely different matter.

Regards

---

### Post by rbfx4x on 2016-04-19
> **grahammechanical said:**
> So, the question is this: Is the Universe repository enabled? Software & Updates>Community maintained free & open source software (universe). I doubt if this is the cause of the problem. It is the best that I offer.

Yes, all repositories are enabled. I managed to install other things like conky, vim, htop etc...

> **grahammechanical said:**
> Of course, it is not relevant to any problem installing Nvidia drivers. Are you using Additional Drivers to do that? As for Skype, well I think that is an entirely different matter.

Regards

Additional Drivers failed and sticks to Nouveau. Command line results in ...
```

jafar@malygos:~$ sudo apt install nvidia-361-updates
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 nvidia-361-updates : Depends: lib32gcc1 but it is not going to be installed
                      Depends: libc6-i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Maybe I should just install again after re-downloading the ISO. I think the one I have is corrupt.

---

### Post by rbfx4x on 2016-04-20
I just reinstalled from an ISO from a few days ago that I know works. 
All good now. It may have just been some corruption. Sorry for making you guys worry about new bugs in 16.04 :)

---

### Post by lisati on 2016-04-20
If you have solved your problem, please mark the thread "Solved" from the "Thread Tools" menu above the first post.

---

