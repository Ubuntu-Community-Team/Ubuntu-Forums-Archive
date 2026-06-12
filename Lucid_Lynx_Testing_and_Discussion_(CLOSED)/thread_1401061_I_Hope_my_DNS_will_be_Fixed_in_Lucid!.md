---
title: "I Hope my DNS will be Fixed in Lucid!"
date: 2010-02-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by the.scarecrow on 2010-02-07
Since Karmic I cannot use my ISP DNS server on my D-Link router. I also have a Seimens router with a different ISP and that works OK.

The D-link works fine with Intrepid, Hardy, WinXP and Win7. But not with Karmic and now Lucid.

The WiFi link to the router looks fine but I can't connect to anything on the Internet unless I change the DNS server to Google or OpenDNS via System>Preferences>Network Connections>WiFi.

This fix is effective but even if it only effects a few users, its a big turn off to a new user when their shiny new Ubuntu install can't get out onto the Internet.

I know when this problem first arose after Karmic was released, quite a few people reported this problem.

Do others still have this problem in Lucid or is it just me?

---

### Post by alphacrucis2 on 2010-02-07
> **the.scarecrow said:**
> Since Karmic I cannot use my ISP DNS server on my D-Link router. I also have a Seimens router with a different ISP and that works OK.

The D-link works fine with Intrepid, Hardy, WinXP and Win7. But not with Karmic and now Lucid.

The WiFi link to the router looks fine but I can't connect to anything on the Internet unless I change the DNS server to Google or OpenDNS via System>Preferences>Network Connections>WiFi.

This fix is effective but even if it only effects a few users, its a big turn off to a new user when their shiny new Ubuntu install can't get out onto the Internet.

I know when this problem first arose after Karmic was released, quite a few people reported this problem.

Do others still have this problem in Lucid or is it just me?

Odd. What DNS server address(es) are you picking up via the D-LINK if you don't override it. I presume you are using DHCP to get this info from the D-LINK. I have a D-LINK router and I don't see any problem like this with either Karmic or Lucid.

---

### Post by cariboo on 2010-02-07
There some setups, that for whatever reason pick up the routers ip address for DNS, the fix for now is to go in to Network-Manager and set DHCP for ip address only, then manually add DNS addresses.

---

### Post by mattman on 2010-02-08
I had this same problem with my wifi ISP (using a Netgear router), since Jaunty or maybe even earlier. I have since switched to DSL and no longer experience this problem. This could be very frustrating for a new user.

---

### Post by the.scarecrow on 2010-02-08
I do have DHCP server selected in my D-Link router and DNS mode set to Auto. The fix I am using is not a problem to me but noobies expect Ubuntu to "work straight out the box"

I have used the same config. in my router for years and don't expect to have to change it to suit new releases of Ubuntu, as I said its only since Karmic I have experienced this problem. Whilst I would quite like some neat fix, that doesn't help new users trying Ubuntu for the first time that get the same problem.

As @mattman put it so well "This could be very frustrating for a new user."

I am not a computer expert and I am using Lucid precisely so that I can point out the problems an ordinary computer user can have. I have high hopes and expectations for Lucid LTS.

---

### Post by alphacrucis2 on 2010-02-08
> **the.scarecrow said:**
> I do have DHCP server selected in my D-Link router and DNS mode set to Auto. The fix I am using is not a problem to me but noobies expect Ubuntu to "work straight out the box"

I have used the same config. in my router for years and don't expect to have to change it to suit new releases of Ubuntu, as I said its only since Karmic I have experienced this problem. Whilst I would quite like some neat fix, that doesn't help new users trying Ubuntu for the first time that get the same problem.

As @mattman put it so well "This could be very frustrating for a new user."

I am not a computer expert and I am using Lucid precisely so that I can point out the problems an ordinary computer user can have. I have high hopes and expectations for Lucid LTS.

If you don't implement your manual fix then what do you end up with in resolv.conf ? My D-LINK returns it's own address as the DNS server in response to DHCP requests. My resolv.conf has 10.1.1.1 as the DNS server. The D-Link acts as a DNS forwarder to the ISP's real DNS servers and everything works fine. I can't reproduce the problem you are having with any version of Ubuntu that I have.

Maybe you should look at the firmware version in your D-LINK and make sure it is running the latest. I recall upgrading the firmware on mine as there were several bugs in the factory shipped version.

---

### Post by cariboo on 2010-02-08
The problem is definitely with Network-Manager, it has nothing to do with what router you are using.

---

### Post by Fred2a on 2010-02-09
It's nice to have this confirmed. I have the same problem, my Hardy server works just fine, but PCs with Karmic and Lucid require manual DNS settings (I think Jaunty was ok as well), this is rather annoying. I thought at first my router was borked.

TIP: When installing from a live CD set the DNS in network manager manually before clicking on install and the installer will be able to contact the repos when it needs/wants to. You'll then have to Fix the DNS again when you first boot into your fresh OS.

It would be nice if ubuntu (which relies heavily on net access for package management) could handle this type of situtation more gracefully when it does occur. Try breaking your DNS settings and see what the system does when you try an update, or to use software centre. Responsive as a brick.

---

### Post by the.scarecrow on 2010-02-09
> **alphacrucis2 said:**
> If you don't implement your manual fix then what do you end up with in resolv.conf ? My D-LINK returns it's own address as the DNS server in response to DHCP requests. My resolv.conf has 10.1.1.1 as the DNS server. The D-Link acts as a DNS forwarder to the ISP's real DNS servers and everything works fine. I can't reproduce the problem you are having with any version of Ubuntu that I have.

Maybe you should look at the firmware version in your D-LINK and make sure it is running the latest. I recall upgrading the firmware on mine as there were several bugs in the factory shipped version.

Sorry, I don't know what you mean. "resolve.conf" is that a file and if so where is it? If you tell me exactly how to get the info you want, I will happily provide it.

My D-Link firmware is way out of date but otherwise is working. I am reluctant to upgrade it because I'm using a UK router in France and it was a pig to get going. Mainly because Orange treats the router setup info like this as a national state secret.

So do I install the French or UK version Firmware and I don't want to bork a perfectly functional router by making the wrong choice. But thats another story.

I'm not trying to help myself here, I am thinking about new 1st time Ubuntu users.

---

### Post by the.scarecrow on 2010-02-09
> **cariboo907 said:**
> The problem is definitely with Network-Manager, it has nothing to do with what router you are using.

Like I said above, if I can provide any information that will help then just tell me how to get it and I will post it here.

Oh and Hardy, Intrepid, Jaunty = OK
Karmic and Lucid = Don't work.

---

### Post by Kazade on 2010-02-09
> **the.scarecrow said:**
> Sorry, I don't know what you mean. "resolve.conf" is that a file and if so where is it? If you tell me exactly how to get the info you want, I will happily provide it.


/etc/resolv.conf

Just paste the contents of that file here (well, actually create a bug report and paste it there :)) 

Make sure you have the DHCP settings to the default before reading the contents though. You should have a line like "nameserver 192.168.0.1" or something, that will be the IP address of the DNS server your router is giving you.

---

### Post by the.scarecrow on 2010-02-09
With the Google DNS installed I get:

> # Generated by NetworkManager
nameserver 8.8.8.8
nameserver 8.8.4.4

and access to the Internet works perfectly.


With Lucid as it comes fresh out the .iso I get:

> # Generated by NetworkManager
nameserver 192.168.1.1

and access to the Internet does not work, this IP address is for the router admin. so that explains why it won't work.

@cariboo907 was spot on with his first post but surely this fix is not acceptable in a LTS release. Thats my point.

---

### Post by alphacrucis2 on 2010-02-09
> **the.scarecrow said:**
> With the Google DNS installed I get:



and access to the Internet works perfectly.


With Lucid as it comes fresh out the .iso I get:



and access to the Internet does not work, this IP address is for the router admin. so that explains why it won't work.

@cariboo907 was spot on with his first post but surely this fix is not acceptable in a LTS release. Thats my point.

As I already said, what is happening is exactly what is supposed to happen. The D-Link acts as a DNS forwarder so the 192.168.1.1 address for your DNS server is correct and normal default behaviour for the DHCP server running on the D-Link. I suggest trying a firmware upgrade of the D-Link itself as there may some issue with the DNS forwarding. (Or at least check the configuration of your dlink)

From the dlink support site:

[QUOTE=DLINK]DNS Relay
When DNS Relay is enabled, the router will play a role as DNS server that send request to ISP DNS server and cache the information for later access. When DNS relay is disabled, the computer will pull information from ISP DNS server.[/QUOTE]

