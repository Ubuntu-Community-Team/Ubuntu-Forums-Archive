---
title: "&quot;Applying Changes&quot; stuck with downloading Flash Player"
date: 2012-06-14
forum: Installation &amp; Upgrades
---

### Post by Oesipower on 2012-06-14
I wanted to install Flash Player to get it running in Opera. While downloading it in Ubuntu Software Center, the process got stuck while "Applying changes" and after 1 hour i decided to kill the process and reboot my computer and try again. It said that Flash Player was already installed and it worked in Opera, so I thought it was ok. But when i want to install any programm in Ubuntu Software Center, it always gets stuck in "Applying changes", so i can't download anything. This would be no problem if I simply install everything manually. The real problem is that everytime I want to update Ubuntu, the updating process gets stuck with "flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.236.orig.tar.gz". This is the last thing I see and it doesn't quit untill I kill the process...

---

### Post by David Andersson on 2012-06-14
> **Oesipower said:**
> I wanted to install Flash Player to get it running in Opera. While downloading it in Ubuntu Software Center, the process got stuck while "Applying changes" and after 1 hour i decided to kill the process and reboot my computer and try again. It said that Flash Player was already installed and it worked in Opera, so I thought it was ok. But when i want to install any programm in Ubuntu Software Center, it always gets stuck in "Applying changes", so i can't download anything. 

Different package managers (Software Center, Synaptic, Update Manager, apt-get) cannot run simultaneously. They either refuse to work (with a message that another is running) or just sit and wait until the other is completed (with a very small message what they wait for). But they do issue messages, at least in my Xubuntu 10.04.

Can you see if there is such a message?

Can you see if another package manager is running? (In System Monitor tab Processes, look for processes with "synaptic" or "apt" in their name)

The previous kill may have corrupted the package database. In my system Update Manager, Software Center and apt-get gives error messages to that effect (and suggest remedies).

Can you see if there is such an error message?

What version of Ubuntu do you use?

---

### Post by Oesipower on 2012-06-14
I tried to check up on everything you said. But while doing this I ran "sudo apt-get update" to figure out whether it still doesn't work and if there is any other process while it's running, but this time it just worked...i didn't change anything or did anything different...it just worked...thanks for your help anyways :)

---

### Post by Oesipower on 2012-07-08
I just tried to install "Wine" with the Software-Center and it got stuck and now the dpkg configure process is trying to install the flashplayer update again :mad: is there any way to just delete flashplayer and install it completely new or something like that?

---

### Post by spaceshipguy on 2013-05-14
> **Oesipower said:**
> ......it got stuck and now the dpkg configure process is trying to install the flashplayer update again :mad: is there any way to just delete flashplayer and install it completely new or something like that?

This is happenning to me with apt-get
Every time I try to use apt-get it trys to download flash, fails and dies.
How can I tell it to stop trying?
Grrr

---

