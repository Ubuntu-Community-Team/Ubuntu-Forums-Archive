---
title: "Upgrade 14.04 &gt; 16.04 &gt;18.04: Software Updater cannot see new releases"
date: 2019-05-12
forum: Installation &amp; Upgrades
---

### Post by claudio-vda on 2019-05-12
Hello, I am experiencing a little problem while searching to update my old Ubuntu 14.04 to a more modern one. I have a desktop version.

The official guide says that in order to update Ubuntu 14.04 to 18.04 I need to pass via 16.04, so I followed the official instructions available [ here]("https://wiki.ubuntu.com/XenialXerus/ReleaseNotes") in order to update to 16.04. Unfortunately, when I come to the following point

[I]Software Updater should open up and tell you: New distribution release '16.04 LTS' is available. 

[/I]this is simply not happening at all: the Software Updater shows just a couple of minor updates but no new versions. Currently, we are in 2019 and not in 2014, so it is a little bit hard to me to understand why my Software Updater cannot realize that :?

May someone help me?

Thank-you very much in advance.

---

### Post by Dennis N on 2019-05-12
You have to update your 14.04 first or you won't get notified of the new version. The guide doesn't mention that from what I see.

In 14.04 set "Software and Updates" utility > updates tab: "Notify me of a new Ubuntu version: For long-term support versions".
Run "Software Updater" tool to update 14.04. You should see notification (see attached image) when updates are done:
Click "upgrade" and it goes to work upgrading to 16.04.

Example is from Xubuntu, but the Software Updater application is the same one as Ubuntu uses.

---

### Post by claudio-vda on 2019-05-12
Thank-you for your answer ;) 

Okay, basing on what you said, I guess I cannot proceed with the double version upgrade, but I have to freshly install Ubuntu 18.04 using a flash version.

I am currently using a non up-to-date version because last update caused a total block of the operative system (yes, version 14.04 starts to be REALLY old :) ), so I just went to an older one from GRUB menu in order to back-up my data and then update everything.

---

### Post by TheFu on 2019-05-12
14.04 repos are disappearing.  They were around 4 weeks ago. I moved 2 systems from 14.04 to 16.04 then.  I'm not ready to go to 18.04. I was moving servers, not desktops.

Have you considered that it might be easier to just do a fresh install 18.04 and move the settings/data over from 14.04?  For a desktop, it shouldn't be too hard. For servers, the complications depend on which server programs are needed.

Assuming you want to try the upgrade anyways, first, 14.04 needs to be fully up to date. This process updates the release tools.```

sudo apt-get update
sudo apt-get dist-upgrade
reboot
```
Fix any issues before moving on. Seriously. Fix any issues. The next steps require a current 14.04. If you are stuck on the issues, open a new thread here and post the 

Make a backup that you 100% know can be restored.  The following steps can break things, badly. Most of the time, it is ok, but not always. **Don't skip the backup.**  Hopefully, it will not be needed, but having insurance is good. The more PPAs used or manually installed .deb files, the more likely bad things will happen.

After the reboot, 16.04 upgrade should be available to the system. If it doesn't, then the upgrade config file probably is set to NEVER offer any upgrades. [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#Upgrading_from_Ubuntu_14.04_LTS_or_15.10](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#Upgrading_from_Ubuntu_14.04_LTS_or_15.10) explains. You can change that, but manually running the next command should still work. Login on the console, not over a network connection.
```
sudo do-release-upgrade
```
This process removes PPAs, modifies the repositories to point to the next LTS and begins the upgrade process. Depending on the packages, dependencies, network speed, this can take 10 min or 3 hours.  

After it completes successfully, do everything again for 18.04. Do not skip the backup step.  If it didn't go perfectly, fix any issues first.

Upgrades often leave cruft behind and complicate things that have changed over time.  For example, the network configuration has drastically changed since 14.04. SystemD has been added.  18.04 uses snaps much more often than previously used. 14.04 doesn't do snaps at all. Apache, DBMS, Php, and other server tools have all changed over this time.  Manual changes are necessary for those migrations, regardless.  I remember the apache 2.2 to 2.4 migration vaguely. It wasn't automatic.

