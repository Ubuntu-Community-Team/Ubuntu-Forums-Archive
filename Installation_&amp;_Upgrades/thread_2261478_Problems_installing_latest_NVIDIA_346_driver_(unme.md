---
title: "Problems installing latest NVIDIA 346 driver (unmet dependencies)"
date: 2015-01-19
forum: Installation &amp; Upgrades
---

### Post by contijn-buijs on 2015-01-19
I am using Deepin OS 14.02 which is based on Ubuntu.

After removing the old 340 driver I went to install the latest one from the edgers repo and I get the following message:

[I]The following packages have unmet dependencies: nvidia-libopencl1-346 : Conflicts: libopencl1 Conflicts: libopencl1:i386 ocl-icd-libopencl1 : Conflicts: libopencl1 ocl-icd-libopencl1:i386 : Conflicts: libopencl1 E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

[/I]I tried multiple things before getting to this point like autoremove, autoclean, purge, update and upgrade. basically everything to get as clean as possible nvidia wise to install the latest one.

I googled a bit for this error and came across a command to maybe remove the conflicts like "*libopencl1*". I then got a message saying that it was a virtual package and it can't be removed.

What I also have gathered is that MAYBE it works better if I use the official nvidia installer ".run" file and stop my "lightdm" it's called?

Basically unloading the GUI and installing it from the terminal. I am a bit scared to do that because what if I do that and I still get the same message? Can I then still get into the OS graphically? I had issues in the past with Ubuntu and black screens after using the installer.

Does anyone know what is causing this issue? It seems so simple. Remove the conflicting packages and then it can install.

---

### Post by tokyobadger on 2015-01-19
The official releases are Deepin 2014 and 2014.1 both of which I understand to be based on Ubuntu 14.04. Deepin 2014.2 is just RC and it's not so clear if it is still 14.04 based.

Next issue you're going to face asking for help would probably be the following "...it has also created its own desktop environment called DDE or Deepin  Desktop Environment which is based on HTML 5 technologies..." 

Finally from [Maggie says:]("http://planet.linuxdeepin.com/deepin-2014-2-released-free%C2%B7unique%C2%B7avant-garde/")[ January 7, 2015 at 3:32 am]("http://planet.linuxdeepin.com/deepin-2014-2-released-free%c2%b7unique%c2%b7avant-garde/#comment-65988")                  Sorry, we do not recommend to install NVIDIA, which will cause many problems.

I can tell you from experience that on an Ubuntu 14.04 and 14.10 that there were issues with the recent nvidia-drivers in upgrading both in Ubuntu provided repos and the xorg-edgers ppa's but as of this weekend there seems to have been a fix for the 346 drivers bumping them from .22 to .35 - the change manifest is worth a read.

Whether you'll get them to work on Deepin I really have no idea.

Best of luck

**EDIT:** It seems Deepin has at least the 346.22 (slightly buggy for installation but non-fatally) [link here](http://forum.cse.yzu.edu.tw/Linux/Deepin/deepin/pool/universe/n/nvidia-graphics-drivers-346/) - how you get that into your sources list I wouldn't know, maybe they'll update to the 346.35 soon

Deepin 2014.2 was released 31 Dec 2014 - my mistake

Since the Deepin Wiki does not yet seem to offer English instructions I had a quick browse of their forums and found [this thread on nvidia proprietary drivers on the OS](http://www.linuxdeepin.com/forum/8/27382) - might be good to join the discussion

---

### Post by contijn-buijs on 2015-01-20
Thanks for your answer. At the moment I got the older version working again and I also noticed in the Deepin store when searching for nvidia there was a install for nvidia-346. Seems the store only loads more content when you are at the bottom of the page. This confused me at first since I thought I reached the end.

At the moment everything works again and I'll hold off for now but I will try to see of the store version works correctly.

I assume the Deepin store version is slightly different then doing it from the terminal? How does these stores work on Linux anyway? Ubuntu also has a store and Mint, does Mint uses the Ubuntu store as source as well?

As for the forum link, I cant reach the page at the moment. I'll look there later.

---

### Post by tokyobadger on 2015-01-20
Good to hear that you have something working. As a gentle heads up, the ubuntu forums just like most distro forums are a place to share knowledge between users; developers rarely engage (based on several distros over nearly 20 years of linux use). All efforts to support fellow users are voluntary.

It may be that a ubuntu user has current/valid knowledge of other distros (eg multi-boot), but in 90%+ cases, the average visitor to these forums is not familiar/up-to-date with other distros no matter how similar they may seem.

If you want to use Deepin, I encourage you to seek support from their forums/community - I for one have no idea what they have done differently (other than basic info on DDE). The forum link I posted is working for me today. If you find a distro's support is not up to your needs/expectations feel free to move on.

---

