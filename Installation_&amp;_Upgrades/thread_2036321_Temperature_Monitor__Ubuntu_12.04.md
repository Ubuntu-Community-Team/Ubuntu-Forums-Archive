---
title: "Temperature Monitor : Ubuntu 12.04"
date: 2012-08-01
forum: Installation &amp; Upgrades
---

### Post by deep2sunny on 2012-08-01
Can you please suggest me a simple application to monitor hard disk and cpu temperature on ubuntu 12.04.:)

Thank You

---

### Post by GreatDanton on 2012-08-01
For cpu temperature I would recommend you lm-sensors.
In terminal type:
```
sudo apt-get install lm-sensors
```

Regards.

---

### Post by QIII on 2012-08-01
To get lm-sensors to do anything after installing it, you have to do

```
sudo sensors-detect
```

You'll get a message to restart some services.  Just follow the instructions.

and answer yes to everything.

Then you can run

```
sensors
```

A very easy to configure graphical interface to monitor sensors is gkrellm.  There are others.  I use conky, which is highly configurable but probably pretty intimidating to begin with.

For HDD temps

```
sudo apt-get install hddtemp
```

Then, 

```
sudo dpkg-reconfigure hddtemp
```

Answer yes to everything, or press enter when a value is already present.

Then you can configure gkrellm to display hddtemps.

---

### Post by Kundan Negi on 2012-08-01
Does your system heats too much or u just want u view the temperature of system. Please specify.:o

---

### Post by gifford on 2012-08-01
lm-sensors with GKrellM works great for me. Monitors cpu's temp as well as HD. Nice graphical interface that allows customization for various other processes as well. Follow the info in the previous thread to activate.

---

### Post by robtygart on 2012-08-18
Is there a way to get it to read in Fahrenheit?


**EDIT:**
Nevermind I got it!

```
sensors -f
```

---

