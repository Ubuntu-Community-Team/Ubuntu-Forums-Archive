---
title: "Shutdown problem with netbook version 10.10"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by click66 on 2010-11-27
Hi guys,

I've just bought a new netbook, downloaded the ubuntu 10.10 netbook edition, created a usb file and installed as windows program. 

There is just one problem and that is when I shutdown my netbook i get this error:

Broadcast message from root@ubuntu
     (unknown) at 12:56... 

The system is going down for halt now!
177.768071 phy0 rt2800_wait_wpdma_ready: error WPDMA TX/RX Busy, aborting.
177.911842 phy0 rt2x00pci_regbusy_read: error indirect register access failed: offset=0x00007010, value=0xffffffff

and he doesn't shutdown.

What can i do to fix this?

Thanks in advantage,

---

### Post by jmwilli25 on 2010-11-29
I too have this same issue. I am fairly sure that it has something to do with the wireless shutting down. What computer do you have? I have a Compaq Mini cq10-405dx.
The reason I think it is the wireless is because my computer also completely freezes if I push the wireless button (to turn it on or off).

---

### Post by WrightPC on 2010-12-04
I found my answer [here]("https://answers.launchpad.net/ubuntu/+question/132350").
Add "blacklist rt2800pci" to "/etc/modprobe.d/blacklist-wlan.conf" with the following command:
```
sudo echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist-wlan.conf
```then reboot. 

Suspend to Ram works reliably.
Hibernate to disk works reliably.
Random boot failures have disappeared.

All is well.

---

### Post by click66 on 2010-12-04
Thanks works fine :)

---

### Post by WrightPC on 2010-12-04
Please mark the thread as [Solved]

---

### Post by dunc47 on 2010-12-13
Many thanks for this it worked on my MSI netbook where I was having the same problem including the freeze on wireless switch op.

---

### Post by gachora on 2011-01-01
Thnx so much it works perfect! happy new year to all):P

---

### Post by Serson_Person on 2011-01-06
> **WrightPC said:**
> I found my answer [here]("https://answers.launchpad.net/ubuntu/+question/132350").
Add "blacklist rt2800pci" to "/etc/modprobe.d/blacklist-wlan.conf" with the following command:
```
sudo echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist-wlan.conf
```then reboot. 

Suspend to Ram works reliably.
Hibernate to disk works reliably.
Random boot failures have disappeared.

All is well.



Hi, I'm sure this post is older but it looks like what I need to do, however when I type the line in the terminal is says "Permission Denied"

Know any way past this?

---

### Post by BunTai on 2011-03-29
> **Serson_Person said:**
> Hi, I'm sure this post is older but it looks like what I need to do, however when I type the line in the terminal is says "Permission Denied"

Know any way past this?

you need to do like this :

You need to have both modules available in order to be able to switch. Check this in a terminal by typing:

lspci -k|grep -i network --after-context 3
03:00.0 Network controller: RaLink RT2860
 Subsystem: Foxconn International, Inc. Device e002
 Kernel driver in use: rt2800pci
 Kernel modules: rt2800pci, rt2860sta

Here, rt2800pci and rt2860sta are both available, while rt2800pci is in use.

Make a file that allows you to easily switch between the two driver modules. For this open a terminal and then open nano by typing:
sudo nano /etc/modprobe.d/blacklist-wlan.conf
Write this two lines in nano:
blacklist rt2800pci
#install rt2860sta /bin/false

Save this (ctrl+O; return; ctrl+X).
If you now shut down and boot your system will then use the rt2860sta.

If, on the other hand, you want to make sure that the rt2860sta does _not_ get used, comment out the other line
sudo nano /etc/modprobe.d/blacklist-wlan.conf
#blacklist rt2800pci
install rt2860sta /bin/false
(Don't forget to save.)
If you now shut down and boot your system will then use the rt2800pci.

The "#" makes everything behind it a comment. It is ignored.

Why not just write blacklist rt2860sta?
A blacklisted module can still be pulled into use under certain circumstances. With the install rt2860sta /bin/false line we can prevent the rt2860sta from ever loading. Such stronger means have so far not turned out to be necessary with the other module.
What does this install line do?
It tells the system that whenever rt2860sta is to be loaded, the command /bin/false is to be executed instead.
What does /bin/false do?
false is a command on your system. So you can find out what it does by typing man false in a terminal.

source : [https://answers.launchpad.net/ubuntu/+question/132350](https://answers.launchpad.net/ubuntu/+question/132350)

---