[http://support.dlink.com/Emulators/di624_revC/help_home.html](http://support.dlink.com/Emulators/di624_revC/help_home.html)

---

### Post by alphacrucis2 on 2010-02-09
> **cariboo907 said:**
> The problem is definitely with Network-Manager, it has nothing to do with what router you are using.


I don't think that has been established yet.

---

### Post by cariboo on 2010-02-09
> **alphacrucis2 said:**
> I don't think that has been established yet.

It may not be, but I've helped enough people that have run into the same problem, to see that it isn't one particular brand of router, wireless nic or wired nic that causes the problem. It happened to me on one Karmic installation when I was running the default firmware on my Linksys WRT54GS.

---

### Post by k3lt01 on 2010-02-10
I have had a similar issue in every .10 release since Gutsy, for some reason the .04s seem to be ok. Now I just [follow this]("http://ubuntuforums.org/showpost.php?p=3996845&postcount=5") and everything is ok.

---

### Post by the.scarecrow on 2010-02-10
> **alphacrucis2 said:**
> As I already said, what is happening is exactly what is supposed to happen. The D-Link acts as a DNS forwarder so the 192.168.1.1 address for your DNS server is correct and normal default behaviour for the DHCP server running on the D-Link. I suggest trying a firmware upgrade of the D-Link itself as there may some issue with the DNS forwarding. (Or at least check the configuration of your dlink)

From the dlink support site:



[http://support.dlink.com/Emulators/di624_revC/help_home.html](http://support.dlink.com/Emulators/di624_revC/help_home.html)

Your advice may well be correct but slightly misses my point. Which is that this self same router works perfectly with WinXP, Win7, Hardy, Intrepid and Jaunty. So logically it should also work with Karmic and Lucid.

My concern is that a new user having just installed Linux for the first time in the form of Lucid, will be very disappointed to hit this problem. So surely the fix required should be done in Lucid so the new user gets onto the Internet when they first fire it up without hassle like this.

Let face it, they may not even be able to ask for a solution here because.... you guessed it their Internet doesn't work anymore.

---

### Post by the.scarecrow on 2010-02-10
> **k3lt01 said:**
> I have had a similar issue in every .10 release since Gutsy, for some reason the .04s seem to be ok. Now I just [follow this]("http://ubuntuforums.org/showpost.php?p=3996845&postcount=5") and everything is ok.

This looks like the same solution I use except I use the GUI via Network Connections.

Still doesn't help a new user installing Ubuntu for the first time with a broken Internet access caused by no DNS.

---

### Post by k3lt01 on 2010-02-10
> **the.scarecrow said:**
> This looks like the same solution I use except I use the GUI via Network Connections.

Still doesn't help a new user installing Ubuntu for the first time with a broken Internet access caused by no DNS.Then your problem is not your router. I'm not sure you can just say that everything is fine with Windows either one of the reasons I moved to Ubuntu is because Vista was such a pain in the butt. What worked perfectly in XP wouldn't work at all in Vista. Each OS has its good and bad points.

---

### Post by the.scarecrow on 2010-02-10
So we have had a good debate and I would like to know if this is a bug and should it be reported on Launchpad? I don't want to waste their time reporting something that is not appropriate.

---

### Post by Digikid on 2010-02-10
> **cariboo907 said:**
> There some setups, that for whatever reason pick up the routers ip address for DNS, the fix for now is to go in to Network-Manager and set DHCP for ip address only, then manually add DNS addresses.

Sorry to say this but we should not HAVE to do that at all.

It is a bug issue that has existed since 9.04 and it needs to be FIXED....not sidestepped....and it needs to be done NOW.

---

### Post by alphacrucis2 on 2010-02-10
> **the.scarecrow said:**
> So we have had a good debate and I would like to know if this is a bug and should it be reported on Launchpad? I don't want to waste their time reporting something that is not appropriate.

What I would do in the this situation is to capture a wireshark
packet trace of the DHCP process. If the router DHCP server is returning the addresses of the ISP's DNS servers but network manager is putting the gateway address into resolv.conf, then that would definitely be a Network Manager bug. On the other hand, if the router DHCP server is returning its local address as a DNS server then that should be ok as long as the DNS relay function is enabled on the router. **BUT** it could even be something weird like the DNS query packets from Lucid not being properly handled by the DNS relay function on the router. In any case a packet trace is what the devs would need to be able to see what is happening. So:

```
sudo apt-get install wireshark
```

The wireshark shortcut will be created under Applications/Internet but to actually capture packets it needs to run as root. To do this enter the following command:

```
gksu wireshark
```


It isn't that scary to run as it's a graphical app.

I would then start up a Wireshark capture of the wifi interface with the wifi down. Then bring it up. Then stop the capture after the wifi has connected. The only problem might be if the wifi driver doesn't play ball with libpcap (which is what wireshark uses to capture the packets). If it works you can save the captured packets as a file that you could upload to launchpad.


Forgot to say. You should see on the wireshark screen at some point after the wifi comes up, a DHCP Request message being sent with a source address of 0.0.0.0. The router should respond with a DHCP ACK. Select the DHCP ACK message and in the frame below you should see a + next to Bootstrap Protocol. Click the + and you will see all the stuff that the DHCP server is dishing out, like ip address, def gway, dns servers etc.

---

### Post by the.scarecrow on 2010-02-11
@alphacrucis2
Well what you say sounds very interesting and I will give it a go then let you know how I get on with it.

Thanks

---

### Post by Kazade on 2010-02-11
> **the.scarecrow said:**
> So we have had a good debate and I would like to know if this is a bug and should it be reported on Launchpad? I don't want to waste their time reporting something that is not appropriate.

It should certainly be reported. Although the DNS IP address is being determine by Ubuntu correctly (it's using the one your router is giving you) there is something else going on that is obviously an Ubuntu issue (as your router works in Windows).

---

### Post by the.scarecrow on 2010-02-11
> No.     Time        Source                Destination           Protocol Info
      3 0.163136    192.168.1.1           192.168.1.5           DHCP     DHCP ACK      - Transaction ID 0xbecdca37

Frame 3 (590 bytes on wire, 590 bytes captured)
    Arrival Time: Feb 11, 2010 22:26:37.008958000
    [Time delta from previous captured frame: 0.007603000 seconds]
    [Time delta from previous displayed frame: 0.007603000 seconds]
    [Time since reference or first frame: 0.163136000 seconds]
    Frame Number: 3
    Frame Length: 590 bytes
    Capture Length: 590 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:bootp]
    [Coloring Rule Name: UDP]
    [Coloring Rule String: udp]
Ethernet II, Src: D-Link_cc:48:a1 (00:15:e9:cc:48:a1), Dst: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
    Destination: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        Address: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.1 (192.168.1.1), Dst: 192.168.1.5 (192.168.1.5)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 576
    Identification: 0x0000 (0)
    Flags: 0x00
        0.. = Reserved bit: Not Set
        .0. = Don't fragment: Not Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 64
    Protocol: UDP (0x11)
    Header checksum: 0xf556 [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.1.1 (192.168.1.1)
    Destination: 192.168.1.5 (192.168.1.5)
User Datagram Protocol, Src Port: bootps (67), Dst Port: bootpc (68)
    Source port: bootps (67)
    Destination port: bootpc (68)
    Length: 556
    Checksum: 0x681e [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Bootstrap Protocol
    Message type: Boot Reply (2)
    Hardware type: Ethernet
    Hardware address length: 6
    Hops: 0
    Transaction ID: 0xbecdca37
    Seconds elapsed: 0
    Bootp flags: 0x0000 (Unicast)
        0... .... .... .... = Broadcast flag: Unicast
        .000 0000 0000 0000 = Reserved flags: 0x0000
    Client IP address: 0.0.0.0 (0.0.0.0)
    Your (client) IP address: 192.168.1.5 (192.168.1.5)
    Next server IP address: 0.0.0.0 (0.0.0.0)
    Relay agent IP address: 0.0.0.0 (0.0.0.0)
    Client MAC address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
    Client hardware address padding: 00000000000000000000
    Server host name not given
    Boot file name not given
    Magic cookie: (OK)
    Option: (t=53,l=1) DHCP Message Type = DHCP ACK
        Option: (53) DHCP Message Type
        Length: 1
        Value: 05
    Option: (t=54,l=4) DHCP Server Identifier = 192.168.1.1
        Option: (54) DHCP Server Identifier
        Length: 4
        Value: C0A80101
    Option: (t=51,l=4) IP Address Lease Time = 1 hour
        Option: (51) IP Address Lease Time
        Length: 4
        Value: 00000E10
    Option: (t=12,l=6) Host Name = "ubuntu"
        Option: (12) Host Name
        Length: 6
        Value: 7562756E7475
    Option: (t=1,l=4) Subnet Mask = 255.255.255.0
        Option: (1) Subnet Mask
        Length: 4
        Value: FFFFFF00
    Option: (t=3,l=4) Router = 192.168.1.1
        Option: (3) Router
        Length: 4
        Value: C0A80101
    Option: (t=6,l=4) Domain Name Server = 192.168.1.1
        Option: (6) Domain Name Server
        Length: 4
        Value: C0A80101
    End Option
    Padding

resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1


All the above is the output from Wireshark, showing the line you asked for with the content of resolv.conf tacked on the end.

This was done with the DNS setup as received from the .iso and not working e.g. I can't connect to anything on the Internet.

I also saved the file as some form of dump that I presume is what Launchpad would want. The above is a copy of a text file I exported detailing that one line and without the smiley faces, wherever did they come from?

So what do you make of this? does it help?

---

### Post by alphacrucis2 on 2010-02-11
```
[B]Length: 4
Value: C0A80101
Option: (t=6,l=4) Domain Name Server = [COLOR="Red"]192.168.1.1[/COLOR]
Option: (6) Domain Name Server
Length: 4
Value: C0A80101
End Option[/B]
Padding

resolv.conf
# Generated by NetworkManager
nameserver [COLOR="Red"]192.168.1.1[/COLOR] 
```

From this you can see that resolv.conf is being correctly set by Network Manager as the DHCP server (your router) is returning 192.168.1.1. (see bolded bit I quoted above). Definitely open a launchpad on this as something really weird must be happening. Before opening the launchpad, I would do one more test. Repeat the Wireshark packet capture but instead of stopping it immediately after the wifi comes up, do this from a terminal prompt first:

```
ping www.google.com
```

That will force a DNS lookup by the resolver. Then stop the capture. In wireshark, you should see a corresponding UDP port 53 (DNS query) packet with a destination of 192.168.1.1 and some sort of response should come back. Hopefully the response will contain some sort of error code which will shed some light on the problem.

---

### Post by xebian on 2010-02-11
Most router will automatically get the DNS ip address from your ISP unless you manually set it. 

The resolv.conf will get these values.

What are in those fields in your router?

---

### Post by alphacrucis2 on 2010-02-11
> **xebian said:**
> Most router will automatically get the DNS ip address from your ISP unless you manually set it. 

The resolv.conf will get these values.

What are in those fields in your router?

My own D-LINK doesn't return the ISP's DNS server addresses, even though it has learned them from upstream. Its' default behaviour is to act as a DNS relay, so that the DHCP clients don't need to know the addresses of the real DNS servers. Instead they use the router's private address as though it were the DNS server. That seems to be what is happenning here as the DHCP ACK from the router is telling the OP's PC to use the router's private address as a DNS server. We know this is working fine with Windows and earlier versions of Ubuntu so it doesn't appear to be anything wrong with the router configuration.

---

### Post by k3lt01 on 2010-02-11
> **Digikid said:**
> Sorry to say this but we should not HAVE to do that at all.

It is a bug issue that has existed since 9.04 and it needs to be FIXED....not sidestepped....and it needs to be done NOW.I have seen this happening since Gutsy (7.10). I really don't think it is anything major but that is just my opinion.

---

### Post by alphacrucis2 on 2010-02-11
> **k3lt01 said:**
> I have seen this happening since Gutsy (7.10). I really don't think it is anything major but that is just my opinion.

Well it would be good to get to the bottom of it. My D-LINK also returns its' private address as a pretend DNS server and DNS lookups get correctly relayed to the real DNS servers on all the versions of Ubuntu I have tested. That is why I am interested to see a wireshark trace of a failing DNS query. It is possible that the DNS relay function on the D-LINK for some reason is incompatible with the resolver running on some versions of linux. The reason I don't have the problem may be because I upgraded the firmware on my D-LINK to the latest version.

---

### Post by xebian on 2010-02-11
> **alphacrucis2 said:**
> My own D-LINK doesn't return the ISP's DNS server addresses, even though it has learned them from upstream. Its' default behaviour is to act as a DNS relay, so that the DHCP clients don't need to know the addresses of the real DNS servers. Instead they use the router's private address as though it were the DNS server. That seems to be what is happenning here as the DHCP ACK from the router is telling the OP's PC to use the router's private address as a DNS server. We know this is working fine with Windows and earlier versions of Ubuntu so it doesn't appear to be anything wrong with the router configuration.

IIRC from your earlier post this happens if DNS relay is enabled in the router.  So the solution is disable it and let it get it from the ISP NDS server, or set the DNS sever ip address manually in your router.

```

Originally Posted by DLINK
DNS Relay
When DNS Relay is enabled, the router will play a role as DNS server that send request to ISP DNS server and cache the information for later access. When DNS relay is disabled, the computer will pull information from ISP DNS server.
```

---

### Post by alphacrucis2 on 2010-02-11
> **xebian said:**
> IIRC from your earlier post this happens if DNS relay is enabled in the router.  So the solution is disable it and let it get it from the ISP NDS server, or set the DNS sever ip address manually in your router.

```

Originally Posted by DLINK
DNS Relay
When DNS Relay is enabled, the router will play a role as DNS server that send request to ISP DNS server and cache the information for later access. When DNS relay is disabled, the computer will pull information from ISP DNS server.
```

Well yes but that would be a workaround rather than a fix of the basic problem. The OP has already implemented a workaround but is not happy that this intervention is required and I agree with him that it shouldn't be necessary and as I say I have no problem with the default DNS relay method working.

---

### Post by xebian on 2010-02-11
> **alphacrucis2 said:**
> Well yes but that would be a workaround rather than a fix of the basic problem. The OP has already implemented a workaround but is not happy that this intervention is required and I agree with him that it shouldn't be necessary and as I say I have no problem with the default DNS relay method working.

So the problem is the router relay function not working properly.

Ubuntu and/or any distro for that matter will use whatever is in /etc/resolv.conf for DNS. Whether that works or not is not Ubuntu's problem.  DNS is just a server that tells  you the ip address of domain hence the name DNS(Domain Name Server).  
So if you put [www.yahoo.com](www.yahoo.com) in your browser, it has to go to the DNS and ask for the ip address.

Nothing to fix here.

---

### Post by alphacrucis2 on 2010-02-11
> **xebian said:**
> So the problem is the router relay function not working properly.

Ubuntu and/or any distro for that matter will use whatever is in /etc/resolv.conf for DNS. Whether that works or not is not Ubuntu's problem.  DNS is just a server that tells  you the ip address of domain hence the name DNS(Domain Name Server).  
So if you put [www.yahoo.com](www.yahoo.com) in your browser, it has to go to the DNS and ask for the ip address.

Nothing to fix here.

We don't know that for sure yet. That is why I want to see a wireshark trace of the DNS UDP query packet and the reply. That should indicate if the problem is really in the ubuntu DNS resolver, or a fault in the DNS relay function of the D-LINK

---

### Post by Fred2a on 2010-02-12
I think the issue is a combination of some types of router combined with Karmic/Lucid.

My machines all get a DNS of 192.168.1.1 from the router, XP can use this ok, Hardy can use this ok, but Karmic/Lucid are not able to support the pass through. 

Other routers I've used with Karmic have been fine though.

---

### Post by the.scarecrow on 2010-02-12
> **alphacrucis2 said:**
> Well it would be good to get to the bottom of it. My D-LINK also returns its' private address as a pretend DNS server and DNS lookups get correctly relayed to the real DNS servers on all the versions of Ubuntu I have tested. That is why I am interested to see a wireshark trace of a failing DNS query. It is possible that the DNS relay function on the D-LINK for some reason is incompatible with the resolver running on some versions of linux. The reason I don't have the problem may be because I upgraded the firmware on my D-LINK to the latest version.

I am completely in agreement with you. This is all about something weird happening to a few users. Its not about finding a fix for me, rather to improve the new user experience by eliminating a quirk of the system in Lucid.

I have the original firmware in my router and its quite old feb07 its got bugs too. I can't set WPA and this seems to be a known fault in the old firmware. But I don't want to do a flash upgrade (see an earlier post).

I hope I will be able to do that ping test a little later and post the results here.

---

### Post by the.scarecrow on 2010-02-12
```
ping www.google.com
```

That will force a DNS lookup by the resolver. Then stop the capture. In wireshark, you should see a corresponding UDP port 53 (DNS query) packet with a destination of 192.168.1.1 and some sort of response should come back. Hopefully the response will contain some sort of error code which will shed some light on the problem.[/QUOTE]

Results below:

```
No.     Time        Source                Destination           Protocol Info
      1 0.000000    fe80::8d69:edeb:b826:9b30 ff02::c               SSDP     M-SEARCH * HTTP/1.1 

Frame 1 (208 bytes on wire, 208 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:22.865052000
    [Time delta from previous captured frame: 0.000000000 seconds]
    [Time delta from previous displayed frame: 0.000000000 seconds]
    [Time since reference or first frame: 0.000000000 seconds]
    Frame Number: 1
    Frame Length: 208 bytes
    Capture Length: 208 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ipv6:udp:http]
    [Coloring Rule Name: HTTP]
    [Coloring Rule String: http || tcp.port == 80]
Ethernet II, Src: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b), Dst: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
    Destination: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        Address: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
    Source: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        Address: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IPv6 (0x86dd)
Internet Protocol Version 6
    0110 .... = Version: 6
        [0110 .... = This field makes the filter "ip.version == 6" possible: 6]
    .... 0000 0000 .... .... .... .... .... = Traffic class: 0x00000000
    .... .... .... 0000 0000 0000 0000 0000 = Flowlabel: 0x00000000
    Payload length: 154
    Next header: UDP (0x11)
    Hop limit: 1
    Source: fe80::8d69:edeb:b826:9b30 (fe80::8d69:edeb:b826:9b30)
    Destination: ff02::c (ff02::c)
User Datagram Protocol, Src Port: 65524 (65524), Dst Port: ssdp (1900)
    Source port: 65524 (65524)
    Destination port: ssdp (1900)
    Length: 154
    Checksum: 0xc8bd [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Hypertext Transfer Protocol
    M-SEARCH * HTTP/1.1\r\n
        [Expert Info (Chat/Sequence): M-SEARCH * HTTP/1.1\r\n]
            [Message: M-SEARCH * HTTP/1.1\r\n]
            [Severity level: Chat]
            [Group: Sequence]
        Request Method: M-SEARCH
        Request URI: *
        Request Version: HTTP/1.1
    Host:[FF02::C]:1900\r\n
    ST:urn:Microsoft Windows Peer Name Resolution Protocol: V4:IPV6:LinkLocal\r\n
    Man:"ssdp:discover"\r\n
    MX:3\r\n
    \r\n

No.     Time        Source                Destination           Protocol Info
      2 1.137501    0.0.0.0               255.255.255.255       DHCP     DHCP Request  - Transaction ID 0xb1156e7b

Frame 2 (342 bytes on wire, 342 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:24.002553000
    [Time delta from previous captured frame: 1.137501000 seconds]
    [Time delta from previous displayed frame: 1.137501000 seconds]
    [Time since reference or first frame: 1.137501000 seconds]
    Frame Number: 2
    Frame Length: 342 bytes
    Capture Length: 342 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:bootp]
    [Coloring Rule Name: UDP]
    [Coloring Rule String: udp]
Ethernet II, Src: Intel_5a:6a:68 (00:0c:f1:5a:6a:68), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
    Destination: Broadcast (ff:ff:ff:ff:ff:ff)
        Address: Broadcast (ff:ff:ff:ff:ff:ff)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
    Source: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 0.0.0.0 (0.0.0.0), Dst: 255.255.255.255 (255.255.255.255)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x10 (DSCP 0x04: Unknown DSCP; ECN: 0x00)
        0001 00.. = Differentiated Services Codepoint: Unknown (0x04)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 328
    Identification: 0x0000 (0)
    Flags: 0x00
        0.. = Reserved bit: Not Set
        .0. = Don't fragment: Not Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 128
    Protocol: UDP (0x11)
    Header checksum: 0x3996 [correct]
        [Good: True]
        [Bad : False]
    Source: 0.0.0.0 (0.0.0.0)
    Destination: 255.255.255.255 (255.255.255.255)
User Datagram Protocol, Src Port: bootpc (68), Dst Port: bootps (67)
    Source port: bootpc (68)
    Destination port: bootps (67)
    Length: 308
    Checksum: 0xa726 [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Bootstrap Protocol
    Message type: Boot Request (1)
    Hardware type: Ethernet
    Hardware address length: 6
    Hops: 0
    Transaction ID: 0xb1156e7b
    Seconds elapsed: 0
    Bootp flags: 0x0000 (Unicast)
        0... .... .... .... = Broadcast flag: Unicast
        .000 0000 0000 0000 = Reserved flags: 0x0000
    Client IP address: 0.0.0.0 (0.0.0.0)
    Your (client) IP address: 0.0.0.0 (0.0.0.0)
    Next server IP address: 0.0.0.0 (0.0.0.0)
    Relay agent IP address: 0.0.0.0 (0.0.0.0)
    Client MAC address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
    Client hardware address padding: 00000000000000000000
    Server host name not given
    Boot file name not given
    Magic cookie: (OK)
    Option: (t=53,l=1) DHCP Message Type = DHCP Request
        Option: (53) DHCP Message Type
        Length: 1
        Value: 03
    Option: (t=50,l=4) Requested IP Address = 192.168.1.5
        Option: (50) Requested IP Address
        Length: 4
        Value: C0A80105
    Option: (t=12,l=6) Host Name = "ubuntu"
        Option: (12) Host Name
        Length: 6
        Value: 7562756E7475
    Option: (t=55,l=13) Parameter Request List
        Option: (55) Parameter Request List
        Length: 13
        Value: 011C02030F06770C2C2F1A792A
        1 = Subnet Mask
        28 = Broadcast Address
        2 = Time Offset
        3 = Router
        15 = Domain Name
        6 = Domain Name Server
        119 = Domain Search [TODO]
        12 = Host Name
        44 = NetBIOS over TCP/IP Name Server
        47 = NetBIOS over TCP/IP Scope
        26 = Interface MTU
        121 = Classless Static Route
        42 = Network Time Protocol Servers
    End Option
    Padding

No.     Time        Source                Destination           Protocol Info
      3 1.145455    192.168.1.1           192.168.1.5           DHCP     DHCP ACK      - Transaction ID 0xb1156e7b

Frame 3 (590 bytes on wire, 590 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:24.010507000
    [Time delta from previous captured frame: 0.007954000 seconds]
    [Time delta from previous displayed frame: 0.007954000 seconds]
    [Time since reference or first frame: 1.145455000 seconds]
    Frame Number: 3
    Frame Length: 590 bytes
    Capture Length: 590 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:bootp]
    [Coloring Rule Name: UDP]
    [Coloring Rule String: udp]
Ethernet II, Src: D-Link_cc:48:a1 (00:15:e9:cc:48:a1), Dst: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
    Destination: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        Address: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.1 (192.168.1.1), Dst: 192.168.1.5 (192.168.1.5)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 576
    Identification: 0x0000 (0)
    Flags: 0x00
        0.. = Reserved bit: Not Set
        .0. = Don't fragment: Not Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 64
    Protocol: UDP (0x11)
    Header checksum: 0xf556 [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.1.1 (192.168.1.1)
    Destination: 192.168.1.5 (192.168.1.5)
User Datagram Protocol, Src Port: bootps (67), Dst Port: bootpc (68)
    Source port: bootps (67)
    Destination port: bootpc (68)
    Length: 556
    Checksum: 0xd192 [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Bootstrap Protocol
    Message type: Boot Reply (2)
    Hardware type: Ethernet
    Hardware address length: 6
    Hops: 0
    Transaction ID: 0xb1156e7b
    Seconds elapsed: 0
    Bootp flags: 0x0000 (Unicast)
        0... .... .... .... = Broadcast flag: Unicast
        .000 0000 0000 0000 = Reserved flags: 0x0000
    Client IP address: 0.0.0.0 (0.0.0.0)
    Your (client) IP address: 192.168.1.5 (192.168.1.5)
    Next server IP address: 0.0.0.0 (0.0.0.0)
    Relay agent IP address: 0.0.0.0 (0.0.0.0)
    Client MAC address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
    Client hardware address padding: 00000000000000000000
    Server host name not given
    Boot file name not given
    Magic cookie: (OK)
    Option: (t=53,l=1) DHCP Message Type = DHCP ACK
        Option: (53) DHCP Message Type
        Length: 1
        Value: 05
    Option: (t=54,l=4) DHCP Server Identifier = 192.168.1.1
        Option: (54) DHCP Server Identifier
        Length: 4
        Value: C0A80101
    Option: (t=51,l=4) IP Address Lease Time = 1 hour
        Option: (51) IP Address Lease Time
        Length: 4
        Value: 00000E10
    Option: (t=12,l=6) Host Name = "ubuntu"
        Option: (12) Host Name
        Length: 6
        Value: 7562756E7475
    Option: (t=1,l=4) Subnet Mask = 255.255.255.0
        Option: (1) Subnet Mask
        Length: 4
        Value: FFFFFF00
    Option: (t=3,l=4) Router = 192.168.1.1
        Option: (3) Router
        Length: 4
        Value: C0A80101
    Option: (t=6,l=4) Domain Name Server = 192.168.1.1
        Option: (6) Domain Name Server
        Length: 4
        Value: C0A80101
    End Option
    Padding

No.     Time        Source                Destination           Protocol Info
      4 1.175320    192.168.1.5           224.0.0.22            IGMP     V3 Membership Report / Join group 224.0.0.251 for any sources

Frame 4 (54 bytes on wire, 54 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:24.040372000
    [Time delta from previous captured frame: 0.029865000 seconds]
    [Time delta from previous displayed frame: 0.029865000 seconds]
    [Time since reference or first frame: 1.175320000 seconds]
    Frame Number: 4
    Frame Length: 54 bytes
    Capture Length: 54 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:igmp]
    [Coloring Rule Name: Routing]
    [Coloring Rule String: hsrp || eigrp || ospf || bgp || cdp || vrrp || gvrp || igmp || ismp]
Ethernet II, Src: Intel_5a:6a:68 (00:0c:f1:5a:6a:68), Dst: IPv4mcast_00:00:16 (01:00:5e:00:00:16)
    Destination: IPv4mcast_00:00:16 (01:00:5e:00:00:16)
        Address: IPv4mcast_00:00:16 (01:00:5e:00:00:16)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.5 (192.168.1.5), Dst: 224.0.0.22 (224.0.0.22)
    Version: 4
    Header length: 24 bytes
    Differentiated Services Field: 0xc0 (DSCP 0x30: Class Selector 6; ECN: 0x00)
        1100 00.. = Differentiated Services Codepoint: Class Selector 6 (0x30)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 40
    Identification: 0x0000 (0)
    Flags: 0x02 (Don't Fragment)
        0.. = Reserved bit: Not Set
        .1. = Don't fragment: Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 1
    Protocol: IGMP (0x02)
    Header checksum: 0x424c [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.1.5 (192.168.1.5)
    Destination: 224.0.0.22 (224.0.0.22)
    Options: (4 bytes)
        Router Alert: Every router examines packet
Internet Group Management Protocol
    IGMP Version: 3
    Type: Membership Report (0x22)
    Header checksum: 0xf902 [correct]
    Num Group Records: 1
    Group Record : 224.0.0.251  Change To Exclude Mode
        Record Type: Change To Exclude Mode (4)
        Aux Data Len: 0
        Num Src: 0
        Multicast Address: 224.0.0.251 (224.0.0.251)

No.     Time        Source                Destination           Protocol Info
      5 1.254016    192.168.1.5           224.0.0.251           MDNS     Standard query response PTR _workstation._tcp.local PTR ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local

Frame 5 (155 bytes on wire, 155 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:24.119068000
    [Time delta from previous captured frame: 0.078696000 seconds]
    [Time delta from previous displayed frame: 0.078696000 seconds]
    [Time since reference or first frame: 1.254016000 seconds]
    Frame Number: 5
    Frame Length: 155 bytes
    Capture Length: 155 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:dns]
    [Coloring Rule Name: TTL low or unexpected]
    [Coloring Rule String: ( ! ip.dst == 224.0.0.0/4 && ip.ttl < 5) || (ip.dst == 224.0.0.0/24 && ip.ttl != 1)]
Ethernet II, Src: Intel_5a:6a:68 (00:0c:f1:5a:6a:68), Dst: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
    Destination: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
        Address: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.5 (192.168.1.5), Dst: 224.0.0.251 (224.0.0.251)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 141
    Identification: 0x0000 (0)
    Flags: 0x02 (Don't Fragment)
        0.. = Reserved bit: Not Set
        .1. = Don't fragment: Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 255
        [Expert Info (Note/Sequence): "Time To Live" > 1 for a packet sent to the Local Network Control Block (see RFC 3171)]
            [Message: "Time To Live" > 1 for a packet sent to the Local Network Control Block (see RFC 3171)]
            [Severity level: Note]
            [Group: Sequence]
    Protocol: UDP (0x11)
    Header checksum: 0xd8b6 [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.1.5 (192.168.1.5)
    Destination: 224.0.0.251 (224.0.0.251)
User Datagram Protocol, Src Port: mdns (5353), Dst Port: mdns (5353)
    Source port: mdns (5353)
    Destination port: mdns (5353)
    Length: 121
    Checksum: 0x4e74 [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Domain Name System (response)
    [Request In: 8]
    [Time: -0.513200000 seconds]
    Transaction ID: 0x0000
    Flags: 0x8400 (Standard query response, No error)
        1... .... .... .... = Response: Message is a response
        .000 0... .... .... = Opcode: Standard query (0)
        .... .1.. .... .... = Authoritative: Server is an authority for domain
        .... ..0. .... .... = Truncated: Message is not truncated
        .... ...0 .... .... = Recursion desired: Don't do query recursively
        .... .... 0... .... = Recursion available: Server can't do recursive queries
        .... .... .0.. .... = Z: reserved (0)
        .... .... ..0. .... = Answer authenticated: Answer/authority portion was not authenticated by the server
        .... .... .... 0000 = Reply code: No error (0)
    Questions: 0
    Answer RRs: 2
    Authority RRs: 0
    Additional RRs: 0
    Answers
        _services._dns-sd._udp.local: type PTR, class IN, _workstation._tcp.local
            Name: _services._dns-sd._udp.local
            Type: PTR (Domain name pointer)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 1 hour, 15 minutes
            Data length: 20
            Domain name: _workstation._tcp.local
        _workstation._tcp.local: type PTR, class IN, ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local
            Name: _workstation._tcp.local
            Type: PTR (Domain name pointer)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 1 hour, 15 minutes
            Data length: 29
            Domain name: ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local

No.     Time        Source                Destination           Protocol Info
      6 1.266645    192.168.1.5           224.0.0.251           MDNS     Standard query ANY 8.6.a.6.a.5.e.f.f.f.1.f.c.0.2.0.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa, "QM" question ANY ubuntu.local, "QM" question ANY 5.1.168.192.in-addr.arpa, "QM" question ANY ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local, "QM" question

Frame 6 (355 bytes on wire, 355 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:24.131697000
    [Time delta from previous captured frame: 0.012629000 seconds]
    [Time delta from previous displayed frame: 0.012629000 seconds]
    [Time since reference or first frame: 1.266645000 seconds]
    Frame Number: 6
    Frame Length: 355 bytes
    Capture Length: 355 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:dns]
    [Coloring Rule Name: TTL low or unexpected]
    [Coloring Rule String: ( ! ip.dst == 224.0.0.0/4 && ip.ttl < 5) || (ip.dst == 224.0.0.0/24 && ip.ttl != 1)]
Ethernet II, Src: Intel_5a:6a:68 (00:0c:f1:5a:6a:68), Dst: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
    Destination: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
        Address: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.5 (192.168.1.5), Dst: 224.0.0.251 (224.0.0.251)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 341
    Identification: 0x0000 (0)
    Flags: 0x02 (Don't Fragment)
        0.. = Reserved bit: Not Set
        .1. = Don't fragment: Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 255
        [Expert Info (Note/Sequence): "Time To Live" > 1 for a packet sent to the Local Network Control Block (see RFC 3171)]
            [Message: "Time To Live" > 1 for a packet sent to the Local Network Control Block (see RFC 3171)]
            [Severity level: Note]
            [Group: Sequence]
    Protocol: UDP (0x11)
    Header checksum: 0xd7ee [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.1.5 (192.168.1.5)
    Destination: 224.0.0.251 (224.0.0.251)
User Datagram Protocol, Src Port: mdns (5353), Dst Port: mdns (5353)
    Source port: mdns (5353)
    Destination port: mdns (5353)
    Length: 321
    Checksum: 0x7c80 [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Domain Name System (query)
    [Response In: 18]
    Transaction ID: 0x0000
    Flags: 0x0000 (Standard query)
        0... .... .... .... = Response: Message is a query
        .000 0... .... .... = Opcode: Standard query (0)
        .... ..0. .... .... = Truncated: Message is not truncated
        .... ...0 .... .... = Recursion desired: Don't do query recursively
        .... .... .0.. .... = Z: reserved (0)
        .... .... ...0 .... = Non-authenticated data OK: Non-authenticated data is unacceptable
    Questions: 4
    Answer RRs: 0
    Authority RRs: 7
    Additional RRs: 0
    Queries
        8.6.a.6.a.5.e.f.f.f.1.f.c.0.2.0.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa: type ANY, class IN, "QM" question
            Name: 8.6.a.6.a.5.e.f.f.f.1.f.c.0.2.0.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa
            Type: ANY (Request for all records)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = "QU" question: False
        ubuntu.local: type ANY, class IN, "QM" question
            Name: ubuntu.local
            Type: ANY (Request for all records)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = "QU" question: False
        5.1.168.192.in-addr.arpa: type ANY, class IN, "QM" question
            Name: 5.1.168.192.in-addr.arpa
            Type: ANY (Request for all records)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = "QU" question: False
        ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local: type ANY, class IN, "QM" question
            Name: ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local
            Type: ANY (Request for all records)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = "QU" question: False
    Authoritative nameservers
        ubuntu.local: type A, class IN, addr 192.168.1.5
            Name: ubuntu.local
            Type: A (Host address)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 2 minutes
            Data length: 4
            Addr: 192.168.1.5
        5.1.168.192.in-addr.arpa: type PTR, class IN, ubuntu.local
            Name: 5.1.168.192.in-addr.arpa
            Type: PTR (Domain name pointer)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 2 minutes
            Data length: 2
            Domain name: ubuntu.local
        ubuntu.local: type HINFO, class IN, CPU I686, OS LINUX
            Name: ubuntu.local
            Type: HINFO (Host information)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 2 minutes
            Data length: 11
            CPU: I686
            OS: LINUX
        ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local: type SRV, class IN, priority 0, weight 0, port 9, target ubuntu.local
            Name: ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local
            Type: SRV (Service location)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 2 minutes
            Data length: 8
            Priority: 0
            Weight: 0
            Port: 9
            Target: ubuntu.local
        ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local: type TXT, class IN
            Name: ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local
            Type: TXT (Text strings)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 1 hour, 15 minutes
            Data length: 1
            Text: 
        ubuntu.local: type AAAA, class IN, addr fe80::20c:f1ff:fe5a:6a68
            Name: ubuntu.local
            Type: AAAA (IPv6 address)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 2 minutes
            Data length: 16
            Addr: fe80::20c:f1ff:fe5a:6a68
        8.6.a.6.a.5.e.f.f.f.1.f.c.0.2.0.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa: type PTR, class IN, ubuntu.local
            Name: 8.6.a.6.a.5.e.f.f.f.1.f.c.0.2.0.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa
            Type: PTR (Domain name pointer)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 2 minutes
            Data length: 2
            Domain name: ubuntu.local

No.     Time        Source                Destination           Protocol Info
      7 1.516328    192.168.1.5           224.0.0.251           MDNS     Standard query ANY 8.6.a.6.a.5.e.f.f.f.1.f.c.0.2.0.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa, "QM" question ANY ubuntu.local, "QM" question ANY 5.1.168.192.in-addr.arpa, "QM" question ANY ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local, "QM" question

Frame 7 (355 bytes on wire, 355 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:24.381380000
    [Time delta from previous captured frame: 0.249683000 seconds]
    [Time delta from previous displayed frame: 0.249683000 seconds]
    [Time since reference or first frame: 1.516328000 seconds]
    Frame Number: 7
    Frame Length: 355 bytes
    Capture Length: 355 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:dns]
    [Coloring Rule Name: TTL low or unexpected]
    [Coloring Rule String: ( ! ip.dst == 224.0.0.0/4 && ip.ttl < 5) || (ip.dst == 224.0.0.0/24 && ip.ttl != 1)]
Ethernet II, Src: Intel_5a:6a:68 (00:0c:f1:5a:6a:68), Dst: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
    Destination: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
        Address: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.5 (192.168.1.5), Dst: 224.0.0.251 (224.0.0.251)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 341
    Identification: 0x0000 (0)
    Flags: 0x02 (Don't Fragment)
        0.. = Reserved bit: Not Set
        .1. = Don't fragment: Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 255
        [Expert Info (Note/Sequence): "Time To Live" > 1 for a packet sent to the Local Network Control Block (see RFC 3171)]
            [Message: "Time To Live" > 1 for a packet sent to the Local Network Control Block (see RFC 3171)]
            [Severity level: Note]
            [Group: Sequence]
    Protocol: UDP (0x11)
    Header checksum: 0xd7ee [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.1.5 (192.168.1.5)
    Destination: 224.0.0.251 (224.0.0.251)
User Datagram Protocol, Src Port: mdns (5353), Dst Port: mdns (5353)
    Source port: mdns (5353)
    Destination port: mdns (5353)
    Length: 321
    Checksum: 0x7c80 [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Domain Name System (query)
    [Response In: 18]
    Transaction ID: 0x0000
    Flags: 0x0000 (Standard query)
        0... .... .... .... = Response: Message is a query
        .000 0... .... .... = Opcode: Standard query (0)
        .... ..0. .... .... = Truncated: Message is not truncated
        .... ...0 .... .... = Recursion desired: Don't do query recursively
        .... .... .0.. .... = Z: reserved (0)
        .... .... ...0 .... = Non-authenticated data OK: Non-authenticated data is unacceptable
    Questions: 4
    Answer RRs: 0
    Authority RRs: 7
    Additional RRs: 0
    Queries
        8.6.a.6.a.5.e.f.f.f.1.f.c.0.2.0.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa: type ANY, class IN, "QM" question
            Name: 8.6.a.6.a.5.e.f.f.f.1.f.c.0.2.0.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa
            Type: ANY (Request for all records)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = "QU" question: False
        ubuntu.local: type ANY, class IN, "QM" question
            Name: ubuntu.local
            Type: ANY (Request for all records)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = "QU" question: False
        5.1.168.192.in-addr.arpa: type ANY, class IN, "QM" question
            Name: 5.1.168.192.in-addr.arpa
            Type: ANY (Request for all records)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = "QU" question: False
        ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local: type ANY, class IN, "QM" question
            Name: ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local
            Type: ANY (Request for all records)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = "QU" question: False
    Authoritative nameservers
        ubuntu.local: type A, class IN, addr 192.168.1.5
            Name: ubuntu.local
            Type: A (Host address)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 2 minutes
            Data length: 4
            Addr: 192.168.1.5
        5.1.168.192.in-addr.arpa: type PTR, class IN, ubuntu.local
            Name: 5.1.168.192.in-addr.arpa
            Type: PTR (Domain name pointer)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 2 minutes
            Data length: 2
            Domain name: ubuntu.local
        ubuntu.local: type HINFO, class IN, CPU I686, OS LINUX
            Name: ubuntu.local
            Type: HINFO (Host information)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 2 minutes
            Data length: 11
            CPU: I686
            OS: LINUX
        ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local: type SRV, class IN, priority 0, weight 0, port 9, target ubuntu.local
            Name: ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local
            Type: SRV (Service location)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 2 minutes
            Data length: 8
            Priority: 0
            Weight: 0
            Port: 9
            Target: ubuntu.local
        ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local: type TXT, class IN
            Name: ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local
            Type: TXT (Text strings)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 1 hour, 15 minutes
            Data length: 1
            Text: 
        ubuntu.local: type AAAA, class IN, addr fe80::20c:f1ff:fe5a:6a68
            Name: ubuntu.local
            Type: AAAA (IPv6 address)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 2 minutes
            Data length: 16
            Addr: fe80::20c:f1ff:fe5a:6a68
        8.6.a.6.a.5.e.f.f.f.1.f.c.0.2.0.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa: type PTR, class IN, ubuntu.local
            Name: 8.6.a.6.a.5.e.f.f.f.1.f.c.0.2.0.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa
            Type: PTR (Domain name pointer)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 2 minutes
            Data length: 2
            Domain name: ubuntu.local

No.     Time        Source                Destination           Protocol Info
      8 1.767216    192.168.1.5           224.0.0.251           MDNS     Standard query ANY 8.6.a.6.a.5.e.f.f.f.1.f.c.0.2.0.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa, "QM" question ANY ubuntu.local, "QM" question ANY 5.1.168.192.in-addr.arpa, "QM" question ANY ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local, "QM" question

Frame 8 (355 bytes on wire, 355 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:24.632268000
    [Time delta from previous captured frame: 0.250888000 seconds]
    [Time delta from previous displayed frame: 0.250888000 seconds]
    [Time since reference or first frame: 1.767216000 seconds]
    Frame Number: 8
    Frame Length: 355 bytes
    Capture Length: 355 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:dns]
    [Coloring Rule Name: TTL low or unexpected]
    [Coloring Rule String: ( ! ip.dst == 224.0.0.0/4 && ip.ttl < 5) || (ip.dst == 224.0.0.0/24 && ip.ttl != 1)]
Ethernet II, Src: Intel_5a:6a:68 (00:0c:f1:5a:6a:68), Dst: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
    Destination: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
        Address: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.5 (192.168.1.5), Dst: 224.0.0.251 (224.0.0.251)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 341
    Identification: 0x0000 (0)
    Flags: 0x02 (Don't Fragment)
        0.. = Reserved bit: Not Set
        .1. = Don't fragment: Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 255
        [Expert Info (Note/Sequence): "Time To Live" > 1 for a packet sent to the Local Network Control Block (see RFC 3171)]
            [Message: "Time To Live" > 1 for a packet sent to the Local Network Control Block (see RFC 3171)]
            [Severity level: Note]
            [Group: Sequence]
    Protocol: UDP (0x11)
    Header checksum: 0xd7ee [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.1.5 (192.168.1.5)
    Destination: 224.0.0.251 (224.0.0.251)
User Datagram Protocol, Src Port: mdns (5353), Dst Port: mdns (5353)
    Source port: mdns (5353)
    Destination port: mdns (5353)
    Length: 321
    Checksum: 0x7c80 [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Domain Name System (query)
    [Response In: 18]
    Transaction ID: 0x0000
    Flags: 0x0000 (Standard query)
        0... .... .... .... = Response: Message is a query
        .000 0... .... .... = Opcode: Standard query (0)
        .... ..0. .... .... = Truncated: Message is not truncated
        .... ...0 .... .... = Recursion desired: Don't do query recursively
        .... .... .0.. .... = Z: reserved (0)
        .... .... ...0 .... = Non-authenticated data OK: Non-authenticated data is unacceptable
    Questions: 4
    Answer RRs: 0
    Authority RRs: 7
    Additional RRs: 0
    Queries
        8.6.a.6.a.5.e.f.f.f.1.f.c.0.2.0.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa: type ANY, class IN, "QM" question
            Name: 8.6.a.6.a.5.e.f.f.f.1.f.c.0.2.0.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa
            Type: ANY (Request for all records)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = "QU" question: False
        ubuntu.local: type ANY, class IN, "QM" question
            Name: ubuntu.local
            Type: ANY (Request for all records)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = "QU" question: False
        5.1.168.192.in-addr.arpa: type ANY, class IN, "QM" question
            Name: 5.1.168.192.in-addr.arpa
            Type: ANY (Request for all records)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = "QU" question: False
        ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local: type ANY, class IN, "QM" question
            Name: ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local
            Type: ANY (Request for all records)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = "QU" question: False
    Authoritative nameservers
        ubuntu.local: type A, class IN, addr 192.168.1.5
            Name: ubuntu.local
            Type: A (Host address)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 2 minutes
            Data length: 4
            Addr: 192.168.1.5
        5.1.168.192.in-addr.arpa: type PTR, class IN, ubuntu.local
            Name: 5.1.168.192.in-addr.arpa
            Type: PTR (Domain name pointer)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 2 minutes
            Data length: 2
            Domain name: ubuntu.local
        ubuntu.local: type HINFO, class IN, CPU I686, OS LINUX
            Name: ubuntu.local
            Type: HINFO (Host information)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 2 minutes
            Data length: 11
            CPU: I686
            OS: LINUX
        ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local: type SRV, class IN, priority 0, weight 0, port 9, target ubuntu.local
            Name: ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local
            Type: SRV (Service location)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 2 minutes
            Data length: 8
            Priority: 0
            Weight: 0
            Port: 9
            Target: ubuntu.local
        ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local: type TXT, class IN
            Name: ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local
            Type: TXT (Text strings)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 1 hour, 15 minutes
            Data length: 1
            Text: 
        ubuntu.local: type AAAA, class IN, addr fe80::20c:f1ff:fe5a:6a68
            Name: ubuntu.local
            Type: AAAA (IPv6 address)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 2 minutes
            Data length: 16
            Addr: fe80::20c:f1ff:fe5a:6a68
        8.6.a.6.a.5.e.f.f.f.1.f.c.0.2.0.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa: type PTR, class IN, ubuntu.local
            Name: 8.6.a.6.a.5.e.f.f.f.1.f.c.0.2.0.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa
            Type: PTR (Domain name pointer)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 2 minutes
            Data length: 2
            Domain name: ubuntu.local

No.     Time        Source                Destination           Protocol Info
      9 1.967650    192.168.1.5           224.0.0.251           MDNS     Standard query response PTR, cache flush ubuntu.local A, cache flush 192.168.1.5 PTR, cache flush ubuntu.local HINFO, cache flush I686 LINUX SRV, cache flush 0 0 9 ubuntu.local TXT, cache flush AAAA, cache flush fe80::20c:f1ff:fe5a:6a68

Frame 9 (331 bytes on wire, 331 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:24.832702000
    [Time delta from previous captured frame: 0.200434000 seconds]
    [Time delta from previous displayed frame: 0.200434000 seconds]
    [Time since reference or first frame: 1.967650000 seconds]
    Frame Number: 9
    Frame Length: 331 bytes
    Capture Length: 331 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:dns]
    [Coloring Rule Name: TTL low or unexpected]
    [Coloring Rule String: ( ! ip.dst == 224.0.0.0/4 && ip.ttl < 5) || (ip.dst == 224.0.0.0/24 && ip.ttl != 1)]
Ethernet II, Src: Intel_5a:6a:68 (00:0c:f1:5a:6a:68), Dst: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
    Destination: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
        Address: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.5 (192.168.1.5), Dst: 224.0.0.251 (224.0.0.251)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 317
    Identification: 0x0000 (0)
    Flags: 0x02 (Don't Fragment)
        0.. = Reserved bit: Not Set
        .1. = Don't fragment: Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 255
        [Expert Info (Note/Sequence): "Time To Live" > 1 for a packet sent to the Local Network Control Block (see RFC 3171)]
            [Message: "Time To Live" > 1 for a packet sent to the Local Network Control Block (see RFC 3171)]
            [Severity level: Note]
            [Group: Sequence]
    Protocol: UDP (0x11)
    Header checksum: 0xd806 [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.1.5 (192.168.1.5)
    Destination: 224.0.0.251 (224.0.0.251)
User Datagram Protocol, Src Port: mdns (5353), Dst Port: mdns (5353)
    Source port: mdns (5353)
    Destination port: mdns (5353)
    Length: 297
    Checksum: 0xcd5a [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Domain Name System (response)
    [Request In: 8]
    [Time: 0.200434000 seconds]
    Transaction ID: 0x0000
    Flags: 0x8400 (Standard query response, No error)
        1... .... .... .... = Response: Message is a response
        .000 0... .... .... = Opcode: Standard query (0)
        .... .1.. .... .... = Authoritative: Server is an authority for domain
        .... ..0. .... .... = Truncated: Message is not truncated
        .... ...0 .... .... = Recursion desired: Don't do query recursively
        .... .... 0... .... = Recursion available: Server can't do recursive queries
        .... .... .0.. .... = Z: reserved (0)
        .... .... ..0. .... = Answer authenticated: Answer/authority portion was not authenticated by the server
        .... .... .... 0000 = Reply code: No error (0)
    Questions: 0
    Answer RRs: 7
    Authority RRs: 0
    Additional RRs: 0
    Answers
        8.6.a.6.a.5.e.f.f.f.1.f.c.0.2.0.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa: type PTR, class IN, cache flush, ubuntu.local
            Name: 8.6.a.6.a.5.e.f.f.f.1.f.c.0.2.0.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa
            Type: PTR (Domain name pointer)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 2 minutes
            Data length: 14
            Domain name: ubuntu.local
        ubuntu.local: type A, class IN, cache flush, addr 192.168.1.5
            Name: ubuntu.local
            Type: A (Host address)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 2 minutes
            Data length: 4
            Addr: 192.168.1.5
        5.1.168.192.in-addr.arpa: type PTR, class IN, cache flush, ubuntu.local
            Name: 5.1.168.192.in-addr.arpa
            Type: PTR (Domain name pointer)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 2 minutes
            Data length: 2
            Domain name: ubuntu.local
        ubuntu.local: type HINFO, class IN, cache flush, CPU I686, OS LINUX
            Name: ubuntu.local
            Type: HINFO (Host information)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 2 minutes
            Data length: 11
            CPU: I686
            OS: LINUX
        ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local: type SRV, class IN, cache flush, priority 0, weight 0, port 9, target ubuntu.local
            Name: ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local
            Type: SRV (Service location)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 2 minutes
            Data length: 8
            Priority: 0
            Weight: 0
            Port: 9
            Target: ubuntu.local
        ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local: type TXT, class IN, cache flush
            Name: ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local
            Type: TXT (Text strings)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 1 hour, 15 minutes
            Data length: 1
            Text: 
        ubuntu.local: type AAAA, class IN, cache flush, addr fe80::20c:f1ff:fe5a:6a68
            Name: ubuntu.local
            Type: AAAA (IPv6 address)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 2 minutes
            Data length: 16
            Addr: fe80::20c:f1ff:fe5a:6a68

No.     Time        Source                Destination           Protocol Info
     10 2.300988    192.168.1.5           224.0.0.251           MDNS     Standard query response PTR _workstation._tcp.local PTR ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local

Frame 10 (155 bytes on wire, 155 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:25.166040000
    [Time delta from previous captured frame: 0.333338000 seconds]
    [Time delta from previous displayed frame: 0.333338000 seconds]
    [Time since reference or first frame: 2.300988000 seconds]
    Frame Number: 10
    Frame Length: 155 bytes
    Capture Length: 155 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:dns]
    [Coloring Rule Name: TTL low or unexpected]
    [Coloring Rule String: ( ! ip.dst == 224.0.0.0/4 && ip.ttl < 5) || (ip.dst == 224.0.0.0/24 && ip.ttl != 1)]
Ethernet II, Src: Intel_5a:6a:68 (00:0c:f1:5a:6a:68), Dst: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
    Destination: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
        Address: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.5 (192.168.1.5), Dst: 224.0.0.251 (224.0.0.251)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 141
    Identification: 0x0000 (0)
    Flags: 0x02 (Don't Fragment)
        0.. = Reserved bit: Not Set
        .1. = Don't fragment: Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 255
        [Expert Info (Note/Sequence): "Time To Live" > 1 for a packet sent to the Local Network Control Block (see RFC 3171)]
            [Message: "Time To Live" > 1 for a packet sent to the Local Network Control Block (see RFC 3171)]
            [Severity level: Note]
            [Group: Sequence]
    Protocol: UDP (0x11)
    Header checksum: 0xd8b6 [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.1.5 (192.168.1.5)
    Destination: 224.0.0.251 (224.0.0.251)
User Datagram Protocol, Src Port: mdns (5353), Dst Port: mdns (5353)
    Source port: mdns (5353)
    Destination port: mdns (5353)
    Length: 121
    Checksum: 0x4e74 [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Domain Name System (response)
    [Request In: 8]
    [Time: 0.533772000 seconds]
    Transaction ID: 0x0000
    Flags: 0x8400 (Standard query response, No error)
        1... .... .... .... = Response: Message is a response
        .000 0... .... .... = Opcode: Standard query (0)
        .... .1.. .... .... = Authoritative: Server is an authority for domain
        .... ..0. .... .... = Truncated: Message is not truncated
        .... ...0 .... .... = Recursion desired: Don't do query recursively
        .... .... 0... .... = Recursion available: Server can't do recursive queries
        .... .... .0.. .... = Z: reserved (0)
        .... .... ..0. .... = Answer authenticated: Answer/authority portion was not authenticated by the server
        .... .... .... 0000 = Reply code: No error (0)
    Questions: 0
    Answer RRs: 2
    Authority RRs: 0
    Additional RRs: 0
    Answers
        _services._dns-sd._udp.local: type PTR, class IN, _workstation._tcp.local
            Name: _services._dns-sd._udp.local
            Type: PTR (Domain name pointer)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 1 hour, 15 minutes
            Data length: 20
            Domain name: _workstation._tcp.local
        _workstation._tcp.local: type PTR, class IN, ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local
            Name: _workstation._tcp.local
            Type: PTR (Domain name pointer)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 1 hour, 15 minutes
            Data length: 29
            Domain name: ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local

No.     Time        Source                Destination           Protocol Info
     11 2.371292    Intel_5a:6a:68        Broadcast             ARP      Who has 192.168.1.1?  Tell 192.168.1.5

Frame 11 (42 bytes on wire, 42 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:25.236344000
    [Time delta from previous captured frame: 0.070304000 seconds]
    [Time delta from previous displayed frame: 0.070304000 seconds]
    [Time since reference or first frame: 2.371292000 seconds]
    Frame Number: 11
    Frame Length: 42 bytes
    Capture Length: 42 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:arp]
    [Coloring Rule Name: ARP]
    [Coloring Rule String: arp]
Ethernet II, Src: Intel_5a:6a:68 (00:0c:f1:5a:6a:68), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
    Destination: Broadcast (ff:ff:ff:ff:ff:ff)
        Address: Broadcast (ff:ff:ff:ff:ff:ff)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
    Source: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: ARP (0x0806)
Address Resolution Protocol (request)
    Hardware type: Ethernet (0x0001)
    Protocol type: IP (0x0800)
    Hardware size: 6
    Protocol size: 4
    Opcode: request (0x0001)
    [Is gratuitous: False]
    Sender MAC address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
    Sender IP address: 192.168.1.5 (192.168.1.5)
    Target MAC address: 00:00:00_00:00:00 (00:00:00:00:00:00)
    Target IP address: 192.168.1.1 (192.168.1.1)

No.     Time        Source                Destination           Protocol Info
     12 2.374498    D-Link_cc:48:a1       Intel_5a:6a:68        ARP      192.168.1.1 is at 00:15:e9:cc:48:a1

Frame 12 (42 bytes on wire, 42 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:25.239550000
    [Time delta from previous captured frame: 0.003206000 seconds]
    [Time delta from previous displayed frame: 0.003206000 seconds]
    [Time since reference or first frame: 2.374498000 seconds]
    Frame Number: 12
    Frame Length: 42 bytes
    Capture Length: 42 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:arp]
    [Coloring Rule Name: ARP]
    [Coloring Rule String: arp]
Ethernet II, Src: D-Link_cc:48:a1 (00:15:e9:cc:48:a1), Dst: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
    Destination: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        Address: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: ARP (0x0806)
Address Resolution Protocol (reply)
    Hardware type: Ethernet (0x0001)
    Protocol type: IP (0x0800)
    Hardware size: 6
    Protocol size: 4
    Opcode: reply (0x0002)
    [Is gratuitous: False]
    Sender MAC address: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
    Sender IP address: 192.168.1.1 (192.168.1.1)
    Target MAC address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
    Target IP address: 192.168.1.5 (192.168.1.5)

No.     Time        Source                Destination           Protocol Info
     13 2.374515    192.168.1.5           192.168.1.1           DNS      Standard query SOA local

Frame 13 (65 bytes on wire, 65 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:25.239567000
    [Time delta from previous captured frame: 0.000017000 seconds]
    [Time delta from previous displayed frame: 0.000017000 seconds]
    [Time since reference or first frame: 2.374515000 seconds]
    Frame Number: 13
    Frame Length: 65 bytes
    Capture Length: 65 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:dns]
    [Coloring Rule Name: UDP]
    [Coloring Rule String: udp]
Ethernet II, Src: Intel_5a:6a:68 (00:0c:f1:5a:6a:68), Dst: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
    Destination: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        Address: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.5 (192.168.1.5), Dst: 192.168.1.1 (192.168.1.1)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 51
    Identification: 0x0123 (291)
    Flags: 0x00
        0.. = Reserved bit: Not Set
        .0. = Don't fragment: Not Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 64
    Protocol: UDP (0x11)
    Header checksum: 0xf640 [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.1.5 (192.168.1.5)
    Destination: 192.168.1.1 (192.168.1.1)
User Datagram Protocol, Src Port: 44780 (44780), Dst Port: domain (53)
    Source port: 44780 (44780)
    Destination port: domain (53)
    Length: 31
    Checksum: 0xae2c [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Domain Name System (query)
    Transaction ID: 0x40ce
    Flags: 0x0100 (Standard query)
        0... .... .... .... = Response: Message is a query
        .000 0... .... .... = Opcode: Standard query (0)
        .... ..0. .... .... = Truncated: Message is not truncated
        .... ...1 .... .... = Recursion desired: Do query recursively
        .... .... .0.. .... = Z: reserved (0)
        .... .... ...0 .... = Non-authenticated data OK: Non-authenticated data is unacceptable
    Questions: 1
    Answer RRs: 0
    Authority RRs: 0
    Additional RRs: 0
    Queries
        local: type SOA, class IN
            Name: local
            Type: SOA (Start of zone of authority)
            Class: IN (0x0001)

No.     Time        Source                Destination           Protocol Info
     14 3.013833    192.168.1.5           224.0.0.251           MDNS     Standard query response PTR, cache flush ubuntu.local A, cache flush 192.168.1.5 PTR, cache flush ubuntu.local HINFO, cache flush I686 LINUX SRV, cache flush 0 0 9 ubuntu.local TXT, cache flush AAAA, cache flush fe80::20c:f1ff:fe5a:6a68

Frame 14 (331 bytes on wire, 331 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:25.878885000
    [Time delta from previous captured frame: 0.639318000 seconds]
    [Time delta from previous displayed frame: 0.639318000 seconds]
    [Time since reference or first frame: 3.013833000 seconds]
    Frame Number: 14
    Frame Length: 331 bytes
    Capture Length: 331 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:dns]
    [Coloring Rule Name: TTL low or unexpected]
    [Coloring Rule String: ( ! ip.dst == 224.0.0.0/4 && ip.ttl < 5) || (ip.dst == 224.0.0.0/24 && ip.ttl != 1)]
Ethernet II, Src: Intel_5a:6a:68 (00:0c:f1:5a:6a:68), Dst: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
    Destination: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
        Address: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.5 (192.168.1.5), Dst: 224.0.0.251 (224.0.0.251)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 317
    Identification: 0x0000 (0)
    Flags: 0x02 (Don't Fragment)
        0.. = Reserved bit: Not Set
        .1. = Don't fragment: Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 255
        [Expert Info (Note/Sequence): "Time To Live" > 1 for a packet sent to the Local Network Control Block (see RFC 3171)]
            [Message: "Time To Live" > 1 for a packet sent to the Local Network Control Block (see RFC 3171)]
            [Severity level: Note]
            [Group: Sequence]
    Protocol: UDP (0x11)
    Header checksum: 0xd806 [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.1.5 (192.168.1.5)
    Destination: 224.0.0.251 (224.0.0.251)
User Datagram Protocol, Src Port: mdns (5353), Dst Port: mdns (5353)
    Source port: mdns (5353)
    Destination port: mdns (5353)
    Length: 297
    Checksum: 0xcd5a [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Domain Name System (response)
    [Request In: 8]
    [Time: 1.246617000 seconds]
    Transaction ID: 0x0000
    Flags: 0x8400 (Standard query response, No error)
        1... .... .... .... = Response: Message is a response
        .000 0... .... .... = Opcode: Standard query (0)
        .... .1.. .... .... = Authoritative: Server is an authority for domain
        .... ..0. .... .... = Truncated: Message is not truncated
        .... ...0 .... .... = Recursion desired: Don't do query recursively
        .... .... 0... .... = Recursion available: Server can't do recursive queries
        .... .... .0.. .... = Z: reserved (0)
        .... .... ..0. .... = Answer authenticated: Answer/authority portion was not authenticated by the server
        .... .... .... 0000 = Reply code: No error (0)
    Questions: 0
    Answer RRs: 7
    Authority RRs: 0
    Additional RRs: 0
    Answers
        8.6.a.6.a.5.e.f.f.f.1.f.c.0.2.0.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa: type PTR, class IN, cache flush, ubuntu.local
            Name: 8.6.a.6.a.5.e.f.f.f.1.f.c.0.2.0.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa
            Type: PTR (Domain name pointer)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 2 minutes
            Data length: 14
            Domain name: ubuntu.local
        ubuntu.local: type A, class IN, cache flush, addr 192.168.1.5
            Name: ubuntu.local
            Type: A (Host address)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 2 minutes
            Data length: 4
            Addr: 192.168.1.5
        5.1.168.192.in-addr.arpa: type PTR, class IN, cache flush, ubuntu.local
            Name: 5.1.168.192.in-addr.arpa
            Type: PTR (Domain name pointer)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 2 minutes
            Data length: 2
            Domain name: ubuntu.local
        ubuntu.local: type HINFO, class IN, cache flush, CPU I686, OS LINUX
            Name: ubuntu.local
            Type: HINFO (Host information)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 2 minutes
            Data length: 11
            CPU: I686
            OS: LINUX
        ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local: type SRV, class IN, cache flush, priority 0, weight 0, port 9, target ubuntu.local
            Name: ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local
            Type: SRV (Service location)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 2 minutes
            Data length: 8
            Priority: 0
            Weight: 0
            Port: 9
            Target: ubuntu.local
        ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local: type TXT, class IN, cache flush
            Name: ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local
            Type: TXT (Text strings)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 1 hour, 15 minutes
            Data length: 1
            Text: 
        ubuntu.local: type AAAA, class IN, cache flush, addr fe80::20c:f1ff:fe5a:6a68
            Name: ubuntu.local
            Type: AAAA (IPv6 address)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 2 minutes
            Data length: 16
            Addr: fe80::20c:f1ff:fe5a:6a68

No.     Time        Source                Destination           Protocol Info
     15 3.635326    192.168.1.5           224.0.0.22            IGMP     V3 Membership Report / Join group 224.0.0.251 for any sources

Frame 15 (54 bytes on wire, 54 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:26.500378000
    [Time delta from previous captured frame: 0.621493000 seconds]
    [Time delta from previous displayed frame: 0.621493000 seconds]
    [Time since reference or first frame: 3.635326000 seconds]
    Frame Number: 15
    Frame Length: 54 bytes
    Capture Length: 54 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:igmp]
    [Coloring Rule Name: Routing]
    [Coloring Rule String: hsrp || eigrp || ospf || bgp || cdp || vrrp || gvrp || igmp || ismp]
Ethernet II, Src: Intel_5a:6a:68 (00:0c:f1:5a:6a:68), Dst: IPv4mcast_00:00:16 (01:00:5e:00:00:16)
    Destination: IPv4mcast_00:00:16 (01:00:5e:00:00:16)
        Address: IPv4mcast_00:00:16 (01:00:5e:00:00:16)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.5 (192.168.1.5), Dst: 224.0.0.22 (224.0.0.22)
    Version: 4
    Header length: 24 bytes
    Differentiated Services Field: 0xc0 (DSCP 0x30: Class Selector 6; ECN: 0x00)
        1100 00.. = Differentiated Services Codepoint: Class Selector 6 (0x30)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 40
    Identification: 0x0000 (0)
    Flags: 0x02 (Don't Fragment)
        0.. = Reserved bit: Not Set
        .1. = Don't fragment: Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 1
    Protocol: IGMP (0x02)
    Header checksum: 0x424c [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.1.5 (192.168.1.5)
    Destination: 224.0.0.22 (224.0.0.22)
    Options: (4 bytes)
        Router Alert: Every router examines packet
Internet Group Management Protocol
    IGMP Version: 3
    Type: Membership Report (0x22)
    Header checksum: 0xf902 [correct]
    Num Group Records: 1
    Group Record : 224.0.0.251  Change To Exclude Mode
        Record Type: Change To Exclude Mode (4)
        Aux Data Len: 0
        Num Src: 0
        Multicast Address: 224.0.0.251 (224.0.0.251)

No.     Time        Source                Destination           Protocol Info
     16 4.028392    fe80::8d69:edeb:b826:9b30 ff02::c               SSDP     M-SEARCH * HTTP/1.1 

Frame 16 (208 bytes on wire, 208 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:26.893444000
    [Time delta from previous captured frame: 0.393066000 seconds]
    [Time delta from previous displayed frame: 0.393066000 seconds]
    [Time since reference or first frame: 4.028392000 seconds]
    Frame Number: 16
    Frame Length: 208 bytes
    Capture Length: 208 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ipv6:udp:http]
    [Coloring Rule Name: HTTP]
    [Coloring Rule String: http || tcp.port == 80]
Ethernet II, Src: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b), Dst: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
    Destination: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        Address: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
    Source: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        Address: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IPv6 (0x86dd)
Internet Protocol Version 6
    0110 .... = Version: 6
        [0110 .... = This field makes the filter "ip.version == 6" possible: 6]
    .... 0000 0000 .... .... .... .... .... = Traffic class: 0x00000000
    .... .... .... 0000 0000 0000 0000 0000 = Flowlabel: 0x00000000
    Payload length: 154
    Next header: UDP (0x11)
    Hop limit: 1
    Source: fe80::8d69:edeb:b826:9b30 (fe80::8d69:edeb:b826:9b30)
    Destination: ff02::c (ff02::c)
User Datagram Protocol, Src Port: 65524 (65524), Dst Port: ssdp (1900)
    Source port: 65524 (65524)
    Destination port: ssdp (1900)
    Length: 154
    Checksum: 0xc8bd [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Hypertext Transfer Protocol
    M-SEARCH * HTTP/1.1\r\n
        [Expert Info (Chat/Sequence): M-SEARCH * HTTP/1.1\r\n]
            [Message: M-SEARCH * HTTP/1.1\r\n]
            [Severity level: Chat]
            [Group: Sequence]
        Request Method: M-SEARCH
        Request URI: *
        Request Version: HTTP/1.1
    Host:[FF02::C]:1900\r\n
    ST:urn:Microsoft Windows Peer Name Resolution Protocol: V4:IPV6:LinkLocal\r\n
    Man:"ssdp:discover"\r\n
    MX:3\r\n
    \r\n

No.     Time        Source                Destination           Protocol Info
     17 4.346584    192.168.1.5           224.0.0.251           MDNS     Standard query response PTR _workstation._tcp.local PTR ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local TXT, cache flush SRV, cache flush 0 0 9 ubuntu.local AAAA, cache flush fe80::20c:f1ff:fe5a:6a68 A, cache flush 192.168.1.5

Frame 17 (239 bytes on wire, 239 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:27.211636000
    [Time delta from previous captured frame: 0.318192000 seconds]
    [Time delta from previous displayed frame: 0.318192000 seconds]
    [Time since reference or first frame: 4.346584000 seconds]
    Frame Number: 17
    Frame Length: 239 bytes
    Capture Length: 239 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:dns]
    [Coloring Rule Name: TTL low or unexpected]
    [Coloring Rule String: ( ! ip.dst == 224.0.0.0/4 && ip.ttl < 5) || (ip.dst == 224.0.0.0/24 && ip.ttl != 1)]
Ethernet II, Src: Intel_5a:6a:68 (00:0c:f1:5a:6a:68), Dst: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
    Destination: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
        Address: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.5 (192.168.1.5), Dst: 224.0.0.251 (224.0.0.251)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 225
    Identification: 0x0000 (0)
    Flags: 0x02 (Don't Fragment)
        0.. = Reserved bit: Not Set
        .1. = Don't fragment: Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 255
        [Expert Info (Note/Sequence): "Time To Live" > 1 for a packet sent to the Local Network Control Block (see RFC 3171)]
            [Message: "Time To Live" > 1 for a packet sent to the Local Network Control Block (see RFC 3171)]
            [Severity level: Note]
            [Group: Sequence]
    Protocol: UDP (0x11)
    Header checksum: 0xd862 [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.1.5 (192.168.1.5)
    Destination: 224.0.0.251 (224.0.0.251)
User Datagram Protocol, Src Port: mdns (5353), Dst Port: mdns (5353)
    Source port: mdns (5353)
    Destination port: mdns (5353)
    Length: 205
    Checksum: 0x5db0 [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Domain Name System (response)
    [Request In: 8]
    [Time: 2.579368000 seconds]
    Transaction ID: 0x0000
    Flags: 0x8400 (Standard query response, No error)
        1... .... .... .... = Response: Message is a response
        .000 0... .... .... = Opcode: Standard query (0)
        .... .1.. .... .... = Authoritative: Server is an authority for domain
        .... ..0. .... .... = Truncated: Message is not truncated
        .... ...0 .... .... = Recursion desired: Don't do query recursively
        .... .... 0... .... = Recursion available: Server can't do recursive queries
        .... .... .0.. .... = Z: reserved (0)
        .... .... ..0. .... = Answer authenticated: Answer/authority portion was not authenticated by the server
        .... .... .... 0000 = Reply code: No error (0)
    Questions: 0
    Answer RRs: 6
    Authority RRs: 0
    Additional RRs: 0
    Answers
        _services._dns-sd._udp.local: type PTR, class IN, _workstation._tcp.local
            Name: _services._dns-sd._udp.local
            Type: PTR (Domain name pointer)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 1 hour, 15 minutes
            Data length: 20
            Domain name: _workstation._tcp.local
        _workstation._tcp.local: type PTR, class IN, ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local
            Name: _workstation._tcp.local
            Type: PTR (Domain name pointer)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 1 hour, 15 minutes
            Data length: 29
            Domain name: ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local
        ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local: type TXT, class IN, cache flush
            Name: ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local
            Type: TXT (Text strings)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 1 hour, 15 minutes
            Data length: 1
            Text: 
        ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local: type SRV, class IN, cache flush, priority 0, weight 0, port 9, target ubuntu.local
            Name: ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local
            Type: SRV (Service location)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 2 minutes
            Data length: 15
            Priority: 0
            Weight: 0
            Port: 9
            Target: ubuntu.local
        ubuntu.local: type AAAA, class IN, cache flush, addr fe80::20c:f1ff:fe5a:6a68
            Name: ubuntu.local
            Type: AAAA (IPv6 address)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 2 minutes
            Data length: 16
            Addr: fe80::20c:f1ff:fe5a:6a68
        ubuntu.local: type A, class IN, cache flush, addr 192.168.1.5
            Name: ubuntu.local
            Type: A (Host address)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 2 minutes
            Data length: 4
            Addr: 192.168.1.5

No.     Time        Source                Destination           Protocol Info
     18 5.060527    192.168.1.5           224.0.0.251           MDNS     Standard query response PTR, cache flush ubuntu.local A, cache flush 192.168.1.5 PTR, cache flush ubuntu.local HINFO, cache flush I686 LINUX SRV, cache flush 0 0 9 ubuntu.local TXT, cache flush AAAA, cache flush fe80::20c:f1ff:fe5a:6a68

Frame 18 (331 bytes on wire, 331 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:27.925579000
    [Time delta from previous captured frame: 0.713943000 seconds]
    [Time delta from previous displayed frame: 0.713943000 seconds]
    [Time since reference or first frame: 5.060527000 seconds]
    Frame Number: 18
    Frame Length: 331 bytes
    Capture Length: 331 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:dns]
    [Coloring Rule Name: TTL low or unexpected]
    [Coloring Rule String: ( ! ip.dst == 224.0.0.0/4 && ip.ttl < 5) || (ip.dst == 224.0.0.0/24 && ip.ttl != 1)]
Ethernet II, Src: Intel_5a:6a:68 (00:0c:f1:5a:6a:68), Dst: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
    Destination: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
        Address: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.5 (192.168.1.5), Dst: 224.0.0.251 (224.0.0.251)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 317
    Identification: 0x0000 (0)
    Flags: 0x02 (Don't Fragment)
        0.. = Reserved bit: Not Set
        .1. = Don't fragment: Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 255
        [Expert Info (Note/Sequence): "Time To Live" > 1 for a packet sent to the Local Network Control Block (see RFC 3171)]
            [Message: "Time To Live" > 1 for a packet sent to the Local Network Control Block (see RFC 3171)]
            [Severity level: Note]
            [Group: Sequence]
    Protocol: UDP (0x11)
    Header checksum: 0xd806 [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.1.5 (192.168.1.5)
    Destination: 224.0.0.251 (224.0.0.251)
User Datagram Protocol, Src Port: mdns (5353), Dst Port: mdns (5353)
    Source port: mdns (5353)
    Destination port: mdns (5353)
    Length: 297
    Checksum: 0xcd5a [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Domain Name System (response)
    [Request In: 8]
    [Time: 3.293311000 seconds]
    Transaction ID: 0x0000
    Flags: 0x8400 (Standard query response, No error)
        1... .... .... .... = Response: Message is a response
        .000 0... .... .... = Opcode: Standard query (0)
        .... .1.. .... .... = Authoritative: Server is an authority for domain
        .... ..0. .... .... = Truncated: Message is not truncated
        .... ...0 .... .... = Recursion desired: Don't do query recursively
        .... .... 0... .... = Recursion available: Server can't do recursive queries
        .... .... .0.. .... = Z: reserved (0)
        .... .... ..0. .... = Answer authenticated: Answer/authority portion was not authenticated by the server
        .... .... .... 0000 = Reply code: No error (0)
    Questions: 0
    Answer RRs: 7
    Authority RRs: 0
    Additional RRs: 0
    Answers
        8.6.a.6.a.5.e.f.f.f.1.f.c.0.2.0.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa: type PTR, class IN, cache flush, ubuntu.local
            Name: 8.6.a.6.a.5.e.f.f.f.1.f.c.0.2.0.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa
            Type: PTR (Domain name pointer)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 2 minutes
            Data length: 14
            Domain name: ubuntu.local
        ubuntu.local: type A, class IN, cache flush, addr 192.168.1.5
            Name: ubuntu.local
            Type: A (Host address)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 2 minutes
            Data length: 4
            Addr: 192.168.1.5
        5.1.168.192.in-addr.arpa: type PTR, class IN, cache flush, ubuntu.local
            Name: 5.1.168.192.in-addr.arpa
            Type: PTR (Domain name pointer)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 2 minutes
            Data length: 2
            Domain name: ubuntu.local
        ubuntu.local: type HINFO, class IN, cache flush, CPU I686, OS LINUX
            Name: ubuntu.local
            Type: HINFO (Host information)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 2 minutes
            Data length: 11
            CPU: I686
            OS: LINUX
        ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local: type SRV, class IN, cache flush, priority 0, weight 0, port 9, target ubuntu.local
            Name: ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local
            Type: SRV (Service location)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 2 minutes
            Data length: 8
            Priority: 0
            Weight: 0
            Port: 9
            Target: ubuntu.local
        ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local: type TXT, class IN, cache flush
            Name: ubuntu [00:0c:f1:5a:6a:68]._workstation._tcp.local
            Type: TXT (Text strings)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 1 hour, 15 minutes
            Data length: 1
            Text: 
        ubuntu.local: type AAAA, class IN, cache flush, addr fe80::20c:f1ff:fe5a:6a68
            Name: ubuntu.local
            Type: AAAA (IPv6 address)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 2 minutes
            Data length: 16
            Addr: fe80::20c:f1ff:fe5a:6a68

No.     Time        Source                Destination           Protocol Info
     19 7.009708    fe80::8d69:edeb:b826:9b30 ff02::c               SSDP     M-SEARCH * HTTP/1.1 

Frame 19 (208 bytes on wire, 208 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:29.874760000
    [Time delta from previous captured frame: 1.949181000 seconds]
    [Time delta from previous displayed frame: 1.949181000 seconds]
    [Time since reference or first frame: 7.009708000 seconds]
    Frame Number: 19
    Frame Length: 208 bytes
    Capture Length: 208 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ipv6:udp:http]
    [Coloring Rule Name: HTTP]
    [Coloring Rule String: http || tcp.port == 80]
Ethernet II, Src: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b), Dst: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
    Destination: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        Address: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
    Source: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        Address: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IPv6 (0x86dd)
Internet Protocol Version 6
    0110 .... = Version: 6
        [0110 .... = This field makes the filter "ip.version == 6" possible: 6]
    .... 0000 0000 .... .... .... .... .... = Traffic class: 0x00000000
    .... .... .... 0000 0000 0000 0000 0000 = Flowlabel: 0x00000000
    Payload length: 154
    Next header: UDP (0x11)
    Hop limit: 1
    Source: fe80::8d69:edeb:b826:9b30 (fe80::8d69:edeb:b826:9b30)
    Destination: ff02::c (ff02::c)
User Datagram Protocol, Src Port: 65524 (65524), Dst Port: ssdp (1900)
    Source port: 65524 (65524)
    Destination port: ssdp (1900)
    Length: 154
    Checksum: 0xc8bd [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Hypertext Transfer Protocol
    M-SEARCH * HTTP/1.1\r\n
        [Expert Info (Chat/Sequence): M-SEARCH * HTTP/1.1\r\n]
            [Message: M-SEARCH * HTTP/1.1\r\n]
            [Severity level: Chat]
            [Group: Sequence]
        Request Method: M-SEARCH
        Request URI: *
        Request Version: HTTP/1.1
    Host:[FF02::C]:1900\r\n
    ST:urn:Microsoft Windows Peer Name Resolution Protocol: V4:IPV6:LinkLocal\r\n
    Man:"ssdp:discover"\r\n
    MX:3\r\n
    \r\n

No.     Time        Source                Destination           Protocol Info
     20 7.369933    192.168.1.5           192.168.1.1           DNS      Standard query SOA local

Frame 20 (65 bytes on wire, 65 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:30.234985000
    [Time delta from previous captured frame: 0.360225000 seconds]
    [Time delta from previous displayed frame: 0.360225000 seconds]
    [Time since reference or first frame: 7.369933000 seconds]
    Frame Number: 20
    Frame Length: 65 bytes
    Capture Length: 65 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:dns]
    [Coloring Rule Name: UDP]
    [Coloring Rule String: udp]
Ethernet II, Src: Intel_5a:6a:68 (00:0c:f1:5a:6a:68), Dst: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
    Destination: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        Address: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.5 (192.168.1.5), Dst: 192.168.1.1 (192.168.1.1)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 51
    Identification: 0x0124 (292)
    Flags: 0x00
        0.. = Reserved bit: Not Set
        .0. = Don't fragment: Not Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 64
    Protocol: UDP (0x11)
    Header checksum: 0xf63f [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.1.5 (192.168.1.5)
    Destination: 192.168.1.1 (192.168.1.1)
User Datagram Protocol, Src Port: 44780 (44780), Dst Port: domain (53)
    Source port: 44780 (44780)
    Destination port: domain (53)
    Length: 31
    Checksum: 0xae2c [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Domain Name System (query)
    Transaction ID: 0x40ce
    Flags: 0x0100 (Standard query)
        0... .... .... .... = Response: Message is a query
        .000 0... .... .... = Opcode: Standard query (0)
        .... ..0. .... .... = Truncated: Message is not truncated
        .... ...1 .... .... = Recursion desired: Do query recursively
        .... .... .0.. .... = Z: reserved (0)
        .... .... ...0 .... = Non-authenticated data OK: Non-authenticated data is unacceptable
    Questions: 1
    Answer RRs: 0
    Authority RRs: 0
    Additional RRs: 0
    Queries
        local: type SOA, class IN
            Name: local
            Type: SOA (Start of zone of authority)
            Class: IN (0x0001)

No.     Time        Source                Destination           Protocol Info
     21 9.997075    fe80::8d69:edeb:b826:9b30 ff02::c               SSDP     M-SEARCH * HTTP/1.1 

Frame 21 (208 bytes on wire, 208 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:32.862127000
    [Time delta from previous captured frame: 2.627142000 seconds]
    [Time delta from previous displayed frame: 2.627142000 seconds]
    [Time since reference or first frame: 9.997075000 seconds]
    Frame Number: 21
    Frame Length: 208 bytes
    Capture Length: 208 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ipv6:udp:http]
    [Coloring Rule Name: HTTP]
    [Coloring Rule String: http || tcp.port == 80]
Ethernet II, Src: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b), Dst: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
    Destination: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        Address: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
    Source: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        Address: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IPv6 (0x86dd)
Internet Protocol Version 6
    0110 .... = Version: 6
        [0110 .... = This field makes the filter "ip.version == 6" possible: 6]
    .... 0000 0000 .... .... .... .... .... = Traffic class: 0x00000000
    .... .... .... 0000 0000 0000 0000 0000 = Flowlabel: 0x00000000
    Payload length: 154
    Next header: UDP (0x11)
    Hop limit: 1
    Source: fe80::8d69:edeb:b826:9b30 (fe80::8d69:edeb:b826:9b30)
    Destination: ff02::c (ff02::c)
User Datagram Protocol, Src Port: 65524 (65524), Dst Port: ssdp (1900)
    Source port: 65524 (65524)
    Destination port: ssdp (1900)
    Length: 154
    Checksum: 0xc8bd [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Hypertext Transfer Protocol
    M-SEARCH * HTTP/1.1\r\n
        [Expert Info (Chat/Sequence): M-SEARCH * HTTP/1.1\r\n]
            [Message: M-SEARCH * HTTP/1.1\r\n]
            [Severity level: Chat]
            [Group: Sequence]
        Request Method: M-SEARCH
        Request URI: *
        Request Version: HTTP/1.1
    Host:[FF02::C]:1900\r\n
    ST:urn:Microsoft Windows Peer Name Resolution Protocol: V4:IPV6:LinkLocal\r\n
    Man:"ssdp:discover"\r\n
    MX:3\r\n
    \r\n

No.     Time        Source                Destination           Protocol Info
     22 12.398555   192.168.1.5           192.168.1.1           DNS      Standard query AAAA ntp.ubuntu.com

Frame 22 (74 bytes on wire, 74 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:35.263607000
    [Time delta from previous captured frame: 2.401480000 seconds]
    [Time delta from previous displayed frame: 2.401480000 seconds]
    [Time since reference or first frame: 12.398555000 seconds]
    Frame Number: 22
    Frame Length: 74 bytes
    Capture Length: 74 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:dns]
    [Coloring Rule Name: UDP]
    [Coloring Rule String: udp]
Ethernet II, Src: Intel_5a:6a:68 (00:0c:f1:5a:6a:68), Dst: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
    Destination: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        Address: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.5 (192.168.1.5), Dst: 192.168.1.1 (192.168.1.1)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 60
    Identification: 0x65ca (26058)
    Flags: 0x02 (Don't Fragment)
        0.. = Reserved bit: Not Set
        .1. = Don't fragment: Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 64
    Protocol: UDP (0x11)
    Header checksum: 0x5190 [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.1.5 (192.168.1.5)
    Destination: 192.168.1.1 (192.168.1.1)
User Datagram Protocol, Src Port: 41227 (41227), Dst Port: domain (53)
    Source port: 41227 (41227)
    Destination port: domain (53)
    Length: 40
    Checksum: 0xf5ff [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Domain Name System (query)
    [Response In: 23]
    Transaction ID: 0x4f38
    Flags: 0x0100 (Standard query)
        0... .... .... .... = Response: Message is a query
        .000 0... .... .... = Opcode: Standard query (0)
        .... ..0. .... .... = Truncated: Message is not truncated
        .... ...1 .... .... = Recursion desired: Do query recursively
        .... .... .0.. .... = Z: reserved (0)
        .... .... ...0 .... = Non-authenticated data OK: Non-authenticated data is unacceptable
    Questions: 1
    Answer RRs: 0
    Authority RRs: 0
    Additional RRs: 0
    Queries
        ntp.ubuntu.com: type AAAA, class IN
            Name: ntp.ubuntu.com
            Type: AAAA (IPv6 address)
            Class: IN (0x0001)

No.     Time        Source                Destination           Protocol Info
     23 12.481328   192.168.1.1           192.168.1.5           DNS      Standard query response

Frame 23 (135 bytes on wire, 135 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:35.346380000
    [Time delta from previous captured frame: 0.082773000 seconds]
    [Time delta from previous displayed frame: 0.082773000 seconds]
    [Time since reference or first frame: 12.481328000 seconds]
    Frame Number: 23
    Frame Length: 135 bytes
    Capture Length: 135 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:dns]
    [Coloring Rule Name: UDP]
    [Coloring Rule String: udp]
Ethernet II, Src: D-Link_cc:48:a1 (00:15:e9:cc:48:a1), Dst: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
    Destination: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        Address: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.1 (192.168.1.1), Dst: 192.168.1.5 (192.168.1.5)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 121
    Identification: 0x0000 (0)
    Flags: 0x02 (Don't Fragment)
        0.. = Reserved bit: Not Set
        .1. = Don't fragment: Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 64
    Protocol: UDP (0x11)
    Header checksum: 0xb71d [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.1.1 (192.168.1.1)
    Destination: 192.168.1.5 (192.168.1.5)
User Datagram Protocol, Src Port: domain (53), Dst Port: 41227 (41227)
    Source port: domain (53)
    Destination port: 41227 (41227)
    Length: 101
    Checksum: 0xda08 [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Domain Name System (response)
    [Request In: 22]
    [Time: 0.082773000 seconds]
    Transaction ID: 0x4f38
    Flags: 0x8180 (Standard query response, No error)
        1... .... .... .... = Response: Message is a response
        .000 0... .... .... = Opcode: Standard query (0)
        .... .0.. .... .... = Authoritative: Server is not an authority for domain
        .... ..0. .... .... = Truncated: Message is not truncated
        .... ...1 .... .... = Recursion desired: Do query recursively
        .... .... 1... .... = Recursion available: Server can do recursive queries
        .... .... .0.. .... = Z: reserved (0)
        .... .... ..0. .... = Answer authenticated: Answer/authority portion was not authenticated by the server
        .... .... .... 0000 = Reply code: No error (0)
    Questions: 1
    Answer RRs: 0
    Authority RRs: 1
    Additional RRs: 0
    Queries
        ntp.ubuntu.com: type AAAA, class IN
            Name: ntp.ubuntu.com
            Type: AAAA (IPv6 address)
            Class: IN (0x0001)
    Authoritative nameservers
        ubuntu.com: type SOA, class IN, mname ns1.canonical.com
            Name: ubuntu.com
            Type: SOA (Start of zone of authority)
            Class: IN (0x0001)
            Time to live: 2 minutes, 28 seconds
            Data length: 49
            Primary name server: ns1.canonical.com
            Responsible authority's mailbox: hostmaster.canonical.com
            Serial number: 2010021103
            Refresh interval: 3 hours
            Retry interval: 1 hour
            Expiration limit: 7 days
            Minimum TTL: 1 hour

No.     Time        Source                Destination           Protocol Info
     24 12.481609   192.168.1.5           192.168.1.1           DNS      Standard query AAAA ntp.ubuntu.com

Frame 24 (74 bytes on wire, 74 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:35.346661000
    [Time delta from previous captured frame: 0.000281000 seconds]
    [Time delta from previous displayed frame: 0.000281000 seconds]
    [Time since reference or first frame: 12.481609000 seconds]
    Frame Number: 24
    Frame Length: 74 bytes
    Capture Length: 74 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:dns]
    [Coloring Rule Name: UDP]
    [Coloring Rule String: udp]
Ethernet II, Src: Intel_5a:6a:68 (00:0c:f1:5a:6a:68), Dst: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
    Destination: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        Address: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.5 (192.168.1.5), Dst: 192.168.1.1 (192.168.1.1)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 60
    Identification: 0x65df (26079)
    Flags: 0x02 (Don't Fragment)
        0.. = Reserved bit: Not Set
        .1. = Don't fragment: Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 64
    Protocol: UDP (0x11)
    Header checksum: 0x517b [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.1.5 (192.168.1.5)
    Destination: 192.168.1.1 (192.168.1.1)
User Datagram Protocol, Src Port: 33523 (33523), Dst Port: domain (53)
    Source port: 33523 (33523)
    Destination port: domain (53)
    Length: 40
    Checksum: 0x98c5 [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Domain Name System (query)
    [Response In: 25]
    Transaction ID: 0xca8a
    Flags: 0x0100 (Standard query)
        0... .... .... .... = Response: Message is a query
        .000 0... .... .... = Opcode: Standard query (0)
        .... ..0. .... .... = Truncated: Message is not truncated
        .... ...1 .... .... = Recursion desired: Do query recursively
        .... .... .0.. .... = Z: reserved (0)
        .... .... ...0 .... = Non-authenticated data OK: Non-authenticated data is unacceptable
    Questions: 1
    Answer RRs: 0
    Authority RRs: 0
    Additional RRs: 0
    Queries
        ntp.ubuntu.com: type AAAA, class IN
            Name: ntp.ubuntu.com
            Type: AAAA (IPv6 address)
            Class: IN (0x0001)

No.     Time        Source                Destination           Protocol Info
     25 12.485539   192.168.1.1           192.168.1.5           DNS      Standard query response[Malformed Packet]

Frame 25 (74 bytes on wire, 74 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:35.350591000
    [Time delta from previous captured frame: 0.003930000 seconds]
    [Time delta from previous displayed frame: 0.003930000 seconds]
    [Time since reference or first frame: 12.485539000 seconds]
    Frame Number: 25
    Frame Length: 74 bytes
    Capture Length: 74 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:dns]
    [Coloring Rule Name: UDP]
    [Coloring Rule String: udp]
Ethernet II, Src: D-Link_cc:48:a1 (00:15:e9:cc:48:a1), Dst: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
    Destination: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        Address: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.1 (192.168.1.1), Dst: 192.168.1.5 (192.168.1.5)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 60
    Identification: 0x0000 (0)
    Flags: 0x02 (Don't Fragment)
        0.. = Reserved bit: Not Set
        .1. = Don't fragment: Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 64
    Protocol: UDP (0x11)
    Header checksum: 0xb75a [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.1.1 (192.168.1.1)
    Destination: 192.168.1.5 (192.168.1.5)
User Datagram Protocol, Src Port: domain (53), Dst Port: 33523 (33523)
    Source port: domain (53)
    Destination port: 33523 (33523)
    Length: 40
    Checksum: 0x18c4 [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Domain Name System (response)
    [Request In: 24]
    [Time: 0.003930000 seconds]
    Transaction ID: 0xca8a
    Flags: 0x8100 (Standard query response, No error)
        1... .... .... .... = Response: Message is a response
        .000 0... .... .... = Opcode: Standard query (0)
        .... .0.. .... .... = Authoritative: Server is not an authority for domain
        .... ..0. .... .... = Truncated: Message is not truncated
        .... ...1 .... .... = Recursion desired: Do query recursively
        .... .... 0... .... = Recursion available: Server can't do recursive queries
        .... .... .0.. .... = Z: reserved (0)
        .... .... ..0. .... = Answer authenticated: Answer/authority portion was not authenticated by the server
        .... .... .... 0000 = Reply code: No error (0)
    Questions: 1
    Answer RRs: 1
    Authority RRs: 0
    Additional RRs: 0
    Queries
        ntp.ubuntu.com: type AAAA, class IN
            Name: ntp.ubuntu.com
            Type: AAAA (IPv6 address)
            Class: IN (0x0001)
[Malformed Packet: DNS]
    [Expert Info (Error/Malformed): Malformed Packet (Exception occurred)]
        [Message: Malformed Packet (Exception occurred)]
        [Severity level: Error]
        [Group: Malformed]

No.     Time        Source                Destination           Protocol Info
     26 12.485719   192.168.1.5           192.168.1.1           DNS      Standard query A ntp.ubuntu.com

Frame 26 (74 bytes on wire, 74 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:35.350771000
    [Time delta from previous captured frame: 0.000180000 seconds]
    [Time delta from previous displayed frame: 0.000180000 seconds]
    [Time since reference or first frame: 12.485719000 seconds]
    Frame Number: 26
    Frame Length: 74 bytes
    Capture Length: 74 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:dns]
    [Coloring Rule Name: UDP]
    [Coloring Rule String: udp]
Ethernet II, Src: Intel_5a:6a:68 (00:0c:f1:5a:6a:68), Dst: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
    Destination: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        Address: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.5 (192.168.1.5), Dst: 192.168.1.1 (192.168.1.1)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 60
    Identification: 0x65e0 (26080)
    Flags: 0x02 (Don't Fragment)
        0.. = Reserved bit: Not Set
        .1. = Don't fragment: Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 64
    Protocol: UDP (0x11)
    Header checksum: 0x517a [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.1.5 (192.168.1.5)
    Destination: 192.168.1.1 (192.168.1.1)
User Datagram Protocol, Src Port: 35400 (35400), Dst Port: domain (53)
    Source port: 35400 (35400)
    Destination port: domain (53)
    Length: 40
    Checksum: 0x5a61 [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Domain Name System (query)
    [Response In: 27]
    Transaction ID: 0x01b5
    Flags: 0x0100 (Standard query)
        0... .... .... .... = Response: Message is a query
        .000 0... .... .... = Opcode: Standard query (0)
        .... ..0. .... .... = Truncated: Message is not truncated
        .... ...1 .... .... = Recursion desired: Do query recursively
        .... .... .0.. .... = Z: reserved (0)
        .... .... ...0 .... = Non-authenticated data OK: Non-authenticated data is unacceptable
    Questions: 1
    Answer RRs: 0
    Authority RRs: 0
    Additional RRs: 0
    Queries
        ntp.ubuntu.com: type A, class IN
            Name: ntp.ubuntu.com
            Type: A (Host address)
            Class: IN (0x0001)

No.     Time        Source                Destination           Protocol Info
     27 12.489620   192.168.1.1           192.168.1.5           DNS      Standard query response A 1.0.0.0

Frame 27 (90 bytes on wire, 90 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:35.354672000
    [Time delta from previous captured frame: 0.003901000 seconds]
    [Time delta from previous displayed frame: 0.003901000 seconds]
    [Time since reference or first frame: 12.489620000 seconds]
    Frame Number: 27
    Frame Length: 90 bytes
    Capture Length: 90 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:dns]
    [Coloring Rule Name: UDP]
    [Coloring Rule String: udp]
Ethernet II, Src: D-Link_cc:48:a1 (00:15:e9:cc:48:a1), Dst: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
    Destination: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        Address: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.1 (192.168.1.1), Dst: 192.168.1.5 (192.168.1.5)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 76
    Identification: 0x0000 (0)
    Flags: 0x02 (Don't Fragment)
        0.. = Reserved bit: Not Set
        .1. = Don't fragment: Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 64
    Protocol: UDP (0x11)
    Header checksum: 0xb74a [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.1.1 (192.168.1.1)
    Destination: 192.168.1.5 (192.168.1.5)
User Datagram Protocol, Src Port: domain (53), Dst Port: 35400 (35400)
    Source port: domain (53)
    Destination port: 35400 (35400)
    Length: 56
    Checksum: 0xf21c [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Domain Name System (response)
    [Request In: 26]
    [Time: 0.003901000 seconds]
    Transaction ID: 0x01b5
    Flags: 0x8100 (Standard query response, No error)
        1... .... .... .... = Response: Message is a response
        .000 0... .... .... = Opcode: Standard query (0)
        .... .0.. .... .... = Authoritative: Server is not an authority for domain
        .... ..0. .... .... = Truncated: Message is not truncated
        .... ...1 .... .... = Recursion desired: Do query recursively
        .... .... 0... .... = Recursion available: Server can't do recursive queries
        .... .... .0.. .... = Z: reserved (0)
        .... .... ..0. .... = Answer authenticated: Answer/authority portion was not authenticated by the server
        .... .... .... 0000 = Reply code: No error (0)
    Questions: 1
    Answer RRs: 1
    Authority RRs: 0
    Additional RRs: 0
    Queries
        ntp.ubuntu.com: type A, class IN
            Name: ntp.ubuntu.com
            Type: A (Host address)
            Class: IN (0x0001)
    Answers
        ntp.ubuntu.com: type A, class IN, addr 1.0.0.0
            Name: ntp.ubuntu.com
            Type: A (Host address)
            Class: IN (0x0001)
            Time to live: 2 hours, 46 minutes, 40 seconds
            Data length: 4
            Addr: 1.0.0.0

No.     Time        Source                Destination           Protocol Info
     28 12.590449   192.168.1.5           1.0.0.0               NTP      NTP client

Frame 28 (90 bytes on wire, 90 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:35.455501000
    [Time delta from previous captured frame: 0.100829000 seconds]
    [Time delta from previous displayed frame: 0.100829000 seconds]
    [Time since reference or first frame: 12.590449000 seconds]
    Frame Number: 28
    Frame Length: 90 bytes
    Capture Length: 90 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:ntp]
    [Coloring Rule Name: UDP]
    [Coloring Rule String: udp]
Ethernet II, Src: Intel_5a:6a:68 (00:0c:f1:5a:6a:68), Dst: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
    Destination: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        Address: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.5 (192.168.1.5), Dst: 1.0.0.0 (1.0.0.0)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 76
    Identification: 0x0000 (0)
    Flags: 0x02 (Don't Fragment)
        0.. = Reserved bit: Not Set
        .1. = Don't fragment: Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 64
    Protocol: UDP (0x11)
    Header checksum: 0x77f4 [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.1.5 (192.168.1.5)
    Destination: 1.0.0.0 (1.0.0.0)
User Datagram Protocol, Src Port: ntp (123), Dst Port: ntp (123)
    Source port: ntp (123)
    Destination port: ntp (123)
    Length: 56
    Checksum: 0x3828 [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Network Time Protocol
    Flags: 0xe3
        11.. .... = Leap Indicator: alarm condition (clock not synchronized) (3)
        ..10 0... = Version number: NTP Version 4 (4)
        .... .011 = Mode: client (3)
    Peer Clock Stratum: unspecified or unavailable (0)
    Peer Polling Interval: 4 (16 sec)
    Peer Clock Precision: 0.015625 sec
    Root Delay:    1.0000 sec
    Root Dispersion:    1.0000 sec
    Reference Clock ID: NULL
    Reference Clock Update Time: NULL
    Originate Time Stamp: NULL
    Receive Time Stamp: NULL
    Transmit Time Stamp: Feb 12, 2010 21:47:35.4555 UTC

No.     Time        Source                Destination           Protocol Info
     29 13.590494   192.168.1.5           1.0.0.0               NTP      NTP client

Frame 29 (90 bytes on wire, 90 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:36.455546000
    [Time delta from previous captured frame: 1.000045000 seconds]
    [Time delta from previous displayed frame: 1.000045000 seconds]
    [Time since reference or first frame: 13.590494000 seconds]
    Frame Number: 29
    Frame Length: 90 bytes
    Capture Length: 90 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:ntp]
    [Coloring Rule Name: UDP]
    [Coloring Rule String: udp]
Ethernet II, Src: Intel_5a:6a:68 (00:0c:f1:5a:6a:68), Dst: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
    Destination: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        Address: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.5 (192.168.1.5), Dst: 1.0.0.0 (1.0.0.0)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 76
    Identification: 0x0000 (0)
    Flags: 0x02 (Don't Fragment)
        0.. = Reserved bit: Not Set
        .1. = Don't fragment: Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 64
    Protocol: UDP (0x11)
    Header checksum: 0x77f4 [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.1.5 (192.168.1.5)
    Destination: 1.0.0.0 (1.0.0.0)
User Datagram Protocol, Src Port: ntp (123), Dst Port: ntp (123)
    Source port: ntp (123)
    Destination port: ntp (123)
    Length: 56
    Checksum: 0x6262 [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Network Time Protocol
    Flags: 0xe3
        11.. .... = Leap Indicator: alarm condition (clock not synchronized) (3)
        ..10 0... = Version number: NTP Version 4 (4)
        .... .011 = Mode: client (3)
    Peer Clock Stratum: unspecified or unavailable (0)
    Peer Polling Interval: 4 (16 sec)
    Peer Clock Precision: 0.015625 sec
    Root Delay:    1.0000 sec
    Root Dispersion:    1.0000 sec
    Reference Clock ID: NULL
    Reference Clock Update Time: NULL
    Originate Time Stamp: NULL
    Receive Time Stamp: NULL
    Transmit Time Stamp: Feb 12, 2010 21:47:36.4555 UTC

No.     Time        Source                Destination           Protocol Info
     30 14.004013   fe80::8d69:edeb:b826:9b30 ff02::c               SSDP     M-SEARCH * HTTP/1.1 

Frame 30 (208 bytes on wire, 208 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:36.869065000
    [Time delta from previous captured frame: 0.413519000 seconds]
    [Time delta from previous displayed frame: 0.413519000 seconds]
    [Time since reference or first frame: 14.004013000 seconds]
    Frame Number: 30
    Frame Length: 208 bytes
    Capture Length: 208 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ipv6:udp:http]
    [Coloring Rule Name: HTTP]
    [Coloring Rule String: http || tcp.port == 80]
Ethernet II, Src: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b), Dst: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
    Destination: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        Address: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
    Source: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        Address: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IPv6 (0x86dd)
Internet Protocol Version 6
    0110 .... = Version: 6
        [0110 .... = This field makes the filter "ip.version == 6" possible: 6]
    .... 0000 0000 .... .... .... .... .... = Traffic class: 0x00000000
    .... .... .... 0000 0000 0000 0000 0000 = Flowlabel: 0x00000000
    Payload length: 154
    Next header: UDP (0x11)
    Hop limit: 1
    Source: fe80::8d69:edeb:b826:9b30 (fe80::8d69:edeb:b826:9b30)
    Destination: ff02::c (ff02::c)
User Datagram Protocol, Src Port: 65524 (65524), Dst Port: ssdp (1900)
    Source port: 65524 (65524)
    Destination port: ssdp (1900)
    Length: 154
    Checksum: 0xc8bd [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Hypertext Transfer Protocol
    M-SEARCH * HTTP/1.1\r\n
        [Expert Info (Chat/Sequence): M-SEARCH * HTTP/1.1\r\n]
            [Message: M-SEARCH * HTTP/1.1\r\n]
            [Severity level: Chat]
            [Group: Sequence]
        Request Method: M-SEARCH
        Request URI: *
        Request Version: HTTP/1.1
    Host:[FF02::C]:1900\r\n
    ST:urn:Microsoft Windows Peer Name Resolution Protocol: V4:IPV6:LinkLocal\r\n
    Man:"ssdp:discover"\r\n
    MX:3\r\n
    \r\n

No.     Time        Source                Destination           Protocol Info
     31 14.590469   192.168.1.5           1.0.0.0               NTP      NTP client

Frame 31 (90 bytes on wire, 90 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:37.455521000
    [Time delta from previous captured frame: 0.586456000 seconds]
    [Time delta from previous displayed frame: 0.586456000 seconds]
    [Time since reference or first frame: 14.590469000 seconds]
    Frame Number: 31
    Frame Length: 90 bytes
    Capture Length: 90 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:ntp]
    [Coloring Rule Name: UDP]
    [Coloring Rule String: udp]
Ethernet II, Src: Intel_5a:6a:68 (00:0c:f1:5a:6a:68), Dst: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
    Destination: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        Address: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.5 (192.168.1.5), Dst: 1.0.0.0 (1.0.0.0)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 76
    Identification: 0x0000 (0)
    Flags: 0x02 (Don't Fragment)
        0.. = Reserved bit: Not Set
        .1. = Don't fragment: Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 64
    Protocol: UDP (0x11)
    Header checksum: 0x77f4 [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.1.5 (192.168.1.5)
    Destination: 1.0.0.0 (1.0.0.0)
User Datagram Protocol, Src Port: ntp (123), Dst Port: ntp (123)
    Source port: ntp (123)
    Destination port: ntp (123)
    Length: 56
    Checksum: 0xe442 [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Network Time Protocol
    Flags: 0xe3
        11.. .... = Leap Indicator: alarm condition (clock not synchronized) (3)
        ..10 0... = Version number: NTP Version 4 (4)
        .... .011 = Mode: client (3)
    Peer Clock Stratum: unspecified or unavailable (0)
    Peer Polling Interval: 4 (16 sec)
    Peer Clock Precision: 0.015625 sec
    Root Delay:    1.0000 sec
    Root Dispersion:    1.0000 sec
    Reference Clock ID: NULL
    Reference Clock Update Time: NULL
    Originate Time Stamp: NULL
    Receive Time Stamp: NULL
    Transmit Time Stamp: Feb 12, 2010 21:47:37.4555 UTC

No.     Time        Source                Destination           Protocol Info
     32 14.692820   193.253.91.110        192.168.1.5           ICMP     Destination unreachable (Network unreachable)

Frame 32 (70 bytes on wire, 70 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:37.557872000
    [Time delta from previous captured frame: 0.102351000 seconds]
    [Time delta from previous displayed frame: 0.102351000 seconds]
    [Time since reference or first frame: 14.692820000 seconds]
    Frame Number: 32
    Frame Length: 70 bytes
    Capture Length: 70 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:icmp:ip:udp]
    [Coloring Rule Name: ICMP errors]
    [Coloring Rule String: icmp.type eq 3 || icmp.type eq 4 || icmp.type eq 5 || icmp.type eq 11]
Ethernet II, Src: D-Link_cc:48:a1 (00:15:e9:cc:48:a1), Dst: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
    Destination: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        Address: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 193.253.91.110 (193.253.91.110), Dst: 192.168.1.5 (192.168.1.5)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 56
    Identification: 0x0000 (0)
    Flags: 0x00
        0.. = Reserved bit: Not Set
        .0. = Don't fragment: Not Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 251
    Protocol: ICMP (0x01)
    Header checksum: 0xe0ab [correct]
        [Good: True]
        [Bad : False]
    Source: 193.253.91.110 (193.253.91.110)
    Destination: 192.168.1.5 (192.168.1.5)
Internet Control Message Protocol
    Type: 3 (Destination unreachable)
    Code: 0 (Network unreachable)
    Checksum: 0x178f [correct]
    Internet Protocol, Src: 192.168.1.5 (192.168.1.5), Dst: 1.0.0.0 (1.0.0.0)
        Version: 4
        Header length: 20 bytes
        Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
            0000 00.. = Differentiated Services Codepoint: Default (0x00)
            .... ..0. = ECN-Capable Transport (ECT): 0
            .... ...0 = ECN-CE: 0
        Total Length: 76
        Identification: 0x0000 (0)
        Flags: 0x02 (Don't Fragment)
            0.. = Reserved bit: Not Set
            .1. = Don't fragment: Set
            ..0 = More fragments: Not Set
        Fragment offset: 0
        Time to live: 61
        Protocol: UDP (0x11)
        Header checksum: 0x7af4 [correct]
            [Good: True]
            [Bad : False]
        Source: 192.168.1.5 (192.168.1.5)
        Destination: 1.0.0.0 (1.0.0.0)
    User Datagram Protocol, Src Port: ntp (123), Dst Port: ntp (123)
        Source port: ntp (123)
        Destination port: ntp (123)
        Length: 56
        Checksum: 0xe442 [unchecked, not all data available]
            [Good Checksum: False]
            [Bad Checksum: False]

No.     Time        Source                Destination           Protocol Info
     33 15.590472   192.168.1.5           1.0.0.0               NTP      NTP client

Frame 33 (90 bytes on wire, 90 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:38.455524000
    [Time delta from previous captured frame: 0.897652000 seconds]
    [Time delta from previous displayed frame: 0.897652000 seconds]
    [Time since reference or first frame: 15.590472000 seconds]
    Frame Number: 33
    Frame Length: 90 bytes
    Capture Length: 90 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:ntp]
    [Coloring Rule Name: UDP]
    [Coloring Rule String: udp]
Ethernet II, Src: Intel_5a:6a:68 (00:0c:f1:5a:6a:68), Dst: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
    Destination: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        Address: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.5 (192.168.1.5), Dst: 1.0.0.0 (1.0.0.0)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 76
    Identification: 0x0000 (0)
    Flags: 0x02 (Don't Fragment)
        0.. = Reserved bit: Not Set
        .1. = Don't fragment: Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 64
    Protocol: UDP (0x11)
    Header checksum: 0x77f4 [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.1.5 (192.168.1.5)
    Destination: 1.0.0.0 (1.0.0.0)
User Datagram Protocol, Src Port: ntp (123), Dst Port: ntp (123)
    Source port: ntp (123)
    Destination port: ntp (123)
    Length: 56
    Checksum: 0x905e [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Network Time Protocol
    Flags: 0xe3
        11.. .... = Leap Indicator: alarm condition (clock not synchronized) (3)
        ..10 0... = Version number: NTP Version 4 (4)
        .... .011 = Mode: client (3)
    Peer Clock Stratum: unspecified or unavailable (0)
    Peer Polling Interval: 4 (16 sec)
    Peer Clock Precision: 0.015625 sec
    Root Delay:    1.0000 sec
    Root Dispersion:    1.0000 sec
    Reference Clock ID: NULL
    Reference Clock Update Time: NULL
    Originate Time Stamp: NULL
    Receive Time Stamp: NULL
    Transmit Time Stamp: Feb 12, 2010 21:47:38.4555 UTC

No.     Time        Source                Destination           Protocol Info
     34 17.005746   fe80::8d69:edeb:b826:9b30 ff02::c               SSDP     M-SEARCH * HTTP/1.1 

Frame 34 (208 bytes on wire, 208 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:39.870798000
    [Time delta from previous captured frame: 1.415274000 seconds]
    [Time delta from previous displayed frame: 1.415274000 seconds]
    [Time since reference or first frame: 17.005746000 seconds]
    Frame Number: 34
    Frame Length: 208 bytes
    Capture Length: 208 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ipv6:udp:http]
    [Coloring Rule Name: HTTP]
    [Coloring Rule String: http || tcp.port == 80]
Ethernet II, Src: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b), Dst: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
    Destination: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        Address: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
    Source: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        Address: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IPv6 (0x86dd)
Internet Protocol Version 6
    0110 .... = Version: 6
        [0110 .... = This field makes the filter "ip.version == 6" possible: 6]
    .... 0000 0000 .... .... .... .... .... = Traffic class: 0x00000000
    .... .... .... 0000 0000 0000 0000 0000 = Flowlabel: 0x00000000
    Payload length: 154
    Next header: UDP (0x11)
    Hop limit: 1
    Source: fe80::8d69:edeb:b826:9b30 (fe80::8d69:edeb:b826:9b30)
    Destination: ff02::c (ff02::c)
User Datagram Protocol, Src Port: 65524 (65524), Dst Port: ssdp (1900)
    Source port: 65524 (65524)
    Destination port: ssdp (1900)
    Length: 154
    Checksum: 0xc8bd [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Hypertext Transfer Protocol
    M-SEARCH * HTTP/1.1\r\n
        [Expert Info (Chat/Sequence): M-SEARCH * HTTP/1.1\r\n]
            [Message: M-SEARCH * HTTP/1.1\r\n]
            [Severity level: Chat]
            [Group: Sequence]
        Request Method: M-SEARCH
        Request URI: *
        Request Version: HTTP/1.1
    Host:[FF02::C]:1900\r\n
    ST:urn:Microsoft Windows Peer Name Resolution Protocol: V4:IPV6:LinkLocal\r\n
    Man:"ssdp:discover"\r\n
    MX:3\r\n
    \r\n

No.     Time        Source                Destination           Protocol Info
     35 17.472490   D-Link_cc:48:a1       Intel_5a:6a:68        ARP      Who has 192.168.1.5?  Tell 192.168.1.1

Frame 35 (42 bytes on wire, 42 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:40.337542000
    [Time delta from previous captured frame: 0.466744000 seconds]
    [Time delta from previous displayed frame: 0.466744000 seconds]
    [Time since reference or first frame: 17.472490000 seconds]
    Frame Number: 35
    Frame Length: 42 bytes
    Capture Length: 42 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:arp]
    [Coloring Rule Name: ARP]
    [Coloring Rule String: arp]
Ethernet II, Src: D-Link_cc:48:a1 (00:15:e9:cc:48:a1), Dst: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
    Destination: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        Address: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: ARP (0x0806)
Address Resolution Protocol (request)
    Hardware type: Ethernet (0x0001)
    Protocol type: IP (0x0800)
    Hardware size: 6
    Protocol size: 4
    Opcode: request (0x0001)
    [Is gratuitous: False]
    Sender MAC address: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
    Sender IP address: 192.168.1.1 (192.168.1.1)
    Target MAC address: 00:00:00_00:00:00 (00:00:00:00:00:00)
    Target IP address: 192.168.1.5 (192.168.1.5)

No.     Time        Source                Destination           Protocol Info
     36 17.472519   Intel_5a:6a:68        D-Link_cc:48:a1       ARP      192.168.1.5 is at 00:0c:f1:5a:6a:68

Frame 36 (42 bytes on wire, 42 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:40.337571000
    [Time delta from previous captured frame: 0.000029000 seconds]
    [Time delta from previous displayed frame: 0.000029000 seconds]
    [Time since reference or first frame: 17.472519000 seconds]
    Frame Number: 36
    Frame Length: 42 bytes
    Capture Length: 42 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:arp]
    [Coloring Rule Name: ARP]
    [Coloring Rule String: arp]
Ethernet II, Src: Intel_5a:6a:68 (00:0c:f1:5a:6a:68), Dst: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
    Destination: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        Address: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        Address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: ARP (0x0806)
Address Resolution Protocol (reply)
    Hardware type: Ethernet (0x0001)
    Protocol type: IP (0x0800)
    Hardware size: 6
    Protocol size: 4
    Opcode: reply (0x0002)
    [Is gratuitous: False]
    Sender MAC address: Intel_5a:6a:68 (00:0c:f1:5a:6a:68)
    Sender IP address: 192.168.1.5 (192.168.1.5)
    Target MAC address: D-Link_cc:48:a1 (00:15:e9:cc:48:a1)
    Target IP address: 192.168.1.1 (192.168.1.1)

No.     Time        Source                Destination           Protocol Info
     37 19.908025   fe80::8d69:edeb:b826:9b30 ff02::1:2             DHCPv6   Solicit

Frame 37 (149 bytes on wire, 149 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:42.773077000
    [Time delta from previous captured frame: 2.435506000 seconds]
    [Time delta from previous displayed frame: 2.435506000 seconds]
    [Time since reference or first frame: 19.908025000 seconds]
    Frame Number: 37
    Frame Length: 149 bytes
    Capture Length: 149 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ipv6:udp:dhcpv6]
    [Coloring Rule Name: UDP]
    [Coloring Rule String: udp]
Ethernet II, Src: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b), Dst: IPv6mcast_00:01:00:02 (33:33:00:01:00:02)
    Destination: IPv6mcast_00:01:00:02 (33:33:00:01:00:02)
        Address: IPv6mcast_00:01:00:02 (33:33:00:01:00:02)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
    Source: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        Address: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IPv6 (0x86dd)
Internet Protocol Version 6
    0110 .... = Version: 6
        [0110 .... = This field makes the filter "ip.version == 6" possible: 6]
    .... 0000 0000 .... .... .... .... .... = Traffic class: 0x00000000
    .... .... .... 0000 0000 0000 0000 0000 = Flowlabel: 0x00000000
    Payload length: 95
    Next header: UDP (0x11)
    Hop limit: 1
    Source: fe80::8d69:edeb:b826:9b30 (fe80::8d69:edeb:b826:9b30)
    Destination: ff02::1:2 (ff02::1:2)
User Datagram Protocol, Src Port: dhcpv6-client (546), Dst Port: dhcpv6-server (547)
    Source port: dhcpv6-client (546)
    Destination port: dhcpv6-server (547)
    Length: 95
    Checksum: 0x1621 [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
DHCPv6
    Message type: Solicit (1)
    Transaction-ID: 0x00452aaf
    Elapsed time
        option type: 8
        option length: 2
        elapsed-time: 63000 ms
    Client Identifier
        option type: 1
        option length: 14
        DUID type: link-layer address plus time (1)
        Hardware type: Ethernet (1)
        Time: 308202630
        Link-layer address: 00:25:11:a7:ae:bc
    Identity Association for Non-temporary Address
        option type: 3
        option length: 12
        IAID: 234886975
        T1: 0
        T2: 0
    Fully Qualified Domain Name
        option type: 39
        option length: 9
        0000 0... = Reserved: 0x00
        .... .0.. = N: N bit cleared
        .... ..0. = O: O bit cleared
        .... ...0 = S: S bit cleared
        Domain: Marc-PC
    Vendor Class
        option type: 16
        option length: 14
        Enterprise-number: Microsoft (311)
        vendor-class-data: 00084D53465420352E30
    Option Request
        option type: 6
        option length: 8
        Requested Option code: Domain Search List (24)
        Requested Option code: DNS recursive name server (23)
        Requested Option code: Vendor-specific Information (17)
        Requested Option code: Fully Qualified Domain Name (39)

No.     Time        Source                Destination           Protocol Info
     38 20.003970   fe80::8d69:edeb:b826:9b30 ff02::c               SSDP     M-SEARCH * HTTP/1.1 

Frame 38 (208 bytes on wire, 208 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:42.869022000
    [Time delta from previous captured frame: 0.095945000 seconds]
    [Time delta from previous displayed frame: 0.095945000 seconds]
    [Time since reference or first frame: 20.003970000 seconds]
    Frame Number: 38
    Frame Length: 208 bytes
    Capture Length: 208 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ipv6:udp:http]
    [Coloring Rule Name: HTTP]
    [Coloring Rule String: http || tcp.port == 80]
Ethernet II, Src: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b), Dst: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
    Destination: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        Address: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
    Source: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        Address: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IPv6 (0x86dd)
Internet Protocol Version 6
    0110 .... = Version: 6
        [0110 .... = This field makes the filter "ip.version == 6" possible: 6]
    .... 0000 0000 .... .... .... .... .... = Traffic class: 0x00000000
    .... .... .... 0000 0000 0000 0000 0000 = Flowlabel: 0x00000000
    Payload length: 154
    Next header: UDP (0x11)
    Hop limit: 1
    Source: fe80::8d69:edeb:b826:9b30 (fe80::8d69:edeb:b826:9b30)
    Destination: ff02::c (ff02::c)
User Datagram Protocol, Src Port: 65524 (65524), Dst Port: ssdp (1900)
    Source port: 65524 (65524)
    Destination port: ssdp (1900)
    Length: 154
    Checksum: 0xc8bd [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Hypertext Transfer Protocol
    M-SEARCH * HTTP/1.1\r\n
        [Expert Info (Chat/Sequence): M-SEARCH * HTTP/1.1\r\n]
            [Message: M-SEARCH * HTTP/1.1\r\n]
            [Severity level: Chat]
            [Group: Sequence]
        Request Method: M-SEARCH
        Request URI: *
        Request Version: HTTP/1.1
    Host:[FF02::C]:1900\r\n
    ST:urn:Microsoft Windows Peer Name Resolution Protocol: V4:IPV6:LinkLocal\r\n
    Man:"ssdp:discover"\r\n
    MX:3\r\n
    \r\n

No.     Time        Source                Destination           Protocol Info
     39 23.993924   fe80::8d69:edeb:b826:9b30 ff02::c               SSDP     M-SEARCH * HTTP/1.1 

Frame 39 (208 bytes on wire, 208 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:46.858976000
    [Time delta from previous captured frame: 3.989954000 seconds]
    [Time delta from previous displayed frame: 3.989954000 seconds]
    [Time since reference or first frame: 23.993924000 seconds]
    Frame Number: 39
    Frame Length: 208 bytes
    Capture Length: 208 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ipv6:udp:http]
    [Coloring Rule Name: HTTP]
    [Coloring Rule String: http || tcp.port == 80]
Ethernet II, Src: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b), Dst: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
    Destination: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        Address: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
    Source: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        Address: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IPv6 (0x86dd)
Internet Protocol Version 6
    0110 .... = Version: 6
        [0110 .... = This field makes the filter "ip.version == 6" possible: 6]
    .... 0000 0000 .... .... .... .... .... = Traffic class: 0x00000000
    .... .... .... 0000 0000 0000 0000 0000 = Flowlabel: 0x00000000
    Payload length: 154
    Next header: UDP (0x11)
    Hop limit: 1
    Source: fe80::8d69:edeb:b826:9b30 (fe80::8d69:edeb:b826:9b30)
    Destination: ff02::c (ff02::c)
User Datagram Protocol, Src Port: 65524 (65524), Dst Port: ssdp (1900)
    Source port: 65524 (65524)
    Destination port: ssdp (1900)
    Length: 154
    Checksum: 0xc8bd [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Hypertext Transfer Protocol
    M-SEARCH * HTTP/1.1\r\n
        [Expert Info (Chat/Sequence): M-SEARCH * HTTP/1.1\r\n]
            [Message: M-SEARCH * HTTP/1.1\r\n]
            [Severity level: Chat]
            [Group: Sequence]
        Request Method: M-SEARCH
        Request URI: *
        Request Version: HTTP/1.1
    Host:[FF02::C]:1900\r\n
    ST:urn:Microsoft Windows Peer Name Resolution Protocol: V4:IPV6:LinkLocal\r\n
    Man:"ssdp:discover"\r\n
    MX:3\r\n
    \r\n

No.     Time        Source                Destination           Protocol Info
     40 26.995439   fe80::8d69:edeb:b826:9b30 ff02::c               SSDP     M-SEARCH * HTTP/1.1 

Frame 40 (208 bytes on wire, 208 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:49.860491000
    [Time delta from previous captured frame: 3.001515000 seconds]
    [Time delta from previous displayed frame: 3.001515000 seconds]
    [Time since reference or first frame: 26.995439000 seconds]
    Frame Number: 40
    Frame Length: 208 bytes
    Capture Length: 208 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ipv6:udp:http]
    [Coloring Rule Name: HTTP]
    [Coloring Rule String: http || tcp.port == 80]
Ethernet II, Src: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b), Dst: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
    Destination: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        Address: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
    Source: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        Address: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IPv6 (0x86dd)
Internet Protocol Version 6
    0110 .... = Version: 6
        [0110 .... = This field makes the filter "ip.version == 6" possible: 6]
    .... 0000 0000 .... .... .... .... .... = Traffic class: 0x00000000
    .... .... .... 0000 0000 0000 0000 0000 = Flowlabel: 0x00000000
    Payload length: 154
    Next header: UDP (0x11)
    Hop limit: 1
    Source: fe80::8d69:edeb:b826:9b30 (fe80::8d69:edeb:b826:9b30)
    Destination: ff02::c (ff02::c)
User Datagram Protocol, Src Port: 65524 (65524), Dst Port: ssdp (1900)
    Source port: 65524 (65524)
    Destination port: ssdp (1900)
    Length: 154
    Checksum: 0xc8bd [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Hypertext Transfer Protocol
    M-SEARCH * HTTP/1.1\r\n
        [Expert Info (Chat/Sequence): M-SEARCH * HTTP/1.1\r\n]
            [Message: M-SEARCH * HTTP/1.1\r\n]
            [Severity level: Chat]
            [Group: Sequence]
        Request Method: M-SEARCH
        Request URI: *
        Request Version: HTTP/1.1
    Host:[FF02::C]:1900\r\n
    ST:urn:Microsoft Windows Peer Name Resolution Protocol: V4:IPV6:LinkLocal\r\n
    Man:"ssdp:discover"\r\n
    MX:3\r\n
    \r\n

No.     Time        Source                Destination           Protocol Info
     41 29.997061   fe80::8d69:edeb:b826:9b30 ff02::c               SSDP     M-SEARCH * HTTP/1.1 

Frame 41 (208 bytes on wire, 208 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:52.862113000
    [Time delta from previous captured frame: 3.001622000 seconds]
    [Time delta from previous displayed frame: 3.001622000 seconds]
    [Time since reference or first frame: 29.997061000 seconds]
    Frame Number: 41
    Frame Length: 208 bytes
    Capture Length: 208 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ipv6:udp:http]
    [Coloring Rule Name: HTTP]
    [Coloring Rule String: http || tcp.port == 80]
Ethernet II, Src: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b), Dst: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
    Destination: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        Address: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
    Source: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        Address: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IPv6 (0x86dd)
Internet Protocol Version 6
    0110 .... = Version: 6
        [0110 .... = This field makes the filter "ip.version == 6" possible: 6]
    .... 0000 0000 .... .... .... .... .... = Traffic class: 0x00000000
    .... .... .... 0000 0000 0000 0000 0000 = Flowlabel: 0x00000000
    Payload length: 154
    Next header: UDP (0x11)
    Hop limit: 1
    Source: fe80::8d69:edeb:b826:9b30 (fe80::8d69:edeb:b826:9b30)
    Destination: ff02::c (ff02::c)
User Datagram Protocol, Src Port: 65524 (65524), Dst Port: ssdp (1900)
    Source port: 65524 (65524)
    Destination port: ssdp (1900)
    Length: 154
    Checksum: 0xc8bd [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Hypertext Transfer Protocol
    M-SEARCH * HTTP/1.1\r\n
        [Expert Info (Chat/Sequence): M-SEARCH * HTTP/1.1\r\n]
            [Message: M-SEARCH * HTTP/1.1\r\n]
            [Severity level: Chat]
            [Group: Sequence]
        Request Method: M-SEARCH
        Request URI: *
        Request Version: HTTP/1.1
    Host:[FF02::C]:1900\r\n
    ST:urn:Microsoft Windows Peer Name Resolution Protocol: V4:IPV6:LinkLocal\r\n
    Man:"ssdp:discover"\r\n
    MX:3\r\n
    \r\n

No.     Time        Source                Destination           Protocol Info
     42 33.997434   fe80::8d69:edeb:b826:9b30 ff02::c               SSDP     M-SEARCH * HTTP/1.1 

Frame 42 (208 bytes on wire, 208 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:56.862486000
    [Time delta from previous captured frame: 4.000373000 seconds]
    [Time delta from previous displayed frame: 4.000373000 seconds]
    [Time since reference or first frame: 33.997434000 seconds]
    Frame Number: 42
    Frame Length: 208 bytes
    Capture Length: 208 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ipv6:udp:http]
    [Coloring Rule Name: HTTP]
    [Coloring Rule String: http || tcp.port == 80]
Ethernet II, Src: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b), Dst: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
    Destination: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        Address: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
    Source: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        Address: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IPv6 (0x86dd)
Internet Protocol Version 6
    0110 .... = Version: 6
        [0110 .... = This field makes the filter "ip.version == 6" possible: 6]
    .... 0000 0000 .... .... .... .... .... = Traffic class: 0x00000000
    .... .... .... 0000 0000 0000 0000 0000 = Flowlabel: 0x00000000
    Payload length: 154
    Next header: UDP (0x11)
    Hop limit: 1
    Source: fe80::8d69:edeb:b826:9b30 (fe80::8d69:edeb:b826:9b30)
    Destination: ff02::c (ff02::c)
User Datagram Protocol, Src Port: 65524 (65524), Dst Port: ssdp (1900)
    Source port: 65524 (65524)
    Destination port: ssdp (1900)
    Length: 154
    Checksum: 0xc8bd [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Hypertext Transfer Protocol
    M-SEARCH * HTTP/1.1\r\n
        [Expert Info (Chat/Sequence): M-SEARCH * HTTP/1.1\r\n]
            [Message: M-SEARCH * HTTP/1.1\r\n]
            [Severity level: Chat]
            [Group: Sequence]
        Request Method: M-SEARCH
        Request URI: *
        Request Version: HTTP/1.1
    Host:[FF02::C]:1900\r\n
    ST:urn:Microsoft Windows Peer Name Resolution Protocol: V4:IPV6:LinkLocal\r\n
    Man:"ssdp:discover"\r\n
    MX:3\r\n
    \r\n

No.     Time        Source                Destination           Protocol Info
     43 36.997260   fe80::8d69:edeb:b826:9b30 ff02::c               SSDP     M-SEARCH * HTTP/1.1 

Frame 43 (208 bytes on wire, 208 bytes captured)
    Arrival Time: Feb 12, 2010 22:47:59.862312000
    [Time delta from previous captured frame: 2.999826000 seconds]
    [Time delta from previous displayed frame: 2.999826000 seconds]
    [Time since reference or first frame: 36.997260000 seconds]
    Frame Number: 43
    Frame Length: 208 bytes
    Capture Length: 208 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ipv6:udp:http]
    [Coloring Rule Name: HTTP]
    [Coloring Rule String: http || tcp.port == 80]
Ethernet II, Src: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b), Dst: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
    Destination: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        Address: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
    Source: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        Address: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IPv6 (0x86dd)
Internet Protocol Version 6
    0110 .... = Version: 6
        [0110 .... = This field makes the filter "ip.version == 6" possible: 6]
    .... 0000 0000 .... .... .... .... .... = Traffic class: 0x00000000
    .... .... .... 0000 0000 0000 0000 0000 = Flowlabel: 0x00000000
    Payload length: 154
    Next header: UDP (0x11)
    Hop limit: 1
    Source: fe80::8d69:edeb:b826:9b30 (fe80::8d69:edeb:b826:9b30)
    Destination: ff02::c (ff02::c)
User Datagram Protocol, Src Port: 65524 (65524), Dst Port: ssdp (1900)
    Source port: 65524 (65524)
    Destination port: ssdp (1900)
    Length: 154
    Checksum: 0xc8bd [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Hypertext Transfer Protocol
    M-SEARCH * HTTP/1.1\r\n
        [Expert Info (Chat/Sequence): M-SEARCH * HTTP/1.1\r\n]
            [Message: M-SEARCH * HTTP/1.1\r\n]
            [Severity level: Chat]
            [Group: Sequence]
        Request Method: M-SEARCH
        Request URI: *
        Request Version: HTTP/1.1
    Host:[FF02::C]:1900\r\n
    ST:urn:Microsoft Windows Peer Name Resolution Protocol: V4:IPV6:LinkLocal\r\n
    Man:"ssdp:discover"\r\n
    MX:3\r\n
    \r\n

No.     Time        Source                Destination           Protocol Info
     44 40.006752   fe80::8d69:edeb:b826:9b30 ff02::c               SSDP     M-SEARCH * HTTP/1.1 

Frame 44 (208 bytes on wire, 208 bytes captured)
    Arrival Time: Feb 12, 2010 22:48:02.871804000
    [Time delta from previous captured frame: 3.009492000 seconds]
    [Time delta from previous displayed frame: 3.009492000 seconds]
    [Time since reference or first frame: 40.006752000 seconds]
    Frame Number: 44
    Frame Length: 208 bytes
    Capture Length: 208 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ipv6:udp:http]
    [Coloring Rule Name: HTTP]
    [Coloring Rule String: http || tcp.port == 80]
Ethernet II, Src: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b), Dst: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
    Destination: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        Address: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
    Source: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        Address: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IPv6 (0x86dd)
Internet Protocol Version 6
    0110 .... = Version: 6
        [0110 .... = This field makes the filter "ip.version == 6" possible: 6]
    .... 0000 0000 .... .... .... .... .... = Traffic class: 0x00000000
    .... .... .... 0000 0000 0000 0000 0000 = Flowlabel: 0x00000000
    Payload length: 154
    Next header: UDP (0x11)
    Hop limit: 1
    Source: fe80::8d69:edeb:b826:9b30 (fe80::8d69:edeb:b826:9b30)
    Destination: ff02::c (ff02::c)
User Datagram Protocol, Src Port: 65524 (65524), Dst Port: ssdp (1900)
    Source port: 65524 (65524)
    Destination port: ssdp (1900)
    Length: 154
    Checksum: 0xc8bd [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Hypertext Transfer Protocol
    M-SEARCH * HTTP/1.1\r\n
        [Expert Info (Chat/Sequence): M-SEARCH * HTTP/1.1\r\n]
            [Message: M-SEARCH * HTTP/1.1\r\n]
            [Severity level: Chat]
            [Group: Sequence]
        Request Method: M-SEARCH
        Request URI: *
        Request Version: HTTP/1.1
    Host:[FF02::C]:1900\r\n
    ST:urn:Microsoft Windows Peer Name Resolution Protocol: V4:IPV6:LinkLocal\r\n
    Man:"ssdp:discover"\r\n
    MX:3\r\n
    \r\n

No.     Time        Source                Destination           Protocol Info
     45 43.998323   fe80::8d69:edeb:b826:9b30 ff02::c               SSDP     M-SEARCH * HTTP/1.1 

Frame 45 (208 bytes on wire, 208 bytes captured)
    Arrival Time: Feb 12, 2010 22:48:06.863375000
    [Time delta from previous captured frame: 3.991571000 seconds]
    [Time delta from previous displayed frame: 3.991571000 seconds]
    [Time since reference or first frame: 43.998323000 seconds]
    Frame Number: 45
    Frame Length: 208 bytes
    Capture Length: 208 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ipv6:udp:http]
    [Coloring Rule Name: HTTP]
    [Coloring Rule String: http || tcp.port == 80]
Ethernet II, Src: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b), Dst: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
    Destination: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        Address: IPv6mcast_00:00:00:0c (33:33:00:00:00:0c)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
    Source: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        Address: Belkin_8c:8f:1b (00:17:3f:8c:8f:1b)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IPv6 (0x86dd)
Internet Protocol Version 6
    0110 .... = Version: 6
        [0110 .... = This field makes the filter "ip.version == 6" possible: 6]
    .... 0000 0000 .... .... .... .... .... = Traffic class: 0x00000000
    .... .... .... 0000 0000 0000 0000 0000 = Flowlabel: 0x00000000
    Payload length: 154
    Next header: UDP (0x11)
    Hop limit: 1
    Source: fe80::8d69:edeb:b826:9b30 (fe80::8d69:edeb:b826:9b30)
    Destination: ff02::c (ff02::c)
User Datagram Protocol, Src Port: 65524 (65524), Dst Port: ssdp (1900)
    Source port: 65524 (65524)
    Destination port: ssdp (1900)
    Length: 154
    Checksum: 0xc8bd [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Hypertext Transfer Protocol
    M-SEARCH * HTTP/1.1\r\n
        [Expert Info (Chat/Sequence): M-SEARCH * HTTP/1.1\r\n]
            [Message: M-SEARCH * HTTP/1.1\r\n]
            [Severity level: Chat]
            [Group: Sequence]
        Request Method: M-SEARCH
        Request URI: *
        Request Version: HTTP/1.1
    Host:[FF02::C]:1900\r\n
    ST:urn:Microsoft Windows Peer Name Resolution Protocol: V4:IPV6:LinkLocal\r\n
    Man:"ssdp:discover"\r\n
    MX:3\r\n
    \r\n
```

Sorry its so big. In it you get "malformed packet" error followed by "Destination unreachable"

---

### Post by the.scarecrow on 2010-02-13
Its gone quiet now. Any comments on the above output?

---

### Post by alphacrucis2 on 2010-02-14
> **the.scarecrow said:**
> Its gone quiet now. Any comments on the above output?


Looks like a bunch of weird multicast stuff going to 224.0.0.251 but that may be something to do with samba. (there's also some IPV6 stuff which is noise as far as we are concerned - IPV6 enabled so is piping up). After that I see a DNS lookup for ntp.ubuntu.com going to 192.168.1.1 which appears to have been given a good response by the router. I don't see an attempt to even lookup [www.google.com](www.google.com). To me it is looking like a problem in Lucid. I would open a launchpad ticket on it at this point.

---

### Post by the.scarecrow on 2010-02-15
I have now reported this as bug report title:

Karmic & Lucid WiFi DNS not working Bug#522337 in network-manager

Thanks for all your advice.

---

### Post by cariboo on 2010-02-15
If you check the Networking & Wireless sub-forum it also affects wired connections, not only wifi.

---

### Post by katie-xx on 2010-02-16
[SIZE=2][COLOR=Blue]I believe the DNS problem may be caused by everything being initially requested by IPV6.
The answer, for me anyhow, was to edit grub, and disable IPV6.
This does seem to be a problem with the Network manager but is easily fixed.

Kate[/COLOR][/SIZE]

---

### Post by Digikid on 2010-02-16
No it does not fix it at all.  It SIDESTEPS IT.

Even with that disabled....it STILL happens.  Even if I find the proper DNS entries...it STILL happens.  I go over and try my friends ISP....guess what????
[COLOR=Red][B]
STILL HAPPENS.[/B][/COLOR]

---

### Post by katie-xx on 2010-02-16
[SIZE=2][COLOR=Blue]Hi there. This edit should fix it ../ etc/default/grub
[/COLOR][/SIZE]
> 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
[SIZE=2][COLOR=Blue]
I can replicate the problem by re-enabing IPV6 and the fix, every time, is to disable IPV6 as above.
Hope this helps
Kate[/COLOR][/SIZE]

---

### Post by the.scarecrow on 2010-02-17
> **katie-xx said:**
> [SIZE=2][COLOR=Blue]I believe the DNS problem may be caused by everything being initially requested by IPV6.
The answer, for me anyhow, was to edit grub, and disable IPV6.
This does seem to be a problem with the Network manager but is easily fixed.

Kate[/COLOR][/SIZE]

Look, the point of this thread is that we don't want to keep fixing it, we know how to do that thanks.

We want it to just work from a fresh install, just like Windows and like Ubuntu used to in releases prior to Karmic.

I reported it as a bug but so far no progress.
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/522337](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/522337)

---

### Post by katie-xx on 2010-02-17
> **the.scarecrow said:**
> Look, the point of this thread is that we don't want to keep fixing it, we know how to do that thanks.
We want it to just work from a fresh install, just like Windows and like Ubuntu used to in releases prior to Karmic.


[SIZE=2][COLOR=Blue]Well, in that case Im afraid you will need to buy yourself a router that can handle IPV6 :)
You will then find it will, indeed, work from a fresh install.
Hope that helps
Kate[/COLOR][/SIZE]

---

### Post by alphacrucis2 on 2010-02-17
> **katie-xx said:**
> [SIZE=2][COLOR=Blue]Well, in that case Im afraid you will need to buy yourself a router that can handle IPV6 :)
You will then find it will, indeed, work from a fresh install.
Hope that helps
Kate[/COLOR][/SIZE]


My router doesn't handle IPV6 either but I don't have the problem. Karmic and Lucid work out of the box for me. There is something very weird going on with certain router/ubuntu version combinations. Much better if the NM people figure out a proper solution so nobody has to buy anything or configure workarounds. If it turns out to be a fault in the router firmware then fine but the wireshark trace the OP posted doesn't show the router doing anything wrong.

---

### Post by scaine on 2010-02-17
I've had this since Karmic too and moved to OpenDNS, thinking it was something to do with my ISP or router.  Thanks for the heads up.  I've "me too'd" on your bug.  Fingers crossed it gets the attention of the NM devs.

You can follow the mail list here : [http://mail.gnome.org/archives/networkmanager-list/2010-February/thread.html](http://mail.gnome.org/archives/networkmanager-list/2010-February/thread.html)

---

### Post by katie-xx on 2010-02-17
[SIZE=2][COLOR=Blue]These things are always interesting but it shouldnt take long to eliminate Network Manager from list of suspects. It isnt logical that Network Manager should be on the bad boys list anyhow ... think about what it does :)
The simplest way is to replace Network Manager with Wicd and see if you still have the same problems.
If you do, well it isnt Network Manager.
Ive already done this on a 9.10 set up, with IPV6 enabled.
Guess what? The exact same problem. Disable IPV6 and there is no problem.
I dont think there is anything at all to do here. Certainly not with Network Manager.
its behaving exactly as designed and so, incidentally is Wicd.
QED.

Kate[/COLOR][/SIZE]

---

### Post by alphacrucis2 on 2010-02-17
> **katie-xx said:**
> [SIZE=2][COLOR=Blue]These things are always interesting but it shouldnt take long to eliminate Network Manager from list of suspects. It isnt logical that Network Manager should be on the bad boys list anyhow ... think about what it does :)
The simplest way is to replace Network Manager with Wicd and see if you still have the same problems.
If you do, well it isnt Network Manager.
Ive already done this on a 9.10 set up, with IPV6 enabled.
Guess what? The exact same problem. Disable IPV6 and there is no problem.
I dont think there is anything at all to do here. Certainly not with Network Manager.
its behaving exactly as designed and so, incidentally is Wicd.
QED.

Kate[/COLOR][/SIZE]

Well that doesn't explain why it does work fine for me with IPV6 enabled and a router that doesn't support IPV6. You are right that it may not be NM causing the issue but the NM devs should be able to at least point the finger, where the problem really lies. To me this would appear to be a "papercut" type of problem and starting with upstreaming the issue to the NM devs would appear to be the only way forward on getting a resolution for everybody.

---

### Post by k3lt01 on 2010-02-17
> **the.scarecrow said:**
> We want it to just work from a fresh install, just like Windows and like Ubuntu used to in releases prior to Karmic.

I reported it as a bug but so far no progress.
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/522337](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/522337)If you go looking a little bit further than your own little issue you will see it has been happening since at least Gutsy, I reported it back then.

