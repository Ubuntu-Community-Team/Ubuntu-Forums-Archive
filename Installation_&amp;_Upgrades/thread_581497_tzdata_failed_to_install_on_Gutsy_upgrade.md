---
title: "tzdata failed to install on Gutsy upgrade"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by wjhildreth on 2007-10-19
While doing a network upgrade from Feisty to Gutsy I had a couple of packages fail. As a result other failed due to dependencies.

I thought I could maybe try to manually install the packages to resolve the problem. The first on the list is tzdata.

When I try 

```
 sudo apt-get install tzdata 
```

I get the following message:

```


joeh@THJOEH:~$ sudo apt-get install tzdata
Reading package lists... Done
Building dependency tree       
Reading state information... Done
tzdata is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on tzdata (>= 2006c-2); however:
  Package tzdata is not configured yet.
dpkg: error processing util-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of locales:
 locales depends on tzdata; however:
  Package tzdata is not configured yet.
dpkg: error processing locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en-base:
 language-pack-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en-base:
 language-pack-gnome-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of util-linux-locales:
 util-linux-locales depends on util-linux (>= 2.13-0); however:
  Package util-linux is not configured yet.
 util-linux-locales depends on util-linux (<< 2.13.0-0); however:
  Package util-linux is not configured yet.
dpkg: error processing util-linux-locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on locales; however:
  Package locales is not configured yet.
 ubuntu-minimal depends on tzdata; however:
  Package tzdata is not configured yet.
 ubuntu-minimal depends on util-linux; however:
  Package util-linux is not configured yet.
 ubuntu-minimal depends on util-linux-locales; however:
  Package util-linux-locales is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en:
 language-pack-en depends on language-pack-en-base; however:
  Package language-pack-en-base is not configured yet.
dpkg: error processing language-pack-en (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en:
 language-pack-gnome-en depends on language-pack-gnome-en-base; however:
  Package language-pack-gnome-en-base is not configured yet.
dpkg: error processing language-pack-gnome-en (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
 util-linux
 locales
 language-pack-en-base
 language-pack-gnome-en-base
 util-linux-locales
 ubuntu-minimal
 language-pack-en
 language-pack-gnome-en
E: Sub-process /usr/bin/dpkg returned an error code (1)
joeh@THJOEH:~$ 


```

Anyone willing to help?

Regards,

Joe

---

### Post by wjhildreth on 2007-10-19
OK, I force a remove of tzdata using apt-get. Next I was notified that there were updates.

tzdata and util-linux were in the list. I told it to update and it went fine. I was then able to install with apt-get the packages I knew to not be installed.

locales
language-pack-en-base
language-pack-gnome-en-base
util-linux-locales
ubuntu-minimal

Now I know there must be some more stuff missing, but I don't know what. How do I find out if some packages are missing from the upgrade?

Is there someplace I can check? A log or something?

Regards,

Joe

---

### Post by wjhildreth on 2007-10-19
I notice I do not have the integrated desktop stuff. In my home machine, stuff like desktop wall paper and effects and other things are grouped all on the same dialog. This machine still has them as individual applets.

I am guessing there has to be more that needs to be installed.

Help Please....

Warm Regards,

Joe

---

### Post by BrooksOfSheffield on 2007-10-19
Not sure how to fix what's going on with your installation at this point, but I have a solution for anyone else who gets the tzdata error.  

The same thing happened with a dist-upgrade from edgy to feisty...  all you have to do is change your timezone and the dist-upgrade will work.  I recommend Europe/Kiev because I know that one works.

Once the upgrade is complete you can change your timezone back.

---

### Post by edk4971 on 2007-10-20
I'm having the exact same problem wjhildreth, compounded by the fact that when the upgrade failed, I went ahead and rebooted  (intending to hopefully start from a known state... I wasn't thinking) so know i'm stuck in CLI, X refuses to boot, complaining about no nvidia drivers or type1 fonts. I can't apt-get install anything because tzdata refuses to configure.

I'm going to try to change TZ to something like Europe/Kiev to see if that works, but everyone else has done it from the GUI do I'm not sure if it's going to work for me.

---

