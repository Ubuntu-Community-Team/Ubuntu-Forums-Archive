---
title: "Could not download all repository indexes"
date: 2011-01-18
forum: Installation &amp; Upgrades
---

### Post by missfroguk on 2011-01-18
Hi,

I'm trying to upgrade from 9.10 to 10.04 but I'm having the following error message when I try and update:

[HTML]Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch http://www.stats.bris.ac.uk/R/karmic/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.[/HTML]

Could somebody tell me what to do next please?

---

### Post by JC Cheloven on 2011-01-18
It seems the server it's down, or don't have the packages right now. 

Please check if you can install any program in the usual way from the repository.

BTW, I always do fresh install instead of upgrading. I think it's less prone to errors.

---

### Post by missfroguk on 2011-01-18
Hi,

Yes, I can download packages the usual way.
I have checked and the page [HTML]http://www.stats.bris.ac.uk/R/karmic/Packages.gz[/HTML] does not exist. Should I change the address in my /etc/apt/sources.list file? At the moment I have
```

deb http://www.stats.bris.ac.uk/R/ karmic/

```

I actually installed R recently and I wonder if I have made a mistake or something. Hard for you to know I guess. Should I try to uninstall R see if it sorts things out?

Thanks.

---

### Post by JC Cheloven on 2011-01-18
Double post, sorry. The forums are running strange today :/
Please see the following one.

---

### Post by JC Cheloven on 2011-01-18
Sorry, I assumed this line belonging to an ubuntu mirror, but I guess it's some special repository you added for a particular statistical software, called "R". Right?

