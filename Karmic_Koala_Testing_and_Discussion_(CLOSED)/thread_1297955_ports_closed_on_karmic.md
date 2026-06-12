---
title: "ports closed on karmic"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Aviendha09 on 2009-10-22
I dual-boot jaunty and karmic (beta). I also download stuff through Transmission. When I'm *in jaunty, everything is swell*, but when I boot in Karmic, transmission and canyouseeme.org tell me my ports are closed. Since firestarter crashes on me, I have tried to manually set ufw using ```
sudo ufw allow 62222
```
and checking with
```
anabel@anabel-desktop:~$ sudo ufw status numbered
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] 62222                      ALLOW IN    Anywhere


```

I have checked my router settings, yet my port(s) remain closed. Why? Is this a temporary security feature?

---

### Post by ikt on 2009-10-22
if you fully disable the firewall does it work? may be different issue.

---

### Post by ethoxyethaan on 2009-10-22
when you refer to "I have checked my router settings, yet my port(s) remain closed. Why? Is this a temporary security feature? "

what exactly do you mean with "i checked my router settings" normally if you CLOSE a port on your LOCAL device and start a program that listens on that device, the program crashes or halts because it can't bind the port.

if it can bind the port locally then perhaps you are doing something else wrong,

Please elaborate on what you want to do.

---

### Post by Aviendha09 on 2009-10-22
No change on disabling ufw. will re-enable.

My router settings are the same in both releases, ie. allow traffic for transmission on port 62222 (tcp, Transmission does not require/specify using udp.) My internet works...  canyouseeme.org reports closed on 62222 (and for tests sake 80, too), transmission sees 62222 as closed. Hmmmmm

---

### Post by OpenGuard on 2009-10-22
```
sudo iptables -L

