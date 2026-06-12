---
title: "can not download videos using youtube-dl"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by bilol on 2011-02-03
Dear all,
First I install youtube-dl to download youtube videos

```
dhiman@dhiman-desktop:~$ sudo apt-get install youtube-dl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-24 linux-headers-2.6.32-24-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  rtmpdump
The following NEW packages will be installed:
  youtube-dl
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/25.0kB of archives.
After this operation, 119kB of additional disk space will be used.
Selecting previously deselected package youtube-dl.
(Reading database ... 272752 files and directories currently installed.)
Unpacking youtube-dl (from .../youtube-dl_2010.04.04-1_all.deb) ...
Processing triggers for man-db ...
Setting up youtube-dl (2010.04.04-1) ...

```

Then I tried to download the video but in vain. 
```
dhiman@dhiman-desktop:~$ youtube-dl "http://www.youtube.com/watch?v=RTR12eM1-Xc"[youtube] Setting language
[youtube] RTR12eM1-Xc: Downloading video info webpage
[youtube] RTR12eM1-Xc: Extracting video information
ERROR: format not available for video

```

Next I follow [this]("http://ubuntuforums.org/showthread.php?t=1410880") thread and try the following: 

```
dhiman@dhiman-desktop:~$ sudo apt-get remove youtube-dl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-24 linux-headers-2.6.32-24-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  youtube-dl
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 119kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 272756 files and directories currently installed.)
Removing youtube-dl ...
Processing triggers for man-db ...


dhiman@dhiman-desktop:~$ sudo wget http://bitbucket.org/rg3/youtube-dl/raw/2010.02.13/youtube-dl -O /usr/local/bin/youtube-dl
--2011-02-03 17:01:07--  http://bitbucket.org/rg3/youtube-dl/raw/2010.02.13/youtube-dl
Resolving bitbucket.org... 207.223.240.182, 207.223.240.181
Connecting to bitbucket.org|207.223.240.182|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://bitbucket.org/rg3/youtube-dl/raw/2010.02.13/youtube-dl [following]
--2011-02-03 17:01:07--  https://bitbucket.org/rg3/youtube-dl/raw/2010.02.13/youtube-dl
Connecting to bitbucket.org|207.223.240.182|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `/usr/local/bin/youtube-dl'

    [  <=>                                                                                                               ] 56,361       202K/s   in 0.3s    

2011-02-03 17:01:09 (202 KB/s) - `/usr/local/bin/youtube-dl' saved [56361]

dhiman@dhiman-desktop:~$ sudo chmod +x /usr/local/bin/youtube-dl


dhiman@dhiman-desktop:~$ youtube-dl "http://www.youtube.com/watch?v=RTR12eM1-Xc"
[youtube] Setting language
[youtube] RTR12eM1-Xc: Downloading video info webpage
[youtube] RTR12eM1-Xc: Extracting video information
ERROR: format not available for video

```

Again I am getting the same error *format not available for video*.
Can anybody help me ?

---

### Post by irv on 2011-02-04
OK, I didn't have youtube-dl installed so I installed it. Ran it and got the same thing you got.
```
irv@irv-laptop:~$ youtube-dl http://www.youtube.com/watch?v=3MHbnyCJi-k&feature=related
[1] 27964
irv@irv-laptop:~$ [youtube] Setting language
[youtube] 3MHbnyCJi-k: Downloading video webpage
[youtube] 3MHbnyCJi-k: Downloading video info webpage
[youtube] 3MHbnyCJi-k: Extracting video information
ERROR: unable to download video (format may not be available)

```
I also noticed that Ubuntu does not support updates for this package.

---

### Post by andrew.46 on 2011-02-25
Perhaps this post may help:

[http://ubuntuforums.org/showpost.php?p=10495793&postcount=19](http://ubuntuforums.org/showpost.php?p=10495793&postcount=19)

Remember that youtube-dl should not be used with youtube itself, only with the other sites spoken of [in the documentation]("http://rg3.github.com/youtube-dl/documentation.html").

---

### Post by zazuge on 2012-09-27
today 27september youtube changed again something
and youtube-dl no longer work
<snip>
I hope ubuntu repo will update its version too ASAP

---

### Post by coffeecat on 2012-09-27
Old thread - and we do not support circumventing any EULA including youtube's. See here:

[http://ubuntuforums.org/showthread.php?t=1850955](http://ubuntuforums.org/showthread.php?t=1850955)

Closed for necromancy.

---

