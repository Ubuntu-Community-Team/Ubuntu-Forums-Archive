---
title: "package updater is stuck ubuntu 19.04"
date: 2019-05-01
forum: Installation &amp; Upgrades
---

### Post by newblank25 on 2019-05-01
I went to use package updater to check on any updates and it stops halfway thru. it won't reset after computer is shut down. I  tried  to update system via terminal command of sudo apt get install & update and still stuck. Any help would be appreciated.Thx

---

### Post by oldos2er on 2019-05-01
Can you please post the full output of the commands you ran?

---

### Post by newblank25 on 2019-05-01
```
You have 2879 packages (100.0%) that can not/no-longer be downloaded
You have 0 packages (0.0%) that are unsupported
```




```
Run with --show-unsupported, --show-supported or --show-all to see more details
michael@michael-p7-1456c:~$ --show-unsupported
--show-unsupported: command not found
michael@michael-p7-1456c:~$ sudo apt update
[sudo] password for michael: 
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [109 kB]
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco InRelease [257 kB]                
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [109 kB]     
Ign:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main Sources [335 kB] 
Get:6 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release [943 B]             
Get:7 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release.gpg [819 B]         
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe Sources [254 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/restricted Sources [2,536 B]
Get:10 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable/main amd64 Packages [1,092 B]
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security InRelease [88.4 kB]    
Get:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates InRelease [97.5 kB]
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Sources [145 kB]
Get:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted Sources [2,116 B]
Get:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-backports InRelease [88.8 kB]
Get:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security InRelease [88.4 kB]
Get:17 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security/multiverse amd64 c-n-f Metadata [116 B]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security/main amd64 Packages [17.7 kB]
Get:19 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security/main i386 Packages [17.7 kB]
Get:20 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/main i386 Packages [981 kB]      
Get:21 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security/main Translation-en [8,064 B]
Get:22 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security/main amd64 DEP-11 Metadata [17.8 kB]
Get:23 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security/main DEP-11 48x48 Icons [1,417 B]
Get:24 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security/main DEP-11 64x64 Icons [1,308 B]
Get:25 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security/main amd64 c-n-f Metadata [1,172 B]
Get:26 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security/universe i386 Packages [7,484 B]
Get:27 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security/universe amd64 Packages [7,472 B]
Get:28 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security/universe Translation-en [3,796 B]
Get:29 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security/universe amd64 c-n-f Metadata [304 B]
Get:30 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security/restricted amd64 c-n-f Metadata [116 B]
Get:31 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/main amd64 Packages [995 kB]
Get:32 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/main Translation-en [509 kB]
Get:33 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/main amd64 DEP-11 Metadata [499 kB]
Get:34 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/main DEP-11 48x48 Icons [97.2 kB]
Get:35 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/main DEP-11 64x64 Icons [179 kB]
Get:36 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/main amd64 c-n-f Metadata [30.0 kB]
Get:37 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/restricted amd64 Packages [14.0 kB]
Get:38 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/restricted i386 Packages [11.1 kB]
Get:39 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/restricted Translation-en [4,960 B]
Get:40 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/restricted amd64 c-n-f Metadata [348 B]
Get:41 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/universe i386 Packages [9,008 kB]
Get:42 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/universe amd64 Packages [9,065 kB]
Get:43 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/universe Translation-en [5,251 kB]
Get:44 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/universe amd64 DEP-11 Metadata [3,546 kB]
Get:45 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/universe DEP-11 48x48 Icons [2,759 kB]
Get:46 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/universe DEP-11 64x64 Icons [8,369 kB]
Get:47 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/universe amd64 c-n-f Metadata [277 kB]
Get:48 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/multiverse i386 Packages [145 kB]
Get:49 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/multiverse amd64 Packages [157 kB]
Get:50 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/multiverse Translation-en [112 kB]
Get:51 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/multiverse amd64 DEP-11 Metadata [51.3 kB]
Get:52 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/multiverse DEP-11 48x48 Icons [10.8 kB]
Get:53 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/multiverse DEP-11 64x64 Icons [221 kB]
Get:54 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/multiverse amd64 c-n-f Metadata [9,348 B]
Get:55 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates/restricted amd64 c-n-f Metadata [116 B]
Get:56 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates/main amd64 Packages [24.5 kB]
Get:57 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates/main i386 Packages [22.6 kB]
Get:58 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates/main Translation-en [10.1 kB]
Get:59 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates/main amd64 DEP-11 Metadata [38.0 kB]
Get:60 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates/main DEP-11 48x48 Icons [2,258 B]
Get:61 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates/main DEP-11 64x64 Icons [2,084 B]
Get:62 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates/main amd64 c-n-f Metadata [1,396 B]
Get:63 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates/universe i386 Packages [12.6 kB]
Get:64 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates/universe amd64 Packages [12.6 kB]
Get:65 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates/universe Translation-en [5,544 B]
Get:66 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates/universe amd64 DEP-11 Metadata [612 B]
Get:67 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates/universe DEP-11 48x48 Icons [4,031 B]
Get:68 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates/universe DEP-11 64x64 Icons [29 B]
Get:69 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates/universe amd64 c-n-f Metadata [612 B]
Get:70 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates/multiverse amd64 c-n-f Metadata [116 B]
Get:71 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-backports/main amd64 c-n-f Metadata [112 B]
Get:72 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-backports/restricted amd64 c-n-f Metadata [116 B]
Get:73 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-backports/universe amd64 Packages [2,884 B]
Get:74 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-backports/universe i386 Packages [2,884 B]
Get:75 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-backports/universe Translation-en [1,268 B]
Get:76 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-backports/universe amd64 DEP-11 Metadata [7,164 B]
Get:77 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-backports/universe DEP-11 48x48 Icons [29 B]
Get:78 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-backports/universe DEP-11 64x64 Icons [29 B]
Get:79 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-backports/universe amd64 c-n-f Metadata [188 B]
Get:80 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-backports/multiverse amd64 c-n-f Metadata [116 B]
Get:81 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security/main amd64 Packages [17.7 kB]
Get:82 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security/main i386 Packages [17.7 kB]
Get:83 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security/main Translation-en [8,064 B]
Get:84 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security/main amd64 DEP-11 Metadata [17.8 kB]
Get:85 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security/main DEP-11 48x48 Icons [1,417 B]
Get:86 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security/main DEP-11 64x64 Icons [1,308 B]
Get:87 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security/main amd64 c-n-f Metadata [1,172 B]
Get:88 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security/restricted amd64 c-n-f Metadata [116 B]
Get:89 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security/universe amd64 Packages [7,472 B]
Get:90 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security/universe i386 Packages [7,484 B]
Get:91 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security/universe Translation-en [3,796 B]
Get:92 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security/universe amd64 c-n-f Metadata [304 B]
Get:93 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security/multiverse amd64 c-n-f Metadata [116 B]
Fetched 44.2 MB in 12s (3,631 kB/s)                                            
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
W: Skipping acquire of configured file 'main'/binary-amd64/Packages' as repository 'http://archive.ubuntu.com/ubuntu disco InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/binary-i386/Packages' as repository 'http://archive.ubuntu.com/ubuntu disco InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/i18n/Translation-en' as repository 'http://archive.ubuntu.com/ubuntu disco InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/i18n/Translation-en_US' as repository 'http://archive.ubuntu.com/ubuntu disco InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/dep11/Components-amd64.yml' as repository 'http://archive.ubuntu.com/ubuntu disco InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/dep11/icons-48x48.tar' as repository 'http://archive.ubuntu.com/ubuntu disco InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/dep11/icons-64x64.tar' as repository 'http://archive.ubuntu.com/ubuntu disco InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/cnf/Commands-amd64' as repository 'http://archive.ubuntu.com/ubuntu disco InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/binary-i386/Packages' as repository 'http://security.ubuntu.com/ubuntu disco-security InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/binary-amd64/Packages' as repository 'http://security.ubuntu.com/ubuntu disco-security InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/i18n/Translation-en_US' as repository 'http://security.ubuntu.com/ubuntu disco-security InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/i18n/Translation-en' as repository 'http://security.ubuntu.com/ubuntu disco-security InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/dep11/Components-amd64.yml' as repository 'http://security.ubuntu.com/ubuntu disco-security InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/dep11/icons-48x48.tar' as repository 'http://security.ubuntu.com/ubuntu disco-security InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/dep11/icons-64x64.tar' as repository 'http://security.ubuntu.com/ubuntu disco-security InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/cnf/Commands-amd64' as repository 'http://security.ubuntu.com/ubuntu disco-security InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/binary-i386/Packages' as repository 'http://archive.ubuntu.com/ubuntu disco-updates InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/binary-amd64/Packages' as repository 'http://archive.ubuntu.com/ubuntu disco-updates InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/i18n/Translation-en_US' as repository 'http://archive.ubuntu.com/ubuntu disco-updates InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/i18n/Translation-en' as repository 'http://archive.ubuntu.com/ubuntu disco-updates InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/dep11/Components-amd64.yml' as repository 'http://archive.ubuntu.com/ubuntu disco-updates InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/dep11/icons-48x48.tar' as repository 'http://archive.ubuntu.com/ubuntu disco-updates InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/dep11/icons-64x64.tar' as repository 'http://archive.ubuntu.com/ubuntu disco-updates InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/cnf/Commands-amd64' as repository 'http://archive.ubuntu.com/ubuntu disco-updates InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
michael@michael-p7-1456c:~$ apt list --upgradable
Listing... Done
michael@michael-p7-1456c:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
michael@michael-p7-1456c:~$ sudo apt upgrade
[sudo] password for michael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
michael@michael-p7-1456c:~$ sudo apt dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
michael@michael-p7-1456c:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
michael@michael-p7-1456c:~$ 
```
Still stuck thx for help.

