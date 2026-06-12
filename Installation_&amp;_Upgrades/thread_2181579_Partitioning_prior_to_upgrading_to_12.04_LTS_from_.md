---
title: "Partitioning prior to upgrading to 12.04 LTS from 10.04 LTS"
date: 2013-10-18
forum: Installation &amp; Upgrades
---

### Post by Bill Dubinski on 2013-10-18
Good Day folks, 
   I want to thank you in advance for taking the time to help me out of give me advice on this day. 
I am a three year user of Ubuntu products, done plenty on "new installs" and manual partitioning prior to install. But my question today lies an already established Ubuntu system running 10.04 (Lucid) LTS and I will be converting to 12.04 LTS (Precise). 

Basically I have two questions. But first, I would love to learn option 2 just to say I have learned it and feel confident with partitioning/installing a new OS when there is an existing /home section on the HDD already. 
Basically, my system is configured in this way. 
1 TB Seagate Barracuda HDD
1 GB (Boot) 
40 GB (Root)
20 GB (Swap) I have 16 GB Ram on Computer) (Originally set it up to be little over equal to the RAM in my computer.)
939 GB (/home) I have a separate partition for /home) 

First Question
1) Is it better to "upgrade" from 10.04 LTS to 12.04 LTS and will choosing "upgrade" not mess with my separate /home partition? 

Or, is it better to do a manual re-install but not mess with the /home partition during install of 12.04? I know this is possible, but have not had much luck in the past, but I sort of rather do a fresh install, but not mess with my /home partition. I also want to do it this way so I know I can do it, plus /boot and /root sections will be formatted fresh with 12.04. Plus, I would like to shrink my swap space anyways since I don't need it that large and give the extra space to /home since my system does not use much swap and it is nearly useless (that large) with the RAM I have. 

I have very little experience using GParted and none with any other partitioning package. I used it once a couple years ago, but I diddn't understand it enough I guess for it to do what I wanted to. 

So if you could please, explain to me which is the better or feasible to do option 1. Or if option 1 will accomplish the same goal as option 2. And if It's better to go with option 2, can you please go through the steps and recommendations for accomplishing my goal of a fresh install and not touching /home partition. 

Again, thank you so much for you time, I greatly appreciate it. 

Bill


[h=1][/h]

---

### Post by oldfred on 2013-10-19
I did upgrades with every version from 6.06 thru 9.04. But to change to 64 bit I had to do a clean install with 9.10. That went so well that I only do clean installs, but with larger hard drive, keep old install and just install to a new 25GB / (root) partition. Since my drive is larger and my data needs are not, I now have every install since 10.04 still on my system. Time to house clean obsolete installs. 

I do not hibernate as it boots fast enough, so smaller swap is all that is needed even with my system with 4GB of RAM. You may never use swap with that much RAM, but should have a little like 2 or 4GB.

If manually reinstalling be sure to include existing /home but DO NOT format it. Then the existing /home will be part of new install. 

Definitely try live installer in live mode to see Unity, or install in another 25GB partition to see if you like it. But best not to go back & forth version wise with existing /home. Apps upgrade and may change data in /home and old versions may then have issues.

Gparted is not difficult to use. I do not attempt to queue changes but only do one thing at a time. Of course good backups are important with any system change, but backups should be a normal process.
       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

I stayed with 10.10 for quite a while as the change to Unity was a lot. Some now like Unity, but my monitor is an older 4:3 and top & bottom panels make more sense. Plus oldfred does not change easily. So I use Ubuntu, but install gnome-panel, or fallback, or now with 13.10 fastback


  Unity Video tutorial and Back to Classic Gnome in 11.10. For 12.04 (see post 4) 
[http://iloveubuntu.net/get-basics-ubuntu-1204s-unity-clear-explanatory-27-minutes-youtube-tutorial](http://iloveubuntu.net/get-basics-ubuntu-1204s-unity-clear-explanatory-27-minutes-youtube-tutorial)
[http://ubuntuforums.org/showthread.php?t=1859961](http://ubuntuforums.org/showthread.php?t=1859961)

 sudo apt-get install gnome-panel
On login screen click on logo/cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 
[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

---

### Post by Bill Dubinski on 2013-10-20
I know what you mean about OldFred does not change quickly. MiddleAgedBill here doesn't either. Especially when the old works great and there is always the "uuuum" moment with new stuff and getting used to it. 

Actually, what I did was I had to buy a new HDD for my back up data. I bought almost the exact same drive I had, 1 TB Seagate SATA 6, but the only difference is the new drive has 64MB of cache, and the older 32mb. I used the new drive for the new install and left my older in tact as is. It still has 10.04 on it, while I loaded this one with 12.04. I do plan to later on after I am done setting this up with all my apps and preferences, I am almost done with that, I plan wo re format the older 1TB drive, remove 10.04 and just keep it for data storage.

---

### Post by oldfred on 2013-10-20
You can easily reinstall old apps. But since so old you actually may want to edit list (its just a text file) to remove some that you may not want. 
If it includes any old kernels remove those. And you can remove all the OpenOffice apps as they now are LibreOffice. Not sure what else but some will not be available as obsolete and others may install but have been replaced.

 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

The dpkg list includes all the dependancies so it is a long list.

 Top level only - no depends (not for reinstall)
sudo apt-get install aptitude
aptitude --disable-columns -F '%p' search '~i!~M!~R(~i)' > toplevel 
or
aptitude search '?installed ?not(?reverse-depends(?installed))'

I like to have an install on every hard drive. You might want to install another copy just to experiment with, or have a place to install the newest to see what is coming in the new 14.04LTS. I find then the change easier to manage as the 2 year leap is often a lot of change.

---

