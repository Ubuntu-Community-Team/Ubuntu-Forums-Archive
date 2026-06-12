---
title: "Upgrade from 10.04 to 11.04"
date: 2011-07-11
forum: Installation &amp; Upgrades
---

### Post by dzwestwindsor on 2011-07-11
I've been running 10.04 since the day it came out. Now, 2 versions later, maybe it's time to upgrade.

Well, first off, should I upgrade? Or should I wait until 10.04 doesn't have support anymore?

Secondly, if I do decide to upgrade, what's the best way? Unfortunately on my 10.04 install (upgraded from Karmic), I don't have a partitioned home directory... should I partition it with GParted or something, in order to do a clean install?

If I do partition my home directory and do a "clean" install, would all my programs be gone? It would be nice to keep some of the programs.. because I have some enormous Git repositories outside my home directory that I would like to keep..

So whats the best way of doing this? Should I even upgrade to 11.04? Should I wait? Next version? Is it possible to upgrade without doing clean install (skip 10.10?)

---

### Post by Blasphemist on 2011-07-11
> **dzwestwindsor said:**
> I've been running 10.04 since the day it came out. Now, 2 versions later, maybe it's time to upgrade.

Well, first off, should I upgrade? Or should I wait until 10.04 doesn't have support anymore?

Secondly, if I do decide to upgrade, what's the best way? Unfortunately on my 10.04 install (upgraded from Karmic), I don't have a partitioned home directory... should I partition it with GParted or something, in order to do a clean install?

If I do partition my home directory and do a "clean" install, would all my programs be gone? It would be nice to keep some of the programs.. because I have some enormous Git repositories outside my home directory that I would like to keep..

So whats the best way of doing this? Should I even upgrade to 11.04? Should I wait? Next version? Is it possible to upgrade without doing clean install (skip 10.10?)

First, I will check out you blog. I suspect you may get a few replies to this, some for and against an upgrade. I moved from 10.04 to 10.10 to 11.04 during beta and now to 11.10 at the start of alpha. I use 11.04 normally and have another partition for 11.10, I'm not crazy. When I did that I shrunk windows, expanded my extended partition into that space and created multiple distro partitions. One swap will do for all. So now I can check out Fedora 15 and Gnome Shell, openSUSE, Kubuntu, Xubuntu and Debian too. 

It was a good learning experience and continues to be. I didn't do partition changes without good preparation and neither should you. Study and backup mainly. Gnome 2.x is no longer being developed and I wanted to check out the other distro's anyway. I find that Gnome 2.x seems old to me now and both Unity and Gnome Shell are to my liking. They are quite similar but I'm sure people will prefer each. 11.10 is the first I know of to go to the 3.0.0-x kernel but you can be sure that it will soon become common. 

It's a matter of preference and need. Download the iso's of a few, put em on a usb (I use multisystem) and give em a look. Check out the sites, enjoy!

---

### Post by akand074 on 2011-07-11
Well do you want very good stability? Or cutting edge software? If you want stability, stick with 10.04 until 12.04 where the nuts and bolts are taken care of. 11.04 just released unity with a very short period of time to develop, and 11.10 is adding a bunch of new core software like lightDM replacing GDM and such and as a result, you'll likely see some issues here and there. There are quite a few in 11.04 as I've noticed. 

Definitely do a clean install. If you came from karmic you might even want to fully clean your home partition. Honestly, clean installs in Ubuntu is nothing like Windows. I can have everything back the way I had it, all my software and such within 30 minutes of completing the install. In terms of programs, all you do is add any third party repositories and then use apt-get or software centre and just install everything in one go from one place.

---

### Post by dzwestwindsor on 2011-07-11
Thanks guys for the answers!

@akand074,

What is the best means of backing up my stuff? Put it on a flash drive or something? :confused:

---

### Post by Blasphemist on 2011-07-11
Back in time is what I use.

---

### Post by akand074 on 2011-07-12
> **dzwestwindsor said:**
> Thanks guys for the answers!

@akand074,

What is the best means of backing up my stuff? Put it on a flash drive or something? :confused:

Depends on how much stuff you have. USB flash drive or external hard drive. You can throw it on another computer over the network. You have a few choices. When you do a clean install, you might want to consider making a separate /home partition (or /data or something if you prefer) and keeping your data there so that you can do clean installs a lot easier without touching your data.

---

