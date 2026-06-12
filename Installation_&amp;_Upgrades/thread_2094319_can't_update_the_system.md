---
title: "can't update the system"
date: 2012-12-13
forum: Installation &amp; Upgrades
---

### Post by Joe 1 on 2012-12-13
Hi all,

when clicking on 'install updates' I get an error message "Failed to download repository information... check your Internet connection."

Also,is there a way to reset the system back to 'factory default'?

I have problems with audio/video and reinstall Nvidia drivers on a weekly basis.

sudo apt-get update
```
Fetched 18.7 MB in 1min 1s (302 kB/s)
W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/Release.gpg  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/source/Sources  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/binary-i386/Packages  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/i18n/Translation-en_CA  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/i18n/Translation-en  Unable to connect to archive.getdeb.net:http:

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Will appreciate your help.

Joe

---

### Post by UltimateCat on 2012-12-13
Are you having trouble with your internet connection staying connected?

One reason why your Update Manager could be failing to fetch the updates from the Repositories is 1- your connection is failing and 2-your sources.list may not have all of the http:// repository address it needs. Check on your sources list.

Do you have a wired or wireless connection?

Depending on what Editor you use (I use Nano) you can add to and edit your sources list.

---

### Post by UltimateCat on 2012-12-13
Articles that may help you to understand more.

The other thing could be is if you haven't done an update in a long time you can get that message.  When you can do an update ASAP and and apt-get upgrade to your system.

[http://www.linux-archive.org/ubuntu-desktop/504106-failed-fetch-updates.html](http://www.linux-archive.org/ubuntu-desktop/504106-failed-fetch-updates.html)
[http://answers.yahoo.com/question/index?qid=20110903104313AAJaoBY](http://answers.yahoo.com/question/index?qid=20110903104313AAJaoBY)
[http://www.linuxquestions.org/questions/linux-newbie-8/failed-to-fetch-893831/](http://www.linuxquestions.org/questions/linux-newbie-8/failed-to-fetch-893831/)
[http://www.serkey.com/tag/failed-to-fetch-ubuntu/](http://www.serkey.com/tag/failed-to-fetch-ubuntu/)

---

### Post by Joe 1 on 2012-12-13
I have a wire connection but that's not the problem. This has started after I tried to install the last version driver from Nvidia due to Audio/Video problems:
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

I guess I did something wrong and I don't know how to go back to fix this.

---

### Post by 2sondad on 2012-12-13
The archive.getdeb.net website has been down for several days.  Other forums are recommending a mirror site for the update.

---

### Post by cigtoxdoc on 2012-12-14
Also, the gods of Ubuntu have declared that gparted is so dangerous to my systems (12.04 LTS) that I am forbiddent to update it.

From time to time, other applications, are also labeled as too dangerous.

Where is individual responsibility?

John

---

### Post by ibjsb4 on 2012-12-14
> **cigtoxdoc said:**
> Also, the gods of Ubuntu have declared that gparted is so dangerous to my systems (12.04 LTS) that I am forbiddent to update it.

From time to time, other applications, are also labeled as too dangerous.

Where is individual responsibility?

John

Don't know anything about the gods of ubuntu, but do know that you should start your own post and not hijack this one.  Then maybe even do an update and post any errors that would show something more relevant than this post.

---

### Post by Frogs Hair on 2012-12-14
There were problems two weeks ago and I think there is a different mirror in this thread.  [http://ubuntuforums.org/showthread.php?t=2088127&page=2](http://ubuntuforums.org/showthread.php?t=2088127&page=2)

---

