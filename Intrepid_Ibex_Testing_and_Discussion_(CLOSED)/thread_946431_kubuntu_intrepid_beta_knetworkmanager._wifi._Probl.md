---
title: "kubuntu intrepid beta: knetworkmanager. wifi. Problems and Fixes"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by linomac on 2008-10-13
Knetworkmanager can become one of the most irritating problems of kubuntu intrepid beta testers. other will try hard to fix it, others will just simply wait till final.
I tried to gather as much information as possible about the matter, and here i present my outcomes. Hope to be useful for someone.

Although I could see my wifi network as available and knetworkmanager tried to connect to it, it was failing.

I resolved my problem with
1.
```
aptitude reinstall knetworkmanager network-manager wpasupplicant
```and
2.
```
aptitude install nscd
```Nscd caches libc-issued requests to the Name Service. If retrieving NSS data is fairly expensive, nscd is able to speed up consecutive access to the same data dramatically and increase overall system performance.

Some hints to resolve your problems
1. Check the logs
```
less /var/log/syslog
```2. Learn to use the following commands

list network devices
```
lshw -C network
```check wireless extensions
```
iwconfig
```scan for wifi networks on range
```
iwlist wlan0 scan
```for extra info to see what is going on
```
dmesg
```and while connecting
```
iwevent
```3. Warning: if wlan0 is defined in /etc/network/interfaces Knetworkmanager will NOT configure it. 
So, you can either choose the manual configuration or Knetworkmanager

----------------------------------------------------------------------------------

More sources to read:

[http://live.gnome.org/NetworkManager](http://live.gnome.org/NetworkManager)
[http://live.gnome.org/NetworkManager](http://live.gnome.org/NetworkManager)
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)
[http://en.opensuse.org/Projects/KNetworkManager](http://en.opensuse.org/Projects/KNetworkManager)
[http://en.wikipedia.org/wiki/NetworkManager](http://en.wikipedia.org/wiki/NetworkManager)
[http://freedesktop.org/wiki/NetworkManager](http://freedesktop.org/wiki/NetworkManager)
[http://www.redhat.com/magazine/003jan05/features/networkmanager/](http://www.redhat.com/magazine/003jan05/features/networkmanager/)
[https://help.ubuntu.com/community/NetworkAdmin](https://help.ubuntu.com/community/NetworkAdmin)
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu](https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu)

--------------------------------------------------------------------------
--------------------------------------------------------------------------

Problems still existing at my computer as of 13 October 2008 latest beta updates:
1. available wifi networks are not shown in the list with right click at tray icon. they are shown only if i want to create new wifi conection
2. i dont see option for dial-up connections and for vpn as i see in screenshots for gnome intrepid
3. preinstalled 3G (mobile internet) operator settings are not shown, like in nm-applet of gnome intrepid
4. no "conect to other network options"

Other users have also mentioned various problem in usability of knetworkmanager
[http://weblog.obso1337.org/2008/expert-review-of-knetworkmanager-07/](http://weblog.obso1337.org/2008/expert-review-of-knetworkmanager-07/)

--------------------------------------------------------------
Other places where knetwork bugs are discussed and u can contribute with your feedback or find solutions

[https://bugs.launchpad.net/opensuse/+source/knetworkmanager/+bug/259278](https://bugs.launchpad.net/opensuse/+source/knetworkmanager/+bug/259278)
[http://bugs.kde.org](http://bugs.kde.org)

-----------------------------------------------------------------

other places where someone can check other possible info
[http://forum.kde.org/](http://forum.kde.org/)
[http://www.kubuntuforums.net/](http://www.kubuntuforums.net/)
[http://kubuntuway.net/](http://kubuntuway.net/)

----------------------


update: i checked a computer with kubuntu hardy - kde4 remix.
network manager works nice there, but it is the old version 0.2 something
maybe there is way to put this old version at intrepid? because 0.7 it is just svn as i understand
so beta intrepid + beta knetworkmanager = ...

---

### Post by jacksaff on 2008-10-16
If anyone knows a painless way to downgrade to the old version of knetworkmanager that is in hardy (it runs on kde3) I'd be very appreciative. The missing functions in the new version are leading to missing hair here.
The version in intrepid doesn't even seem to have a presence on the web. All the info I can find shows the old version. Will the kde4 manager be ready in time for 8.10? It's a huge step backwards in terms of missing functions at the moment.

---

### Post by hyper_ch on 2008-10-16
I would use WICD as network manager: [http://wicd.sourceforge.net](http://wicd.sourceforge.net) - actually I use it on Kubuntu Ibex

---

### Post by linomac on 2008-10-16
i agree with you.
maybe they are working on it.
we ll see what happens in 2 weeks

---

### Post by linomac on 2008-10-16
> **hyper_ch said:**
> I would use WICD as network manager: [http://wicd.sourceforge.net](http://wicd.sourceforge.net) - actually I use it on Kubuntu Ibex

Questions for WICD

does it integrate well with kde?
do u see trayicon?

should i remove knetworkmanager and also networkmanager service?
or i let NetworkManager service running ?

does it locates automatically the interfaces or should i set them up at /etc/network/interfaces

---

### Post by hyper_ch on 2008-10-16
yes, it integrates with kde and yes, you see a trayicon (after you've logged out of the session and started it again) and it will auto-deetec interfaces, no need to edit the interfaces file and when you add the wicd repository it will also auto-remove the knetworkmanager and its service. It will be a replacement for it.

Just add the repository and install wicd :)

---

### Post by linomac on 2008-10-16
thanks a lot hyper_ch
you are great!
i m going to try it

---

### Post by linomac on 2008-10-16
after latest upgrades knetworkmanager connects with wifi,but the problems continue.

the newconnection-> wlan0 does not find all networks available, even the closest ones, autoupdate for network scanning does not work
generally it has hard time scannig for networks

---

### Post by Dareus on 2008-10-24
I had some troubles with bc43 firmware but now it works, quite well to be honest (at least as well as in hardy to me). I thing that i really dislike is the old qt3 style, a lot of efforts were put in porting adept, kdesudo and other tools to qt4, why not do the same for knetworkmanager?

---