BTW, the GUI is completely different between 14.04 Unity --> 16.04 Gnome3 --> 18.04 Gnome3 apps inside snaps.

I'm running 16.04 on my desktop and laptop still. In another year, I'll look to see if 18.04 is an option.

All these words make it seem harder than it will likely be. Just work 1 step at a time, stop if anything fails at any point.

---

### Post by claudio-vda on 2019-05-12
> **TheFu said:**
> 
Have you considered that it might be easier to just do a fresh install 18.04 and move the settings/data over from 14.04?


This is my favorite option. Next week-end I am going to to that ;)

> **TheFu said:**
> 
BTW, the GUI is completely different between 14.04 Unity --> 16.04 Gnome3 --> 18.04 Gnome3 apps inside snaps.


I was really comfortable using Gnome in past versions, e.g. 7.04 or 10.04, so I am really happy about the fact that Gnome is back ;)

---

### Post by TheFu on 2019-05-13
> **claudio-vda said:**
> This is my favorite option. Next week-end I am going to to that ;)

I was really comfortable using Gnome in past versions, e.g. 7.04 or 10.04, so I am really happy about the fact that Gnome is back ;)

Those were gnome2.  Gnome3 is completely, unrecognizable, different, when compared to gnome2.

There is good news.  You don't have to use Gnome3. There are many different GUIs, some are based on Gnome2 like lxde, Mate, Xfce, and a few others.   They have the added benefit of not being as GPU and RAM intensive.
* Ubuntu-Mate is what I like for noobs. It is much lighter than either KDE or Gnome3 versions, but still pleasing.
* LUbuntu is LXQt ... I think in 18.04.  The 16.04 version is LXDE.  That is because they changed from the Gnome2 GTK toolkit to the KDE Qt toolkit.
* XUbuntu is XFCE for both. Think this is based on Gnome2.

I don't use any DE, just a window manager, which saves about 200MB of RAM use, in trade for less "pretty" menus.  Actually, my setup doesn't have any menus, but that's a personal decision.  

I miss 10.04.  That was the last LTS from Canonical that didn't do anything "funky" to be different. It was Linux the way that Linux was meant to be, IMHO.  Since then, every release has broken something important to me or made it unnecessarily complex in the name of noob-useability.  

To move your settings and data, for most people, they just need to move their HOME directory.  Normally I'd suggest looking at a tool like aptik, but it wasn't working on 14.04 and moving between 4 years of updates, any non-standard application is likely to break compatibility in the data files.  Use a normal backup tool, like rdiff-backup or back-in-time or even rsync to get the data you want off, then start fresh.  

If you make a list of manually installed packages on the current system, then most of those can be batch installed on 18.04 with a few commands.  They will find the prior settings, since you'll restore your HOME directory and should migrated any settings and just work.  That's the theory.  I use it all the time to move systems.  The command is ... let me find it in my backup script:```

 aptmark showauto | tee $local_backup/apt-mark.auto
 aptmark showmanual | tee $local_backup/apt-mark.manual
```
Later, on the new system you'll take those lists of manually installed packages and feed them in and batch install.
```
######[ to restore pkgs ]#######
### sudo apt-mark auto $(cat apt-mark.auto)
### sudo apt-mark manual $(cat apt-mark.manual )
### sudo apt-get -u dselect-upgrade

```
I capture the automatically installed packages too because it is small and I might need it it, but I never have. You can ignore that part (the lines with "auto" in them).
Be certain to include the file containing the list into your backup storage. ;)  Having the data, then wiping it isn't useful. ;) It needs to be on different media, right?  I meantion this because in my early stages of doing backups I was capturing all sorts of data about the system, packages, configs, etc. and storing it into a directory that wasn't actually included in my backup or restores.

---

### Post by rsteinmetz70112 on 2019-05-13
I don't know if the repositories for 14,04 are still available but,

 if  ```
sudo apt update
sudo apt upgrade
``` work, they are still available.

---

