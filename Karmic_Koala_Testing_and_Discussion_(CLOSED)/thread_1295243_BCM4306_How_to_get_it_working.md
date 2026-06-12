---
title: "BCM4306: How to get it working??"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by crys on 2009-10-19
Hi,

I have a Broadcom BCM4306 wireless card in my notebook. The big question is how to get it working, especially, which driver is responsible? 
The bcmwl driver only seems to support BCM4311, BCM4312, BCM4321, BCM4322 (according to the package info of bcmwl) and 'modprobe wl' doesn't bring the interface up.
The b43 driver is blacklisted, and modprobing it results in 
'ADDRCONF(NETDEV_UP): wlan1: link is not ready'. Perhaps that's the reason why it's blacklisted?!
Any other suggestions? Perhaps ndiswrapper?

I remember it once worked with an earlier Ubuntu version. But with current Karmic -> no luck so far.

Thanks for any idea.
Chris

---

### Post by mikedep333 on 2009-10-19
It's an old wireless card. I'm sure it's supported. What does the hardware drivers (system > administration > hardware drivers) offer?

---

### Post by xebian on 2009-10-19
> **crys said:**
> Hi,

I have a Broadcom BCM4306 wireless card in my notebook. The big question is how to get it working, especially, which driver is responsible? 
The bcmwl driver only seems to support BCM4311, BCM4312, BCM4321, BCM4322 (according to the package info of bcmwl) and 'modprobe wl' doesn't bring the interface up.
The b43 driver is blacklisted, and modprobing it results in 
'ADDRCONF(NETDEV_UP): wlan1: link is not ready'. Perhaps that's the reason why it's blacklisted?!
Any other suggestions? Perhaps ndiswrapper?

I remember it once worked with an earlier Ubuntu version. But with current Karmic -> no luck so far.

Thanks for any idea.
Chris

Install the b43-fwcutter

---

### Post by crys on 2009-10-19
system > administration > hardware drivers offers nothing. I tried that before, the list is completely empty.
b43-fwcutter is already installed and along with it the firmware which gets loaded when I modprobe b43.
dmesg tells me:

```

[  764.814466] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[  764.962732] phy0: Selected rate control algorithm 'minstrel'
[  764.963757] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[  764.994360] udev: renamed network interface wlan0 to wlan1
[  765.024319] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  765.118212] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[  765.138205] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[  765.166806] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[  765.296304] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  765.357109] Registered led device: b43-phy0::tx
[  765.357163] Registered led device: b43-phy0::rx
[  765.357216] Registered led device: b43-phy0::radio
[  765.358172] ADDRCONF(NETDEV_UP): wlan1: link is not ready

```

The last line is what bothers me.

---

### Post by novafluxx on 2009-10-19
There is another BCM package for Broadcom wireless devices in the repos, and on the LiveCD. Thats what I had to use to get my wireless working. In previous versions it was always offered to me and listed under Hardware Driver, but in 9.10 it isn't and I have to do this manually.


I'm not sure what the name of the package is at this time, but if you put your CD in, and make sure you have the CD as a repo source, refresh the list, search synaptic for "bcm" and there should be 2 in there, the fwcutter package and another one...

Give this a shot and lemme know what happens!

---

### Post by mikedep333 on 2009-10-19
I think the "link is not ready" means that it isn't connected to a wireless network. Isn't the wireless card showing up under network-manager? What happens when you run:
```
sudo iwlist wlan0 scanning
```

---

### Post by mikedep333 on 2009-10-19
Actually, are you sure b43 is blacklisted? All I see is:
```
# replaced by b43 and ssb.
blacklist bcm43xx
```

---

### Post by crys on 2009-10-19
Thanks for the hints.
After deinstalling the bcmwl package, the blacklist entries for b43 and ssb disappeared and both now get loaded when the system starts up.
And it even now shows up in the Hardware Drivers dialog.

However, b43 is still not operational since the 'link not ready' issue remains.
As a consequence, 'iwlist wlan1 scanning' results in 'No scan results' and nm-applet also doesn't find anything, although there is plenty of wireless networks here.

The only other bcm related package is 'bcm5700-source' which seems to be for a different broadcom chipset.

---

### Post by novafluxx on 2009-10-19
> **crys said:**
> Thanks for the hints.
After deinstalling the bcmwl package, the blacklist entries for b43 and ssb disappeared and both now get loaded when the system starts up.
And it even now shows up in the Hardware Drivers dialog.

However, b43 is still not operational since the 'link not ready' issue remains.
As a consequence, 'iwlist wlan1 scanning' results in 'No scan results' and nm-applet also doesn't find anything, although there is plenty of wireless networks here.

The only other bcm related package is 'bcm5700-source' which seems to be for a different broadcom chipset.

bcmwl didn't work for you? Did you reboot after installing it?

---

### Post by crys on 2009-10-19
No, bcmwl didn't work. I modprobed it but it didn't detect my card. Regarding to the package info, it isn't supposed to work with bcm4306. See my first post.

---

### Post by mikedep333 on 2009-10-19
> **crys said:**
> Thanks for the hints.
After deinstalling the bcmwl package, the blacklist entries for b43 and ssb disappeared and both now get loaded when the system starts up.
And it even now shows up in the Hardware Drivers dialog.

However, b43 is still not operational since the 'link not ready' issue remains.
As a consequence, 'iwlist wlan1 scanning' results in 'No scan results' and nm-applet also doesn't find anything, although there is plenty of wireless networks here.

The only other bcm related package is 'bcm5700-source' which seems to be for a different broadcom chipset.

Crys, until you tell it to connect to a wireless network, the 'link not ready' message is the intended functionality for a functional wireless card. It is the same as having an unplugged wired ethernet adapter. The iwlist output suggests your card is working, as far as linux can tell. If nm-applet at least mentions wireless networks, your card is working as far as linux can tell.

Right now I would bet there is an issue with the antenna. Did you press a wi-fi antenna button on your laptop? Or is there a regular enable/disable wi-fi button on your laptop?

---

### Post by houstonbofh on 2009-10-19
I am having the same issue on Jaunty.  The card worked before, but performance has been degrading with upgrades, and it would set speeds at 1mb, and frequently disconnect.  Now there is nothing in network manager.  And if I scan from the terminal;

lee@portable:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.


This may not just be a Karmic issue.

---

### Post by AKviking on 2009-10-21
> **crys said:**
> Hi,

I have a Broadcom BCM4306 wireless card in my notebook. The big question is how to get it working, especially, which driver is responsible? 
The bcmwl driver only seems to support BCM4311, BCM4312, BCM4321, BCM4322 (according to the package info of bcmwl) and 'modprobe wl' doesn't bring the interface up.
The b43 driver is blacklisted, and modprobing it results in 
'ADDRCONF(NETDEV_UP): wlan1: link is not ready'. Perhaps that's the reason why it's blacklisted?!
Any other suggestions? Perhaps ndiswrapper?

I remember it once worked with an earlier Ubuntu version. But with current Karmic -> no luck so far.

Thanks for any idea.
Chris

I'm not sure if this will work for you or not.  It got mine going a while back.  I'm running on Intrepid, so I'm not sure if there'll be a problem with this on Karmic Koala.  Just my 2 cents.  
[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=1240500[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1240500")

---

### Post by nanog on 2009-10-21
I fixed this bug by buying an intel wireless card for 15 bucks.

---

### Post by forumache on 2009-10-22
> **nanog said:**
> I fixed this bug by buying an intel wireless card for 15 bucks.

You worked around this bug. The bug is still there. You just don't know about it. The fix is yet to come. Please don't mark this thread solved ;)

---

