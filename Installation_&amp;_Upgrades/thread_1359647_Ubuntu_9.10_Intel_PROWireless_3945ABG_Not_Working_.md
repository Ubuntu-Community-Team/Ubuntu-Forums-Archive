---
title: "Ubuntu 9.10: Intel PRO/Wireless 3945ABG Not Working (Worked on Jaunty)"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by rug2 on 2009-12-19
Hello, 

I've just upgraded to 9.10 (fresh install from scratch). Everything seems fine, except the wireless. I don't know where to begin to fix this issue. From what others are reporting, it seems to be some sort of bug and I've tried many of the methods recommended as a fix, which I believe are just reiterations of fixes to problems that existed on previous versions of ubuntu with this wireless chipset. These failed fix attempts were:

```

sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1

```

and 

```

"install the linux-backports-modules", this didn't fix it either.

```


Turning off the ethernet connection doesn't bring up the wireless either. This thread [http://ubuntuforums.org/showthread.php?t=1322643](http://ubuntuforums.org/showthread.php?t=1322643) recommends opening a bug report. How and who should I report to? 

**_If it helps, here's some info:_**

**relevant line from lspci: **
```
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

**relevant lshw: **
```
root@rug-laptop:/home/rug# !lshw
lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:36:7f:c2
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:28 memory:f0800000-f0800fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:07:08.0
       logical name: eth0
       version: 02
       serial: 00:a0:d1:66:2d:2a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.2 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:f0905000-f0905fff ioport:4000(size=64)

```




Thanks for any help, 
rug

---

### Post by C0p3rn1c on 2009-12-20
Bugs should be reported on the following site:
[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

I think I have the same problem, it's being handled at the following URL: 
[https://bugs.launchpad.net/ubuntu/+source/linux+bug/405656](https://bugs.launchpad.net/ubuntu/+source/linux+bug/405656)

Please register at launchpad and you can help the Ubuntu team by supplying more information about this issue.If your issue differs from mine, make sure there isn't already an existing bug report in the launchpad system before posting a new one. 

Best regards,

c0p3rn1c

---

### Post by darco on 2009-12-20
I have the same network card and when I first installed KK, it also did not recognize the card. I cant recall exactly what I did since its been awhile but I used this sticky to resolve. I believe it was a ndiswrapper issue

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

good luck

darco

---

### Post by haribol707 on 2009-12-20
I have the same wireless card but did not face any issues when I tried KK. It was detected at install time. Only problem was the known issue with frequently dropped wireless connections. However, I have reverted to 9.04 due to various other reasons. Waiting for KK to stabilize before I upgrade again. Have you tried running off Live CD? Does it work then?

---

### Post by rug2 on 2009-12-21
> **darco said:**
> I have the same network card and when I first installed KK, it also did not recognize the card. I cant recall exactly what I did since its been awhile but I used this sticky to resolve. I believe it was a ndiswrapper issue

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

good luck

darco

Thanks for the replies people. I'll try playing around with ndiswrapper and see if it makes things work. Since some of you are reporting the card as working, I'll hold on the bug report for now.

---

### Post by seenthelite on 2009-12-21
I have the same card on Dell Inspiron 6400 and have installed 9.10 a couple of times and each time no wireless. My fix is install wicd and reboot. I must stress that if you do this you will lose Network Manager and it is difficult to reinstall it. So Synaptic Package Manager simply select wicd install and reboot.   I no longer have Network Manager and do not need it.

---

### Post by rug2 on 2009-12-21
> **seenthelite said:**
> I have the same card on Dell Inspiron 6400 and have installed 9.10 a couple of times and each time no wireless. My fix is install wicd and reboot. I must stress that if you do this you will lose Network Manager and it is difficult to reinstall it. So Synaptic Package Manager simply select wicd install and reboot.   I no longer have Network Manager and do not need it.

Wouldn't this suggest that the problem is with network manager or one of it's underlying tools? Do you still have the signal dropping issues with wicd? Thanks.

---

### Post by rug2 on 2009-12-22
Ok, wicd didn't help. 

I've gone through [this Wireless Trouble shooter]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") and have come to this: 

```

4.2.5. Driver looks ok, device disabled

    * Newer laptops come with features to disable the wireless radio to save battery when not in use. Usually this is switched by a FN+Fx key combo or specific button for the purpose. It is possible driver and everything is ok but the wireless device is in the disabled state and can't be used. Using the designated key(s) in linux sometimes does not work.

      Usually this is apparent by running the lshw command you see *-network:1 DISABLED or wireless=radio off, or if you run the iwconfig command you see eth1      NOT READY!. So how do you rectify this? It varies so much the exact solution can't be put here in this document for all the different models. So...
    *

      Look at the LaptopTestingTeam page on the team wiki to see if your laptop is listed with any information.
    * Do a google search using terms such as manufacture, model, linux, wireless, enable, button, radio....etc. When searching and finding similar pages that don't help, use words that are used in those pages to help you search.
    *

      Go to the ubuntu forums and ask, maybe someone else has the same laptop and knows the work around.
    *

      Some laptops have a controller chip on the motherboard that is only accessible through a different OS. If you have turned off your WiFi card in a different operating system, you may have to boot back into that OS and enable the card before it is accessible to Linux. 

