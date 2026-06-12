---
title: "Icons In System Settings(unity) are Missing Ubuntu Server 17.04"
date: 2017-07-02
forum: Installation &amp; Upgrades
---

### Post by caneraydinbey on 2017-07-02
I just installed 17.04 server and then desktop but I have only those icons (this is not actually my setting, but it is broken the same way)
I tried these command in an attempt to solve it:
```

    sudo apt-get install ubuntu-desktop
    sudo apt-get remove unity-control-center
    sudo apt-get install unity-control-center
    sudo apt-get install ubuntu-desktop
    sudo apt-get install unity-control-center
    sudo apt-get install unity-control-center-signon gnome-control-center-unity
    sudo apt-get update --fix-missing
    sudo apt-get -f install
```
But I did not manage to solve it. Can you suggest any ways to solve my problem?

i reinstalled ubuntu desktop notihng changed sudo apt-get install --reinstall ubuntu-desktop 0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded. 
I did this also
[https://askubuntu.com/questions/466720/system-settings-icons-missing-in-14-04/621874#621874]("https://askubuntu.com/questions/466720/system-settings-icons-missing-in-14-04/621874#621874")
but it also added only one icon. online accounts.

They are lots of still missing icons like power.
When  i write `gnome-control -center`, i t brings lots of icons but when i click for example display, console shows:
```
&#10140;  ~ gnome-control-center
    
    ** (gnome-control-center:11997): WARNING **: Ignoring launcher gufw (missing desktop file)
    
    ** (gnome-control-center:11997): WARNING **: Ignoring launcher landscape-client-settings (missing desktop file)
    
    ** (gnome-control-center:11997): WARNING **: Ignoring launcher ubuntuone-installer (missing desktop file)
    
    (gnome-control-center:11997): display-cc-panel-WARNING **: no sunset data, using 16.00
    
    (gnome-control-center:11997): display-cc-panel-WARNING **: no sunrise data, using 8.00
    
    (gnome-control-center:11997): display-cc-panel-WARNING **: no sunset data, using 16.00
    
    (gnome-control-center:11997): display-cc-panel-WARNING **: no sunrise data, using 8.00
    
    (gnome-control-center:11997): display-cc-panel-WARNING **: no sunset data, using 16.00
    
    (gnome-control-center:11997): display-cc-panel-WARNING **: no sunrise data, using 8.00
    
    (gnome-control-center:11997): display-cc-panel-WARNING **: no sunset data, using 16.00
    
    (gnome-control-center:11997): display-cc-panel-WARNING **: no sunrise data, using 8.00
```
And this did nothing
 ```
 sudo apt-get install unity-control-center-signon gnome-control-center-unity
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    Note, selecting 'unity-control-center' instead of 'gnome-control-center-unity'
    unity-control-center is already the newest version (15.04.0+17.04.20170402.6-0ubuntu1).
    unity-control-center-signon is already the newest version (0.1.9+16.10.20160825-0ubuntu1).
    The following packages were automatically installed and are no longer required:
      linux-headers-4.10.0-22 linux-headers-4.10.0-22-generic
      linux-image-4.10.0-22-generic linux-image-extra-4.10.0-22-generic
      linux-signed-image-4.10.0-22-generic
    Use 'sudo apt autoremove' to remove them.

```
Also this did not do anything
```
 sudo apt-get update
 sudo apt-get install --reinstall ubuntu-desktop
 sudo apt-get install unity
 sudo shutdown -r now

```
see
```
 &#10140;  ~ sudo apt-get update
    sudo apt-get install --reinstall ubuntu-desktop
    sudo apt-get install unity
    Hit:1 [http://repo.steampowered.com/steam](http://repo.steampowered.com/steam) precise InRelease
    Ign:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease        
    Hit:3 [http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu](http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu) zesty InRelease
    Hit:4 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                
    Hit:5 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) zesty InRelease
    Hit:6 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release          
    Hit:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty InRelease           
    Hit:8 [https://deb.nodesource.com/node_6.x](https://deb.nodesource.com/node_6.x) yakkety InRelease         
    Hit:9 [http://ppa.launchpad.net/papirus/papirus/ubuntu](http://ppa.launchpad.net/papirus/papirus/ubuntu) zesty InRelease
    Hit:10 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) zesty InRelease     
    Hit:11 [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) zesty InRelease
    Hit:12 [https://packages.microsoft.com/repos/vscode](https://packages.microsoft.com/repos/vscode) stable InRelease 
    Get:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-security InRelease [89.2 kB]
    Ign:15 [http://repo.mongodb.org/apt/ubuntu](http://repo.mongodb.org/apt/ubuntu) xenial/mongodb-org/3.2 InRelease
    Hit:16 [http://repo.mongodb.org/apt/ubuntu](http://repo.mongodb.org/apt/ubuntu) xenial/mongodb-org/3.2 Release
    Get:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates InRelease [89.2 kB]
    Get:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-security/main amd64 DEP-11 Metadata [5,812 B]
    Get:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-security/universe amd64 DEP-11 Metadata [8,904 B]
    Get:21 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-security/universe DEP-11 64x64 Icons [27.0 kB]
    Get:22 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates/main amd64 DEP-11 Metadata [41.8 kB]
    Get:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates/main DEP-11 64x64 Icons [14.0 kB]
    Get:24 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates/universe amd64 DEP-11 Metadata [57.5 kB]
    Get:25 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates/universe DEP-11 64x64 Icons [58.7 kB]
    Fetched 392 kB in 1s (228 kB/s)                                     
    Reading package lists... Done
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    The following packages were automatically installed and are no longer required:
      linux-headers-4.10.0-22 linux-headers-4.10.0-22-generic
      linux-image-4.10.0-22-generic linux-image-extra-4.10.0-22-generic
      linux-signed-image-4.10.0-22-generic
    Use 'sudo apt autoremove' to remove them.
    0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
    Need to get 0 B/3,612 B of archives.
    After this operation, 0 B of additional disk space will be used.
    (Reading database ... 356900 files and directories currently installed.)
    Preparing to unpack .../ubuntu-desktop_1.379_amd64.deb ...
    Unpacking ubuntu-desktop (1.379) over (1.379) ...
    Setting up ubuntu-desktop (1.379) ...
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    unity is already the newest version (7.5.0+17.04.20170407.1-0ubuntu1).
    The following packages were automatically installed and are no longer required:
      linux-headers-4.10.0-22 linux-headers-4.10.0-22-generic
      linux-image-4.10.0-22-generic linux-image-extra-4.10.0-22-generic
      linux-signed-image-4.10.0-22-generic
    Use 'sudo apt autoremove' to remove them.
    0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
And i installed xubuntu and logged and settings are same. Missing icons. SO it is not about unity?
I have t hose enviroments [enter image description here][2]
[1]: [https://i.stack.imgur.com/jCM8h.jpg](https://i.stack.imgur.com/jCM8h.jpg)
[2]: [https://i.stack.imgur.com/no4Ox.jpg](https://i.stack.imgur.com/no4Ox.jpg)

---

