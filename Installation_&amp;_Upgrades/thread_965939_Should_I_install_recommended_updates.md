---
title: "Should I install recommended updates?"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by Arrowx7 on 2008-10-31
Just wanted to hear from people who know anything about ubuntu updates.

I know I should install critical updates, but are recommended updates important?
I heard they can mess up the ubuntu installation.  Is this true?  Should I install them?  Will I have problems with software if I don't install them?

Any information or suggestions would be much appreciated.

Thanks

---

### Post by Mark224 on 2008-11-01
Lots of people have had troubles after installing the recommended updates including myself.  I would not install them unless you are sure that they will work on your hardware.

---

### Post by meindian523 on 2008-11-01
Mark224:
Is this with Intrepid?

---

### Post by Mark224 on 2008-11-01
No, this is with Hardy.

---

### Post by OrangeCrate on 2008-11-01
> **Arrowx7 said:**
> Just wanted to hear from people who know anything about ubuntu updates.

I know I should install critical updates, but are recommended updates important?
**I heard they can mess up the ubuntu installation.  Is this true?**  Should I install them?  Will I have problems with software if I don't install them?

Any information or suggestions would be much appreciated.

Thanks

Personally, I've never heard that. I've installed every update since Breezy (so it's been quite a while), and I've never had a problem.

Besides, I simply not smart enough to think I can pick and choose which updates to keep, and which to reject, not knowing how they interact with other packages. So, I just install all of them.

---

### Post by caro on 2008-11-01
> **OrangeCrate said:**
> Personally, I've never heard that. I've installed every update since Breezy (so it's been quite a while), and I've never had a problem.

Besides, I simply not smart enough to think I can pick and choose which updates to keep, and which to reject, not knowing how they interact with other packages. So, I just install all of them.

I agree.  No problems here.

---

### Post by ssam on 2008-11-01
in the past there have been a couple of bad updates that have caused problems for some people. since then the process has been tightened up, with more testing of updates.

updates to a stable ubuntu release are only allowed if they fix a security problem or a serious bug. see [http://wiki.ubuntu.com/StableReleaseUpdates](http://wiki.ubuntu.com/StableReleaseUpdates)

---

### Post by meindian523 on 2008-11-01
Now that it's Hardy,I can confirm there's no problem with installing the Recommended Updates.I can't claim the experience of OrangeCrate,but I have installed all updates,including recommended since Feisty and there has never been a problem.

---

### Post by Arrowx7 on 2008-11-01
Alright thanks guys,
I currently have Intrepid.

Another question: Does it remove the old packages?  Each set of updates is like 100 megs --- huge space.  I was wondering whether it would just keep occupying more and more space on my hard drive.

Thanks.

---

### Post by meindian523 on 2008-11-02
It replaces the old packages.

---

### Post by Mark224 on 2008-11-02
> **meindian523 said:**
> Now that it's Hardy,I can confirm there's no problem with installing the Recommended Updates.I can't claim the experience of OrangeCrate,but I have installed all updates,including recommended since Feisty and there has never been a problem.

You obviously haven't read this thread [http://ubuntuforums.org/showthread.php?t=948584]("http://ubuntuforums.org/showthread.php?t=948584").  There are loads of people experiencing problems with the updates.

---

### Post by meindian523 on 2008-11-02
That's right,I haven't.But the update went fine for me and instead of doing something "experimental",I used some common sense and told the installer to keep the installed menu.lst.
I then checked the menu.lst,saw that it was still booting 2.6.24-19 and hand edited it to boot 2.6.24-21.So that I don't get screwed up,I kept the old kernel on standby by editing Recovery mode,so that I could boot into the old kernel and edit menu.lst back to it's original state in case 2.6.24-21 didn't work out for me.The new kernel ran fine,so today I edited menu.lst so that it boots 2.6.24-21 and restored recovery mode entry so that it boots 2.6.24-21 in Recovery mode.

---

### Post by Mark224 on 2008-11-02
What's "experimental" about installing recommended updates?  Not all Ubuntu users are Linux gurus.

For example I could not log in via the GUI when booting 2.6.24-21 nor get networking going again so I went back to 2.6.24-19.

---

### Post by meindian523 on 2008-11-02
Nothing experimental about installing recommended updates,lots of stuff experimental about doing a 3 way merge for menu.lst.

---

### Post by Mark224 on 2008-11-03
Sorry, but I've no idea what a "three way merge for menu.lst" means.

When I installed the updates I was not presented with any options to choose.  After the updates it told me to reboot which I did and then things were broken.

In the end I reinstalled Ubuntu from scratch because I did not know how to solve all the problems.

---

### Post by Mark224 on 2008-11-03
Deleted

---

### Post by meindian523 on 2008-11-05
An explanation of what I'm speaking about:
When I installed the new kernel,it had a default menu.lst and after configuration,it gave me options about what to do with menu.lst.Options were to retain the old one,replace the old with the default and something called a three-way merge,which had an (experimental) tag next to it.
1]I knew nothing of how this worked and 
2]It had that explicitly mentioned *experimental* tag next to it.
I used some common sense and opted to retain the old menu.lst and followed as described in my earlier post.And voila,nothing broke when I hand edited the menu.lst to boot the new kernel.

---

### Post by Mark224 on 2008-11-05
That's interesting.  I wonder why you were presented with these options and I was not?

I completely reinstalled Hardy, this time without the restricted ATI driver, installed updates, and all went fine.

According to what I have read on other threads the problems I had are known bugs.

---

### Post by meindian523 on 2008-11-06
THAT I wouldn't know either.

---

### Post by cybrsaylr on 2008-11-07
I've installed every update since Feisty and had no problems except for one update on Hardy that knocked out wireless on my new Toshiba laptop. My desktop has had no problems with installing all updates from Feisty thru Ibex.

---

### Post by grabro on 2009-01-09
Hi

I've been following these posts hoping someone would resolve my question but nobody has so here goes.

1) If I installed Ubuntu (8.10) over my existing OS will it allow me to keep my /home directory(separate partition) and will it also allow me to save my existing configuration files?

2) Will subsequent releases allow the same thing and not be a complete new install?


My concern is that Mepis moved from being an Ubuntu based OS to a Debian based OS because releases were a totally new install. I understand new releases of Debian just update the kernel.
 
I've been using Mepis 6.5 which is based upon Ubuntu (I prefer KDE) and I recently installed the Debain based Mepis 7.9rc1 on a separate partition. 

While Mepis 7.9 is good its wifi configuration is abysimal(41% signal strength and 248 b/s rate to download a single package). The same wifi configuration in 6.5 is 85%+ signal strength and it really flies.

The only difference between the two is the OS so Ubuntu appears to have a much better wifi configuration than Debian and because of this I'm thinking of changing to Ubuntu(with KDE).

grabro

---

### Post by meindian523 on 2009-01-09
If you are going Ubuntu with KDE,you need Kubuntu.And yes,it will keep your config files,if you tell it not to format your separate /home partition.

---

