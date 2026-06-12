---
title: "Edgy upgrade made Atheros wireless stop working"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by btilly on 2006-10-31
I am using a Thinkpad G41.  I am trying to connect to a local wireless Linksys router.  The laptop uses an Atheros card, so I am using madwifi.  I am getting a failure and no obvious error messages.

The script that I use to connect looks like this:

```
#! /bin/bash
ifconfig ath0 up
iwconfig ath0 channel 1
iwconfig ath0 essid tilly
dhclient ath0
```

Until my upgrade this worked fine.  I get no errors from ifconfig or iwconfig.  I can see that the network is there with iwlist.  (The driver works at least a little bit...)  The network is unencrypted.  (I don't care if you steal my wireless connectivity.)  When I plug in an ethernet cable, "dhclient eth0" works fine.

I tried recompiling madwifi from source then rebooting.  I experience the same (lack of) symptoms.  Googling didn't turn up anything obvious.

From the iwscan here is the network I am trying to connect to:

```
          Cell 04 - Address: 00:02:2D:20:C8:8A
                    ESSID:"tilly"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/94  Signal level=-44 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
```

And here is "iwconfig ath0"

```
ath0      IEEE 802.11g  ESSID:"tilly"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:17 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=52/94  Signal level=-43 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
Does anyone have any suggestions for where I can look for more information about what could be causing this problem, or possible ways to solve it?

Thanks,
Ben

---

### Post by wieman01 on 2006-10-31
Question (because I am a bit nosy): Why do you upgrade to Edgy at all? The current stable version with Long Terms Support (LTS) is Dapper. I don't really understand why people even bother to install Edgy.

Second, please post this file:
> sudo gedit /etc/network/interfaces
Then also tell us more about your local wireless network: DHCP or static IP, no encryption (?), ESSID ("tilly"?), router IP.

---

### Post by btilly on 2006-11-01
> **wieman01 said:**
> Question (because I am a bit nosy): Why do you upgrade to Edgy at all? The current stable version with Long Terms Support (LTS) is Dapper. I don't really understand why people even bother to install Edgy.

My home laptop was Dapper, my work computer is Hoary.  Hoary is getting long in the tooth, and I wanted to decide whether I should upgrade it to Dapper or Edgy.  I thought it was better to test Edgy on my personal equipment first.

Given my current experience, I'm glad I did.  Also I don't like Firefox 2 as much.  (At least until tab mix plus is ported.)

> **wieman01 said:**
> Second, please post this file:

Then also tell us more about your local wireless network: DHCP or static IP, no encryption (?), ESSID ("tilly"?), router IP.

Um, I already posted most of that when I posted the results of iwscan.  The fact that the script I was using invokes dhcpclient should tell you that I am using DHCP.  The script I was using ignores /etc/network/interfaces so that is irrelevant.  But if I add a section for ath0 in there and use ifup, I get the same result as with the script I was already using.

Far more useful has been stuff that I've found indicating that there was a major codebase change in madwifi.  Some cards that were supported are no longer supported.  I've found the old madwifi code but it does not compile cleanly for me.  (Various unsupported symbols.)  According to [http://madwifi.org/browser/branches/madwifi-old/INSTALL](http://madwifi.org/browser/branches/madwifi-old/INSTALL), it only works for kernels 2.4.2x - 2.6.10.  Unfortunately Edgy is on kernel 2.6.17.

From what I read on the madwifi site, my wireless card *should* be supported by the new codebase.  I'm still trying to decide whether I should locate an old Linux kernel, downgrade that, then install the old drivers, or whether I should locate my exact wireless card and research getting that to work properly with the new code.

Incidentally I see lots of other people reporting problems with their wireless cards.  I wonder whether the new madwifi codebase could be responsible for some of those as well...

Cheers,
Ben

---

### Post by wieman01 on 2006-11-01
I assume your built-in card is also wireless B, correct? 

Have you given "ndiswrapper" a shot instead? If the "madwifi" driver is corrupt "ndiswrapper" may work for you. This is a nice howto:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

The reason why I was asking all these questions about your network is that it is sometimes hard to assess the level of "proficiency" that users have. Their Ubuntu setup is one thing, however, very often it turns out that their routers happen to have different settings. But you seem to know what you're doing.

First: I recommend Dapper nonetheless as it is the current non-experimental version.
Second: Give "ndiswrapper" a go if you prefer Edgy nonetheless.

---

### Post by btilly on 2006-11-05
Thanks, after some more head banging I tried your suggestion and used ndiswrapper and now I have wireless connectivity again. :-)

Cheers,
Ben

---

