---
title: "Broadcom wireless not working in Karmic Alpha 3"
date: 2009-08-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by fjosh on 2009-08-10
I'm unable to get my Broadcom wireless working even after installing bcmwl-kernel-source.  Checked "dkms status" and it seems to be compiled correctly.


 I can get it working under b43-fwcutter but transfer speeds are 100 - 300 bytes/second under this method with 50-60% signal strength.


 Let me know if further information is needed. It's hard to really do anything as internet access through a wired connection is not possible and I have to boot into an XP partition to relay any information.

---

### Post by The Toxic Mite on 2009-08-10
> **fjosh said:**
> I'm unable to get my Broadcom wireless working even after installing bcmwl-kernel-source.  Checked "dkms status" and it seems to be compiled correctly.


 I can get it working under b43-fwcutter but transfer speeds are 100 - 300 bytes/second under this method with 50-60% signal strength.


 Let me know if further information is needed. It's hard to really do anything as internet access through a wired connection is not possible and I have to boot into an XP partition to relay any information.

Heh. Do realise that Karmic is unstable so don't expect everything to work. ;)

Have you got a stable release of Ubuntu kicking about in your room/house somewhere?

---

### Post by fjosh on 2009-08-10
> **The Toxic Mite said:**
> Heh. Do realise that Karmic is unstable so don't expect everything to work. ;)

Have you got a stable release of Ubuntu kicking about in your room/house somewhere?
Yes and yes.

I'm also running Intel video so I really wanted to give 9.10 a try to see if the Intel regression issues of Jaunty were fixed at all.

I also realize the answer to that is the last LTS.

I'd also rather at least try at trouble shooting any current Alpha release issues I'm having as to do my part at attempting to move the community forward.

Nearly everything on this laptop runs better on XP and that, well, sucks.

---

### Post by tekstr1der on 2009-08-10
Running Broadcom wireless on karmic here for the full dev cycle without issue since dkms came about. You are sure the kernel is loading the correct driver?
```

lsmod | grep wl
```

Also, check System>Administration>Hardware Drivers. Is the Broadcom STA wireless driver listed and in use?

---

### Post by fjosh on 2009-08-10
> **tekstr1der said:**
> Running Broadcom wireless on karmic here for the full dev cycle without issue since dkms came about. You are sure the kernel is loading the correct driver?
```

lsmod | grep wl
```Also, check System>Administration>Hardware Drivers. Is the Broadcom STA wireless driver listed and in use?
Regarding the Hardware Drivers app, it's completely blank.  When I was attempting at getting b43-fwcutter running half way decently it did show the b43 driver as activated.

I'll get back to you in a few minutes about the results of ```
lsmod | grep wl
```

EDIT: It returns nothing.  Reading through the entire list lsmod brings up shows nothing regarding any wireless device.

---

### Post by taavikko on 2009-08-10
What does the "dkms status" say, rather than just telling it's been compiled.
check the "dmesg" for any clues.

also "nm-tool" provides a little info.

---

### Post by fjosh on 2009-08-10
```
josh@printer:~$ dkms status  
bcmwl, 5.10.91.9+bdcom, 2.6.31-3-generic, i686: installed
```I'm unsure if there is a specific entry I should be grepping from dmesg but the command by itself returns far too much information to be useful.

lspci returns:
```
02:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

nm-tool returns information regarding the 10/100 wired connection only:
```
 	josh@printer:~$ nm-tool   

 NetworkManager Tool  
 

 State: disconnected  
 

 - Device: eth0 -----------------------------------------------------------------  
   Type:              Wired  
   Driver:            8139too  
   State:             unavailable  
   Default:           no  
   HW Address:        00:03:25:25:5A:94  
 

   Capabilities:  
     Carrier Detect:  yes  
     Speed:           10 Mb/s  
 

   Wired Properties  
     Carrier:         of
```

Also, after reading your sig, I would like to thank everybody so far for the help.

---

### Post by tekstr1der on 2009-08-10
Are you still running RC3 kernel?

```
uname -r
```

 If you are on the newer 31-5 kernel you need to rebuild the dkms module against it.

```
sudo aptitude reinstall bcmwl-kernel-source
```

---

### Post by fjosh on 2009-08-10
> **tekstr1der said:**
> Are you still running RC3 kernel? If you are on the newer 31-5 kernel you need to rebuild the dkms module against it.
2.6.31-3-generic

