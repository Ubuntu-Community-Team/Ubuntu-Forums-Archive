---
title: "Should I upgrade to 9.10? How will it affect Locked packages?"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2009-12-13
I have to keep my current version of Wine locked to my installed version (custom compiled by a developer). And I'm in the middle of fairly important work, so I don't want any big disruptions resulting from an upgrade gone bad. Should I upgrade from 9.04 to 9.10?

The main motivation for upgrading is that I'm getting ready to install the Android SDK and 9.04 repos don't have the required version of Eclipse. I can either just install Eclipse manually, or I can upgrade to 9.10.

In my situation, which would people recommend? Thanks

---

### Post by slakkie on 2009-12-13
I would try to mix my system, install Eclipse from Karmic on your Jaunty.

Yesterday I wrote something about it on my blog: [http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/](http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/)

You could use that to receive updates for Eclipse on Karmic, and keep your own system on Jaunty. And when you feel ready to move on, you can remove the preferences file or change it to upgrade.

---

### Post by Timby on 2009-12-13
> **MountainX said:**
> I have to keep my current version of Wine locked to my installed version (custom compiled by a developer). And I'm in the middle of fairly important work, so I don't want any big disruptions resulting from an upgrade gone bad. Should I upgrade from 9.04 to 9.10?

The main motivation for upgrading is that I'm getting ready to install the Android SDK and 9.04 repos don't have the required version of Eclipse. I can either just install Eclipse manually, or I can upgrade to 9.10.

In my situation, which would people recommend? Thanks

Don't upgrade to 9.10 yet wait until all the Bugs have been sorted.

I have upgraded and now I cant use my PC anymore.

I think that I will have to reinstall 9.4 as no one seems able to help me.

---

### Post by MountainX on 2009-12-13
> **slakkie said:**
> I would try to mix my system, install Eclipse from Karmic on your Jaunty.

Yesterday I wrote something about it on my blog: [http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/](http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/)

You could use that to receive updates for Eclipse on Karmic, and keep your own system on Jaunty. And when you feel ready to move on, you can remove the preferences file or change it to upgrade.

Fantastic blog post! Thank you! I am very glad to learn about this and I plan to follow your suggestion. (If I run into issues, should I post back here or on your blog?)

---

### Post by aust77 on 2009-12-13
> **Timby said:**
> Don't upgrade to 9.10 yet wait until all the Bugs have been sorted.

I have upgraded and now I cant use my PC anymore.

I think that I will have to reinstall 9.4 as no one seems able to help me.

I agree here. I plan on waiting until Lucid comes out, then I'll upgrade via CD. Or I can wait until the bugs sort out, as said.

In regards to your problem, there is no direct issue with manually installing. Heck, I recommend it. I installed Karmic with like 200 MB RAM over the requirements and it wouldn't boot up. I was forced to reinstall Jaunty, thus losing all my previous work. I am not discouraging you, as if you want to upgrade it is your choice. All I ask is you please read the release notes found here: [http://www.ubuntu.com/getubuntu/releasenotes/910overview](http://www.ubuntu.com/getubuntu/releasenotes/910overview)
so you know what you are getting into. Please take my advice seriously, as I lost much work when I upgraded!

---

### Post by slakkie on 2009-12-13
> **MountainX said:**
> Fantastic blog post! Thank you! I am very glad to learn about this and I plan to follow your suggestion. (If I run into issues, should I post back here or on your blog?)

On my blog or PM on the forums, what you prefer :)

---

### Post by geoff511 on 2009-12-13
Totally agree with what was said ---
DON'T UPGRADE !!
I just did, now I can't access the internet via firefox.
Most of the packages & progs that I usually use for DVD work isn't there, well I can't find them. And I can't find/dload/update codecs.
So now I am going to have to waste a day or so and install the 9.04 version.
This 9.10 version is CRAP!!

---

### Post by MountainX on 2009-12-13
> **slakkie said:**
> I would try to mix my system, install Eclipse from Karmic on your Jaunty.

Yesterday I wrote something about it on my blog: [http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/](http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/)

You could use that to receive updates for Eclipse on Karmic, and keep your own system on Jaunty. And when you feel ready to move on, you can remove the preferences file or change it to upgrade.
It would help me get started using apt/preferences if you gave a specific example for Ubuntu for using eclipse from karmic (9.10) on my jaunty box without upgrading jaunty.

From your blog, I understand that I will need to create /etc/apt/preferences. Will the contents of that file look like this?

