---
title: "Upgrade to 7.1 now PC freezes before GUI . . ."
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by MatthewJS on 2007-11-07
. . . loads.
My wife selected upgrade on her Feisty upgrade manager. It ran for some time and then froze. After a few hours I rebooted. Now, when it boots, it stops before loading the GUI (i.e. just after the Ubuntu progress bar has been cleared off the screen). 

If I go into rescue mode I can see her data files etc. but I have no idea how to rescue the GUI.

I would hugely appreciate any support.

Matthew

The selected lines from the upgrade log are as follows:
> 
2007-11-07 06:40:52,981 INFO release-upgrader version '0.81' started
2007-11-07 06:40:55,515 DEBUG lsb-release: 'feisty'
2007-11-07 06:40:55,515 DEBUG _pythonSymlinkCheck run
2007-11-07 06:40:58,691 DEBUG checkViewDepends()
2007-11-07 06:41:00,459 DEBUG Foreign: 
2007-11-07 06:41:00,459 DEBUG Obsolete: 
2007-11-07 06:41:00,461 DEBUG updateSourcesList()
2007-11-07 06:41:00,559 DEBUG rewriteSourcesList()
2007-11-07 06:41:00,564 DEBUG examining: 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted'
2007-11-07 06:41:00,564 DEBUG entry 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted' updated to new dist
2007-11-07 06:41:00,565 DEBUG examining: 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted'
2007-11-07 06:41:00,565 DEBUG entry 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted' updated to new dist
.
.
.
2007-11-07 06:44:27,128 INFO using backports in '/tmp/tmpn3kBIw/backports' 
2007-11-07 06:44:27,129 DEBUG have: ['/tmp/tmpn3kBIw/backports/release-upgrader-apt_0.6.46.4ubuntu10.3_i386.udeb', '/tmp/tmpn3kBIw/backports/release-upgrader-dpkg_1.14.5ubuntu11.2_i386.udeb']
2007-11-07 06:44:27,130 DEBUG setting MinAge to 10
2007-11-07 06:44:27,131 DEBUG no file '/etc/apt/apt.conf.d/25adept-archive-limits'
2007-11-07 06:44:47,817 DEBUG cancelClicked
2007-11-07 06:44:47,841 ERROR IOError in cache.commit(): 'Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/p/perl/libperl5.8_5.8.8-7ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/perl/libperl5.8_5.8.8-7ubuntu3_i386.deb) 
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/p/perl/perl-base_5.8.8-7ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/perl/perl-base_5.8.8-7ubuntu3_i386.deb) 
.
.
.
Gazillions of failed to fetches
.
.
.
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/b/brltty/brltty-x11_3.7.2-7.1ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/b/brltty/brltty-x11_3.7.2-7.1ubuntu1_i386.deb) 
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/b/brltty/brltty_3.7.2-7.1ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/b/brltty/brltty_3.7.2-7.1ubuntu1_i386.deb) 
'. Retrying (currentTry: 2)
2007-11-07 06:44:48,754 ERROR giving up on fetching after maximum retries


---

