---
title: "Change Download Mirror During Ubuntu Installation?"
date: 2014-07-11
forum: Installation &amp; Upgrades
---

### Post by Espionage724 on 2014-07-11
It seems I download realatively slowly from Ubuntu's main download server, and I wanted to change the location. I've been reinstalling frequently, and installs are painfully slow (talking speeds less than 50KB/s; I think I even seen bytes/s a few times) because of the slow downloads; especially during the language pack downloads.

I know I can download updates faster from other mirrors, but afaik, I can only change where I download the updates from after the OS install. Can I change where the installer itself downloads the language packs and everything else it needs?

I use 14.04 also if it matter.

---

### Post by patsev-anton on 2014-07-12
May be you try use torrent?

---

### Post by Espionage724 on 2014-07-14
> **patsev-anton said:**
> May be you try use torrent?
Pretty sure I can't download language packs during ubiquity nor system updates with torrents.

Anyone else have any suggestions? I do frequent reinstalls, and can't afford waiting over an hour just for language packs and whatever else to download. My connection isn't being throttled, and it only seems to be both the Main and US servers being slow during normal times (slow being 10-50KB/s). Was able to get my max DL speed (350KB/s) earlier around 7AM though when downloading updates from the US server. Are both those servers getting hammered at normal times or something?

---

### Post by oldfred on 2014-07-14
I would definitely not tick the install updates or restricted extras and install those after changing server for updates.

I might be temped it really slow to just disconnect from Internet. Then with working install you can change server & start all the updates.

I always change to one that is local, but it is normally really good. Only once when it was new release day had it ever been slow more me.

---

### Post by Espionage724 on 2014-07-20
> **oldfred said:**
> I would definitely not tick the install updates or restricted extras and install those after changing server for updates.

I might be temped it really slow to just disconnect from Internet. Then with working install you can change server & start all the updates.

I always change to one that is local, but it is normally really good. Only once when it was new release day had it ever been slow more me.

I don't install updated nor proprietary software during installation (both checkboxes unchecked).

Doing another reinstall currently that's already over an hour "Downloading packages". This is ridiculous...

---

### Post by oldfred on 2014-07-20
Another alternative is just install minimal. Then change mirror before downloading everything you want.

       [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
HowTo Achieve "Ubuntu-Desktop-Minimal" 
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)
Install script for minimal
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

---

### Post by plucky on 2014-07-21
> I don't install updated nor proprietary software during installation (both checkboxes unchecked).

Doing another reinstall currently that's already over an hour "Downloading packages". This is ridiculous... 

It shouldn't be trying to download from the internet if you did not tick the boxes.

Try the install with no internet connection and see if the install is still as slow.

Turn off networking.

Are you using Live DVD or USB?

---

### Post by Espionage724 on 2014-07-21
> **plucky said:**
> It shouldn't be trying to download from the internet if you did not tick the boxes.

Try the install with no internet connection and see if the install is still as slow.

Turn off networking.

Are you using Live DVD or USB?

Ubuntu downloads language packs regardless if you check either of those boxes. Installing without internet is fine, but I'd really rather not avoid the download. Using LiveUSB.

Another install I did about 9-10 hours ago downloaded the packs just fine at normal speed.

---

### Post by Bashing-om on 2014-07-21
Espionage724; Hi !

Here is a thought, change the mirror -select best server -  prior to doing the install.
From the standard desktop liveDVD :
ubuntu Software Center -> taskbar (edit) -> software sources -> download from -> other -> select best server. This will run a series of test and give you the option to use and set an alternate mirror.

If you are installing from an alternate install method, perhaps manually edit '/etc/apt/sources.list' to reflect the 'best server' .

[INDENT][INDENT]workie great ?
[/INDENT][/INDENT]

---

### Post by Espionage724 on 2014-07-21
> **Bashing-om said:**
> Espionage724; Hi !

Here is a thought, change the mirror -select best server -  prior to doing the install.
From the standard desktop liveDVD :
ubuntu Software Center -> taskbar (edit) -> software sources -> download from -> other -> select best server. This will run a series of test and give you the option to use and set an alternate mirror.

If you are installing from an alternate install method, perhaps manually edit '/etc/apt/sources.list' to reflect the 'best server' .

[INDENT][INDENT]workie great ?
[/INDENT][/INDENT]

Hi; unfortunately it seems changing the mirror doesn't actually do anything from a LiveCD; I changed the mirror over to a us.kernel.org address and reloading sources prior to starting the install, but ubiquity still showed that it was downloading from archive.ubuntu.com.

---

### Post by Bashing-om on 2014-07-21
Espionage724; Shucks,

Well, was a thought, I had thunk as one can change the boot parameter options, one might be able to change the mirror for the install.

[INDENT][INDENT]as I live and
[INDENT][INDENT][INDENT]don't learn
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

