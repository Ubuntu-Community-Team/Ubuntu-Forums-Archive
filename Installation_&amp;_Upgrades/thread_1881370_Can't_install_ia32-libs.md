---
title: "Can't install ia32-libs"
date: 2011-11-15
forum: Installation &amp; Upgrades
---

### Post by lkjoel on 2011-11-15
I'm trying to install ia32-libs, but it doesn't let me:
```
lkjoel@lkjoel-desktop:~/workspace/relinux$ sudo apt-get install ia32-libs 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch
E: Unable to correct problems, you have held broken packages
```
Some information about my system:
```
lkjoel@lkjoel-desktop:~/workspace/relinux$ uname -a
Linux lkjoel-desktop 3.1.0-2-generic #3-Ubuntu SMP Sat Oct 29 00:48:30 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
lkjoel@lkjoel-desktop:~/workspace/relinux$ lsb_release -a
LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu precise (development branch)
Release:	12.04
Codename:	precise
lkjoel@lkjoel-desktop:~/workspace/relinux$ 
```

---

### Post by BillyBoa on 2011-11-15
You have the same results installing it from Synaptic? From there you could resolve the broken packages issue.

---

### Post by lkjoel on 2011-11-15
Well, it's possible for me to install it, but it'll remove around 200-400 packages (that I use).

---

### Post by Frogs Hair on 2011-11-15
Hello lkjoel .

Since 12.04 is pre alpha you may want to have your thread to the link below . I would expect problems at this point in development . [http://ubuntuforums.org/forumdisplay.php?f=412](http://ubuntuforums.org/forumdisplay.php?f=412)

---

### Post by finderlite on 2012-04-29
```
sudo apt-get install librtmp0/precise
```
solved the problem.

---

### Post by KrisWillis on 2012-05-23
> **finderlite said:**
> ```
sudo apt-get install librtmp0/precise
```
solved the problem.

Having upgraded from 10.04 to 12.04, I also had this same problem, your solution also fixed it for me.

I don't understand why though. How does downgrading the RTMP toolkit fix the issue of missing ia32-libs?

If you don't mind me asking, how did you figure this out, or where did you read about it?

---

### Post by baijea on 2012-09-18
Hi,

the solution to a similar problem I had is listed in [http://ubuntuforums.org/showpost.php?p=12246372&postcount=7](http://ubuntuforums.org/showpost.php?p=12246372&postcount=7).

Hope this helps!

---

