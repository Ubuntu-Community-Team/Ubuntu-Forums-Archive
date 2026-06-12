---
title: "Classic &quot;unmet dependencies&quot; issue"
date: 2015-01-01
forum: MINT
---

### Post by mbnoimi on 2015-01-01
I want to install "gradle" but unfortunately I faced "unmet dependencies" how can I fix this issue?

PS

[list]
[*]I read the mentioned solution in [http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa](http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa) but it didn't help me out :(
[*]I'm using Linux mint 17 x64 Cinnamon
[/list]

```
    mbnoimi-laptop mbnoimi # apt-get update && apt-get -y dist-upgrade && apt-get autoremove
    Ign http://dl.google.com stable InRelease
    Ign http://download.jitsi.org unstable/ InRelease                             
    Get:1 http://dl.google.com stable Release.gpg [198 B]                         
    Ign http://security.ubuntu.com trusty-security InRelease                       
    Get:2 http://download.jitsi.org unstable/ Release.gpg [72 B]                   
    Get:3 http://dl.google.com stable Release [1,338 B]                           
    Ign http://archive.canonical.com trusty InRelease                             
    Get:4 http://security.ubuntu.com trusty-security Release.gpg [933 B]           
    Get:5 http://download.jitsi.org unstable/ Release [1,547 B]                   
    Get:6 http://dl.google.com stable/main amd64 Packages [469 B]                 
    Get:7 http://security.ubuntu.com trusty-security Release [62.0 kB]             
    Ign http://archive.ubuntu.com trusty InRelease                                 
    Get:8 http://archive.canonical.com trusty Release.gpg [933 B]                 
    Get:9 http://download.jitsi.org unstable/ Packages [1,874 B]                   
    Get:10 http://dl.google.com stable/main i386 Packages [464 B]                 
    Get:11 http://archive.canonical.com trusty Release [9,359 B]                   
    Ign http://archive.ubuntu.com trusty-updates InRelease                         
    Get:12 http://repo.steampowered.com precise InRelease [2,840 B]               
    Get:13 http://security.ubuntu.com trusty-security/main amd64 Packages [182 kB]
    Get:14 http://archive.canonical.com trusty/partner amd64 Packages [5,562 B]   
    Get:15 http://archive.ubuntu.com trusty Release.gpg [933 B]                   
    Get:16 http://archive.canonical.com trusty/partner i386 Packages [6,252 B]     
    Get:17 http://archive.canonical.com trusty/partner Translation-en [4,561 B]   
    Get:18 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]           
    Get:19 http://archive.ubuntu.com trusty Release [58.5 kB]                     
    Get:20 http://security.ubuntu.com trusty-security/restricted amd64 Packages [8,861 B]
    Ign http://dl.google.com stable/main Translation-en_US                         
    Get:21 http://security.ubuntu.com trusty-security/universe amd64 Packages [76.0 kB]
    Ign http://dl.google.com stable/main Translation-en                           
    Ign http://download.jitsi.org unstable/ Translation-en_US                     
    Ign http://download.jitsi.org unstable/ Translation-en                         
    Get:22 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [1,143 B]
    Get:23 http://repo.steampowered.com precise/steam Sources [549 B]             
    Get:24 http://security.ubuntu.com trusty-security/main i386 Packages [174 kB] 
    Get:25 http://archive.ubuntu.com trusty-updates Release [62.0 kB]             
    Get:26 http://security.ubuntu.com trusty-security/restricted i386 Packages [8,832 B]
    Get:27 http://security.ubuntu.com trusty-security/universe i386 Packages [76.0 kB]
    Get:28 http://repo.steampowered.com precise/steam amd64 Packages [604 B]       
    Get:29 http://archive.ubuntu.com trusty/main amd64 Packages [1,350 kB]         
    Get:30 http://security.ubuntu.com trusty-security/multiverse i386 Packages [1,395 B]
    Get:31 http://security.ubuntu.com trusty-security/main Translation-en [91.4 kB]
    Get:32 http://security.ubuntu.com trusty-security/multiverse Translation-en [587 B]
    Get:33 http://repo.steampowered.com precise/steam i386 Packages [804 B]       
    Get:34 http://security.ubuntu.com trusty-security/restricted Translation-en [2,266 B]
    Get:35 http://security.ubuntu.com trusty-security/universe Translation-en [41.5 kB]
    Get:36 http://archive.ubuntu.com trusty/restricted amd64 Packages [13.0 kB]   
    Get:37 http://archive.ubuntu.com trusty/universe amd64 Packages [5,859 kB]     
    Get:38 http://archive.ubuntu.com trusty/multiverse amd64 Packages [132 kB]     
    Get:39 http://archive.ubuntu.com trusty/main i386 Packages [1,348 kB]         
    Ign http://ppa.launchpad.net trusty InRelease                                 
    Ign http://ppa.launchpad.net trusty InRelease                                 
    Ign http://ppa.launchpad.net trusty InRelease                                 
    Ign http://ppa.launchpad.net trusty InRelease                                 
    Ign http://packages.linuxmint.com qiana InRelease                             
    Ign http://extra.linuxmint.com qiana InRelease                                 
    Ign http://ppa.launchpad.net trusty InRelease                                 
    Ign http://ppa.launchpad.net trusty InRelease                                 
    Get:40 http://extra.linuxmint.com qiana Release.gpg [198 B]                   
    Get:41 http://packages.linuxmint.com qiana Release.gpg [198 B]                 
    Ign http://ppa.launchpad.net trusty InRelease                                 
    Ign http://ppa.launchpad.net trusty InRelease                                 
    Get:42 http://archive.ubuntu.com trusty/restricted i386 Packages [13.4 kB]     
    Ign http://ppa.launchpad.net trusty InRelease                                 
    Get:43 http://extra.linuxmint.com qiana Release [3,144 B]                     
    Get:44 http://packages.linuxmint.com qiana Release [18.6 kB]                   
    Ign http://ppa.launchpad.net trusty InRelease                                 
    Ign http://ppa.launchpad.net trusty InRelease                                 
    Get:45 http://archive.ubuntu.com trusty/universe i386 Packages [5,866 kB]     
    Ign http://ppa.launchpad.net trusty InRelease                                 
    Get:46 http://extra.linuxmint.com qiana/main amd64 Packages [7,906 B]         
    Get:47 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
    Get:48 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
    Get:49 http://extra.linuxmint.com qiana/main i386 Packages [7,890 B]           
    Get:50 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
    Get:51 http://packages.linuxmint.com qiana/main amd64 Packages [30.4 kB]       
    Get:52 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
    Get:53 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
    Get:54 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
    Get:55 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
    Get:56 http://packages.linuxmint.com qiana/upstream amd64 Packages [23.8 kB]   
    Get:57 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
    Get:58 http://ppa.launchpad.net trusty Release.gpg [836 B]                     
    Get:59 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
    Get:60 http://packages.linuxmint.com qiana/import amd64 Packages [32.5 kB]     
    Get:61 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
    Ign http://repo.steampowered.com precise/steam Translation-en_US               
    Get:62 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
    Ign http://repo.steampowered.com precise/steam Translation-en                 
    Get:63 http://ppa.launchpad.net trusty Release [14.0 kB]                       
    Get:64 http://ppa.launchpad.net trusty Release [15.1 kB]                       
    Get:65 http://ppa.launchpad.net trusty Release [15.1 kB]                       
    Get:66 http://packages.linuxmint.com qiana/backport amd64 Packages [20 B]     
    Get:67 http://archive.ubuntu.com trusty/multiverse i386 Packages [134 kB]     
    Get:68 http://ppa.launchpad.net trusty Release [15.1 kB]                       
    Get:69 http://ppa.launchpad.net trusty Release [15.1 kB]                       
    Get:70 http://ppa.launchpad.net trusty Release [14.0 kB]                       
    Get:71 http://packages.linuxmint.com qiana/romeo amd64 Packages [14.9 kB]     
    Get:72 http://ppa.launchpad.net trusty Release [14.0 kB]                       
    Get:73 http://ppa.launchpad.net trusty Release [14.0 kB]                       
    Get:74 http://ppa.launchpad.net trusty Release [15.1 kB]                       
    Get:75 http://ppa.launchpad.net trusty Release [15.1 kB]                       
    Get:76 http://packages.linuxmint.com qiana/main i386 Packages [29.7 kB]       
    Get:77 http://ppa.launchpad.net trusty Release [15.1 kB]                       
    Get:78 http://ppa.launchpad.net trusty Release [15.1 kB]                       
    Ign http://extra.linuxmint.com qiana/main Translation-en_US                   
    Get:79 http://ppa.launchpad.net trusty/main Sources [638 B]                   
    Get:80 http://ppa.launchpad.net trusty/main amd64 Packages [737 B]             
    Get:81 http://archive.ubuntu.com trusty/main Translation-en [762 kB]           
    Get:82 http://packages.linuxmint.com qiana/upstream i386 Packages [23.8 kB]   
    Get:83 http://ppa.launchpad.net trusty/main i386 Packages [737 B]             
    Get:84 http://ppa.launchpad.net trusty/main Sources [679 B]                   
    Get:85 http://packages.linuxmint.com qiana/import i386 Packages [32.5 kB]     
    Ign http://extra.linuxmint.com qiana/main Translation-en                       
    Get:86 http://ppa.launchpad.net trusty/main amd64 Packages [587 B]             
    Get:87 http://ppa.launchpad.net trusty/main i386 Packages [584 B]             
    Get:88 http://ppa.launchpad.net trusty/main Translation-en [402 B]             
    Get:89 http://ppa.launchpad.net trusty/main Sources [1,527 B]                 
    Get:90 http://ppa.launchpad.net trusty/main amd64 Packages [1,187 B]           
    Get:91 http://ppa.launchpad.net trusty/main i386 Packages [1,187 B]           
    Get:92 http://packages.linuxmint.com qiana/backport i386 Packages [20 B]       
    Get:93 http://archive.ubuntu.com trusty/multiverse Translation-en [102 kB]     
    Get:94 http://archive.ubuntu.com trusty/restricted Translation-en [3,457 B]   
    Get:95 http://ppa.launchpad.net trusty/main Translation-en [597 B]             
    Get:96 http://ppa.launchpad.net trusty/main Sources [20.0 kB]                 
    Get:97 http://packages.linuxmint.com qiana/romeo i386 Packages [14.9 kB]       
    Get:98 http://archive.ubuntu.com trusty/universe Translation-en [4,089 kB]     
    Get:99 http://ppa.launchpad.net trusty/main amd64 Packages [18.7 kB]           
    Get:100 http://ppa.launchpad.net trusty/main i386 Packages [18.7 kB]           
    Get:101 http://ppa.launchpad.net trusty/main Translation-en [15.3 kB]         
    Get:102 http://ppa.launchpad.net trusty/main Sources [14.9 kB]                 
    Get:103 http://ppa.launchpad.net trusty/main amd64 Packages [17.5 kB]         
    Get:104 http://ppa.launchpad.net trusty/main i386 Packages [17.4 kB]           
    Get:105 http://ppa.launchpad.net trusty/main Translation-en [9,473 B]         
    Get:106 http://ppa.launchpad.net trusty/main Sources [630 B]                   
    Get:107 http://ppa.launchpad.net trusty/main amd64 Packages [719 B]           
    Get:108 http://ppa.launchpad.net trusty/main i386 Packages [718 B]             
    Get:109 http://archive.ubuntu.com trusty-updates/main amd64 Packages [387 kB] 
    Get:110 http://ppa.launchpad.net trusty/main Sources [624 B]                   
    Get:111 http://ppa.launchpad.net trusty/main amd64 Packages [547 B]           
    Get:112 http://ppa.launchpad.net trusty/main i386 Packages [559 B]             
    Get:113 http://ppa.launchpad.net trusty/main Sources [733 B]                   
    Get:114 http://ppa.launchpad.net trusty/main amd64 Packages [521 B]           
    Get:115 http://ppa.launchpad.net trusty/main i386 Packages [529 B]             
    Get:116 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [8,861 B]
    Get:117 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [229 kB]
    Get:118 http://ppa.launchpad.net trusty/main Sources [1,765 B]                 
    Get:119 http://ppa.launchpad.net trusty/main amd64 Packages [1,671 B]         
    Get:120 http://ppa.launchpad.net trusty/main i386 Packages [1,680 B]           
    Get:121 http://ppa.launchpad.net trusty/main Translation-en [816 B]           
    Get:122 http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages [9,356 B]
    Get:123 http://ppa.launchpad.net trusty/main Sources [5,196 B]                 
    Get:124 http://archive.ubuntu.com trusty-updates/main i386 Packages [379 kB]   
    Get:125 http://ppa.launchpad.net trusty/main amd64 Packages [10.7 kB]       
    Get:126 http://ppa.launchpad.net trusty/main i386 Packages [10.7 kB]           
    Get:127 http://ppa.launchpad.net trusty/main Translation-en [4,512 B]         
    Get:128 http://ppa.launchpad.net trusty/main Sources [1,784 B]                 
    Get:129 http://ppa.launchpad.net trusty/main amd64 Packages [1,548 B]         
    Get:130 http://ppa.launchpad.net trusty/main i386 Packages [1,545 B]           
    Get:131 http://ppa.launchpad.net trusty/main Translation-en [866 B]           
    Get:132 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [8,832 B]
    Get:133 http://ppa.launchpad.net trusty/main Sources [6,495 B]                 
    Get:134 http://archive.ubuntu.com trusty-updates/universe i386 Packages [230 kB]
    Get:135 http://ppa.launchpad.net trusty/main amd64 Packages [9,597 B]         
    Get:136 http://ppa.launchpad.net trusty/main i386 Packages [9,897 B]           
    Get:137 http://ppa.launchpad.net trusty/main Translation-en [3,938 B]         
    Get:138 http://archive.ubuntu.com trusty-updates/multiverse i386 Packages [9,539 B]
    Get:139 http://archive.ubuntu.com trusty-updates/main Translation-en [181 kB] 
    Get:140 http://archive.ubuntu.com trusty-updates/multiverse Translation-en [4,719 B]
    Get:141 http://archive.ubuntu.com trusty-updates/restricted Translation-en [2,266 B]
    Get:142 http://archive.ubuntu.com trusty-updates/universe Translation-en [117 kB]
    Ign http://archive.ubuntu.com trusty/main Translation-en_US                   
    Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US             
    Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
    Ign http://archive.ubuntu.com trusty/restricted Translation-en_US             
    Ign http://ppa.launchpad.net trusty/main Translation-en                       
    Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
    Ign http://archive.ubuntu.com trusty/universe Translation-en_US               
    Ign http://ppa.launchpad.net trusty/main Translation-en                       
    Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
    Ign http://ppa.launchpad.net trusty/main Translation-en                       
    Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
    Ign http://ppa.launchpad.net trusty/main Translation-en                       
    Ign http://packages.linuxmint.com qiana/backport Translation-en_US             
    Ign http://packages.linuxmint.com qiana/backport Translation-en               
    Ign http://packages.linuxmint.com qiana/import Translation-en_US               
    Ign http://packages.linuxmint.com qiana/import Translation-en                 
    Ign http://packages.linuxmint.com qiana/main Translation-en_US                 
    Ign http://packages.linuxmint.com qiana/main Translation-en                   
    Ign http://packages.linuxmint.com qiana/romeo Translation-en_US               
    Ign http://packages.linuxmint.com qiana/romeo Translation-en                   
    Ign http://packages.linuxmint.com qiana/upstream Translation-en_US             
    Ign http://packages.linuxmint.com qiana/upstream Translation-en               
    Fetched 22.8 MB in 20s (1,085 kB/s)                                           
    Reading package lists... Done
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    Calculating upgrade... Done
    0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
    mbnoimi-laptop mbnoimi # apt-get install gradle
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    Some packages could not be installed. This may mean that you have
    requested an impossible situation or if you are using the unstable
    distribution that some required packages have not yet been created
    or been moved out of Incoming.
    The following information may help to resolve the situation:

    The following packages have unmet dependencies:
     gradle : Depends: libgradle-plugins-java (= 1.4-2ubuntu1) but it is not going to be installed
    E: Unable to correct problems, you have held broken packages.
    mbnoimi-laptop mbnoimi #

```

---

### Post by overdrank on 2015-01-01
Hello, thread moved to MINT

---

### Post by slickymaster on 2015-01-01
Try it this way, so you can get all the dependencies fulfilled:```
sudo add-apt-repository ppa:cwchien/gradle
sudo apt-get update
sudo apt-get install gradle
```

Please refer to [https://bugs.launchpad.net/linuxmint/+bug/1335390](https://bugs.launchpad.net/linuxmint/+bug/1335390)

---

