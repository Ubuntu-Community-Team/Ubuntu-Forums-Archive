---
title: "Updating software load on USB stick"
date: 2017-01-31
forum: Installation &amp; Upgrades
---

### Post by gmerrick on 2017-01-31
I frequently reformat machines and install a new Ubuntu system on them.  Is there any way of updating the patches and software fixed on the distro ISO that is installed on the USB stick to save me a little time from having to do updates after the installation?

---

### Post by sudodus on 2017-01-31
You can download the ***daily iso file*** from the [testing tracker](http://iso.qa.ubuntu.com/). If you get the very newest version, it will be a bumpy ride, but if you get the daily iso file of the LTS version, now xenial alias 16.04 LTS, it will be less bumpy. After installing you should turn off the 'xenial proposed' repository.

And you can update the iso file with ***zsync*** instead of downloading the whole file.

---

### Post by gmerrick on 2017-01-31
> **sudodus said:**
> You can download the ***daily iso file*** from the [testing tracker](http://iso.qa.ubuntu.com/). If you get the very newest version, it will be a bumpy ride, but if you get the daily iso file of the LTS version, now xenial alias 16.04 LTS, it will be less bumpy. After installing you should turn off the 'xenial proposed' repository.

And you can update the iso file with ***zsync*** instead of downloading the whole file.

I'm not looking for the latest ISO.  What I want to do is similar to the slipstreaming of patches you could do to the windows CD's.  I would like to do a similar thing with the Ubuntu Boot USB stick and ensure that the latest updates and patches are on the stick when I do an install.

---

### Post by howefield on 2017-01-31
That's a lot of work when the goal is purely to save time, the LTS daily iso is simply the release plus patches. Using zsync as suggested by sudodus is a cool way of keeping it up to date.

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

---

### Post by ajgreeny on 2017-01-31
> **howefield said:**
> That's a lot of work when the goal is purely to save time, the LTS daily iso is simply the release plus patches. Using zsync as suggested by sudodus is a cool way of keeping it up to date.

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
This is the way I have done it a few times without a problem.

It simply means you are using an ISO image file that has already been fully patched and updated so you will end up with the OS you would have had if you installed using  the standard ISO file and then upgraded the OS packages in the usual way.

It will not, of course, do anything to add the non-default applications that you may install manually yourself after installing the OS, but it will probably save you some time and bandwidth, if that is a problem for you, so I suggest is still worth doing.

---

### Post by C.S.Cameron on 2017-02-01
You can do an install to USB stick and update as you want the final product.
The USB stick can be cloned to the target drive or can be made into an .img file that can be written to the target drive using Image Writer in Windows or mkusb in Ubuntu.

I understand there are forks of remastersys, such as pinguybuilder [http://pinguyos.com/2015/09/pinguy-builder-an-app-to-backupremix-buntu/](http://pinguyos.com/2015/09/pinguy-builder-an-app-to-backupremix-buntu/)
This can be used to remaster the install iso.

---

