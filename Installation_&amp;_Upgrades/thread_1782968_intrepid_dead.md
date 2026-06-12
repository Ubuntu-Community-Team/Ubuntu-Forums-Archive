---
title: "intrepid dead?"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by Arijan on 2011-06-15
Since ATI dropped support for a number of graphic cards, I've been stucked with kernel 2.6.27 on my laptop with integrated gcard, because proper 3d is a must, and open source drivers are not sufficient. Currently I have Ubuntu 8.10, but been using Open Suse 11, Fedora 10 (and couple more, all with old kernel). 
But for a while I am not able to use 8.10 because the repos are dead (I thought that only security updates will be terminated, not majority of standard 8.10 compiled packages, as it appears); so my Ubuntu Intrepid is dead, for I cannot install anything, except what I have on initial cd and some major packages from the part of repos that are still alive somehow.

So what's going on exactly? Some repos are there, and majority are gone.
Is there any alternative that I can try with crappy hardware (crappy vendor more precisely) I have here?
Has anyone succeeded downgrading to intrepid kernel from newer ubuntu (9.10 or even 10)?
Is there any solution?

Thanks in advance

---

### Post by coffeecat on 2011-06-15
Intrepid has been effectively "dead" for more than a year now, since 30th April 2010 to be precise, when it became unsupported. It was not an LTS so it was supported for 18 months only.

You say the open source driver was not sufficient. I guess that means that you want the Intrepid kernel for the 2008 version of the catalyst/fglrx driver. You'd need the 2008 version of the xserver as well, so getting that combination to work in a later version of Ubuntu would fall somewhere between a nightmare and an impossibility, I would guess.

However, your experience of the open source ATI driver is an out-of-date one. It has been developed enormously since 2008 and there is a fair chance that 3d is supported in your card with the version of the open source driver that comes with recent versions of Ubuntu. The important question is: which ATI graphics chipset do you have?

---

### Post by Arijan on 2011-06-15
Thanks for reply.

I'm afraid my open source ati driver experience is not so outdated since I've been trying that stuff with newer kernels on Ubuntu, Debian, Fedora, Suse, all of them with Radeon based on Gallium - the case with those is, desktop effects are ok (which I never use), and even Blender can somehow pass, but that's the end of "stretching" - beyond that, there's only a visual mess...

My chipset is Ati Mobility Radeon Xpress 1200. I know I can't expect a lot of this low-end hardware, but all was doing fine until ATI screwed a big time.

I know that downgrading to older kernel and Xorg is a mess (it only worked once with Suse: from 11.1 to 11 - but that's another story), I don't expect it to work on Ubuntu, nor even Debian, for this is a huge gap between kernel versions.

Well, I knew there's no hack to this, but I hoped something new came up.
So waiting for open source driver improvement, or new hardware, or bye bye 3d.

And in the end there is a possibility to download all ubuntu 8.10 packages in a several dvd-s

---

### Post by TBABill on 2011-06-15
The PCLinuxOS 2010 iso (201012) has an older xorg version than ubuntu and is just now going through an update. Can you download that iso and give it a try with your card? You may find they have support for older cards still. Just a thought...hope you find what helps.

---

### Post by Arijan on 2011-06-15
Definitely worth trying! it appears the Xorg is even older than Intrepid's, and the kernel is new. Very interesting; just have to see if everything else works - it could save the mission.
Thanks a bunch!

---

### Post by Arijan on 2011-06-16
Absolutely no luck!

I dedicated whole day to PCLOS 2010 usb live, hoping that it will work in this particular issue. 
fglrx is installed by default but not in use - mesa was running instead. And while I was repairing it in xorg.conf, I suddenly realized I was wrong : xorg isn't that old in this distro version - it is 1.6.5 (and Intrepid has 1.5.2), and further, fglrx version is 8.8 with catalyst 10 - which is specifically pointed out by ATI that will not support legacy cards (last catalyst for legacy is 9.3)

So I could be sure there is no way this can be solved with old fglrx and newer kernel. 
It's a damn dead end - I can't believe the both important things are failing here: ATI support, and Intrepid's repos (which are false and uncompleted) - all other Ubuntu versions are there (not supported, but ARE there) even 6, 7, but not Intrepid! 

Edit:

At least I found working Interpid repos, I thought they were incomplete because of the address :
[http://old-releases.ubuntu.com/ubuntu/dists/intrepid/](http://old-releases.ubuntu.com/ubuntu/dists/intrepid/) 
and it should be :
[http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid
as it sais in this thread:
[http://ubuntuforums.org/showthread.php?t=1758218](http://ubuntuforums.org/showthread.php?t=1758218)

---

