---
title: "DNS problem"
date: 2005-07-19
forum: Installation &amp; Upgrades
---

### Post by scorpio2002 on 2005-07-19
Hi there! 
I'm in a network cennected to a router. Ubuntu has some problems in detecting the DNS, as it takes as a DNS the gateaway of my router and so, each time I boot, I have to set manually the exact DNS before being able to connect.

How can I prevent Ubuntu from setting the DNS at each boot?

Ciao,
Donato :-)

---

### Post by mcduck on 2005-07-19
You'll need to comment out some lines in /etc/dhcp3/dhclient-script.

Like this:
```

#        if [ -n "$new_domain_name_servers" ]; then
#            for nameserver in $new_domain_name_servers; do
#                echo nameserver $nameserver >>$new_resolv_conf
#            done
#        else # keep 'old' nameservers
            egrep -i '^ *[:space:]*nameserver' /etc/resolv.conf >> \
                  $new_resolv_conf
#        fi

```

After that you can manually set your DNS servers and they'll work even after reboot. Something like this should work for other network settings as well.

---

### Post by mingus on 2005-07-19
Just fyi, when using DHCP on a LAN, the router's IP is the gateway and it should be returning to Ubuntu the DNS server IP's.  Did you try configuring the system with a static IP address? - that will bypass DHCP and should avoid overwriting the DNS entries.

---

