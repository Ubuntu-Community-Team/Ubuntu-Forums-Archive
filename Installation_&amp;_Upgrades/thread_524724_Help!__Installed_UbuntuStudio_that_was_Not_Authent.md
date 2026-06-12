---
title: "Help!  Installed UbuntuStudio that was Not Authenticated!"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by ratdog on 2007-08-13
I may have messed up on this one...
I followed the procedure outlined here: [http://doc.gwos.org/index.php/HowToIntegrateUbuntuStudio](http://doc.gwos.org/index.php/HowToIntegrateUbuntuStudio)
for installing ubuntu studio.  At some point in the install, I was warned that a package could not be authenticated, but accepted the risk installed anyway.  
So now Ubuntu's update function wont work as it tells me I have a broken package.
I looked in my Synaptic Package Manager and the ubuntustudio-audio package is the broken one.  When I check it for reinstallation it informs me the package can not be authenticated.  Should I go ahead and try anyway, I assume it will get me right back where I am.  
I ran apt-get update and these are the errors I got back:
---------------------------------------------
$ sudo apt-get update -qq
bzip2: (stdin) is not a bzip2 file.
W: GPG error: [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A361B38AB6A4EB33
W: You may want to run apt-get update to correct these problems
--------------------------------------------
I'm quite new to Ubuntu and don't know where to go from here...  Help!
The RatDog

ps:  I'm trying to set up my ubuntu for some open source music production and am having problems with apps sending out too high of an audio signal.  Check out this thread :   [http://ubuntuforums.org/showthread.php?t=519333](http://ubuntuforums.org/showthread.php?t=519333)

---

### Post by overdrank on 2007-08-15
> **ratdog said:**
> I may have messed up on this one...
I followed the procedure outlined here: [http://doc.gwos.org/index.php/HowToIntegrateUbuntuStudio](http://doc.gwos.org/index.php/HowToIntegrateUbuntuStudio)
for installing ubuntu studio.  At some point in the install, I was warned that a package could not be authenticated, but accepted the risk installed anyway.  
So now Ubuntu's update function wont work as it tells me I have a broken package.
I looked in my Synaptic Package Manager and the ubuntustudio-audio package is the broken one.  When I check it for reinstallation it informs me the package can not be authenticated.  Should I go ahead and try anyway, I assume it will get me right back where I am.  
I ran apt-get update and these are the errors I got back:
---------------------------------------------
$ sudo apt-get update -qq
bzip2: (stdin) is not a bzip2 file.
W: GPG error: [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A361B38AB6A4EB33
W: You may want to run apt-get update to correct these problems
--------------------------------------------
I'm quite new to Ubuntu and don't know where to go from here...  Help!
The RatDog

ps:  I'm trying to set up my ubuntu for some open source music production and am having problems with apps sending out too high of an audio signal.  Check out this thread :   [http://ubuntuforums.org/showthread.php?t=519333](http://ubuntuforums.org/showthread.php?t=519333)

HI if you have not solved your issue yet you can try to fix the broken packages in synaptic manager. Under edit you can choose fix broken package and the click the reload button. If this doesn't work then  under settings filter and search the broken packages there. Hope this helps and if not then post back here, and try to update through the terminal with 
```
sudo apt-get update
```
and post errors.

---

