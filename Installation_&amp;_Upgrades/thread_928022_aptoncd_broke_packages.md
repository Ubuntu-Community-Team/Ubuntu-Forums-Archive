---
title: "aptoncd broke packages"
date: 2008-09-23
forum: Installation &amp; Upgrades
---

### Post by lengo on 2008-09-23
I wasn't sure if this should go in "Absolute Beginner Talk" or here, but I put it here. Mods can move if necessary . . .

I installed 8.04 from CD and was kindly informed that there were 252 updates (and as many or more MB :shock:) waiting for me. Being as I am in a country where internet access is at a premium, I visited the network administrator at a local educational institution who kindly provided me with a CD of packages created with APTonCD. I loaded the packages to my cache (/var/cache/apt/archives) and, after a fairly long internet search, found that I could install them with:
```
sudo dpkg -i *.deb
```
Everything installed (be that good or bad) and I ended up with 32 broken packages. And then things started to unravel . . . The same icon that informed me that there were updates available now informed me that there were broken packages and that I could right-click to run Synaptic Package Manager, and run the 'Broken' filter to fix them. I did so, selected one of the broken packages to mark for 'complete removal', and clicked apply. Apparently, all these packages were related because I was informed that to remove the package I had selected I had to remove all 32 broken packages (is this normal?!) Thinking, naively, that Synaptic Package Manager accurately sorted through dependencies and provided the most robust update management around, I went ahead with it. And now I'm screwed . . . The first thing I noticed was my internet connection was gone (wireless managed with wicd). Then I noticed a 'muted' speaker in the upper right (sound packages are missing). Not knowing what else is broken (I have no idea what all the 'lib' files were), is there any way to get back to where I was? I thought Synaptic was meant to protect me from myself, sorting through dependencies that I cannot possible be expected to be aware of. I guess I was wrong. Anyway, wondering if there's any help available out there . . . Thanks.

---

### Post by robert shearer on 2008-09-23
As it is such a new install you might want to consider getting your admin friend to download the Hardy Heron 8.04.1 install cd (same type as you first used ie live desktop or alternate install) as it is the latest version with updates and reinstall.

The aptoncd packages on your cd will be to-date for 8.04.1 but you are trying to install them to 8.04 and dependencies need to be resolved.This would need an active connection.

Usually when using a aptoncd I just put it in the drive and wait for it to load the drive icon.Soon after a box appears asking if I want to open it with the package manager. Hit yes and wait. Synaptic will open and scan the cd and update its sources by adding the cd as a repository.

 At this stage no packages are installed. Close Synaptic and WAIT. The update icon appears in the panel after Synaptic and apt-update have run the new info and adjusted sources and package lists. This can take a while (15 min plus on my 1Ghz/p3/512Mb.)

Then click on the update icon, the update manager will open and show the updates available. Click on install. Unmet dependencies will be advised and you can install all other packages.

Then you can activate your internet connection and run update manager again for the packages with unmet dependencies.
This ensures that the minimum download is used..

---

### Post by lengo on 2008-09-23
Thank you for your helpful reply! The box I saw when I inserted the CD was a choice between Create or Restore. I chose Restore, Loaded the packages (to my /archive directory) and then was stymied . . . at which point I ran sudo dpkg -i *.deb. Patience is a virtue, they say! So I'll try to secure a copy of 8.04.1 and try my luck. Looks like a clean install would make more sense at this point anyway . . .

---

### Post by robert shearer on 2008-09-23
> **lengo said:**
> Thank you for your helpful reply! The box I saw when I inserted the CD was a choice between Create or Restore. I chose Restore, Loaded the packages (to my /archive directory) and then was stymied . . . at which point I ran sudo dpkg -i *.deb. Patience is a virtue, they say! So I'll try to secure a copy of 8.04.1 and try my luck. Looks like a clean install would make more sense at this point anyway . . .

Yes, that is the box you get when you OPEN the aptoncd application.

If you just put the cd into the drive as if it were any other media and wait then the default action of Ubuntu is to recognise it as a cd of software packages and ask if you want to open it with the package manager (default is Synaptic) click yes and it will run as outlined in my first post.

In other words you don't need to open aptoncd and restore.This alternative works too.

Also from your post be aware that it takes a while for aptoncd (if you do elect to use the restore option) to sort and configure the packages and that nothing appears to happen for a long time. If you want to see this in action open a terminal and type 
```
top
```
then look for apt-update (from memory here so could be variation of) and when it finishes then the update icon should appear in the panel.

So there are two options to use aptoncd .

1) Use the Restore option within the application to copy and update all the packages from the cd to your computer.

2) Add the cd as a local repository where the details of the packages are added to  Synaptics "database" and the packages will be loaded from the cd as needed. (it will ask you to insert the cd when it needs to copy packages)

---

### Post by roshanjose on 2008-12-18
i haven't got a cd but i got all the packages into a pen drive...

so this does not install the packages by itself

---