Nothing has been updated.  Just a fresh install of Alpha 3, and I didn't get the ISO from the daily builds.

---

### Post by meborc on 2009-08-10
i had the same problem in kubuntu 4 days ago daily-live... installed the STA drivers from the command line, the hardware manager showed empty... nm found access points but was unable to connect... 

will dig deeper ;)

---

### Post by tekstr1der on 2009-08-10
Did you remove b43-fwcutter? Almost seems like the kernel is trying but failing to load a different driver. b43 will not work anymore. Unless you have reason not to, I would fully update the system. When the newer kernel is installed, the dkms module will be built automatically for it. Watch the terminal output as this happens and verify afterward with dkms status.

---

### Post by fjosh on 2009-08-10
> **tekstr1der said:**
> Did you remove b43-fwcutter? Almost seems like the kernel is trying but failing to load a different driver. b43 will not work anymore. Unless you have reason not to, I would fully update the system. When the newer kernel is installed, the dkms module will be built automatically for it. Watch the terminal output as this happens and verify afterward with dkms status.
I indeed did.

```
sudo apt-get remove b43-fwcutter
```

Unless there is something further to do.

Updating everything is out of the question until I get wireless working, unfortunately.  I have no wired internet access.

---

### Post by taavikko on 2009-08-10
check that wireless radio switch is on (nothing is blocked)
```
rfkill list
```

---

### Post by fjosh on 2009-08-10
```
josh@printer:~$ rfkill list   No command 'rfkill' found, did you mean:  
Command 'rafkill' from package 'rafkill' (universe)
```Unsure if rafkill was just an updated/different version of rfkill I did this:


```
josh@printer:~$sudo apt-cdrom add
``````
josh@printer:~$sudo apt-get install rafkill
```Which it told me it couldn't find the package.  I'll search for a .deb.

---

### Post by taavikko on 2009-08-10
> **fjosh said:**
> ```
josh@printer:~$ rfkill list   No command 'rfkill' found, did you mean:  
Command 'rafkill' from package 'rafkill' (universe)
```Unsure if rafkill was just an updated/different version of rfkill I did this:


```
josh@printer:~$sudo apt-cdrom add
``````
josh@printer:~$sudo apt-get install rafkill
```Which it told me it couldn't find the package.  I'll search for a .deb.

NO, I meant for an rfkill
it's a tool provided by wireless-tools, it was introduced in
```
wireless-tools (29-2ubuntu2) karmic; urgency=low

  * Added rfkill from sipsolutions.net
    http://git.sipsolutions.net/rfkill.git
    HEAD 942974036993a84d0beede0c1bbc19cdd3e9db40
    Added rfkill/COPYING to debian/copyright
    Added rfkill/README to debian/README.Debian

```
But since your not up-to-date chances are your running previous version...

---

### Post by fjosh on 2009-08-10
Sorry for the confusion.  I'm still learning a lot everyday.

Hopefully I did this right then.

I downloaded the deb of wireless-tools from the Karmic category at packages.ubuntu.com which I am assuming is the latest version, booted back over into Ubuntu, and installed it.  After that:

```
josh@printer:~$ rfkill list   
josh@printer:~
```It just sends me back to a command prompt with no information given.

I guess that is a step better than command not found.

---

### Post by BXCracer on 2009-08-10
I don't know how about you guys but the b43 driver gives a lot better performance for me. Speed and latency is much better with it. Even though STA drivers reports better signal strength, my router shows that signal is stronger with the b43 one.
Do any of you have such issues with STA driver ?

---

### Post by Luca_turicci on 2009-08-12
hi there guys, i just installed Karmic Alpha 3, Netbook Remix on a HP Mini 110, my wireless card isn't working either, although, everything else works so far. Mine is a BCM4310 wireless card, and i remember when i booted with the live USB i could choose frome 2 Wireless drivers, one privative and one open-source, anyone has been able to solve the problem?

---

### Post by Peter09 on 2009-08-12
My D-Link usb wireless dongle has not been working for weeks, don't know if this is the same bug.

---

### Post by fjosh on 2009-08-12
It's frustrating to say the least and the only thing keeping XP on my HDD.

I wonder if MS pays these companies, such as Broadcom, to stay out of the Linux sector of the market.  ;)

---

