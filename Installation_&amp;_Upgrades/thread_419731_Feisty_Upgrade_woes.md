---
title: "Feisty Upgrade woes"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by doooh_head on 2007-04-23
Hi All,

This has to be, for me, the worst experience ever in trying to upgrade.  I'm so disgusted.  Don't get me wrong, I know part of the problem is me, I am losing patience with the amount of work that is necessary to keep a system running.  Here's what happened:

After the release announcement last week of Feisty, I got home and immediately started the upgrade.  I noticed right away that as it was downloading files from the internet that it was awfully slow.  I attributed it to the fact that Ubuntu is more popular now and that alot of people may be attempting to download it at the same time.  I let it run overnight.  When I got up in the morning it had failed to download files.  Again I attributed it to busy servers.  I tried that for two days.  Nothing worked.  I downloaded and burned the alternate ISO image and it got alot further before it too started to download files from the internet, where again it got very very slow.  I was under the impression that the alternate CD was there so that you didn't have to goto the internet for files.  Regardless of which option I told it to use (get files from the internet as well, or not) it went to the internet and got bogged down.  I came here and discovered that the repository that I was downloading from (the default CA archive, for Canada) must just be bad and that I could simply choose a different one.  I switched to a different mirror and had all of the files for the upgrade in less than half an hour and the installation began, I walked away while it was doing this.  After awhile I checked up on it and a dialog was up asking if I wanted to keep or replace my xorg configuration.  I foolishly chose to keep it thinking that since I had gone through all of the effort of setting up my dual monitors that I would like to retain all of that, bad idea.  After the installation was done and the system was rebooted, the graphical system would not load.  I'm not all that familiar with Linux, so when my graphical display got messed up I lost all patience with it.  I started to reinstall, I told you I'm beginning to lose patience with this kind of bullshit.

Why can't the configuration files simply be merged somehow with new configuration requirements so that this kind of screwup doesn't happen?  In any case I followed the reinstallation process and got a new fresh install working with all of Feisty's nice new display happiness.  For me to get back to where I have a working  configuration whereby I can access my work computer, etc, is not a simple task (for me).  Of course the first thing I needed to accomplish was to get my dual monitors working once again.  I searched and found a site with specific Feisty instructions for my ATI graphics card.  It also included instructions for installing Beryle so I followed it.  The specific thing for me that I did was figure out how to copy and replace the xorg.conf file in case anything I did caused any kind of screwup, previously I didn't know how to do that.  I played with this for hours.  I could get dual monitors to work, but there was always something that was a little screwy.  Once I got dual monitors working, then Beryle wouldn't work.  Then I did something (not sure what) then all of a sudden my default monitor had switched to the other monitor (than the one I wanted to be the default) and I couldn't figure out how to get it back to using the other one.  

After days and days and countless hours I've just given up.  Oh I'll likely still go and piss around with it, and attempt to get it working again, but I have just had a very poor experience this time around and from my perspective it all began when the upgrade process gave me the impression that my configuration files could be retained and used when in fact they can't be, or shouldn't be unless you're a Linux guru who knows what that means.  Everything would have been fine if after doing the upgrade I had to figure out how to get my dual monitors back, but having my system come back in an unworking condition (for me) was the bitter end of a very poor upgrade.  

Yes I know, I really do know that alot of my problems, I caused, but I guess I expect more from Ubuntu, thats all.  I'll give it a few days then I'll attempt to get back at trying to figure out my problems.  I may look into reverting to an install that I had on a smaller hard disk (that I hope I still have) and see if I can copy that to my existing hard disk (as I've done previously) and see if I can work through another upgrade from it.  We'll see.

Doooh!

---

### Post by Sef on 2007-04-23
What are your computer specs?

---

### Post by doooh_head on 2007-04-23
My machines' specs are:
AMD2200+, 512Mb of memory, 2 60Gb drives, ATI 9250 graphics card with two CRT's connected up to it (one of them using an adapter), Microsoft mouse and keyboard.  I've been running Edgy on it ever since it came out.  I've never had any hardware issues with it and Ubuntu.

---

