---
title: "Upgrading 6.06 LTS -&gt; 7.10 (dapper -&gt; gutsy)"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by R3M3 on 2007-10-18
I have an infrequently used (x)ubuntu 6.06 LTS box. As I'm hoping to get more use out of it shortly, I am hoping to upgrade it to the latest (x)ubuntu. I know from the (very helpful) ubuntu.com front page that I can't do a direct update to Gutsy. However, I'd prefer not to waste time/bandwidth with a D->E->F->G multi-upgrade path.

Do any of you have any suggestions on how best to do the upgrade, while minimizing the amount of time and re-tweaking required?

My /home is on a separate partition, so that's not too much of an issue. I don't believe that I've done a ton of customization (although it's been a while, so I can't be too sure). Mainly it's the additional programs installed, and any driver settings. (as well as any issues I might not be thinking of at the moment.)

Thanks.

P.S. If anyone knows of any issues I should be aware of with respect to the differences between straight ubuntu 7.10 and xubuntu 7.10, I'd appreciate it.

---

### Post by linuxwizard on 2007-10-18
Look over this

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by tgalati4 on 2007-10-18
Linux Mint may be quicker.  It's currently based on Feisty, but it works pretty well.

If the box is not frequently used (as you say) then there shouldn't be a lot of personal data/settings on it.  Start fresh and you will be happier.

---

### Post by Ubangi on 2007-10-18
I am running on 64 bit K8 system and have used all of these version of Ubuntu, upgrading to new releases as they happened. However, it has never been easy and I am getting tired of it.

I like using Opera but, despite it being mentioned in the Ubuntu "software catalogue" webpage, it is not available through the normal update routes. I laboriously installed my own .deb package but it is lost with every upgrade.  So are any other manually installed or unsupported packages.

Also, fstab gets over-written, so you won't see any of your disks again.
The upgrade process takes a long time but you cannot leave it unattended, because it stops at random intervals, asking for trivial confirmations. You can never be quite sure what will have stopped working afterwards.

The upgrade process appeared to be going round in circles for several days, downloading loads of Open Office packages over and over again, sometimes failing with "dependency conflicts" on other packages.

There are too many potentially conflicting ways to install/update/upgrade software in Ubuntu, not counting the unofficial ones (update-manager, synaptic package manager, add-remove applications, apt-get, etc, etc. Why can't we have everything under one roof?

To sum up, Ubuntu still has some way to go to achieve a truly user friendly upgrade process. I think this should be given priority, given that upgrades are needed quite often.

I recommend starting from scratch, using a CD and a virgin disk and then not upgrading again for as long as you can put it off.

---

### Post by mattpker on 2007-10-18
Really the quickest way to do it would to be to backup everything in /home and do a full re-install to 7.10.  In the time it would take to upgrade each time it would be quicker to just make the tweaks. Let me know how it gose.

---

### Post by motin on 2007-10-19
Agree. Here is some useful notes from when I installed Feisty after Dapper and reconfigured it all within a couple of hours: [http://ubuntuforums.org/showthread.php?t=412183](http://ubuntuforums.org/showthread.php?t=412183)

---

### Post by R3M3 on 2007-10-26
I ended up doing the straight reformat-reinstall route for all my non-home partitions.

But before the installation, I did a:
[INDENT]sudo dpkg --get-selections > ~/oldpackages.txt[/INDENT]
to get a list of packages I'd installed. Then after the update, I scrolled through it and used Synaptic to install the packages I still wanted.

I also used the Restricted Driver Manager to set up the 3D drivers for my Nvidia graphics card.

The process was relatively painless, and so far I don't seem to have any problems I could convincingly blame on the "update".  

Thanks for the help.

---

### Post by motin on 2007-10-27
I still recommend using debfoster instead of dpkg --get-selections, since debfoster only takes into account the packages not installed by dependencies, and at the same time you get a nice guided tour of all packages and have the option to directly decide which ones you want to keep and not.

Did you follow the link that I posted just above?

---

