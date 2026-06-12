---
title: "wlan0: disassociating by local choice (reason=3)"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by David Gerard on 2009-04-12
I've just upgraded from Kubuntu Intrepid (with Kubuntu 4.2 PPA) to Jaunty. All appears to have gone well ... except a certain lack of wifi:

Apr 12 18:54:14 heidi kernel: [  139.758121] wlan0: direct probe to AP 00:18:4d:df:f1:e8 try 1
Apr 12 18:54:14 heidi kernel: [  139.761388] wlan0 direct probe responded
Apr 12 18:54:14 heidi kernel: [  139.761396] wlan0: authenticate with AP 00:18:4d:df:f1:e8
Apr 12 18:54:14 heidi kernel: [  139.765071] wlan0: authenticated
Apr 12 18:54:14 heidi kernel: [  139.765080] wlan0: associate with AP 00:18:4d:df:f1:e8
Apr 12 18:54:14 heidi kernel: [  139.772086] wlan0: RX AssocResp from 00:18:4d:df:f1:e8 (capab=0x11 status=0 aid=2)
Apr 12 18:54:14 heidi kernel: [  139.772092] wlan0: associated
Apr 12 18:54:14 heidi kernel: [  139.781517] wlan0: disassociating by local choice (reason=3)
Apr 12 18:54:16 heidi kernel: [  141.781101] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate

The wifi's Intel iwl3945.

Currently on wired Ethernet. This is more than a little bit of a pain in the backside ...

Any ideas?

Is there a list anywhere of what these "reasons" are?

---

### Post by newruler on 2009-04-14
I too have that same issue.  I am using Ubuntu Jaunty (gnome flavor), in my situation I have three AP's, two are open and one uses WPA.  I can connect and stay connected to two of the three.  Only one of the open AP's is giving me this issue.  It is my own AP that I have running in an old Soekris 4521 box.  I have two wireless cards in it, both pcmcia, one is Engenius EL-2011CD Plus Ext2, the other is a SMC 2532w-b.  I have set it to use both cards as an AP and neither one will work properly.  Occassionally I actually do connect but if I disconnect and try again it gives me the error you showed from syslog
here is a snippet from mine showing it's failure then ability to connect to another AP (in this case the one with WPA)

Apr 14 11:16:21 josh-laptop NetworkManager: <info>  Config: set interface ap_scan to 1 
Apr 14 11:16:21 josh-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected 
Apr 14 11:16:21 josh-laptop kernel: [ 1901.883123] wlan0: disassociating by local choice (reason=3)
Apr 14 11:16:21 josh-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Apr 14 11:16:21 josh-laptop kernel: [ 1901.889054] wlan0: authenticated
Apr 14 11:16:21 josh-laptop kernel: [ 1901.889063] wlan0: associate with AP 00:02:6f:01:ba:7d
Apr 14 11:16:21 josh-laptop kernel: [ 1901.892188] wlan0: RX AssocResp from 00:02:6f:01:ba:7d (capab=0x1 status=0 aid=1)
Apr 14 11:16:21 josh-laptop kernel: [ 1901.892193] wlan0: associated
Apr 14 11:16:21 josh-laptop kernel: [ 1901.902816] wlan0: disassociating by local choice (reason=3)
Apr 14 11:16:21 josh-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associated 
Apr 14 11:16:21 josh-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected 
Apr 14 11:16:36 josh-laptop NetworkManager: <info>  wlan0: link timed out. 
Apr 14 11:16:56 josh-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Apr 14 11:17:00 josh-laptop kernel: [ 1940.837697] wlan0: deauthenticated
Apr 14 11:17:00 josh-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Apr 14 11:17:00 josh-laptop kernel: [ 1940.843801] wlan0: authenticate with AP 00:1a:70:6a:d4:26
Apr 14 11:17:00 josh-laptop kernel: [ 1940.845632] wlan0: authenticated
Apr 14 11:17:00 josh-laptop kernel: [ 1940.845638] wlan0: associate with AP 00:1a:70:6a:d4:26
Apr 14 11:17:00 josh-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated 
Apr 14 11:17:00 josh-laptop kernel: [ 1940.849230] wlan0: RX AssocResp from 00:1a:70:6a:d4:26 (capab=0x411 status=0 aid=2)
Apr 14 11:17:00 josh-laptop kernel: [ 1940.849235] wlan0: associated
Apr 14 11:17:00 josh-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 14 11:17:00 josh-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 14 11:17:00 josh-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Apr 14 11:17:00 josh-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'PC

---

### Post by David Gerard on 2009-04-15
... and I have no idea why. But I did:

1. force an install of a KDE network-manager thing I forget the name of (I know this is less than helpful)

2. add the Network Manager widget to the panel

3. Try a Belkin PC card wifi. It then associated *both* wifis ...

Then I unplugged the PC card, and the internal wifi Just Worked.

o_0

---

### Post by MacUntu on 2009-04-15
Try to install the package linux-backports-modules-jaunty (it contains updated drivers).

---

### Post by syko21 on 2009-04-15
This bug has been recently documented by another member. Please post and expand on it here
[https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/361461](https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/361461)

the package is listed as wicd and it's a different card but the dmesg error is exactly the same so there might be some relation

---

