---
title: "From lubuntu 13.10 to 14.04 nm-applet and wired connections doesn't work fine!"
date: 2014-04-25
forum: Installation &amp; Upgrades
---

### Post by ruoccocostruzioni on 2014-04-25
Hi.
I update from lubuntu 64bit 13.10 to 14.04.
I've an Acer Aspire 7738
No error occurred.

After reboot I found a grub error so i reinstall grub from live CD.

Then the panel doesn't show network manager.
I go into accessories -> default applications ->autostart
I've set config-only mode with:
  dropbox start -i
  end PULSE_LATENCY_MSEC=60 skype %U

than, I've add to that command, nm-applet: nm-applet icon does not appear on strart.

Than I make a wired connection with my USB device (samsung galaxy S2). The connection  is established.
But the wired network doen't work; only wifi connection go well (with an other device).
Before upgrading all was well.

This is output of my ifconfig:
```
eth0      Link encap:Ethernet  IndirizzoHW 00:1f:16:94:02:24  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6136 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:465008 (465.0 KB)  Byte TX:465008 (465.0 KB)

usb0      Link encap:Ethernet  IndirizzoHW 02:3c:31:64:6a:0c  
          indirizzo inet:192.168.42.231  Bcast:192.168.42.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::3c:31ff:fe64:6a0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:1726 (1.7 KB)  Byte TX:11310 (11.3 KB)

wlan0     Link encap:Ethernet  IndirizzoHW 00:22:fa:1f:37:be  
          indirizzo inet:192.168.1.100  Bcast:192.168.1.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::222:faff:fe1f:37be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20323 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15848 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:16862594 (16.8 MB)  Byte TX:3269236 (3.2 MB)
```

I try to config autostart applications; I setted to "no"  disable autostart applications.
I have the same problem and at house, I can't use wifi connections ](*,)

---

### Post by Rex Bouwense on 2014-04-25
Menu->Preferences->Default applications for LXSession.  Then navigate to Core Applications->Network GUI.  Type in nm-applet and then hit reload.

---

### Post by kalehrl on 2014-04-25
This works but after reboot, it doesn't.
You need to add 'nm-applet' in autostart for it to work after reboot.

---

### Post by Rex Bouwense on 2014-04-25
> **kalehrl said:**
> This works but after reboot, it doesn't.
You need to add 'nm-applet' in autostart for it to work after reboot.
I left that off, didn't I.  Sorry.

---

### Post by ruoccocostruzioni on 2014-04-27
Ok.
I not sure what's happens: into accessories -> default applications ->autostart I remake the no-config configuration.
I clear and re-add the nm-applet command mannually.

After reboot all go well!\\:D/

---

