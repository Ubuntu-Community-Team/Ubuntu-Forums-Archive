---
title: "Check_mk to ubuntu on raspberry-pi 3b"
date: 2017-12-22
forum: Installation &amp; Upgrades
---

### Post by flixflachs on 2017-12-22
Hi,

currently i am trying to install a check_mk server (raw) for home use on my raspberry pi 3 with ubuntu 16.04.02 mate via ssh.


When i tried to

```
 wget https://mathias-kettner.de/support/1.2.8p26/check-mk-raw-1.2.8p26_0.xenial_amd64.deb/
```

and

```
gdebi check-mk-raw-1.2.8p26_0.xenial_amd64.deb
```

it says

"Wrong architecture 'amd64'"

I am aware of the fact that the Rasp. 3b has a 1.2GHz _64-bit_ quad-core _ARMv8_ CPU, which means for me that it is a "normal/usefull" 64 bit system (no AMD or Intel).

Is there any solution to run a pi with ubuntu (mate or not?) AND check_mk?


Thanks for future help ;)

flixflachs

---

### Post by DuckHook on 2017-12-22
Welcome to the forums, flixflachs.

I have no real knowledge about raspberry pis (wish I had one!) but I do know that you can't run amd or i386 binaries on them. The pi uses a RISC chip, not a CISC, so it needs packages ending:```
***arm64.deb
```
This page may help: [https://wiki.ubuntu.com/ARM/RaspberryPi#Ubuntu_arm64.2FAArch64](https://wiki.ubuntu.com/ARM/RaspberryPi#Ubuntu_arm64.2FAArch64)

---

### Post by flixflachs on 2017-12-23
Thanks for your answer.

The only way I see to solve this is to compile it to an Arm64 (in some way :confused:)

Is this even a possible solution? I can not imagine that this is the way to go.

---

### Post by DuckHook on 2017-12-23
This might help: [https://www.vdsar.net/raspberry-pi-open-monitoring-distribution-setup-guide/](https://www.vdsar.net/raspberry-pi-open-monitoring-distribution-setup-guide/)

Although you can compile it (you can compile anything with source and if you know what you are doing), this solution adds a PPA from someone who presumably already has compiled it and is offering the binary for download. I have no experience with either your package or Raspi, so can't help you any further on the technical front. However, in my research, I also came across this: [https://www.vdsar.net/raspberry-pi-open-monitoring-distribution-setup-guide/](https://www.vdsar.net/raspberry-pi-open-monitoring-distribution-setup-guide/)

Apparently, check_mk is resource heavy and so disk intensive that:

[LIST=1]
[*]You will find the raspi too underpowered, and
[*]You will wear out your SSD card after a month or two of use.
[*]
[/LIST]
Of the two, the latter issue is more severe. A write-exhausted SSD will refuse further writes thus crashing your system. The various posters recommend a NUC from Intel over the raspi.

---

### Post by flixflachs on 2017-12-24
Thanks for the links.
The first one seems to be quiet helpfull (Edit: for the pi to be monitored?). So the guy downloads a "_all.deb"-file to extract it (the link is still available). So far so good, but it's only the agent as i see it.

To take reference to your keywords:

1. Yes, the pi is underpowered, but I just want to test it and do it "because i can" :p
2. it is just a test, there won't be any productive use over a long time.

---

### Post by DuckHook on 2017-12-24
Following a series of links from the first one that I gave you yields: [http://mathias-kettner.com/check_mk_download.php?HTML=yes](http://mathias-kettner.com/check_mk_download.php?HTML=yes)

A further link to the source code is at bottom of that page.

I really know nothing further about check-mk. It appears to be a rather obscure app. You may have to compile it from source for your purposes.

Good Luck and Happy Ubuntu-ing!

---

### Post by flixflachs on 2018-05-16
Hey, finally i found a guide:

[https://hope-this-helps.de/serendipity/archives/Raspberry-Pi3-OMD-Open-Monitoring-Distribution-471.html](https://hope-this-helps.de/serendipity/archives/Raspberry-Pi3-OMD-Open-Monitoring-Distribution-471.html)

It is in german, but following the pictures explain it well

---

