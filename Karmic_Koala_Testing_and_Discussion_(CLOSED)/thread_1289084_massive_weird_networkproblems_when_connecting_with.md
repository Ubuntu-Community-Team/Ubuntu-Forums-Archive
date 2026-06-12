---
title: "massive weird networkproblems when connecting with wlan"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by gruadp on 2009-10-12
I'v massive networkproblems here with karmic. I use ubuntu since 7.x on my laptop but I've never experienced such problems.

i) when I connect via LAN, everything is fine

ii) when I connect via WLAN with a intel-ipw2200 or an atheros-card to a netgear-router or a dlink-router then the following problem happens:

    * firefox and opera get extremely slow. some pages arent reachable at all
    * I cannot connect to some hosts via ssh, while I can ping the same hosts and connect to other hosts in the same network. 
    * access to nfs-shares in the local network is working, but bash-auto-completion on mounted shares takes ages and even timeouts.


I can ping all hosts and get very good latency. Signal-Quality is fine and the same pages that troubles me in firefox and opera seems to make no problem when downloading them with "wget -p". I can copy huge files via smb/nfs without problems in the expected wlan-speed 15-20MBit/seconds

Its really weird !! I monitored the traffice with tcpdump but I'm no expert on tcp-level and didnt know what to look for. I tried ping with huge packagesizes and had no loss. No bad entries in syslog.  Its just strange.

I'm on an acer aspire 2020 (karmic tells me that it does not know about this bios on boot in a wmi-message) and I didnt have this problems with 8.04,8.10,9.04,9.10

---

### Post by homerhomer on 2009-10-12
I have noticed some strangeness with Karmic too, Mine will connect but it pauses for about 3-5 seconds and then it connects.

---

### Post by mad0master on 2009-10-12
Same problem here: upgraded from 9.04 to 9.10 (beta of karmic)

connecting with lan everything is fine.
connecting with wlan: connection process is fast, but the connected itself work extremely slow!

Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k on Lenovo T61 laptop (Intel Wireless WiFi Link 4965AGN)

---

### Post by maheshasolkar on 2009-10-12
I too am seeing some strange problems with varied level of reproducibility. What is reproducible is that wireless does not connect. This only started when I updated my system around Saturday.

My laptop stopped connecting to the default access point. I removed the entry from the connections and created a new one. It let me enter the password (WPA2 Personal) and click 'connect' (or 'apply' - don't remember). But the connection failed after trying for a long time.

Sometimes, I can enter the password, but the 'apply' button is greyed out, so I can't do much.

Looking at the log, it looks like the authentication happens correctly, but there is a problem with DHCP handshake. Other computers on the wireless network work fine, so the router is set up correctly.

Here's my HW info:

  02:0b.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
  ipw2200 - Intel(R) PRO/Wireless 2200/2915 Network Driver

---

### Post by MALEADt on 2009-10-12
Another vote on wireless issues. I had it back ago ~Alpha2, and it seems to be acting strange once again.

---

### Post by laborg on 2009-10-12
anyone filed a bug so far? my wlan reacts also strange.

---

### Post by maheshasolkar on 2009-10-12
> **laborg said:**
> anyone filed a bug so far? my wlan reacts also strange.

Behavior I am seeing is too inconsistent to file a bug. I am not sure I'll be able to reproduce the behavior to provide sufficient logs/transcripts if I file a bug.

---

