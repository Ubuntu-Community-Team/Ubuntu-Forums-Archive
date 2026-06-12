---
title: "Upgrade minidlna package"
date: 2012-11-18
forum: Installation &amp; Upgrades
---

### Post by Shutterstrom on 2012-11-18
Hi, I've really tried to brows the web for help but I can't find any info that is helping me to complete my task.

What I would like to do is to upgrade minidlna on my ubuntu server 12.04 LTS. The current version installed is 1.0.21, and it came when I typed ```
sudo apt-get install minidlna
```.

But this is an old version of minidlna and the latest one is 1.0.25.

_Question #1_
Why does not Ubuntu upgrade to 1.0.25 version

_Question #2_
Is there a way for me to upgrade minidlna with ```
sudo apt-get update
``` and ```
sudo apt-get upgrade
``` If so, how can i make Ubuntu understand that tere is an update for minidlna?

_Question #3_
I also tried to install a .patch file for minidlna, but I don't know where the files are that I want to patch. Are these files that I want to patch on my server even though I used ```
sudo apt-get install minidlna
```

I guess you can tell that I'm quite new to Linux so please keep it as easy to understand as possible with good code examples and tips.

Thanks in advance!

---

### Post by raja.genupula on 2012-11-18
Hi
      Providing an upgrade to a specific software is not a big deal , though its not such easy thing . Anything you'd like to install can be fine if you satisfied all required dependencies with the specific versions requirements.

you can have your desired version for sure . get the version source package from its source site and you can install it manually .

But for manually installed packages/applications Ubuntu not going to provide any updates . so you are at your own risk .

Hope that helps.

---

### Post by Shutterstrom on 2012-11-18
> **raja.genupula said:**
> Hi
      Providing an upgrade to a specific software is not a big deal , though its not such easy thing . Anything you'd like to install can be fine if you satisfied all required dependencies with the specific versions requirements.

you can have your desired version for sure . get the version source package from its source site and you can install it manually .

But for manually installed packages/applications Ubuntu not going to provide any updates . so you are at your own risk .

Hope that helps.

Hi Raja and thanks for the reply.

What I'm looking for is a way for Ubuntu tu understand that there is an update for minidlna by using the apg-get commando. Is there a way to do that? (refering to my question #2)

If I download the minidlna_1.0.25_src.tar.gz from sourceforge.net, this means that I will install it manually and will not be able to upgrade minidlna via apt-get in the future?

If it's possible to upgrade minidlna via apt-get commando, how can I do that then?

---

### Post by raja.genupula on 2012-11-21
yes thats what i mean . If you have install it manually then in future you can't update with apt-get .

wait for some more time , I am sure Ubuntu will provide it with next updates . There might be some serious bugs associated with the latest version . 

wait for some more time . 

else in the launchpad page of that pkg you can see whose maintaining it and you can contact the maintainer about the update .

Hope that helps .

---

### Post by zvacet on 2012-11-22
Yuo can add [this]("https://launchpad.net/~flexiondotorg/+archive/server-stuff") PPA.Version is 1.0.24.

---

### Post by TiloBunt on 2013-01-22
please check this bug 
[https://bugs.launchpad.net/ubuntu/+source/minidlna/+bug/1026550](https://bugs.launchpad.net/ubuntu/+source/minidlna/+bug/1026550)

also I just update via PPA from previous post ([https://launchpad.net/~flexiondotorg/+archive/server-stuff](https://launchpad.net/~flexiondotorg/+archive/server-stuff))

looks fine (1.0.24)
make sure you backup you config file

funny enough Ubuntu 12.10 comes with 1.0.24 as already. 

cheers

---

