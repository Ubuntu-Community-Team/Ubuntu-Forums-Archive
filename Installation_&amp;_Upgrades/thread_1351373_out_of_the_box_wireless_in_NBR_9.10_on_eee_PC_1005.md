---
title: "out of the box wireless in NBR 9.10 on eee PC 1005HA ?"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by luckyduck3 on 2009-12-10
Many people seem to experience everything working "out of the box" when installing NBR 9.10 on the eee PC 1005HA.  However, for me:

Not working:
-------------
[wireless] (actually working ...see below)
fn keys: [wireless on/off], touchpad on/off
microphone

Tested and working:
-------------------
fn keys: brightness, ext. display, sleep, mute, volume control
webcam

I'm happy to follow the directions at:

[http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/](http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/)

to get everything working, but I don't want to be using special kernel modules if I don't have to.  Because everyone else seems to have "everything work out of the box" on this machine, I just wanted to check to make sure I'm not missing something obvious.

As for the wireless, my card seems to be recognized, yet no connections appear automatically:

```
wlan0     Link encap:Ethernet  HWaddr <correct_MAC_Addr>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr <MAC_Addr_Plus_Zeros>  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Any thoughts?

Also, while I have your attention, earlier I was able to manually install the linux-backports-modules-karmic_2.6.31.16.29 package (and dependents) in order to get wireless working.  After doing so, I tried to 'sudo apt-get install subversion' and the same for openjdk-6-jdk, but in both cases, nothing found!  I did not alter the sources.list, but indeed verified that universe and multiverse are listed, so I'm confused.  Why wouldn't those common packages be available to this system?

Thanks so much for any help!

By the way: I don't see how this would affect the wireless, etc., but before installing ubuntu, I was using the pre-installed windows XP for a couple days and I did allow the Asus Live Update feature to install a BIOS update.  Could that be the reason why my particular machine is so (un-)special?

----- end of original post ----

[UPDATE]: Okay, I feel dumb.  The wireless _does_ work out of the box.  I was right clicking on the wireless icon instead of left clicking.  Once I did that, I saw my network just sitting there.  The other things still appear to be broken.  I'll proceed with following directions from:
[http://vip.asus.com/forum/view.aspx?id=20091110101016812&SLanguage=en-us&board_id=20&model=Eee%20PC%201005HA&page=1](http://vip.asus.com/forum/view.aspx?id=20091110101016812&SLanguage=en-us&board_id=20&model=Eee%20PC%201005HA&page=1)
but it would be nice if I didn't have to do that.

[UPDATE]: Okay, another reason for me to feel dumb: before installing any new packages, you have to run 'sudo apt-get update'. :)  Then you can install svn, java, etc.

---

### Post by gabak on 2010-01-02
hey did you try to plug in an external wifi antena? maybe your internal wifi does nt work.
then run ubuntu 9.10
can u tell me what does NBR stand for?

---

