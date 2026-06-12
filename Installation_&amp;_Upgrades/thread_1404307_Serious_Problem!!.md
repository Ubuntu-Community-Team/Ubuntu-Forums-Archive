---
title: "Serious Problem!!"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by virsto on 2010-02-11
This morning after booting up my system (Ubuntu 9.10) I had a popup for installation of some updates. These are the updates that were checked:

_Important security updates_
 gnome-screensaver
 libmysqlclient16
 mysql-common
_Recommended updates_
 python-ubuntuone-client
 python-ubuntuone-storageportocol

Of course, I went ahead with the install --- or at least tried to. However, these were never installed and the system seems to hangup with the popup displayed until it is closed. This attempted update seems to be the source of a serious problem (IMHO).

That is, I am now unable to execute:

 Administration ->  Software Sources
 Administration ->  Synaptic Package Manager

When I try to execute these the "busy icon" stays up for a few seconds then disappears.
Note, I can go to Update Manager; but, if I try to install any of these, the same problem occurs (as described previously).

It seems that there has been some change in user privileges --- security breech??
I went into the terminal and issued the sudo su command, and this is what happened:

  virgil@virgil-desktop:~$ **sudo su**
  sudo: must be setuid root

Normally, I would be asked for my password. But, now I get this response, and as a newbie to Ubuntu, I do not understand how to respond to this message. 

I need help on this, please!:!:

---

### Post by virsto on 2010-02-11
Ok, I found a partial solution from an earlier Web posting on this problem. I performed the following steps:

1. Rebooted in recovery mode
2. In the root executed the following: 

 chown root:root /usr/bin/sudo
 chmod 4111 /usr/bin/sudo

3. Rebooted

I was now able to install the 5 updates (mentioned in my previous comment), and **sudo** now works!

However, ***I am still unable to perform an install on any of the software packages in "Ubuntu Software Center**"*. I now get a very strange behavior when I click on install for any package in the software center --- the popup window to authenticate appears for a few milliseconds, jitters horizontally, and then disappears. Thus, I am unable to authenticate any installation. Note, I also saw this behavior with the installation of the updates, before I made the changes above. 

It appears to me that this problem with the software center is related to the original problem, but is now occurring at a different level. It seems that I have used **chown** or **chmod**  (or both) wrongly; but, I have no idea on how to fix this. :(

I was able to use Synaptic Package Manager to reinstall the software center; but this had no effect --- still can not install any package given in the software center!


I need help again on how to return my system to normal!:?:

---

### Post by theDaveTheRave on 2010-02-23
virsto,

I would recomend attempting the following.


```

sudo apt-get check

```

to confirm that all the required dependencies are being found. if any are found then you can 'fix them' with 

```

sudo apt-get fix-broken

```

alternatively you may need to 

```

sudo apt-get reinstall

```

to ensure that you have the upto date version of everything.

That should sort out your prblems.... but...

save any error messages that are returned, and post them here.

David.

---

