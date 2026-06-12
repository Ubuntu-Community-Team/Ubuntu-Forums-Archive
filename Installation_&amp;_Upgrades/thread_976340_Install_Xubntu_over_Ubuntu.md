---
title: "Install Xubntu over Ubuntu"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by dgerwin11 on 2008-11-09
I have decided to install Xubuntu 8.10 over Ubuntu 8.04  My intention is for Xubuntu to be my main OS.  Do I leave Ubuntu installed, or do I delete it somehow?  Also how to make X my default OS?  This machine was built with Ubuntu 8.04 as the only operating system, so there are no Windows issues involved.

---

### Post by ronnielsen1 on 2008-11-09
sudo apt-get install xubuntu-desktop would do it. You could keep ubuntu-desktop or get rid of it. If you keep it, you will be given the option in sessions to change window managers or desktop environments
Sorry I didn't notice you had 8.04 installed. Are there files you want to keep?

---

### Post by dgerwin11 on 2008-11-09
No files of any import.

---

### Post by ronnielsen1 on 2008-11-09
> No files of any import.xubuntu-desktop appears to be in the universe repository so it would have to be enabled through System > Administration > Synaptic

 Settings > Repositories

If there are no files you wish to save (since you're wanting to go to Xubuntu 8.10 from Ubuntu 8.04) this might be better to do a fresh install. If there are files you wish to save, you can try the synaptic way.

---

### Post by OrangeCrate on 2008-11-09
> **dgerwin11 said:**
> **I have decided to install Xubuntu 8.10 over Ubuntu 8.04 ** My intention is for Xubuntu to be my main OS.  Do I leave Ubuntu installed, or do I delete it somehow?  Also how to make X my default OS?  This machine was built with Ubuntu 8.04 as the only operating system, so there are no Windows issues involved.

Updating to Xubuntu 8.10 from Ubuntu 8.04 won't be possible without a clean install. An alternative might be, to add the Xubuntu desktop to your 8.04 installation prior to upgrading to 8.10, and then it would upgrade both. See instructions on how to do that here:

**Installing Xfce on Ubuntu**

[http://psychocats.net/ubuntu/xubuntu](http://psychocats.net/ubuntu/xubuntu)

Once upgraded, you could remove Ubuntu, and get to a clean Xubuntu install by using these instructions:

**Getting Back to a Pure XFCE on Ubuntu**

[http://psychocats.net/ubuntu/purexfce](http://psychocats.net/ubuntu/purexfce)

BTW, you'll notice that you'll be using aptitude, rather than apt-get to install, which will make removing Xfce much easier if at some point you don't like it.

---

### Post by m_l17 on 2008-11-09
I would backup all files and do a fresh install. If you have a separate /home partition, it can be reused [but backup anyways just in case]. But you have to use the same username.

---

