---
title: "Time for new distro??"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by Big_J on 2007-04-19
Maybe it's time for me to switch off ubuntu. Even though it's very stable, and perhaps the best distro, but I'm having just about enough of the occasional problems, because these occasional problems are always almost impossible to fix. 

This time however, my whole life literally hangs on the line... 
12 pages of an college English report, that I need to finalize and finish within three days, and a huge program that I cannot possible reprogram within 3 days. 
Given that they need to be turned in so soon, and this isn't little kid's highschool, there are no second chances, and my scholarship hangs on the line. Not to mention that the way by which I came upon Linux in the first place is because I'm too poor to afford Windows. Great. Thank you ubuntu developers.

Before you respond, my anger is justified.
You see, I was NOT trying to upgrade to 7.04, no no. I simply clicked on the cute orange button and installed "security updates."

Ok. I mainly wrote that to get your attention as this is not another failed upgrade issue. I have a copy of the program on my laptop, and I have a  hard copy of the paper so worst case scenario, I just need to retype it. 

But as I said before, I wasn't upgrading to 7.04, I was simply installing the updates and I can no longer use ubuntu (x anyway).
The updates were:
libx11-6
libx11-data
libx11-dev
tzdata

After the update, I could no longer get to home folder, so I restarted and walla. GDM does not start. All I get is the rotating circle mouse cursur and it goes on and on. 
I downgraded libx11-6, libx11-data, and libx11-dev to the version they were before the upgrade, yet I still cannot gdm.
X runs fine, but I also tried to reconfigure xorg.conf just in case, nothing. 
I have no idea why this happened, but I really need to fix it asap.

You think it may have something to do with gnome?
What can or should I do?

If I go into recovery mode, it says that mounting local filesystems failed, and the keyboard goes out. Any ideas?

Please help.

---

### Post by floke on 2007-04-19
can you get to terminal - startx - and then once on to a desktop try 
sudo /etc/init.d/restart gdm [the last bit might be wrong way around]

if this fails - you can install kdm and set to default until you can fix gdm

---

### Post by erikcw on 2007-04-19
If you didn't format your partition, you can use the LiveCD or Knoppix to get your school projects...

---

### Post by Big_J on 2007-04-19
> can you get to terminal - startx - and then once on to a desktop try
sudo /etc/init.d/restart gdm [the last bit might be wrong way around]

if this fails - you can install kdm and set to default until you can fix gdm
"Fatal server error:
Server is already active for display 0
Xlib: connection to ":0.0" refused by server
Xlib: No protocol speceified

Giving up."

maybe it's more than gdm??
And I cannot install KDM because all the servers are overloaded with everyone trying to upgrade.

> If you didIf you didn't format your partition, you can use the LiveCD or Knoppix to get your school projects...n't format your partition, you can use the LiveCD or Knoppix to get your school projects...
I haven't tried Knoppix, but no, I cannot use the liveCD. I can only mount the swap on the live cd (unless I'm doing something wrong. If so, then how do I do it?).

Thanks for the help both of you, but I'm still stuck.

---

### Post by Podex on 2007-04-19
So what have you tried exactly to mount the partition on the LiveCD? Did you try
```
sudo mount /dev/hda1 /media/hda1
```
or similar?

---

### Post by Big_J on 2007-04-19
ahh, no, my line was different.
Thanks.

But no matter, i would really like to use my installed system. Please someone help. Tell me what I can post to help you help me :)

---

### Post by Jengu on 2007-04-19
Installing over an existing installation rather than trying to fix it was probably a mistake. Since you know the names of the updated packages, you could have rolled them back to an earlier version. I don't know if there's a builtin way to do that, but you can do it by hand by going into /var/cache/apt/archives and finding the deb's for those packages. You'll see multiple deb files for those packages probably. For each package, find the .deb file that is one version back from the latest. Then do "dpkg -i thatpackage.deb" for each one. That should in effect, undo the update. Afterwards you might try reinstalling the updated packages and seeing if the problem is reproduceable, and if so file a bug report.

