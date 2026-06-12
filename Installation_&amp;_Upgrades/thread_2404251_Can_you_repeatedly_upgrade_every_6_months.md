---
title: "Can you repeatedly upgrade every 6 months?"
date: 2018-10-22
forum: Installation &amp; Upgrades
---

### Post by Ice-Tea on 2018-10-22
Has anyone successfully upgraded every 6 months on top of their old release and kept their current setup and configuration without needing to do a fresh install?

I love Ubuntu but not being a rolling release is annoying and LTS gets old.

---

### Post by hackerb9 on 2018-10-22
I'm curious about this as well. The Debian-Testing model seems to work well for a lot of people. 

By the way, I'm posting this from a laptop that started with Dapper Drake that has never been wiped with a fresh install. It's been release upgraded every so often, mostly at LTS points, and is now on Cosmic Cuttlefish. It's surprising to me how little reconfiguration I've had to do.

---

### Post by dino99 on 2018-10-22
A Dapper rolling upgrades, wow, what a long experience; and you are still curious  :D;):D:lolflag:

But how can you change your old EXT2 partition to a more modern one ? or adapt to some heavy transitions of the structure scheme itself ?
Yes it is possible, you are the skilled one proving it is possible, but just a few users successfully have done it without hitting a major problem alongside.
I myself started with Dapper, so long time ago, but i do a fresh install with all the coming LTS, even if canonical have made a huge progress in quality, testing inside before publishing updates since Lucid or so.

---

### Post by Impavidus on 2018-10-22
You can upgrade every 6 months, but it doesn't always work for everybody. I've got one old computer on which I originally installed Dapper Drake. It was upgraded LTS to LTS until it ran Trusty Tahr with hardly any config changes. At one point I had to manually fix networking, at another point I had to upgrade grub legacy to grub 2. By then it had accumulated enough cruft that I made a backup of the /home directory and did a fresh install of Xenial Xerus, at the same time moving from ext2 to ext4 (or is it still ext3? I may have to check that). It's now been upgraded to Bionic Beaver. On my main laptop I usually do one fresh install followed by 3 upgrades, then keep it at an LTS release as backup system. I dual boot the latest release and the LTS release before the latest.

---

### Post by hackerb9 on 2018-10-22
> **dino99 said:**
> A Dapper rolling upgrades, wow, what a long experience; and you are still curious  :D;):D:lolflag:

I'm still curious because I don't know how hard it would have been if I had set my system to automatically update every six months. As a guess, I think that by mostly jumping from LTS to LTS, I saved myself a lot of pain.

> **dino99 said:**
> But how can you change your old EXT2 partition to a more modern one ? or adapt to some heavy transitions of the structure scheme itself ?

I'm pretty sure I didn't use EXT2 for Dapper, since EXT3 had been out five years prior. Still, you're right, I'm using EXT4 now, so I'm trying to remember how I did it. Likely it was when I put an SSD in and copied the files over using something like [FONT=Fixedsys]rsync -avPCHAX  /  /mnt[/FONT].  That's not something I'd expect most Ubuntu users to do (particularly installing grub in a chroot), but I don't think they'd have to. EXT2 or 3 would still be working just fine since Ubuntu doesn't care what the underlying filesystem implementation is.  As for major changes in the structure scheme (init.d to upstart to systemd), I don't recall having any trouble. There were some hassles with the APM / ACPI implementation in certain Linux kernels, but that's more a problem of this particular computer than something everyone would face.

> **dino99 said:**
> Yes it is possible, you are the skilled one proving it is possible, but just a few users successfully have done it without hitting a major problem alongside.


Oh! :o That's good to know. I had presumed that most Ubuntu users went along with the LTS updates. I used to have a policy of always doing a fresh install to a new hard drive for any OS upgrade, but that was long, long ago.

I've used Debian GNU/Linux on my main computers since well before Ubuntu existed, and it's still my distribution of choice. But when people (usually coming from Microsoft Windows) ask for my advice on what to run, I usually recommend Ubuntu since it seems more polished, with friendlier documentation. (And of course, there's this helpful forum!:KS) As you point out, I am skilled, so I know my judgment may be out of wack. That's why I started running this laptop: if I'm going to be recommending Ubuntu, I ought to know what I'm throwing Unix-innocents into. (Or, as Unix admin Dorothy Parker might say, *"What fresh shell is this?"*) ;-)

---

### Post by dino99 on 2018-10-22
Keep your curiosity on, its a healthy trend   :p

---

### Post by RobGoss on 2018-10-22
It would be great if Ubuntu was a rolling release, This way we won't have room worry about loosing data

I've moves to other rolling release to see how it works

---