So, you can you comment that line in /etc/apt/sources.list (that's, put a # sign at the beginning of the line), save it, and run "sudo apt-get update".

After that, the upgrade to 10.04 should perform as expected. 

Later on, I dunno really whether that line in the sources.list is required or not, or advidable for keeping up to date that "R" software. You'd know better, after reading the manuals for that app. Anyway I see binaries for lucid and even maverick in the page [http://www.stats.bris.ac.uk/R/](http://www.stats.bris.ac.uk/R/)
(so, no worries: in fact I'd suggest to simply install the binaries if you trust on them, and let aside your sources.list file)

Hope to correctly understand your situation.

---

### Post by missfroguk on 2011-01-24
Thank you JC, I have no problem with my updates anymore. 

Let me know if you want me to post this somewhere else though but although my system is updated, I'm not offered the upgrade to 10.04. Any idea why this is happening?
Can I upgrade it another way (i.e. not via the update manager) without having to do a clean install of 10.04?

Thanks.

---

### Post by JC Cheloven on 2011-01-24
> **missfroguk said:**
> (...) although my system is updated, I'm not offered the upgrade to 10.04. Any idea why this is happening?
Can I upgrade it another way (i.e. not via the update manager) without having to do a clean install of 10.04?

Probably your system is configured so that it doesn't offer distribution upgrades. Please open Administration- Software Sources, go to the Updates tab, at the bottom where it says "show new versions of the distribution", choose "LTS editions only". Close that.

Now, if you open Administration- updates, you should be greeted with an option to upgrade to Lucid at the top.

Regarding the terminal approach: I'm unsure whether ```
sudo do-release-upgrade
``` would bring you to Lucid or to Maverick. The man page says "Upgrade  the  operating  system  to  the  latest  release (...)". I don't have a 9.10 machine at hand right now, but you can find out by running (this will not make any actual change in your system, thus no need for sudo) ```
do-release-upgrade -c
```

EDIT: checked in a karmic machine this morning. The option -c was not yet implemented at the time. But you can use -s and abort when you're prompted for your password. I did, and it seems do-release-upgrade will install Lucid (not maverick), so you should be ok.
[INDENT]BTW: I always do fresh installs. I think it's less prone to errors.[/INDENT]

---

### Post by missfroguk on 2011-01-30
Finally ready to upgrade, I thought, but I'm a bit puzzled as I get  
```
sudo do-release-upgrade
[sudo] password for missfroguk: 
Checking for a new ubuntu release
No new release found

```

I have had problems with grub a few months ago so I wonder if this puzzled the system a bit and for some reason can't get the new releases (see this thread for details [http://ubuntuforums.org/showthread.php?t=1612068]("http://ubuntuforums.org/showthread.php?t=1612068")).

Regarding re-installing rather than upgrading. I have a dual boot machine and I wonder if this may complicate things a bit. I'm worried that if I reinstall rather than upgrades I'll get into complications and mess up with Ubuntu and windows. You may disagree and convince me!

---

### Post by JC Cheloven on 2011-01-31
So, did you gave a try to the first thing (enabling upgrade-checking from the software sources dialog?)

> **missfroguk said:**
> Regarding re-installing rather than upgrading. I have a dual boot machine and I wonder if this may complicate things a bit. I'm worried that if I reinstall rather than upgrades I'll get into complications and mess up with Ubuntu and windows. You may disagree and convince me!

:lolflag: You asked for it.
If for anything at all, I'm notorious over here for choosing the easier and safer solution when possible, rather than the more savy-oriented, usually more complicated, one. Sure we would learn more pursuing the problem and finding "the smart solution", but usually I don't have neither the deep knowledge nor the patience/inclination to do so. Here my thoughts:

- In my **experience**, upgrading can be way more problematic than fresh installing. To speak only about recent dates, I've done in 2010 over 40 fresh installs in dual boot (most of them at other people's pc's), and never had a single problem with grub not catching the win2 boot, or the like. The only upgrade I tried (in one of my machines) messed up some packages I had installed manually. Similar experience in previous years btw.

- You have an old, several-steps-backwards version of ubuntu (although jaunty was awesome at the time though). You also had problems with this install before. Whether those problems are related with your current situation or not, is, IMHO, something difficult to know, and which isn't worth to be worked out. Because there is a safer and simpler solution.

I can't offer 100% guarantee of course, but if you try maverick in live and it works (or lucid for that matter), you back up your important data, and you make the fresh install properly, I'd expect a complete success.

But it's up to you, of course. And a marginal risk is always present (whatever you do). But if you decide to install, don't hesitate to come back here for guidance, if needed. 

Cheers
JC

---

### Post by missfroguk on 2011-02-01
> So, did you gave a try to the first thing (enabling upgrade-checking from the software sources dialog?)
Yes I did but it didn't work.

> You asked for it.
If for anything at all, I'm notorious over here for choosing the easier and safer solution when possible, rather than the more savy-oriented, usually more complicated, one. 
Sounds good to me...You win, I'll try and install 10.04 from scratch making sure I back everything up, trying Maverick live first. Actually, I wonder if I may as well wait a couple more months and wait for the next LTS...

Anyway, thank you for everything and I will post back on the forum if it is a disaster!

---

### Post by JC Cheloven on 2011-02-01
> **missfroguk said:**
> Sounds good to me...You win, I'll try and install 10.04 from scratch making sure I back everything up, trying Maverick live first. Actually, I wonder if I may as well wait a couple more months and wait for the next LTS...
Nice. Surely you think it's more complicated than it actually is. I'd like this to be a real success for you, and something to learn from for future occasions. So, first of all, please don't get into confusion:
[INDENT]- The last LTS release is Lucid Lynx 10.04. It has support until april 2013.
- There will NOT be another LTS release until april 2012.
- The current release, Maverick Meerkat 10.10, has support until april 2012 (yes, "eventually" the same as the release date of next LTS).[/INDENT]
So, next you should:
[INDENT]- Choose either Lucid or Maverick, based on your preferences and in what works better in your pc. You could try them both in live. It's cheap ;)
- Find out what your current partition scheme is, to identify where your current Ubuntu is installed. If unsure, please post back the output of "sudo fdisk -l", either from your current jaunty install or from live (doesn't matter). 
- Boot in live with the choosen release, and install in the partition of your old ubuntu. At the time of partitioning, I'd choose "advanced", to have some more control. Eventually, during the process you may want to format the ubuntu partition to ext4. And you should have already a swap partition, use that (it's the default option anyway). As to the rest, you should be fine with the defaults. 
NOTE: all data in that partition will be erased. You should backup before all relevant data.[/INDENT]

Finally, "just in case it inspires", I tell you my own setup: I have win2 in the first primary partition (seldom used), and then several logical partitions. One for the current ubuntu version I'm using, one for the previous version I used, one bigger one for my data (which may be accesed from every OS, it's in fact a separate second internal disk).
This way I have always a fallback old well known system if something goes wrong with the newer one. Rarely, if ever, happened till now though.

> Anyway, thank you for everything and I will post back on the forum if it is a disaster!

I hope not ;) Of course you're welcome if I can do anything else. I feel somehow engaged to yor new install :p

Best
JC

---

### Post by missfroguk on 2011-05-29
Hello, 

I finally have time to install 10.04.

> Find out what your current partition scheme is, to identify where your current Ubuntu is installed. If unsure, please post back the output of "sudo fdisk -l"

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4060102a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       19628   156122108    7  HPFS/NTFS
/dev/sda3           19628       29353    78110988    7  HPFS/NTFS
/dev/sda4           29354       38913    76790700    5  Extended
/dev/sda5           29354       38913    76790668+  83  Linux

```

> Eventually, during the process you may want to format the ubuntu partition to ext4. And you should have already a swap partition, use that (it's the default option anyway). 

Ok, you've lost me! According to the output above, which partition should I set up Ubuntu in? I don't know what a swap partition is...I also like your idea of having my old version of Ubuntu in a different partition as a back-up, but I don't know how to do this.

Thanks!

---

### Post by JC Cheloven on 2011-05-30
Hi, glad to hear from you! :)

So, you have one hard disk, with the following:

- A small partition of 'unknown' type, probably set by the manufacturer for system testing apps or something similar. 
- Two NTFS windows partitions, one big (~140Gb) where probably your win2 lies, and a second one (~75Gb), you should know for what purpose.
- And extended partition with a linux partition in it (~70Gb).
- You have no swap space.

You have several possibilities, depending on how you are using the NTFS partitions. Here some ideas:

- Please, first backup all your important data. Messing with partitions always has some risk.
- To set up partitions in a disk you have to boot from somewhere else (i.e, from a live cd session). The way to go is to choose the ubuntu version you decided to install, and boot in live with that.

SCENARIO 1: YOU WANT TO REPLACE YOUR CURRENT UBUNTU WITH THE NEW ONE.

- From live, start gparted (program to set up partitions), wipe the /dev/sda5 partition (apply changes), create a swap partition of about 500Mb (or as much as your ram, or even more if you plan to hibernate) using some of the free space left (apply changes), and then create an ext4 partition with the rest of the free space left (apply changes). 

- The ext4 partition should have been named /dev/sda6. Check that using the "sudo fdisk -l" command (as in your previous post), and then go install in that sda6 partition. You should choose "advanced" when asked for partitions by the installer.


SCENARIO 2: YOU WANT TO KEEP YOUR CURRENT UBUNTU ALONG WITH THE NEW ONE.

- Start from live & gparted as before.

- You could shrink your current /dev/sda5 partition to a little less than a half (if it's currently 70Gb, shrink it to ~32 Gb). That's only possible if there is enough free space in your sda5, of course. Then use a little of the obtained space to set up a swap partition, and the rest to create an ext4 one, in which you can install the new ubuntu later on.

- ALTERNATIVELY, you could take the opportunity, and reconsider how you are using your whole disk. For example, a possible setup (tailored for your situation) would be: ~1.5Gb to keep untouched your current /dev/sda1, ~58Gb NTFS for win2 (the result of shrinking your current /dev/sda2 partition, if my guesses are correct), ~200GB NTFS for your data (to be accessed from Windows or Ubuntu at wish), extended of the rest of the space, and inside that ~25Gb ext4 for UbuntuV1, ~25Gb ext4 for UbuntuV2, and ~500Mb for some swap space. 

If you are interested in the last "ALTERNATIVELY" possibility, some previous checking would be needed (to see where your windows actually is). The eventual shrinking of the win2 partition is better done from within win2 itself, after taking out as much files as possible (its destination will be the big data partition afterwards), and after a defragmentation.

Hey, I wrote a manual :)
Hope this helps

PD.- perhaps you're right in that it shoud be better to start another thread for the follow up of this. If needed, please do it and post here a last one with a link, so that I can be aware.

---

