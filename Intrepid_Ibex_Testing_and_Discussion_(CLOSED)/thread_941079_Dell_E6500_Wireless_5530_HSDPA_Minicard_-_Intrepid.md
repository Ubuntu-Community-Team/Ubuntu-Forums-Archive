---
title: "Dell E6500 Wireless 5530 HSDPA Minicard - Intrepid"
date: 2008-10-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by craigmain on 2008-10-07
After a long night of fighting I finally solved this problem. The solution is as follows:

Turn on the RF Circuit Power :-)

```

AT+CFUN=1

```

To make it easier, this is what I have done:

1) Install Kernel Source
2) Patch options.c with [http://markmail.org/message/bidokb5yg34akroh]("http://markmail.org/message/bidokb5yg34akroh")
3) Compile the module
```

make -C /lib/modules/2.6.27-6-generic/build M=/usr/src/linux-source-2.6.27/drivers/usb/serial/

```
4) Copy /usr/src/linux-source-2.6.27/drivers/usb/serial/option.ko to /lib/modules/2.6.27-6-generic/kernel/drivers/usb/serial/option.ko
5) Create /etc/modprobe.d/blacklist-acm
```

# Don't load cdc-acm 
blacklist cdc-acm

```
6) Add ```
option
``` to /etc/modules
7) Create a /etc/wvdial.conf file
```

[Dialer Defaults]
New PPPD = yes
Stupid Mode = 1

[Dialer pin]
Modem = /dev/ttyUSB10
Init1 = AT+CPIN=<put your pin here>

[Dialer On]
Modem = /dev/ttyUSB10
Init1 = AT+CFUN=1

[Dialer Off]
Modem = /dev/ttyUSB10
Init1 = AT+CFUN=4

[Dialer 5530]
Init1 = AT 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Modem = /dev/ttyUSB10
Baud = 460800
ISDN = 0
Phone = *99***1#
Password = password
Username = username


```
8) Run "wvdial pin" to unlock your sim
9) Run "wvdial On" to turn on the RF power (wait a few seconds for it to register on the network)
10) Run "wvdial 5530" to connect to the net
11) ^C to disconnect
12) Run "wvdial Off" to turn off the RF power to save power

And thats it :-)

Hi All,

I have recently got a Dell E6500 which has a 5530 HSDPA GSM card.

I have patched the kernel option.c file with [http://markmail.org/message/bidokb5yg34akroh]("http://markmail.org/message/bidokb5yg34akroh")

dmesg now shows:
> [  752.584412] usbserial: USB Serial support registered for GSM modem (1-port)
[  752.584530] option 8-6:1.0: GSM modem (1-port) converter detected
[  752.584905] usb 8-6: GSM modem (1-port) converter now attached to ttyUSB0
[  752.584939] option 8-6:1.1: GSM modem (1-port) converter detected
[  752.585180] usb 8-6: GSM modem (1-port) converter now attached to ttyUSB1
[  752.585217] option 8-6:1.2: GSM modem (1-port) converter detected
[  752.585432] usb 8-6: GSM modem (1-port) converter now attached to ttyUSB2
[  752.585465] option 8-6:1.3: GSM modem (1-port) converter detected
[  752.585695] usb 8-6: GSM modem (1-port) converter now attached to ttyUSB3
[  752.585730] option 8-6:1.4: GSM modem (1-port) converter detected
[  752.585950] usb 8-6: GSM modem (1-port) converter now attached to ttyUSB4
[  752.585987] option 8-6:1.5: GSM modem (1-port) converter detected
[  752.586214] usb 8-6: GSM modem (1-port) converter now attached to ttyUSB5
[  752.586250] option 8-6:1.6: GSM modem (1-port) converter detected
[  752.586476] usb 8-6: GSM modem (1-port) converter now attached to ttyUSB6
[  752.586513] option 8-6:1.7: GSM modem (1-port) converter detected
[  752.586767] usb 8-6: GSM modem (1-port) converter now attached to ttyUSB7
[  752.586800] option 8-6:1.8: GSM modem (1-port) converter detected
[  752.587011] usb 8-6: GSM modem (1-port) converter now attached to ttyUSB8
[  752.587044] option 8-6:1.9: GSM modem (1-port) converter detected
[  752.587278] usb 8-6: GSM modem (1-port) converter now attached to ttyUSB9
[  752.587315] option 8-6:1.10: GSM modem (1-port) converter detected
[  752.587530] usb 8-6: GSM modem (1-port) converter now attached to ttyUSB10
[  752.587607] usbcore: registered new interface driver option
[  752.587612] option: USB Driver for GSM modems: v0.7.2


When I try to connect however, I get the following in syslog:
> Oct  8 00:17:05 f3021114-E6500 NetworkManager: <info>  Activation (ttyUSB0) starting connection 'Vodacom' 
Oct  8 00:17:05 f3021114-E6500 NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 
Oct  8 00:17:05 f3021114-E6500 NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct  8 00:17:05 f3021114-E6500 NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started... 
Oct  8 00:17:05 f3021114-E6500 NetworkManager: <debug> [1223417825.116360] nm_serial_device_open(): (ttyUSB0) opening device... 
Oct  8 00:17:05 f3021114-E6500 NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete. 
Oct  8 00:17:16 f3021114-E6500 NetworkManager: <WARN>  init_done(): Modem initialization timed out 
Oct  8 00:17:16 f3021114-E6500 NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 9 
Oct  8 00:17:16 f3021114-E6500 NetworkManager: <debug> [1223417836.470457] nm_serial_device_close(): Closing device 'ttyUSB0' 
Oct  8 00:17:16 f3021114-E6500 NetworkManager: <info>  Marking connection 'Vodacom' invalid. 
Oct  8 00:17:16 f3021114-E6500 NetworkManager: <info>  Activation (ttyUSB0) failed. 
Oct  8 00:17:16 f3021114-E6500 NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 
Oct  8 00:17:16 f3021114-E6500 NetworkManager: <info>  (ttyUSB0): deactivating device. 
Oct  8 00:17:16 f3021114-E6500 NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Oct  8 00:17:16 f3021114-E6500 NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed


If I connect to /dev/ttyUSB0 via minicom, and issue ATZ, I get ERROR returned.

Has anyone been able to get one of these cards working?

Thanks
Craig

---

### Post by geek65535 on 2008-10-28
Thanks for the info. I was able to plug in your /etc/wvdial.conf, and was up and running in no time.

Now, on to the built-in gps receiver! Have you gotten it to work?

paul

---

### Post by craigmain on 2008-10-29
> **geek65535 said:**
> Thanks for the info. I was able to plug in your /etc/wvdial.conf, and was up and running in no time.

Now, on to the built-in gps receiver! Have you gotten it to work?

paul

Glad it helped :-)

As for the gps receiver, I'm still investigating....

C

---