### Post by meborc on 2009-08-13
just tried with kubuntu daily (yesterdays version)... no luck... :( i guess i will have to wait some more

---

### Post by geordish on 2009-08-13
I had the same issue as fjosh, running all up to date, and:
Linux mercury 2.6.31-5-generic #24-Ubuntu SMP Sat Aug 1 12:48:18 UTC 2009 i686 GNU/Linux

I did rfkill list as mentioned above, and got given:

```

dave@mercury:~$ rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: yes
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

ran rfkill unblock all, and my wireless connected straight up. Odd! I also assume bluetooth wasn't working too.

---

### Post by Luca_turicci on 2009-08-13
> **fjosh said:**
> 
I wonder if MS pays these companies, such as Broadcom, to stay out of the Linux sector of the market.  ;)

I don't know, but i've read somewhere that MS prevents companies like HP from making powerfull netbooks unless they run windows, i guess that's because of linpus, MI, and the thing running on EEEPC. 

Also i remember something about Foxconn motherboards not working properly with linux.

---

### Post by novafluxx on 2009-08-13
Never had a problem in previous releases with my Broadcom wireless card (Including Jaunty alpha's and  Intrepid). It always worked out of the box.

I installed Karmic after Alpha 3, and null, zero, nothing.

Regression?

I'm going to try alpha 4 right now, and see what happens...:(

---

### Post by fjosh on 2009-08-14
> **novafluxx said:**
>  I'm going to try alpha 4 right now, and see what happens...:(
No luck, it's still broke for me after formatting and reinstalling Alpha 4.

Is bcmwl-kernel-source working for anybody with Broadcom?

---

### Post by Slug71 on 2009-08-14
Working for me. After i did a fresh install with Alpha 4 it wasnt. I checked Synaptic and it said the bcmwl driver was installed. I installed DKMS and rebooted and then it said that the bcmwl driver wasnt installed. Installed the bcmwl driver in Synaptic again and rebooted and now my wireless works good. 

I think DKMS and the bcmwl driver both need to be installed, and they arent by default. At least thats what ive found.

---

### Post by Slug71 on 2009-08-14
Damn NM keyring is annoying though. Have to enter a stupid password after every reboot/startup.

---

### Post by tekstr1der on 2009-08-14
> **Slug71 said:**
> I think DKMS and the bcmwl driver both need to be installed, and they arent by default. At least thats what ive found.

Yes, that's absolutely true. Without DKMS, the module will not be built against the current kernel when you install bcmwl-kernel-source. 

Working fine here.

---

### Post by Luca_turicci on 2009-08-15
> **Slug71 said:**
> Damn NM keyring is annoying though. Have to enter a stupid password after every reboot/startup.

Yeah, I found that annoying too. Plus it always asks me for permission to mount the windows partition at start up.

And yeah, the wireless drivers are not installed by default. That kinda sucks. But i'm not having anymore trouble with the Gnome Daemon, or anything, no more messages of apps crashing. that's great, this Alpha seems more stable than Alpha 3.

---

### Post by meborc on 2009-08-15
i'm still having trouble with my kubuntu karmic install... the wireless areas are identified and properly shown in the NM applet, but nothing happens when i try to connect :(

the wired connection works fine, but no go with the wireless

i'll keep on trying to get an ugly fix ;)

---

### Post by martijntje on 2009-08-15
I am also having trouble getting wireless to work.

The strange thing is, it *did* work with the LiveCD. Hardware Drivers does detect the card and shows an option to 'Activate' it, but this does not really do anything (it exits really quickly)

---

### Post by Luca_turicci on 2009-08-15
I was having that problem, try installing from Synaptyc, bcm43xx-fwcutter, that's what i did.

---

### Post by Slug71 on 2009-08-16
> **Luca_turicci said:**
> Yeah, I found that annoying too. Plus it always asks me for permission to mount the windows partition at start up.

And yeah, the wireless drivers are not installed by default. That kinda sucks. But i'm not having anymore trouble with the Gnome Daemon, or anything, no more messages of apps crashing. that's great, this Alpha seems more stable than Alpha 3.

Yep, im getting the Windows partition thing too.

---

### Post by Slug71 on 2009-08-16
> **meborc said:**
> i'm still having trouble with my kubuntu karmic install... the wireless areas are identified and properly shown in the NM applet, but nothing happens when i try to connect :(

the wired connection works fine, but no go with the wireless

i'll keep on trying to get an ugly fix ;)

Have you got DKMS and bcmwl-xx-xx, installed?

---

### Post by meborc on 2009-08-16
> **Slug71 said:**
> Have you got DKMS and bcmwl-xx-xx, installed?

yep, the dkms was installed out of the box... the hardware drivers thing was empty... so i did an upgrade and restart... and the broadcom drivers showed up in the menu... i installed them, the wireless networks were identified and shown in the NM applet, but there is no way i am able to connect to any of them... 

i'll try to purge/install bcmwl again

---

### Post by martijntje on 2009-08-16
I wanted to see what exactly ubuntu does when you install the bcmwl driver so I downloaded the bcmwl-kernel-source package and went to compile it.

However, the Makefile doesn't have any targets. Anyone know what's this about?

EDIT: Managed to get it working, here's what I did:

Remove the old b43-fwcutter stuff

```
sudo aptitude remove --purge b43-fwcutter
```

Install and build dkms module

```
sudo aptitude install dkms bcmwl-kernel-source
sudo dkms add -m bcmwl -v 5.10.91.9+bdcom
sudo dkms build -m bcmwl -v 5.10.91.9+bdcom
sudo dkms install -m bcmwl -v 5.10.91.9+bdcom
```

Now reboot, and wireless should be working

---

### Post by fjosh on 2009-08-16
Which chipset are you running?

---

### Post by martijntje on 2009-08-16
> **fjosh said:**
> Which chipset are you running?
Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

---

### Post by meborc on 2009-08-17
with todays updates a kernel update was included, this built the dkms module bcmwl again... i was very excited until i tried to connect to a wireless point :)

seems to me the problem in kubuntu is the network manager applet... when i removed it and installed wicd, i was able to connect to my home wireless... so it seems the drivers are installed correctly

---

### Post by geordish on 2009-08-18
> **meborc said:**
> with todays updates a kernel update was included, this built the dkms module bcmwl again... i was very excited until i tried to connect to a wireless point :)

seems to me the problem in kubuntu is the network manager applet... when i removed it and installed wicd, i was able to connect to my home wireless... so it seems the drivers are installed correctly

Same issue here. NetworkManager just doesn't see my wireless interface. Switching to wicd works just fine. Looks like a bug in Network Manager.

---

### Post by geordish on 2009-08-18
> **geordish said:**
> Same issue here. NetworkManager just doesn't see my wireless interface. Switching to wicd works just fine. Looks like a bug in Network Manager.

Further to this, I get this in my syslog:

```

Aug 18 19:37:12 mercury NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/eth1, iface: eth1)
Aug 18 19:37:12 mercury NetworkManager: <info>  (eth1): driver supports SSID scans (scan_capa 0x01).
Aug 18 19:37:12 mercury NetworkManager: <info>  (eth1): new 802.11 WiFi device (driver: 'wl')
Aug 18 19:37:12 mercury NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Aug 18 19:37:12 mercury NetworkManager: <info>  (eth1): now managed
Aug 18 19:37:12 mercury NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
Aug 18 19:37:12 mercury NetworkManager: <info>  (eth1): preparing device.
Aug 18 19:37:12 mercury NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Aug 18 19:37:12 mercury NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess#012
Aug 18 19:37:12 mercury NetworkManager: <info>  (eth1): supplicant manager state:  down -> idle
Aug 18 19:37:18 mercury NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/eth1, iface: eth1)
Aug 18 19:39:44 mercury NetworkManager: <info>  (eth1): now unmanaged
Aug 18 19:39:44 mercury NetworkManager: <info>  (eth1): device state change: 2 -> 1 (reason 36)
Aug 18 19:39:44 mercury NetworkManager: <info>  (eth1): cleaning up...
Aug 18 19:39:44 mercury NetworkManager: <info>  (eth1): taking down device.
Aug 18 19:40:44 mercury NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/eth1, iface: eth1)
Aug 18 19:40:44 mercury NetworkManager: <info>  (eth1): driver supports SSID scans (scan_capa 0x01).
Aug 18 19:40:44 mercury NetworkManager: <info>  (eth1): new 802.11 WiFi device (driver: 'wl')
Aug 18 19:40:44 mercury NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Aug 18 19:40:44 mercury NetworkManager: <info>  (eth1): now managed
Aug 18 19:40:44 mercury NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
Aug 18 19:40:44 mercury NetworkManager: <info>  (eth1): preparing device.
Aug 18 19:40:44 mercury NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Aug 18 19:40:44 mercury NetworkManager: <info>  (eth1): supplicant manager state:  down -> idle


