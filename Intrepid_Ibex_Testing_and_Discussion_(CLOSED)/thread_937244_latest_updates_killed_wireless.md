---
title: "latest updates killed wireless"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ELD on 2008-10-03
Has anyone elses wireless stopped working with latest updates?

---

### Post by Lorenz on 2008-10-03
No, acutally it works finally fine here (ipw3945). I had the problem, that I always had to enter the passkey when I restarted, but keyring manager seems to work now...might also be because I added the lauchpad ppa network-manager to my software sources.

---

### Post by ELD on 2008-10-03
I don't even have a password on mine and it still won't connect, netgear pci.

---

### Post by FuturePilot on 2008-10-03
> **ELD said:**
> I don't even have a password on mine and it still won't connect, netgear pci.

Is it an atheros chipset?

---

### Post by ELD on 2008-10-03
> **FuturePilot said:**
> Is it an atheros chipset?

Yeah i'm pretty sure it is, it finds networks, but won't connect, passworded or not.

---

### Post by xeriouxi on 2008-10-03
I'm having issues with this, too!

It finds the SSID etc. fine but it stalls when it's requesting something from the router (I can't remember the exact message) and then it disconnects entirely. I'm using an F5D7050 via ndiswrapper. Ubuntu is out of action at the moment for me. =(

---

### Post by bubba_169 on 2008-10-03
Im having the same problem with an intel 2200bg wireless card. One workaround is to keep clicking the network name every 10 seconds after it starts requesting an address. It might be the most efficient way but it seems to work and should connect eventually... 

PS You will need to do this every time you reboot!

---

### Post by FuturePilot on 2008-10-03
> **ELD said:**
> Yeah i'm pretty sure it is, it finds networks, but won't connect, passworded or not.

