---
title: "Why dpkg speaks chineese in gnome-terminal."
date: 2011-11-19
forum: Installation &amp; Upgrades
---

### Post by v_mil on 2011-11-19
Dear All!
After upgrading from Natty to Oneiric dpkg speaks English or Ukrainian.
After HDD change and clean installation dpkg starts speak chineese in gnome-terminal. I don't understand it.  All other terminal applications speaks Ukrainian or English. 
The locale of interface is Ukrainian. How to switch dpkg to Ukrainian or English?
I try to press CTRL+ALT+1, login and use dpkg. It works without any locale problem. Please, help me!
With best regards.
Viktor.

IN GNOME-TERMINAL:
TROUBLE:
~$ dpkg
dpkg: error: &#38656;&#35201;&#19968;&#20010;&#25351;&#31034;&#25805;&#20316;&#30340;&#36873;&#39033;

&#36755;&#20837; dpkg --help &#21487;&#33719;&#24471;&#23433;&#35013;&#21644;&#21368;&#36733;&#36719;&#20214;&#21253;&#30340;&#26377;&#20851;&#24110;&#21161; 
[*]&#65307;
&#20351;&#29992; dselect &#25110;&#26159; aptitude &#23601;&#33021;&#22312;&#21451;&#22909;&#30340;&#30028;&#38754;&#19979;&#31649;&#29702;&#36719;&#20214;&#21253;&#65307;
&#36755;&#20837; dpkg -Dhelp &#21487;&#30475;&#21040; dpkg &#38500;&#38169;&#26631;&#24535;&#30340;&#20540;&#30340;&#21015;&#34920;&#65307;
&#36755;&#20837; dpkg --force-help &#21487;&#33719;&#24471;&#25152;&#26377;&#24378;&#21046;&#25805;&#20316;&#36873;&#39033;&#30340;&#21015;&#34920;&#65307;
&#36755;&#20837; dpkg-deb --help &#21487;&#33719;&#24471;&#26377;&#20851;&#25805;&#20316; *.deb &#25991;&#20214;&#30340;&#24110;&#21161;&#65307;

&#24102;&#26377; 
[*] &#30340;&#36873;&#39033;&#23558;&#20250;&#36755;&#20986;&#36739;&#22823;&#31687;&#24133;&#30340;&#25991;&#23383; - &#21487;&#20351;&#29992;&#31649;&#36947;&#23558;&#20854;&#36755;&#20986;&#36830;&#25509;&#21040; less &#25110; more &#65281;

NORMAL BEHAVIOUR (English/Ukrainian):
~$ cd 123
bash: cd: 123: No such file or directory
user@Notebook:~$ sudo apt-get update
&#1030;&#1075;&#1085; [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease
&#1030;&#1075;&#1085; [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                    
&#1030;&#1075;&#1085; [http://ua.archive.ubuntu.com](http://ua.archive.ubuntu.com) oneiric InRelease                           
&#1030;&#1075;&#1085; [http://ua.archive.ubuntu.com](http://ua.archive.ubuntu.com) oneiric-updates InRelease                   
&#1030;&#1075;&#1085; [http://ua.archive.ubuntu.com](http://ua.archive.ubuntu.com) oneiric-backports InRelease                 
&#1030;&#1075;&#1085; [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                               
&#1042; &#1082;&#1077;&#1096;&#1110; [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                          
&#1042; &#1082;&#1077;&#1096;&#1110; [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg               
&#1042; &#1082;&#1077;&#1096;&#1110; [http://ua.archive.ubuntu.com](http://ua.archive.ubuntu.com) oneiric Release.gpg                      
&#1054;&#1090;&#1088;:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                   
...
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: &#1057;&#1083;&#1110;&#1076;&#1091;&#1102;&#1095;&#1110; &#1087;&#1110;&#1076;&#1087;&#1080;&#1089;&#1080; &#1085;&#1077; &#1084;&#1086;&#1078;&#1091;&#1090;&#1100; &#1073;&#1091;&#1090;&#1080; &#1087;&#1077;&#1088;&#1077;&#1074;&#1110;&#1088;&#1077;&#1085;&#1110;, &#1090;&#1086;&#1084;&#1091; &#1097;&#1086;, &#1087;&#1091;&#1073;&#1083;&#1110;&#1095;&#1085;&#1080;&#1081; &#1082;&#1083;&#1102;&#1095; &#1074;&#1110;&#1076;&#1089;&#1091;&#1090;&#1085;&#1110;&#1081;: NO_PUBKEY 5A9A06AEF9CB8DB0

---