```

---

### Post by prunch1910 on 2009-08-20
Hi,
I have the alpha 4 and a broadcom wifi card. It worked on the live cd but not on the install, nor did I have the option of a restricted driver for it or my ati graphics card. I edited /etc/modprobe.d/blacklist.conf and blacklisted ssb. on restart immediately after that the hardware drivers window popped up and offered two broadcom drivers and the ati one too. Hope this helps. Since then the wifi has worked perfectly, connecting to my home network and using the internet without drama.

---

### Post by MikeCamel on 2009-09-01
Folks -

Buried up a few posts back, now, is the suggestion that you try 'rfkill unblock all'.

This worked a treat for me, and all of my problems were immediately solved.  Worth a try.

-Mike.

---

### Post by honda on 2009-09-06
So I just installed alpha 5 on my compaq 701eo netbook. Wlan worked fine using live usb, but not after installing. Seems that there are different ways this can fail, for me the hardware driver did find the broadcom STA driver, but the activation quit after a second or so without error and without actually activating anything. Tried the various tricks mentioned here, including blacklisting ssd, but nothing worked. dkms status said the module was installed. So I tried this: 

sudo dkms remove -m bcmwl -v 5.10.91.9+bdcom --all
sudo dkms add -m bcmwl -v 5.10.91.9+bdcom 
sudo dkms build -m bcmwl -v 5.10.91.9+bdcom 
sudo dkms install -m bcmwl -v 5.10.91.9+bdcom 

and then it started working and has since.

(ie. I removed the driver and rebuild it and reinstalled it)

(my wlan chip is a BCM4312 chip)

---

### Post by jlacroix on 2009-09-17
> **honda said:**
> So I just installed alpha 5 on my compaq 701eo netbook. Wlan worked fine using live usb, but not after installing. Seems that there are different ways this can fail, for me the hardware driver did find the broadcom STA driver, but the activation quit after a second or so without error and without actually activating anything. Tried the various tricks mentioned here, including blacklisting ssd, but nothing worked. dkms status said the module was installed. So I tried this: 

sudo dkms remove -m bcmwl -v 5.10.91.9+bdcom --all
sudo dkms add -m bcmwl -v 5.10.91.9+bdcom 
sudo dkms build -m bcmwl -v 5.10.91.9+bdcom 
sudo dkms install -m bcmwl -v 5.10.91.9+bdcom 

and then it started working and has since.

(ie. I removed the driver and rebuild it and reinstalled it)

(my wlan chip is a BCM4312 chip)

I have a wlan chip as well, and I tried your instructions, but no go.

```
jeremy@jeremy-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

