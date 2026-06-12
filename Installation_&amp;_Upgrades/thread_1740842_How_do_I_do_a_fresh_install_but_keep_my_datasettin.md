---
title: "How do I do a fresh install but keep my data/settings/configurations/browser info?"
date: 2011-04-27
forum: Installation &amp; Upgrades
---

### Post by Elludium_Q-36 on 2011-04-27
I have a box that is offline and I want to keep my configurations/data/settings/browser info, etc. so there's no need to download and do everything over.

The reason I need to do a fresh install is that I added 10.04 packages from a CD to an 8.04 system and it now won't take alternative CD upgrades with the cdromupgrade script.

The packages refuse to downgrade via the "force version" option.

I have:
*Backed up my keys with command "sudo apt-key exportall > ~/repositories.key"

*Backed up "sources.list" file and "sources.list.d" folder.

I'm told I can back up the "archives" folder so I don't have to redownload all the packages.

It didn't work for me but I've read I can back up program/package configurations with commands: "dpkg --get-selections "*" >myselections" and "debconf-get-selections > debconfsel.txt"

How do I back up the Firefox profile directories.

I have been told about Keryx keryxproject.org and Remastersys but I think I need to do it old school this time.

Thanks in advance

---

### Post by falko on 2011-04-27
Do you have a separate /home partition? In this case you can just re-install Ubuntu and tell the installer to **not** format /home.

---

### Post by Dutch70 on 2011-04-27
Also, check here for more info.
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1580857[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1580857")

---

### Post by Elludium_Q-36 on 2011-04-29
Thanks but I have already backed up the /home/ and /etc/ directories.

I'm looking for help on the rest:

> 
I'm told I can back up the "archives" folder so I don't have to redownload all the packages.

It didn't work for me but I've read I can back up program/package configurations with commands: "dpkg --get-selections "*" >myselections" and "debconf-get-selections > debconfsel.txt"

How do I back up the Firefox profile directories.

I have been told about Keryx keryxproject.org and Remastersys but I think I need to do it old school this time.

Thanks in advance



The box is offline on "sneakernet" so I need help backing up what's already on-board.

---

### Post by dino99 on 2011-04-29
dont use the installer, its too scary; make a manual install following the help below. If you dont format your existing /home, there is no need to backup your data/settings

here is how to install:


use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by Elludium_Q-36 on 2011-04-30
Thanks but I'm not really in need of repartioning.

I need to reinstall because of bad packages held.
I added packages from a 10.04 CD to an 8.04 system :o<

I'm offline so need to save the downloaded package files and it would be nice to keep my configurations and settings, along with the data...

---

### Post by dino99 on 2011-04-30
" I added packages from a 10.04 CD to an 8.04 system " very bad idea

so reformat to do a clean install, that it

---

### Post by Elludium_Q-36 on 2011-04-30
Right, I know that...

I've backed up the /home/ and the /etc/ directories.

> 

I have a box that is offline and I want to keep my configurations/data/settings/browser info, etc. so there's no need to download and do everything over.

The reason I need to do a fresh install is that I added 10.04 packages from a CD to an 8.04 system and it now won't take alternative CD upgrades with the cdromupgrade script.

The packages refuse to downgrade via the "force version" option.

I have:
*Backed up my keys with command "sudo apt-key exportall > ~/repositories.key"

*Backed up "sources.list" file and "sources.list.d" folder.

I'm told I can back up the "archives" folder so I don't have to redownload all the packages.

It didn't work for me but I've read I can back up program/package configurations with commands: "dpkg --get-selections "*" >myselections" and "debconf-get-selections > debconfsel.txt"

How do I back up the Firefox profile directories.

I have been told about Keryx keryxproject.org and Remastersys but I think I need to do it old school this time.


---

### Post by oldfred on 2011-04-30
Your Firefox profile in in /home.
~/.mozilla/firefox

If you have mixed packages, I would think your archives may also be mixed?

I use the dpkg commands to export a list of installed apps & reinstall, but it requires online access.

I have not used, but have seen suggestions for:
aptoncd 
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
Download once for many machines
How To Install Apt-Cacher-NG in Ubuntu Linux
[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)

---

### Post by Elludium_Q-36 on 2011-05-02
Thanks oldfred,

I planned on doing a fresh install, restoring a backup of the package archive/cache but only reinstalling the correct packages.

There seem to only be 13 incorrect packages from the source-> deb cdrom:[Kubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.2)]/ lucid main restricted    These show up in Synaptic by selecting the "Origin" button and highlighting "Kubuntu 10.04.1 LTS..."  I'd do a fresh install but leave these packages out.

