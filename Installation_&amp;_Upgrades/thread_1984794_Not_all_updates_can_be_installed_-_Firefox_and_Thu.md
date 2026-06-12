---
title: "Not all updates can be installed - Firefox and Thunderbird"
date: 2012-05-22
forum: Installation &amp; Upgrades
---

### Post by bobhaugen on 2012-05-22
I'm on Ubuntu 10.04.  Update Manager says "Not all updates can be installed".  Firefox and Thunderbird are unchecked, and seem to be the problems.

This has been going on for a couple of weeks.  Thought I'd wait and see if it resolved itself, but doesn't seem to be happening.

Anybody else seeing this problem, or is it only me?

Anybody got any ideas of what to do, if anything?

Thanks.

---

### Post by zvacet on 2012-05-22
Post here output of 

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by bobhaugen on 2012-05-22
> **zvacet said:**
> Post here output of 

```
sudo apt-get update && sudo apt-get upgrade
```

Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US                                   
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]                                              
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_US                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                                    
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) lucid/main Translation-en_US
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                   
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                                           
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg [189B]                                              
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US              
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg [198B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                             
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release [57.2kB]                 
Get:8 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,250B]                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                                   
Get:9 [http://dl.google.com](http://dl.google.com) stable/main Packages [769B]                       
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release [57.3kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages [1,386kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages [6,208B]                                                                                         
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages [5,448kB]                                                                                          
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages [180kB]                                                                                          
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources [659kB]                                                                                                 
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources [3,775B]                                                                                          
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources [3,165kB]                                                                                           
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources [119kB]                                                                                           
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages [412kB]                                                                                       
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages [2,855B]                                                                                
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages [130kB]                                                                                   
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages [5,368B]                                                                                
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources [122kB]                                                                                        
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources [1,259B]                                                                                 
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources [40.5kB]                                                                                   
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources [2,323B]                                                                                 
Fetched 11.8MB in 1min 43s (115kB/s)                                                                                                                        
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  firefox thunderbird thunderbird-locale-en-gb
The following packages will be upgraded:
  firefox-3.0-gnome-support firefox-gnome-support firefox-locale-de firefox-locale-en firefox-locale-es firefox-locale-fr firefox-locale-pt
  firefox-locale-zh-hans firefox-locale-zh-hant libxml2 libxml2-dbg libxml2-utils python-libxml2 ubufox xul-ext-ubufox
15 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 5,528kB of archives.
After this operation, 106kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

---

### Post by bobhaugen on 2012-05-23
The Firefox support forum says this is an Ubuntu build, gotta get help from Ubuntu.

Here are the details from the Update Mgr:

Changes for the versions:
11.0+build1-0ubuntu0.10.04.2
12.0+build1-0ubuntu0.10.04.1

Version 12.0+build1-0ubuntu0.10.04.1: 

  * New upstream stable release (FIREFOX_12_0_BUILD1)
    - see LP: #987262 for USN information

That's [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/987262](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/987262)

---

### Post by zvacet on 2012-05-23
> After this operation, 106kB of additional disk space will be used.
 Do you want to continue [Y/n]? n

Why did you answered **no**? You should select yes and updates will be installed.

> 15 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

For those witch are not upgraded run 

```
sudo apt-get dist-upgrade
```

If you have synaptic you can handle all updates from there.In synaptic click on **refresh** and after it is finished click **mark all updates**.

If you don&#729;t have synaptic install it


```
sudo apt-get install synaptic
```

---

### Post by bobhaugen on 2012-05-23
> **zvacet said:**
> Why did you answered **no**? You should select yes and updates will be installed.


I was afraid that several Firefox components would be upgraded, but not Firefox, so the whole lot would be out of sync.

Did a lot of searching for this problem, and while I did not find the exact problem (which surprises me), I did see several complaints about Firefox not working after partial upgrades.

And other vague warnings about using dist-upgrade.

So not understanding what I was doing, preferred to do nothing.  Seems like a minor upgrade anyway.

I tried your recommended synaptic procedure, which also failed.

Synaptic said it had to remove the Adobe Flash plugin to upgrade Firefox, which might had been the problem in the first place.  But then the Flash removal failed, so the whole upgrade halted.

Might try again after a reboot...and removing the Flash plugin first.

---

### Post by jadtech on 2012-05-23
try this in terminal 

```


sudo apt-get upgrade -f


```

if it asked you if you want to continue  yes is the right answer :) 

upgrade -f will build a decadency tree ( list) and down load everything necessary  for what there is to upgrade then install it .. 

if you have been running  your browser while trying to do this that could be a  part of the problem , I have never had notice about removing flash to update a browser  either way if the broswer is open then the plugin could be counted as in use  ..

---

### Post by bobhaugen on 2012-05-23
Tried again after reboot.  Tried first to remove Flash plugin manually.  Could only find how to disable it.  Did not help.

Flash removal failed again.

Thanks for trying, though, I do appreciate it.

---

### Post by zvacet on 2012-05-23
You can uninstall flash from synaptic.
```
The following packages have been kept back:
 firefox thunderbird thunderbird-locale-en-gb
```

> And other vague warnings about using dist-upgrade.

Command
```
sudo apt-get dist-upgrade
```

will upgrade packages witch are kept back..

---

### Post by bobhaugen on 2012-05-23
Synaptic continues to be unable to remove Flash plugin.

So should I do:
sudo apt-get upgrade
or
sudo apt-get upgrade -f

and then follow with 
sudo apt-get dist-upgrade
?

---

### Post by zvacet on 2012-05-23
If you still have problems with flash remove in and install again with synaptic.After that also in synaptic click refresh and mark all updates.That should solve your problems.

---

### Post by zvacet on 2012-05-24
```
sudo apt-get --purge remove <package_name>
```

---

### Post by bobhaugen on 2012-05-24
tried
sudo apt-get update && sudo apt-get upgrade
followed by
sudo apt-get dist-upgrade

dist-upgrade failed on the same error trying to remove the flash plugin that synaptic failed on.

Also tried 
sudo apt-get upgrade -f
Did not upgrade firefox.

So in the end, firefox has not been upgraded, but still runs.  (The other components that did get upgraded apparently are not out-of-sync enough to kill it.)  

Which I guess is ok.

---

### Post by bobhaugen on 2012-05-24
Hah!  Fixed the problem, using this tip from Professor Farnsworth:
[http://ubuntuforums.org/showthread.php?t=1973994](http://ubuntuforums.org/showthread.php?t=1973994)

> I had this problem and ended up fixing it by referencing [http://blog.bodhizazen.net/linux/apt...oken-packages/](http://blog.bodhizazen.net/linux/apt...oken-packages/). Basically something like the below seemed to remove it for me, and I can now install other packages and such:

cd /var/lib/dpkg/info/
sudo rm adobe-flashplugin.*
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin


After that, Update Manager upgraded Firefox and Thunderbird without complaint.

---

### Post by jeannacav on 2012-06-07
I have been having this problem too.
I am hoping all the firefox  security upgrades that did not install were thunderbird related.

I do not need thunderbird and I would much rather uninstall that than flash followed by reinstall.

Is that even possible?
Or
will I really mess things up by removing thunderbird, which I do not recall installing and assume it came as part of a package.

Thanks for any help here.

jeanna

---

### Post by jeannacav on 2012-06-13
Actually, the part where prof farnsworth says "something like"... is what bothers me.
I am unwilling to try "something like"..
I do not know enough to help myself out of a mess,because I do not understand all he is telling me to do.

Please someone, I need some help here. 

Is that set of 3 lines the exact code?

thanks,

jeanna

---

### Post by Cavsfan on 2012-06-13
**zvacet** has the right idea. I never use Update Manager. I always use 

```
sudo apt-get update
sudo apt-get upgade
```Install all that there are and then 
use 
```
sudo apt-get dist-upgrade
```to get the ones held back such as a new kernel, etc.

A friend in this forum **ranch hand** calls Update Manager Update Mangler.

These commands will never let you down. I only use Update Manager to view what the updates are.

---

### Post by Cavsfan on 2012-06-13
To make it easier you can set these update commands as a script:
enter 
```
gedit /home/username/.bashrc
```in terminal (no sudo required).
Then towards the bottom where you see aliases.
Copy and paste this into that file:
```
# update aliases
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
alias ud2='sudo apt-get dist-upgrade'
```Then save it. You will have to logout and back in for them to take effect.
Then you just enter **ud** in terminal and your password and get all of the updates offered.
If anything is held back enter **ud2** in terminal to install the ones held back.

I called then ud and ud2 but, you can name them whatever you want.

---

### Post by jeannacav on 2012-06-15
Thanks cavsfan

 Today,I managed to get my son to hold my hand while I did those 3 lines exactly as dr farnsworth had written them and I do have flash installed and working.

I probably have thunderbird too, but oh well.

So, thank you

jeanna

---

### Post by firekage on 2012-06-15
> **bobhaugen said:**
> 
Synaptic said it had to remove the Adobe Flash plugin to upgrade Firefox, which might had been the problem in the first place.  But then the Flash removal failed, so the whole upgrade halted.


BTW - i did this thing earlier and i...regret it till now. Why? Because i upgrade default Firefox (7.0.1 if i remember correctly) to a Firefox 13. I had the same warning that flashplugin should be uninstalled. I did it, i installed Firefox 13 and the problems started right away with flash movies - youtube etc. They wouldn't load, wouldn't play, flashplugin wasn't present or what after upgrading Firefox? There were only icedtea web plugin. Than i purged firefox 13, installed default but problem with flash was still present. I could not install it trough terminal using: 

sudo apt-get install flashplugin-installer
sudo apt-get install flashplpugin-downloader

Only flash that worked after upgrading to firefox 13 and purging it and go back to firefox 7 was from adobe website, but after installation there is no plugin for mozilla firefox...plugin was in flashplugin-installer and flashplugin-downloader but i couldn't install it even with install -f command.

After this whole mess up i had "adobe flashplayer" or "adobe flashplugin" "has crashed - send message" or something similar from few sites with flash movies. 

Without flashplugin-installer or flashplugin-downloader in system i had played movies in firefox on youtube, and so on, trough html5.0 but i couldn't rewind or forward movies at all, so i installed icedtea web plugin (but i read that it is only for 64 bit system).

I tried reinstall, remove, purge but only flash that could be installed for firefox 7 and 13 was from adobe website, other doesen't wokr.

---

### Post by Cavsfan on 2012-06-16
> **jeannacav said:**
> Thanks cavsfan

 Today,I managed to get my son to hold my hand while I did those 3 lines exactly as dr farnsworth had written them and I do have flash installed and working.

I probably have thunderbird too, but oh well.

So, thank you

jeanna

You are welcome Jeanna! Were you able to edit the script file and add those commands ?
```
gedit /home/username/.bashrc 
```

Entering **ud** is much easier than entering 
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean
```
And **ud2** is easier than entering ```
sudo apt-get dist-upgrade
```
Once you put those commands in there you just need to logout and back in for them to work.

> **firekage said:**
> BTW - i did this thing earlier and i...regret it till now. Why? Because i upgrade default Firefox (7.0.1 if i remember correctly) to a Firefox 13. I had the same warning that flashplugin should be uninstalled. I did it, i installed Firefox 13 and the problems started right away with flash movies - youtube etc. They wouldn't load, wouldn't play, flashplugin wasn't present or what after upgrading Firefox? There were only icedtea web plugin. Than i purged firefox 13, installed default but problem with flash was still present. I could not install it trough terminal using: 

sudo apt-get install flashplugin-installer
sudo apt-get install flashplpugin-downloader

Only flash that worked after upgrading to firefox 13 and purging it and go back to firefox 7 was from adobe website, but after installation there is no plugin for mozilla firefox...plugin was in flashplugin-installer and flashplugin-downloader but i couldn't install it even with install -f command.

After this whole mess up i had "adobe flashplayer" or "adobe flashplugin" "has crashed - send message" or something similar from few sites with flash movies. 

Without flashplugin-installer or flashplugin-downloader in system i had played movies in firefox on youtube, and so on, trough html5.0 but i couldn't rewind or forward movies at all, so i installed icedtea web plugin (but i read that it is only for 64 bit system).

I tried reinstall, remove, purge but only flash that could be installed for firefox 7 and 13 was from adobe website, other doesen't wokr.

Not sure what version of Ubuntu you are running *firekage*, but in Precise 12.04 Synaptic Package Manager when I enter flash, 
I see I have **flashplugin-installer**, **libquvi7**, **libquvi-scripts** and **ubuntu-restricted-extras** installed.

BTW, if you haven't already in Firefox 13 go to Edit > Preferences and then click on Tabs at the top and make sure everything is checked.
Then when you open up a new tab, it automatically switches to that tab.
What I really like about FF 13 is that when you click on a new tab you see several of the recent pages you have been to. Which makes it a lot nicer. :)

---

### Post by jeannacav on 2012-06-22
> **firekage said:**
> BTW - i did this thing earlier and i...regret it till now. Why? Because i upgrade default Firefox (7.0.1 if i remember correctly) to a Firefox 13. I had the same warning that flashplugin should be uninstalled. I did it, i installed Firefox 13 and the problems started right away with flash movies - youtube etc. They wouldn't load, wouldn't play, flashplugin wasn't present or what after upgrading Firefox? There were only icedtea web plugin. Than i purged firefox 13, installed default but problem with flash was still present. I could not install it trough terminal using: 

sudo apt-get install flashplugin-installer
sudo apt-get install flashplpugin-downloader

Only flash that worked after upgrading to firefox 13 and purging it and go back to firefox 7 was from adobe website, but after installation there is no plugin for mozilla firefox...plugin was in flashplugin-installer and flashplugin-downloader but i couldn't install it even with install -f command.

After this whole mess up i had "adobe flashplayer" or "adobe flashplugin" "has crashed - send message" or something similar from few sites with flash movies. 

Without flashplugin-installer or flashplugin-downloader in system i had played movies in firefox on youtube, and so on, trough html5.0 but i couldn't rewind or forward movies at all, so i installed icedtea web plugin (but i read that it is only for 64 bit system).

I tried reinstall, remove, purge but only flash that could be installed for firefox 7 and 13 was from adobe website, other doesen't wokr.

If you look at the third line of dr farnsworth's fix, you will see where it says force remove after it said remove.
I think that was the really important part.
I didn't think it had worked because the only reply terminal gave was that it had removed flash, but it had indeed reinstalled it too since it works.
I have no idea if you can try this again with the state things are in, but you might try it and see... it might just fix flash for you.

btw, my son had me copy paste those lines using the right click contextual menu, because terminal won't see the keyboard commands. (This made a difference because I had missed the double dash.)

good luck,

jeanna

the 3 lines are:

> cd /var/lib/dpkg/info/
sudo rm adobe-flashplugin.*
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin 

---

