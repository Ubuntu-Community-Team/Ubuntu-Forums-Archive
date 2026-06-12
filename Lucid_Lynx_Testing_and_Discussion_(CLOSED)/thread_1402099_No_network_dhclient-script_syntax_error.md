---
title: "No network: dhclient-script syntax error"
date: 2010-02-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by paul_in_london on 2010-02-08
Following recent updates of **dhcp3-common**, **dhcp3-server** and **dhcp3-client** I have no network.

When I try to restart networking, I get:

```
Listening on LPF/eth1/00:1d:60:43:fb:12
Sending on   LPF/eth1/00:1d:60:43:fb:12
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.254 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
/sbin/dhclient-script: line 75: syntax error near unexpected token `}'
/sbin/dhclient-script: line 75: `}'
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

/sbin/dhclient-script: line 75: syntax error near unexpected token `}'
/sbin/dhclient-script: line 75: `}'
Listening on LPF/eth1/00:1d:60:43:fb:12
Sending on   LPF/eth1/00:1d:60:43:fb:12
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
cDHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
send_packet: Network is down
```

Anyone else seeing this? Chrooting into Lucid from my Arch install and reinstalling those dhcp packages didn't help.

---

### Post by avenger0017 on 2010-02-09
Running lucid in virtual box here, getting the same thing after updating:

$ sudo dhclient eth2
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

/sbin/dhclient-script: line 75: syntax error near unexpected token `}'
/sbin/dhclient-script: line 75: `}'
Listening on LPF/eth2/08:00:27:fa:1c:19
Sending on   LPF/eth2/08:00:27:fa:1c:19
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.87.100 from 192.168.87.1
DHCPREQUEST of 192.168.87.100 on eth2 to 255.255.255.255 port 67
DHCPACK of 192.168.87.100 from 192.168.87.1
/sbin/dhclient-script: line 75: syntax error near unexpected token `}'
/sbin/dhclient-script: line 75: `}'

---

### Post by jppr on 2010-02-09
dhcp3 updated last night, i don´t have any problem, system works fine.

---

### Post by tghe-retford on 2010-02-09
Can confirm. Need to go to work though. If a bug report has been started when I get back, I will confirm it.

---

### Post by BuMRK on 2010-02-09
Fix

edit

sudo nano /sbin/dhclient-script

```

make_resolv_conf() {
    if [ "$new_domain_name" -o "$new_domain_name_servers" ]; then
        # Find out whether we are going to mount / rw
        exec 9>&0 </etc/fstab
        rootmode=rw
        while read dev mnt type opts dump pass junk; do
            [ "$mnt" != / ] && continue
            case "$opts" in
                ro|ro,*|*,ro|*,ro,*)
                   rootmode=ro
                   ;;
                 esac
         done
         exec 0>&9 9>&-

        # Wait for /etc/resolv.conf to become writable
        if [ "$rootmode" = "rw" ]; then
            while [ ! -w /etc ]; do
                sleep 0.1
            done
        fi
#--add__
    fi


```

---

### Post by avenger0017 on 2010-02-09
Thanks BuMRK, that fixes the problem.

---

### Post by BuMRK on 2010-02-09
new version dhcp3-client (3.1.3-2ubuntu2)

[http://packages.ubuntu.com/lucid/dhcp3-client](http://packages.ubuntu.com/lucid/dhcp3-client)

---

### Post by code850 on 2010-02-09
Here too, dhcp update from today or yeasterday broke my network.

---

### Post by bewolf on 2010-02-09
Same issu here :(

---

### Post by paul_in_london on 2010-02-09
Confirmed fixed. Corrected **/sbin/dhclient-script**, rebooted and then I was able to update/upgrade directly from Lucid as normal instead of having to rely on a chroot. Cheers.

---

### Post by nbubis on 2010-02-10
The fix suggested fixes the syntax error, but dhcpclient still cannot connect - I'm getting "no DHCPOFFERS" from both wired and wireless cards.

Any ideas?

---

