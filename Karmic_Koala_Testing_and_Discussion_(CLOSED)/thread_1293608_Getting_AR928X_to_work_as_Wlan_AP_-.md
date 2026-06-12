---
title: "Getting AR928X to work as Wlan AP :-/"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Harper04 on 2009-10-17
Hi i hope you guys can give me a hand :),
a week ago i bought a nano ITX Board with a AR928X chip integrated, i want to build a Wlan AP / Router / Mediaserver etc with it.

I installed Ubunut 9.10 on it and tried to make an AP with hostapd (9.2 in ubuntu repository),
My Problem is that after some time i lost connection and cant reconnect, if i turn wlan down before connection lost and try to reconnect it wont work too :(.

I also tried to compile the newest Version of hostapd (yesterday), and still got the same problems, mayby you can help me with this. I really need this wlan AP :( .

Please help me, mayby there's a hack or a working version :-/

this is my configuration file:

interface=wlan0
driver=nl80211
ssid=TomsWLan
hw_mode=g
channel=11
auth_algs=1 #1

ieee80211n=1
ht_capab=[HT40-][SHORT-GI-40][DSSS_CCK-40]

macaddr_acl=0

wpa=2 #2
wpa_passphrase=imbapass
wpa_key_mgmt=WPA-PSK
wpa_pairwise=CCMP

wme_enabled=0

This is a log from startup:
Oct 17 13:00:01 tom-desktop avahi-daemon[882]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.1.
Oct 17 13:00:01 tom-desktop avahi-daemon[882]: New relevant interface wlan0.IPv4 for mDNS.
Oct 17 13:00:01 tom-desktop avahi-daemon[882]: Registering new address record for 192.168.0.1 on wlan0.IPv4.
Oct 17 13:00:01 tom-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:15.0/0000:04:00.0/net/mon.wlan0, iface: mon.wlan0)
Oct 17 13:00:01 tom-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:15.0/0000:04:00.0/net/mon.wlan0, iface: mon.wlan0): no ifupdown configuration found.
Oct 17 13:00:03 tom-desktop avahi-daemon[882]: Registering new address record for fe80::224:23ff:fe08:f8ae on wlan0.*.
Oct 17 13:00:04 tom-desktop wpa_supplicant[1230]: CTRL-EVENT-SCAN-RESULTS 
Oct 17 13:00:04 tom-desktop wpa_supplicant[1230]: WPS-AP-AVAILABLE 

with console:
Configuration file: /etc/hostapd/hostapd.conf
Using interface wlan0 with hwaddr 00:24:23:08:f8:ae and ssid 'TomsWLan'
wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: authenticated
wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: associated (aid 1)
wlan0: STA 00:22:43:46:8d:d0 RADIUS: starting accounting session 4AD9A3B4-00000000
wlan0: STA 00:22:43:46:8d:d0 WPA: pairwise key handshake completed (RSN)

This is a log from first connection:
Oct 17 13:00:42 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: authentication OK (open system)
Oct 17 13:00:42 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-AUTHENTICATE.indication(00:22:43:46:8d:d0, OPEN_SYSTEM)
Oct 17 13:00:42 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-DELETEKEYS.request(00:22:43:46:8d:d0)
Oct 17 13:00:42 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: authenticated
Oct 17 13:00:42 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: association OK (aid 1)
Oct 17 13:00:42 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: associated (aid 1)
Oct 17 13:00:42 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-ASSOCIATE.indication(00:22:43:46:8d:d0)
Oct 17 13:00:42 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-DELETEKEYS.request(00:22:43:46:8d:d0)
Oct 17 13:00:42 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: event 1 notification
Oct 17 13:00:42 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: start authentication
Oct 17 13:00:42 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.1X: unauthorizing port
Oct 17 13:00:42 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: sending 1/4 msg of 4-Way Handshake
Oct 17 13:00:43 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: EAPOL-Key timeout
Oct 17 13:00:43 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: sending 1/4 msg of 4-Way Handshake
Oct 17 13:00:43 tom-desktop wpa_supplicant[1230]: WPA: No Ack bit in key_info
Oct 17 13:00:43 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: received EAPOL-Key frame (2/4 Pairwise)
Oct 17 13:00:43 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: sending 3/4 msg of 4-Way Handshake
Oct 17 13:00:43 tom-desktop wpa_supplicant[1230]: WPA: No Ack bit in key_info
Oct 17 13:00:43 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: received EAPOL-Key frame (4/4 Pairwise)
Oct 17 13:00:43 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.1X: authorizing port
Oct 17 13:00:43 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 RADIUS: starting accounting session 4AD9A3B4-00000000
Oct 17 13:00:43 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: pairwise key handshake completed (RSN)

