---
title: "Problems with Software Management after failed Skype install"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by Shadowrain on 2011-07-26
Hello,
I tried to install Skype on my 64-bit Kubuntu 10.04.2 with the  commands:

sudo dpkg -i skype*.deb
sudo apt-get -f install

I got the following error messages:

dpkg: dependency problems prevent configuration of skype:
 skype depends on lib32stdc++6 (>= 4.1.1-21); however:
  Package lib32stdc++6 is not installed.
 skype depends on lib32asound2 (>> 1.0.14); however:
  Package lib32asound2 is not installed.
 skype depends on ia32-libs; however:
  Package ia32-libs is not installed.
 skype depends on libc6-i386 (>= 2.7-1); however:
  Package libc6-i386 is not installed.
 skype depends on lib32gcc1 (>= 1:4.1.1-21+ia32.libs.1.19); however:
  Package lib32gcc1 is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype

Now I tried to install the missing packages via the Software Management, but I always get the message:

There are broken dependecies on your system. Please use an advanced package manage e.g. Synaptic or aptitude to resolve this situation.

At this point I tried to follow the instruction in this post: [http://ubuntuforums.org/showthread.php?t=1798023&highlight=broken+dependencies](http://ubuntuforums.org/showthread.php?t=1798023&highlight=broken+dependencies)

But I still get error messages in the Software Management and the atp-get update command didn't work.

I hope I managed to describe the problem in an appropriate way and someone can help me.

---

### Post by westie457 on 2011-07-26
Hello. Welcome to the Forums.

Open the Software Centre, click Edit and in the menu select Software sources. In the first tab put a check mark in all the boxes except the one marked Source Code. In the next tab check all the boxes. Click on Close. When prompted on screen update the information. Then try to install.

---

### Post by Shadowrain on 2011-07-26
Thanks for your reply. 

The update took place but I still get the error messages, when I try to install and in the Software Center as well.

---

### Post by westie457 on 2011-07-26
> **Shadowrain said:**
> Thanks for your reply. 

The update took place but I still get the error messages, when I try to install and in the Software Center as well.

Run this in a terminal ```
sudo dpkg --configure -a
```
Then try the install again. if it fails try install via Synaptic.

---

### Post by Shadowrain on 2011-07-26
I solved the problem by chance. I tried to install the flash-player with

sudo apt-get install flashplugin-nonfree

The command line told me to run 'apt-get -f install' to correct the unmet packages dependencies. After I did that it installed Skype by itself. I have to say, I don't understand fully what happend, but it worked.

---

