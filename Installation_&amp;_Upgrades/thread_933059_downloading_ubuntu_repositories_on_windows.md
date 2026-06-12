---
title: "downloading ubuntu repositories on windows"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by techdude26@gmail.com on 2008-09-29
I have installed the security updates for ubuntu from [http://security.ubuntu.com](http://security.ubuntu.com)........ but due to some reason I have to format my machine. Now I reinstalled ubuntu 7.10 64-bit (gutsy gibbon) and I have to download the security updates again. Last time I downloaded security updates it took 8hrs to download :(, as the internet speed is slow.

I have a faster internet available at some other location and machine which has windows xp. I want to know whether is it possible that I download the security and other repositories from this machine, copy and install them on my ubuntu. If yes, how????

---

### Post by Partyboi2 on 2008-09-29
You could use the "generate package download script" in synaptic. See [[COLOR=Blue]here[/COLOR]]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript")

---

### Post by WWSmith36 on 2008-09-29
If you are updating between releases, you could just download the latest ISO, burn it to a CD, and use that to update the computer. I recommend the alternate install CD for this. 

[http://releases.ubuntu.com/releases/8.04/](http://releases.ubuntu.com/releases/8.04/)
[http://cdimage.ubuntu.com/releases/](http://cdimage.ubuntu.com/releases/) with .torrent links

Just update from CD-Rom

apt-cdrom add
aptitude update

Hopefully that does what you need.

You will probably want to remove the CD line from his apt repositories (/etc/apt/sources.list) after the update.

---

### Post by techdude26@gmail.com on 2008-11-12
The update manager is in startup and it notifies me of updates whenever I connect to internet. So I don't know what all updates it had downloaded on a fresh gutsy gibbon installation.

Now since I have already downloaded all the required packages, hence the synaptic generated script won't contain the packages/downloads that I will require if I have to reinstall the Ubuntu.

In short I want some way so that next time I reinstall Ubunutu I need not to download the updates from net. This can be possible if I backup the packages which are there downloaded by my current installation.

Or an alternate way is to get the packages/repositories from a windows machine having faster internet connection.

But the question is how???

---

### Post by Partyboi2 on 2008-11-12
You can use the 'generate package download script' to get your machine up-to-date with all the current updates then you can use [[COLOR=Blue]aptoncd [/COLOR]]("http://aptoncd.sourceforge.net/")to make a copy of all your installed packages and use it next time you reinstall.

---

