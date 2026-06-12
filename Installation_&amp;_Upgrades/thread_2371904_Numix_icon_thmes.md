---
title: "Numix icon thmes"
date: 2017-09-19
forum: Installation &amp; Upgrades
---

### Post by pizzipao2 on 2017-09-19
I tried to install numix icon set theme on Ubuntu 16.04 and I'm not able to install any other software or system update. At the command sudo apt-get install -f  the followning happen. Please anyone can help? 
```
sudo apt-get install -f
[sudo] password for pizzipao: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  wine-devel wine-devel-amd64 wine-devel-i386:i386
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  numix-icon-theme
The following NEW packages will be installed
  numix-icon-theme
0 to upgrade, 1 to newly install, 0 to remove and 36 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/2,110 kB of archives.
After this operation, 48.9 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 498116 files and directories currently installed.)
Preparing to unpack .../numix-icon-theme_0.3+900~201707122252~ubuntu16.04.1_all.deb ...
Unpacking numix-icon-theme (0.3+900~201707122252~ubuntu16.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/numix-icon-theme_0.3+900~201707122252~ubuntu16.04.1_all.deb (--unpack):
 trying to overwrite '/usr/share/icons/Numix/48/actions/document-send.svg', which is also in package numix-white-icons 1.1.5~xenial~NoobsLab.com
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/numix-icon-theme_0.3+900~201707122252~ubuntu16.04.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Frogs Hair on 2017-09-19
Hello:

It looks like you have a conflict with the Numix White theme and being that this is a 3rd party PPA you may have to let the people at noobslab know about it. I had the same problem with a PPA from this website. Are these sets from different PPA's ? The command I used to resolve this requires the aptitude package so try the command below instead. You may have a half installed package.


```
sudo dpkg --remove --force-remove-reinstreq numix-icon-theme
 
```


> Unpacking numix-icon-theme (0.3+900~201707122252~ubuntu16.04.1) ...dpkg: error processing archive /var/cache/apt/archives/numix-icon-theme_0.3+900~201707122252~ubuntu16.04.1_all.deb (--unpack): [COLOR=#b22222]trying to overwrite '/usr/share/icons/Numix/48/actions/document-send.svg', which is also in package numix-white-icons 1.1.5~xenial~NoobsLab.comdpkg-deb: error: subprocess paste was killed by signal (Broken pipe)[/COLOR]

---

### Post by pizzipao2 on 2017-09-19
Thanks Frogs
The PPA used was the following: sudo add-apt-repository ppa:numix/ppa. The command which resolved your issue, didn't work with me. Really I don't know what to do. [COLOR=#DDDDDD][FONT=monospace]
[/FONT][/COLOR]

---

### Post by Frogs Hair on 2017-09-19
You have two different PPAs with variations of the same icons. Let's try the other set.

```
sudo apt remove numix-white-icons
```

---

### Post by pizzipao2 on 2017-09-19
Keep doing the same. 

```
sudo apt remove numix-white-icons
[sudo] password for pizzipao: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 numix-icon-theme-circle : Depends: numix-icon-theme but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
pizzipao@pizzipao:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  wine-devel wine-devel-amd64 wine-devel-i386:i386
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  numix-icon-theme
The following NEW packages will be installed
  numix-icon-theme
0 to upgrade, 1 to newly install, 0 to remove and 36 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/2,110 kB of archives.
After this operation, 48.9 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Selecting previously unselected package numix-icon-theme.
(Reading database ... 498116 files and directories currently installed.)
Preparing to unpack .../numix-icon-theme_0.3+900~201707122252~ubuntu16.04.1_all.deb ...
Unpacking numix-icon-theme (0.3+900~201707122252~ubuntu16.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/numix-icon-theme_0.3+900~201707122252~ubuntu16.04.1_all.deb (--unpack):
 trying to overwrite '/usr/share/icons/Numix/48/actions/document-send.svg', which is also in package numix-white-icons 1.1.5~xenial~NoobsLab.com
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/numix-icon-theme_0.3+900~201707122252~ubuntu16.04.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Frogs Hair on 2017-09-19
Open software & updates and under the other software tab disable the noobslab ppa check box. Run the same command and highlight the text when you paste the output and use The # symbol from the tools wrap the text with code tags.

```
sudo apt remove numix-white-icons
```

If that fails try the following next.

```
sudo dpkg --remove -force --force-remove-reinstreqgrep ^ /etc/apt/sources.list /etc/apt/sources.list.d/* numix-white-icons
```

```
sudo apt update
```

---

