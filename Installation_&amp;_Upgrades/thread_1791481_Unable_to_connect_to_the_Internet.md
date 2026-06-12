---
title: "Unable to connect to the Internet"
date: 2011-06-26
forum: Installation &amp; Upgrades
---

### Post by HarriU11-04 on 2011-06-26
I have installed Ubuntu 11.04 on a system (Details below) and it seems I can hardly do anything.

I installed on a laptop that already had Windows XP SP3, creating a dual boot machine with wubi. *DUAL BOOTING IS WORKING FINE* Sorry, hand must have slipped on the caps lock there....

1. How do I access SystemTools?
2. Using network manager, I added a connection for Mobile Broadband, and the connection seems to work, but I still cannot connect to the Internet. Note that previously the USB modem works fine in Windows.

Modem: Huawei E1556 from Claro (Caribbean)

Machine: Panasonic Toughbook CF30, dual processor. Harddisk has 5 partitions. Windows is on C:\, Ubuntu on G:\ as a wubi file.

If anyone can help, I would geatly appreciate it. Please note that currently, I can only access the internet via the Windows partition, which means if I have to download install new package(s) in Ubuntu to get this working, I'm stuck.


Harri

---

### Post by varunendra on 2011-06-27
Be cautious with your *CAPS LOCK* next time!:)

To add system tools, right-click on **Applications menu > Edit Menus > System Tools (in the left pane) > check Configuration editor **(others too if you wish).

What are the symptoms that make you think the connection is working? Please post the outputs of the following:
```
ifconfig
``````
route -n
```

---

### Post by HarriU11-04 on 2011-06-28
Thankx for the typing tip ;). I ran the commands. "route -n" showed an empty routing table. The other log files are attached. Thank you very much for offering to help!

Just one more point: the ISP provider at the moment is Claro (Caribbean), but in the next two days I will switch it to Vodafone UK mobile broadband.

---

### Post by varunendra on 2011-06-28
Copy-pasting your file contents to make it readable for all:

syslog.txt:
```
Jun 27 20:27:53 ubuntu NetworkManager[1032]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Jun 27 20:27:53 ubuntu NetworkManager[1032]: <warn> GSM connection failed: (32) Sending command failed: device is not enabled
Jun 27 20:27:53 ubuntu NetworkManager[1032]: <info> (ttyUSB0): device state change: 4 -> 9 (reason 1)
Jun 27 20:27:53 ubuntu NetworkManager[1032]: <info> Marking connection 'Cable & Wireless Default 1' invalid.
Jun 27 20:27:53 ubuntu NetworkManager[1032]: <warn> Activation (ttyUSB0) failed.
Jun 27 20:27:53 ubuntu NetworkManager[1032]: <info> (ttyUSB0): device state change: 9 -> 3 (reason 0)
Jun 27 20:27:53 ubuntu NetworkManager[1032]: <info> (ttyUSB0): deactivating device (reason: 0).
Jun 27 20:27:53 ubuntu modem-manager[1039]: <info>  Modem /org/freedesktop/ModemManager/Modems/1: state changed (connected -> disconnecting)
Jun 27 20:27:53 ubuntu modem-manager[1039]: <info>  Modem /org/freedesktop/ModemManager/Modems/1: state changed (disconnecting -> connected)
Jun 27 20:27:53 ubuntu NetworkManager[1032]: <info> disconnect failed: (32) The serial port is not open.
```

