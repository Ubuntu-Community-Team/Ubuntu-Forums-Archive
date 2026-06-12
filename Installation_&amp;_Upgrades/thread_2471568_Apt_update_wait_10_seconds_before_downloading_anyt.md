---
title: "Apt update wait 10 seconds before downloading anything."
date: 2022-02-03
forum: Installation &amp; Upgrades
---

### Post by georgesgiralt on 2022-02-03
Hello Guys,
Since some time ™ when I run :
```
 sudo apt update
```
the command stalls for (timed) 10s and then start to display 
```
Atteint*:1 http://fr.archive.ubuntu.com/ubuntu focal InRelease
Atteint*:2 http://dl.google.com/linux/chrome/deb stable InRelease                                                                                                                                          
Réception de*:3 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]                                                                                                                        
Atteint*:4 http://dl.google.com/linux/earth/deb stable InRelease                                                                                                                                           
Atteint*:5 http://ppa.launchpad.net/phoerious/keepassxc/ubuntu focal InRelease                                                                                                                             
Atteint*:6 https://repo.skype.com/deb stable InRelease                                                                                                                                                     
Réception de*:7 http://fr.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]                                                                                                                       
Atteint*:8 http://lenovo.archive.canonical.com focal InRelease                                                                                                                                             
Atteint*:9 http://ppa.launchpad.net/apandada1/foliate/ubuntu focal InRelease                                                                                                                               
Atteint*:10 https://deb.opera.com/opera-stable stable InRelease                                                                                                                                            
Réception de*:11 https://mega.nz/linux/MEGAsync/xUbuntu_20.04 ./ InRelease [2&#8239;441 B]                                                                                                              
Réception de*:12 http://fr.archive.ubuntu.com/ubuntu focal-backports InRelease [108 kB]                                                                               
Atteint*:13 http://ppa.launchpad.net/atareao/atareao/ubuntu focal InRelease                              
Atteint*:14 https://packages.microsoft.com/ubuntu/20.04/prod focal InRelease                                                    
Atteint*:15 http://ppa.launchpad.net/audio-recorder/ppa/ubuntu focal InRelease                          
Atteint*:16 http://ppa.launchpad.net/dismine/valentina-dev/ubuntu focal InRelease             
Atteint*:17 http://ppa.launchpad.net/heyarje/makemkv-beta/ubuntu focal InRelease
Atteint*:18 http://ppa.launchpad.net/mkusb/ppa/ubuntu focal InRelease
Atteint*:19 http://ppa.launchpad.net/musicbrainz-developers/stable/ubuntu focal InRelease
Atteint*:20 http://ppa.launchpad.net/shutter/ppa/ubuntu focal InRelease
Atteint*:21 http://ppa.launchpad.net/slimbook/slimbook/ubuntu focal InRelease
Réception de*:22 http://security.ubuntu.com/ubuntu focal-security/main amd64 DEP-11 Metadata [40,7 kB]
Réception de*:23 http://security.ubuntu.com/ubuntu focal-security/universe amd64 DEP-11 Metadata [66,2 kB]
Réception de*:24 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 DEP-11 Metadata [2&#8239;464 B]
Réception de*:25 http://fr.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [1&#8239;550 kB]
.........................................
```
So the command is "running fine" but after a 10 second delay. 
I've searched all I can, but to no avail. 
I've also tried to run apt with debug :
```
sudo apt -oDebug::pkgAcquire::Worker=1 update
```
but I did not understand a bit of what I got... 
So please, could you help me solve this annoying problem ? 
Thank you in advance and have a nice and bright day !

---

### Post by TheFu on 2022-02-05
My first guess is that your primary DNS setting is broken.  I'd check that.

---

### Post by georgesgiralt on 2022-02-05
Hello TheFu,
Thank you for your answer. 
I'd thought of that and then excluded it because all my machines get their DNS settings from the ISP router in the house via DHCP and, thus, get the same setting. Only one machine shows this behavior (and it is not wired but with Wifi connection). 
Here is that I've got from resolvectl :
```
# resolvectl
Global
       LLMNR setting: no                  
MulticastDNS setting: no                  
  DNSOverTLS setting: no                  
      DNSSEC setting: no                  
    DNSSEC supported: no                  
          DNSSEC NTA: 10.in-addr.arpa     
                      16.172.in-addr.arpa 
                      168.192.in-addr.arpa
                      17.172.in-addr.arpa 
                      18.172.in-addr.arpa 
                      19.172.in-addr.arpa 
                      20.172.in-addr.arpa 
                      21.172.in-addr.arpa 
                      22.172.in-addr.arpa 
                      23.172.in-addr.arpa 
                      24.172.in-addr.arpa 
                      25.172.in-addr.arpa 
                      26.172.in-addr.arpa 
                      27.172.in-addr.arpa 
                      28.172.in-addr.arpa 
                      29.172.in-addr.arpa 
                      30.172.in-addr.arpa 
                      31.172.in-addr.arpa 
                      corp                
                      d.f.ip6.arpa        
                      home                
                      internal            
                      intranet            
                      lan                 
                      local               
                      private             
                      test                

Link 4 (enx00e04c685fcb)
      Current Scopes: none
DefaultRoute setting: no  
       LLMNR setting: yes 
MulticastDNS setting: no  
  DNSOverTLS setting: no  
      DNSSEC setting: no  
    DNSSEC supported: no  

Link 3 (wlp0s20f3)
      Current Scopes: DNS          
DefaultRoute setting: yes          
       LLMNR setting: yes          
MulticastDNS setting: no           
  DNSOverTLS setting: no           
      DNSSEC setting: no           
    DNSSEC supported: no           
  Current DNS Server: 212.27.40.241
         DNS Servers: 151.80.222.79
                      212.27.40.240
                      212.27.40.241
                      fd0f:ee:b0::1
          DNS Domain: ~.           

Link 2 (enp44s0)
      Current Scopes: none
DefaultRoute setting: no  
       LLMNR setting: yes 
MulticastDNS setting: no  
  DNSOverTLS setting: no  
      DNSSEC setting: no  
    DNSSEC supported: no 
#
```
So I'm puzzled... 
Have a nice day !

