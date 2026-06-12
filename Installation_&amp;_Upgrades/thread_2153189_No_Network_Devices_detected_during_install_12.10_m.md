---
title: "No Network Devices detected during install 12.10 mini.iso"
date: 2013-06-10
forum: Installation &amp; Upgrades
---

### Post by fredfillis on 2013-06-10
Currently have Ubuntu 12.10 installed on [Shuttle XS35GSV3]("http://http://global.shuttle.com/news/productsSpec?productId=1587") and been having some problems with AMD drivers and XBMC.

Was suggested to me that I try some beta drivers with a 12.10 minimal install. So, I downloaded the 64 bit version of 12.10 from [http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-amd64/current/images/netboot/mini.iso)

I burned the ISO to a CD and once into the install process the installer indicates that no network devices were found. Tried again from a USB drive, same result. Tried the 32 bit version with the same result.

Have a wired connection.

Any ideas why network devices would not be detected? What do I need to do to get the minimal install to work?

---

### Post by Bucky Ball on 2013-06-10
*Thread moved to **Installation & Upgrades**.*

You probably need to bone up on the mini.iso install. It is not like a desktop, it doesn't just install and that's that. You need to tell the mini install what to drag in when you're installing it. If you didn't do that, you pretty much have the Ubuntu base kernel and not much else. You need to install Network Manager and anything else you might need manually. 

When you are installing, you should have gotten the option to connect to internet then. You need to do this else you can't install any packages as the mini install is just the base kernel. 

Generally, you need to make a list of what you are going to need then type that in at that part of the install (you need to type 'cli' at the cursor to get there). Anyway, look here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

There's plenty of info on the interwebs about this ...

PS: Unless you installed one manually when you were installing the mini you don't even have a desktop environment I suspect, just a cli. I'd probably suggest getting familiar with the mini.iso install, prepare, then reinstall and follow the steps carefully (you need to tell it how to get online in the early stages). Good luck. It's worth the effort I reckon as mini installs are super fast.

PPS: You haven't tried to fix the problems with 12.10 and Xbmc, etc? You might have the same issue with any 12.10 install. Tried an LTS, 12.04 for instance?

---

### Post by fredfillis on 2013-06-11
Thanks for the reply Bucky Ball.

> **Bucky Ball said:**
> ... You need to install Network Manager and anything else you might need manually ... When you are installing, you should have gotten the option to connect to internet then. 
But the network devices are not found and therefore I cannot connect to the internet to download / install any other bits and pieces. I have a bit of a laundry list of other bits and pieces to install per this post over at the XBMC forum [http://forum.xbmc.org/showthread.php?tid=116996&pid=960883#pid960883](http://forum.xbmc.org/showthread.php?tid=116996&pid=960883#pid960883)

> **Bucky Ball said:**
> PPS: You haven't tried to fix the problems with 12.10 and Xbmc, etc? You might have the same issue with any 12.10 install. Tried an LTS, 12.04 for instance?

Yep, hot on the trail of a fix. Trying the mini with a beta AMD driver as recommended by XBMC gurus.:)

---

### Post by fredfillis on 2013-06-13
I think that 12.10 minimal is missing the jme driver. Not sure how to make this work.

---

### Post by Bucky Ball on 2013-06-13
Whatever that is, you would need to install it manually unless it is part of the Ubuntu base kernel. I repeat, any software or apps you want to use you are going to need to install manually. I would start with:

```
sudo apt-get install xfce4 synaptics
```

That will install a desktop environment and a package manager. Unless you want to do everything from a terminal that is. 

If you have a wired connection, all good. You can set wireless up later. That is NOT going to work out of the box with a minimal install in every situation. Try:

```
sudo apt-get install network-manager
```

You can get your wireless going with that, probably. A minimal requires quite a bit of research and preparation. It is not really something to do on a whim unless you are ready for a steep learning curve or already know what you're doing. Good luck with it.

---

### Post by fredfillis on 2013-06-14
After banging my head against a wall for many hours over the past few days I conclude that a minimal install is not going to happen. 

No matter what I try, I cannot get the installer to "detect" my network card and therefore it is not possible to download any packages for installation. I've seen this problem reported occasionally by others but they were never really given any help with solutions.

A one liner to just "Choose Command-line-install and use xbmc for username" made it all seem so simple.

---

