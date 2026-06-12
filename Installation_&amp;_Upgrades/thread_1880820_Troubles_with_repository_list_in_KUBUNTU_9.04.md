---
title: "Troubles with repository list in KUBUNTU 9.04"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by zolkin on 2011-11-14
Occasionally, my repository list doesn't work properly.
Before this day I used astromirror.uchicago but they stoped work.
After the editing of /etc/apt/source.list

**********************************************
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.                                    

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in     
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.                                                                   
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe                      
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe                  
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe              
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe          

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in      
## multiverse WILL NOT receive any review or updates from the Ubuntu        
## security team.                                                           
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse                     
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse                 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse             
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse         

## Uncomment the following two lines to add software from the 'backports'
## repository.                                                           
## N.B. software from this repository may not have been tested as        
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.                               
# deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is 
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.                                                                
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner                 
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner             

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe           
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe       
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse         
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse

#Added by software-properties
deb [http://ftp5.gwdg.de/pub/opensuse/repositories/home:/amilcarlucas/xUbuntu_9.04/](http://ftp5.gwdg.de/pub/opensuse/repositories/home:/amilcarlucas/xUbuntu_9.04/) ./
deb [http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu) jaunty main
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free #Skype

**********************************************
 My synaptic shows me the following after the reload

**********************************************
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: &#1057;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1080;&#1077; &#1087;&#1086;&#1076;&#1087;&#1080;&#1089;&#1080; &#1085;&#1077; &#1084;&#1086;&#1075;&#1091;&#1090; &#1073;&#1099;&#1090;&#1100; &#1087;&#1088;&#1086;&#1074;&#1077;&#1088;&#1077;&#1085;&#1099;, &#1090;&#1072;&#1082; &#1082;&#1072;&#1082; &#1085;&#1077;&#1076;&#1086;&#1089;&#1090;&#1091;&#1087;&#1077;&#1085; &#1086;&#1090;&#1082;&#1088;&#1099;&#1090;&#1099;&#1081; &#1082;&#1083;&#1102;&#1095;: NO_PUBKEY 2836CB0A8AC93F7A&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://ftp5.gwdg.de/pub/opensuse/repositories/home:/amilcarlucas/xUbuntu_9.04/./Packages](http://ftp5.gwdg.de/pub/opensuse/repositories/home:/amilcarlucas/xUbuntu_9.04/./Packages)  404 Not Found
&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found [IP: 91.189.92.170 80]
&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages)  404 Not Found [IP: 91.189.92.170 80]
&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources)  404 Not Found [IP: 91.189.92.170 80]
&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources)  404 Not Found [IP: 91.189.92.170 80]
&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.92.170 80]
&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources)  404 Not Found [IP: 91.189.92.170 80]
&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages)  404 Not Found [IP: 91.189.92.170 80]
&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources)  404 Not Found [IP: 91.189.92.170 80]
&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages)  404 Not Found [IP: 91.189.92.170 80]
&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages)  404 Not Found [IP: 91.189.92.170 80]
&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources)  404 Not Found [IP: 91.189.92.170 80]
&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources)  404 Not Found [IP: 91.189.92.170 80]
&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.92.170 80]
&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources)  404 Not Found [IP: 91.189.92.170 80]
&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages)  404 Not Found [IP: 91.189.92.170 80]
&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources)  404 Not Found [IP: 91.189.92.170 80]
&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages)  404 Not Found [IP: 91.189.92.170 80]
&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages)  404 Not Found [IP: 91.189.92.170 80]
&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources)  404 Not Found [IP: 91.189.92.170 80]
&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources)  404 Not Found [IP: 91.189.92.170 80]
&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.92.170 80]
&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources)  404 Not Found [IP: 91.189.92.170 80]
&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages)  404 Not Found [IP: 91.189.92.170 80]
&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources)  404 Not Found [IP: 91.189.92.170 80]
&#1053;&#1077;&#1082;&#1086;&#1090;&#1086;&#1088;&#1099;&#1077; &#1080;&#1085;&#1076;&#1077;&#1082;&#1089;&#1085;&#1099;&#1077; &#1092;&#1072;&#1081;&#1083;&#1099; &#1085;&#1077; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1083;&#1080;&#1089;&#1100;, &#1086;&#1085;&#1080; &#1073;&#1099;&#1083;&#1080; &#1087;&#1088;&#1086;&#1080;&#1075;&#1085;&#1086;&#1088;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1099; &#1080;&#1083;&#1080; &#1074;&#1084;&#1077;&#1089;&#1090;&#1086; &#1085;&#1080;&#1093; &#1073;&#1099;&#1083;&#1080; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1085;&#1099; &#1089;&#1090;&#1072;&#1088;&#1099;&#1077; &#1074;&#1077;&#1088;&#1089;&#1080;&#1080;
**********************************************

Any ideas how to fix it?

---

### Post by snowpine on 2011-11-14
Jaunty 9.04 is "end of life" and unsupported. Time to install a supported release (10.04 or newer) from: [http://kubuntu.com](http://kubuntu.com)

---

### Post by dniMretsaM on 2011-11-14
9.04 is no longer supported, that's the cause of the repository issues. Install a newer version (do a fresh install). 10.04 is the current LTS release, but I find 11.xx to be stable as well.

---

