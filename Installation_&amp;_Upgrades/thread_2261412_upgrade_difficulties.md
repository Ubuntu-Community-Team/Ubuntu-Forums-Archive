---
title: "upgrade difficulties"
date: 2015-01-18
forum: Installation &amp; Upgrades
---

### Post by yeshua-1 on 2015-01-18
I'm attempting to upgrade from 13.10 to 14.04. 
I am getting the following message:

[I]Could not calculate the upgrade
An unresolvable problem occurred while calculating the upgrade.
 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug using the command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal.[/I]

Do all updates hang if you use a piece of software not provided by Ubuntu? I can't believe that is the case.
How can I go about finding the offending piece of software?
Any advice appreciated.

---

### Post by grahammechanical on 2015-01-18
Unofficial packages not provided by Ubuntu through the Software Centre but through a personal Package Archive (PPA) do cause problems for the Update Manager because the URL to the PPA might not be working.

But you have a different problem. Ubuntu 13.10 reached End of Life at July 2014. Its repositories are now closed. That is what is preventing the Upgrade. Some of us, including myself, recommend doing a fresh install. We recommend this because of the number of people saying "I upgraded and now Ubuntu is broken."

If you want to risk it then you have to edit this file: /etc/apt/sources.list and look for the URLs to the Ubuntu archives. Look for something like this

> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) saucy main restricted

gb.archive.ubuntu.com is the server that my Ubuntu gets updates from. In your case the line will have to be changed to 

> deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) saucy main restricted

And you must do that with every line that has a reference to the archive. Then run

```
sudo apt-get update
sudo apt-get upgrade
```

then open Update Manager and you should have a button to let you upgrade to 14.04.

To edit that file with administrator privileges run

```
sudo -H gedit /etc/apt/sources.list
```

Some people will say that you should use

```
gksudo gedit /etc/apt/sources.list
```

But if gksu is not installed, and I do not think that it is installed in 13.10, then you cannot install gksu because the repositories are closed.

Regards.

---

### Post by yeshua-1 on 2015-01-18
I see, I guess I will need to proceed with a new install. sigh.

---

### Post by tokyobadger on 2015-01-19
So you can't use gksu/gksudo, but you can still run 
```
sudo -H gedit /etc/apt/sources.list
```
another alternative is to use nano
```
sudo nano /etc/apt/sources.list
```
No need to give up on the upgrade so quickly :-)

**EDIT** The following has worked for me over the years (particularly in installing development releases of Ubuntu) but use at your own risk and only after backing up anything you value
```
sudo sed -i 's/saucy/trusty/g' /etc/apt/sources.list
```
```
sudo apt-get update && sudo apt-get dist-upgrade
```
Any 3rd party stuff like ppa's will get hammered (some survive ;-) )

---

### Post by ian-weisser on 2015-01-19
> **yeshua-1 said:**
> Do all updates hang if you use a piece of software not provided by Ubuntu?

Of course not. Only especially poorly crafted packages cause either a version conflict or file conflict.
Most non-Ubuntu packages have no conflict at all, and do not break upgrades.

---

