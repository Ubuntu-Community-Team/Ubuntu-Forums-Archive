---
title: "Huge network problems in alpha6 release"
date: 2009-09-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by slakkie on 2009-09-20
Hello to all,

I'm having serious problems with my networking after the alpha6 upgrade (from alpha4).

I've first disabled the netbase upgrade because I suspected the upstart job to cause problems. Then I've disabled the wpasupplicant upgrade as well, but while keeping both at the same level as alpha4. But no dice.

I have no wireless at all, it doesn't see my network (which can be seen when running alpha4). I only have a wired connection.
 
My interfaces file:
```

# Our various networks, both work and home
mapping eth0
    script guessnet-ifupdown
    map default: missing-cable
    map verbose: false
    map debug: false
    map work-fixed home-fixed2 home-fixed aruba-vrolijk missing-cable

iface aruba-vrolijk inet dhcp
    test peer address 192.168.1.1 mac 00:08:5C:89:0A:81 source 192.168.1.4
    dns-domain euronet.nl
    dns-search euronet.nl wanadoo.nl online.nl sf6800.euronet.nl euro.net

iface work-fixed inet static
    test peer address 194.134.x.x mac 00:00:0C:xx:xx:xx source 194.134.x.x
    address 194.134.x.x
    netmask 255.255.255.0
    gateway 194.134.x.x
    dns-domain euronet.nl
    dns-search euronet.nl orange.nl wanadoo.nl online.nl sf6800.euronet.nl euro.net
    dns-nameservers 194.134.5.5 194.134.0.97
    metric 1
    post-up /home/wesleys/bin/mount_smb start
    pre-down /home/wesleys/bin/mount_smb stop

iface home-fixed2 inet static
    test peer address 192.168.1.254 mac 00:24:17:47:FA:BA source 192.168.1.14
    address 192.168.1.14
    netmask 255.255.255.0
    gateway 192.168.1.254
    dns-domain opperschaap.net
    dns-search opperschaap.net euronet.nl wanadoo.nl online.nl
    dns-nameservers 194.134.5.5 194.134.0.97
    metric 1

iface home-fixed inet static
    test peer address 192.168.1.1 mac 00:60:4C:CC:86:39 source 192.168.1.14
    address 192.168.1.14
    netmask 255.255.255.0
    gateway 192.168.1.1
    dns-domain opperschaap.net
    dns-search opperschaap.net euronet.nl wanadoo.nl online.nl
    dns-nameservers 194.134.5.5 194.134.0.97
    metric 1

mapping wlan0
    script guessnet-ifupdown
    map default: missing-cable
    map verbose: true
    map debug: true
    map work-wifi home-wifi home-wifi2 wifi-open missing-cable

iface wifi-open inet dhcp
    wireless-essid any
    test wireless open
    dns-domain opperschaap.net
    dns-search opperschaap.net euronet.nl wanadoo.nl online.nl
    dns-nameservers 194.134.5.5 194.134.0.97

iface work-wifi inet dhcp
    test wireless essid "Online Wireless"
    dns-domain euronet.nl
    dns-search euronet.nl orange.nl wanadoo.nl online.nl sf6800.euronet.nl euro.net
    dns-nameservers 194.134.5.5 194.134.0.97
    metric 2

iface home-wifi inet static
    test wireless essid wnl.opperschaap.net
    address 192.168.1.114
    netmask 255.255.255.0
    gateway 192.168.1.1
    dns-domain opperschaap.net
    dns-search opperschaap.net euronet.nl wanadoo.nl online.nl
    dns-nameservers 194.134.5.5 194.134.0.97
    mtu 1940
    metric 20

iface home-wifi2 inet static
    test wireless essid wnl2.opperschaap.net
    address 192.168.1.114
    netmask 255.255.255.0
    gateway 192.168.1.254
    dns-domain opperschaap.net
    dns-search opperschaap.net euronet.nl wanadoo.nl online.nl
    dns-nameservers 194.134.5.5 194.134.0.97
    metric 20

```