```
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```

---

### Post by novafluxx on 2009-09-18
:(> **jlacroix said:**
> I have a wlan chip as well, and I tried your instructions, but no go.
```
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```

Same thing I have excactly what I have, (rev 01) and everything...

I installed Alpha 6 last night, and it didn't work right, but I restarted and it booted and offered me fwcutter as a driver but wouldn't install just hung.

---

### Post by patasenko on 2009-09-18
I too have Broadcom wireless, but I managed to solve it. There were no drivers found at Hardware drivers, then I just installed bcmwl from synaptic.

---

### Post by Slug71 on 2009-09-18
Just install DKMS and bcmwl drivers from Synaptic.

Hopefully this is installed by default with Alpha 6 now. Havent tried a fresh install yet since Alpha 3.

---

### Post by jlacroix on 2009-09-18
> **Slug71 said:**
> Just install DKMS and bcmwl drivers from Synaptic.

Hopefully this is installed by default with Alpha 6 now. Havent tried a fresh install yet since Alpha 3.

I tried that and it didn't work either. The problem happened after the laptop froze in the middle of installing it the first time. I reinstalled Kubuntu completely and that is what it took to fix it.

---

### Post by novafluxx on 2009-09-18
I'm burning a CDRW of Alpha 6 right now. I'll check in about an hour if its working.

How can I install it from synaptic if I don't have internet access????:confused:

---

### Post by Slug71 on 2009-09-19
> **novafluxx said:**
> I'm burning a CDRW of Alpha 6 right now. I'll check in about an hour if its working.

How can I install it from synaptic if I don't have internet access????:confused:

Wired connection?

---