ifconfig.txt:
```
eth0      Link encap:Ethernet  HWaddr 00:0b:97:7c:24:d9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:87:3e:65  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


dmesg.txt:
```
[    0.559690] usbcore: registered new interface driver usbfs
[    0.559707] usbcore: registered new interface driver hub
[    0.559747] usbcore: registered new device driver usb
[    1.524043] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    1.904065] usb 2-2: new low speed USB device using uhci_hcd and address 2
[    2.122913] input: Fujitsu Component USB Touch Panel as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input4
[    2.123085] generic-usb 0003:0430:0530.0001: input,hidraw0: USB HID v1.00 Device [Fujitsu Component USB Touch Panel] on usb-0000:00:1d.0-2/input0
[    2.123108] usbcore: registered new interface driver usbhid
[    2.123110] usbhid: USB HID core driver
[    6.344073] usb 1-8: new high speed USB device using ehci_hcd and address 4
[   10.462195] usb 1-8: USB disconnect, address 4
[   10.732059] usb 1-8: new high speed USB device using ehci_hcd and address 5
[   10.979319] usb 1-8: USB disconnect, address 5
[   15.336079] usb 1-8: new high speed USB device using ehci_hcd and address 6
[   17.072318] usbcore: registered new interface driver uas
[   17.095950] scsi9 : usb-storage 1-8:1.3
[   17.106482] scsi10 : usb-storage 1-8:1.4
[   17.120948] usbcore: registered new interface driver usb-storage
[   17.219463] usbcore: registered new interface driver usbserial
[   17.219576] usbcore: registered new interface driver usbserial_generic
[   17.219579] usbserial: USB Serial Driver core
[   17.350496] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB0
[   17.356346] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB1
[   17.360282] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB2
[   17.361991] usbcore: registered new interface driver option
[   19.428489] usb 1-8: USB disconnect, address 6
[   19.708054] usb 1-8: new high speed USB device using ehci_hcd and address 7
[   19.859759] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB0
[   19.956677] usb 1-8: USB disconnect, address 7
[   24.356060] usb 1-8: new high speed USB device using ehci_hcd and address 8
[   24.505392] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB0
[   24.507187] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB1
[   24.508898] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB2
[   24.514581] scsi15 : usb-storage 1-8:1.3
[   24.520195] scsi16 : usb-storage 1-8:1.4
[  285.805376] usb 1-8: USB disconnect, address 8
[  294.824081] usb 1-8: new high speed USB device using ehci_hcd and address 9
[  294.972167] scsi17 : usb-storage 1-8:1.0
[  294.972829] scsi18 : usb-storage 1-8:1.1
[  295.716989] usb 1-8: USB disconnect, address 9
[  302.608081] usb 1-8: new high speed USB device using ehci_hcd and address 10
[  302.756946] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB0
[  302.757556] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB1
[  302.758088] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB2
[  302.758851] scsi22 : usb-storage 1-8:1.3
[  302.760344] scsi23 : usb-storage 1-8:1.4
```

So dmesg shows the usb modem is detected properly, still the connection is failing (syslog). While adding the connection for your modem, did you get relevant options to choose from? Can you confirm that the final settings for the connection are same as those appear in windows (number, APN, anything else if applicable)?

---

### Post by HarriU11-04 on 2011-06-29
> **varunendra said:**
> While adding the connection for your modem, did you get relevant options to choose from? Can you confirm that the final settings for the connection are same as those appear in windows (number, APN, anything else if applicable)?

Well spotted, because I was *not* offered relevant settings when adding the connection for the modem. The modem was from Claro, but the choices on offer were Digicel or Cable & Wireless.

Since then I have switched to using a modem from Vodafone UK (because I and the machine are now physically in the UK now). Vodafone UK was offered and I chose "Topup and Go" APN. Still no joy. Copied below is the new syslog. It appears the modem hangs up in the middle of pppd configuration?

```

