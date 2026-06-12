---
title: "Wireless-less after upgrading to Hardy"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by E-Cecilia on 2008-10-25
[I]Hi!

Perhaps some of you can help me.. :)

I upgraded from Gutsy and after rebooting I found out that somehow it's whipped the wireless connection away.

This are my specs:
Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

I tried quite a lot of guides I found on the net, but none have worked so far (I wouldn't be posting this otherwise).

Any ideas?[/I]

---

### Post by burnetbj on 2008-10-25
Hi there

Not sure I can help you but was just wondering is it that you have lost your wireless connection lists? SSID 

Or is it your system is no longer displaying the option for wireless....not recognizing your NIC?

---

### Post by E-Cecilia on 2008-10-25
[I]Hmm... 

There's no wireless connection option whatsoever in the Network Manager, but it does recognize my wcard on System/Adm/Hardware Testing.

Any inspiration?[/I]

---

### Post by burnetbj on 2008-10-25
Sorry had to take off for a few 

So when you go up to the right hand corner by date and clock and click on the network manager......do you get a option to enable or disable wireless? if so then I assume its recognizing your wireless nic.

If thats the case I think you need to recreate your wireless connections...like recreate them ....retype SSID name and Encryption key....


I am assuming the new kernal over wrote your connections to a default state of blank

---

### Post by E-Cecilia on 2008-10-25
> **burnetbj said:**
> Sorry had to take off for a few 

So when you go up to the right hand corner by date and clock and click on the network manager......do you get a option to enable or disable wireless? if so then I assume its recognizing your wireless nic.

If thats the case I think you need to recreate your wireless connections...like recreate them ....retype SSID name and Encryption key....


I am assuming the new kernal over wrote your connections to a default state of blank

When I go to the right hand corner and click on the Network Manager, there are two connections listed. This is what it looks like:

---

### Post by burnetbj on 2008-10-25
I am no expert here and could be worng but doesnt look like the OS is finding your nic and or it is failing to assign a driver. Have you tried to connect the laptop using the wired connect and run your update manager .....Almost always this fixed the problem for me in the past 

Hopefully someone with experience will jump in here soon :)

---

### Post by burnetbj on 2008-10-25
Actually I am going to start up my laptop.....I think we should see both ethernet ports.


Wired = etho
Wireless = etho1

sec brb

---

### Post by burnetbj on 2008-10-25
OK in your terminal 

type 

ifconfig


and you should see 

etho 

and 

etho1

if not then i dont think your OS is detecting your NIC

---

### Post by E-Cecilia on 2008-10-25
> **burnetbj said:**
> I am no expert here and could be worng but doesnt look like the OS is finding your nic and or it is failing to assign a driver. Have you tried to connect the laptop using the wired connect and run your update manager .....Almost always this fixed the problem for me in the past 

Hopefully someone with experience will jump in here soon :)

[I]Hopefully... But in the meantime I'm remigrating to Gutsy (because the wireless did work there).

And just in case, do you happen to know someone who had problems running WoW on Wine 1.0?[/I]

---

### Post by E-Cecilia on 2008-10-25
> **burnetbj said:**
> OK in your terminal 

type 

ifconfig


and you should see 

etho 

and 

etho1

if not then i dont think your OS is detecting your NIC

*I see [I]eth0 *and *lo*. That's not good, is it?[/I]

---

### Post by maestrobwh1 on 2008-10-25
If you were using Broadcom, you must have used fwcutter or ndiswrapper to get the card to work.  Do you remember what you did to get it to work?  

The fwcutter method was integrated with the "restricted-manager"  and if you were wired in via a network cable, it would download and install the appropriate firmware.  I favored ndiswrapper because it was more stable for me.  

Until Intrepid, the driver doesn't completely work in the kernel but it identifies the hardware for you at least so you CAN get it working.

First, open a terminal and type
$ lspci

You'll get a bunch of stuff, and look for "Broadcom" if it isn't anywhere, I don't know what to tell you other than to make sure it is not blacklisted in the /etc/modprobe.d/blacklist file.  It may have been blacklisted if you used ndiswrapper, as that was part of the procedure from my memory. (it would something like "blacklist bcm43xx")

If you didn't see it in the output of "lspci" you could try opening a terminal and seeing what happens when you type
$ sudo modprobe bcm43xx
if you get a prompt back with no errors, then it is loaded.
If you get an error that it doesn't exist, try booting with an older kernel and try this again.

At any rate, if you see that it does "exist" then...

See if restricted-manager is installed.

You could open a terminal and just type
$ sudo restricted-manager (I think this is what the package is called) and see if it pops up.  IF it does and IF it lists your Broadcom card, you'll have to wire yourself up to the internet via a cable and follow the directions.  It will fetch and configure the firmware for you.

If not, you'll have to do some research on how to use ndiswrapper with Hardy (and you'll have to blacklist the driver again).  Hardy does something weird with interfering with ndiswrapper, and I have seen instructions and workarounds for it on the net.

Anyway, I know that with Intrepid, there was an attempt to have the Broadcom cards work out of the box... no other Ubuntu distro has had that option as far as I know.

This is why I researched what Atheros mini pci card would fit in my laptop, and I yanked out the Broadcom card two years ago.  You could go for an Airlink101 usb mini adapter.  Works out of the box with Ubuntu, is very small, etc.

---

