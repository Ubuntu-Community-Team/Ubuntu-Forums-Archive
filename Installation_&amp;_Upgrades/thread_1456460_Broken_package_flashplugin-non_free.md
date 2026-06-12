---
title: "Broken package flashplugin-non free"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by swudee on 2010-04-17
Hi

I have just updated one of my computers from 8.04 to 10.04 (32 bit)
The package manager has stuck on a broken flashplugin-nonfree package.
I have tried uninstalling the package with Synaptic. It said the package is in a "very bad inconsistent state" and I should try to reinstall it before removing it. 

sudo apt-get -f install
brings up the same error
Preconfiguring packages ...
dpkg: error processing flashplugin-nonfree (--purge):
Package is in a very bad inconsistent state - you should try reinstalling it before attempting removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: sub-process /usr/bin/dpkg returned an error (1)
A package failed to install. Trying to recover:

This forum looked interesting

[http://ubuntuforums.org/showthread.php?t=1350700&highlight=flashplugin-nonfree](http://ubuntuforums.org/showthread.php?t=1350700&highlight=flashplugin-nonfree)

It was for Karmic, but it didn't work for me.

In short, I can't install it and I can't uninstall it.
Hopefully some else has some ideas. It seems to crop up a bit in the forums, often cured by a reinstall:(

Regards Dave

---

### Post by swudee on 2010-04-17
Solved

I found this post in Launchpad and has fixed the problem.

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/518263](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/518263)

Monkey  wrote on 2010-02-08:  	  #2

1. Please do in the Terminal the next command and copy the output here:
sudo dpkg --configure -a

2. Try ro reinstall

3. If You can´t do it. Please do in the terminal the next command and copy the output here:
sudo apt-get -f install flashplugin-nonfree

Thank You for making Ubuntu better.
Changed in flashplugin-nonfree (Ubuntu):
status: 	New &#8594; Incomplete


I should also mention that I needed to run

sudo apt-get -f upgrade

to finish the update after the dpkg problem was fixed

---

### Post by Denny Johnson on 2010-05-11
Dave....thanks for posting your solution.
I had the exact same problem.
The number 4 post [Alexey] at your link was an easy to follow solution.

---

