---
title: "From 15.04 to 15.10 (command line upgrade)"
date: 2016-02-14
forum: Installation &amp; Upgrades
---

### Post by cogset on 2016-02-14
I shall apologize in advance for this well known question, however if I may ask: now that the time has come to move from 15.04 to 15.10 (BTW, that being the main reason why I've always used only LTS releases, i.e. I don't like frequent system upgrades... but the official Ubuntu-Mate release available was 15.04, so I went with it) how inappropriate would be to upgrade in the so called "debian way", in other words ensure that the system is currently up to date, _edit the sources.list file to point to the 15.10 release_, then go ahead with **apt-get update** followed by **apt-get dist-upgrade**?

  You may ask why go the trouble, well I've been managing package(s) installing and upgrades from command line for a while now, so bringing up the update manager and let it do all the work looks like taking a step back to me.
 I understand it does some behind-the scenes work to set things properly for a full system update, but I'd like to get more in control: of course I have a recent full-system backup already, and I have a standard installation as far as I can see, meaning no ppas have been added, no alternative kernels, no custom built packages and no packages from backports or proposed updates have been installed that I know of (at least, I've never purposely installed a package from backports with the -t vivid-backports option) .

  I have however all old kernels still left behind, I should have cleaned them  but I think I can still do that before the update and just leave the latest one. 

 If I go that route, I would of course first simulate the upgrade to check that nothing important gets removed or that some unmet dependencies get in the way - therefore, I could always put the original sources back in place and launch the update manager.  Any thoughts? Any reason why that could fail and/or break the system?

---

### Post by QIII on 2016-02-14
Hello!

```
apt-get dist-upgrade
```

will not take you to the next release.  That command will upgrade your *current* release to its most recent and updated components -- but still leave you at 15.04.

The command ```
do-release-upgrade
``` is [what you are looking for]("https://help.ubuntu.com/lts/serverguide/installing-upgrading.html").

As to whether or not that is appropriate, it is up to you.  Make sure you do 

```
sudo apt-get update && sudo apt-get dist-upgrade
```

and

```
sudo apt-get autoremove
```

first to be sure everything, including the kernel & headers, is up to date.

Could it fail and break your system?  Yes.  Is that likely?  Hard to say.

If you have complete backups, you mitigate your risk.

Personally, I always do a fresh installation to be sure that all the cobwebs are swept out of the corners.

---

### Post by cogset on 2016-02-15
I believe you may have missed this line which I have now highlighted in my post:[U]

> _edit the sources.list file to point to the 15.10 release_, then go ahead with **apt-get update** followed by **apt-get dist-upgrade**
[/U]
of course I didn't intend to move from 15.04 to 15.10 just by means of dist-upgrade alone.

Again, I have a full back up and I'm going to first simulate the upgrade process with apt-get -s upgrade to see what is going to happen, I'm just curious as to why this method is generally not advised: I get that the update manager makes things much easier, but what is that possibly makes Ubuntu more prone to breakage (*IF that is the case, I'm not claiming it actually is)* when relying on traditional command line apt tools for upgrading?

As for completely reinstalling...well, I think I get the general idea, but after running this OS for not even 6 full months, that seem definitely overkill to me: I've been using some LTS releases for more than 5 years (yes, even after support ended) without issues, besides I'm annoyed enough that I've had to pick a non-LTS release in this case, reinstalling would be just too much for me.

On regard to that, I always disinstall some packages that I don't need, disable services I don't want, modify some config files in /home and /etc, add a couple of commands to rc.local and maybe .xsessionrc : in short, I'd definitely want to keep all these modifications and not overwrite anything or install again packages that I've already removed.

---

### Post by cogset on 2016-02-23
So, it's done: I've purged older kernels/headers (as should I have done way before), made a backup, then simulated the update with apt-get -s upgrade and apt-get -s dist-upgrade first, after checking that there were no warnings or broken packages  I've finally removed the -s option and upgraded from 15.04 to 15.10.

  Other than losing a custom terminal image background and the lightdm greeter background, everything else looks OK.

Again, I'm curious about the technical reasons for which a command line upgrade is  generally discouraged for desktops: is that just for the sake of an easy upgrade option using the GUI (which I can understand) or are there more technical reasons behind this?

What should I eventually check to make sure that I haven't a broken system?

---