---

### Post by Big_J on 2007-04-19
> Installing over an existing installation rather than trying to fix it was probably a mistake. Since you know the names of the updated packages, you could have rolled them back to an earlier version. I don't know if there's a builtin way to do that, but you can do it by hand by going into /var/cache/apt/archives and finding the deb's for those packages. You'll see multiple deb files for those packages probably. For each package, find the .deb file that is one version back from the latest. Then do "dpkg -i thatpackage.deb" for each one. That should in effect, undo the update. Afterwards you might try reinstalling the updated packages and seeing if the problem is reproduceable, and if so file a bug report.
That's basically what I did. I simply downgraded them back to the previous version!

After about 10 minutes of waiting, I was able to download KDM and install it. It runs but I cannot log in.
after I type my password, it says:
"Cannot open theme file /usr/share/apps/kdm/themes/kubuntu"
and goes back to the login prompt.

---

### Post by Big_J on 2007-04-19
bump... HELP

---

### Post by askreet on 2007-04-19
Whomever suggested that you install KDM was mistaken, the KDM package in Ubuntu requires a whole lot of packages.  Can you post the output of mount for us?

---

### Post by Big_J on 2007-04-19
I already have kde installed. 
Why mount, I'm not trying to mount anything right now?
I want to log in to my installed system, which is mounted already...

---

### Post by spaceghoti on 2007-04-19
> "Cannot open theme file /usr/share/apps/kdm/themes/kubuntu"I assume this means you can get to the login window, which means you can get to a terminal session through CTRL-ALT-F2.  If you log in that way, what happens if you *ls /usr/share/apps/kdm/themes/kubuntu*?  Do you get access denied or does the path not exist?  In the case of access denied you can *sudo chmod* the folder to give yourself the permissions you need (665 should work), in the case of the directory not existing you can create it yourself and leave it blank, see what Kubuntu does with it.

Hope this helps!

---

### Post by Big_J on 2007-04-20
I used "update-rc.d -f gdm" so I can start in text mode, but now my keyboard won't work. I cannot type anything so I'm pretty much screwed arn't  I?

Edit:
fixed by unplugging and plugging back in 

Now when I try to startx, I get a list of errors. Pretty much everything is an error. Cannot open this cannot open that, could not init font path element for all of them.

refcount is 2, should be 1

I CANNOT STARTX now!

---

