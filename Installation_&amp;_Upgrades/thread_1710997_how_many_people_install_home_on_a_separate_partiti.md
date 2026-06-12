---
title: "how many people install /home on a separate partition? bad idea?"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by nrundy on 2011-03-20
I've read several accounts of users who upgraded Ubuntu versions and ran into problems. I read that putting /home on a separate partition can make it easier to do upgrades. But it seems to me application versions and even the default applications themselves change so much between Ubuntu releases that I question whether it's a good idea to have all the "OLD" config files and settings that get stored in /home sitting around when running a new Ubuntu release.

Does anyone think it's a better idea to just put the whole Ubuntu install (i.e., /  and /home) on the same partition? And then when upgrading, backup, and then just fresh install everything (to get the cleanest possible installation)?

---

### Post by Sefianix on 2011-03-20
I always create a separate /home partition.  I've done it mostly for the reasons you mentioned: retaining all my old data.  I keep most of my .config files.  I do however delete my .kde* and .gnome* stuff.  [i don't remember specifig . folders... I just check when I do an upgrade.]  However, it's ALWAYS a good idea to backup all your important data before an upgrade in case something REALLY goes wrong.

I kinda wish wish Ubuntu did what Mint does: provide a utility to backup settings.  I haven't tried Mint's util but it sounds like a great idea.

---

### Post by nrundy on 2011-03-20
so you go thru your /home folder before upgrading and delete everything that begins with .gnome? How does the new .gnome stuff get resinstalled if you have /home on separate partition?

---

### Post by Sefianix on 2011-03-20
I either ssh in after an upgrade and before my first login under the upgrade and remove stuff that way.  [I always have SSH installed and I have several machines at home.]  Then when I log in after deleting those . files/folders, Gnome or KDE creates the new . stuff they need.  So far, I've not had problems.  YMMV.  I can't remember why I started doing it this way... maybe there was locked files if I'm already logged in??  

You could also do the Ctrl-Alt-F1 (or F2..F4) to get one of the terminals and log in from there.  I just use ssh b/c I get more columns of text so it makes reading easier for me.

