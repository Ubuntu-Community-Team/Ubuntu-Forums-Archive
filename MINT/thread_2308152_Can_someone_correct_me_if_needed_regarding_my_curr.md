---
title: "Can someone correct me if needed regarding my current Network / DNS / OpenVPN config"
date: 2015-12-31
forum: MINT
---

### Post by Elishasmantle on 2015-12-31
ALERT>> Noob on Linux>Comedy Movie:popcorn:

Hello,

I'm asking for correction or confirmation about the way I am going about this and if I am doing it correctly? Please see details below.

1) I had issues with Networking-Manager and it not responding and I was able to get that resolved by just un-installing all packages with Network-Manager in the name and re-installing them. I used the GUI software manager.
2) nm-applet was also having to be started alt-F2 and and typing nm-applet and running it.
I edited the file /etc/xdg/autostart/nm-applet.desktop
```
OnlyShowIn=KDE;
```
and the nm-applet now starts on boot. Not sure this was the advised way to get this working but I had tried several methods posted online and nothing I tried had corrected issue.

I edited the /etc/resolv.conf as below. Now, I have seen posts about other saying there is a warning at top of file about the resolv.conf file being auto-generated, but I do not get this message and do currently believe my networking components are using this resolv.con file entries for it's dns entries. One question I do have is about DNS entries. I am under the impression that only 3 DNS entries can be used and any others in the file are dis-regarded? I have commented out the 3 cox dns entries and my preferred NordVPN dns entries I have put at the top assuming the list is used from top-to-bottom? If so my thoughts are to have 2 dns entries for my vpn provider and have 1 from opendns or google? I would then remove or comment out the remaining entries.
```

NordVPN
nameserver 162.242.211.137
nameserver 78.46.223.24
#OPENDNS
nameserver 208.67.222.222
nameserver 208.67.220.220
#Google
nameserver 8.8.8.8
nameserver 8.8.4.4
#Cox Cable
#nameserver 68.105.28.11
#nameserver 68.105.29.11
#nameserver 68.105.28.12

```

I used these sites to test for vulnerabilities:
[https://www.dnsleaktest.com/](https://www.dnsleaktest.com/)
[https://www.privateinternetaccess.com/forum/discussion/2114/ipv6-leak-dns-leak-e-mail-ip-leak](https://www.privateinternetaccess.com/forum/discussion/2114/ipv6-leak-dns-leak-e-mail-ip-leak)
[https://www.perfect-privacy.com](https://www.perfect-privacy.com)
[http://dnsleak.com/](http://dnsleak.com/)
[https://ipleak.net/](https://ipleak.net/)
At https:ipleak.net Fixed a Mozilla WebRTC leak:
Mozilla Firefox: Type "about:config&#8221; in the address bar. Scroll down to &#8220;media.peerconnection.enabled&#8221;, double click to set it to false.
and tested for Torrent Address detection: On connection without OpenVPN my IP is seen by my ISP provider, using same test connected to OpenVPN my IP is detected from my VPN provider.

When connected to OpenVPN I think that I am passing all tests I have run on above mentioned websites, but I do on occasion while connected to OpenVPN have the test sites detect a opendns name server, which, I thought, I do not want to happen, but rather my 2 NordVPN dns IP's to exclusively be used?

I also would like to know if it is true that disabling IPv6 is suggested due to possible : Slowness, security or openvpn dns leak issues?

Thank You,

Elishasmantle

---

### Post by dave205 on 2015-12-31
Yep!  I've been fighting this as well. I can't comment on the issue you're having with the network manager startgin as I have not seen those issues. I have however been having DNS issues like you. 

In summary I have found that if I run openvpn from CLI (with the fix described here [http://www.ubuntubuzz.com/2015/09/how-to-fix-openvpn-dns-leak-in-linux.html](http://www.ubuntubuzz.com/2015/09/how-to-fix-openvpn-dns-leak-in-linux.html)), then everything works fine. The only "problem" is that I have to run it from command line (pain in the a$$) and also you have to enter your username & pwd every time (another pain). If I use the network manager then I cannot get Ubuntu 15.10 to use the specified DNS servers and ignore the ones from my ISP. 

read here - [http://ubuntuforums.org/showthread.php?t=2307975](http://ubuntuforums.org/showthread.php?t=2307975)  

Also it is my understanding that one cannot simply edit the resolv.conf file in Ubuntu like you can in RedHat. I have yet to find confirmation of that though.

What Ubuntu version are you using?

---

### Post by Elishasmantle on 2016-01-01
Dave, I actually run Linux Mint 17.2 x64 but I always use Ubuntu forums because they are so vastly much larger and fixes I find work nearly always the same.

I'm surprised I only got one reply so far as openvpn, network-manager and dns leak articles are a pretty big topic once a person gets to looking around.

In the properties for the VPN there are fields for the DNS. I am wondering if dns server entries are put there they will be used instead of pulling them from somewhere else?

Dave, Are you familiar with the RESOLVCONF app and how it dynamically works with programs and sets networking info? There are several articles on this topic. So for the VPN, resolvconf dynamically sets those settings up and auto-generates the settings needed, well, these settings can be modified if needed. Going to dig a little and see if I can use those settings to correct issue.

Did you ever hear of disabling IPv6 because of the issues I mentioned in my first post?

Thank You,

Elishasmantle

---

### Post by howefield on 2016-01-01
Thread moved to the "*MINT*" forum.

---

### Post by dave205 on 2016-01-01
> **Elishasmantle said:**
> Dave, I actually run Linux Mint 17.2 x64 but I always use Ubuntu forums because they are so vastly much larger and fixes I find work nearly always the same.

I'm surprised I only got one reply so far as openvpn, network-manager and dns leak articles are a pretty big topic once a person gets to looking around.

In the properties for the VPN there are fields for the DNS. I am wondering if dns server entries are put there they will be used instead of pulling them from somewhere else?

Dave, Are you familiar with the RESOLVCONF app and how it dynamically works with programs and sets networking info? There are several articles on this topic. So for the VPN, resolvconf dynamically sets those settings up and auto-generates the settings needed, well, these settings can be modified if needed. Going to dig a little and see if I can use those settings to correct issue.

Did you ever hear of disabling IPv6 because of the issues I mentioned in my first post?

Thank You,

Elishasmantle

I saw those fields in the config files (openvpn & network config manager both) as well.  I haven't had time to explore further but I have 2 more pages bookmarked that I want to dig into deeper about it. I'm not sure how resolvconf exactly works but I think it is a script that looks to see if the vpn is UP or DOWN and then runs to set the DNS. From what I've seen though, you do not set the DNS in the resolv.conf file like you do in RedHat.   

As for IPv6, I think that only applies if you are given an IPv6 address (which most are not).  Bottom of page talks ab IPv6 - [https://www.blackvpn.com/support/linux/linux-openvpn-cli/](https://www.blackvpn.com/support/linux/linux-openvpn-cli/)  also though It talks of a VPN Demon which I want to look in to. 

Here's the links I hope to look more into later - [https://support.blackvpn.com/kb/faq.php?id=74](https://support.blackvpn.com/kb/faq.php?id=74)  (I'd really rather not deal with the firewall rules. I just want privacy when I activate the VPN, and the system to behave "normally" when its off.)

---

### Post by Elishasmantle on 2016-01-01
Dave,

I'll be using my Ubuntu OS from now on so my posts don't get moved to a different group. That way my posts will stay in Ubuntu Area Forums instead of sub/other topic forums.

The issue here pertains to Network-Manager and OpenVPN and is affecting multiple flavors of Linux. But anyway when I gather more info I will get back to you.

elishasmantle

---

