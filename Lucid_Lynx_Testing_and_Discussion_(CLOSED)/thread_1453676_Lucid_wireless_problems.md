---
title: "Lucid wireless problems"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sandfly357 on 2010-04-13
I've recently upgraded from 9.10 to 10.04 on my Compaq nx6125 laptop, which uses a Broadcomm b4318 chip. I had wireless working perfectly pre-upgrade.

After the upgrade, wireless continued to work perfectly, even surviving reboots, for several days. Two days ago, when rebooted, no indicator light appears fro the adapter, and all connectivity is lost. the device is still there and recognised, but I cannot enable it.

However, if I manually point my system (iwconfig wlan0 essid any) I connect to my neighbours SSID (which is wide open and unencrypted, foolish man) and I can connect  to the internet and the device functions perfectly. But as soon as I point back to my own SSID (which is broadcasting, not hidden), the interface drops and an iwconfig output shows no association.

How can this be? I know it's a cliche, but I have changed nothing on my system or my router, and neither is configured to auto-update without confirmation. My other home systems continue to connect and function normally. It cannot be the upgrade, as this worked for several days previously. So how can my adapter only wake up and connect to an open router all of a sudden?

Any words of wisdom would be greatly appreciated!

---

### Post by perriko on 2010-04-22
Ditto here! I had WPA2 working fine on 9.10. Now I can connect at home WPA but not at work WPA2. I have changed nothing!

Help from anywhere, please - otherwise will have to go back to 9.10 to maintain productivity!

---

### Post by flammon on 2010-04-23
Yes, same problem here. Has a bug been reported?

---

### Post by sartic on 2010-04-23
In karmic my wireless was crap so i used backport. try it:
linux-backports-modules-wireless-lucid-generic
In Jaunty and Lucid now i do not need it anymore.

---

### Post by jondodson on 2010-04-23
Same problem.  Beta 2 was fine until wednesday then all of a sudden no wifi.  Karmic laptop connects ok.  Lucid wifi symbol just keeps pulsing but no connection.  WPA2.  64 bit.  Belkin PCI wifi card.  If you click the wifi icon it thinks it's connected, but it isn't.

---

### Post by DodgeV83 on 2010-04-23
Same issue here, no WPA2 connectivity on a Wubi installed 10.04.

Connects fine to a non-encrypted router.  Will try tonight with WICD instead of Network Manager.

---

### Post by xrado on 2010-04-23
same here with Lucid RC

---

### Post by whitetimer on 2010-04-23
I did a clean install of RC this morning and have no problem with a wireless connection .. But did with Beta 2 

:popcorn:

---

### Post by ozorba on 2010-04-23
In my case it is different. I get wiFi connection. However, once in a while I loose it. It says that it is connected but I get no iternet traffic. careful checking showed that ufw (ubuntu firewall) detected some activity reporting an ip address trying to get in. Like this:
[17144.978512] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:5e:6b:89:21:03:1e:e5:98:a9:fc:06:00 SRC=81.159.59.250 DST=192.168.1.5 LEN=132 TOS=0x00 PREC=0x00 TTL=111 ID=30201 PROTO=UDP SPT=51126 DPT=50605 LEN=112

---

### Post by blackSP on 2010-04-24
Here to with an Edimax 7711utn on my PC
Had a real crappy connection with 9.10 64bit but it worked, sort of (Laptop is fine btw, no probs whatsoever).
But since I upgraded the PC to 10.04 64bit I have zero connection. I can see networks but no connection. This sucks!

I'm going back to wired :(

---

### Post by c00lwaterz on 2010-04-24
same problem with my wifi and ubuntu 10.04 beta2.

at first I can connect to my access point but no internet. then i update wicd etc then now i cannot connect to my acess point too.

there is some problem i think in lucid that we need to configure.

so i use wired when using ubuntu 10.04

---

### Post by And1945 on 2010-04-24
Why are there all of a sudden all these wifi problems? Ever since madwifi went legacy there has no more than problems.

I have had wifi problems with my HP laptop with 9.04, 9.10, 10.04 beta 1, beta 2 and now rc.

Oh yeah, and installing wireless backports does not do the trick for me.

---

### Post by c00lwaterz on 2010-04-25
i also having hard time fixing it. searching the google engine until almost every instruction i tried were failed. it can detect the acess point but cannot connect properly and also no internet access even connect for a few seconds then it will auto disconnect. I try fixing then it won't connect anymore to my access point.

---

### Post by Khakilang on 2010-04-25
I had not problem with Lubuntu Lucid Lynx. I did a clean install with my USB wifi adapter plug in and manage to do all the updates. Connect automatically every time I boot.

---

### Post by blackSP on 2010-04-26
I'm gonna fix this once and for all.
1) I don't need no stinking USB adapter so that one is gonna be burned
2) I have a nice Ethernet connection on my mobo, that's what I'll use
3) No ugly wires in my house
4) The solution: I'll get me a nice wireless receiver with an Ethernet connection and stick that in my mobo with a good old cat5 cable!

---

### Post by And1945 on 2010-04-26
I made a clean install of Ubuntu 10.04 RC, and it worked. My wifi that is. Do not know what went wrong.

But the cool thing is now, that it works, my wifi indicator flashes on activity :D

---