### Post by Bucky Ball on 2013-06-14
Might be easier to just install Xbmc if a media server is what you're after. A minimal is not for the faint hearted and sometimes hard to get right. As I say, they can take quite a bit of planning.

Then again, if you 'cli' at the prompt during install you will get a cursor and the option to install whatever you want/need. Have you tried typing there something like:

```
sudo apt-get install xbmc
```

I have no doubt you would need to add more than that, though.

 ;)

---

### Post by fredfillis on 2013-06-14
Thanks for taking the time ...

I actually have a running XBMC setup under 12.10. I have AMD graphics which is apparently problematic under Linux. I have been getting some help over at XBMC forums with a specific audio / video problem where the recommendation was to try a minimal install and a specific beta driver.

So, a "normal" ubuntu install detects my wired network and runs off on it's merry way. A minimal install on the same machine cannot detect my wired connection and because it wants to download packages etc it cannot.That is where I'm stuck.

Your reference to CLI is the fundamental process that I need to follow. I have a laundry list of things I need to instal via the CLI. But no internet means no install.

---

### Post by Bucky Ball on 2013-06-14
Got ya. As I mentioned earlier, during the install there is a section near the beginning where you input your network details and get online before any of the rest happens. You're missing it. You need to enter gateway IP, DNS IPs, subnet mask, network name, etc. If you're not doing that bit that would be the problem. It is one of the first steps from memory, but I haven't done a mini in couple of years.

PS: With that shopping list, try and avoid anything your really don't need. Chucking too much on there (if you intend to install ubuntu-desktop, for instance, just install Ubuntu!) would defeat the purpose of a mini install and increase the possibility of whatever is causing issues getting reinstalled. 

You might want to follow the instructions at the link I provided to the letter and try again from the start.

1/ Boot from the CD;
* After inputting details, including network details, choose 'Manual Package Selection';
* Add your package list I guess, with 'sudo apt-get install ...'

I realise the way I remember was probably the command line install:
2/ Type CLI;
3/ You should get to another prompt where you can input tasksel to select which system profile you want. I've never used this. From memory you are in regular CLI there and as long as you are online you should be able to start installing things.

I have a spare partition and a bit of time so might install the mini later and have a look. Been meaning to do another one (I still sometimes think of that 12 seconds from power on to login screen just as I'm about to drift off to sleep). ;)

PS: Just follow this:

[http://www.maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24](http://www.maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24)

It's all there.

PPS: I generally choose to partition manually and size the partition. The mini iso can just be chucked on a 10Gb partition (probably 5Gb or less in reality but you want some room to expand). Now days I let it install /home as a directory in /, kill all the folders in /home once installed and create symlinks to the folders on my /storage partition instead. Then all installs can use same data.

A morning mouthful, sorry about that. Good luck. ;)

---

### Post by fredfillis on 2013-06-16
Thanks again Bucky Ball, I will have another look at the minimal install as per your suggestions. The link you provided seems to miss out the one step I'm getting hung up on, that is the "detect network devices" or similar. I comes up right before the hosthame screen. It appears to be looking for a network interface or a live connection, Just comes back and says no devices found. There is no opportunity to enter IP addresses etc.

Weekend is over for me so I'll be having a look as time is available.

Cheers!

---

### Post by Bucky Ball on 2013-06-19
Well, I'm typing to you now from my Ubuntu Xfce4 Mini install!

First, make sure you have a cable plugged in that you know is going to get you online. 

When you boot from the disk, choose to install from the options, go through the steps and watch carefully for when the install process attempts to connect to the network. It would be hard to miss if it doesn't connect because the very next screen would ask whether you want to manually input the details (static IP for instance) and just sits there waiting for input so you'd get no further.

Follow your nose until you reach the end of it, pop the disk, reboot (with the cable still in) and you should be greeted with a screen where you can enter what you want to install. I can't find the bit of paper I scrawled my list on but it was something like:

```
sudo apt-get install xfce4 xubuntu-restricted-extras brasero thunderbird firefox gcc apt synaptics filezilla putty gdm update-manager network-manager
```

That's not comprehensive and suits me, probably not you. If I find the bit of paper I'll update the list.

Whether it's of any use, I installed on a spare partition alongside Xubuntu 12.04 LTS and Win7. There's a section of the install where you install grub. Things went a bit strange here and it wouldn't let me install grub, so I didn't, as far as I know. I rebooted back into my regular Xubuntu 12.04, sudo update-grub, Mini on the menu, boot back to the mini install and that's when I put my install list in (above). So I ended up with my original 12.04 regular install controlling grub still. Just thought I'd throw that in ...

---

### Post by fredfillis on 2013-06-22
Nice work Bucky!

I'm still stuck with the mini since I don't get to input any network details. What ISO are you using?

---

### Post by Bucky Ball on 2013-06-22
12.04 LTS Minimal install. Got it pretty rock solid, tweaked and using it now. Only what I want on here, no fat, and it's becoming my main squeeze.

How come you can't input network details? Are you online with a cable? Get install Network Manager or Wicd and put network details in there:

```
sudo apt-get install network-manager
```

Not quite getting what you mean ... you have installed the mini iso and can't get online so can go no further? :-k

PS: Something else really strange happened. My network card was recognised and working right out of the box, but for some reason the /etc/network/interfaces file was missing 'auto wlan'. Added that and fine. The strangest part was that the same happened in my stable install! I can only think this was coincidental and must have happened during an update both installs had and been fixed in the next one (I update often).

If you've got other issues please post a new thread in the appropriate forum if you want and post a link back here as we are heading off-topic. ;)

---

### Post by fredfillis on 2013-06-24
> How come you can't input network details? Are you online with a cable?

No clue. All I do know is that the computer works fine with a wired connection and 2.10 desktop installed. The mini.iso displays the screen below when I try to install.

[https://www.dropbox.com/s/95v2dlcxun3wgtd/20130624_201344.jpg](https://www.dropbox.com/s/95v2dlcxun3wgtd/20130624_201344.jpg)

---

### Post by Bucky Ball on 2013-06-24
Ah, ok. Please run this and post back result:

```
sudo lshw -C network
```

It is strange it is finding no interface during network detection. Try this:

Boot from the install media. When you're at the screen with the install options, etc, hit F6 and you should get some options. Choose 'nomodset' and continue. What happens at the network part (make sure the cable is plugged in from boot)?

---

### Post by sudodus on 2013-06-24
Maybe you can find some valuable tips at this link

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Unmanaged_Wired_Network](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Unmanaged_Wired_Network)

---

### Post by Bucky Ball on 2013-06-24
> **sudodus said:**
> Maybe you can find some valuable tips at this link

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Unmanaged_Wired_Network](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Unmanaged_Wired_Network)

