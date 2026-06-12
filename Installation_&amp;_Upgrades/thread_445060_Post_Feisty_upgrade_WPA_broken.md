---
title: "Post Feisty upgrade WPA broken"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by greeners on 2007-05-15
Hi all,

Just when I though I would never have Wifi trouble again (after ditching FedoraCore and loading Ubuntu) I upgraded version 6 (working WPA) to version 7 (broken WPA).  I used the update manager in the System/Administration menu and clicked on the button telling me there was an upgrade to version 7 available (900 modules later it rebooted and no network)...

I'm a bit of a noob but not incapable.  I've got an Atheros chipset 3Com card which uses the Madwifi driver I beleive.

The system log extract when I try to associate with my access point are below so any comments would be very welcome:

May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): s=0 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): EAPOL: External notification - EAP fail=0 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): EAPOL: External notification - portControl=Auto 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): CTRL_IFACE monitor attached - hexdump(len=41): <snip> 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): Wireless event: cmd=0x8b1a len=17 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): Authentication with 00:00:00:00:00:00 timed out. 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): CTRL_IFACE monitor send - hexdump(len=41): <snip> 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): Added BSSID 00:00:00:00:00:00 into blacklist 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): State: ASSOCIATING -> DISCONNECTED 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): WEXT: Operstate: linkmode=-1, operstate=5 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): No keys have been configured - skip key clearing 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): EAPOL: External notification - portEnabled=0 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): EAPOL: External notification - portValid=0 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): Setting scan request: 0 sec 0 usec 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): State: DISCONNECTED -> SCANNING 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): Trying to associate with SSID 'chezcroft' 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): hexdump(len=41): <snip> 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): Cancelling scan request 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): WPA: clearing own WPA/RSN IE 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): Automatic auth_alg selection: 0x1 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): WPA: No WPA/RSN IE available from association info 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): WPA: Set cipher suites based on configuration 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): WPA: clearing AP WPA IE 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): WPA: clearing AP RSN IE 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): WPA: using GTK TKIP 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): WPA: using PTK TKIP 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): WPA: using KEY_MGMT WPA-PSK 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): WPA: Set own WPA IE default - hexdump(len=24): <snip> 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): No keys have been configured - skip key clearing 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): wpa_driver_madwifi_set_drop_unencrypted: enabled=1 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): State: SCANNING -> ASSOCIATING 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): WEXT: Operstate: linkmode=-1, operstate=5 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): wpa_driver_madwifi_associate 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): Setting authentication timeout: 60 sec 0 usec 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): EAPOL: External notification - EAP success=0 
May 15 20:13:24 laptop NetworkManager: <information>^Iwpa_supplicant(10125): EAPOL: External notification - EAP fail=0 
May 15 20:14:24 laptop NetworkManager: <information>^IActivation (ath0/wireless): association took too long (>120s), failing activation. 
May 15 20:14:24 laptop NetworkManager: <information>^IActivation (ath0) failure scheduled... 
May 15 20:14:24 laptop NetworkManager: <information>^IActivation (ath0) failed for access point (chezcroft) 
May 15 20:14:24 laptop NetworkManager: <information>^IActivation (ath0) failed. 
May 15 20:14:24 laptop NetworkManager: <information>^IDeactivating device ath0. 
May 15 20:14:24 laptop avahi-daemon[5767]: Withdrawing address record for fe80::20d:54ff:fef7:940d on ath0.
May 15 20:14:29 laptop avahi-daemon[5767]: Registering new address record for fe80::20d:54ff:fef7:940d on ath0.*.
May 15 20:14:38 laptop kernel: [ 3005.708000] ath0: no IPv6 routers present

---

### Post by flabdablet on 2007-05-20
Feisty broke my WPA wireless too.

For Dapper and Edgy, I had previously followed a recipe from Somewhere On The Internet for getting WPA working, which involved setting up /etc/wpa_supplicant.conf with something like

```
network={
        ssid="my-wlan-ssid"
        key_mgmt=WPA-PSK
        psk=ef98fa27f3a28...
}
```

and putting the following stanza in /etc/network/interfaces:

```
iface wlan0 inet dhcp
    pre-up wpa_supplicant -Bw -c /etc/wpa_supplicant.conf -i wlan0 -D wext
    post-down pkill wpa_supplicant
```

I was never really happy with this - it seemed a bit crude - but it worked OK for Dapper and Edgy.

I found a marginal improvement on this to make Feisty happy, and posted it here; but it was still crude as hell, and there's now a [much better way to do it]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/24295/comments/2").

So, I've now got rid of /etc/wpa_supplicant.conf entirely, and the wlan0 stanza of my /etc/network/interfaces file now looks like this:

```
iface wlan0 inet dhcp
    wpa-driver wext
    wpa-ssid my-wlan-ssid
    wpa-psk ef98fa27f3a28...
```

Here's hoping that the next version of the wireless configuration GUI understands WPA and WPA2 so we don't all have to keep jumping through these hoops!

---

### Post by handaxe on 2007-05-22
You could in the interim try out WIcd as your wireless connection manager.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

You can always re-install NM if you will, so nothing lost...

Wicd has worked for many folks in dealing with issues apparent under NM. That written, Wicd is not perfect and cannot help where there are fundamental problems between card/driver and "helper" progs like wpa_supplicant, iwlist etc.

HA

---

### Post by greeners on 2007-05-29
Thanks for taking time to reply, it is much appreciated.  I will take a look at WIcd.

I suspect that it will not work as the Feisty Fawn driver is broken and Ubuntu will be unusable until a new release is made of rt61pci.  I can download and compile up the rt61-1.1.0 driver but having already had a go at that wasn't very sucessful.  Even the C code needed a hack to make it compile with the Feisty Fawn 2.6 kernel.

---

