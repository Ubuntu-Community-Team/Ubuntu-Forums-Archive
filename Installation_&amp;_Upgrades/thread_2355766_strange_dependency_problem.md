---
title: "strange dependency problem"
date: 2017-03-16
forum: Installation &amp; Upgrades
---

### Post by anutosho on 2017-03-16
For some time now I've got a dependency problem with kaffeine / libxine2,

Right now I have kaffeine installed when I do a dist-upgrade it tells me that it want to uninstall kaffeine due to unmet dependencies.

```
# LC_ALL=C aptitude dist-upgrade |tee upgrade.log 
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Building tag database...
The following packages will be upgraded:
  libxine2{b} 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2777 kB of archives. After unpacking 7608 kB will be used.
The following packages have unmet dependencies:
 libxine2 : Depends: libavcodec56-ffmpeg which is a virtual package and is not provided by any available package.

            Depends: libavformat56-ffmpeg which is a virtual package and is not provided by any available package.

            Depends: libavutil54-ffmpeg which is a virtual package and is not provided by any available package.

            Depends: libgraphicsmagick3 (>= 1.3.5) which is a virtual package and is not provided by any available package.

            Depends: libpostproc52 (>= 5:0.git20120217~) which is a virtual package and is not provided by any available package.

            Conflicts: libxine2-bin but 1.2.6-1build5 is installed.
            Conflicts: libxine2-ffmpeg but 1.2.6-1build5 is installed.
            Conflicts: libxine2-misc-plugins but 1.2.6-1build5 is installed.
            Conflicts: libxine2-x but 1.2.6-1build5 is installed.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     kaffeine                    
2)     libxine2                    

Accept this solution? [Y/n/q/?] 

```

I agreed and then tried to reinstall kaffeine and got this:

```
# LC_ALL=C aptitude install kaffeine |tee install.log
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Building tag database...
The following NEW packages will be installed:
  kaffeine libxine2{ab} 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 2777 kB/3227 kB of archives. After unpacking 10.1 MB will be used.
The following packages have unmet dependencies:
 libxine2 : Depends: libavcodec56-ffmpeg which is a virtual package and is not provided by any available package.

            Depends: libavformat56-ffmpeg which is a virtual package and is not provided by any available package.
            Depends: libavutil54-ffmpeg which is a virtual package and is not provided by any available package.
            Depends: libgraphicsmagick3 (>= 1.3.5) which is a virtual package and is not provided by any available package.
            Depends: libpostproc52 (>= 5:0.git20120217~) which is a virtual package and is not provided by any available package.

            Conflicts: libxine2-bin but 1.2.6-1build5 is installed.
            Conflicts: libxine2-ffmpeg but 1.2.6-1build5 is installed.
            Conflicts: libxine2-misc-plugins but 1.2.6-1build5 is installed.
            Conflicts: libxine2-x but 1.2.6-1build5 is installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     kaffeine [Not Installed]                           
2)     libxine2 [Not Installed]                           


Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:

     Install the following packages:    
1)     libxine2 [1.2.6-1build5 (xenial)]


Accept this solution? [Y/n/q/?] y
The following NEW packages will be installed:
  kaffeine libxine2{a} 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/451 kB of archives. After unpacking 2458 kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information...
Selecting previously unselected package libxine2.
(Reading database ... 277878 files and directories currently installed.)
Preparing to unpack .../libxine2_1.2.6-1build5_amd64.deb ...
Unpacking libxine2 (1.2.6-1build5) ...
Preparing to unpack .../kaffeine_1.2.2-3_amd64.deb ...
Unpacking kaffeine (1.2.2-3) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for menu (2.1.47ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Setting up libxine2 (1.2.6-1build5) ...
Setting up kaffeine (1.2.2-3) ...
Processing triggers for menu (2.1.47ubuntu1) ...
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Writing extended state information...
Building tag database...


```

Kaffeine is now installed and working, but with the next dist-upgrade I get the first error message again.

I have no idea what's going on here.

My sources.list looks like this

```

deb http://de.archive.ubuntu.com/ubuntu/ xenial restricted main universe multiverse
deb http://de.archive.ubuntu.com/ubuntu/ xenial-updates main restricted universe multiverse
deb http://de.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ xenial partner
deb http://security.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse

# from sources.list.d
deb http://ppa.launchpad.net/dobey/audiotools/ubuntu/ xenial main
deb http://dl.google.com/linux/earth/deb/ stable main 
deb http://dl.google.com/linux/talkplugin/deb/ stable main 
deb http://ppa.launchpad.net/kxstudio-debian/gcc5/ubuntu/ xenial main
deb http://ppa.launchpad.net/kxstudio-debian/gcc5-deps/ubuntu/ xenial main
deb [arch=amd64,i386] http://kxstudio.linuxaudio.org/repo/ gcc5 free
deb [arch=amd64,i386] http://kxstudio.linuxaudio.org/repo/ stable free 
deb [arch=amd64,i386] http://kxstudio.linuxaudio.org/repo/ gcc5 non-free
deb [arch=amd64,i386] http://kxstudio.linuxaudio.org/repo/ stable non-free 
deb https://deb.nodesource.com/node_6.x/ xenial main
deb http://ppa.launchpad.net/philip5/extra/ubuntu/ xenial main 
deb http://ppa.launchpad.net/videolan/stable-daily/ubuntu/ xenial main
deb http://ppa.launchpad.net/yavdr/testing-vdr/ubuntu/ trusty main 

```

I have no idea what libxine2{b} is . Obviously it's NOT the sameas libxine2 1.2.6-1build5 - but where does it comes from?

[edit] OK, now I've found the error. It was the old yavdr repository. Changing it to xenial fixed the problem.
Sorry for the noise[/edit]

---

