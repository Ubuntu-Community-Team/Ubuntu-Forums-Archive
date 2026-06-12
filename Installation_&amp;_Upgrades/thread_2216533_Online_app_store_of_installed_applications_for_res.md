---
title: "Online app store of installed applications for restore after reinstallation/upgrade"
date: 2014-04-12
forum: Installation &amp; Upgrades
---

### Post by hariks0 on 2014-04-12
Hi All,

As 14.04 is round the corner, I just wanted to know if there is any possibility for storing the list of installed applications as in the Google play store. So that the same applications can be reinstalled/restored online in the new Ubuntu with ease.

TIA.

---

### Post by slickymaster on 2014-04-12
I'm not aware of the existence of such application, but you can perform a backup list of your installed applications just by running the following command in a terminal window:```
dpkg --get-selections > ~/my-packages
```This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages"```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```It will download and install all the programs for you, except those that you installed manually, if they are not in the repositories.

---

### Post by Double.J on 2014-04-12
> **slickymaster said:**
> ...save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages"...

Fantastic solution Slickymaster!

I must admit I've never done this. I usually keep a list of my packages, and skim over it when setting up a clean install. 

Only thing I'd add is to make a backup of your systems list of repositories. If you've added third party repositories, it's really helpful to remember what they were in case you can't find it after a reinstall.

```
sudo cp /etc/apt/sources.list ~/Documents/sources.list.txt
```

Note that unlike Slickymaster's  guide, after installing the latest system, you would not want to replace the existing sources.list file with this one. Just use it as a guide.

For example, mine begins:
```
# deb cdrom:[Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release i386 (20140204)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates main restricted
```(note '#' means the line will be ignored by the system)

As you can see my sources list shows quite clearly that I am currently on my LTS install, 12.04 precise pangolin. notice how the first few repos I've included all have 'precise' in them? if you got rid of your 14.04 sources.list, and pasted this in, then Ubuntu would keep looking for updates and new software in the old repos (in the case of updates it would just keep reporting you have the latest software)

The third party repos you may have added for extra software are listed at the bottom of the list. Here are couple of mine from my 11.10 install:
```
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu saucy main
deb-src http://extras.ubuntu.com/ubuntu saucy main
deb http://repository.spotify.com stable non-free
deb-src http://repository.spotify.com stable non-free
```Again notice how one entry is specific to the relase (saucy) and the other (spotify) uses one repository for all currently supported releases? it's the second type you'd want to use.

Finally there are PPAs (personal package archives) that you may have added (I've added over thirty!) They are not in your sources list, but are also sources for your system. They live in /etc/apt/sources.d/ 

My first two entries are:
```
user@computer:/etc/apt/sources.list.d$ ls
gwendal-lebihan-dev-cinnamon-stable-precise.list
gwendal-lebihan-dev-cinnamon-stable-precise.list.save
ninja-ide-developers-ninja-ide-stable-precise.list
ninja-ide-developers-ninja-ide-stable-precise.list.save
```

Now these are a folder of documents, not a nice list of instructions in one file. This answer on [ask ubuntu]("http://askubuntu.com/questions/28644/how-can-i-backup-my-ppas") is far too awesome for me to take credit on! You do have to also check what changes from one release to the next. For example the simply fantastic ninja ide I've been using for python programming for a little while Is now in the main repos in 14.04!


Hope its been helpful :D

All the best,

Jj

---

### Post by slickymaster on 2014-04-14
> **Double.J said:**
> Fantastic solution Slickymaster!
<--- smip --->

It's a fantastic solution indeed, but I'm not the one to take the credits for it. The credits belong to [lovinglinux]("http://ubuntuforums.org/member.php?u=649167"), a former forum contributor.

---

### Post by thedoommakerybr on 2014-05-10
This is really wonderful. I think, it would be even greater if we could back-up the settings of these programs and then restore after they are installed automatically. Is this possible? For future installs (another distro with the same desktop environment maybe or a previous release), can we do this by creating a separate /usr partition and not formatting it when performing a clean install? This question can be totally irrelevant and the reason I'm asking this is that I think program files and settings are kept in /usr directory. I might be totally wrong though. Thanks.

---

### Post by SeijiSensei on 2014-05-10
One caveat about PPAs.  If you install repos with the "apt-add-repository" application, the configuration files will be kept in /etc/apt/sources.list.d/, one for each repo.  So you would need to backup this directory as well.

If you know the name of a package you need to install, you can always download it from the complete package list for Ubuntu here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/).

---

### Post by oldfred on 2014-05-10
All the settings for each user are in /home. So backing up and reinstalling /home restores all the settings for every program.
Only hardware system based manual changes may be in /etc. And if you install web server, databases or other server apps, they may have their own directories where ever you created them. 

       1. /home (Users' personal files and settings) including keys in ~/.gnupg
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup
5. list of installed applications 
6. any customized grub in 40_custom or settings in /etc/default/grub
7. Sources & ppas as discussed above

      
 Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

---

### Post by thedoommakerybr on 2014-05-10
@oldfred thanks. So I'll need to create a separate partition for /home in my future fresh installs to keep my settings for other fresh installs. That sounds even better. Thanks.

---

### Post by oldfred on 2014-05-10
You can use a separate /home. 

But I have mulitple installs, so I keep all data in a shared data partition and leave /home inside my / (root). Then /home is tiny. I find my /home is 2GB and 1.5GB of that is .wine for my Picasa which I do not move to the data partition.

---

