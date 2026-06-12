---
title: "Updates cannot access internet"
date: 2011-04-14
forum: Installation &amp; Upgrades
---

### Post by triplemaya on 2011-04-14
I have a repeat of a previous problem, due to reinstalling karmic. The new install sees the net ok, firefox and thunderbird work perfectly. however, updates not working. When i do sudo apt-get update tries url after url but cannot connect. The update manager cannot connect at all.

I have tried a new version of sources gerated by the Ubuntu Sources List Generator at
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)
but this does not help, as it did not last time.

I have tried different servers, which seemed to do the trick last time, but this time it makes no difference at all.

As before, I am not using a proxy.

---

### Post by mörgæs on 2011-04-14
9.10 has only a few weeks left of support. 

You should rather install a fresh 10.04.2 or 10.10

---

### Post by triplemaya on 2011-04-14
Good point. (though I thought it was lts) I'm going with 10.10. The problem is I have to axe ooo quickstart if I want to be able to shut the computer down! I am somewhat disapointed this has not been fixed, but then, it is free software!

Thanks for your input.

---

### Post by KegHead on 2011-04-14
Hi!

Try:

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

Please advise.

KegHead

---

### Post by triplemaya on 2011-04-14
Hi KegHead. Thanks for the suggestion. However, as stated in the last post, I decided to give 10.10 a try.

HOWEVER. At the moment I am nearing the point of beating my forehead bloody with the problems I am having with 10.10 - details on request!

If you are relatively confident that this would solve the problem I will probably abandon 10.10 and go back to karmic, which was working relatively well ( apart from synaptic crashing on first use, gnome desktop tool crashing on first use, and java being unuseable, which is why I was going for a reinstall)

---

### Post by mörgæs on 2011-04-14
You have marked the thread 'solved', and still you indicate that you have serious errors? If you still have errors, please post a thorough hardware list.

If you want to test something else than 10.10 (which is a good idea), 10.04.2 is the one to try. Remember to have wired internet access while installing. An alternate CD rather than the standard one is even better.

Forget about 9.10 - even I will have to let go of it in a week's time...

---

### Post by triplemaya on 2011-04-15
Asus P5QPL-AM - onboard everything
E6300
Crucial 4GB DDR2 800MHz/PC2-6400
Hitachi DeskStar 1TB
wired internet access only

My problem with the new install of 10.10 was a corrupted database preventing any apt operations, even after a reboot. That has been resolved by yet another reinstall. I think the problem might have been caused by my terminating an install process before it was finished, I can't think of anything else. I think it is the install of wine which leads to a attempt to install of fonts which looks as if it is never going to end. Thinking this might be the problem I left the pc on all night, and it did finish in the end. After everything else is finished, I estimate it takes about 8 hours for apt to finish trying a long list of sites and giving up.

This is a sample of what it was still busy doing when I went to bed 


--2011-04-14 22:53:49--  [http://dfn.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://dfn.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
Resolving dfn.dl.sourceforge.net... 32.1.6.56, 2001:638:d:c101:acdc:1979:2:1001
Connecting to dfn.dl.sourceforge.net|32.1.6.56|:80... failed: Connection timed out.
Connecting to dfn.dl.sourceforge.net|2001:638:d:c101:acdc:1979:2:1001|:80... failed: Network is unreachable.
--2011-04-14 22:54:49--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
Resolving heanet.dl.sourceforge.net... 32.1.7.112, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|32.1.7.112|:80... failed: Connection timed out.
Connecting to heanet.dl.sourceforge.net|2001:770:18:aa40::c101:c142|:80... failed: Network is unreachable.
--2011-04-14 22:55:49--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
Resolving jaist.dl.sourceforge.net... 32.1.2.0, 2001:200:141:feed::feed
Connecting to jaist.dl.sourceforge.net|32.1.2.0|:80... failed: Connection timed out.
Connecting to jaist.dl.sourceforge.net|2001:200:141:feed::feed|:80... failed: Network is unreachable.
--2011-04-14 22:56:50--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
Resolving nchc.dl.sourceforge.net... 32.1.14.16, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|32.1.14.16|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2011-04-14 22:57:50--  [http://ufpr.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://ufpr.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
Resolving ufpr.dl.sourceforge.net... 1.0.0.0
Connecting to ufpr.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-04-14 22:58:50--  [http://internode.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://internode.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
Resolving internode.dl.sourceforge.net... 1.0.0.0
Connecting to internode.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-04-14 22:59:50--  [http://voxel.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://voxel.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
Resolving voxel.dl.sourceforge.net... 1.0.0.0
Connecting to voxel.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-04-14 23:00:52--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
Resolving kent.dl.sourceforge.net... 1.0.0.0
Connecting to kent.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.


But eventually it gave up on the fonts

The following fonts failed to install :  andale32.exe arialb32.exe arial32.exe comic32.exe courie32.exe georgi32.exe impact32.exe times32.exe trebuc32.exe verdan32.exe webdin32.exe.
The fonts are NOT installed.
Please run 'dpkg-reconfigure ttf-mscorefonts-installer' to perform the installation again


and went on to complete the install of some 25 packages it was working on.


The remaining problems with 10.10 are not being able to shut the computer down unless I kill ooo quickstarter, and not being able to use ctrl ctrl. I,ve just disabled the quickstarter, which is a real nuisance but I can live with it. Similarly, I just work around not being able to assign ctrl ctrl - it seems that all the latest distros have this bug, and no one is very interested in it.

---

### Post by mörgæs on 2011-04-15
I can not really get the overview of where it goes awry. Can you install a plain vanilla 10.10 and apply all updates without errors, and is it stable through a few reboots?

---

### Post by triplemaya on 2011-04-15
Thanks for your concern. 10.10 is working fine now I have reinstalled it again, apart from the minor problems. I think that what messed up the apt database, on the previous install of 10.10, was me terminating the process of installing all the software I use, thinking this action did not matter, and that I could restart the process. As far as I can tell, this is not a safe operation!

I'm pretty sure it is wine that causes the problem, as the hours of error messages seem to all be about dot exes for certain fonts. I am most curious as to why the install operation of wine runs to 5 hours or more of trying so many sites and failing on all of them.

---

