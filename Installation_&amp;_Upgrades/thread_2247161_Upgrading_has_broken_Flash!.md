---
title: "Upgrading has broken Flash!"
date: 2014-10-06
forum: Installation &amp; Upgrades
---

### Post by kazakore on 2014-10-06
Just got my laptop back after a month away from it and done the usual update/upgrade and now Flash in Firefox isn't working any more!

I don't really care about Youtube or Flash game etc, much of which should be coverable by HTML5 in this day and age, but I do care greatly about being able to easily manage my photo albums on Facebook!!

Running "sudo apt-get install flashplayer-installer" and I am informed it is already installed and the latest version. Tried removing and re-installing and it seems to pause for ages so I think there might be something going on wrong there...

sudo apt-get install flashplugin-installer 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  x-ttcidfont-conf xfs
The following NEW packages will be installed
  flashplugin-installer
0 to upgrade, 1 to newly install, 0 to remove and 0 not to upgrade.
Need to get 0 B/6,948 B of archives.
After this operation, 140 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously unselected package flashplugin-installer.
(Reading database ... 334000 files and directories currently installed.)
Preparing to unpack .../flashplugin-installer_11.2.202.406ubuntu0.14.04.2_amd64.deb ...
Unpacking flashplugin-installer (11.2.202.406ubuntu0.14.04.2) ...
Processing triggers for update-notifier-common (0.154.1) ...
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.406.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.406.orig.tar.gz)



Then sits for ages doing nothing!!

(and finally this time on trying again more message:

Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 239, in process_download_requests
    dest_file = urllib.urlretrieve(files[i])[0]
  File "/usr/lib/python2.7/urllib.py", line 94, in urlretrieve
    return _urlopener.retrieve(url, filename, reporthook, data)
  File "/usr/lib/python2.7/urllib.py", line 268, in retrieve
    block = fp.read(bs)
  File "/usr/lib/python2.7/socket.py", line 380, in read
    data = self._sock.recv(left)
timeout: timed out
Setting up flashplugin-installer (11.2.202.406ubuntu0.14.04.2) ...




Please help me get my Flash working again as it should. Surely making sure something as heavily used as Flash isn't broken during Upgrade should be pretty high on the priorities list!!! I don't really want to install Chrome at all! I much prefer Firefox and just having Chrome installed generally doubles the download required pretty much every time I run an Update! This isn't really acceptable travelling SE Asia with often very poor internet connections!!

---

### Post by TheFu on 2014-10-06
[https://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html](https://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html) may help with understanding. Flash on Linux has been abandoned by Adobe. This was announced years ago.

[http://askubuntu.com/questions/172783/adobe-will-stop-releasing-new-versions-of-flash-what-will-happen-to-flash-supp](http://askubuntu.com/questions/172783/adobe-will-stop-releasing-new-versions-of-flash-what-will-happen-to-flash-supp) is another answer.

Blame Adobe, not Ubuntu or Firefox.

---

### Post by coffeecat on 2014-10-06
Blaming Adobe hardly helps the OP troubleshoot a problem with a version of the flashplugin-installer and flash which are working just fine in my Ubuntu 14.04. Let's focus on trying to get something to work that should be working rather than having a discussion about Adobe's development strategy. 

@kazakore, as I said, the upgrade to flashplugin-installer_11.2.202.406ubuntu0.14.04.2_amd64.deb on my system did not break flash. I wonder if this may be a clue:

> **kazakore said:**
> 
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.406.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.406.orig.tar.gz)



Then sits for ages doing nothing!!

And:

> **kazakore said:**
> 
timeout: timed out

I wonder if there was a temporary server problem at archive.canonical.com or perhaps a network problem your end. Try clicking on this link:

[http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.406.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.406.orig.tar.gz)

Are you offered a download of the tar.gz package? Don't bother to download it - that's just to see if a valid request is getting through to archive.canonical.com from your system. If yes, try this again:

```
sudo apt-get install --reinstall flashplugin-installer
```

Post the terminal output from that command and let us know if that helped at all.

---

### Post by kazakore on 2014-10-06
> **coffeecat said:**
> 

I wonder if there was a temporary server problem at archive.canonical.com or perhaps a network problem your end. Try clicking on this link:




I think that's all it was as trying remove/install again a couple of hours later and it fixed the issue. Now just need good enough mobile internet to actually be able to upload my photos, which is currently beyond lacking!! But that's Nepal for you.



TheFu: I know all about the dropped support and non-relasing of future versions for Linux! If you had actually read my post it would have been clear that had nothing to do with my problem!

Still an Upgrade shouldn't really have broken the Firefox plugin, as it's not being updated and thus wouldn't have been an upgraded package. At least I can be happy it did eventually reinstall and start to work again as usual :)

---

### Post by coffeecat on 2014-10-06
> **kazakore said:**
> 
Still an Upgrade shouldn't really have broken the Firefox plugin, as it's not being updated and thus wouldn't have been an upgraded package. At least I can be happy it did eventually reinstall and start to work again as usual :)

My guess is that the installer deletes the old flash files before downloading the tar.gz that has the new ones, therefore if there is a network hiccup between downloading the .deb and the .tar.gz, that will cause flash to be broken. Only a guess though. I'm glad it's working now.

---

