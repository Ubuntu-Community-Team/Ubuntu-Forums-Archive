---
title: "Install from a web page"
date: 2013-04-03
forum: Installation &amp; Upgrades
---

### Post by Ralph L on 2013-04-03
I tried to install flashplugin-nonfree-11.2.202.251ubuntu0.12.04.1 from [https://launchpad.net/~ubuntu-mozill...+build/3962442](https://launchpad.net/~ubuntu-mozill...+build/3962442). but it didn't work.  However, I may have used the incorrect installation procedure. Can anybody tell me how to install from a web page like [https://launchpad.net/~ubuntu-mozill...+build/3962442](https://launchpad.net/~ubuntu-mozill...+build/3962442) ???? Apparently I don't know how to do it.

---

### Post by ibjsb4 on 2013-04-03
Your links do not work.

12o4 has flash in the repository.  Why not use it?

---

### Post by Ralph L on 2013-04-04
ibjsb4
Thank you for responding.  Sorry about messing up the link--not sure how I did that.  The link should be [https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/+build/3962442](https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/+build/3962442)

As for why I don't use the flash in the xubuntu 12.04 repository, it is because it doesn't work on my old compaq presario 2100.  I saw somewhere that newer version of flash use SSE 2 and that older cpus, particularly amd ones, may not have that.  Perhaps this is why it won't work.  I actually got it working with Flash 11.1 r102, but then firefox disabled the plugin saying it was too old.  So my thought is to work my way back through older versions until I find the most recent version that will actually work.  I am also trying to get Flash Aid to work, but that is on another forum thread.

---

### Post by slickymaster on 2013-04-04
In that page you have the [flashplugin-installer_11.2.202.251ubuntu0.12.04.1_i386.deb]("https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/+build/3962442/+files/flashplugin-installer_11.2.202.251ubuntu0.12.04.1_i386.deb") file. As this is a deb file, to install it just download it and double click on it, and then select Install Package.

Alternatively, you can also install a .deb file by opening a terminal and typing:
```
sudo dpkg -i package_file.deb
```

To uninstall a .deb file, deselect it in your package manager, or type:
```
sudo dpkg -r package_name
```

---

### Post by claracc on 2013-04-04
> **Ralph L said:**
> I tried to install flashplugin-nonfree-11.2.202.251ubuntu0.12.04.1 from [https://launchpad.net/~ubuntu-mozill...+build/3962442](https://launchpad.net/~ubuntu-mozill...+build/3962442). but it didn't work.  However, I may have used the incorrect installation procedure. Can anybody tell me how to install from a web page like [https://launchpad.net/~ubuntu-mozill...+build/3962442](https://launchpad.net/~ubuntu-mozill...+build/3962442) ???? Apparently I don't know how to do it.

To install software from a ppa you have to add the ppa to your sources.list file, to do it, you click in the link [https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa), then it appears a page where it is explained howto add this ppa to your system and howto install software from this ppa through updating.

---

### Post by Ralph L on 2013-04-04
slickymaster

I am really confused.  Trying to understand how things work I first went to the download web site and double clicked the flashplugin-installer .deb file and it seemed to install.  Then I used synaptic or USC (I don't remeber which) to remove it.  Then I download the flashplugin-installer file and flashplugin-downloader .deb file to a folder on my hard disk, and ran the Terminal dpkg method.  It completed without error, but /usr/lib/flashplugin-installer folder did not have to .so file that it needs.  So that method didn't work.  Then I again uninstalled flashplugin-installer with synaptic and tried reinstalling using the double click on the flash-installer file on the web site.  This time the install was unsuccessful.

I am right back to ground zero, unable to consistently install flash from this type of web site.

---

### Post by slickymaster on 2013-04-05
> **Ralph L said:**
> slickymaster

I am really confused.  Trying to understand how things work I first went to the download web site and double clicked the flashplugin-installer .deb file and it seemed to install.  Then I used synaptic or USC (I don't remeber which) to remove it.  Then I download the flashplugin-installer file and flashplugin-downloader .deb file to a folder on my hard disk, and ran the Terminal dpkg method.  It completed without error, but /usr/lib/flashplugin-installer folder did not have to .so file that it needs.  So that method didn't work.  Then I again uninstalled flashplugin-installer with synaptic and tried reinstalling using the double click on the flash-installer file on the web site.  This time the install was unsuccessful.

I am right back to ground zero, unable to consistently install flash from this type of web site.

Let's try another way.
Download this tar: [flashplugin-nonfree_11.2.202.251ubuntu0.12.04.1.tar.gz]("https://launchpad.net/ubuntu/+archive/primary/+files/flashplugin-nonfree_11.2.202.251ubuntu0.12.04.1.tar.gz")
The open a terminal window and run the following:
```
cd /path/to/folder_with_flashplugin-nonfree_11.2.202.251ubuntu0.12.04.1.tar.gz
tar xvzf flashplugin-nonfree_11.2.202.251ubuntu0.12.04.1.tar.gz
```
See if there is any README file with specific installation instructions. If there aren't any specific instructions proceed with the install
```
./configure
make
make install
```

---

### Post by Ralph L on 2013-04-05
slickymaster

Thank you for responding again.  As you can see I need lots of help.  I followed your directions for downloading the source tarball.  I extracted it fine.  But when I typed "./configure", it said "bash: ./configure: No such file or directory".  I searched the entire directory and there is no "configure" file.  Any further ideas???

---

### Post by claracc on 2013-04-06
You are trying to compile and install the source package, for this you need to have installed compilation software: build-essential as it is indicated, here: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo). Before trying things, it is important to know what are you doing.

Following your problem in thread: [http://ubuntuforums.org/showthread.php?t=2131197&page=2](http://ubuntuforums.org/showthread.php?t=2131197&page=2) and as you got (at the end) installed flashaid, I recommend to install any flashplayer plugin through the custom way in flashaid ( the script will remove the installed flashplayer one if any and will install the desired one)

---

### Post by slickymaster on 2013-04-06
> **Ralph L said:**
> slickymaster

Thank you for responding again.  As you can see I need lots of help.  I followed your directions for downloading the source tarball.  I extracted it fine.  But when I typed "./configure", it said "bash: ./configure: No such file or directory".  I searched the entire directory and there is "configure" file.  Any further ideas???

> **claracc said:**
> You are trying to compile and install the source package, for this you need to have installed compilation software: build-essential as it is indicated, here: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo). Before trying things, it is important to know what are you doing.

Following your problem in thread: [http://ubuntuforums.org/showthread.php?t=2131197&page=2](http://ubuntuforums.org/showthread.php?t=2131197&page=2) and as you got (at the end) installed flashaid, I recommend to install any flashplayer plugin through the custom way in flashaid ( the script will remove the installed flashplayer one if any and will install the desired one)

I wasn't aware of the fact that you already had installed flashdaid. In truth I didn't knew of this second thread, mentioned by claracc. But, and after reading it, I think that claracc is right, since you already have flashaid it's easier and preferable to install flashplugin through flashaid.

---

### Post by Ralph L on 2013-04-11
claracc, slickymaster
Thank you for the time you spent helping me.  Using the new version of flashaid I installed fp_11.1.102.63_archive.zip from [http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html) .  It worked, although each time I access a web site that uses it, I get a warning message.  Guess I will just have to live with that.  I experimented with slightly newer versions of flashplayer for the same web site, but none of them would work, so I guess I have the newest version that will work.

Also, I found that what we thought was a source .tar.gz file at [https://launchpad.net/ubuntu/+archive/primary/+files/flashplugin-nonfree_11.2.202.251ubuntu0.12.04.1.tar.gz](https://launchpad.net/ubuntu/+archive/primary/+files/flashplugin-nonfree_11.2.202.251ubuntu0.12.04.1.tar.gz) is NOT a source file at all.  That is why I couldn't do a ./configure on it.  Instead it looks like a conglomeration of .deb type files.

As to my origninal question in this post about how to install the .deb files from [https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/+build/3962442](https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/+build/3962442), I discovered that there was a missing dependency that was listed in the "information icon" in the notification area on one of the panels.  It seems strange to me that neither Ubuntu Software Center nor dpkg puts out an easily noticed error message either in the USC window or, for dpkg, in the Terminal output, but instead shows up in an obscure panel location. Also, I couldn't find a way to list the missing dependency in either USC or dpkg.  For my own education can anybody tell me how to find a missing dependency in a .deb package, other than listing all dependencies and searching through my entire system for each of 20 or more dependencies????

---

### Post by slickymaster on 2013-04-11
> **Ralph L said:**
>  It seems strange to me that neither Ubuntu Software Center nor dpkg puts out an easily noticed error message either in the USC window or, for dpkg, in the Terminal output, but instead shows up in an obscure panel location.
dpkg itself is not capable of managing repositories. It is required to use a higher-level tool, like apt-get, to fetch anything from repositories. dkpg is only the core tool, that installs/removes/configures packages, taking care of dependencies and other factors. apt-get and aptitude are tools that manage repositories, download data from them, and use dkpg to install/remove packages from them. This means, that apt-get and aptitude can resolve dependencies and get required packages from repository, but dpkg cannot, because it knows nothing about repositories.

> **Ralph L said:**
> For my own education can anybody tell me how to find a missing dependency in a .deb package, other than listing all dependencies and searching through my entire system for each of 20 or more dependencies????
You can install a package and get it's dependencies from repositories with [GDebi]("https://launchpad.net/gdebi"). It's a tool that can install .deb packages.
```
sudo gdebi name_of_package.deb
```
If you already installed the package with missed dependencies, you can dowload and install dependencies automatically with
```
sudo apt-get -f install
```

EDIT: Anyway, glad you got it fix. That's what's important.

---