```

This is a dead end. The wireless card, according to the trouble shooter is communicating with the kernel and the drivers are loaded. But it's been disabled. I will try one thing and report back immediately, that is trying to see if I left the wireless card disabled on Windows 7.

---

### Post by rug2 on 2009-12-22
[SIZE="5"][COLOR="Red"]**SOLVED**[/COLOR][/SIZE]

I feel like an idiot. I forgot all about the wireless kill switch on the side of the laptop. It was disabled using that. 

Thanks for all the help, everything is working now. :)

---

### Post by karmikdingo on 2009-12-30
Mate, what can I say? I didn't notice the latitude d420 switch in the right side of the board either! Thanks for pointing us to that place!

cheers

KD

---

### Post by Petteri666 on 2010-03-06
> **rug2 said:**
> [SIZE="5"][COLOR="Red"]**SOLVED**[/COLOR][/SIZE]

I feel like an idiot. I forgot all about the wireless kill switch on the side of the laptop. It was disabled using that. 

Thanks for all the help, everything is working now. :)

If it helps you at all there are more idiots around. I just spend last night and this morning "debugging" this problem :D Thanks for the post, without it I had not noticed the switch.

---

### Post by slingshotsuicide on 2010-11-13
For what it's worth to others reading this who aren't suffering a PBKAC (just a little jib, no insult meant), I found on my upgrade from Karmic to Lucid that aside from removing my icon theme, 'buntu decided to install nm in spite of the fact that i've been using wicd.  It failed to remove wicd however.  I discovered this by trying to install nm to reinstall wicd.  When apt reported that nm was already it's latest and greatest, I simply **apt-get remove network-manager** and wicd was immediately able to connect wireless to my WPA2 AP.  Hope this helps someone.

---

### Post by aaronLund on 2010-11-28
> **slingshotsuicide said:**
> For what it's worth to others reading this who aren't suffering a PBKAC (just a little jib, no insult meant), I found on my upgrade from Karmic to Lucid that aside from removing my icon theme, 'buntu decided to install nm in spite of the fact that i've been using wicd.  It failed to remove wicd however.  I discovered this by trying to install nm to reinstall wicd.  When apt reported that nm was already it's latest and greatest, I simply **apt-get remove network-manager** and wicd was immediately able to connect wireless to my WPA2 AP.  Hope this helps someone.

Many thanks for writing this, sss.

I just upgraded ubuntustudio from 8.04 to 10.04 on an old fl91 laptop and couldn't get wireless to work.

Your post put it all together.  Well that, and having to delete my bios settings (I think, anyway).

Just out of curiosity....I had 8.04 on this (with a working wlan card), installed Win 7 for my wife (never put it online though as this machine may not be powerful enough) and decided to just put 10.4 on it.  Since I never saw wireless when I had Win 7 on it (for those couple of days), I don't know if it wasn't working there but.....do you suppose that installing that (win 7) could have overwritten my BIOS settings which was somehow getting in the way of powering my WLAN card?

The issue was that I couldn't even see any networks with 10.4 and kept on seeing the dreaded 'avahi' next to the wlan0 listing in ifconfig.

Truth be told, there isn't anything in the bios about powering the wlan card but I did get some warnings about TPM having some mismatch right after clearing the bios by unplugging the battery.  (My F2 key is dead!  So you can see the rabbit hole I was just in).

I learned a shitload of stuff about wireless in linux though. I've always heard the stories but have somehow managed to get lucky.

Looks like I'm still dropping this connection pretty regularly but the fact that it's working at all is blowing my mind.  That was like 2 days of hacking away at this issue.

Thanks again.

---

### Post by aaronLund on 2010-11-28
I think I solved the dropping connections issue as well.

See here:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/348204?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/348204?comments=all)

Look for Wadelius's post.

Do that.

OK, I'll include it just because that would be the right thing to do.

[QUOTE="Wadelius"]I was finally able to fix this

I've had this problem for a long time and have tried a lot of fixes, none of them have worked. I finally gave up and ordered a new network card with another chip. It has not arrived yet, so naturally I find a solution that works when trying to take care of another problem :-). In my case the cause of the connection dropping was tcp window scaling. I found it here:
[http://wheel.troxo.com/2008/06/05/tcp-window-scaling-conundrum/](http://wheel.troxo.com/2008/06/05/tcp-window-scaling-conundrum/)
and here:
[http://www.youtube.com/watch?v=N_AzSOJbKlI](http://www.youtube.com/watch?v=N_AzSOJbKlI)

Some network cards have problems with tcp window scaling, which means changing the size of the packets on demand. You can either change the max min boundaries of the packets, or disable scaling altogether. What worked for me was disabling it.

To disables tcp window scaling you need to add the line below to your /etc/sysctl.conf.
net.ipv4.tcp_window_scaling=0

To reset run
sudo sysctl -p
[/QUOTE]

---