I think your getting overly worked up when you don't even really know what the issue is. It is no use reporting something that isn't at fault, I found that out with my report. Anyway people are just trying to help you out and in doing that they are most likely helping you to narrow it down to the real problem. That way you can help the devs with accurate reporting.

---

### Post by the.scarecrow on 2010-02-18
> **k3lt01 said:**
> If you go looking a little bit further than your own little issue you will see it has been happening since at least Gutsy, I reported it back then.

I think your getting overly worked up when you don't even really know what the issue is. It is no use reporting something that isn't at fault, I found that out with my report. Anyway people are just trying to help you out and in doing that they are most likely helping you to narrow it down to the real problem. That way you can help the devs with accurate reporting.

Look, I bow to your superior knowledge and I accept that I am totally ignorant when it comes to operating systems. Thankfully clever people like yourself help dumb users like me out all the time.

That said I regularly use Windows, Hardy and Itrepid on this same D-Link without having to manually specify the DNS. But then, what do I know? after all why care about new users trying out Lucid for the first time?

---

### Post by k3lt01 on 2010-02-18
There is no need to be smart in your reply. There are many of us having a similar if not identical problem and we have said how we get around it. Some of us have reported our problem as well and are trying to work with others, like yourself, to come up with a good fix.

---

### Post by Digikid on 2010-02-18
> **katie-xx said:**
> [SIZE=2][COLOR=Blue]Well, in that case Im afraid you will need to buy yourself a router that can handle IPV6 :)
You will then find it will, indeed, work from a fresh install.
Hope that helps
Kate[/COLOR][/SIZE]

