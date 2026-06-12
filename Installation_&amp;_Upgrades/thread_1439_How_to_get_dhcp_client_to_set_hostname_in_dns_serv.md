---
title: "How to get dhcp client to set hostname in dns server"
date: 2004-10-21
forum: Installation &amp; Upgrades
---

### Post by mxc on 2004-10-21
Hi all,

I am uising a dns server which allows for the dhcp client to update the dns record. I have edited /etc/networl/interfaces and added the option 

> hostname mypcname

to the entry for eth0 which has the method for dhcp set. Despite this the dns server is not updated with the hostname of the machine. How do I set up ubuntu to allow the computer to set its hostname on the dns server?

---

### Post by seantellis on 2006-08-25
Here's how I did it, after some searching:

First, take a copy of your current DHCP configuration:

```
sudo cp /etc/dhcp3/dhclient.conf /etc/dhcp3/dhclient.conf.backup
```

Then edit the DCHP configuration file:
```
sudo gedit /etc/dhcp3/dhclient.conf
```

In my file, there was a commented-out line:
```
#send host-name "some.random.host.name";
```

Uncomment this and change it to send your host and domain name:
```
send host-name "my-host.my-domain";
```

Obviously, put in your own host and domain names.

Then restart the network interface which will recontact the DHCP server:
```
sudo ifdown eth0
sudo ifup eth0
```

Again, if your primary network interface is not eth0, put the correct interface in instead.

The raw information for this was found on David Martin's Ubuntu starter page at [http://www.cs.cornell.edu/~djm/ubuntu/#send-dhcp](http://www.cs.cornell.edu/~djm/ubuntu/#send-dhcp).

---

### Post by djSeverin on 2007-04-03
Thankyou very much for the great how-to seantellis, worked a treat.

Cheers,
Sev

---