```

What's the output ?

---

### Post by lovinglinux on 2009-10-22
Have you configured the Karmic installation to use a static IP? If it is using DHCP it could be getting a different IP from the router and thus the forwarded connections could be going to the wrong address.

Also try these commands:

```
sudo iptables -F
sudo iptables -X
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
```

This will clear the firewall (iptables) rules and set it to accept all connections.

If that works, than it's probably Firestarter messing up your iptables.

---

### Post by Aviendha09 on 2009-10-22
```
anabel@anabel-desktop:~$ sudo iptables -L
[sudo] password for anabel: 
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  mymodem              anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  mymodem              anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.2.255       
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anabel-desktop       mymodem             tcp dpt:domain 
ACCEPT     udp  --  anabel-desktop       mymodem             udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:52222:52226 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:52222:52226 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (8 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (2 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootps 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootpc 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state NEW 
ACCEPT     udp  --  anywhere             anywhere            state NEW 

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:62222 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:62222 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:62223 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:62223 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:62224 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:62224 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:62225 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:62225 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:62226 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:62226 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:62227 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:62227 

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination         
anabel@anabel-desktop:~$ 
[HTML][/HTML]
```

---

### Post by OpenGuard on 2009-10-22
Seems like it's have been messed up by Firestarter. Turn it off, [reset iptables]("http://pikt.org/pikt/samples/reset_iptables.html"), set ufw rules ( default deny, allow <port> ) and restart your PC.

---

### Post by Aviendha09 on 2009-10-22
I really don't know enough to start messing with static ip/dhcp. I was recommended dhcp and linux always picks that option though I have a dsl connection with a Gateway router connected to my eth0 port. My ISP doesn't grant me a fixed ip. 

I would rather not leave my computer wide open, as important viruses (or whatever intrusions) are sure to come along someday. I will try the iptables commands soon, after lunch?

---

### Post by mcduck on 2009-10-22
> **Aviendha09 said:**
> I really don't know enough to start messing with static ip/dhcp. I was recommended dhcp and linux always picks that option though I have a dsl connection with a Gateway router connected to my eth0 port. My ISP doesn't grant me a fixed ip. 

I would rather not leave my computer wide open, as important viruses (or whatever intrusions) are sure to come along someday. I will try the iptables commands soon, after lunch?

Most routers will allow you to configure static IP for your machines in the router itself, which means that you can leave the settings on the computer to DHCP.

Also, you really don't need a firewall in Ubuntu unless you are running some server software that you want to restrict while the server itself doesn't have suitable configuration for limiting connections. And you *definitely* don't need to worry about any viruses, somebody will have to actually figure out a way to make a working Linux virus before you need to start worrying about them.. ;)

The default Ubuntu install isn't restricting any network traffic and there's a good reason for that: it doesn't have to. With no services running that would respond to incoming connections a firewall is pointless.

---

### Post by Aviendha09 on 2009-10-22
Damn this itch, forget dinner.... I tried the whole iptables reset thing (the commands, not the bash script, I'm not there yet)  and the ports are open and what a difference! Thank you! 

Should I report the Firestarter incident as a bug? (I may already have, mind you)

Now, are there any loose ends that need tying so I'm not out there parading naked ?

---

### Post by OpenGuard on 2009-10-22
> **Aviendha09 said:**
> Damn this itch, forget dinner.... I tried the whole iptables reset thing (the commands, not the bash script, I'm not there yet)  and the ports are open and what a difference! Thank you! 

Should I report the Firestarter incident as a bug? (I may already have, mind you)

Now, are there any loose ends that need tying so I'm not out there parading naked ?

```
sudo ufw default deny
```This will ensure that all ports are closed, except the custom ones you define by hand.

---

### Post by lovinglinux on 2009-10-22
> **Aviendha09 said:**
> I really don't know enough to start messing with static ip/dhcp. I was recommended dhcp and linux always picks that option though I have a dsl connection with a Gateway router connected to my eth0 port. My ISP doesn't grant me a fixed ip. 

Is not the external IP I'm talking about, is the internal IP of your machine. When you connect to your router using DHCP, it assigns you an internal IP, which is something like 192.168.1.x or 192.168.2.x. If your computer is the only one in your local network, then you always get the first available IP, but if you have more than one computer, then the IP assigned to your machine will varies according to the order of connection. So you might get 192.168.1.y instead of 192.168.1.x if there is already another computer connected to your router. The problem is that when you forward the port used by the torrent client, you need to specify the internal IP of the machine running the torrent client, otherwise the incoming connections will take the wrong route and die.

> **Aviendha09 said:**
> I would rather not leave my computer wide open, as important viruses (or whatever intrusions) are sure to come along someday. I will try the iptables commands soon, after lunch?

The suggestions are not supposed to be used forever, just to troubleshoot the problem. Besides, a firewall won't protect you as you might think. If you are not running any applications that listen to ports (like a Bittorrent client), then all ports will be virtually closed and all incoming connections will be rejected anyway, so a firewall won't help. Additionally, if you don't forward the port from the router to your machine, you don't really need a firewall, because the router is already blocking unwanted connections.

Using a firewall to protect your machine while you use Bittorrent also won't protect you, since you need to open the port for the torrent connections and the torrent client will be listening to unrequested incoming connections. Other ports that are not being listen by a server (ssh, samba, vnc, bittorrent and others) are already closed.

So, unless you need to block access to certain IP addresses while allowing others, the firewall won't help you.

I recommend that you read the security section of the [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

---

### Post by Aviendha09 on 2009-10-22
Thank you, that was the quickest debugging yet! :guitar:

---

### Post by Aviendha09 on 2009-10-24
OOPs! Solved too soon!
Shut down last nite and restarted computer today....problem is back! I repeated all the iptables commands and it was solved again...but how do I keep it this way? Will I have to use that script ? (what...do I just chmod it?) 
I wont be here long today...I will be more available on monday...thx for the help...

---

### Post by OpenGuard on 2009-10-24
Have you enabled ufw ?

```
sudo ufw enable

```

---

### Post by Aviendha09 on 2009-10-24
Yes I have. I got it working all right, I just wonder how come I had to reset the iptables all over again....I just removed Firestarter since the trouble started after it crashed while configuring it. There is a bug filed at lauchpad.

---

### Post by OpenGuard on 2009-10-24
Wait. Are you telling me that even after removing Firestarter, *someone* is configuring iptables ?

```
dpkg -l | fire
```

Can you show us the output ?

---

### Post by lovinglinux on 2009-10-24
I think you need to purge Firestarter instead of removing it.

```
sudo apt-get purge firestarter
```

---

### Post by Aviendha09 on 2009-10-24
yep! I just rebooted, did sudo iptables -L, and got a whole lot data, *quoted above*. Canyouseeme.org shows me blocked all over, even 80 (how come my i-net works?)

this is the output of your request:
```
anabel@anabel-desktop:~$ dpkg -l | fire
No command 'fire' found, did you mean:
 Command 'lire' from package 'lire' (universe)
 Command 'file' from package 'file' (main)
 Command 'fyre' from package 'fyre' (universe)
fire: command not found

```  good luck! (I must be going, one of (one of) my daughters birthday parties)


edit: test: Whoa! transmission says port open, and canyouseeme too (I changed port, the other remains closed, but I had a few covered in ufw. Even with that very long iptables -L output...time will tell, now I gotta GO!

---

### Post by OpenGuard on 2009-10-24
> **Aviendha09 said:**
> yep! I just rebooted, did sudo iptables -L, and got a whole lot data, *quoted above*. Canyouseeme.org shows me blocked all over, even 80 (how come my i-net works?)

this is the output of your request:
```
anabel@anabel-desktop:~$ dpkg -l | fire
No command 'fire' found, did you mean:
 Command 'lire' from package 'lire' (universe)
 Command 'file' from package 'file' (main)
 Command 'fyre' from package 'fyre' (universe)
fire: command not found

```  good luck! (I must be going, one of (one of) my daughters birthday parties)


edit: test: Whoa! transmission says port open, and canyouseeme too (I changed port, the other remains closed, but I had a few covered in ufw. Even with that very long iptables -L output...time will tell, now I gotta GO!

Gee! Sorry, misspelled #-o

```
dpkg -l | grep fire
```

---

### Post by Longinus00 on 2009-10-24
> **Aviendha09 said:**
> I really don't know enough to start messing with static ip/dhcp. I was recommended dhcp and linux always picks that option though I have a dsl connection with a Gateway router connected to my eth0 port. My ISP doesn't grant me a fixed ip. 

Before enabling static IP on your computer, check to see if your router supports assigning forwarding via mac addresses/hostname instad. My motorola cable modem/router supports this so there is no longer any worry about getting assigned a different IP address. An alternative is to see if you can get your router to reserve a dhcp IP for a specific computer and so simulates setting up a static IP on your computer.

---

### Post by Aviendha09 on 2009-10-25
Hi again! Only a few minutes free: the ports are open (when requested, eg transmission started) I guess the problem is finally solved: here is the output of the command
```
anabel@anabel-desktop:~$ dpkg -l | grep fire
ii  firefox                               3.5.3+build1+nobinonly-0ubuntu6            meta package for the popular mozilla web bro
ii  firefox-3.5                           3.5.3+build1+nobinonly-0ubuntu6            safe and easy web browser from Mozilla
ii  firefox-3.5-branding                  3.5.3+build1+nobinonly-0ubuntu6            Package that ships the firefox branding
ii  firefox-3.5-gnome-support             3.5.3+build1+nobinonly-0ubuntu6            Support for Gnome in Mozilla Firefox
ii  firefox-gnome-support                 3.5.3+build1+nobinonly-0ubuntu6            meta package pointing to the latest gnome-su
rc  firestarter                           1.0.3-7ubuntu5                             gtk program for managing and observing your 
ii  ufw                                   0.29-4ubuntu1                              program for managing a Netfilter firewall

``` as requested. Firestarter still around?

Also here is that really *way too long* iptables output :

```
anabel@anabel-desktop:~$ sudo iptables -L
[sudo] password for anabel: 
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootps 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootpc 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state NEW 
ACCEPT     udp  --  anywhere             anywhere            state NEW 

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:62222 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:62222 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:62223 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:62223 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:62224 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:62224 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:62225 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:62225 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:62226 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:62226 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:62227 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:62227 

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination         
anabel@anabel-desktop:~$ 

```

Any suggestions? it's was much much shorter when I executed the iptables "reset" commands (see above), but the result doesn't "stick". Is this problem solved?

---

### Post by OpenGuard on 2009-10-25
Get rid of services, config files and whatnot ..

```
find /etc -name firestarter -exec rm -rf {} \;
```

---