---

### Post by TheFu on 2022-02-05
Some guessing ... 

So ... wifi and using the ISP DNS servers? For a desktop, I wouldn't use wifi nor the slow ISP DNS servers. Actually, I wouldn't use resolved either.  Seems you have 4 DNS server listed. Can you reduce that to just 2 and be certain to remove 151.80.222.79, since it isn't being used.  It is listed in the DNS records as a "Failover Ips".  

Actually, if you look at the DNS order used, it seems the 3rd in the list is what is answering, so the first 2 are timing out.  Is 1.1.1.1 and 1.0.0.1 not faster?  

I think if IPv6 is available, then Ubuntu uses that preferentially. If you don't use IPv6, best to disable it with grub options. If you do use it, move the primary DNS to the first one.

If you remove resolverd, I think that could help too. Let me know if that is something useful. As it is, you have dns caching locally. Does the router not provide DNS caching? If it does, enable that and point all your DHCP and static system to the router for DNS. That will be faster, almost certainly.  

For some wifi setups, the connection is dropped after 30 seconds and has to re-connect before any data can be requested.  Often, this is a default for a laptop, so you'll want to research if this is happening or not. Use LAN systems to check it, not the internet. We don't want too much complexity when trying to figure out networking issues.

---

### Post by georgesgiralt on 2022-02-05
I was not clear enough. 
I've a desktop machine on a wired connection to the ISP router (Free, in France). This machine gets it's IP information from DHCP (including DNS settings) and is running 20.04.3 LTS software. 
My problem above is on a laptop, running same Ubuntu version, but with different software installed (! don't know if this make a difference). This laptop use Wifi to connect to the very same ISP router (provides both wired and wifi connection) and get it's IP information via DHCP including route and DNS. 
I'm not sure I understand fully what you wrote above. So I will have to do some digging and checks to reply to you. 
HAve a nice day !

---

### Post by TheFu on 2022-02-05
> **georgesgiralt said:**
> I was not clear enough. 

It could easily be me too.  We'll figure it out.

> **georgesgiralt said:**
> 
I've a desktop machine on a wired connection to the ISP router (Free, in France). This machine gets it's IP information from DHCP (including DNS settings) and is running 20.04.3 LTS software. 
My problem above is on a laptop, running same Ubuntu version, but with different software installed (! don't know if this make a difference). This laptop use Wifi to connect to the very same ISP router (provides both wired and wifi connection) and get it's IP information via DHCP including route and DNS. 
I'm not sure I understand fully what you wrote above. So I will have to do some digging and checks to reply to you. 
HAve a nice day !

The laptop/wifi system is using wifi?  So that's why the re-connection could be happening.  There is usually a wifi setting or power setting to control the wifi radio which prevents power-saving mode.  I've never had this issue. I don't use wifi on my laptop, but I've seen it recommended in these forums - disable power management for the wifi radio. [https://askubuntu.com/questions/85214/how-can-i-prevent-iwconfig-power-management-from-being-turned-on](https://askubuntu.com/questions/85214/how-can-i-prevent-iwconfig-power-management-from-being-turned-on) seems related.

If the laptop has both wired and wifi enabled at the same time, that could cause LAN routing issues too. Only enable 1 or the other (wired/wifi) on a system at a time.

Or are both showing the same issue?

Which other systems aren't seeing issues - and which applications?  For some time, Android systems ignored DNS settings and always contacted google's DNS at 8.8.8.8 regardless.

---

### Post by georgesgiralt on 2022-02-05
So :
Laptop :Wifi turned off. Then Ethernet cable plugged in Resolvectl gives : 
```
Link 4 (enx00e04c685fcb)
      Current Scopes: DNS          
DefaultRoute setting: yes          
       LLMNR setting: yes          
MulticastDNS setting: no           
  DNSOverTLS setting: no           
      DNSSEC setting: no           
    DNSSEC supported: no           
  Current DNS Server: fd0f:ee:b0::1
         DNS Servers: 151.80.222.79
                      212.27.40.240
                      212.27.40.241
                      fd0f:ee:b0::1
          DNS Domain: ~.           

Link 3 (wlp0s20f3)
      Current Scopes: none         
DefaultRoute setting: no           
       LLMNR setting: yes          
MulticastDNS setting: no           
  DNSOverTLS setting: no           
      DNSSEC setting: no           
    DNSSEC supported: no           
         DNS Servers: fd0f:ee:b0::1
          DNS Domain: ~.    
```
Apt update still delays 10 seconds it's work. 
On the Desktop machine :
Wired connection. Same DHCP settings as the laptop. 
Apt update react instantly. 
As you can see, this time the IPV6 DNS  setting is used first.

---

### Post by TheFu on 2022-02-05
What is in the /etc/resolv.conf file?  That's what matters ... along with the **route -n** output.  resolved and all systemd-resolved stuff only modifies those settings. They aren't involved in the middle.

Would be good to see the differences in the laptop and desktop for those two things.

Is the laptop using an SSD?

---

### Post by georgesgiralt on 2022-02-05
Yest the laptop is stuffed with SSD drives and the desktop too (for the system)
Laptop : 
```
# cat /etc/resolv.conf
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "resolvectl status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.

nameserver 127.0.0.53
options edns0 trust-ad
# route -n
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
0.0.0.0         192.168.0.254   0.0.0.0         UG    100    0        0 enx00e04c685fcb
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enx00e04c685fcb
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enx00e04c685fcb

```
And the desktop :
```
#  cat /etc/resolv.conf
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "resolvectl status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.

nameserver 127.0.0.53
options edns0 trust-ad
# route -n
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
0.0.0.0         192.168.0.254   0.0.0.0         UG    100    0        0 eno1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eno1
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 eno1

```

---

### Post by TheFu on 2022-02-05
Short of removing all systemd-resolved dependencies (which we don't need), I have just 1 more guess.
What device is enx00e04c685fcb?  Model number and vendor, please.  Could there be a short in the connection from the PC to the local switch?

---

### Post by MAFoElffen on 2022-02-05
@both TheFu and the OP...  Just FYI...

He is using defaults for Resolv... The default (currently) for /etc/resolv.conf is a symlink there, instead of a file, and that file it points to is built 'dynamically' with each boot. You can replace it with a real file to set as manual, but there are many ways to override the User selected NameServers before doing something like that... First of which would be to specify it in the NetPlan .yaml file.

Just because he is DHCP, he can still specify preferred NameServers in NetPlan settings... That will overrided that part of that. That is what I would recommend, and what I think TheFu is hinting at...

If Server Edition, 'managed' is via networkd. If Desktop, it is going to say it is managed via network-manager... Which is still networkd, but goes through the Gnome GUI utilities first (in-between). Both still look at the NetPlan .yaml def file. If he is Desktop Edition, he can go to the Gnome GUI Utitls to say where he wants his NameServers...

Setting it to 1.1.1.1 is CloudFlare's main OpenDNS Server pool... Which is secure and the fastest out there.

Just saying what is running around in my head about this.

---

### Post by georgesgiralt on 2022-02-05
The Ethernet interface is  on a Thunderbolt  dock and is a ID 0bda:8153 Realtek Semiconductor Corp. RTL8153 Gigabit Ethernet Adapter. On the laptop there is one Ethernet interface which is ... also a Realtek : Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15) ...
So I doubt it make any difference. 
No the connection betwen the laptop and the switch is perfect. I made the cable myself and use it often without any problem or error. And it is normally used for a printer. 
Obviously, the problem is not here.

---

### Post by MAFoElffen on 2022-02-05
I believe and agree with TheFu that the problem is at your ISP, where it seems to be timing out on their first two DNS server choices your ISP has set... It does not seem to be a problem with your hardware.

He was hinting that you can "tune" that to adjust for that . bypass their settings by specify your own preference of NameServers to: 1.1.1.1, 1.1.1.0, then use the one it is failing over to at your own ISP as the third choice. That is how I read and interpreted his posts to you. I agree that "that" is a good plan to try.

If you can post your /etc/netplan/[whatever_name].yaml file within CODE tags in a post, he can recommend what changes you need to do there to do that,,, I am on my way into work.

---

### Post by georgesgiralt on 2022-02-05
MAFoElffen, the dns settings in NetworkManager GUI are to use DHCP values for IPV4 and IPV6.  And it does. Resolvectl shoes that as it gave the DNS I set up into the Proxad router DHCP server. Both the laptop and the desktop use the very same settings (checked) the only differences between them being that the desktop primary use a wired connection and the laptop a Wifi connection. 
As per the repos, the laptop has more of them configured as I have a set of software different from the set my wife use on it's machine.
As the behavior on the laptop is not changed when I plug a cable into one of it's interfaces, and given it use the same DNS servers as the desktop, and still shox the delay in apt response, IMHO, this issue is not network related. (I was trained at IPV4 networks but was not top notch when I was working, and now I'm retired, so I'm becoming worse.... )

Anyway, thank you for the ideas you gave me ! Have a nice Sunday !

---

### Post by georgesgiralt on 2022-02-05
> **MAFoElffen said:**
> I believe and agree with TheFu that the problem is st your ISP, where it is timing out on the first two DNS server choices your ISP has set... It does not seem to be a problem with your hardware.

He was hinting that you can "tune" that to adjust for that . bypass their settings by specify your own preference of NameServers to: 1.1.1.1, 1.1.1.0, then use the one it is failing over to at your own ISP as the third choice. That is how I read and interpreted his posts to you. I agree that "that" is a good plan to try.

Sorry, but I disagree. 
Both computer use the same ISP router to access the internet. One via Wifi and the router, the other via a wire to the very same router and the very same DNS settings. 
So maybe the ISP chosen DNS are not the best one and/or they want to "see" what I'm looking at but they do so identically regarding the desktop traffic and the laptop traffic. I doubt the behavior they set is different from one computer to the other. Both machines run the same Ubuntu version with the same set of updates applied, the only difference being that the desktop got it's DHCP lease this morning and my laptop got a new one every time I unplugged a cable or turned Wifi on or off. 
I will try to use your given DNSs tomorrow if time permit either in DHCP server setting or at the laptop NetworkManager GUI. 
This thing is becoming strange, isn't it ?

---

### Post by MAFoElffen on 2022-02-05
Yes... Agreed that "you are using DHCP" and TheFu ID'ed that those ISP set NameServer settings are failing over on the first two NameServers to a third NameServer. You can override those NameServer Settings, while still using DHCP for everything else... By giving it "Hints" for that.

You lose nothing by giving it a try right? If it works, then solved. If not, it rules that out to check that off the list of possible problems, and guides you to try other things.

---

### Post by georgesgiralt on 2022-02-05
OK. So I set in NetworkManager GUI local DNS settings. 1.1.1.1 and 1.1.1.0 and... guess what ? apt update took 12 seconds to start working. 
I'll switch to something else. Maybe viewing a film on DVD as this things begin to itch a bit. 
Thank you both very very much for your help ! 
I'll sleep on it and see what this give me ;-) 
Have a nice and bright Sunday !

---

### Post by MAFoElffen on 2022-02-05
Thank you for trying that. That does check that off the list now. Just getting ready to walk inside to my work.

On my breaks, will read the rest of your posts and see if I see anything else.

Have you done a Dig Trace to see the timings of where it hits what, when? That might be what to look at next...
```

dig +trace http://fr.archive.ubuntu.com

```

---

### Post by georgesgiralt on 2022-02-05
Took only 19 ms ... 
```

# dig +trace http://fr.archive.ubuntu.com

; <<>> DiG 9.16.1-Ubuntu <<>> +trace http://fr.archive.ubuntu.com
;; global options: +cmd
.			58084	IN	NS	h.root-servers.net.
.			58084	IN	NS	i.root-servers.net.
.			58084	IN	NS	j.root-servers.net.
.			58084	IN	NS	k.root-servers.net.
.			58084	IN	NS	l.root-servers.net.
.			58084	IN	NS	m.root-servers.net.
.			58084	IN	NS	a.root-servers.net.
.			58084	IN	NS	b.root-servers.net.
.			58084	IN	NS	c.root-servers.net.
.			58084	IN	NS	d.root-servers.net.
.			58084	IN	NS	e.root-servers.net.
.			58084	IN	NS	f.root-servers.net.
.			58084	IN	NS	g.root-servers.net.
;; Received 262 bytes from 127.0.0.53#53(127.0.0.53) in 11 ms

com.			172800	IN	NS	a.gtld-servers.net.
com.			172800	IN	NS	b.gtld-servers.net.
com.			172800	IN	NS	c.gtld-servers.net.
com.			172800	IN	NS	d.gtld-servers.net.
com.			172800	IN	NS	e.gtld-servers.net.
com.			172800	IN	NS	f.gtld-servers.net.
com.			172800	IN	NS	g.gtld-servers.net.
com.			172800	IN	NS	h.gtld-servers.net.
com.			172800	IN	NS	i.gtld-servers.net.
com.			172800	IN	NS	j.gtld-servers.net.
com.			172800	IN	NS	k.gtld-servers.net.
com.			172800	IN	NS	l.gtld-servers.net.
com.			172800	IN	NS	m.gtld-servers.net.
com.			86400	IN	DS	30909 8 2 E2D3C916F6DEEAC73294E8268FB5885044A833FC5459588F4A9184CF C41A5766
com.			86400	IN	RRSIG	DS 8 1 86400 20220218170000 20220205160000 9799 . ale27rGPTMteUIm1pYjP+on1dAfp7Qt1ymZ+Xzl62GWGcMHXiZ+VRy65 sv4j1dbF/2QlgudX3xHKnxxY3dSRbA+/6Nvt0Vu+BTaWCfhBrRc8sdeE 6tQGhfAaQSI4ChT/u7Q4tWYt+onYWgm/QLhocc8JqgVe/IE0pWWXoQAv Mc8OzFX/n+Yp82C/qalQVDNOJy1dElSrJqZQlJukH6MUxnEYYoU5pDpb inOdcVaGqc5GKdTBsxf9hJLIr9YOXxOcKWnqJeosckH5y2LtjB/2DNtD jLofQfqmpM8FCnH/dlhbIKB73Lb848XvBrFlNXt6b/lH/+xL9l9ysCl4 JX+qBw==
;; Received 1188 bytes from 2001:7fd::1#53(k.root-servers.net) in 19 ms

ubuntu.com.		172800	IN	NS	ns1.canonical.com.
ubuntu.com.		172800	IN	NS	ns2.canonical.com.
ubuntu.com.		172800	IN	NS	ns3.canonical.com.
CK0POJMG874LJREF7EFN8430QVIT8BSM.com. 86400 IN NSEC3 1 1 0 - CK0Q1GIN43N1ARRC9OSM6QPQR81H5M9A NS SOA RRSIG DNSKEY NSEC3PARAM
CK0POJMG874LJREF7EFN8430QVIT8BSM.com. 86400 IN RRSIG NSEC3 8 2 86400 20220212052323 20220205041323 38535 com. CBwoS9EXFknrXU9PibFkgxIe3I00/r/qjlGzv48XNFY477Jhq/cTvfgq 9hRZmio2p6x1de4fWkPT1pe9CWkyDBvIZAg6ezURmsZgehZUwDeJJ1Mb NfTT/NCrXkN8dyuLaG+sXL3UHje6z1m6Nje5SkuQ0+Am6Kx+yotFXGKE dC/MEnhTIJgpMPk9KJQTdf09m5Q7xRhYTyY+JkMV+gchKg==
894IO8AM9NDQ8VM84GPASGU0QDHFLFS1.com. 86400 IN NSEC3 1 1 0 - 894J5FN26LROBLRR48NQHCUNICNAGJQ6 NS DS RRSIG
894IO8AM9NDQ8VM84GPASGU0QDHFLFS1.com. 86400 IN RRSIG NSEC3 8 2 86400 20220212062835 20220205051835 38535 com. T/cZ5Nr2ihvftJ0ePvZzeNWlmZGNbHoxn5w7ZRcJWx97jyY41BmNkMAQ eegZXbX5AOmRkEUtugUGDfe61oqk0wpQabIIoaQglotldiTTb0XCRnf/ YHQdFUmPEI9jAeTZQMbKYZNxkMjkYAhWhQxNW84Yp3LqNzGV5kzMCptL ktzB9MaKue1a2e/O4FNnC0CKj/7BRwdYO4RkaHt/c0Sv4w==
;; Received 718 bytes from 192.52.178.30#53(k.gtld-servers.net) in 27 ms

http://fr.archive.ubuntu.com. 60 IN	A	91.189.88.142
http://fr.archive.ubuntu.com. 60 IN	A	91.189.88.152
http://fr.archive.ubuntu.com. 60 IN	A	91.189.91.38
http://fr.archive.ubuntu.com. 60 IN	A	91.189.91.39
ubuntu.com.		172800	IN	NS	ns1.canonical.com.
ubuntu.com.		172800	IN	NS	ns2.canonical.com.
ubuntu.com.		172800	IN	NS	ns3.canonical.com.
;; Received 233 bytes from 91.189.95.3#53(ns2.canonical.com) in 19 ms


```
We are chasing the wrong rabbit here.

---

### Post by MAFoElffen on 2022-02-06
Yes we are chasing the wrong ghost. 

Those timings are great. They are better than I get here.

---

### Post by TheFu on 2022-02-06
We are getting a trickle of information.
[LIST]
[*]Multiple systems use DHCP.
[*]The DNS settings come from the ISP for all systems - Linux and non-Linux.
[*]2 Ubuntu systems running the same release with DHCP settings.
[*]Both Ubuntu systems use systemd-resolved (eeeew, I'm not a fan)
[LIST]
[*][*]1 is fast, the Ubuntu desktop
[*][*]The other is slow.  The slow one is a laptop. On the laptop, both wifi and wired connections both show the same behavior.
[*][*]On the laptop, there are realtek network devices (eeeew, I'm not a fan).
[*][*]On the laptop, there are more repos configured.
[/LIST]
[*]The user makes their own cable and declared "the cable is good."
[/LIST]

I'm a huge believer in simplify and test, repeat.  Keep simplifying until the issue can only be 1 thing, then fix that.

Suggestions:
[LIST=1]
[*]Simplify the laptop's repos. This appears to be the main difference, so perhaps one of the non-Canonical repos is just slow.
[*]Change the cable with another that is proven good. Change the switch port used too, please. Just swap them around. It is always the simple things. 
[*]Set the DNS settings in the router to use 1.1.1.1 and 1.0.0.1.  You should probably be using these any way. They are typically fast and definitely privacy related. If you want more privacy, consider settings DNSSEC or DNSoHTTPS so your ISP cannot snoop on DNS traffic locations.
[*]Remove systemd-resolved.  While you are at it, enable the DNS cache on the router and point the DHCP settings for DNS to the router LAN-IP.  
[*]If you want more privacy, less tracking, and overall faster web/internet, then setup a pi-hole (or 2) on your network and use those as DNS caching servers. If you don't get any advertising, that won't slow typical web browsing down and clog the pipe. pi-hole can run on a raspberry-pi, inside a VM, inside a Linux container. It doesn't need the entire r-Pi CPU, so that device can be used for 20 other things too.  I run it in LXD containers on x86-64 systems that stay powered 24/7/365. If power use is a consideration, many routers can run the Pi-Hole software too.
[/LIST]

A question.  Is the issue with all network access on the LAN, only internet, or only with specific repos?

That's all I got for now.

---

### Post by georgesgiralt on 2022-02-06
Hello TheFu, and good morning!
Some answers and some research I've done today :
At the question "On the laptop, there are realtek network devices (eeeew, I'm not a fan)." actually, only the Ethernet interfacesare from Realtek. The Wifi is an Intel card. The desktop use an Intel Ethernet interface. 
This morning I tried to trace DNS traffic to each of the repos configured on the laptop. The fastest is at 12 ms (!) and the slowest at 350 ms. This latter one is the only to be slow. All others are in the 12~25 ms range. So maybe we can exclude this out. I've done the math. Even if I do a dns query for each line of repo, I'm well under the second for all the searches ! (there are actually multiples repos on the same server for example ppa.launchpad.net )
Also, I've tried to remove all DNS settings from DHCP and said the computers to use the router as a DNS source (forcing them to use the ISP defined ones). No change at all in speed or behavior. 
I can also tell you that surfing on the Web is fast even if I try to reach a site I did not try for ages. It is almost instantaneous so no DNS lagging .... 
I've tried your "change your cable" approach to a factory made one set on a different router port. No change at all. Not surprising given that the laptop behave consistently whatever interface is used to connect to the Web.
I'll try to use a set of DNS half in IPV4 and half in IPV6 just to see but IMHO this is not where the problem lies, even if it is a good advice. (I have some work to do on this subject I'm not keen enough so will definitely try to follow your advice)...
The puzzling thing is tat there is no information in the log file from apt. (or I'm not good enough to find it)  
Thank you very much for your time and wisdom, much appreciated.

---

### Post by TheFu on 2022-02-06
Ok, so we are done with DNS and cabling and switch issues. Those have been excluded.  In fact, your DNS times are faster than mine hitting a PiHole on my LAN.

I'm back to the differences in repos. Alas, my knowledge about those is superficial.  The inxi tool can dump all the repos configured on a system. **inxi -r** is the command. If it were me, I'd get the list for both Ubuntu systems and compare them. Then I'd remove 1 and test until the problem repo becomes clear.  Repeat. My 20.04 system has 11 repos configured. I see a few I should remove. **sudo add-apt-repository --remove {repo name}** is the command. This only works for PPAs - which are the most likely problem, by far.

---

### Post by MAFoElffen on 2022-02-06
Remember that the UbuntuForums 'system-info' script has 2 routines to list the repo's from the sources.list and from sourcesd... Could be,

But extracted from what you had listed in the first post:
```

http://fr.archive.ubuntu.com/ubuntu focal InRelease
http://fr.archive.ubuntu.com/ubuntu focal-backports                                                                             
http://fr.archive.ubuntu.com/ubuntu focal-updates InRelease
http://security.ubuntu.com/ubuntu focal-security InRelease
http://dl.google.com/linux/chrome/deb stable InRelease
http://dl.google.com/linux/earth/deb stable InRelease
https://packages.microsoft.com/ubuntu/20.04/prod focal InRelease                                                    
https://repo.skype.com/deb stable InRelease
http://lenovo.archive.canonical.com focal InRelease                                                                                                                                             
https://deb.opera.com/opera-stable stable InRelease                                                                                                                                            
https://mega.nz/linux/MEGAsync/xUbuntu_20.04 ./ InRelease                                                                                                          
http://ppa.launchpad.net/phoerious/keepassxc/ubuntu focal InRelease
http://ppa.launchpad.net/apandada1/foliate/ubuntu focal InRelease                                                                                                                               
http://ppa.launchpad.net/atareao/atareao/ubuntu focal InRelease                              
http://ppa.launchpad.net/audio-recorder/ppa/ubuntu focal InRelease                          
http://ppa.launchpad.net/dismine/valentina-dev/ubuntu focal InRelease             
http://ppa.launchpad.net/heyarje/makemkv-beta/ubuntu focal InRelease
http://ppa.launchpad.net/mkusb/ppa/ubuntu focal InRelease
http://ppa.launchpad.net/musicbrainz-developers/stable/ubuntu focal InRelease
http://ppa.launchpad.net/shutter/ppa/ubuntu focal InRelease
http://ppa.launchpad.net/slimbook/slimbook/ubuntu focal InRelease

```

If you ping or used traceroute to each, that might find if something is responding slowly to you...

---

### Post by TheFu on 2022-02-06
I would remove these:
```
[http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
[http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable InRelease
[https://packages.microsoft.com/ubuntu/20.04/prod](https://packages.microsoft.com/ubuntu/20.04/prod) focal InRelease                                                    
[https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease
[https://deb.opera.com/opera-stable](https://deb.opera.com/opera-stable) stable InRelease                                                                                                                                            
[https://mega.nz/linux/MEGAsync/xUbuntu_20.04](https://mega.nz/linux/MEGAsync/xUbuntu_20.04) ./ InRelease                                                                                                          
[http://ppa.launchpad.net/phoerious/keepassxc/ubuntu](http://ppa.launchpad.net/phoerious/keepassxc/ubuntu) focal InRelease
[http://ppa.launchpad.net/apandada1/foliate/ubuntu](http://ppa.launchpad.net/apandada1/foliate/ubuntu) focal InRelease                                                                                                                               
[http://ppa.launchpad.net/atareao/atareao/ubuntu](http://ppa.launchpad.net/atareao/atareao/ubuntu) focal InRelease                              
[http://ppa.launchpad.net/audio-recorder/ppa/ubuntu](http://ppa.launchpad.net/audio-recorder/ppa/ubuntu) focal InRelease                          
[http://ppa.launchpad.net/dismine/valentina-dev/ubuntu](http://ppa.launchpad.net/dismine/valentina-dev/ubuntu) focal InRelease             
[http://ppa.launchpad.net/heyarje/makemkv-beta/ubuntu](http://ppa.launchpad.net/heyarje/makemkv-beta/ubuntu) focal InRelease
[http://ppa.launchpad.net/musicbrainz-developers/stable/ubuntu](http://ppa.launchpad.net/musicbrainz-developers/stable/ubuntu) focal InRelease
[http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) focal InRelease
[http://ppa.launchpad.net/slimbook/slimbook/ubuntu](http://ppa.launchpad.net/slimbook/slimbook/ubuntu) focal InRelease

```
and keep the rest, as a starting point.  Perhaps you can see my pattern?

---

### Post by MAFoElffen on 2022-02-07
As a quick test... Without having to manually edit the files... You could just start the "Updates & Software" GUI > go to the Other Software Tab, then uncheck the checkboxes for those, then try an apt update and see if that makes a difference...

What that does in the background is just places an "#" comment character in front of those lines, in the appropriate files for each. If you took a screenshot of what is checked, before you make changes, you will know how to get back to how you were, before changing things..

---

### Post by TheFu on 2022-02-07
> **MAFoElffen said:**
> As a quick test... Without having to manually edit the files... You could just start the "Updates & Software" GUI > go to the Other Software Tab, then uncheck the checkboxes for those, then try an apt update and see if that makes a difference...

What that does in the background is just places an "#" comment character in front of those lines, in the appropriate files for each. If you took a screenshot of what is checked, before you make changes, you will know how to get back to how you were, before changing things..

What is they thing called "GUI" that you speak?  I can't imagine it could be as good as vim. That's an amazing GUI. ;)

If you run: 
$ inxi -r > ~/my-repos-desktop # on the desktop
$ inxi -r > ~/my-repos-laptop  # on the laptop
on both systems, then compare the files, differences should be clear.  Make the latop look like the desktop and see if things are still delayed.

---

### Post by georgesgiralt on 2022-02-07
Today is a busy day but I'll try this as soon as I get the chance ! Keep you posted.

---

### Post by MAFoElffen on 2022-02-07
> **TheFu said:**
> What is they thing called "GUI" that you speak?  I can't imagine it could be as good as vim. That's an amazing GUI. ;) 

The "Software & Updates" GUI application...

As good as VIM? LOL. Just "different". (Now I know you are joking and teasing me.) Please see for yourself in the screenshot in the attachment... 

(K.I.S.S.) Users can click a checkbox with their mouse... Presto. No magic. Not much skill needed. They can also find all their repo pointers in one place... To temporarily make them active or not, edit them or remove them... Sometimes it is simpler, than searching the individual files in the sourcesd directory to edit each file, to make a temporary change... Right? (Click, click, click, click... Done.)

---

### Post by schragge on 2022-02-07
^ I don't think that commenting out or removing URLs would help. It would help if **apt update** were stuck at downloading from one of the URLs. But the pause occurs before that. I'd rather look at the contents of **/etc/apt.conf.d/**. Perhaps, a script in **APT::Update::[noparse][/noparse]Pre-Invoke** in one of configuration snippets there takes too long?

---

### Post by georgesgiralt on 2022-02-07
Hello Guys!
So I take some time to test this. 
I've "ticked off" all additional repos  except the Ubuntu standard ones. 
Apt update command start at .... approx 9 seconds (if my memory serves me right, yesterday it was around 10~ 12 seconds delay) so not a huge difference and maybe not where the problem lies... 
As per the /etc/apt.conf.d, here is the content of the directory. 
```
# ls apt.conf.d/
00aptitude    01autoremove-kernels  15update-stamp	 20auto-upgrades  30autoproxy	       50unattended-upgrades   60icons-hidpi	90junior-config
00trustcdrom  01-vendor-ubuntu	    20apt-esm-hook.conf  20dbus		  50appstream	       51ubuntu-advantage-esm  70debconf	99synaptic
01autoremove  10periodic	    20archive		 20packagekit	  50command-not-found  60icons		       88libdvdcss-pkg	99update-notifier
#
```
Have a nice day.

---

### Post by schragge on 2022-02-07
Compared to what I have in there, I'd like to have a look at those I don't have
```
20auto-upgrades 30autoproxy 51ubuntu-advantage-esm 88libdvdcss-pkg 90junior-config
```
Perhaps,
```
grep APT::Update::Pre-Invoke /etc/apt/apt.conf.d/*
```
will catch something?

Besides, **squid-deb-proxy** which **30autoproxy** is related to should write logs to **/var/log/squid-deb-proxy/access.log** on the proxy server (which is probably *not* the host we're looking at that has **squid-deb-proxy-client** installed). I should say **30autoproxy** looks like the most probable culprit to me.

I don't have **junior-config** installed, but from what I know about Debian Blends is should be innocent. It probably just updates user menu in **DPkg::[noparse][/noparse]Post-Invoke**.

---

### Post by georgesgiralt on 2022-02-07
Hello here I am again.
```
# grep APT::Update::Pre-Invoke /etc/apt/apt.conf.d/*
#
```
And : 
```

# cat 20auto-upgrades
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
APT::Periodic::Unattended-Upgrade "0";
# cat 30autoproxy
Acquire::http::ProxyAutoDetect "/usr/share/squid-deb-proxy-client/apt-avahi-discover";
# cat 51ubuntu-advantage-esm
Unattended-Upgrade::Allowed-Origins {
  "${distro_id}ESM:${distro_codename}-security";
};
# cat 88libdvdcss-pkg 
DPkg::Post-Invoke { "[ -x /usr/lib/libdvd-pkg/b-i_libdvdcss.sh ] && /usr/lib/libdvd-pkg/b-i_libdvdcss.sh || true"; };
# cat 90junior-config
/*
 * APT configuration file for junior-config package
 */

DPkg {
	Post-Invoke {"test -f /var/run/junior-config.usermenu && if [ -x /usr/sbin/blend-update-usermenus ] ; then /usr/sbin/blend-update-usermenus junior ; fi ; rm -f /var/run/junior-config.usermenu";};
}
# ls /var/log/squid-deb-proxy/access.log
ls: impossible d'accéder à '/var/log/squid-deb-proxy/access.log': Aucun fichier ou dossier de ce type
#
```
Edit : You should know that this system has history. It has been installed eons ago and upgraded since with every LTS version availlable. IT also had suffered hardware "upgrades" as I switched laptops keeping the hard drive from the old to the new system.Taking benefit from LVM versatility, I've since switched from total mechanical HDD to M.2 Sata and after that, M.2 NVME mixed with harddisk and then M.2 NVME and SSD.... So the apt configuration (which I did not touch per se) comes from long time ago...

---

### Post by schragge on 2022-02-07
Rename **30autoproxy** to **30autoproxy~**, then try **apt update** again. APT ignores config files that end in **~**, **.bak**, **.disabled**, or **.dpkg-[a-z]+**.

---

### Post by georgesgiralt on 2022-02-07
> **schragge said:**
> Rename **30autoproxy** to **30autoproxy~**, then try **apt update** again. APT ignores config files that end in **~**, **.bak**, **.disabled**, or **.dpkg-[a-z]+**.

Bingo ! 
That did it ! 
I have still to figure why it suddenly slowed the "thing".... 
Thanks a big lot ! 
A thorn less in my foot.

---

### Post by schragge on 2022-02-07
Do you have a caching proxy server running in your local network? If not, **squid-deb-proxy-client** cannot possibly work.
```
sudo apt purge squid-deb-proxy-client
```
and remove that **30autoproxy~** completely.

Alternatively, you *do* have a proxy server, but your Avahi Daemon is broken/misconfigured.

---

### Post by TheFu on 2022-02-07
I *would never have figured out* the proxy thing. It is pretty unusual. BTW, I USE a proxy, apt-cacher-ng, for my APT configs across all systems, here. I don't know anyone else doing something similar in a home environment.

It was previously configured to use or seek out a system proxy settings?

BTW, **dircmp** can compare all the files from /etc/apt/ on both systems.  Just use **sshfs** to mount 1 system's files to the other box. While I've never done this, /etc/apt/ isn't really THAT system specific, so using **rsync** to mirror the settings from 1 to the other could have been attempted. Just make a backup (or simply move /etc/apt ... /etc/apt-old/) before moving the structure into place.  Then do an update/upgrade cycle.

---

### Post by schragge on 2022-02-07
[quote=TheFu]It was previously configured to use or seek out a system proxy settings?[/quote]
It was configured to listen on the network and to discover proxy services advertised via Avahi. I don't understand why it took 10&#8211;12 sec. Default timeout in the source is [two seconds]("https://bazaar.launchpad.net/~squid-deb-proxy-developers/squid-deb-proxy/trunk/view/head:/apt-avahi-discover"). Perhaps, **APT::Avahi-Discover::Timeout** was set to another value in **/etc/apt/apt.conf**. Or the code in Focal uses different timeout than the latest version on Launchpad.

---

### Post by georgesgiralt on 2022-02-07
So answer to various questions :
No I do not have any apt-cache server on my network. We had one at work a very long time ago but it would be very difficult for me to set up one now... Retirement has it's toll... 
I've removed squid-deb-proxy-client with  --purge, the 30autoproxy~ file and checked that the desktop machine had no 30autoproxy nor squid-deb-proxy-client ... This may explain why it was running fine ;-) 
I've to figure what and why this .deb was installed in the first place. 
Strange, strange....
Thank you all for your help ! I've to ask another question, though, TheFu, do you have something on configuring secure DNS ? 
Have a nice and bright day !

---

### Post by TheFu on 2022-02-07
> **georgesgiralt said:**
> So answer to various questions :
No I do not have any apt-cache server on my network. We had one at work a very long time ago but it would be very difficult for me to set up one now... Retirement has it's toll... 
I've removed squid-deb-proxy-client with  --purge, the 30autoproxy~ file and checked that the desktop machine had no 30autoproxy nor squid-deb-proxy-client ... This may explain why it was running fine ;-) 
I've to figure what and why this .deb was installed in the first place. 
Strange, strange....
Thank you all for your help ! I've to ask another question, though, TheFu, do you have something on configuring secure DNS ? 
Have a nice and bright day !

Since I setup DNS-over-HTTPS, I've since moved to using a raspberry pi for LAN DNS and DNS filtering. All DNS queries go through those 2 systems.  I have posted here how to setup a raspberry pi inside an LXD container, but it was less about steps 1 ... 10 and more about which guides I followed and how easy it was.  Let me search my local wiki for that post ...  [Https://ubuntuforums.org/showthread.php?t=2440863&p=13947454#post13947454](Https://ubuntuforums.org/showthread.php?t=2440863&p=13947454#post13947454) .  Just enough hints to follow along and do it, but it assumes based knowledge of lxd, networking, backing storage. My storage is extremely layered because lxd hates LVM and nearly demands that we use zfs.

My notes say that after I had the pi-hole running, setting it up as a LAN DNS took 4 minutes, so it was really fast for me to accomplish the 2nd part.  I need to move the pi-hole systems to 20.04.  They are fairly self contained and the migration should be really easy.  In theory. :)

---