Jun 29 18:22:35 ubuntu NetworkManager[984]: <info> (ttyUSB0): device state change: 2 -> 3 (reason 0)
Jun 29 18:22:48 ubuntu gdm-session-worker[1246]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jun 29 18:22:56 ubuntu rtkit-daemon[1256]: Successfully made thread 1465 of process 1465 (n/a) owned by '1000' high priority at nice level -11.
Jun 29 18:22:56 ubuntu rtkit-daemon[1256]: Supervising 4 threads of 2 processes of 2 users.
Jun 29 18:22:56 ubuntu rtkit-daemon[1256]: Successfully made thread 1466 of process 1465 (n/a) owned by '1000' RT at priority 5.
Jun 29 18:22:56 ubuntu rtkit-daemon[1256]: Supervising 5 threads of 2 processes of 2 users.
Jun 29 18:22:56 ubuntu rtkit-daemon[1256]: Successfully made thread 1467 of process 1465 (n/a) owned by '1000' RT at priority 5.
Jun 29 18:22:56 ubuntu rtkit-daemon[1256]: Supervising 6 threads of 2 processes of 2 users.
Jun 29 18:23:08 ubuntu kernel: [   59.177710] UDF-fs: Filesystem marked read-only because writing to pseudooverwrite partition is not implemented.
Jun 29 18:23:08 ubuntu kernel: [   59.206959] UDF-fs INFO UDF: Mounting volume 'UDF Volume', timestamp 2011/05/31 16:30 (1f10)
Jun 29 18:27:23 ubuntu anacron[949]: Job `cron.daily' started
Jun 29 18:27:23 ubuntu anacron[1978]: Updated timestamp for job `cron.daily' to 2011-06-29
Jun 29 18:28:23 ubuntu NetworkManager[984]: user_connection_updated_cb: assertion `old_connection != NULL' failed
Jun 29 18:28:23 ubuntu NetworkManager[984]: <info> Activation (ttyUSB0) starting connection 'Vodafone TopUp and Go'
Jun 29 18:28:23 ubuntu NetworkManager[984]: <info> (ttyUSB0): device state change: 3 -> 4 (reason 0)
Jun 29 18:28:23 ubuntu NetworkManager[984]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 29 18:28:23 ubuntu NetworkManager[984]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Jun 29 18:28:23 ubuntu NetworkManager[984]: <info> (ttyUSB0): device state change: 4 -> 6 (reason 0)
Jun 29 18:28:23 ubuntu NetworkManager[984]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Jun 29 18:28:23 ubuntu NetworkManager[984]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 29 18:28:23 ubuntu NetworkManager[984]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Jun 29 18:28:23 ubuntu NetworkManager[984]: <info> (ttyUSB0): device state change: 6 -> 4 (reason 0)
Jun 29 18:28:23 ubuntu NetworkManager[984]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Jun 29 18:28:23 ubuntu modem-manager[1015]: <info>  (ttyUSB0) opening serial port...
Jun 29 18:28:23 ubuntu modem-manager[1015]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (disabled -> enabling)
Jun 29 18:28:23 ubuntu modem-manager[1015]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabling -> enabled)
Jun 29 18:28:23 ubuntu NetworkManager[984]: <info> WWAN now enabled by management service
Jun 29 18:28:23 ubuntu modem-manager[1015]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabled -> registered)
Jun 29 18:28:23 ubuntu modem-manager[1015]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (registered -> connecting)
Jun 29 18:28:23 ubuntu modem-manager[1015]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (connecting -> connected)
Jun 29 18:28:23 ubuntu NetworkManager[984]: <info> Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled...
Jun 29 18:28:23 ubuntu NetworkManager[984]: <info> Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting...
Jun 29 18:28:23 ubuntu NetworkManager[984]: <info> (ttyUSB0): device state change: 4 -> 5 (reason 0)
Jun 29 18:28:23 ubuntu NetworkManager[984]: <info> Activation (ttyUSB0) Stage 2 of 5 (Device Configure) successful.
Jun 29 18:28:23 ubuntu NetworkManager[984]: <info> Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 29 18:28:23 ubuntu NetworkManager[984]: <info> Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete.
Jun 29 18:28:23 ubuntu NetworkManager[984]: <info> Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) started...
Jun 29 18:28:23 ubuntu NetworkManager[984]: <info> (ttyUSB0): device state change: 5 -> 7 (reason 0)
Jun 29 18:28:23 ubuntu NetworkManager[984]: <info> starting PPP connection
Jun 29 18:28:23 ubuntu NetworkManager[984]: <info> pppd started with pid 2032
Jun 29 18:28:23 ubuntu NetworkManager[984]: <info> Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) complete.
Jun 29 18:28:23 ubuntu pppd[2032]: Plugin /usr/lib/pppd/2.4.5/nm-pppd-plugin.so loaded.
Jun 29 18:28:23 ubuntu pppd[2032]: pppd 2.4.5 started by root, uid 0
Jun 29 18:28:23 ubuntu pppd[2032]: Using interface ppp0
Jun 29 18:28:23 ubuntu pppd[2032]: Connect: ppp0 <--> /dev/ttyUSB0
Jun 29 18:28:23 ubuntu NetworkManager[984]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jun 29 18:28:23 ubuntu NetworkManager[984]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jun 29 18:28:23 ubuntu pppd[2032]: CHAP authentication succeeded
Jun 29 18:28:23 ubuntu pppd[2032]: CHAP authentication succeeded
Jun 29 18:28:24 ubuntu kernel: [  374.732234] PPP BSD Compression module registered
Jun 29 18:28:24 ubuntu kernel: [  374.753743] PPP Deflate Compression module registered
Jun 29 18:28:25 ubuntu pppd[2032]: Modem hangup
Jun 29 18:28:25 ubuntu pppd[2032]: Connection terminated.
Jun 29 18:28:25 ubuntu avahi-daemon[905]: Withdrawing workstation service for ppp0.
Jun 29 18:28:25 ubuntu NetworkManager[984]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jun 29 18:28:25 ubuntu modem-manager[1015]: <info>  (ttyUSB0) closing serial port...
Jun 29 18:28:25 ubuntu modem-manager[1015]: <info>  (ttyUSB0) serial port closed
Jun 29 18:28:26 ubuntu pppd[2032]: Exit.
Jun 29 18:28:26 ubuntu NetworkManager[984]: <warn> pppd pid 2032 exited with error: A modem hung up the phone
Jun 29 18:28:44 ubuntu NetworkManager[984]: <warn> pppd timed out or didn't initialize our dbus module

```

