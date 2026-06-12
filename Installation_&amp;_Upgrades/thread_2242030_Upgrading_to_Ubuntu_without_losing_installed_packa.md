---
title: "Upgrading to Ubuntu without losing installed packages"
date: 2014-08-30
forum: Installation &amp; Upgrades
---

### Post by Mandeep_Singh on 2014-08-30
Hello all, I got a problem please help. I am a Linux Mint user and I want to  go for ubuntu now but I don't want to lose my currently installed  packages and settings. So, is there any way to install Ubuntu  without losing this stuff.

---

### Post by kansasnoob on 2014-08-30
It's not possible to convert Mint to Ubuntu. Even during a typical release upgrade from one version of Ubuntu to the next it's not possible to keep all previously installed apps in sync if they were installed from anything other than the standard Ubuntu repos or if they've been dropped from the repos between versions.

So you really have only two options; (a) backup anything and everything important and perform a fresh install, or (b) consider a dual-boot of Mint and Ubuntu if you have enough free space. Option (b) can seem a bit complex the first time you do it but in the long run it provides a great deal of flexibility.

On my "production" machine I ran a dual-boot of Precise and Trusty for a few months while I was tweaking Trusty to my liking. That way I could take my time fiddling with Trusty and just boot into Precise when I had things to get done.

But installations (and particularly reinstallations) require planning to avoid bugs like this:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

So if you want to consider a dual-boot start a new thread and explain what you want to do. Be patient and be sure you understand what you're doing before you actually do anything ................. sort of like woodworking - measure two or three times and cut only once :)

And always create a backup!!!!

---

### Post by grahammechanical on 2014-08-30
There is a reason why it is called Linux Mint and not Ubuntu Mint. It is different and the differences are enough to deny use of the word "Ubuntu" in the name. Linux Mint will use software packages that are not in the Ubuntu repositories. It is very likely that any attempt to do what you want will result in a broken OS with a fresh install as the best way of fixing it.

---

### Post by ajgreeny on 2014-08-30
I totally agree with the two above posts and I don't think it is possible, but you could always try; it would be very interesting to find out what happens.

Disable the mint repositories in your software sources, remove any packages with **mint** in their name and then finally install **ubuntu-desktop** package; the Ubuntu repos are enabled in mint, as far as I'm aware, so it should be there to install.

However,  you need to be prepared for a lot of probable breakages; this is most definitely not a  generally considered way of going about this change, and I fear that itwill  end in disaster for your current installation, and eventually  require you to start from scratch and clean install your wished for  Ubuntu version as suggested above.

Just make sure you have good backups of  everything in your home, and if bandwidth and download restrictions are a  problem for you, copy all the packages from mint's  /var/cache/apt/archives to a newly made folder in your home, eg  ~/backup, with  command ```
cp /var/cache/apt/archives/*.deb backup
``` and you can  then use those .deb files to reinstall the packages you want on the new  installation, by copying the .debs back to /var/cache/apt/archives/ and then using either **apt-get install package**, or my preferred **synaptic** package manager.

---

