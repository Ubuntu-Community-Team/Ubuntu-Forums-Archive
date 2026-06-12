---
title: "can I upgrade 8.10 to 9.04 when it comes out?"
date: 2009-03-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Whiteeagle on 2009-03-21
This is what my PC is
emachine
XP-SP2
Celeron(R)CPU 2.93GHx
2.93GHz,760MB of RAM
I want to put 8.10 in F Drive 73.7 GB free space. Nothing else 
on drive.

I want to install Ubuntu and have 8.10 ready to install, but since 9.04 is so close will I be able to upgrade to 9.04. I read where you can't upgrade 8.04 to 8.10 and wondering if I would have trouble with 9.04.:popcorn:

---

### Post by tbegush on 2009-03-21
Yes you can upgrade to 9.04, the same way you'd install updates - through the update manager, - but I suggest that you wait until the official release

---

### Post by OrangeCrate on 2009-03-21
> **Whiteeagle said:**
> This is what my PC is
emachine
XP-SP2
Celeron(R)CPU 2.93GHx
2.93GHz,760MB of RAM
I want to put 8.10 in F Drive 73.7 GB free space. Nothing else 
on drive.

I want to install Ubuntu and have 8.10 ready to install, but since 9.04 is so close will I be able to upgrade to 9.04. **I read where you can't upgrade 8.04 to 8.10** and wondering if I would have trouble with 9.04.:popcorn:

That's not true. You can't by default, because it an LTS version, but if you change the upgrade option in Software Sources from long term support only, to normal releases, you can upgrade to 8.10. After making the change, the next time you open Update Manager, it will offer you the option to upgrade.

And, confirming what has already been said, you can go ahead and install 8.10 now, and then simply upgrade to 9.04 via the Update Manager after it's released, or, you can wait to install 9.04 fresh after release.

---

### Post by stone1343 on 2009-03-21
I have a follow-up question: What's the difference between updating Intrepid to Jaunty or installing Jaunty fresh? I have my Acer Aspire One working fine, I had to download madwife-hal (maybe you've met her  :-)  ) and alsa-driver, plus I've updated OOo and Gimp and done some other basic configuration. Will upgrading to Jaunty undo all that stuff? As I understand it, Jaunty includes the 2.6.28 kernel, which may have the madwife stuff built-in, so does it clean up the stuff I installed which is no longer needed? Is the upgrade basically just a whole bunch of individual packages? Does each package have the smarts to properly install itself? Are some of the packages written by Canonical?

If there's somewhere you can point me, that's awesome.

---

### Post by RedSingularity on 2009-03-21
I plan on upgrading as well when the stable release is finally out.  I hope it doesnt mess with my settings though.  I put to much work into my current setup!

---

### Post by OrangeCrate on 2009-03-21
Contrary to what you might have heard, or read, upgrading is actually preferred over a fresh install...

> Actually, We do NOT advise a clean install every time you want to upgrade. The upgrade path receives far more testing and attention than the clean install path. The official recommended method for moving to a new version of Ubuntu is to use a supported upgrade procedure!

jdong - post #96 - in this thread:

[http://ubuntuforums.org/showthread.php?p=6063808](http://ubuntuforums.org/showthread.php?p=6063808)

---

### Post by RedSingularity on 2009-03-21
Ohhh thats good to know.  I always thought it was the other way around.

---

### Post by RD1 on 2009-03-21
> Ohhh thats good to know. I always thought it was the other way around.

Only if you're running Windows. :p

---

### Post by zvacet on 2009-03-21
@ **Shadow121**

>  I hope it doesnt mess with my settings though

Best way to protect your settings is to have separate home partition.if you don´t have one you can make it following [this]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") or [this]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html") guide.

---

### Post by RedSingularity on 2009-03-21
Interesting......thanks!  :)

---

### Post by Whiteeagle on 2009-03-27
> **tbegush said:**
> Yes you can upgrade to 9.04, the same way you'd install updates - through the update manager, - but I suggest that you wait until the official release

Thanks, 
Yeah, I was planning to wait for the new one.:)

---

### Post by Whiteeagle on 2009-03-27
> **OrangeCrate said:**
> That's not true. You can't by default, because it an LTS version, but if you change the upgrade option in Software Sources from long term support only, to normal releases, you can upgrade to 8.10. After making the change, the next time you open Update Manager, it will offer you the option to upgrade.

And, confirming what has already been said, you can go ahead and install 8.10 now, and then simply upgrade to 9.04 via the Update Manager after it's released, or, you can wait to install 9.04 fresh after release.

Thanks for this. 
I feel better about doing it now. 
I was unable to install 8.04 for some reason so I installed 7.10. then when I got the good version of 8.10 I couldn't uninstall 7.10. It's all clear now. Had to format so 7.10 disappeared anyway.
Thanks guys. I'll learn this stuff eventually.
No need to respond to 7.10. That's in my past. But it sure was a simple one to install.

---

### Post by KCG102282 on 2009-03-27
> **Whiteeagle said:**
> I read where you can't upgrade 8.04 to 8.10

Where di you read this I did it last night?

---

### Post by Whiteeagle on 2009-03-27
> **zvacet said:**
> @ **Shadow121**



Best way to protect your settings is to have separate home partition.if you don´t have one you can make it following [this]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") or [this]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html") guide.

I was going to stop with the questions but I _have_ to ask this question.
If I am going to use only Ubuntu on this hard drive, is it necessary to have a separate home partition? There will be regular Windows folders, (Program Files, Recycler and System Volume Information)but I don't plan to use them.

---

### Post by snova on 2009-03-27
> **Whiteeagle said:**
> If I am going to use only Ubuntu on this hard drive, is it necessary to have a separate home partition?

No. It's never necessary, though it has some advantages.

---

### Post by Whiteeagle on 2009-04-09
> **KCG102282 said:**
> Where di you read this I did it last night?

Sorry, It looks like I misread. It was this:

> [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Before You Start

By default Ubuntu 8.04 LTS will not offer a upgrade to 8.10. This is because the 8.04 LTS version is a long term support release and 8.10 is a regular release. Upgrades from 8.04 LTS to 8.10 are fully supported, of course, and easy to enable.

    *

      You can directly upgrade to Ubuntu 8.10 from Ubuntu 8.04 LTS (see UpgradeNotes).
    *

      The upgrade will not be presented by default because 8.10 is not a Long Term Support (LTS) release.
    * Be sure that you have all updates applied to Ubuntu 8.04 LTS before you upgrade.
    *

      Before upgrading it is recommended that you read the release notes for Ubuntu 8.10, which document caveats and workarounds for known issues in this version.

If you have a version of Ubuntu which was released before Ubuntu 8.04 LTS, please see Installation/UpgradeFromOldVersion for information on how to upgrade. 

But since I didn't have 8.04 I went ahead with 8.10. It installed but I can't get into it.
I reboot and I get a black page with about 3 types of ubuntu and 2 windows selections to make. I gave up in ubuntu and clicked on the windows and it went to another black page with windows and ubuntu. I clicked on ubuntu and it took me to the ubuntu sign in page but it won't go any further.
With y'all talking about having the partition, I don't think I made one. When I installed it asked me about the partition and I chose to put ubuntu on all the free space on the drive. It's a 75 GB drive with only about 3 folders of windows that I cannot delete. One won't even let me look to see what's in it.
I may just wait for 9.04 as I haven't been able to put anything on 8.10 to upgrade to 9.04. 
Thanks for all your help.

---