Yep. You could install without network and that should get you to a cli where you can then change the /etc/network/interfaces file as described on that page, presuming it is not correct already and there is some other problem. If that brings up the network, install a desktop environment, synaptics (and whatever else) with 'apt-get' and reboot.

You are sure the cable connection is working fine I guess? You are getting online with the same cable on another install or another machine?

---

### Post by fredfillis on 2013-06-28
Thanks for the tips Bucky and  						 							sudodus, appreciate your taking the time to reply. 

Yep, my wired network connection is fine. Works fine on same machine with full version of Ubuntu 12.10 and I have been through the "full" install multiple times with the same machine ... no worries!

Have been away for a couple of days but will give these ideas a try and report back!

---

### Post by fredfillis on 2013-06-28
> **Bucky Ball said:**
> Ah, ok. Please run this and post back result:

```
sudo lshw -C network
```

This is what I get under the full 12.10
```
xbmc@luckybox:~$ sudo lshw -C network
[sudo] password for xbmc: 
  *-network               
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:02:00.5
       logical name: eth0
       version: 03
       serial: 80:ee:73:43:b4:f9
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.8 duplex=full ip=192.168.54.119 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:46 memory:d0200000-d0203fff ioport:d100(size=128) ioport:d000(size=256)
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 74:e5:43:ed:26:73
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.5.0-34-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 ioport:c000(size=256) memory:d0100000-d0103fff


```

---

### Post by fredfillis on 2013-06-28
> **Bucky Ball said:**
> Boot from the install media. When you're at the screen with the install options, etc, hit F6 and you should get some options. Choose 'nomodset' and continue. What happens at the network part (make sure the cable is plugged in from boot)?

Cannot get F6 to work. You mean the minimal install media? If so, it appears that I am unable to press any key at the right time to make the F6 option available. Not sure what nomodeset would do for me anyway given my problem is with network not video.

> Yep. You could install without network No clue how to do that, since the mininal install always ends up with the same problem

---

### Post by Bucky Ball on 2013-06-28
'nomodset' actually worked for someone with this prob on a minimal on another thread. Don't ask me how but no harm trying.

---

