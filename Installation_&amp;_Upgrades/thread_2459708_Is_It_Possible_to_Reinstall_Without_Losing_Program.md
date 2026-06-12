---
title: "Is It Possible to Reinstall Without Losing Programs?"
date: 2021-03-24
forum: Installation &amp; Upgrades
---

### Post by rebeltaz on 2021-03-24
I know I can backup and restore my /home directory, but is there anyway that you can do a re-install without losing any programs that you've installed. After years of using this system, I would be hard pressed to remember every change I've made or every program I would need to reinstall

---

### Post by guiverc on 2021-03-24
You haven't provided OS & release details, so I'll be general.

For Ubuntu Desktop installs you can opt to install using "*Something else*" (*'Manual' or 'Manual Partitioning*') if using a *live* installer and if you select your existing partitions, and do** not** format any partition(s), it'll cause the installer to

- note your installed packages (those not installed by installation media)
- erase system directories
- install new system
- attempt to add back additional programs (*if available in new release in Ubuntu repositories*)
- ask you to reboot

It won't touch your user directory.  Please note this install is triggered by the '**no format**', if you format a partition (esp. / partition) you'll lose what was there (and a *clean* install is instead performed).

It won't work for programs where no source is available, and is tested only with Ubuntu repositories (not 3rd party or PPAs). It may work with some PPAs, but it's intention was the Ubuntu repositories.

It's a very fast *upgrade via re-install* option, however if you were using it to upgrade 18.04 to 20.04, as Qt4 & python2 reached EOL during 2019 & were removed from Debian & Ubuntu repositories, programs that relied on either may have been dropped from 20.04 (*if they weren't ported to Qt5 and/or python3*) so won't be able to be re-installed. That will thus result in the error that not all packages could be restored.

It's not as *useful* with server applications, as user programs store their configs in $HOME or the user directory which isn't touched (*unless you format*), however due to system directories being wiped, and many server applications storing their configs in system directories, those programs will need their config/setup files restored post-install.

*Note:  I saw on a bug report mention that due to the number of bug reports filed because not all packages could be restored (3rd party), this feature was going to be  removed; but it was still working last time I tried it using a hirsute daily (and all prior releases).*

---

### Post by yancek on 2021-03-24
This should work.  It worked for me about a month ago with another LInux OS which was on a single partition and I simply selected to install without formatting.  All the personal data I had as well  as software I had installed was available.   I don't know that this will work with Ubuntu, some caveats explained in post 2.  I would also wonder about problems with versions as you have apparently had your version of Ubuntu installed for some time and I would think you might have problems installing a newer version/release of Ubuntu.  In my case, I had just installed the OS and still had the same installation media.

---

### Post by ActionParsnip on 2021-03-24
Most configurations are in /home on a per user basis or in /etc
If you backup these folders then you'll be OK

---

### Post by oldfred on 2021-03-24
Your normal backup should be including a list of installed applications. 

My backup includes this also. The dpkg list is a very long text list of all applications and the dependencies. 
If upgrading, you may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/).

And if you installed ppas, you can back those up. But if installing a new version, old ppa may not have newer version available. I just copy into /home, so backup of /home includes my packages & sources. 
sudo cp -r /etc/apt/sources.list.d /Like-a-FlashDrive

---

### Post by TheFu on 2021-03-24
> **rebeltaz said:**
> I know I can backup and restore my /home directory, but is there anyway that you can do a re-install without losing any programs that you've installed. After years of using this system, I would be hard pressed to remember every change I've made or every program I would need to reinstall

So ... a good backup includes all HOME directories, /etc/, /usr/local/ and any other places where you've manually modified or placed files.  People commonly install fonts and theme packages under /usr/share/ - so I hear. I don't, but whatever.

