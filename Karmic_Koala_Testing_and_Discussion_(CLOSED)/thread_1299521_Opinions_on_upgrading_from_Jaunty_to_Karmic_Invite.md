---
title: "Opinions on upgrading from Jaunty to Karmic Invited"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by annie227 on 2009-10-24
I'm relatively newish to Ubuntu,been using/learning about it for a solid 6 months at least and am loving it.
I dual-boot Jaunty and XP,having tried going soley with Jaunty but found it better for me at this stage to have XP and all its programs as back-up for when I'm in over my head or lack time to learn a new 'thing".I love linux and have found myself checking the date,with the release of Karmic drawing closer,I'm going to install it no doubt.
Now,I want to know what other people intend doing and/or what they'd advise
-upgrade to 9.10 from 9.04 or clean install 9.10?
-install 9.10 on its own partition and keep 9.04 until such time...?
-should I triple boot Jaunty,Karmic and XP?
Will this official release of karmic be much different to what's available today to download?
Thanks very much for any replies,I'm very keen for opinions.

---

### Post by Dark_Stang on 2009-10-24
Directions for an upgrade can be found here...
[http://www.ubuntu.com/getubuntu/releasenotes/910overview](http://www.ubuntu.com/getubuntu/releasenotes/910overview)

However I always do a clean instal out of habit when I'm upgrading. That way I know it's all fresh and I don't have to worry about anything. The main differences will be... everything is newer. New inferface, new kernel, new everything. The official release won't be much different from what's out there right now, if at all.

I wouldn't bother triple booting... It just doesn't seem needed.

---

### Post by Paqman on 2009-10-24
Up to you. An in-place upgrade is definitely the easier option, but reinstalling would allow you to switch to ext4, which is a big part of Karmic's improvements.

---

### Post by annie227 on 2009-10-24
Thanks Dark_Stang and paqman,good to know.
I wont be triple booting,(just curiosity)
I'm happy with my current installation that's why I'm considering upgrading(plus I've never done it)
but I'm wondering whether if there'd be an issue with the ext 4 thing and it appears there will be

---

### Post by MelDJ on 2009-10-24
upgrade to 9.10 from 9.04 or clean install 9.10?

upgrade if you want to keep your files in the computer
clean install if you dont really have many files.

---

### Post by misfitpierce on 2009-10-24
As said this is one release I would recommend a fresh install and not an upgrade. It by default installs using new filesystem which is EXT4 instead of EXT3 which has great speed improvments on reading and writing and if you upgrade the default on 9.04 was EXT3 and it will not upgrade filesystem format. So I recommend a fresh install for this one!

---

### Post by emigrant on 2009-10-24
my jaunty is already in ext4, so upgrading is the right thing right?

---

### Post by mivo on 2009-10-24
As I never had an upgrade work for me flawlessly, I would recommend a clean reinstall. If you have a separate /home, this shouldn't take much time, though. :)

---

### Post by mapes12 on 2009-10-24
> **mivo said:**
> As I never had an upgrade work for me flawlessly, I would recommend a clean reinstall. If you have a separate /home, this shouldn't take much time, though. :)**+1**

and here's how to create a separate /home 

[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

---

### Post by tuahaa on 2009-10-24
What I would do is make a new partition for Karmic. The benefits are that 1) Fresh install, 2) You can access the data from other partitions (In my case atleast) and 3)You can delete it if you don't like it- but make sure you can still boot into the other OS's after you get rid of it!

---

### Post by amosmj on 2009-10-24
for all those folks that do a clean install each time. Is there a quick, possibly command-line, way to get all the apps you used to have, get your desktop the way you like and your task bar?

---

### Post by Dark_Stang on 2009-10-25
> **amosmj said:**
> for all those folks that do a clean install each time. Is there a quick, possibly command-line, way to get all the apps you used to have, get your desktop the way you like and your task bar?
If you keep you're /home directory on a separate partition none of that gets erased as long as you don't reformat that partition. I've been doing that since about... 5.10? Ran that on my Acer laptop, coppied it over to this laptop, and I'm up to 9.04 now.