Yes look here
[http://ubuntuforums.org/showpost.php?p=5898116&postcount=12]("http://ubuntuforums.org/showpost.php?p=5898116&postcount=12")
This will only work if you have an atheros based card.

---

### Post by ELD on 2008-10-07
> **FuturePilot said:**
> Yes look here
[http://ubuntuforums.org/showpost.php?p=5898116&postcount=12]("http://ubuntuforums.org/showpost.php?p=5898116&postcount=12")
This will only work if you have an atheros based card.

Edit > Tried it and it did nothing for me.

---

### Post by drumsticks on 2008-10-07
Had the same problem with the iwlagn driver.

The problem occurred when I upgraded:
network-manager (0.7~~svn20080928t225540+eni0-0ubuntu2) to 0.7~~svn20081004t225044-0ubuntu1
network-manager-gnome (0.7~~svn20080927t101113-0ubuntu1) to 0.7~~svn20081005t082522-0ubuntu1

I reverted to the older version and it worked again.

---

### Post by dunbrokin on 2008-10-07
Yep, I have the same problem on my PCMIA card....it seems widespread...my card will not even detect my wireless router....it used to do so in Hardy.

---

### Post by ELD on 2008-10-07
Seems we have a pretty big problem, the amount of people complaining wireless is borked, is it the new network manager updates or driver problems?

I hope this is fixed for the RC (well should be!). I am going to have to do a clean install of Hardy :(

---

### Post by Masoris on 2008-10-07
I have a similar problem. My USB wireless lan card works, but very unstable. It is randomly disconnected very frequently, and gnome network manager sometimes crash when I trying to connect.

So I'm use normal wired connection now, I'm waiting to be fixed this problem.

---

### Post by fastcars4 on 2008-10-07
My wireless appears to be connecting, I even get an ip address.  The problem is I cannot ping anything on the network or get to the internet.  Any else having the same problems with the new updates?

---

### Post by pytheas22 on 2008-10-07
Those of you having this problem should first try connecting with [wicd]("http://wicd.sourceforge.net").  If wicd works, then Network Manager was probably the root of the problem, and you should file a bug report appropriately (installing wicd requires you to uninstall NM; if you want NM back, type 'sudo apt-get install network-manager-gnome' or 'sudo apt-get install network-manager-kde').

If wicd doesn't help, you should figure out which chipset your wireless card has--unless everyone in this thread has the same kind of chipset, don't assume that the behavior you're experiencing represents a generic wireless problem in Intrepid.  Chances are that it's caused by distinct problems in various wireless drivers that will need to be resolved individually.

If you don't know which chipset you have, take a look [here]("http://burnthesorbonne.com/?page_id=20").  The output of the command 'lshw -C Network' may also tell you; for example, here is the output for my card, where it tells me that I have an Atheros chipset using the ath_pci (aka madwifi) driver:
```

  *-network:0             
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: **Atheros** Communications Inc.
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: wifi0
       version: 01
       serial: 00:19:e0:67:8a:f1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes **driver=ath_pci** latency=168 maxlatency=28 mingnt=10 **module=ath_pci** multicast=yes wireless=IEEE 802.11g
```

After you've figured out which chipset you have and which driver you're using and have determined that you can't connect either in wicd or Network Manager, you should google around to see if there are any bug reports for your issue on Intrepid.  Chances are that there will be.   But if not, please file bug reports so that the issue can be fixed before the stable release of Intrepid.

---

### Post by fastcars4 on 2008-10-08
I installed wicd and I can now connect with the wireless.

Thanks for the help.

---

### Post by davidyu on 2008-10-08
To my thinkpad T60, 2.6.27-6 kills my wireless. 
I found it convert my wireless key to wrong chars.
It's bug, right.

---

### Post by pytheas22 on 2008-10-08
> To my thinkpad T60, 2.6.27-6 kills my wireless.
I found it convert my wireless key to wrong chars.
It's bug, right.

If it works under all other kernels but not 2.6.27-6, then it's probably a bug, yes.  Which wireless driver do you use (ath_pci, ath9k, iwl4965, iwl3945, iwlagn, etc...)?  With that information you can figure out whether the problem has been reported or not.

---

### Post by zoomy942 on 2008-10-08
with my iwl4965, it connects but its dreafully slow and randomly stops transferring info to my router.

havent tried wicd yet

---

### Post by crazypenguin2008 on 2008-10-08
my linksys usb card with RAlink chipset connected fine untill i updated yesterday(10/7/2008) now i cant connect to a wireless network and there is no option to configure/create one. dredfully disapointing.

---

### Post by anil_robo on 2008-10-08
I had a DLINK DFE 530 TX+ NIC (not wireless) that also stopped working after the last update. Really distressed because I had to get another computer to keep my hosted websites working.

---

### Post by hdhrnova on 2008-10-08
2.6.27-6 killed my wifi Broadcom Corporation BCM4312 802.11a/b/g (rev 02)

wpa keys are corrupt too.

---

### Post by ELD on 2008-10-09
Well my wireless has started working on the only change i did was detailed in this post -> [http://ubuntuforums.org/showpost.php?p=5898116&postcount=12](http://ubuntuforums.org/showpost.php?p=5898116&postcount=12)

Didn't work till the 2nd reboot though wierdly.

---

### Post by chronographer on 2008-10-09
My ralink card has stopped working too. see here: [http://ubuntuforums.org/showthread.php?t=934055&highlight=rt73]("http://ubuntuforums.org/showthread.php?t=934055&highlight=rt73")

and here: [http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=8&t=4993&p=30716#p30716]("http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=8&t=4993&p=30716#p30716")

So. built in drivers don't work, and I can't compile my own drivers (as I usually do)...

Anyone with working rt73, please post to the first link and let me know as I would love to know that it is a prob with my setup, and not Ubuntu!

---

### Post by colinpat on 2008-10-10
I can only get WAN to work by booting with kernel 2.6.24-19  works great.
Any of the 2.6.27 kernels don't work
Colin

---

### Post by colinpat on 2008-10-10
I can only get WAN to work by booting with kernel 2.6.24-19

---

### Post by hdhrnova on 2008-10-11
> **hdhrnova said:**
> 2.6.27-6 killed my wifi Broadcom Corporation BCM4312 802.11a/b/g (rev 02)

wpa keys are corrupt too.


2.6.27-7 update got wireless going again.  However it was unstable after a few minutes. Finally found this thread and blacklisted b43 driver and now using b44. Seems to be stable.  Can we just get rid of b43?? Interpid has both b43 and b44.

This is the thread that I used to fix my stability problem.
[http://ubuntuforums.org/showthread.php?p=5922478](http://ubuntuforums.org/showthread.php?p=5922478)



I also had another machine which as also having a conflict.  That had an atheros chipset.  The conflict was with ath_pci vs ath_5k.  Both were being loaded. I had to blacklist ath_pci and then it was better.

---

### Post by colinpat on 2008-10-11
I have found that iwl4965 works fine.
iwlagn says connected with ip address but can't ping anything.
I have PRO/Wireless 4965 AG or AGN Network Connection
How can you put iwl4965 in kernel 2.6.27-xx

---

### Post by techdude3177 on 2008-10-11
i got the iwl3945 driver for my intel wlan card and everything seems to be working great, i am even able to pick up wireless signals that i couldnt pick up before

---

### Post by rfmug on 2008-10-22
Yep - I have an Atheros AR2413 in an Acer 3682 laptop that stopped working around that time.

---

