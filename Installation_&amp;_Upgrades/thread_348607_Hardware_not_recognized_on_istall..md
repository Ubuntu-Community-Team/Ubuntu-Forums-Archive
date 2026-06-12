---
title: "Hardware not recognized on istall."
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by seedsca on 2007-01-29
Hello. I've installed kubuntu 6.10 and there seem to be some issues.
My eth card is not recognized at all. In system settings - system services while attempting to start networking I recieve the message. 

siocsifaddr: no such device.
eth0: error while getting interface flags: no such device
eth0: error while getting interface flags: no such device
bind socket to interface: no such device
failed to bring up eth0.
there is already a pid file /var/rundhclient.eth1.pid with pid 134993416
...
and this repeats for eth1, eth2, ath0, and wlan0

also when I do a lspci there is no output at all... very strange to me. I'm not sure where to go from here.

this computer is dual booting to windows xp and all the hardware works fine there. I'm very confused as to what steps to take next.

any thoughs?

---

### Post by Stemp on 2007-01-29
> also when I do a lspci there is no output at all... very strange to me. I'm not sure where to go from here.

```
lspci | grep ethernet
```

```
dmesg | grep eth0
```

---

### Post by seedsca on 2007-01-29
lspci | grep ethernet outputs nothing at all so does
dmesg | grep eth0

the computer I'm using to write this right now is also a 6.10 fresh install and both these commands work as expected.

an other odditty I've noticed is that to get to the graphical mode I have to send a ctrl-alt-backspace. else it'll sit there with a black screen for ever. Mother board not supported??

---

### Post by Stemp on 2007-01-30
> Mother board not supported??

Clearly if you have no output on lspci there is something wrong.
What motherboard is it ?

---

### Post by charlvj on 2007-01-30
> **Stemp said:**
> ```
lspci | grep ethernet
```

I tried this and noticed the output of lspci has 'Ethernet' not 'ethernet', so try 
```
lspci | grep -i Ethernet
```

---

### Post by seedsca on 2007-01-30
motherboard is a via p4pb 400

correct me if I'm wrong but pipping the output of lspci to grep would not add something there that is not outputting on a simple lspci. and sadly nothing does show up on that either...

Also this does not work with a live cd boot of kubuntu dapper? I'm soooo lost.

---