---

### Post by autark on 2009-10-25
> **Dark_Stang said:**
> If you keep you're /home directory on a separate partition none of that gets erased as long as you don't reformat that partition.

That will take care of preserving your personal files. To keep the selection of installed packages, you need to make a list of your current package selection and use that list in your fresh installation. I can never remember the commands to do this but I'm sure somebody can fill me in. 

If you have made changes to configuration files in /etc and possibly other places, I don't know of any other way than to manually carry over your changes from the old installation to the new one. That is, if you can remember which files you have altered.

---

### Post by KrazyPenguin on 2009-10-25
Here is what I do:
1.Adding Additional Software

Goto Ubuntu Tweak website and install key and edit sources.list according to instructions.
Install using ubuntu tweak APPLICATIONS --- audacious, compiz-config-settings-manager, deluge, exaile, getting things gnome, gmail notifier, google earth, mplayer, screenlets, skype, ubuntu-restricted-extras, virtual-box, vlc player, wine
Install using ubuntu tweak THIRD PARY SOURCES: --- Experimental Gnome Games, medibuntu, Ubuntu Tweak 
Install System &#8594; Nautilus &#8594; “Nautilus with Root Privileges”

Install additional software from repositories: (Split into 2 – high priority and low priority)

High Priority Software
sudo aptitude install bootchart exaile flashplugin-nonfree keepassx libdvdcss2 mplayer mplayer-fonts mplayer-skins speedcrunch  thunderbird ubuntu-restricted-extras ubuntu-tweak vlc w32codecs wine 
Medium Priority Software
sudo aptitude install acidrip amsn bum community-themes compizconfig-settings-manager deluge-torrent easycam2-gtk emerald giver gnome-themes-extras googleearth-package gparted grsync gufw kmymoney2 msttcorefonts nautilus-image-converter rar screenlets skype startupmanager streamtuner subversion timer-applet virtualbox-ose wallpaper-tray xdiskusage
Low Priority Software
sudo aptitude install  burgerspace  lbreakout2 monkey-bubble neverball openarena pinball
 
Frostwire – not is repos, goto website and install deb – need ubuntu-restricted-extras (above)
		(In Karmic Frostwire was successfully installed off website!!!)



Truecrypt – install from website

I just keep this list handy, and once in a while add or remove a program from it.  Of course the packages you use will be different.

---

### Post by mivo on 2009-10-25
> **autark said:**
> To keep the selection of installed packages, you need to make a list of your current package selection and use that list in your fresh installation. I can never remember the commands to do this but I'm sure somebody can fill me in.

```
dpkg --get-selections > installed-software
```

For more details, see here: [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

---

### Post by KrazyPenguin on 2009-10-25
> **annie227 said:**
> I'm relatively newish to Ubuntu,been using/learning about it for a solid 6 months at least and am loving it.
I dual-boot Jaunty and XP,having tried going soley with Jaunty but found it better for me at this stage to have XP and all its programs as back-up for when I'm in over my head or lack time to learn a new 'thing".I love linux and have found myself checking the date,with the release of Karmic drawing closer,I'm going to install it no doubt.
Now,I want to know what other people intend doing and/or what they'd advise
-upgrade to 9.10 from 9.04 or clean install 9.10?
-install 9.10 on its own partition and keep 9.04 until such time...?
-should I triple boot Jaunty,Karmic and XP?
Will this official release of karmic be much different to what's available today to download?
Thanks very much for any replies,I'm very keen for opinions.

Karmic is still a little buggy, so if you don't mind breakages, etc, then go ahead and upgrade to karmic.  But if you have a working jaunty and your happy with it, then really no sense upgrading to karmic.

If you do upgrade i would recommend keeping jaunty on the system, in case you wish to go back.

---

### Post by dino99 on 2009-10-25
don't forget to use recent formatting tools; the best i'd used is parted magic.

Remember too, some apps run outside your /home ( i know it's silly) like boinc; if your crunch is on the way, wait to upload them before formatting  :(

---

