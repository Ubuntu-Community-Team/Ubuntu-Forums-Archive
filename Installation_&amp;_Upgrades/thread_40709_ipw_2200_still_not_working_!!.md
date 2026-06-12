---
title: "ipw 2200 still not working !!"
date: 2005-06-10
forum: Installation &amp; Upgrades
---

### Post by ranger79 on 2005-06-10
Greetings !

First of all, I'm using Hoary and Acer TravelMate 290 for the installation and I've confirmed that it is a ipw2200 from my WinXP.

I've been following exactly like the how-to and suggestions given in [HOWTO: ipw2200 + wpa](http://www.ubuntuforums.org/showthread.php?t=26623). I decided to start another thread as the original one is too long and getting very difficult to read. 

Below is the sequence of events:
1) Follow steps in the above how-to. Ensure old drivers deleted. Driver compilation OK. Got "Firmware error detected.  Restarting." No luck here. Found out later that the PSK must be generated using wpa_passphrase. Still not working, however.

Got the following error:
------------------------------------------------------
hk@hk:~$ dmesg | grep ipw
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.4
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: Firmware error detected.  Restarting.
ipw2200: failed to send SYSTEM_CONFIG command
ipw2200: ipw_send_system_config failed
ipw2200: failed to send SSID command
ipw2200: failed to send ASSOCIATE command
ipw2200: failed to send SSID command
ipw2200: failed to send SSID command
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
------------------------------------------------------

2) Read another how-to [HOWTO: Automated WPA Encryption with ndiswrapper drivers](http://ubuntuforums.org/showthread.php?t=31418). Decided to give the older 1.0.3 and firmware 2.2 a try. Did not get the firmware error like the step 1.

------------------------------------------------------
hk@hk:~$ dmesg | grep ipw
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.3
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
------------------------------------------------------

However, wireless still not working. Got the following error by using the commands suggested in this how to. Hopefully some one can help me figure out.
------------------------------------------------------
hk@hk:~$ **sudo dhclient -r eth1 && ifconfig eth1 down && killall wpa_supplicant** 
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:0e:35:24:63:cd
Sending on   LPF/eth1/00:0e:35:24:63:cd
Sending on   Socket/fallback
SIOCSIFFLAGS: Permission denied
------------------------------------------------------
hk@hk:~$ **sudo ifconfig eth1 up && /usr/sbin/wpa_supplicant -w -Dipw -ieth1 -c/etc/wpa_supplicant.conf -dd**
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 5 - start of a new network block
ssid - hexdump_ascii(len=6):
     xx xx xx xx xx xx                                 xxxxxx
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='xxxxxx'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
ioctl[SIOCSIWMODE]: Operation not permitted
Could not configure driver to use managed mode
SIOCSIFFLAGS: Permission denied
Could not set interface 'eth1' UP
socket(PF_PACKET, SOCK_RAW): Operation not permitted
Waiting for interface..
socket(PF_PACKET, SOCK_RAW): Operation not permitted
Waiting for interface..
socket(PF_PACKET, SOCK_RAW): Operation not permitted
Waiting for interface..
socket(PF_PACKET, SOCK_RAW): Operation not permitted
Waiting for interface..
socket(PF_PACKET, SOCK_RAW): Operation not permitted
Waiting for interface..
socket(PF_PACKET, SOCK_RAW): Operation not permitted
Waiting for interface..
socket(PF_PACKET, SOCK_RAW): Operation not permitted
Waiting for interface..
socket(PF_PACKET, SOCK_RAW): Operation not permitted
Waiting for interface..
socket(PF_PACKET, SOCK_RAW): Operation not permitted
Waiting for interface..
socket(PF_PACKET, SOCK_RAW): Operation not permitted
Waiting for interface..
socket(PF_PACKET, SOCK_RAW): Operation not permitted
Waiting for interface..
socket(PF_PACKET, SOCK_RAW): Operation not permitted
Waiting for interface..
socket(PF_PACKET, SOCK_RAW): Operation not permitted
Waiting for interface..
socket(PF_PACKET, SOCK_RAW): Operation not permitted
Waiting for interface..
------------------------------------------------------

Attached below my /etc/wpa_supplicant.conf, which is the same regardless the version of the driver i used:
------------------------------------------------------
ctrl_interface=/var/run/wpa_supplicant

eapol_version=1

network={
       ssid="xxxxxx"
       proto=WPA
       key_mgmt=WPA-PSK
       #psk="secrect phrase"
       psk=generated key here
}
------------------------------------------------------

Below is the output of the iwconfig
------------------------------------------------------
hk@hk:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"xxxxxx"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
------------------------------------------------------

Can any one enlighten me on what could've gone wrong?

Thanks in advance.

Best regards,
Ranger79

---

### Post by ranger79 on 2005-06-10
I just realised that the AP at work that I've been trying to access may not have the WPA enabled.

According to [How To Upgrade the Driver for your IPW2200 Wireless Card](http://nickselby.com/articles/technology/?a=1807), the version 1.0.0 is possibly the most stable driver.

I've tried the steps in the above article and  I am now able to access my home AP (without any encryption).

With that success, I use the GUI tool to add the WEP key and it is working !!  \\:D/ 

I'm eager to try out at work next Monday  ;-)

---

### Post by ranger79 on 2005-06-13
Got the wireless working perfectly at work now.

Even install the wifi-radar and the gnome net applet. So far still have to do manual switching by editing the /etc/network/interfaces file. Will continue to find out how to do the automatic switching.

---

