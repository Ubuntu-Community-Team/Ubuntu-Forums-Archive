---
title: "OK one month in and I am tapping out"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by ajd79 on 2010-05-26
I have been using Ubuntu 10.04 for about a month on my Toshiba satellite.  9.10 was brilliant, it recognized the wireless card upon install. Then I "upgraded" to 10.04 and I have only one good thing to say purple is better than orange.  

Everything I have tried, for hours a day I might add, has not worked.  I give up.  I am not dual booting but that was not an issue with previous incarnations of the operating system.  I want to either revert to 9.10 or just leave the Ubuntu community entirely.  I need wireless.

I am using a Satellite P205d-s7802 with an Atheros AR5001 wireless card.

I have followed all the directions and generous help but at this point the only question I have is: How do I revert to previously installed versions of linux. Do I need to reformat the HD or is there a less intrusive way?

Sorry to be so long  winded but I rant when frustrated. [-(

---

### Post by bondo101 on 2010-05-26
Go back to Karmic I had some troubles with lucid I went back now 
no more problems , I liked lucid but I will wait for awile till the bugs are sorted out.I get frustrated  also but don't give up 
.Its alot better than the blue screen of death.:)

---

### Post by WinRiddance on 2010-05-26
> **bondo101 said:**
> Go back to Karmic I had some troubles with lucid I went back now 
no more problems , I liked lucid but I will wait for awile till the bugs are sorted out.I get frustrated  also but don't give up 
.Its alot better than the blue screen of death.:)

Have you tried installing **wicd** directly from the software center? That solved the problem for our Son with his Acer laptop. It's another more user friendly network manager. Once installed and working make sure that the default Network Manager is either disabled or removed entirely to avoid any conflicts. I use wicd myself and like it much better. Of course there's always cable DSL via ethernet cable too, of course. Ubuntu always recognizes that. No way on earth that I'll ever go back to that BSOD again !!!

---

### Post by WinRiddance on 2010-05-26
Check this link here too, for Atheros Wireless cards.
[http://ubuntuforums.org/showthread.php?t=1484242](http://ubuntuforums.org/showthread.php?t=1484242)

---

### Post by ajd79 on 2010-05-28
These worked great, thanks a lot. Lucid still won't CONNECT to my wireless but I at least can see that it is there.  I think that I am going to revert to a previous install till the bugs are worked out.  Is it as simple and painful as Format the HD and install from previous disc?

If not any help will be appreciated. BSOD is not the way I want to go. I like actually being able to use my computer. :)

---

### Post by davidmohammed on 2010-05-28
before you do that - can you look at your system logs (administration - log file viewer) to see if there are any errors relating to your wireless card at around boot time.  It should indicate why it is not connecting.

---

### Post by ajd79 on 2010-05-28
as far as error reports what am I looking for specifically?

---

### Post by kiddykoff on 2010-05-28
I'm using an atheros card too.
```

network
             description: Wireless interface
             product: AR5001 Wireless Network Adapter
             vendor: Atheros Communications Inc.
             physical id: 0
             bus info: pci@0000:03:00.0
             logical name: wlan0
             version: 01
             serial: 00:1f:3a:86:a2:9b
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ath5k ip=192.168.5.146 latency=0 multicast=yes wireless=IEEE 802.11bg
             resources: irq:19 memory:f6000000-f600ffff

```

when using karmic everything worked peachy except for my killswitch. Now in Lucid, the killswitch works as well as the led associated with it. Is there anything i can do to help?

---

### Post by davidmohammed on 2010-05-28
> **ajd79 said:**
> as far as error reports what am I looking for specifically?

look at dmesg - towards the bottom it should have messages relating to loading of device drivers such as your wireless card

---

### Post by WinRiddance on 2010-05-28
> **ajd79 said:**
> These worked great, thanks a lot. Lucid still won't CONNECT to my wireless but I at least can see that it is there.  I think that I am going to revert to a previous install till the bugs are worked out.  Is it as simple and painful as Format the HD and install from previous disc?

If not any help will be appreciated. BSOD is not the way I want to go. I like actually being able to use my computer. :)
.

Sometimes there's a conflict between wicd and the default network manager which is installed automatically. Sometimes it's even necessary to remove or disable the default network manager. **If you've already installed wicd** to your Ubuntu, go ahead and try this:

START ---> SYSTEM ---> PREFERENCES ---> Click on **Startup Applications**

Now find both, wicd and the network manager - see if both of them are on at the same time. If so, go ahead and uncheck the network manager followed by restarting your computer. Then see if your WiFi network comes up. Also, if you're connected to a **external WiFi modem or router** you might have to enter the network key into your WiFi settings before they'll recognize your connection. Last but not least, if you happen to have a WiFi USB stick available, go ahead and plug that sucker in ... it might actually work after a few seconds. Seen that happen twice ....

---

### Post by davidmohammed on 2010-05-29
[this guy]("http://ubuntuforums.org/showthread.php?t=1496577") has had some success with your type of wireless card.  Might want to give it a try.

---

