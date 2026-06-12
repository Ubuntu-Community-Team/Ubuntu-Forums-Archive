---
title: "help installing 32-bit packages on 64-bit machine ubuntu 17.04"
date: 2017-09-20
forum: Installation &amp; Upgrades
---

### Post by liewjls on 2017-09-20
Hi,

I have currently using ubuntu 17.04 and I bit stuck getting 32-bit packages to build some libraries such as vlc-qt. Things have been change and i'm still wondering what has gone wrong. :( 
Previously when i was using ubunt 16.04, I could easily install 32-bit packages by adding ":i386" at the end of the packages. But now I can't retrieve any of it. For example:

```
~# apt install qtbase5-dev:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 qtbase5-dev:i386 : Depends: libgles2-mesa-dev:i386 but it is not going to be installed or
                             libgles2-dev:i386 but it is not installable
E: Unable to correct problems, you have held broken packages.
```


Any help please? Otherwise i'll rollback to 16.04 


Thanks.

---

### Post by kc1di on 2017-09-20
Hi liewjls  and Welcome to Ubuntu Forums,

Ubuntu is moving away for 32 bit builds and the older programs may not have been built for 32 bit processors in the newer repositories. 
if you can get the libraries you need from other sources it may still be possible to build the 32 bit programs you want. But this may degrade the 17.04 install and cause security issues. why do you need the 32 bit build?  is there not a 64 bit equivalent?

---

### Post by liewjls on 2017-09-20
Thanks kc1di,

The reason i need the 32-build is because there are 40% of the product is still running 32 bits hardware. They are really old project and we still need to support them, it's a pain. Is there any equivalent for 64 bits? I doubt i can build and compile 64-bit but run it on 32bit device?

thanks.

---

### Post by mastablasta on 2017-09-22
what if you used 32bit OS to compile it? or 16.04?

---

### Post by ian-weisser on 2017-09-22
> **liewjls said:**
> 
```
The following packages have unmet dependencies.
 qtbase5-dev:i386 : Depends: libgles2-mesa-dev:i386 but it is not going to be installed or
                             libgles2-dev:i386 but it is not installable
E: Unable to correct problems, you have held broken packages.
```

That looks like a plain old version conflict, not an architecture conflict.

---

### Post by liewjls on 2017-09-28
Need to use 32bit OS.

thanks

---

### Post by liewjls on 2017-09-28
yeah. But sadly 17.04 doesn't support 32 bits library eh?

---

### Post by ubfan1 on 2017-09-29
Please post the output of:     apt-cache policy libgles2-mesa:i386    The 17.04 release seems to have the same support for 32 as previous releases. Did you ever run  sudo apt-get update  to get the current repositories updated?

---

