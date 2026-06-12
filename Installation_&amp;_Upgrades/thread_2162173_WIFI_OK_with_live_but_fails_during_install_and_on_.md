---
title: "WIFI OK with live but fails during install and on installed Lubuntu 13.04"
date: 2013-07-13
forum: Installation &amp; Upgrades
---

### Post by NuxNik on 2013-07-13
Interesting problem
For the last few weeks, I have been using a DVD to install Lubuntu 13.04 on different partitions.
To test different hardware configurations, and just playing with grub and other software
Installs were fast and clean.
No problems.

In the last couple of days, even though the live install works fine with wireless, the installation process and the installed OS fail on the WIFI,.

The problem is independent of the WIFI dongle used.
The 3 I have, all worked previously, and they work fine on 2 other laptops using Lubuntu 13.04 and Vista
They ALL work on the live install.They can even be interchanged "hot" with the live install runing

But NONE work with the installation process - get a fail to connect message during the install
And NONE work once the installed Lubuntu is booted up.

I was debating if this was more of a wireless problem
But since the live install is NOT a problem, clearly something fails during the installation process

I also tried doing an install without connecting - no joy
Still no connection possible after the new install is booted.

---

### Post by varunendra on 2013-07-13
Please show us the details of the usb dongles you are using -
```
lsusb
```

Run the same command with all three plugged in (simultaneously or consecutively). If running while only one is plugged in at a time, only post the line that changes.

If you also have a pci wireless card, then also -
```
lspci -nnk | grep -iA2 net
```

Once we have the hardware details, we can try to fix the one that is easiest, then the rest if needed (would be easier with a working internet connection).

---

### Post by NuxNik on 2013-07-13
Thanks for responding

In the interval between my original post,I dug out an old PCI  Broadcom -b/g card bcm4306 - [14e4:4320], which has worked for me in the past and responds to b43-legacy drivers .

That one acted like a dead mackerel during the live install.
Currently, on live install these are the results for:


>lsusb< gives:[COLOR=#000000]

Bus 001 Device 005: ID 148f:3072 Ralink Technology, Corp. RT3072 Wireless Adapter
Bus 002 Device 002: ID 0a81:0205 Chesen Electronics Corp. PS/2 Keyboard+Mouse Adapter
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

----------------------------------------

[/COLOR]>[COLOR=#000000][FONT=Ubuntu Mono]lspci -nnk | grep -iA2 net< gives:
[/FONT][/COLOR]
Bus 001 Device 005: ID 148f:3072 Ralink Technology, Corp. RT3072 Wireless Adapter
Bus 002 Device 002: ID 0a81:0205 Chesen Electronics Corp. PS/2 Keyboard+Mouse Adapter
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 12)
    Subsystem: Elitegroup Computer Systems Device [1019:8056]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Kernel driver in use: firewire_ohci
03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 12)
    Subsystem: Elitegroup Computer Systems Device [1019:8056]
    Kernel driver in use: sky2

----------------------------------


