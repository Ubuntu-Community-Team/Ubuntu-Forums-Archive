---
title: "Can't upgrade - Fails with broken dependencies"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by DougEdey on 2010-04-30
I've been trying all morning to update from a working 9.10 to 10.04 and unfortunately every time I try it blocks me.


An unresolvable problem occurred while calculating the upgrade: 
E:Unable to correct problems, you have held broken packages. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug against the 
'update-manager' package and include the files in 
/var/log/dist-upgrade/ in the bug report. 


Restoring original system state


I've uploaded the full apt log to pastebin here:

[http://pastebin.com/BaGyN3Bp](http://pastebin.com/BaGyN3Bp)

---

### Post by mac9416 on 2010-04-30
DougEdey,

Maybe you should report a bug? You can do that by running 'ubuntu-bug update-manager.' Don't forget to include any files in /var/log/dist-upgrade/.

---

### Post by xtracool_protik on 2010-05-01
Hey same here,
 I've same error. I tried few workarounds but nothing worked.
 Hope someone fixes it soon :)

---

### Post by e_liming on 2010-05-01
I've got the same error upgrading from Karmic. Anybody have a solution?

---

### Post by xtracool_protik on 2010-05-03
bump ](*,)
no one had the issue?

---

### Post by xtracool_protik on 2010-05-03
Hey mac9416, Thanks for the keryx :) I'm gonna put a link on a blog

---

### Post by mac9416 on 2010-05-03
> **xtracool_protik said:**
> Hey mac9416, Thanks for the keryx :) I'm gonna put a link on a blog

Cool, thanks very much!  :)

---

### Post by xtracool_protik on 2010-05-07
Hey guys,
 I happen to have 2 Ubuntu installations on my laptop. One to mess up and other to carry changes which were long term and good in first case.
 So I failed upgrading on my messy setup, however I could successfully upgrade for clean system.
 DougEdey did u get yours working. Here are some ideas about my system if anyone can give me pointers I'll like to work around:

 I've plenty of third party repositories and softwares installed (Suspicious one is : bleeding edge Video drivers with xorg - edgers)

 I wanted to follow [https://help.ubuntu.com/community/CleanUpgrade](https://help.ubuntu.com/community/CleanUpgrade)
 to get upgrade however removing xorg means no display (I'm not much of a terminal person but I'm ready to take a path if anyone have few guidelines)

 So if anyone can help me I would like to know safe way to remove third party softwares -- video specifically
 Or going back to drivers which are available in Ubuntu repository from edgers

 BTW was working on other Ubuntu in the morning and man I love the connectivity improvements would like to get my workspace ubuntu to 10.04

Thanks for any help
Regards

---

### Post by xtracool_protik on 2010-05-08
bump

---

### Post by xtracool_protik on 2010-05-20
hmm,
 I think I'll go ahead with clean upgrade. However I need few inputs. 
1. If I remove xorg can I install it back again (without any issue i.e.)
2. Can I export history of synaptic so to know what all packages I have to install back again?

Thanks
Regards
Pratik

---

### Post by Elfy on 2010-05-20
along the lines of "Can I export history of synaptic ..." [http://ubuntuforums.org/showpost.php?p=4020978&postcount=4](http://ubuntuforums.org/showpost.php?p=4020978&postcount=4)

Perhaps removing all the 3rd party repos and installing ubuntu-desktop will help.

Though to be honest I would likely just do a clean install on it after backing up anything I needed.

---

### Post by xtracool_protik on 2010-05-20
Hey forestpiskie,
 Thanks for quick response 
 The package selection didn't work for me last time as I had installed few of them through 3rd party repositories.
 And I'm just being lazy avoiding to go through setting up everything from scratch for new installation (not to mentions my cross compile toolchains though I just export paths)
 I'll give it a try just by deselecting all 3rd party repositories and report back in some time.

---

### Post by xtracool_protik on 2010-05-20
Just deselecting 3rd party repos didn't help :(
Anything else as a suggestion?

---

### Post by xtracool_protik on 2010-05-20
Hey forestpiskie
Just looked at irc channel for help. Good work :)

---

### Post by xtracool_protik on 2010-05-20
Here is something which worked for me
[http://ubuntuforums.org/showthread.php?t=1488156](http://ubuntuforums.org/showthread.php?t=1488156)

I'll put it up on my blog as well, upgrade is currently going on :D

---

### Post by bcschmerker on 2010-05-20
I had a different version of the same problem on my first attempt to upgrade from 8.04.4 (more failures to install than packages broken by version incompatibility), and my Everex was temporarily unusable.  However, my /home disc had ext3 intact and I was able to clean-install the rest of 10.04 from an AMD64 Install CD, using ext4 for all other required partitions on my system.  My Everex is running fast as it ever did on a 2.8 GHz core clock as a result.  I still have a few settings bugs to ID and squash hereon, of course, as many programs used in 8.04 have been replaced outright in 10.04; but that will be straightforward enough. ;-)

---

### Post by Elfy on 2010-05-20
> **xtracool_protik said:**
> Hey forestpiskie
Just looked at irc channel for help. Good work :)

I'm glad that the irc link worked for you - possibly I saw you in there in logs - I'm not forestpiskie in there though

Also glad you go there in the end :)

---

### Post by bcschmerker on 2010-08-26
> **bcschmerker said:**
> I had a different version of the same problem on my first attempt to upgrade from 8.04.4 (more failures to install than packages broken by version incompatibility), and my Everex was temporarily unusable.  However, my /home disc had ext3 intact and I was able to clean-install the rest of 10.04 from an AMD64 Install CD, using ext4 for all other required partitions on my system....Update:  I ended up having to reinstall 10.04 as the i386 Version due to an incompatibility between Adobe® Flash™ 10.1.53.64 (32-bit only) and Mozilla® Firefox® 3.6.3.  This time, I took the precaution of saving docs and .mozilla to a USB chip and going ext4 across all partitions; this reset the other hidden files kept in the subdirectories of /home to defaults for 10.04, where I found problems with the ext3 /home inherited from 8.04.4.  (Flash™ and Firefox® have both since been upgraded.)

---

