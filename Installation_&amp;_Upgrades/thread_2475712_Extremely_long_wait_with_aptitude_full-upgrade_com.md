---
title: "Extremely long wait with aptitude full-upgrade command from Ubuntu 14.04 LTS to 14.10"
date: 2022-06-05
forum: Installation &amp; Upgrades
---

### Post by cdslinux on 2022-06-05
My friend had an abandoned VM on one of his computers that was about 8 years old. He installed it with Ubuntu 14.04 LTS and had some data in there. He wanted to revisit this VM and realises that the newest Ubuntu release is 22.04 LTS, so he has to upgrade. For some reason, on that VM, the upgrade within LTS versions won't work, so he is forced to go through the in-between versions (example: 14.10, 15.04, 15.10, 16.10, etc.).

He attempts to upgrade to Ubuntu 14.10 (utopic). Now because the dist upgrader gives an error for some reason, he has to use the Debian method of upgrading by changing sources.list and running the 3 commands. He is able to get the aptitude update and aptitude safe-upgrade command working successfully, but after that, the aptitude full-upgrade command gives some trouble. The aptitude full-upgrade has this "open: closed: defer: conflict:" way of 'resolving packages with dependency problems'. I put that in quotes because to me, it doesn't look like it's actually resolving any sort of problem by counting huge amounts of stuff, but I don't know. In my friend's case, the aptitude full-upgrade has been remaining at that "open: closed: defer: conflict:" stage for about 2 hours. When he ran the command, the 'dependency resolution' count drastically increased for the first hour, but now it is getting slower and slower. 

For information, there is disk activity, both read and write. He has also used the "-y" when running the aptitude full-upgrade command so he doesn't have to keep typing "yes".

What do I do in this case? Do I just keep waiting since there is disk activity, or is there any sort of other option that I should type to bypass this stage?

My friend doesn't want to clean install because he doesn't want to risk loosing anything.

Image on the left is the resolution stage, and image on the right is the VM disk activity indicator.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290578&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=290579&stc=1[/IMG]

---

### Post by TheFu on 2022-06-05
Doing that many upgrades is foolish.
Boot the 14.04, backup anything that cannot be lost, create a new VM and install the current LTS (22.04) into it, then restore the backed up data.
Anything else will just leave so much cruft behind that the system will likely be unstable.

BTW, there's little need to upgrade through all the non-LTS versions.  LTS-to-LTS upgrades have been working well since 10.04, provided only 2 are done.  On the 3rd LTS, it is time to do a fresh install.  Your friend is way, way, way, passed the 3rd LTS.  

IMHO.

Definitely don't even attempt 14.04 --> 14.10 or using any odd-year releases OR any October releases.

---

### Post by Impavidus on 2022-06-06
Just backup the data and do a clean install. What's backed up, won't be lost. Maybe not everything will work instantly after restoring the data, but what won't work wouldn't have worked either after upgrading the whole way.

---