Not true. I have a router that can do IPV6 and so does my neighbor.  Sorry but in this respect you are incorrect.

Also the.scarecrow is 100% correct.  He was not being smart whatsoever to your help.  It is how YOU interpret  it.

---

### Post by Digikid on 2010-02-20
Any more thoughts on how to get Canonical off their rears and fix this?

---

### Post by k3lt01 on 2010-02-20
> **Digikid said:**
> Any more thoughts on how to get Canonical off their rears and fix this?Yep being polite might be a good start. Otherwise try filing an accurate bug report.

---

### Post by the.scarecrow on 2010-02-20
> **Digikid said:**
> Any more thoughts on how to get Canonical off their rears and fix this?

I suppose its just a matter of waiting now and also assisting the devs if asked to do so.

There is still plenty of time for it to be fixed.

---

### Post by amano on 2010-02-20
Where is the bug report?

---

### Post by dentaku65 on 2010-02-20
You can fix it in your box; edit:

```
sudo vi /etc/dhcp3/dhclient.conf
```
Add at the end of the file:
```
#OpenDNS
prepend domain-name-servers 208.67.222.222, 208.67.220.220;
```
Save and reboot your machine.

---

### Post by k3lt01 on 2010-02-20
> **dentaku65 said:**
> You can fix it in your box; edit:

```
sudo vi /etc/dhcp3/dhclient.conf
```
Add at the end of the file:
```
#OpenDNS
prepend domain-name-servers 208.67.222.222, 208.67.220.220;
```
Save and reboot your machine.Check out post 16 and you will see that has already been suggested.

---

### Post by 23meg on 2010-02-20
> **the.scarecrow said:**
> I suppose its just a matter of waiting now and also assisting the devs if asked to do so.

There is still plenty of time for it to be fixed.

And that concludes this thread, which seems to be getting heated, and isn't producing anything towards fixing the issue.

The bug reported by the OP is [bug #522337]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/522337"). If you can reproduce the issue and would like to help, [https://wiki.ubuntu.com/DebuggingNetworkManager](https://wiki.ubuntu.com/DebuggingNetworkManager) can help you gather debugging information.

---

