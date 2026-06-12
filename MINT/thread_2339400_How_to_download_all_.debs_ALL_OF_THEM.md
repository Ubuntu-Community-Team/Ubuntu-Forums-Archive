---
title: "How to download all .debs ALL OF THEM"
date: 2016-10-08
forum: MINT
---

### Post by mintmag on 2016-10-08
Hi there I wish to download every single package from the archive. I used used apt-get download "*" which crabs most things but a few still slip through. one of them was libnss-mdns:i386 why was this noy included is the list of files?

Furthermore I am fully aware of the size of such downloads I am trying to create a repository/

---

### Post by PaulW2U on 2016-10-08
> **mintmag said:**
> Furthermore I am fully aware of the size of such downloads I am trying to create a repository/
I'm not sure you are trying to accomplish what you wish to do in the correct way as there is an **apt-mirror** command that I think you should be using.

The answer, although very old now, may be on these very forums - [HOWTO: Setup Local Repository Mirror]("https://ubuntuforums.org/showthread.php?t=599479"). It might be best to also search the web for a solution that has been written more recently.

---

### Post by mintmag on 2016-10-08
> **PaulW2U said:**
> I'm not sure you are trying to accomplish what you wish to do in the correct way as there is an **apt-mirror** command that I think you should be using.

The answer, although very old now, may be on these very forums - [HOWTO: Setup Local Repository Mirror]("https://ubuntuforums.org/showthread.php?t=599479"). It might be best to also search the web for a solution that has been written more recently.


Apt-mirror doesn't work for me. Download "*" mostly does I just want to know why it doesn't grab packages like libnss-mdns:i386 Why can't libnss-mdns:i386 be installed with apt-get install. Crossover needs it.

---

### Post by ian-weisser on 2016-10-08
> **mintmag said:**
> Why can't libnss-mdns:i386 be installed with apt-get install.
Using apt to install libnss-mdns works fine here.

---

### Post by mintmag on 2016-10-08
> **ian-weisser said:**
> Using apt to install libnss-mdns works fine here.

What version of Ubuntu are you using?

---

### Post by ian-weisser on 2016-10-08
One of my Ubuntu 16.04 test systems.

---

### Post by mintmag on 2016-10-08
> **ian-weisser said:**
> One of my Ubuntu 16.04 test systems.


It seems that this packages wasn't included with apt-get download "*" any idea why. I can't seem to find it with apt-cache either.

---

### Post by vasa1 on 2016-10-09
Is your OS 64-bit?

---

### Post by mintmag on 2016-10-09
Oh yes and it turns out that you can download it with apt-get install. But for some reason download "*" doesn't grab everything.

