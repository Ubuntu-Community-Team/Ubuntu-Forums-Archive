---
title: "dhcp / dns / bind"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by balddogger on 2007-04-26
Hello,

I'm using 7.04 server addtion and trying to setup a local dns server.  Here are my thoughts...

1) Setup dhcp-server3 to assign the static ip address to my machines / periphals on my local network
2) Setup local dhcp / dns / bind servers so that I can access my machines / periphals with the following names
     server.dogger.home  192.168.1.1
     gate.dogger.home     192.168.1.2
     home.dogger.home    192.168.1.3
     hp2710.dogger.home 192.168.1.4
     nas.dogger.home        192.168.1.5

The idea is if I want to add my network printer to any of the other machines on the network, I just just add hp2710.dogger.home.  If I want to access the browers config for my printer, [http://hp2710.dogger.home](http://hp2710.dogger.home).  If I want to ssh, ssh server.dogger.com, if I want to access my web page [http://server.dogger.home](http://server.dogger.home)

Instead of creating a host file for each machine, have a local dns server running on 192.168.1.1.  If the url is not part of the dogger.home network, everything would be forwarded to the DNS server provide by my ISP.

I've played with all the configuration files and just can't seem to get all this working.  If anyone has some example configuraiton files from their own local network that they can share, that would be great.  I can't be the only person that wants to do this :-)

Thanks for your help,

Chad

---

### Post by Big Ed on 2007-04-26
This thread has a pretty good set of instructions for setting up a dns server in Ubuntu:

[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

Read more that just the first bit because there are additional details further down.

Static dhcp should be easy but google isn't giving me anything that looks pertinent without knowing more about the software that Ubuntu Server Edition uses.  I can say that I didn't bother with dhcp on my server; I have one of those ubiquitous firewall/routers that serves up dhcp assignments.  And it's dead easy to set that to deliver the same ip to each computer every time.  If you are using this, you will have to put in the ip of your server as the dns server so that it is passed onto the other computers when they boot.  

Hmm, I wonder if the dns solution your're implementing could be configured on the router also.  I'll have to try that when I get home.

Ed

---

### Post by balddogger on 2007-04-27
Thanks Ed for the info.  I have seen the URL you mentioned and tried using that.  But I'm missing something, in the zone files.  Any idea on where I can get some detail itself on Ubunutu / Debian Zone files?

Why DHCP server running under Ubuntu?  My Linksys gateway has the same options you are talking about, but I was looking for a little more control.  I have a Linksys gateway and a Linksys range extender, for some reason, the extender isn't passing back the DHCP server response to any of my machines.  With the DHCP server running under Ubuntu, I have a little more control and in-site into what-is-going on.

---

### Post by Big Ed on 2007-04-27
> **balddogger said:**
> Thanks Ed for the info.  I have seen the URL you mentioned and tried using that.  But I'm missing something, in the zone files.  Any idea on where I can get some detail itself on Ubunutu / Debian Zone files?

Why DHCP server running under Ubuntu?  My Linksys gateway has the same options you are talking about, but I was looking for a little more control.  I have a Linksys gateway and a Linksys range extender, for some reason, the extender isn't passing back the DHCP server response to any of my machines.  With the DHCP server running under Ubuntu, I have a little more control and in-site into what-is-going on.

Is this what you're looking for?  
[http://www.debuntu.org/2006/08/05/85-how-to-setting-up-a-dns-zone-with-bind9](http://www.debuntu.org/2006/08/05/85-how-to-setting-up-a-dns-zone-with-bind9)

Can't help you with the extender.  I've never used one.

Ed

---

### Post by balddogger on 2007-05-02
So, here are my changes, any ideas?

1) named.conf.local

zone "dogger.foo" {
        type master;
        file "dogger.foo.db";
        notify no;
};

zone "1.168.192.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/zones/reverse/192.168.1";
};

2) dogger.foo.db
$TTL 3D
@       IN      SOA     ns.dogger.foo. (
                        200608081       ; serial, todays date + todays serial #
                        8H              ; refresh, seconds
                        2H              ; retry, seconds
                        4W              ; expire, seconds
                        1D )            ; minimum, seconds
;
                NS      ns              ; Inet Address of name server
