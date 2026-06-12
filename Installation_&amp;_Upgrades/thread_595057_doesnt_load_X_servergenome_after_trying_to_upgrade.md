---
title: "doesnt load X server/genome after trying to upgrade"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by code_linux on 2007-10-28
Yesterday, i tried to upgrade Ubuntu to 7.10 from 7.04. Everything was going on fine, but when programs were getting installed, it displayed errors for "genome-themes". The upgrade ended with prompting anything. 
I restarted and now X server doesnt load. I can switch between terminals but when i go to GUI, its still shows "wait" icon. 

Here's part of the main.log file...




2007-10-28 01:27:33,564 DEBUG dir '/usr' needs '556294144.0' of '<DistUpgradeControler.FreeSpace object at 0x4be35d0>' (2214718764.000000)
2007-10-28 01:27:33,564 DEBUG dir '/usr' needs '52428800' of '<DistUpgradeControler.FreeSpace object at 0x4be35d0>' (1658424620.000000)
2007-10-28 01:27:33,564 DEBUG dir '/boot' needs '31457280' of '<DistUpgradeControler.FreeSpace object at 0x4be35d0>' (1605995820.000000)
2007-10-28 01:27:33,565 DEBUG dir '/' needs '10485760' of '<DistUpgradeControler.FreeSpace object at 0x4be35d0>' (1574538540.000000)
2007-10-28 01:31:45,564 INFO using backports in '/tmp/tmpWbj1El/backports' 
2007-10-28 01:31:45,565 DEBUG have: ['/tmp/tmpWbj1El/backports/release-upgrader-dpkg_1.14.5ubuntu11.2_amd64.udeb', '/tmp/tmpWbj1El/backports/release-upgrader-apt_0.6.46.4ubuntu10.3_amd64.udeb']
2007-10-28 01:31:45,566 DEBUG setting MinAge to 10
2007-10-28 01:31:45,567 DEBUG no file '/etc/apt/apt.conf.d/25adept-archive-limits'
2007-10-28 03:52:44,157 ERROR IOError in cache.commit(): 'Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2_amd64.deb) Error reading from server. Remote end closed connection [IP: 91.189.88.46 80]
'. Retrying (currentTry: 0)
2007-10-28 03:53:03,063 INFO cache.commit()
2007-10-28 03:58:09,097 DEBUG got a conffile-prompt from dpkg for file: '/etc/login.defs'
2007-10-28 07:23:27,891 WARNING no activity on terminal for 240 seconds (Preparing to configure login)
2007-10-28 07:44:23,914 ERROR got an error from dpkg for pkg: 'gnome-themes': 'subprocess post-installation script returned error exit status 127
'
2007-10-28 07:44:24,060 ERROR got an error from dpkg for pkg: 'gnome-themes': 'subprocess post-installation script returned error exit status 127
'
2007-10-28 08:04:02,310 WARNING no activity on terminal for 240 seconds (Configuring gnome-themes)
2007-10-28 08:04:02,717 ERROR SystemError from cache.commit(): installArchives() failed
2007-10-28 08:04:45,152 DEBUG setting MinAge to 2
2007-10-28 08:04:45,153 DEBUG no file '/etc/apt/apt.conf.d/25adept-archive-limits'



And i should mention.. i had beryl installed with Ubuntu.. and had no problems with it. 

Also, is there a way to go back to the last working version and discard all the upgrade that was done! 

Thanks a lot!

---

### Post by Caffeine_Junky on 2007-10-29
Hmmm, ..I think a fresh install will be the best way out for you, but have a look at the following links anyway:

[https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)

[http://ubuntuforums.org/showthread.php?t=591814](http://ubuntuforums.org/showthread.php?t=591814)

---