Everythings working, i got internet!^^

now disconnecting from AP:
Could not set station 00:22:43:46:8d:d0 flags for kernel driver (errno=22).
wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: disassociated
Could not set station 00:22:43:46:8d:d0 flags for kernel driver (errno=22).
Station 00:22:43:46:8d:d0 trying to deauthenticate, but it is not authenticated.
Station 00:22:43:46:8d:d0 trying to deauthenticate, but it is not authenticated.


Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: event 2 notification
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.1X: unauthorizing port
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: disassociated
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-DISASSOCIATE.indication(00:22:43:46:8d:d0, 8)
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-DELETEKEYS.request(00:22:43:46:8d:d0)
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: event 2 notification
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.1X: unauthorizing port
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: disassociated
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-DISASSOCIATE.indication(00:22:43:46:8d:d0, 8)
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-DELETEKEYS.request(00:22:43:46:8d:d0)
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: event 2 notification
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.1X: unauthorizing port
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: disassociated
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-DISASSOCIATE.indication(00:22:43:46:8d:d0, 8)
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-DELETEKEYS.request(00:22:43:46:8d:d0)
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: event 2 notification
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.1X: unauthorizing port
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: disassociated
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-DISASSOCIATE.indication(00:22:43:46:8d:d0, 8)
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-DELETEKEYS.request(00:22:43:46:8d:d0)
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: event 2 notification
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.1X: unauthorizing port
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: disassociated
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-DISASSOCIATE.indication(00:22:43:46:8d:d0, 8)
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-DELETEKEYS.request(00:22:43:46:8d:d0)
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: event 2 notification
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.1X: unauthorizing port
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: disassociated
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-DISASSOCIATE.indication(00:22:43:46:8d:d0, 8)
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-DELETEKEYS.request(00:22:43:46:8d:d0)
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: event 2 notification
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.1X: unauthorizing port
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: disassociated
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-DISASSOCIATE.indication(00:22:43:46:8d:d0, 8)
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-DELETEKEYS.request(00:22:43:46:8d:d0)
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: event 3 notification
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.1X: unauthorizing port
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: deauthenticated
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-DEAUTHENTICATE.indication(00:22:43:46:8d:d0, 8)
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-DELETEKEYS.request(00:22:43:46:8d:d0)
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: handle_action - unknown action category 3 or invalid frame
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: handle_action - unknown action category 3 or invalid frame
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: handle_action - unknown action category 3 or invalid frame
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: handle_action - unknown action category 3 or invalid frame
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: handle_action - unknown action category 3 or invalid frame
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: handle_action - unknown action category 3 or invalid frame
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: handle_action - unknown action category 3 or invalid frame
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: handle_action - unknown action category 3 or invalid frame
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: handle_action - unknown action category 3 or invalid frame
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: handle_action - unknown action category 3 or invalid frame
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: handle_action - unknown action category 3 or invalid frame
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: handle_action - unknown action category 3 or invalid frame
Oct 17 13:05:18 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: handle_action - unknown action category 3 or invalid frame
Oct 17 13:05:22 tom-desktop wpa_supplicant[1230]: Failed to initiate AP scan.


now connecting:
wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: authenticated
wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: associated (aid 1)
wlan0: STA 00:22:43:46:8d:d0 RADIUS: starting accounting session 4AD9A3B4-00000001
wlan0: STA 00:22:43:46:8d:d0 WPA: pairwise key handshake completed (RSN)


