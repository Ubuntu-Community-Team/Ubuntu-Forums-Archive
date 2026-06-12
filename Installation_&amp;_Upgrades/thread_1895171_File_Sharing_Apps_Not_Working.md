---
title: "File Sharing Apps Not Working"
date: 2011-12-14
forum: Installation &amp; Upgrades
---

### Post by satya ub on 2011-12-14
I have encountered this problem a week back. When i add a torrent it reaches to say 50% and freezes there. Though there is exchange of data the torrent remains stagnant.

I have tried alternatives to Transmission like Deluge, Vuze & qBittorrent but in vain. The same problem surfaced again.

I have tried re-installing those aforesaid apps but it didn't work.

Please tell me what to do.

---

### Post by 0N3 on 2011-12-14
I use Deluge I find it to be brillaint. Have you the most recent version of it?
Open a terminal and add the ppa

sudo add-apt-repository ppa:deluge-team/ppa

sudo apt-get update && sudo apt-get upgrade

The latest version is 1.3.3.0

---

### Post by satya ub on 2011-12-14
Yes i have the latest file sharing clients installed from Ubuntu Software Center. But the issue crops up.

---

### Post by 0N3 on 2011-12-14
The ones via the Software Centre don't necessarily mean the most up to date to get the most up to date versions you must add the ppa.

---

### Post by satya ub on 2011-12-15
Yes i have checked all of the versions. They are up to date on my PC. Please someone provide me a solution.

I reported the problem on Transmission yesterday. In the report i saw that a bug was there.

Feel bad since i don't know any coding of Ubuntu.

---

### Post by satya ub on 2011-12-15
Even Ktorrent is not working. The download directory is "Private" folder. I have tried with the destination as "Downloads". Even that wouldn't work. I wonder what happened to all of the apps: Transmission, Vuze, Deluge, qBitTorrent, Flush & Bittorrent Download Client.

Ten days before my Ubuntu was running sharp. I don't know what happened.
Looking forward to some guidance & support.

---

### Post by darkod on 2011-12-15
Did you try to completely deinstall Transmission with purge and install again? And let it download in Downloads for start.

sudo apt-get --purge remove transmission transmission-daemon
sudo apt-get install transmission transmission-daemon

I have Transmission running on ubuntu server 10.04.3 for example and it's running just fine.

Or is it possible that your ISP started blocking the traffic?

---

### Post by satya ub on 2011-12-15
No i didn't purge it because i don't know. But i did what you told me to.
When i typed in the first command i got the below content from Terminal though Transmission is installed on my PC. I have all of the File Sharing Clients on my PC right now.

From Terminal

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package transmission-daemon is not installed, so not removed
Package transmission is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libpanel-applet-4-0 libx264-106 libbluray0 libswt-gnome-gtk-3.6-jni
  linux-headers-2.6.38-8 linux-headers-3.0.0-12 libswt-gtk-3.6-java libdvbpsi6
  libswt-webkit-gtk-3.6-jni libswt-cairo-gtk-3.6-jni libswt-gtk-3.6-jni
  liblzo2-2 linux-headers-2.6.38-8-generic linux-headers-3.0.0-12-generic
  libdmapsharing2 libmatroska3 gir1.2-panelapplet-4.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 40 not upgraded."

Later i typed in the second command. It installed Transmission.

The below link shows the report of Transmission in Apport

[http://imageshack.us/photo/my-images/690/screenshotixh.png/](http://imageshack.us/photo/my-images/690/screenshotixh.png/)

---

### Post by darkod on 2011-12-15
It is very strange it says not installed but you claim it is.

Anyway, after it was installed, did you try it?

---

### Post by satya ub on 2011-12-15
I have been using Transmission trouble free for the past four months until now. Say the torrent size is 600MB. The count goes till 45%, progresses to 47% and comes back to 45% and freezes there even though there is exchange of data. As you see in the image it mentions a bug.
I don't think my ISP throttles.

My only fear is that, "Do i have to go for a complete re-install of Ubuntu 11.10 in order to surpass this issue?"

---

### Post by satya ub on 2011-12-15
I have just tried to download a torrent. It's not working.

---

### Post by darkod on 2011-12-15
If it's related only to the transmission bug, how come other software you have used does the same? There might be a bug but it doesn't seem that all users are affected. For me it works fine for example, and for millions of others.
Do you have other reasons to believe you are affected by a bug except that it stops downloading? Any other symptoms that this bug has and they show up for you too?

And on the other hand, just because you were downloading fine for 4 months doesn't mean your ISP can't start blocking you when noticing the amount and type of traffic you are generating. That's why I suggested it as one option since you said all P2P software seemed to be affected.

---

### Post by darkod on 2011-12-15
> **satya ub said:**
> I have just tried to download a torrent. It's not working.

Do you have the port forwarded on your router? Torrent clients work best if the port is forwarded to that machine.

---

### Post by satya ub on 2011-12-15
I use a modem. Even KGet isn't working. The send/receive packets keep on blinking without 1MB of data being downloaded.

---

