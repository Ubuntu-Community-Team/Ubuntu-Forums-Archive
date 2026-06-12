---
title: "Downloading Karmic updates"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by zagnut telstar on 2009-12-17
Ubuntu 9.10 networking doesn't seem to work on my machine. I'd like to download the current set of updates on another machine and then install them on Karmic. Can Karmic generate a list of packages to download, and then is there an easy way to install them once they are downloaded?

I'm hoping that the updates will solve my networking problem.  It's a fairly generic machine, a 2005 Compaq AMD Athlon 64 with integrated Realtek wired networking.

Thanks.


edit: Have I posted this to the wrong forum? Is there a better place for this question? I've done some searching and haven't found any solution for downloading updates. I would think this would be a common question.

---

### Post by leprkhn on 2009-12-17
Perhaps fixing your network connection would be easier.

What is the output from
```
lspci | grep -i network
```

What does
```
sudo ifconfig
```
tell you?

---

### Post by zagnut telstar on 2009-12-17
Hi. I don't actually have 9.10 installed at the moment. I reinstalled 8.10 when I couldn't get things working. Networking seems fine there but didn't work on either 9.10 or 9.4

---

### Post by leprkhn on 2009-12-17
```
lspci | grep -i network
```
Will still have the same output. That output will tell us which network controller is on your motherboard. Perhaps giving more insight into where the issue is coming from.

---

### Post by zagnut telstar on 2009-12-17
Hmm, rebooting from xp into 8.10, networking didn't work. Maybe it's a rebooting from xp issue.  (lspci | grep -i network) didn't produce anything.  Just lspci showed a line:  Ethernet Controller: Realtek Semiconductor Co., RTL-8139/8139C/8139+ (rev 10)  Sorry for delay. Things keep intruding. Let me cold boot it and see if I get anything different.

---

### Post by zagnut telstar on 2009-12-17
Well. Networking in 8.10 was working previously, but doesn't seem to be now. Cold booting made no difference.

---

### Post by zagnut telstar on 2009-12-17
Oh, and sudo ifconfig shows:  eth0 Link encap:Ethernet HWaddr blah blah      UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1      RX packets... all 0      TX Packets... all 0      collisions:0 txqueuelen:1000      RX bytes:0 TxBytes:0      Interrupt:21 Base address:0xdc00  lo   link encap:local loopback      inet addr 127.0.0.1 mask 255.0.0.0      UP LOOPBACK RUNNING MTU:16436 Metric:1      collisions:0 txqueuelen:0      RX bytes:0 TxBytes:0

---

### Post by leprkhn on 2009-12-17
> **zagnut telstar said:**
> Oh, and sudo ifconfig shows:  eth0 Link encap:Ethernet HWaddr blah blah      UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1      RX packets... all 0      TX Packets... all 0      collisions:0 txqueuelen:1000      RX bytes:0 TxBytes:0      Interrupt:21 Base address:0xdc00  lo   link encap:local loopback      inet addr 127.0.0.1 mask 255.0.0.0      UP LOOPBACK RUNNING MTU:16436 Metric:1      collisions:0 txqueuelen:0      RX bytes:0 TxBytes:0

That's good. At least we know that Ubuntu can see your eth0. Which it should because [THIS]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=6&PFid=6&Level=5&Conn=4&DownTypeID=3&GetDown=false#2") (RealTek) page says that drivers for this chip have been built into the main kernel.

Have you tried:
```
sudo ifconfig eth0 up
```

---

### Post by zagnut telstar on 2009-12-17
sudo ifconfig eth0 up  No output from this.  I guess I really need to learn how to format things here...

---

### Post by leprkhn on 2009-12-17
> **zagnut telstar said:**
> I guess I really need to learn how to format things here...

You ARE learning!
Every problem brings you closer to knowing how to solve the next problem.

Unfortunately, I'm out of ideas.
You may want to see if someone in [THE NETWORKING FORUM]("http://ubuntuforums.org/forumdisplay.php?f=336") knows what to do.

---

### Post by zagnut telstar on 2009-12-17
Thank you very much for your help. I'll check over there...

---

### Post by leprkhn on 2009-12-17
Sure thing, boss. Best of luck to you.

---

### Post by nibirumarduk on 2009-12-18
> **zagnut telstar said:**
> Ubuntu 9.10 networking doesn't seem to work on my machine. I'd like to download the current set of updates on another machine and then install them on Karmic. Can Karmic generate a list of packages to download, and then is there an easy way to install them once they are downloaded?

I'm hoping that the updates will solve my networking problem.  It's a fairly generic machine, a 2005 Compaq AMD Athlon 64 with integrated Realtek wired networking.

Thanks.


edit: Have I posted this to the wrong forum? Is there a better place for this question? I've done some searching and haven't found any solution for downloading updates. I would think this would be a common question.


zagnut telstar, I'm not sure if I'm getting you right but to replicate your packages selection on another machine or restore it if re-installing, you can type dpkg --get-selections > /home/username/dpkg-get-selections-master.txt to the other machine, and when there type sudo dpkg --set-selections < /home/username/dpkg-get-selections-master.txt && sudo apt-get dselect-upgrade

Good luck!

---

### Post by zagnut telstar on 2010-02-18
Just wanted to note here that the answer to my networking problem was found at:
[http://www.linuxquestions.org/questions/linux-networking-3/realtek-813981688169-on-2.6.21.3-or-newer-593495/](http://www.linuxquestions.org/questions/linux-networking-3/realtek-813981688169-on-2.6.21.3-or-newer-593495/)

---