Oct 17 13:05:26 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: authentication OK (open system)
Oct 17 13:05:26 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-AUTHENTICATE.indication(00:22:43:46:8d:d0, OPEN_SYSTEM)
Oct 17 13:05:26 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-DELETEKEYS.request(00:22:43:46:8d:d0)
Oct 17 13:05:26 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: authenticated
Oct 17 13:05:26 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: association OK (aid 1)
Oct 17 13:05:26 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: associated (aid 1)
Oct 17 13:05:26 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-ASSOCIATE.indication(00:22:43:46:8d:d0)
Oct 17 13:05:26 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-DELETEKEYS.request(00:22:43:46:8d:d0)
Oct 17 13:05:26 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: event 1 notification
Oct 17 13:05:26 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: start authentication
Oct 17 13:05:26 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.1X: unauthorizing port
Oct 17 13:05:26 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: sending 1/4 msg of 4-Way Handshake
Oct 17 13:05:26 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: EAPOL-Key timeout
Oct 17 13:05:26 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: sending 1/4 msg of 4-Way Handshake
Oct 17 13:05:26 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: received EAPOL-Key frame (2/4 Pairwise)
Oct 17 13:05:26 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: sending 3/4 msg of 4-Way Handshake
Oct 17 13:05:26 tom-desktop wpa_supplicant[1230]: WPA: No Ack bit in key_info
Oct 17 13:05:26 tom-desktop wpa_supplicant[1230]: WPA: No Ack bit in key_info
Oct 17 13:05:26 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: received EAPOL-Key frame (4/4 Pairwise)
Oct 17 13:05:26 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.1X: authorizing port
Oct 17 13:05:26 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 RADIUS: starting accounting session 4AD9A3B4-00000001
Oct 17 13:05:26 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: pairwise key handshake completed (RSN)

So far there seems to be no error but the client cant connect it just gives it up



IF i just wait unitl i lost connection i get:
wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: deauthenticated due to local deauth request

if i try to reconnect i get a lot of messages like this
Oct 17 11:45:12 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: authentication OK (open system)
Oct 17 11:45:12 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-AUTHENTICATE.indication(00:22:43:46:8d:d0, OPEN_SYSTEM)
Oct 17 11:45:12 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-DELETEKEYS.request(00:22:43:46:8d:d0)
Oct 17 11:45:12 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: authenticated
Oct 17 11:45:12 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: association OK (aid 1)
Oct 17 11:45:12 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 IEEE 802.11: associated (aid 1)
Oct 17 11:45:12 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-ASSOCIATE.indication(00:22:43:46:8d:d0)
Oct 17 11:45:12 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 MLME: MLME-DELETEKEYS.request(00:22:43:46:8d:d0)
Oct 17 11:45:12 tom-desktop hostapd: wlan0: STA 00:22:43:46:8d:d0 WPA: event 1 notification

---

### Post by Harper04 on 2009-10-18
No one able to help me? :-(

---

### Post by timeking on 2009-10-24
ath9k/hostapd combination is a disaster in karmic. i gave up after spending 2 weekends and installed 9.04 with backports - works, at least somehow.

---

### Post by timeking on 2009-10-25
After a misleading post and a lot of pain, my setup finally works. 
9.10 dev edition (server) drops connections, loses packets and performs otherwise unacceptable. Getting bleeding edge ath9k from linux-wireless doesn't help.
Eventually, I managed to get it to work with 9.04 + backports.
Few notes:
- hostapd config standard, nothing unusual;
- dnsmasq config standard;
- iptables config standard;
- WMM had to be disabled on one of the station laptops network card settings;
 
AP:
Pentium III-800 VIA Apollo 133, 640 MB RAM headless machine;
DWA-552 wireless (AR9223 chip inside);
 
Stations:
ASUS Eee 1005HAB (atheros card 11n); no setup required;
DELL Inspiron 1300 (broadcom card 11b/g); WMM had to be disabled
 
You may ask a question - why am I posting to an AR928X thread? Linux detects my card as AR928X...
 
Another interesting observation - appears as while 9.10 was working (in was for very short intervals), it was much faster than 9.04.

---

### Post by Harper04 on 2009-10-25
Well i dont think the problems under karmic are limited to just AR928X, actually i couldnt find anyone who got hostapd and ath9k working correctly on 9.10

Well okay i only found 4 guys trying it ;).


So you say connecting, reconnecting etc. works perfectly under 9.04 with backports enabled?, I'll try it tonight.

> Another interesting observation - appears as while 9.10 was working (in was for very short intervals), it was much faster than 9.04.
Mayby you could look into the config setting and modify ht_cap
( #ht_capab=[HT40-][SHORT-GI-20][SHORT-GI-40]), i modified the values to the output of a command (i believe iw, will search for it later) and got double speed

---

