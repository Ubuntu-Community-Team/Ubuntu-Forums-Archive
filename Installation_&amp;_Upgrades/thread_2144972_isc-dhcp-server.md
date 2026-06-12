---
title: "isc-dhcp-server"
date: 2013-05-13
forum: Installation &amp; Upgrades
---

### Post by jrperry on 2013-05-13
Hello,

I have started working on setting up a dhcp server.
So far no luck, but I have just started. If you have any resources that would help me out please let me know. I have just started working on this again and decided to document my journey.

[http://bit.ly/10o1Ewj](http://bit.ly/10o1Ewj)

---

### Post by Lars Noodén on 2013-05-14
To get started with the ISC dhcp server, you need either a static ip number on one interface or at least a predictable one.  Then you can set the server to listen to that interface and network.  If your static IP number is 192.168.0.1 then your initial configuration could look something like this in dhcpd.conf:

```

option  domain-name "dhcp.example.com";
option  domain-name-servers 193.210.19.19, 193.210.18.18, 193.210.19.190;

subnet 192.168.0.0 netmask 255.255.255.0 {
        option routers 192.168.2.0;

        range 192.168.0.32 192.168.0.63;
}

``` 

The manual page for [dhcp.conf](http://linux.die.net/man/5/dhcpd.conf) is quite useful, if a little abstract.

But maybe we should ask first what are your plans for using dhcp?

---

### Post by jrperry on 2013-05-14
I volunteer for a not-for-profit that provides afterschool programming to the community through two organizations it supports. One provides programming for kids aged eight to thirteen. The other provides programming for kids aged twelve to eighteen. We currently have ten computers but I am looking to double that number in the next year. For them my primary goal is to set certain IP addresses based on the MAC address of the device. I do realize that the easy way is to set them to a static address at the device, but I am not the only person with admin privileges on those devices and this is something I don&#8217;t want them playing with.
 
I would also like to reserve ip addresses for a certain number of personal laptops so I can filter as many resources out of the dhcp range as possible. We have a large number of open jacks through the building and I don&#8217;t want people to be plugging into them and accessing things they shouldn&#8217;t. When I took this project on it was such a mess the easiest way to fix everything was to rip it out and start again.

Down the road I may choose to give each organization their own subnet, or a subnet for the dhcp range and one for everyone else, but at this point there are other things I would like to do before I think of complicating things.

---

### Post by Lars Noodén on 2013-05-14
Ok.  It's easy to assign ip numbers based on MAC addresses.

```

host notebook {
  hardware ethernet *xx:xx:xx:xx:xx:xx*;
  fixed-address 192.168.0.100;
  option host-name "notebook";
}

```

I haven't tried excluding unknown MAC addresses, but I'd expect that it is possible.

But keep in mind that it is dead simple for anyone to change their MAC address before connecting to the LAN.

---

### Post by jrperry on 2013-05-14
My current train of thought is anyone who plugs into the network by default gets assigned to the dhcp range. The only devices that don't get assigned to that range are devices I want to have access to all the resources on the network, know the MAC address for, and physically assign to another address in the dhcpd.conf file.

My first concern though is getting the server running. which I haven't done yet.
Details of what I have done to try and get it working are listed here [http://bit.ly/10o1Ewj](http://bit.ly/10o1Ewj)

I have posted log files and other documentation that personally I think it takes up too much room to put here.

---

