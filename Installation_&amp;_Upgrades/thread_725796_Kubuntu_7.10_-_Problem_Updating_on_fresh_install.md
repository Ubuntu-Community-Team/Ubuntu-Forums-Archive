---
title: "Kubuntu 7.10 - Problem Updating on fresh install"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by smiv on 2008-03-16
Hi All,

First of all, my apologies if this problem has already been identified in another post. If it has, please direct me there. I have done a quick search however, I'm supposed to be studying so I just want a quick solution.

I'm having a very strange problem updating Kubuntu 7.10 when I do a fresh install. Below is the sequence of events.

 1. Boot Kubuntu for the first time
 2. Install nvidia drivers by clicking the popup tray icon.
 3. Restart pc.
 4. Open Adept from "updates" tray icon.
 5. Fetch update list and commence downloading.
 6. Adept begins installing and part way through shows the following message.
*    "There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages. "*
 7. Click ok. Adept now displays the following message.
*     "A new distribution version is available! Click next if you wish to upgrade now."*
 8. Click the "Version Upgrade" button
 9. Click next a few times to get through the upgrade wizard (no special options or anything, only messages are displayed)
 10. Upgrade manager starts getting update list.
 11. A message is displayed stating that canonical no longer supports "libportaudio0".
 12. The upgrade list is displayed. Click start upgrade.
 13. Upgrade manager hangs on the 4th task, "Installing the upgrades". 0% is displayed. No terminal info is displayed. No cpu or disk usage apparent.

I tried this once last night and thought that my install image was out of date, so I downloaded a new one and tried again today to no avail. I haven't tried any other methods such as using apt. I don't believe that such a simple process should require any fiddling at all. 

If anyone has had this problem or knows of this problem, please let us all know. If screenshots or more info is required, please let me know.

Thanks

---

### Post by LarryJ2 on 2008-03-17
Just FYI,  I also have this problem.  Problem has appeared in multiple fresh installs of Kubuntu 7.10 Desktop.  No solution found yet.

---

### Post by taurus on 2008-03-17
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by DMK62 on 2008-03-17
Hi

I have also run into this problem with a clean install of Kubuntu. To the best of my knowledge there is a bug in the Adept Updater. It tells you there is a new version available but that is not the case.

It will also run into dependency problems with Qt3 if I remember correctly. That is most likely the source of your error of could not commit changes.

Do you have any data on the system right now ? If so, back it up and I would personally recommend just doing another clean install. 

This method worked for me.

1. Clean install

2. Install the nvidia drivers with the Restricted Drivers manager. Reboot and make sure 3d acceleration is working by testing it by running glxgears in konsole.

3. Install the updates and if you encounter that error wait until it finishes. It will give you list of items that could not be updated. Then click ok and then make sure to click on Quit and not Upgrade. Reboot the system.

4. From konsole run the following commands.

sudo apt-get update

sudo dpkg --configure -a

You may be prompted during the updates on whether to update or keep current version of qt3 or something similiar to that. Enter N to keep current version. I did that and did not encounter any issues later on.

Reboot when that is finished.

5. From konsole run

sudo apt-get update

sudo apt-get upgrade

sudo apt-get clean

hth 

Dale

---

### Post by LarryJ2 on 2008-03-17
> Post your /etc/apt/sources.list.

Here's my sources.list: (attached as temp.txt)

---

### Post by DMK62 on 2008-03-17
LarryJ2

I am currently not on Kubuntu so I can't say for sure about the sources.list but it looks ok to me. As mentioned in my previous post there is a bug with adept and there is an issue with dependencies when installing the updates to a clean install. 

I tested it with 3 clean installs using the Ubuntu main server, the main canadian server, and the university of sherbrooke ( montreal ) servers and they all ended up having the same problems. 

The problem with adept offering an upgrade after the updates are finished is something that was in beta, rc, and final releases of Kubuntu 7.10. After installing the initial updates it goes away. 

You may want to check the kubuntu forums for additional info as the could not commit  message is a common post on the forums there.

Hopefully some of these issues will be cleared up with the release of Kubuntu Hardy.

If you have any additional questions please feel free to ask.

Dale

---

### Post by LarryJ2 on 2008-03-18
Thanks Dale.  I think I have enough knowledge of Ubuntu now so that I can productively  participate in the Hardy Beta.  Maybe we can squash some of these irritations early on.   
Larry

---

### Post by DMK62 on 2008-03-18
You're welcome Larry.

Hopefully the Hardy version of Kubuntu will be more stable than the last few releases of Kubuntu.

Once Kubuntu Gutsy Gibbon is set up it is fairly stable. You just need to be able to deal with the current bugs. I am currently using a Ubuntu based KDE distro , Mint 4.0 KDE Community Edition, and it is stable so far and without the updating bugs etc which affect the current Kubuntu release. It is not quite as fast as Kubuntu but I can deal with that if it is more stable. I will definitely be trying Hardy shortly after it is released.

Just my opinions concerning Kubuntu. It does have less devs to maintain it and bug fixes can be long in coming. It is mainly kde 3.5.8 with some kde 4.0 components added that may be a source of problems. An example was strigi when it was first released last fall. I think to a certain degree most KDE distros are affected by the have one foot planted in 3.5.x and the other in 4.x. Once KDE 4 is stable I think there will be a noticable difference in stability, etc.

I browsed a few of your previous posts and I would say you definitely have more than enough knowledge to know your way around Ubuntu / Linux.

Dale

---