So - that should get most of the data and nearly all OS settings.
What you need now is to capture all the installed programs.  It was really easy in the past since we all used APT packages.  Getting a list of manually installed packages from APT is easy, backup that list and after the install on the new system, feed that list into apt and they will be installed.  Easy-peasy.
```
# Daily dump of current packages to local_backup=$HOME/backup
dpkg --get-selections  > $local_backup/dpkg.list
apt-mark showauto | tee $local_backup/apt-mark.auto
apt-mark showmanual | tee $local_backup/apt-mark.manual

######[ to restore pkgs ]#######
### sudo apt-get install -y $(< $local_backup/apt-mark.manual) 
##       or screw around with these   ##
### sudo apt-mark auto $(cat apt-mark.auto)
### sudo apt-mark manual $(cat apt-mark.manual)
### sudo apt-get -u dselect-upgrade
```

In theory, on the apt-mark showmanual, but since these files are tiny, why not have too much information just in-case?
Manually compiled and installed software should be placed into /usr/local/ ... so the backups in the first group would get that.

No we have flatpaks, appimages and snaps.  Each of those has different liability for backups.  Many have a "list" option, so 
```
sudo snap list | tee $local_backup/snap-list
```
will get the snaps to be installed. I don't have many, so never looked for a way to automatically re-install snaps.

AppImages are standalone files and they don't update themselves by default. If they do - it is a feature that the dev included in the program.  Anyway, I place all my AppImages under /usr/local/appimages/ so those all get included in the first group too.  If you put them in your HOME directory, then then backing that up will get them too.  Be certain that you manually upgrade these packages at least monthly, but weekly would be better (for some values of "better").

Flatpaks - I haven't done much with these. Think they probably have a **flatpak list** command, so I'd use that and store the output into a file that is included in my backups.

Programmers might have multiple specialized environments for developing in different versions of python, ruby, perl and each of those might have specific versions of modules for the language version. That means capturing that information may be needed too.  Most languages have a package manager tool which can output a list of installed packages and versions. Use those to create list-o-package files which can be fed back later.

So, if you stick with only APT packages, what is needed to backup and restore is simpler.

So - don't do these things in the order I've written.  Probably want to make those lists of packages first and put those lists into directories that get included in the backup locations already.

[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006) - has an easy version of my script to get you started.
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986) talks about restoring and what order to restore, since it matters.

Backups usually take 1-5 minutes nightly. These are automatic, daily, versioned and use perhaps 1.3x the amount of storage that the files being backed up require for 90 days of versions.

Restores take between 30 and 45 minutes.  The first step is a fresh install of the OS I want. Obviously, this is for the normal stuff a server or desktop would need. Restoring huge amounts of data will take longer, but for getting a system back to usefulness with web, email, and other normal desktop needs, 45 minutes is on the high end of the time needed. It completely changes the troubleshooting decisions.  If I've spent 30 minutes trying to fix something that I or an update broke, then I'll stop, wipe the system, and go through my restore process.

I'm not a fan of installing over an existing install. This encouraged people to take chances and possibly lose lots of data.  Because it might be ok sometimes, they probably wouldn't make any backups, so total data loss is much more likely. The most certain way to NOT have issues is to make great backups.  It's a pay now or pay later thing. Computers seem to "know" when you don't have good backups and they seem to fail more often, losing data.  Once you have good backups, you'll seldom lose any data.  Guess that's the way of the Universe.

---

### Post by rebeltaz on 2021-03-24
Thank you ALL for the excellent responses! 

I should have said that my current version is 18.04 LTS. So, what I will probably do is make a complete mirror of the drive - just in case - and then do a re-install of that, the 18.04 system. After that, if it works, I may or may not do an upgrade to 20. Meh... 18 has been fine for me. It just that I transferred the drive to a different computer and I feel things aren't quite right. 

@theFu - Dude! That is one detailed explanation! Thank you so much! I'll have to look at those links. Yeah... I am lax in my backups (as in I don't have any of the directories) but I do try to have multiple copies of important data on different drives. I will have to try to make it a point to do that more often. What do you back up to, just out of curiosity?

---

### Post by TheFu on 2021-03-24
> **rebeltaz said:**
>  What do you back up to, just out of curiosity?

Please read the links, then ask questions.

---

