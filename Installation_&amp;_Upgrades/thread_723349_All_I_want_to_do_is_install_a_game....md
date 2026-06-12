---
title: "All I want to do is install a game..."
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by mrphil on 2008-03-13
Hello.

I installed Ubuntu 3 days ago. On this months Linux Format DVD is a game called Scorched3d. I remember this game from years ago and want to have a look and play it. So I double clicked on the icon on the dvd called 'scorched3d-data_41.3dfsg-1~getdeb1_all.deb' which opened up the package installer. I clicked on install.

It did some stuff and then told me that all was ok.

Where is the icon to start the game? I have found the folder that has all the data files in it, but there seems to be no executable, a search for 'scorched3d' returns 2 results, one is an icon in the '/usr/share/app-install/icons' folder, and the other is '/usr/share/app-install/desktop/scorched36.desktop' which seems to be a configuration file.

I have no idea what to do now.

Please help, I really want to like Linux/Ubuntu and use it but simple things like no shortcuts or icons to start the things that I install are making me want to bin it. :-( 

Cheers,

---

### Post by scragar on 2008-03-13
try running:
```
find -atime 1 | grep Scorch
``` to see if you can find the folder it's installed to(or with any luck something in /usr/bin which would be the launcher).

---

### Post by ShodanjoDM on 2008-03-13
You have installed the game data, it still needs another package.

Download both .deb files from here:

[http://getdeb.net/release.php?id=2043](http://getdeb.net/release.php?id=2043) (32 bit)

or from here if you're using Ubuntu 64 bit:

[http://getdeb.net/release.php?id=2044](http://getdeb.net/release.php?id=2044)

---

### Post by ruibernardo on 2008-03-13
You can use getdebs packages, you have to download them all and certify yourself about missing dependencies. If you installed the packages with gdebi (clicking on a deb file), the dependencies should be displayed. If you used "dpkg", run "sudo apt-get install -f" to make APT resolve the problem and download/install all missing packages from the repositories.

Another way is to compile from source: [Howto run latest Scorched3d in Feisty and Gutsy]("http://ubuntuforums.org/showthread.php?t=580704").

That howto was done for version 41.2 and should be adapted. I made it because alien (a rpm to deb converter) didn't work at the time with that version - 41.2.

The third way is to use alien to convert the rpm package from scorched3d.co.uk to a deb file and install it after - works with 41.3!
```
sudo apt-get install alien
wget -c http://prdownloads.sourceforge.net/scorched3d/Scorched3D-41.3-1.i386.rpm?download
sudo alien Scorched3D-41.3-1.i386.rpm
sudo dpkg -i [the name of the deb package.deb]

```To create a menu, right-click on the Gnome menu, choose "Edit menus", click on "Games" and then on "New item". Give it a name and paste "/usr/bin/scorched3dc" on the "Command" textbox. Change "/usr/bin/scorched3dc" to "/usr/local/bin/scorched3dc" if you compiled from sources.

Have fun :popcorn:

---

### Post by mrphil on 2008-03-13
> **epimeteo said:**
> 

The third way is to use alien to convert the rpm package from scorched3d.co.uk to a deb file and install it after - works with 41.3!
```
sudo apt-get install alien
wget -c http://prdownloads.sourceforge.net/scorched3d/Scorched3D-41.3-1.i386.rpm?download
sudo alien Scorched3D-41.3-1.i386.rpm
sudo dpkg -i [the name of the deb package.deb]

```


OK, so I tried the above and when I tried the first line 
```
sudo apt-get install alien
``` all I got was ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package alien is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package alien has no installation candidate

```

So do I need to update my repositories? (I understand about them ;-) ) If so, please tell me how to do it and what repositories to specify.

Also, I went to your link above about compiling it myself but failed at the first hurdle. I copied and pasted the first line (the really long one,) made the changes specified in one of the replies below and found that it couldn't find the packages.

AAAAAAARRRRGGHHHHHH!!!!


Cheers,

---

### Post by kaurman on 2008-03-13
Hi!

Why don't you just go to terminal and type: 'sudo apt-get install scorched3d'?

---

### Post by mrphil on 2008-03-13
> **kaurman said:**
> Hi!

Why don't you just go to terminal and type: 'sudo apt-get install scorched3d'?

Thanks,

Tried that and got
```
laptop:~$ sudo apt-get install scorched3d
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  scorched3d: Depends: scorched3d-data (= 40.1d.dfsg-1ubuntu1) but 41.3dfsg-1~getdeb1 is to be installed
E: Broken packages

```

At least it prompted a response, I suppose.

I downloaded both the files required for the game, do they need to be in a specific dir for the apt-get install command?

Cheers,

---

### Post by ruibernardo on 2008-03-13
Ok, at this point you should have your apt system broken. You can't find the package "alien", which is in the main repository? Verify which repositories you have enabled in Synaptic, clicking the menu "Settings" -> "Repositories" and enable all of them (the last one - "Source code" - is optional). And click "Update" in the task bar (Synaptic should tell you to do it).

Now you have to decide from where you want to install it. And please install the same software from ONE source only! If the getdebs packages installation failed, remove the packages you installed (in Synaptic select the menu "Edit" -> "Resolve boken packages" and remove).

With all the repositories enabled you can find "scorched3d" and "scorched3d-data" in Synaptic. The version is "40.1", so it is a bit old and you can't play online with it on most on schorced3d servers in the Internet. If you plan to play online, don't install it from the ubuntu repositories.


Again, with all repos enabled in Synaptic, install "alien" and then try again to convert the rpm package to a deb file and install it.  One last note about alien/dpkg: when you install the converted rpm (the deb file) with dpkg use the filename instead of the package name (package name: software_version_arch_dist.deb - for example: wine_0.9.57~winehq0~ubuntu~7.10-1_i386.deb).

---

### Post by mrphil on 2008-03-14
THANK YOU!!

I have now discovered 'System > Administration > Synaptic Package Manager'

It looked like only the data package had been installed. I tried to install the other packages but they kept coming up with a dependency problem. So I was able to remove the package I downloaded from the Scorched3d website, and install the older version from the Ubuntu Repository. 

As it goes, Scorched3d won't run on my test laptop 'cos it isn't powerfull enough!

Thanks for all your help,

Phil

---