[COLOR=#000000][FONT=Ubuntu Mono]and >[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]lspci -vvnn | grep 14e4< (edited) gives:[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]
        *-network
             description: Network controller
             product: BCM4306 802.11b/g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: 6
             bus info: pci@0000:01:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=b43-pci-bridge latency=64
             resources: irq:17 memory:fd800000-fd801fff
   ------------<snip>
 *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:5
       logical name: wlan1
       serial: c8:3a:35:c3:c3:26
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.8.0-19-generic firmware=0.29 ip=192.168.0.26 link=yes multicast=yes wireless=IEEE 802.11bgn

---------------------------------------------

Since the problem is consistent with all my wireless dongles, I am sticking to the one I have been using in the recent past, that has worked till about 4 installs ago...



[COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR]

---

### Post by varunendra on 2013-07-13
> **NuxNik said:**
> In the interval between my original post,I dug out an old PCI  Broadcom -b/g card bcm4306 - [14e4:4320], which has worked for me in the past and responds to b43-legacy drivers .
So do we have a working wireless now?

For the usb one -
> Bus 001 Device 005: ID **[COLOR="#FF0000"]148f:3072[/COLOR]** Ralink Technology, Corp. RT3072 Wireless Adapter

It *should* work with the native rt2800usb driver, and it seems to have been loaded for it. Since you said the problem is same across others as well (assuming they use different chip/drivers), I suspect the problem may be external. However, please try this first after plugging in your usb adapter (and turning off the pci adapter if you can) -

```
sudo modprobe -rfv rt2800usb
sudo modprobe -v rt2800usb nohwcrypt=Y
```

If this doesn't help you connect to wireless networks, please follow the "Wireless Script" link in my signature and post back the report generated by the script suggested in the linked post.

---

### Post by NuxNik on 2013-07-13
> **varunendra said:**
> So do we have a working wireless now?
For the usb one -
It *should* work with the native rt2800usb driver, and it seems to have been loaded for it. Since you said the problem is same across others as well (assuming they use different chip/drivers), I suspect the problem may be external. However, please try this first after plugging in your usb adapter (and turning off the pci adapter if you can) -

```
sudo modprobe -rfv rt2800usb
sudo modprobe -v rt2800usb nohwcrypt=Y
```

If this doesn't help you connect to wireless networks, please follow the "Wireless Script" link in my signature and post back the report generated by the script suggested in the linked post.

Problem is still the same, the lve edition works, the installed verson does not

Sadly the modprobe command failed on a "could not find moddep"
So I have no results for you.

But the irony remains, why the Live edition has no problems recognizing and using the USB dongles, while the hard install, is NOW failing  when it did not before.
As a matter of fact, the dongle I'm using now, actually was inserted after the live edition came up, because I had forgetten to put it back before loading the CD. No problem recognizing it or using it.

I'm thinking something wrong with my DVD, but I actually made a fresh one since, and the problem continues BUT ONLY with a hard install..

---

### Post by NuxNik on 2013-07-13
STOP THE PRESSES...
   This is NOT a NETWORK or DONGLE problem...

Serendipity has struck...

While rebooting from live distro to hard drive install, as I was going to select on the GRUB menu, my dog came in and nudged my arm a couple of times.
I ended up clicking on the 3.8.0.19 kernel option instead of the .26 option
And as soon as the desktop popped up, the wireless dongle connected to the LAN almost immediately.

So I tried it a couple of times.
Kernel 19 works, Kernel 26, dead as a washed up mackerel.
Ditto for recovery modes for the kernels.

Just to be nasty, I pulled out the dongle and put another one in.
The "Disconnected" pop-up popped up, then disappeared to beimmediately replaced by the "Connected" pop-up.

So then I pulled the 2nd dongle, and replaced the 1st one on a USB port in the back of the computer (instead of the front)
Pop-ups, popped up and disappeared, and the network connection is still hot...

So this clearly proves that somewhere in the install process, the  kernel 26 version of the install is bunged up.

One more reason to love my tree-climbing Vizsla..

So the question now is, how do I fix the kernel 26 install problem, that was not a problem a few days ago...

1) How can I upgrade to 3.8.0.26 ?
2) Is this an issue that needs to be reported ?
3) What could have caused this problem in the first place ?

Nonetheless, thanks to the people who were trying to get me up and running by attacking the WIFI problem.

---

### Post by varunendra on 2013-07-14
> **NuxNik said:**
> Sadly the modprobe command failed on a "**[COLOR="#FF0000"]could not find moddep[/COLOR]**"....

That was enough to suggest a broken system, but thanks to your dog to help confirming it.. :P

You should try completely purging the latest kernel, as well as the downloaded (cached) packages, then do a fresh update/upgrade from kernel xx.19. To find out the package names to be purged -
```
dpkg --get-selections | grep 3.8.0.26
```
It should return the exact names of the linux-image and headers that are installed. Purge these with "*sudo apt-get purge <whatever comes up above, separated by spaces>*". For example -
```
sudo apt-get purge **[COLOR="#0000CD"]linux-headers-3.8.9.26[/COLOR] [COLOR="#B22222"]linux-headers-3.8.9.26-generic[/COLOR] [COLOR="#4B0082"]linux-image-3.8.9.26-generic[/COLOR]**
```

Delete the cached packages so they are not installed again (might be broken themselves) and have to be downloaded fresh -
```
sudo apt-get clean
```

Then do a fresh update/upgrade-
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by NuxNik on 2013-07-14
That did it.

I'm just curious to find out when and how the glitch got into the process

My DVD looks OK, and it has worked fine for the last weeks since I started the project.
It's also stored in a sleeve when not in use, so the odds of physical damage are low'

I suspect that very recent upgrades during install may be the problem.

---

### Post by varunendra on 2013-07-14
Glad it worked. :)

> **NuxNik said:**
> I suspect that very recent upgrades during install may be the problem.

Kernel version xx.26 is not part of the live iso, so it was most certainly an update. By the way there is an option on the Live DVD to "Check disk for defects" that can be used to verify its integrity : [https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options](https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options)


**EDIT :** You can edit your **First post** to mark the thread as [SOLVED], currently you have only your last post marked as such : [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Thanks! :)

---

### Post by NuxNik on 2013-07-15
> **varunendra said:**
> Glad it worked. :)
Kernel version xx.26 is not part of the live iso, so it was most certainly an update. By the way there is an option on the Live DVD to "Check disk for defects" that can be used to verify its integrity : [https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options](https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options)

**EDIT :** You can edit your **First post** to mark the thread as [SOLVED], currently you have only your last post marked as such : [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
Thanks! :)


I assumed that the check disk was for the hard drive not the CD/DVD
I will scan it when I have some free time  (Right now, a February 31 priority [IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG].

The fist post flag will be set as soon as this post is ended

Thanks for the help....

---

