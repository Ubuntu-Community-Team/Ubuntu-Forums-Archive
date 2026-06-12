---
title: "Feisty Upgrade breaks Networking"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by jmcclean on 2007-06-16
There have been a couple of similar posts to mine, with some advice that suggests that what may be going on is some kernel patches are preventing networking from working.

**Symptons**
Neither the network cable nor the wireless networking work.

**Background**
This is a Dell Inspiron 8000. It was running Edgy successfully for quite some time. I upgraded to feisty through the upgrade manager. After the reboot, the networking would not work. Clicking on the network manager gives a dialog that reads:

   SIOCGIFFLAGS error: No such device

**Various Information**

"ifconfig -a" only shows the loopback address. 

"lpsci" lists "Ethernet controller" Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)

cat /etc/network/interface reads

  auto lo
  iface lo inet loopback

  iface wlon0 inet dhcp
  wireles-essid jandh

  auto wlan0

sudo /etc/inet.d/networking restart results in a bunch of 'no such device' messages.

Any help would be very much appreciated.

---

### Post by jmcclean on 2007-06-17
Well, I figured this out so I'm posting my solution in case it helps someone else.

Two things seemed to be going on. First, I'm not sure my 10/100 connection ever worked. I always used wireless and just tried the wired when the wireless went dead. (I bought the computer used.) So that's still a bit of a mystery.

The second thing is I was running the driver for my Realtek RTL8180L card referenced here:

[http://pcburn.com/article.php?sid=628](http://pcburn.com/article.php?sid=628)

The feisty upgrade just seems to have removed that, as near as I can tell. Instead of putting it back (it was a little flakey and would seize the machine on occassion) I went the ndiswrapper route. The best doc. was here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

:D

---

### Post by Tahi_Kiwi on 2007-12-25
Has anyone been able to contact Ubuntu development that the the Updates are breaking network connectivity? Over the past few months, this problem has been reported here.

It's frustrating, but it wouldn't surprise me, if Ubuntu software development were totally unaware of these problems. I've worked in environments at other software companies where development and customer support issues were totally oblivious to each other.

---

