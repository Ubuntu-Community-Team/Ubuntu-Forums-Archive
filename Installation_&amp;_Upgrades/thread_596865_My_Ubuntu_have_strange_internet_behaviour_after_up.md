---
title: "My Ubuntu have strange internet behaviour after upgraded to Gutsy..."
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by cloudstrife87 on 2007-10-30
I had a very strange internet behaviour after upgrading from Feisty to Gutsy, which previously work perfectly in Feisty using my prolink wireless adapter or ethernet.

First of all, it detects my network but there's no internet connection, therefore i googled and finally found a solution:

Add "blacklist ipv6" in "/etc/modprobe.d/blacklist"

I was so excited as my firefox finally loads webpages, but wait, why doesn't my apt-get and update manager works?? it stucked at connecting to the ubuntu server and connection time out, sigh...

Later on, i tried on searching on best ubuntu servers through system > administration > software sources > ubuntu software tab > download from: > other > select best server. It tested all servers and selected a Taiwan server for me (mirror.nttu.edu.tw), then i try apt-get again, it works!!! so i thought its may be its bcoz incorrect server address.

After a few minutes later, when i try apt-get update again, omg, the similar time out problem appears again, then i repeated the select best server process again, it still selects the same taiwan server as before. Then i tried apt-get update again, whoa it works again. strange...

Then i used add/remove programs, tried to install the macromedia flash plugin, but during the installation, it requires to connect to [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz), and guess what, the connection time out again. So i just close the installation and load Add/remove programs to install other programs. omg, it got error to install other programs and asked me to load dpkg --configure -a. it must be half way flash installation that causes it. so i run dpkg --configure -a, and as expected, the installation stucked at connecting fpdownload.macromedia.com.

I tried to download the [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz) manually from firefox, however, i didnt know how to install it manually...

I was so dissapointed, and tried dpkg --configure -a again. voila!! it finally connected to fpdownload.macromedia.com and completed the flash installation finally. strange strange...

Later i tried to install another program (can't remember whats the name), similar to above, it stuck at connecting to  [http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe). so i manually download that andale32.exe in firefox then load load dpkg --configure -a again. whoa, it installation runs smoothly...

Then i try to run apt-get update, as expected it has connection time out. So i try load the Taiwan ubuntu server address at firefox ([http://mirror.nttu.edu.tw/](http://mirror.nttu.edu.tw/)). Then i run apt-get update again. Ya, it works again, strange strange strange......

Anyone here have any idea what happened for my internet settings? I've sicked of everytime need to load the address manually in firefox before the installation and apt-get works. Plus my pidgin stil unable to connect to msn and yahoo yet....

---

### Post by njh on 2007-11-04
does this help: [http://ubuntuforums.org/showthread.php?p=1486101](http://ubuntuforums.org/showthread.php?p=1486101)

---