;
ns              A       192.168.1.1
www             CNAME   [www.dogger.foo](www.dogger.foo).
ftp             CNAME   ns
server          CNAME   ns
gw              A       192.168.1.2
                TXT     "Network gateway"
home            A       192.168.1.3
                TXT     "Home Computer"
hp2710          A       192.168.1.4
                TXT     "Printer"
nas             A       192.168.1.5
                        "Network HD"

3) reverse/192.168.1

$TTL 3D
@       IN      SOA     ns.dogger.foo. (
                        200608051 ; Serial, todays date + todays serial
                        8H      ; Refresh
                        2H      ; Retry
                        4W      ; Expire
                        1D)     ; Minimum TTL
                NS      ns.dogger.foo

1               PTR     ns.dogger.foo.
2               PTR     gw.dogger.foo.
3               PTR     home.dogger.foo.
4               PTR     hp2710.dogger.foo.
5               PTR     nas.dogger.foo.

4) resolv.conf
    search dogger.foo
    nameserver 192.168.1.1

5) dhcpd.conf

# A slightly different configuration for an internal subnet.
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.10 192.168.1.100;
  option domain-name-servers 192.168.1.1;
  option domain-name "dogger.foo";
  option routers 192.168.1.2;
  option broadcast-address 192.168.1.255;
  default-lease-time 600;
  max-lease-time 7200;
}

6) interfaces
iface eth0 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.2

7) named.conf.options
        forwarders {
                68.87.75.194;
                68.87.64.146;
        };


The results, dns works fine for anything in the outside world, but none of my local network - - from nslookup
 nslookup
> [www.google.com](www.google.com)
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
[www.google.com](www.google.com)  canonical name = [www.l.google.com](www.l.google.com).
Name:   [www.l.google.com](www.l.google.com)
Address: 209.85.165.99
Name:   [www.l.google.com](www.l.google.com)
Address: 209.85.165.103
Name:   [www.l.google.com](www.l.google.com)
Address: 209.85.165.104
Name:   [www.l.google.com](www.l.google.com)
Address: 209.85.165.147
> nas.dogger.foo
Server:         192.168.1.1
Address:        192.168.1.1#53

** server can't find nas.dogger.foo: SERVFAIL
>

---

### Post by phormion on 2007-05-02
> **balddogger said:**
> So, here are my changes, any ideas?

2) dogger.foo.db
$TTL 3D
@       IN      SOA     ns.dogger.foo. (
                        200608081       ; serial, todays date + todays serial #
                        8H              ; refresh, seconds
                        2H              ; retry, seconds
                        4W              ; expire, seconds
                        1D )            ; minimum, seconds
;
                NS      ns              ; Inet Address of name server
;
ns              A       192.168.1.1
www             CNAME   [www.dogger.foo](www.dogger.foo).


The above line doesn't make any sense - it's a circular CNAME. If you check /var/log/messages, do you see any errors reported by named while starting up? 

Another option would be to run named-checkzone on the zone file - check the manual page for usage instructions. 

> 
5) dhcpd.conf

# A slightly different configuration for an internal subnet.
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.10 192.168.1.100;
  option domain-name-servers 192.168.1.1;
  option domain-name "dogger.foo";
  option routers 192.168.1.2;
  option broadcast-address 192.168.1.255;
  default-lease-time 600;
  max-lease-time 7200;
}


I would set the least time to something more than 10 minutes (600 seconds), I don't think you want your machines to keep renewing their addresses that often. Also, what I'd do is assign specific IPs to certain MACs statically, since you don't have that many computers around. 

> 
7) named.conf.options
        forwarders {
                68.87.75.194;
                68.87.64.146;
        };


You don't need forwarders in order for your DNS server to function - in fact, most DNS experts (at least the ones on bind-users) recommend against it, since it introduces another point of failure - the ISP's DNS servers. 

> 
The results, dns works fine for anything in the outside world, but none of my local network - - from nslookup
 nslookup
...
> nas.dogger.foo
Server:         192.168.1.1
Address:        192.168.1.1#53

** server can't find nas.dogger.foo: SERVFAIL
>

That might be because the zone failed to load (although SERVFAIL can in general mean many things). nslookup is not the best troubleshooting tool, try querying the server using dig - its output is more verbose and it doesn't do things behind the scenes, like appending the domains in the search list. Try: 'dig @192.168.1.1 nas.dogger.foo', for example.

---