```
# Allow Eclipse from Karmic on my Jaunty system
Package: eclipse
Pin: release a=karmic
Pin-priority: 990
```I have also added the following line in /etc/apt/apt.conf.d/01ubuntu 
```
APT::Default-Release "jaunty";
```And finally, I have created /etc/apt/sources.list.d/eclipse-repos.list with these 3 lines:

```
deb http://ppa.launchpad.net/eclipse-team/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/eclipse-team/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/yogarine/eclipse/ubuntu karmic main
```How close am I to having this correct?

You know, using preferences seems ideal, but this has a much steeper learning curve than simply manually installing eclipse. I'd be finished with that by now. But I have a little more time time now, and I'd like to learn this method.

Thanks for making your blog post.

BTW, [https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto) seems to indicate that using preferences is not the preferred way to do this in Ubuntu. But (afaik) their alternative didn't seem to offer any protection against upgrading stuff that I don't want upgraded...

Looks like I'm not even close to having this right.
EDIT: 
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
  404 Not Found
[snip]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources
  404 Not Found
W: Failed to fetch [http://ppa.launchpad.net/eclipse-team/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages](http://ppa.launchpad.net/eclipse-team/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages)  404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/eclipse-team/ppa/ubuntu/dists/karmic/main/source/Sources](http://ppa.launchpad.net/eclipse-team/ppa/ubuntu/dists/karmic/main/source/Sources)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by QIII on 2009-12-13
While it is unfortunate in the extreme that any of you have run into problems with Karmic, and this forum exists to help you sort them out, I would hardly call Karmic "crap".

The only problems I had with Karmic were in the Alphas, where I expected to have problems.

Updates are problematic.  Clean installs generally go better.  But to do the latter without a lot of heartache, it is best to have a separate /home partition, back it up just in case, save off a list of apt installed applications and use that list to automatically reinstall the new versions (third party applications will have to be reinstalled manually in most cases) and use the manual partition method during setup to retain you current /home partition.

Was Karmic "crap" for you?  Obviously.  Was it "crap" for everyone?  No.

---

### Post by slakkie on 2009-12-13
> **MountainX said:**
> It would help me get started using apt/preferences if you gave a specific example for Ubuntu for using eclipse from karmic (9.10) on my jaunty box without upgrading jaunty.

From your blog, I understand that I will need to create /etc/apt/preferences. Will the contents of that file look like this?

```
# Allow Eclipse from Karmic on my Jaunty system
Package: eclipse
Pin: release a=karmic
Pin-priority: 990
```I have also added the following line in /etc/apt/apt.conf.d/01ubuntu 
```
APT::Default-Release "jaunty";
```And finally, I have created /etc/apt/sources.list.d/eclipse-repos.list with these 3 lines:

```
deb http://ppa.launchpad.net/eclipse-team/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/eclipse-team/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/yogarine/eclipse/ubuntu karmic main
```How close am I to having this correct?

You know, using preferences seems ideal, but this has a much steeper learning curve than simply manually installing eclipse. I'd be finished with that by now. But I have a little more time time now, and I'd like to learn this method.


That is very true, but it becomes really handy once you get the hang of it.

On Ubuntu the default release doesn't really help. You can use it, but you still have to define preferences for jaunty-updates, jaunty-security etc etc if you use those repo's.

Your config looks good, except that you're not denying other packages from karmic to be installed. Below you'll find my version, which does exactly that.

> 
Looks like I'm not even close to having this right.
EDIT: 
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
  404 Not Found
[snip]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources
  404 Not Found
W: Failed to fetch [http://ppa.launchpad.net/eclipse-team/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages](http://ppa.launchpad.net/eclipse-team/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages)  404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/eclipse-team/ppa/ubuntu/dists/karmic/main/source/Sources](http://ppa.launchpad.net/eclipse-team/ppa/ubuntu/dists/karmic/main/source/Sources)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

I have those errors as well. You need to remove that PPA from your sources.list.

I would create the following preferences file (I use lucid/karmic, but you'll get the idea :)):

```

# Do not allow lucid, you might also want to add jaunty-security and -updates
Package: *
Pin: release a=lucid
Pin-Priority: -10

# Now allow karmic updates to dripple in
Package: *
Pin: release a=karmic
Pin-Priority: 990

Package: *
Pin: release a=karmic-updates
Pin-Priority: 990

Package: *
Pin: release a=karmic-security
Pin-Priority: 990

Package: *
Pin: release a=karmic-backports
Pin-Priority: 990

Package: *
Pin: release a=karmic-proposed
Pin-Priority: 990

# Eclipse based on version
Package: eclipse
Pin: version 3.5.1*
Pin-Priority: 990

```

---