Now in the Synaptic menu, -> Settings -> Preferences, under the "Files" tab/"Temporary files" my selection is: "Only delete packages which are no longer available."  You can also select: "Delete downloaded packages after installation." or "Leave all downloaded packages in the cache."   So where is this cache/archive of temporary files that contains downloaded packages?

Actually APTonCD sounds like it may do the trick as it seems I can edit packages.  I might be able to bring it to my machine with Keryx [http://keryxproject.org/](http://keryxproject.org/)

It's not installed on my machine but I read in another thread that the command:
```

debconf-get-selections

```
is for configuration/settings...
> 
kubuntu@Kubuntu-jc1:~$ dpkg-get-selections --help
bash: dpkg-get-selections: command not found
kubuntu@Kubuntu-jc1:~$ debconf-get-selections --help
The program 'debconf-get-selections' is currently not installed.  You can install it by typing:
sudo apt-get install debconf-utils
bash: debconf-get-selections: command not found
kubuntu@Kubuntu-jc1:~$


I have backed up the /home/ and /etc/ directories.

I also backed up my keys:
```

sudo apt-key exportall > /media/disk/Kubuntu2/repositories.key

```

I grabbed APTonCD and debconf-utils with keryx [http://keryxproject.org/](http://keryxproject.org/) and would appreciate any more info...

---

### Post by Elludium_Q-36 on 2011-05-03
I could not find the package archive cache...  Where might they be found?

I need help on using debconf-utils, specifically debconf-get-selections

---

### Post by oldfred on 2011-05-03
Do you mean this. But it requires on line access to download new packages.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

dpkg --get-selections > ~/my-packages
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings'

---

### Post by Elludium_Q-36 on 2011-05-03
If I knew where the package cache archives did lie, I could even backup and restore them manually.  I searched my system for file:/// *.deb but only got a few packages in the trash and it found those in a [Keryx]("http://keryxproject.org/") folder on my USB flash/thumb drive that had been mounted.

Either they're in a hidden folder and I forgot to check an option for hidden files or they got wiped out when I reloaded in synaptic as they may have been deemed no longer available.

I pretty much already had figured out restoring packages while online and, in my case, I can save the synaptic markings as a .txt file to open on a windows box.  Then I could manually add packages to [Keryx]("http://keryxproject.org/").

I was able to add [APTonCD]("https://help.ubuntu.com/community/APTonCD") but it does not automatically point to the package file archives.  You must know where they are located.

I was told about [Remastersys]("http://remastersys.sourceforge.net/") in another post and that may automagically point to the package file archives, which is simply a matter of knowing where they are filed.  I've downloaded remastersys_2.0.12-1_all.deb for Hardy & Jaunty so I'll see what it's all about.

If I must manually download the packages again, I must.  Really I need help with global settings & configurations, as well as for individual applications.  The program debconf-utils debconf-get-selections, specifically debconf-get-selections when flagged with "--help" outputs some global configuration data to the Konsole screen.  I had hoped someone could help with the syntax to backup this to a file and restore.

If I could afford to have the paid support, my Kubuntu box would be online also and not offline, on "sneakernet".  I know there are help posts and many a user post here but 'tis not an easy task to search through all when on "sneakernet", with limited time access at the library or while paying at a 'net cafe'.  If I had a laptop, with WiFi, this wouldn't even be an issue.

As I wrote before, I already backed up the /home/ directory, as well as the /etc/ directory.  The sources.list file and sources.d folder are in etc and I can edit those manually.  I understand that /home/ contains some application configuration settings, in hidden files. Unfortunately some files/folders in /etc/ refuse to manually copy when backing up, even when doing so as root.

I have backed up my authentication keys:
```
sudo apt-key exportall > /media/disk/Kubuntu2/repositories.key
```

Any help is appreciated =;

---

