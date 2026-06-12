---
title: "Ubuntu 11.10 won't connect wired connection"
date: 2012-08-14
forum: Installation &amp; Upgrades
---

### Post by flyingfisch on 2012-08-14
I installed Ubuntu 11.10 on my Dell Optiplex 745 today. I could not connect to the internet with the LiveCD, but I installed it anyway. It still doesn't work. This is the first time linux has been installed on this computer. Windows XP connects with no problem.

I have a Broadcom NetXtreme 57xx Gigabit Controller.

I have tried removing Network Manager and using dhclient but it doesn't work either.


EDIT:
I also tried
  
  ```
modprobe tg3
```and then
  
  ```
dhclient eth0
```The last command runs forever. I dont know if thats good or bad. when i do
  
  ```
ping google.com
```  or try to open a page with firefox, i get a connection error.

  EDIT:

  ok.lspci output: 

```
flyingfisch@Office-OptiPlex-745:~$ lspci
    00:00.0 Host bridge: Intel Corporation 82Q963/Q965 Memory Controller Hub (rev 02)
    00:01.0 PCI bridge: Intel Corporation 82Q963/Q965 PCI Express Root Port (rev 02)
    00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
    00:02.1 Display controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
    00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
    00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
    00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
    00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
    00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
    00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
    00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
    00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
    00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
    00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
    00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
    00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
    00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
    00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
    00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
    03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)
```

 EDIT2:
  I don't know, maybe i am not running tg3 correctly?
  When i run modprobe tg3, it does not run forever. It just finishes with no output. Like this:
  ```
# modprobe tg3 
# _ 
```dhclient loops forever though. Is that OK?

---

### Post by flyingfisch on 2012-08-14
Bump.

Note to mods:

If I am bumping too early, please remove this post ;)

---

### Post by flyingfisch on 2012-08-15
bump?

EDIT:

I booted the Ubuntu 12.04 LiveCD and it still cannot connect to the internet. I did "modprobe tg3" and it didn't seem to do anything. What should I do?

---

### Post by niaxilin on 2012-09-03
I had a problem getting the NetXtreme BCM5754 to load when I moved my Ubuntu 12.04 hard drive to another system. It turned out that the NetXtreme jumped to eth1, and I had to enable eth1 (instead of eth0) in the **/etc/network/interfaces** configuration.

Or instead, I found out I could just delete **/etc/udev/rules.d/70-persistent-net.rules** and upon reboot and the system forgot about the old controller and inserted the BCM5754 as eth0. Voila!

PS. The **tg3** driver was correct.

---