Actually, once I screwed my gnome settings (can't remember what) and deleted my .gtk/.gnome stuff and logged back in... gnome recreated the . stuff and was back the default settings.  Only sucks that you have to re-customize your desktop.

---

### Post by mörgæs on 2011-03-20
A backup is only a backup if it is physically and electronically separated from the main system, for example a USB hard drive which is not permanently attached. 

Since I have this, I always do a clean install of a new release, and there is no need for a separate /home. 

Old configuration files often make more harm than good. I only keep xorg.conf, all other configuration files are flushed. After all it does not take long to configure the new system, and who knows... maybe your taste has changes or the new default settings are better than in the previous version.

---

### Post by Sefianix on 2011-03-20
Morgaes' advice is probably the best.  

However, it's doesn't always fit *every* situation.  I spent money for a TB drive and most of that is my home.  I've got lots of movies and music.  I'd like to keep it across upgrades if I can.  But it's not terribly important.  I do have a 60GB external USB so I backup my most important data.  But it's not going to fit all my lesser important data.  Thus, why I have a separate /home partition so Ubuntu installs don't wipe out all that data.  Like i said before, you should always make a backup of your important data regardless of whether you use a separate /home or not.

---

### Post by grahammechanical on 2011-03-20
The value of a separate home partition, in my opinion, is when you do something that messes up the OS. Then you can reinstall the OS without loosing your data or settings. So, you have to reinstall the programs as well but they pick up their respective dot files. And you are back to normal.

This proved valuable to me last year when my graphic card overheated. At the time I did not know the graphic card was the problem. By the time I worked out that I needed to replace the card I messed up the OS trying to fix things. In the meaning time the OS would only boot in low resolution mode. Then it would not boot at all. Live CDs when they loaded would not install. The answer was a new graphic card and a new install and everything was fine. Panic over.

Regards.

---

### Post by Bruce S on 2011-03-26
I also rely on a separate  home partition to avoid losing it if(or rather when) there is a disaster.

It is not difficult to partition for it so I would think everyone would do it.
Murphy"s Law is still valid after 60 years.:o

---

### Post by ottosykora on 2011-03-26
one more

yes me too, have home as separate partition. on most linux installs I have. Very handy when one time something got mesed up, I just could install the system over and had at least all data and also settings to this and that, internet, gpg keys and setup, mail setup, and so many other things ready just after installation.
While installation itself may take few minutes, this whole config thing is time consuming, takes often hours to transfer all needed things from other PC, and is simply here after reinstall. That makes it nice.

---

### Post by malspa on 2011-03-26
Another one here, I always install /home on a separate partition, even though I rarely upgrade, preferring to do fresh installations. 

It's mostly out of habit because that's how I've always installed Linux distros. But I figure it's painless and there might come a day when I'm glad I kept kept /home separate from /, so why not?

---

### Post by coffeecat on 2011-03-26
> **Bruce S said:**
> I would think everyone would do it.

Hmmm. No, everyone does not do it. A separate home partition has both advantages and disadvantages. A one size fits all approach is simplistic.

@nrundy, I think the answer depends on your situation. If you are running just one instance of Ubuntu which you upgrade and you do not have Windows, then a separate /home partition is a good idea.

If you dual-boot with Windows and you want to share data with Windows then you really need a separate shared data partition formatted NTFS, because it's a bad idea to regularly access your Windows C: partition from Ubuntu. If you have all your personal data on a shared NTFS partition then a separate /home partition is inefficient of disc space. You can always set up symlinks from your NTFS partition to your home folder. Of course, the disadvantage of not having a separate home partition in this situation is that you lose all your personal settings if you do a fresh install of Ubuntu rather than a version upgrade.

If you multi-boot with other releases of Ubuntu - I have Lucid, Maverick and Natty testing on separate partitions, then a shared home partition is a really bad idea. Goodness knows what Natty's /home configurations would do to Lucid's applications and desktop. :?

And if you multi-boot with other distros, then a separate home partition is going to be a real pain. Ubuntu sets the UID of the first account at 1000. Distros such as Fedora and PCLinuxOS to 500. You'll run slap into permissions hell.

---

### Post by Quackers on 2011-03-26
I have separate home partitions for all of my Linux OSes, but I'm having second thoughts now, as I really don't see too much of an advantage. If you don't have a separate home partition, you can always backup your home folder anyway.
Certainly in upgrades a separate home partition can cause more problems than it solves.
In future, I will not have a separate home partition, but will make more use of clonezilla - in case of disasters, I think :-)

---

### Post by malspa on 2011-03-26
> **coffeecat said:**
> And if you multi-boot with other distros, then a separate home partition is going to be a real pain. Ubuntu sets the UID of the first account at 1000. Distros such as Fedora and PCLinuxOS to 500. You'll run slap into permissions hell.

This is true, I've run into it with both PCLOS and Fedora. However, the fix was fairly painless -- here, for both distros, I just logged in as root and ran the following:

```
#usermod -u 1000 -g 100 [username]
```

Problem solved.

---

### Post by coffeecat on 2011-03-26
> **malspa said:**
> This is true, I've run into it with both PCLOS and Fedora. However, the fix was fairly painless -- here, for both distros, I just logged in as root and ran the following:

```
#usermod -u 1000 -g 100 [username]
```Problem solved.

Did you run into any configuration issues in /home configuration files with a mixture of Fedora, PCLinuxOS and Ubuntu? With Fedora going to gnome 3 and gnome-shell for F15, and Ubuntu going to Unity in Natty that could lead to some - um - fun with future releases! :)

---

### Post by mcduck on 2011-03-26
I don't keep a separate /home partition. There's too much stuff in /home that  actually *don't* want to keep through version upgrades or share between different installed distributions.

Instead I use a separate storage/data partition, and then link the directories from there into my home. This gives me pretty much all the benefits of separate /home partition without any of the downsides. :)

---

### Post by malspa on 2011-03-26
> **coffeecat said:**
> Did you run into any configuration issues in /home configuration files with a mixture of Fedora, PCLinuxOS and Ubuntu? With Fedora going to gnome 3 and gnome-shell for F15, and Ubuntu going to Unity in Natty that could lead to some - um - fun with future releases! :)

No, I don't share my /home directories between distros, and I use separate data partitions that I can access from each distro.

---