---

### Post by varunendra on 2011-06-30
Confirm your plan, dialing no and APN from your service provider.
In India here, sometimes I needed to explicitly declare the network type as '3G (UMTS/HSPA)' and to disable the roaming mode (clearing the check-box below network type). This can also be confirmed with the service provider.

Beyond this, any suggestions from me would be just 'shots in the dark'. Like - 'try changing compression settings in ppp settings' since the modem hangs while registering those modules.

---

### Post by HarriU11-04 on 2011-07-03
Thanks for all your advice and help. I finally resolved this, by a combination of luck and searching the internet for solutions.

Just a note: betavine/VMC/BCM is absolutely USELESS since the first line in the install instructions is that you need a working Internet connection, in order to download it *and* its dependencies.

System: K3565 Vodafone UK USB 3G modem, on Ubuntu 11.04 (natty narwhal). Configured as a dual boot machine (Windows XP SP3) -  I was getting tired of switching between windows to search for solutions and store webpages, then ubuntu to try out the advice/suggestions

1. One basic problem was there is no DNS resolution with this modem (K3565) sometimes - there was a reference to this fact somewhere. Note: I always booted into linux with the modem already attached. It always recognised the modem and connected to it. So you have create or edit /etc/resolv.conf and put in the DNS servers there. Something like:

e.g.        [FONT=Courier New]nameserver 123.45.678.908
[/FONT]
To find your DNS server, in Windows with the modem connected, in a command prompt, do 
[FONT=Courier New]ipconfig /all[/FONT]

2. In NetworkManager, you need the correct settings, in my case APN was wrong (ppbundle.internet). In my case, should pp.internet.

Find the correct APN:
[http://ubuntuforums.org/showthread.php?t=1484806](http://ubuntuforums.org/showthread.php?t=1484806)

Other NetworkManager settings:
IPv4 tab. Automatic (PPP) addresses only. Set DNS servers here too, separated by a comma
Mobile Broadband tab 
    Basic section. Number: *99#   Username: web   Password: web
    Advanced section. APN: pp.internet

"Connect automatically" and "Available to all users" were selected

---

### Post by varunendra on 2011-07-03
Hi,
Thanks for sharing the solution. I just want to add something for those facing such issues for the first time-

[LIST=1]
[*]Manually putting a DNS IP in /etc/resolv.conf or putting the same through Network Manager are same things (one automatically does the other).
[*]If you put it manually in /etc/resolv.conf file, then you may need to restart NetworkManager to reflect the change in it.
[*]AFAIK, regardless of whether or not you have a working internet connection, resolv.conf file is always expected to already exist in /etc directory, so there should be no need to create it. And of-course you need root privileges to edit it (e.g. **gksu gedit /etc/resolv.conf**)
[*]In order to confirm if the DNS settings (manual or automatic) are saved and effective, the command **route -n** should reflect the configured DNS IP.
[/LIST]
Hope your solutions help someone saving their time and avoid frustration.

---

### Post by HarriU11-04 on 2011-07-06
Thanks for your tips. Jus t a couple more points

Re point #3, resolv.conf was not created/initialized when I installed ubuntu. This is a know issue with K3565 modems and ubuntu. Generally I use "sudo vi" because I'm comfortable with the vi editor.

Also, I had to run pppconfig (under sudo) and configure a connection in there as well. Phew!

Now I just to setup Dansguardian, squid and iptables (stage 2), then install VMWare for linux (stage 3), and put an image of my Windows machine onto it. Gotta a long road ahead of me.....

---