My wpa_supplicant file:
```

#
#  Please see /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz
#  for more complete configuration parameters.
#
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1
country=NL
device_name=eniac

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
  key_mgmt=NONE
  priority=1
}

network={
  ssid="wnl.opperschaap.net"
  scan_ssid=1
  proto=WPA
  key_mgmt=WPA-PSK
  pairwise=TKIP
  psk=mysupersecretpasswd
  priority=2
}

network={
  ssid="wnl2.opperschaap.net"
  scan_ssid=1
  #key_mgmt=WPA-PSK
  #proto=WPA RSN
  #pairwise=CCMP TKIP
  #group=CCMP TKIP
  psk=mysupersecretpasswd
  priority=5
}

```

I have a general stop/start script for my networking part, which worked fine until alpha6:

```

#!/bin/bash

INT="eth0 wlan0"

stop() {
    /etc/init.d/networking stop
    /etc/init.d/wpa.sh stop
    /etc/init.d/ifplugd stop
    for i in $INT ; do
        ifconfig $i 0.0.0.0 down &>/dev/null
    done

}

start() {
    /etc/init.d/ifplugd start
    /etc/init.d/wpa.sh start
    /etc/init.d/networking start
}

restart() {
    stop
    sleep 5
    start
}

$1

```

While writing this I thought of ifplugd and guessnet which could also be responsible for this. Will see if that could cause problems. 

Guessnet has a problem indeed, which I reported, but I don't get the same error I do get when on alpha4 (and guessnet hasn't changed from jaunty).

My question is, does anyone having a similar setup experiences the same issue? And if I would to file a bug report, against which package would I file this? Or would I let the devs handle this and just file it against Ubuntu..

The only updates for me are:

```

http://archive.ubuntu.com karmic/universe                guessnet                            0.49-1
http://archive.ubuntu.com karmic/main                    wpasupplicant                       U: 0.6.9-3 / 0.6.9-3ubuntu1
http://archive.ubuntu.com karmic/universe                ifplugd                             0.28-15ubuntu1
http://archive.ubuntu.com karmic/main                    netbase                             U: 4.35ubuntu1 / 4.35ubuntu2

```

---

### Post by ktraub on 2009-09-21
slakkie I am having similar problems.
I have a wired interface with a static IP address and a Wifi adapter that uses dhcp.

No matter what, network-manager can't seem to establish a default gateway in the routing table.

I've had to resort to scripts to add the appropriate default gateway depending on what environnment I am in.

I've noticed that if the wired interface is unplugged on boot, netmgr still thinks it is alive and uses it as the default gateway, which obviously won't work as it isn't plugged in so using the wireless interface at that point won't work.

So for now, I have different scripts which I run to manually insert a default GW route depending on the environment and I have to hack together a new one each time I connect to a new WiFi access point.

Frankly, if it wasn't for the Mobile broadband support in network-manager, I'd toss it altogether and go back to WiCD.

Hope that helps.
-Kev

---

### Post by slakkie on 2009-09-23
I restored to alpha4, and pinned some packages:

```

Explanation: Added on 20090923:082500 by pkg2pin or dpkg2pin
Package: libc6
Pin: version 2.10.1-0ubuntu8
Pin-Priority: 1001

Explanation: Added on 20090923:082500 by pkg2pin or dpkg2pin
Package: guessnet
Pin: version 0.49-1
Pin-Priority: 1001

Explanation: Added on 20090923:082500 by pkg2pin or dpkg2pin
Package: wpasupplicant
Pin: version 0.6.9-3
Pin-Priority: 1001

Explanation: Added on 20090923:082500 by pkg2pin or dpkg2pin
Package: ifplugd
Pin: version 0.28-15ubuntu1
Pin-Priority: 1001

Explanation: Added on 20090923:082500 by pkg2pin or dpkg2pin
Package: netbase
Pin: version 4.35ubuntu1
Pin-Priority: 1001

```

Upgraded, and I don't have the issue anymore..

---