So after re downloading all .deb files I've noticed that it's downloaded a lot more amd64 files then i386. Anyway know why this is the results of the downloads can be found here.   [https://drive.google.com/file/d/0B5PLItq4rD2jTGlkdXRKNXQwekU/view?usp=sharing](https://drive.google.com/file/d/0B5PLItq4rD2jTGlkdXRKNXQwekU/view?usp=sharing)

---

### Post by ian-weisser on 2016-10-09
> **mintmag said:**
> It seems that this packages wasn't included with apt-get download "*" any idea why. I can't seem to find it with apt-cache either.
Look at it the other way around.
A package needs to be in your package database (apt-cache) for apt to be aware of it. Apt cannot download packages that it is unaware of.

If libnss-mdns is not in your package database, then your sources are likely incomplete.
These are the Ubuntu sources with that package:

```
$ rmadison libnss-mdns libnss-mdns | 0.10-3.2 | precise | amd64, armel, armhf, i386, powerpc
 libnss-mdns | 0.10-6   | trusty  | amd64, arm64, armhf, i386, powerpc, ppc64el
 libnss-mdns | 0.10-6   | vivid   | amd64, arm64, armhf, i386, powerpc, ppc64el
 libnss-mdns | 0.10-6   | wily    | amd64, arm64, armhf, i386, powerpc, ppc64el
 libnss-mdns | 0.10-7   | xenial  | amd64, arm64, armhf, i386, powerpc, ppc64el, s390x
 libnss-mdns | 0.10-7   | yakkety | amd64, arm64, armhf, i386, powerpc, ppc64el, s390x
```

---

### Post by mintmag on 2016-10-09
Yeah it's not in the cache because apt-cache search didn't show it even though apt-get get install is still able to grab it. So why would not be in there. I'm looking at your code but I don't quite understand it. libnss-mdns:i386 isn't the only package I want to get. I want to download all packages that can be download from the repo. A total mirror in other words. But I don't want to use apt-mirror because I just couldn't get it to work. download "*" works but doesn't seem to grab everything.

---

### Post by ian-weisser on 2016-10-09
Apt is not really designed for that purpose, so I'm not terribly surprised you are having problems like these.
I'm not sure I understand why you need a full mirror instead of, say, a caching proxy...but that doesn't seem relevant. You want to make a mirror without using apt-mirror.
Were that my challenge, I would script the mirroring using wget's ability to spider specific dirs.
Did you figure out how to index the mirror so it's useful to apt?

---

### Post by HermanAB on 2016-10-09
Well, as said above, apt-mirror is the correct tool to use.  Scroll down to 'Private Ubuntu Mirror' for details:
[http://www.aeronetworks.ca/2016/02/mirror-mirror-on-wall.html](http://www.aeronetworks.ca/2016/02/mirror-mirror-on-wall.html)

If apt-mirror doesn't work, then you should fix the problem since then other issues that you may have will likely be resolved too.

---

### Post by mintmag on 2016-10-09
> **ian-weisser said:**
> Apt is not really designed for that purpose, so I'm not terribly surprised you are having problems like these.
I'm not sure I understand why you need a full mirror instead of, say, a caching proxy...but that doesn't seem relevant. You want to make a mirror without using apt-mirror.
Were that my challenge, I would script the mirroring using wget's ability to spider specific dirs.
Did you figure out how to index the mirror so it's useful to apt?


Okay I found the problem but I still need the solution. When you compare these two you can see exactly whats going on. 

apt-get download "*"  (Linux Mint 32bit) [https://drive.google.com/open?id=0B5PLItq4rD2jdGxSeGk1QzFsRjQ](https://drive.google.com/open?id=0B5PLItq4rD2jdGxSeGk1QzFsRjQ) 
apt-get download "*" (Linux Mint 64bit) [https://drive.google.com/open?id=0B5PLItq4rD2jTGlkdXRKNXQwekU](https://drive.google.com/open?id=0B5PLItq4rD2jTGlkdXRKNXQwekU)



It's not downloading all the i386 packages even though the architecture was added. Linux mint is multi arch by default. I need to find a way to add both all amd64 and i368 to apt so that download "*" can grab them

 I am 100% sure that will fix the problem. As for the index yes I have been able to get it to work. That's why I'm using this instead of apt-mirror. I could not get apt-mirror it to index properly. I'm not sure if it's simply incompatible or if I just can't figure it out. Either way I have no further interest in using apt-mirror when that has actually worked. Doing this on a 32bit system works 100% perfectly. But doing in a amd64 even with both architectures enabled is proving tricky.

---

### Post by deadflowr on 2016-10-10
This is on mint?

---

### Post by mintmag on 2016-10-10
Guys I think I solved the problem apt-get download '*':i386 that seems to do it

> **deadflowr said:**
> This is on mint?

Yes the Mint forums are kind of empty

---

### Post by QIII on 2016-10-10
Moved to MINT.

Having specified that this was Mint might have kept people from suggesting things that did not work for you.  Mint's repos might be arranged quite differently.

---

### Post by mintmag on 2016-10-10
Mint's repos are almost exactly the same and I solved it.

---

### Post by deadflowr on 2016-10-10
> **mintmag said:**
> Mint's repos are almost exactly the same and I solved it.

They aren't.
Mint is setup to access and use Ubuntu's repos, but that is on top of Mint's own repos, which adds a layer of complexity that Ubuntu does not have.

Moot point if this is solved, though.
Please mark this thread as Solved if it is, please.

Or maybe even post about how you came to a solution.

---

### Post by mintmag on 2016-10-10
Sure I will, can you tell me how to mark as solved. I'm not 100% sure and I'll also test the repo with Ubuntu just to see if it works.

Okay to download all packages from a repository cd into the directory you want to download them into and type  ```
 apt-get download '*' 
``` 

For 64bit versions you will also need to type
```
 apt-get download '*':i386 
``` 

This will download the 32bit packages which are often skipped with '*'

This will take a while to download so do keep that in mind. Also use caution when browsing the directory, having over a 100 gigabytes worth of .deb files in one folder can cause stability issues if you're not careful.

---

### Post by deadflowr on 2016-10-10
> **mintmag said:**
> Sure I will, can you tell me how to mark as solved. I'm not 100% sure and I'll also test the repo with Ubuntu just to see if it works.

You already marked as solved, it seems.
I guess magic is real sometimes.

[s]It would be good to see what differs between Mint and Ubuntu is this particular method.
Whatever the particular method used happened to be...[/s]

I see you posted the answer while I was typing.

---

