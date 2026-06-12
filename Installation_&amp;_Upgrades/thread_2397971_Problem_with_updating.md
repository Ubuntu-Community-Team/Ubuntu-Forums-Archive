---
title: "Problem with updating"
date: 2018-08-06
forum: Installation &amp; Upgrades
---

### Post by Ursus Maritimus on 2018-08-06
Hi,

I've got 14.04 LTS and have problems with updating.. I've tried different thread options from here and google, but I haven't been able to find a solution. Was updating via Terminal and the reply was:
N: Ignoring file 'google-chrome.list.save.1' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
W: Failed to fetch [http://dl.google.com/linux/earth/deb/dists/stable/Release](http://dl.google.com/linux/earth/deb/dists/stable/Release)  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

Any ideas, what should I try and do..?

Thanks

---

### Post by Impavidus on 2018-08-06
The first is a note. It informs you that some file is ignored. Judging from its name, it's probably a dublicate or a backup. Do you have another file there with the same contents? Then it can be safely ignored or you can delete the file.

The second is a warning. The repository for Google Earth only has a 64 bit version available, but your computer tries to find the 32 bit version. Are you running a 32 or 64 bit OS? Google has dropped support for 32 bits.

---

### Post by Ursus Maritimus on 2018-08-07
Thanks for the info. What's the part I should delete, this is stopping me running updates manually via terminal. I got that part from the text I read, but cause I'm running 64, I don't understand how is it still affecting me.. Earlier I got the same type of messages related to google earth and I thought sorting that, everything would be fine.. But I guess not.

---

### Post by Impavidus on 2018-08-08
This is not stopping the updates. It's a warning, not an error. At worst, it stops you from upgrading from the google earth repository.

For the first one, what's present in /etc/apt/sources.list.d/ ?```
ls -l /etc/apt/sources.list.d
```

For the second, what do you get from```
uname -a
dpkg --list google*
```

---

### Post by Ursus Maritimus on 2018-08-17
The first one gave me this:
-rw-r--r-- 1 root root 210 Aug  6 12:23 clipgrab-team-ppa-trusty.list
-rw-r--r-- 1 root root 210 Aug  6 12:23 clipgrab-team-ppa-trusty.list.save
-rw-r--r-- 1 root root 134 Aug  6 12:23 deluge-team-ppa-trusty.list
-rw-r--r-- 1 root root 134 Aug  6 12:23 deluge-team-ppa-trusty.list.save
-rw-r--r-- 1 root root 189 Aug  6 12:23 google-chrome.list
-rw-r--r-- 1 root root 189 Aug  6 11:40 google-chrome.list~
-rw-r--r-- 1 root root 189 Aug  6 12:23 google-chrome.list.save
-rw-r--r-- 1 root root 191 Jun  7 12:01 google-chrome.list.save.1
-rw------- 1 root root   1 May 22 23:46 google-earth.list.save
-rw-r--r-- 1 root root 175 Aug  6 12:23 google-earth-pro.list
-rw-r--r-- 1 root root 175 Aug  6 12:23 google-earth-pro.list.save
-rw-r--r-- 1 root root 142 Aug  6 12:23 mc3man-trusty-media-trusty.list
-rw-r--r-- 1 root root 142 Aug  6 12:23 mc3man-trusty-media-trusty.list.save
-rw-r--r-- 1 root root 144 Aug  6 12:23 nilarimogard-webupd8-trusty.list
-rw-r--r-- 1 root root 144 Aug  6 12:23 nilarimogard-webupd8-trusty.list.save
-rw-r--r-- 1 root root 146 Aug  6 12:23 n-muench-programs-ppa-trusty.list
-rw-r--r-- 1 root root 146 Aug  6 12:23 n-muench-programs-ppa-trusty.list.save
-rw-r--r-- 1 root root 150 Aug  6 12:23 otto-kesselgulasch-gimp-trusty.list
-rw-r--r-- 1 root root 150 Aug  6 12:23 otto-kesselgulasch-gimp-trusty.list.save
-rw-r--r-- 1 root root 264 Aug  6 12:23 qbittorrent-team-qbittorrent-stable-trusty.list
-rw-r--r-- 1 root root 264 Aug  6 12:23 qbittorrent-team-qbittorrent-stable-trusty.list.save
-rw-r--r-- 1 root root 262 Aug  6 12:23 rvm-smplayer-trusty.list
-rw-r--r-- 1 root root 262 Aug  6 12:23 rvm-smplayer-trusty.list.save
-rw-r--r-- 1 root root  56 Aug  6 13:10 skype-stable.list
-rw-r--r-- 1 root root  56 Aug  6 12:23 skype-stable.list.save
-rw-r--r-- 1 root root 142 Aug  6 12:23 strukturag-libde265-trusty.list
-rw-r--r-- 1 root root 142 Aug  6 12:23 strukturag-libde265-trusty.list.save

---

### Post by Ursus Maritimus on 2018-08-17
2nd:

Linux jsu-X201EV 4.4.0-132-generic #158~14.04.1-Ubuntu SMP Thu Aug 2 13:54:18 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

and 

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  google-chrome- 68.0.3440.84 amd64        The web browser from Google
ii  google-earth-p 7.3.2.5491-r amd64        Explore, search and discover the

---

### Post by Impavidus on 2018-08-18
I think you can safely remove /etc/apt/sources.list.d/google-chrome.list.save.1. It only has two bytes more than the other files with similar names and isn't used anyway. Just to be sure, have a look at its contents and compare them to the contents of /etc/apt/sources.list.d/google-chrome.list.save.

As for the second, your system is 64 bit and you run 64 bit google earth and chrome. You can force the system to check for 64 bit updates only. Open the list file for google earth (I think it's /etc/apt/sources.list.d/google-earth-pro.list) and make sure it says [arch=amd64] between the word deb and the url, separated with spaces from both. And have a look at [this related thread](https://ubuntuforums.org/showthread.php?t=2398421&p=13791423#post13791423), posts 6 and 7 and links therein.

---

### Post by Ursus Maritimus on 2018-09-12
Thanks for the help, even you wrote them a while go.. I'm not for sure, what should I do in first part. 2nd, I tried to follow the links and instructions, but it didn't do anything.. Or I didn't do right things.. Anyway, the reply was this:

N: Ignoring file 'google-chrome.list.save.1' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
W: Failed to fetch [http://dl.google.com/linux/earth/deb/dists/stable/Release](http://dl.google.com/linux/earth/deb/dists/stable/Release)  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)


E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Ursus Maritimus on 2018-09-12
Somehow sorted, I think.. Via terminal, I can't get update to go through, but with software updater, things worked.. Even google earth stable worked.. Weird, but ok.. :)

---