---

### Post by newblank25 on 2019-05-01
i also tried uninstalling and a reinstall which didn't work.

---

### Post by rsteinmetz70112 on 2019-05-01
What does ```
sudo apt install -f 
```do?

What does```
sudo dpkg --configure -a do
```?

---

### Post by Impavidus on 2019-05-02
Show the contents of your sources.list:```
cat /etc/apt/sources.list
```

---

### Post by newblank25 on 2019-05-02
# N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco main'
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) disco-security multiverse main universe restricted main'
# deb [arch=amd64,i386] [http://repo.vivaldi.com/stable/deb/](http://repo.vivaldi.com/stable/deb/) stable main # disabled on upgrade to disco

---

### Post by dino99 on 2019-05-02
As your installation is 'disco', remove everything else from /etc/apt/sources.list.
Then clean the system via: clean,autoclean,autoremove,gtkorphan,bleachbit (as root, carefully select options).
Log out/in, and from a terminal: update, then run 'sudo apt -f install' and 'sudo dpkg --configure -a' .
Take note of the warnings/errors at that step (we need to know if the ' /var/lib/dpkg/status' is corrupted or not; if corrupted, about which package(s)).

Post to let us know.

---

### Post by Impavidus on 2019-05-02
You've got a stray apostrophe in two entries, which generate warnings in apt update, you've got a xenial repository that should be removed and some of the disco repositories are missing. Best to make a backup of your current /etc/apt/sources.list (although it's more or less useless) and start fresh. Use this as your new sources.list:```
deb http://archive.ubuntu.com/ubuntu disco main universe restricted multiverse
#deb-src http://archive.ubuntu.com/ubuntu disco main universe restricted multiverse

deb http://archive.ubuntu.com/ubuntu disco-updates main universe restricted multiverse
#deb-src http://archive.ubuntu.com/ubuntu disco-updates main universe restricted multiverse

deb http://archive.ubuntu.com/ubuntu disco-backports main universe restricted multiverse
#deb-src http://archive.ubuntu.com/ubuntu disco-backports main universe restricted multiverse

deb http://security.ubuntu.com/ubuntu disco-security main universe restricted multiverse
#deb-src http://security.ubuntu.com/ubuntu disco-security main universe restricted multiverse
```You can enable the source repositories if you wish, but you don't have to. There are some ways to tweak this, but that should give you something decent.

I hope I got that one right. I'm using cosmic myself.

---

### Post by newblank25 on 2019-05-02
I ran bleach as root. Isn't the command **sudo apt-get clea**n the one to use? &the same for others.This is what i got when running sudo apt-get autoremove
sudo apt-get autoremove
[sudo] password for michael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
used terminal for [COLOR=#000000]/var/lib/dpkg/status and got this result what did I do wrong?[/COLOR]
michael@michael-p7-1456c:~$ /var/lib/dpkg/status
bash: /var/lib/dpkg/status: Permission denied
thx for help

---

### Post by newblank25 on 2019-05-03
is this the same as package updater
[COLOR=#242729][FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif]sudo -- sh -c 'apt-get update; apt-get upgrade -y; apt-get dist-upgrade -y; apt-get autoremove -y; apt-get autoclean -y'[/FONT][/COLOR]or [COLOR=#242729][FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif]wajigdailyupgrade
let me know thx[/FONT][/COLOR]

---

