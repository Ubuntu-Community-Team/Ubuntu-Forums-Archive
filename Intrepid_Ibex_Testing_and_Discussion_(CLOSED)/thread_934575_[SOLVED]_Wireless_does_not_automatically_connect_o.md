---
title: "[SOLVED] Wireless does not automatically connect on boot"
date: 2008-09-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by wilsong on 2008-09-30
Hello, I am running Ubuntu 8.10 Alpha 6,

I have had ubuntu start and ask me to enter the WEP key, for the wireless but i would like to have it auto connect, when i try to set it up for auto connecting, it doesnt connect and it always seems that i have to go into Network Connections, Wireless, and click on Auto (My Wireless Routers SSID here) and it says 9 hours ago (last time i connected i suppose)

When i edit that, it says "auto ssid"

I have checked Connect Automatically , I checked System setting (i am a little confused on what this does, but i am wanting it to always find and connect to this device anytime its in range..

When i set the wireless ssid its already correct,
Mode Infrastructure
MTU auto

BSSID blank
MAC blank

Wireless Security WEP 40/128-Bit key

I use a 128bit key, i click show key, and type it in..

Wep index 1 Autho Open system,

I set IPv4 to the settings i use, and i have also tried to do Auto DHCP,

the only problem, it will connect, but when i reboot, i start again it doesnt automatically connect, i always have to reenter the ssid wither in the popup box that comes up when i boot, or having to go into Network connections.

Please help! Thanks

ran lshw -C network 

heres the results for the wireless 

 *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
*-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1b:fc:44:99:3a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.92 multicast=yes wireless=IEEE 802.11bg

---

### Post by blakamin on 2008-10-01
Does the same for me with WPA.
Quite annoying and I still haven't found a work-around:( 
 ```
*-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:6d:3f:ea
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 01
       serial: 00:19:7e:c1:a3:5f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.200 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
```

---

### Post by wilsong on 2008-10-01
Its nice to see that I am not the only one. Anyone else having similar issues? Anyone else have any questions or need any info from me I would be happy to give to figure this out. Thanks.

---

### Post by lisati on 2008-10-01
Have a look here: [http://ubuntuforums.org/showpost.php?p=1351902&postcount=2](http://ubuntuforums.org/showpost.php?p=1351902&postcount=2)

---

### Post by garba on 2008-10-01
or here:

man iwconfig
man wpa_supplicant

i can't stand networkmanager anymore, most of the troubles people are having with wireless devices is not because of poor drivers for their hardware, it's because of NM sucking to no end, on hardy my wireless card (d-link) works no problem with WPA, but not through NM, which can't even get my card associated with my WPA-protected AP

---

### Post by taavikko on 2008-10-01
Is automatic login enabled?
That used to raise this issues...
Can't be sure now, since never used automatic login.

But for a workaround disable automatic login, if that clears yous issue.

---

### Post by DavidONE on 2008-10-01
I tried disabling auto login - it made no difference.

---

### Post by wilsong on 2008-10-01
> **taavikko said:**
> Is automatic login enabled?
That used to raise this issues...
Can't be sure now, since never used automatic login.

But for a workaround disable automatic login, if that clears yous issue.

No, i do not have it set to automatically login.

---

### Post by wilsong on 2008-10-02
If any new people have installed the BETA and are having issues with Network Manager not remembering your password or connecting automatically please repost here thanks!

---

### Post by SarahKH on 2008-10-02
> **wilsong said:**
> If any new people have installed the BETA and are having issues with Network Manager not remembering your password or connecting automatically please repost here thanks!

*raises hand*

Using the ath5k_pci module.

---

### Post by kakalaky on 2008-10-02
Also broke here.

---

### Post by Foaming Draught on 2008-10-03
Same here, Intel ipw2200.

---

### Post by wilsong on 2008-10-03
Just to verify, everyone sets up their wireless connection, and every reboot, the network manager ask for the WEP Key, you can enter it but it never remembers and doesn't connect automatically from boot, as i would imagine we all would like making our network a "preferred AP/Router" 

It seems like different wireless cards / and more users seem to be agreeing about this, really would be nice to have a Network Manager fix.. anyone know if there is a bug out? ill check launchpad and see if i can find anything.  

PLEASE Keep posting if your having the same issue!

---

### Post by wilsong on 2008-10-03
I think i might have found a fix for this issue... 

Updating to 0.7~~svn20080928t225540+eni0-0ubuntu2~nm3 . Once entered password is now displayed in the nm-applet connection settings panel!

I updated Network-Manager to the version mentioned above by adding

deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main

to the sources.list.

Please anyone test and let me know if they have any luck too!?

---

### Post by wilsong on 2008-10-03
AWESOME :)! AGAIN Verified the problem FIXED! :D 

network-manager (0.7~~svn20080928t225540+eni0-0ubuntu2)

Network Manager and Gnome Keyring are not working together like they should, because NM 0.7 sets hostname to localhost.localdomain instead of what is in /etc/hostname - we fallback to hostname configured in  /etc/hostname even when no distro specific system plugin is enabled; 



Can someone else update Network-Manager with the above Repo's and see if it fixes theirs too :)!! 

I'm going to mark this solved!! If anyone else sees anyone on the forum that has wireless issue try to show them the steps in the future ;) hopefully this will get on a regular update repo soon! thanks for the help!

---

### Post by supersmashbrothers on 2008-10-03
I confirmed that NetworkManager from the Intrepid repository version 0.7~~svn20080928t225540+eni0-0ubuntu2 auto connects and does not not ask for a password after you give it once.

---

### Post by wilsong on 2008-10-03
> **supersmashbrothers said:**
> I confirmed that NetworkManager from the Intrepid repository version 0.7~~svn20080928t225540+eni0-0ubuntu2 auto connects and does not not ask for a password after you give it once.

When you say Intrepid Repository are you referring to [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main   the repo i stated that you would have had to add to your list.. or the Original Ubuntu repos, because as far as i know the launchpad isnt added, and i dont think the package as been added to the regular repos.. just wanted to clarify, thanks though glad its working for you!!

---

### Post by hyper7 on 2008-10-03
> **wilsong said:**
> AWESOME :)! AGAIN Verified the problem FIXED! :D 

network-manager (0.7~~svn20080928t225540+eni0-0ubuntu2)

Network Manager and Gnome Keyring are not working together like they should, because NM 0.7 sets hostname to localhost.localdomain instead of what is in /etc/hostname - we fallback to hostname configured in  /etc/hostname even when no distro specific system plugin is enabled; 



Can someone else update Network-Manager with the above Repo's and see if it fixes theirs too :)!! 

I'm going to mark this solved!! If anyone else sees anyone on the forum that has wireless issue try to show them the steps in the future ;) hopefully this will get on a regular update repo soon! thanks for the help!

Totally solved.

I was having to re-enter my key after every boot, but after updating network manager, it saved the pass to keyring and works like a charm

Thanks for the info, man.

---

### Post by wilsong on 2008-10-03
> **hyper7 said:**
> Totally solved.

I was having to re-enter my key after every boot, but after updating network manager, it saved the pass to keyring and works like a charm

Thanks for the info, man.

 Sweet, If anyone else can verify, please post, and if you know someone that is looking for a solution if you want to tell them, i dont know if this is the first thread on this or not, if someone knows of a previous thread (the first thread we could consolidate. AWESOME! Long live Ibex!

---

### Post by beameup on 2008-10-03
I had that problem and it also wouldn't stay connected long. WICD has been working fine. I'll give this a try tomorrow and see how it goes.

---

### Post by alej on 2008-10-03
any reason why this fix isn't making it to the official repos?

---

### Post by beameup on 2008-10-03
Couldn't wait. After installing I still have the disconnect problem, so I went back to WICD which works. 
I suspect this has something to do with the acer-wmi not supported boot message, but as long as I have working wifi, guess I'll leave it alone.

I might have to give the acerhk tool a try.

Glad it's solved everyone's issues though.

---

### Post by Lorenz on 2008-10-03
I have the same problem and additionally I have to start Network Manager via Terminal and "nm-applet" on each startup. I have a ipw3945 card.

---

### Post by wilsong on 2008-10-03
> **beameup said:**
> Couldn't wait. After installing I still have the disconnect problem.

I dont know if you were having the boot trouble, or maybe this ath_pci problem check this thread [http://ubuntuforums.org/showthread.php?t=936712&page=2](http://ubuntuforums.org/showthread.php?t=936712&page=2) 

2 people have had this work, including me, I am glad your solution is working maybe you can post a bug if you can figure out whats going on.

---

### Post by wilsong on 2008-10-03
> **Lorenz said:**
> I have the same problem and additionally I have to start Network Manager via Terminal and "nm-applet" on each startup. I have a ipw3945 card.

Did you see the part where it talked about the solution? Its on page 2, see if it might work..

---

### Post by wilsong on 2008-10-03
> **alej said:**
> any reason why this fix isn't making it to the official repos?

I guess someone fixed network manager on launchpad and is just waiting for it to get approve or whatever process it takes to get something on the repo?

---

### Post by hyper7 on 2008-10-03
> **alej said:**
> any reason why this fix isn't making it to the official repos?
Network manager has been getting tons of updates and they haven't frozen a specific build for Ibex yet.

---

### Post by wilsong on 2008-10-03
NOTICE: 

To everyone that updated using this, and it worked, I saw a new update come through just a few ago.. but i didnt update to it, 

it was 0.7~~svn20080927t101113-0ubuntu and I am not sure if it has the fix applied from

0.7~~svn20080928t225540+eni0-0ubuntu2~nm3

anyone willing to test and try it to see if it works with connecting on boot? At this point I am not willing to (because its working) the date looks to be the only difference, 9/27  and 9/28.. I am going to stick with this one but anyone willing to be a "tester" and find out for us would be great.. thanks

---

### Post by beameup on 2008-10-03
> **wilsong said:**
> I dont know if you were having the boot trouble, or maybe this ath_pci problem check this thread [http://ubuntuforums.org/showthread.php?t=936712&page=2](http://ubuntuforums.org/showthread.php?t=936712&page=2) 

2 people have had this work, including me, I am glad your solution is working maybe you can post a bug if you can figure out whats going on.

Ok, I'll have a look at it. Whatever happened to NM on my Acer TM4502, happened in Hardy and I'm not sure what caused it. I only used official update repos. 

NM will connect but almost immediately loses signal and disconnects and continues that same pattern. I'm only about 20' from the router, get a 99% signal with Wicd.

I had posted a thread a few days ago with the error messages I had while booting but it's not answered yet. I can't find which log to look at so I can post a detailed description.

[http://ubuntuforums.org/showthread.php?t=932453](http://ubuntuforums.org/showthread.php?t=932453)

---

### Post by kakalaky on 2008-10-03
> **wilsong said:**
> NOTICE: 

To everyone that updated using this, and it worked, I saw a new update come through just a few ago.. but i didnt update to it, 

it was 0.7~~svn20080927t101113-0ubuntu and I am not sure if it has the fix applied from

0.7~~svn20080928t225540+eni0-0ubuntu2~nm3

anyone willing to test and try it to see if it works with connecting on boot? At this point I am not willing to (because its working) the date looks to be the only difference, 9/27  and 9/28.. I am going to stick with this one but anyone willing to be a "tester" and find out for us would be great.. thanks
I just installed the update and it fixed the problem.  Just click "always allow" when it prompts you for access to the default keyring.

---

### Post by wilsong on 2008-10-04
> **beameup said:**
> Ok, I'll have a look at it. Whatever happened to NM on my Acer TM4502, happened in Hardy and I'm not sure what caused it. I only used official update repos. 

NM will connect but almost immediately loses signal and disconnects and continues that same pattern. I'm only about 20' from the router, get a 99% signal with Wicd.

I had posted a thread a few days ago with the error messages I had while booting but it's not answered yet. I can't find which log to look at so I can post a detailed description.

[http://ubuntuforums.org/showthread.php?t=932453](http://ubuntuforums.org/showthread.php?t=932453)

I do think that network manager has several things that they are working on and need to fix before intrepid goes into full release.. it seems they have a few issues to iron out.. I am glad there is something that works for you I am not as familiar with WICD, but i did once use a program called Wifi-radar that was  very nice in hardy (because hardys network manager didnt show signal strengths and was  very odd if you wanted to connect to a wireless network.

---

### Post by faustobp on 2008-10-06
Does anyone knows if the maintainers of network-manager on intrepid are aware of this bug (I can't find the bug on launchpad)? 

There are plans to include this fix on official intrepid repositories before release?

---

### Post by mschraier on 2008-10-06
i am using the Beta version.  My wifi light goes on but when i click on the silver earth in the systray there are no wifi connections shown.  so i go and create a new one by selecting my SSID. then save and connect.  the silver earth remains and no signal bars show.  i am also running hardy on a separate partition with no issues.  this was a beta installed from a downloaded ISO.

---

### Post by hyper7 on 2008-10-06
> **mschraier said:**
> i am using the Beta version.  My wifi light goes on but when i click on the silver earth in the systray there are no wifi connections shown.  so i go and create a new one by selecting my SSID. then save and connect.  the silver earth remains and no signal bars show.  i am also running hardy on a separate partition with no issues.  this was a beta installed from a downloaded ISO.

What wireless card do you use, and have you hard-connected and installed the latest updates?

---

### Post by beameup on 2008-10-07
> **wilsong said:**
> I do think that network manager has several things that they are working on and need to fix before intrepid goes into full release.. it seems they have a few issues to iron out.. I am glad there is something that works for you I am not as familiar with WICD, but i did once use a program called Wifi-radar that was  very nice in hardy (because hardys network manager didnt show signal strengths and was  very odd if you wanted to connect to a wireless network.

After todays kernel update and a slew of others, I reinstalled Network Manager and it's now working fine  :guitar: 

Looks like my sound is working better too. I have to check a few things out, but thats another thread.

---

