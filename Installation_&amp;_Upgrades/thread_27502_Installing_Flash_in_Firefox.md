---
title: "Installing Flash in Firefox"
date: 2005-04-16
forum: Installation &amp; Upgrades
---

### Post by Frihet on 2005-04-16
Has anyone successfully installed flash in firefox?

The macromedia how-to does not seem to work.

---

### Post by bored2k on 2005-04-16
[QUOTE=Frihet]Has anyone successfully installed flash in firefox?

The macromedia how-to does not seem to work.[/QUOTE]
 sudo apt-get install flashplayer-mozilla or flashplayer-nonfree 

Those would work.

---

### Post by Frihet on 2005-04-16
Hi, bored2k.

You're probably right.  I'll bet I have to add "nonfree" to apt-get somewhere?

I'm looking.

George

---

### Post by fipeso on 2005-04-16
Newbie here :)

What is the relation betwen apt-get and GUI:"Synaptic Package Manager" ?

---

### Post by bored2k on 2005-04-16
[QUOTE=Frihet]Hi, bored2k.

You're probably right.  I'll bet I have to add "nonfree" to apt-get somewhere?

I'm looking.

George[/QUOTE]
 [http://ubuntuguide.org/#flash-mozilla](http://ubuntuguide.org/#flash-mozilla)

Have fun with flash ;) [ninjai.com rocks]

---

### Post by bored2k on 2005-04-16
[QUOTE=fipeso]Newbie here :)

What is the relation betwen apt-get and GUI:"Synaptic Package Manager" ?[/QUOTE]
 Post your question in another thread with a related topic, or create a new if you supposedly don't find one.

edit > Nevermind. But next time do so.
Synaptic is a GUI frontend for apt-get. Nothing more.

---

### Post by fipeso on 2005-04-16
But it IS related :) "Installing Flash in Firefox"

I'm about to install Flash for Firefox, and want to do it right. I am in the belive that using packages, makes it easier to get patches in the future.

Then again I could be wrong:

Text from  "/etc/apt/sources.list"
" Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
"

---

### Post by bored2k on 2005-04-16
[QUOTE=fipeso]But it IS related :) "Installing Flash in Firefox"

I'm about to install Flash for Firefox, and want to do it right. I am in the belive that using packages, makes it easier to get patches in the future.

Then again I could be wrong:

Text from  "/etc/apt/sources.list"
" Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
"[/QUOTE]
 Follow the mighty ubuntuguide.org and you would be fine. We all do so forget that, that line is like  Windows 200page long EULA you supposedly read and clicked next ;) .

---

### Post by Frihet on 2005-04-16
Here is what I get:

y7150@P2100:~$ sudo apt-get install flashplayer-mozilla
Password:
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Rele ase i386 (20050407) hoary/universe Packages (/var/lib/apt/lists/Ubuntu%205.04%20 %5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_universe_bi nary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package flashplayer-mozilla
y7150@P2100:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release [16.8kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [16.9kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/universe Sources
Fetched 34.1kB in 1s (18.1kB/s)
Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/dists/hoary/Release  Unable to find expected entry  universe/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/universe Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
y7150@P2100:~$ sudo apt-get install flashplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/universe Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package flashplayer-mozilla

Thoughts?

---

### Post by bored2k on 2005-04-16
[http://packages.ubuntu.com/warty/web/flashplayer-mozilla](http://packages.ubuntu.com/warty/web/flashplayer-mozilla)

Get it there, then 
sudo dpkg -i filename.deb

Also, your box is trying to fetch from the cdrom, disable that like shown on the guide
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by Frihet on 2005-04-16
OK, bored2k, that got it.  Flash is installed.  Now to install the flashblock extension.

Thanks!!!

---

### Post by Ubunted on 2005-04-16
By far the easiest way to install Flash in Firefox is to simply go to a flash-enabled site, click the "Get Plugins" button when it pops out, and let FF do it automagically.

---