### Post by kingmob on 2007-04-20
Altough it will not be 'clean', you might be better of or at least quicker by using live-cd, backing up your files to your home directory (if they aren't there already) and do a clean install with the old /home mount intact.

I'm by no means an expert, so what i would try first in this situation, is completely removing gdm and kdm and then work up from there by startin x from tty1 by hand. Then finish your project and work on getting a decent system after that. I can relate with hours of work being destroyed yesterday by a system hang, had to rewrite a big part of my thesis :|

---

### Post by Big_J on 2007-04-20
> **kingmob said:**
> Altough it will not be 'clean', you might be better of or at least quicker by using live-cd, backing up your files to your home directory (if they aren't there already) and do a clean install with the old /home mount intact.

I'm by no means an expert, so what i would try first in this situation, is completely removing gdm and kdm and then work up from there by startin x from tty1 by hand. Then finish your project and work on getting a decent system after that. I can relate with hours of work being destroyed yesterday by a system hang, had to rewrite a big part of my thesis :|

Ahh. But sometime ago, while installing a few too many applications on my small 5GB root partition, I had about 20mb left and my system slowed down to a halt. So I reinstalled with my home on / 
I have one big partition for root and home.

everytime I try to use apt-get or aptitude now it gives me errors

```

E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
Setting up gdm(2.16.1-0ubuntu4.1) ...
 *reloading GNOME Display Manager configuration...
 * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.
gtk-update-icon-cache: symbol lookup error: /usr/lib/libgdk_pixbuf-2.0.so.0: undefined symbol: g_type_register_static_simple
dpkg: error processing gdm (--configure):
subprocess post installation script returned error exit status 127
Errors were encountered while processing: 
 gdm
```

---

### Post by Big_J on 2007-04-20
> **kingmob said:**
> Altough it will not be 'clean', you might be better of or at least quicker by using live-cd, backing up your files to your home directory (if they aren't there already) and do a clean install with the old /home mount intact.

I'm by no means an expert, so what i would try first in this situation, is completely removing gdm and kdm and then work up from there by startin x from tty1 by hand. Then finish your project and work on getting a decent system after that. I can relate with hours of work being destroyed yesterday by a system hang, had to rewrite a big part of my thesis :|

I recovered the paper through live cd, it's on my laptop now. 
I just need to log in to my desktop now (in gui). I have way too much data to give up, downloading everything will take months. Backup is an option, but I don't have time to do it now, since finals are next week, and I want to use my desktop. This is way too much trouble for a simple "security" update, and I refuse to reinstall for it.

Argh. I cannot even reinstall ubuntu-deskotp, it gives me the same error for gdm, gnome-orca and planner

---

### Post by Big_J on 2007-04-20
Howcome so many applications just bacame broken all of a sudden? Why am I unable to install gdm, gnome-orca and some other stuff unsatifiable when i try to install ubuntu-desktop?
I'm starting to think this is all due to the servers overloading. Any ideas?

---

### Post by kingmob on 2007-04-20
You can't uninstall gdm etc?
It looks like something is wrong with your x-server, so i think it is best if you start from there. Take some care looking at the errors startx throw to you, look at /var/log/Xorg.log, it should give you some clues to what is happening. 

What i had with updating to feisty was that the tty files got corrupted, maybe this is somehow related?

---

### Post by Big_J on 2007-04-20
yes, x crashes now, but the problem didn't start with x crashing.
Of course I can uninstall gdm. Why would I not be able to? 
I already have uninstalled it, and I cannot reinstall it.

when I startx now, it tells me that pretty much everything it needs to use cannot be opened, and everything it needs to load cannot be found. 
I reconfigured it and still the same thing.

What's really pissing me off and confusing me is that I was NOT trying to upgrade to feisty. I was happy with edgy.
I was simply installing three x updates, libx11-6 and so on, and everything went bad. The first thing I tried was to downgrade them back to what they were, and everything was still horribly wrong. And now everything is messed up.
The same updates are available for my laptop, and I'm afraid to apply them.

---

### Post by kerry_s on 2007-04-20
You can always try pure debian, if you want to give up on ubuntu.

net install-> [http://debian.cites.uiuc.edu/pub/debian-cd/current/i386/iso-cd/debian-40r0-i386-netinst.iso](http://debian.cites.uiuc.edu/pub/debian-cd/current/i386/iso-cd/debian-40r0-i386-netinst.iso)

kde install-> [http://debian.cites.uiuc.edu/pub/debian-cd/current/i386/iso-cd/debian-40r0-i386-kde-CD-1.iso](http://debian.cites.uiuc.edu/pub/debian-cd/current/i386/iso-cd/debian-40r0-i386-kde-CD-1.iso)

xfce4 install-> [http://debian.cites.uiuc.edu/pub/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso](http://debian.cites.uiuc.edu/pub/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso)

Use installgui for the pretty installer. :)

---

### Post by Big_J on 2007-04-20
I switched to ubuntu from debian! (to debian from slackware...)
I like ubuntu, and normally when things go wrong it's my fault, but this time this should not have happened.
Anyway, I'm really stressed over this, but nothing to do. I backed up my important data to six dvds, and did a fresh install of feisty. 

All is good now, except of course that I need to reinstall all the applications, and recustomize everything, go through the lengthy process of restoring the stuff I couldn't backup (like bookmarks, settings, cookies and whatnot). And of course download all the files that I did not backup.

I really hate the new partition editor in the installation, I wish it was the same as the ones before (gpartition I believe). Everything went smoothly, but the parition editor automatically wrote the table without asking, and I lost a huge ntfs partition that I had lots of files on. And the migration tool didn't detect anything from my windows.

Oh well. Awaiting a new total disaster and reinstallation in six months. :)


Edit:
I must say, Feisty is running very smoothly. I like it.
It's better than an upgrade from dapper to edgy. So far very good.

---

### Post by floke on 2007-04-20
Glad to hear you got it working. Have been offline since I posted so was unable to keep track of your problem. I had a similar thing to you the other day - my own fault though (was messing around with login options and broke it - could't get to login screen and had the same error as you about gdm 'reload' etc.). I searched for hours online and found not a single answer to the problem. In the end I installed KDM + startx to get to a semi-working system. Then restarted gdm from the gui and was able to - slowly (amidst crashes) change the login options back the way they were originally. 

Just rambling here really, but felt I owed you some explanation for the KDM thing, since it clearly didn;t work for you. Anyway, so that was the rationale behind it.

Glad it all worked out., And good luck with your studies.

:)

---

### Post by Big_J on 2007-04-21
> **Steve.K said:**
> Glad to hear you got it working. Have been offline since I posted so was unable to keep track of your problem. I had a similar thing to you the other day - my own fault though (was messing around with login options and broke it - could't get to login screen and had the same error as you about gdm 'reload' etc.). I searched for hours online and found not a single answer to the problem. In the end I installed KDM + startx to get to a semi-working system. Then restarted gdm from the gui and was able to - slowly (amidst crashes) change the login options back the way they were originally. 

Just rambling here really, but felt I owed you some explanation for the KDM thing, since it clearly didn;t work for you. Anyway, so that was the rationale behind it.

Glad it all worked out., And good luck with your studies.

:)

Thanks. I'm still kind of pissed that I had to do a complete reinstall for simply updating my software, but I'm kind of glad too because I really like Feisty, it's pretty smooth.

One thing greatly bothered me though, the partition editor on feisty is horrible. I accidentally chose an option that deleted all paritions on the hardrive, and without pressing apply or a confirmation, the table was written and I lost a huge ntfs partition that had many files and windows programs (mainly games).
Good thing I didn't touch the windows harddrive, or I would be screwed.

---

### Post by bulldog on 2007-04-21
> **Big_J said:**
> Thanks. I'm still kind of pissed that I had to do a complete reinstall for simply updating my software, but I'm kind of glad too because I really like Feisty, it's pretty smooth.

One thing greatly bothered me though, the partition editor on feisty is horrible. I accidentally chose an option that deleted all paritions on the hardrive, and without pressing apply or a confirmation, the table was written and I lost a huge ntfs partition that had many files and windows programs (mainly games).
Good thing I didn't touch the windows harddrive, or I would be screwed.

Download the GParted live cd [aprox. 50MB] burn it on a cd-r,and you have a nice partitioner with a GUI.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

You can create your partitions on forehand and you only have to mount them when you install ubuntu.

I'm sorry to read about your mis fortune with Edgy.
But to avoid that kind of things for the future,I would recommend the LTS Release called Dapper Drake.
It's the long time support and very stable release of ubuntu.

If you persist in using Feisty,it can happen again,although I can imagine you like Feisty very much,like I do.:) 

Or create a separate /home for your data,so you can reinstall without losing anything.

---

### Post by kingmob on 2007-04-22
Sorry for the late reply, i see it is now not very useful anymore.
I've had this in the past, that X started telling me it couldn't find anything. It looked like it was searching for the wrong kernel. Last time it turned out i had somehow switched from generic to something different. Removing all obsolete kernels, uninstalling al xorg packages and then reinstalling the correct ones fixed that for me. Sounds like a lot of work but that actually took me 5 minutes then. The problem was figuring out what was wrong as always.

I think this has to do with the fact that you start messing with your Ubuntu at a certain level, because you are not totally clueless. Problem is, something will probably break and if it doesn't happen immediately, it will be hard to trace if you are not a guru.

For instance feisty is giving me a hard time because I updated from edgy with custom nvidia drivers. I have enough of a clue to install those custom drivers, but not how to tell feisty everything is all right and just go ahead with the update.

---

