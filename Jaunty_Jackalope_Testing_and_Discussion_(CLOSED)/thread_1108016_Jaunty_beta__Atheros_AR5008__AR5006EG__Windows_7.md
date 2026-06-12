---
title: "Jaunty beta / Atheros AR5008 / AR5006EG / Windows 7"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by -::Bas::- on 2009-03-27
Ok, strange things are happening here.

I've got an MSI Wind laptop, which runs the beta of Jaunty with Windows 7 in a dual boot.
I tested this with two wifi cards, Atheros AR5006EG and Atheros AR5008.

The thing is that in Windows the wifi works perfectly, no problems connecting. In Ubuntu however, it's intermittent: 2 out of 3 boots the wireless cannot connect to my router (WPA security). After a reinstall of the beta today, i couldn't get my wifi working, not after 5/6 boots (AR5008). It hangs on that it cannot authenticicate with my router, that' what i read in the logs.
With the networkmanager I can see all the wireless networks in the neighbourhood. iwconfig tells me that my wifi is in range, but not connected.
I hoped their was some fix for it, wanted to update, so I plugged it with a cable into my router, and badabadabing, I had two network connections, one wired, one wireless.

So the wireless is back, but it's really confusing as to what made it come back.

---

### Post by grantk86 on 2009-03-27
I'm also having problems with my Atheros AR5006EG (Asus eeePC 1000HA) after updating from Jaunty Alpha 6 to Beta this morning.  My wireless has worked fine in Alpha 6 for the past two weeks, but today after upgrading it seems to randomly cease functioning.

I can connect to all of my networks at home and school, and the network icon always says that it is connected, but most of the time it seems to hang when transfering.  When doing a speed test in Vancouver, I get a high ping (~120 ms) and very slow transfer rates for my connection (~1 Mbps down, 0.15 Mbps up) from the AR5006EG.  When I do the same test on my older laptop running Intrepid (Atheros AR5001X+), I consistently get 10 Mbps up and down at a ping of only 5 ms.  I tried enabling the proprietary Madwifi driver, but then my wireless card was not even detected by Network Manager.

---

### Post by grantk86 on 2009-03-27
My syslog outputs the following:
```
Mar 27 17:04:14 ubuntu kernel: [ 2121.393564] ath5k phy0: unsupported jumbo
```
over and over while on wireless.  Wireless is completely unusable now... I have to be plugged in.  Anyone else having this problem?

---

### Post by grantk86 on 2009-03-27
New bug report filed here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350004](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350004)

---

### Post by Gnurou on 2009-03-28
Same problem here with Macbook/AR5008. I can get a list of networks, but no way to associate to any of them. As far as I know, it was not working with the alpha version neither.

---

### Post by mykrob on 2009-03-28
have you guys tried the madwifi driver?

That's what I had to use in Intrepid to get a stable wifi

the most recent revision is here:

[http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3942-20090205.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3942-20090205.tar.gz)

---

### Post by Gnurou on 2009-03-29
Right, I was using it a while ago, shame on me for not trying that...

Using the madwifi drivers wifi works perfectly. The only problem is that the encryption key seems not to be correctly set by the network manager plasmoid (kubuntu here), and I have to run iwconfig manually to fix it and get a working connection. (edit: entering an hex key instead of a passphrase fixes that) But apart from that everything is ok - I'm writing this message from my wireless connection.

Still, it is sad that atheros chips do not work out of the box. I thought madwifi was included in the latest kernels, but from the module names it seems it is not. The kernel module used by default was ath9k, while the working madwifi module is ath_pci.

Anyway, thanks a lot for pointing this! It truly helped.

---

### Post by wally the duck on 2009-04-06
Compag CQ60 210US (Atheros wireless). No wireless.
I have some more things to try (after about two days already) but one issue is that the wireless seems to come up 'off' from bootup even I've set the BIOS to enable it... and then nothing in the linux drivers seems capable of turning it on.

Had one brief flicker of success after a madwifi update... but as soon as I disconnected the card went off and there it stayed.

---

### Post by wally the duck on 2009-04-06
Update the previous post
Compaq CQ 210US Ubuntu Jaunta beta with 2-6-28-11 kernel, atheros wireless.
New install, shut down bluetooth process.

Wireless now works perfectly with the default driver (except blue light stays orange).

---

### Post by ebug on 2009-04-10
hey wally,

Could you please give us the details how you did it. Thanks.
i got G60-120us. ubuntu actualy reconizes it but i need to press the wireless button beside the power button and keeping it pressed all the time to stay connected. once i release the butoon, it disconnects. Now I am thinking, why did hp made this kind of approach when a good old manual switch is perfectly ok. My dv2000 laptop works well with the manual switch.

Anyway, i hope you reply soon, coz im already short of temper with this hp laptop.

thanks again!

---

### Post by wally the duck on 2009-04-20
Compaq CQ60 210 US; atheros

With the Jaunty (beta) I did 2 things: I set the bios to enable network on startup and, in Jaunty, I turned off the bluetooth services (set them to not autostart in System...Administration...Services).

I loaded no special drivers and did not change the default wireless driver from what Jaunty loaded.

After that, wireless worked perfectly (except no blue light). I used it for about a week and then sent the laptop back to its owner for whom I had installed Ubuntu.

---

