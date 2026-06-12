---
title: "Boot loader hangs at startup"
date: 2006-08-10
forum: Installation &amp; Upgrades
---

### Post by pcnomad on 2006-08-10
6.06 on 433MHz Celeron. 256Mb ram. System starts and runs fine after initial re-boot after install but hangs on start-up after that. Boot loader hangs at: Configuring network interfaces.
Any ideas?
P.S. Pretty new to Linux in general, so please take easy on the terminal jargon.

---

### Post by loserboy on 2006-08-10
its in your network card, I had the same problem

can you give the specs of it

also did you try to configure it after that 1st boot

---

### Post by pcnomad on 2006-08-11
I'm guessing that you mean the wireless card.
It's a Linksys WMP54G.
Yes, on the first re-boot after removing live disc. At one point I had it working without any encytion and also with WAP/TKIP but not with WEP. It work for a moment then quit.
After re-booting the system hangs up at configuring network interfaces.

---

### Post by pcnomad on 2006-08-11
Removed wireless card and system boots right up and works flawlessly with a hard wire to the same router.
Would really like to be able to use wireless. Any help or ideas would be appreaciated.

---

### Post by loserboy on 2006-08-11
ok lemme check on something here

---

### Post by loserboy on 2006-08-11
ok, well you need to undo the configuration settings that you made so you can stick the card back in and start over.
theres a way to bypass the network configuration when booting... i have to go find the thread.

---

### Post by loserboy on 2006-08-11
[this]("http://www.ubuntuforums.org/showthread.php?t=223265") is all I could find on bypassing that part.

anyway when/if you get back yo your desktop again, you need to open a console and type

```
lspci
```

then find you wireless card, mine looks like this

```
0000:02:02.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
```

then get back to me.

Edit: ya know even better if you get all that just go [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")
it will explain better than me

---

### Post by pcnomad on 2006-08-11
Thanks alot for your help. I'll get right on that and let you know how it turns out.

---

### Post by loserboy on 2006-08-11
hey wait a sec i found a problem with that guys code


sudo vi /etc/networking/interfaces    should be

sudo vi /etc/network/interfaces

at least thats what it is on my machine

---

### Post by pcnomad on 2006-08-11
The machine I'm playing with is in a place of business and its almost closing time so I won't be able to post until tomarrow. I'll read up on the article you pointed out and I'll let you know how it turns out then.

---

### Post by pcnomad on 2006-08-12
Alright, finally got around the boot hang-up, Thanks alot.
Now back to the original problem, no wireless. Once I got to the desktop I configured the wireless card (Linksys WMP54G) but still no wireless. I think its connecting but no internet. 
I then: cat /etc/resolv.conf and my ISP's primary and secondary DNS servers are listed.
Now what? I have no clue what I'm doing! But I'm not going to give up!

Here is the output of ifconfig:

ra0       Link encap:Ethernet  HWaddr 00:16:B6:9A:DA:CF
          inet addr:192.168.1.116  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:b6ff:fe9a:dacf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15274 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1704 errors:5 dropped:5 overruns:0 carrier:0
          collisions:38 txqueuelen:1000
          RX bytes:1305066 (1.2 MiB)  TX bytes:93214 (91.0 KiB)
          Interrupt:9

Here is the output of iwconfig: 

ra0       RT61 Wireless  ESSID:"startrek"
          Mode:Managed  Frequency:11 MHz  Access Point: 00:13:10:05:4A:96
          Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=100/70  Signal level:-31 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I have the router set to no encryption. I don't know what else to look at.

---

### Post by loserboy on 2006-08-12
run "lspci" in terminal then show me what it has for the wireless card

---

### Post by loserboy on 2006-08-12
right now what we're looking for is a way to identify the chipset to make sure its supported in ubuntu, see I had a WMP45G that for the life of me i could not get working, cuz they change chipsets without telling you except sometimes they put a version number or you can find out through lspci and match it up to a list users have made.

---

### Post by dragonlor20 on 2006-08-24
> **loserboy said:**
> right now what we're looking for is a way to identify the chipset to make sure its supported in ubuntu, see I had a WMP45G that for the life of me i could not get working, cuz they change chipsets without telling you except sometimes they put a version number or you can find out through lspci and match it up to a list users have made.

Is there any way I could convince you to continue on with this thread? I have followed your instructions and it has gotten me back into gnone twice now trying to configure this card, but I still don't have any real internet. I mean, it finds the networks and all of that, but no webpages. Any help would be appreciated....

---

