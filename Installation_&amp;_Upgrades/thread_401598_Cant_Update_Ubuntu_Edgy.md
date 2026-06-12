---
title: "Cant Update Ubuntu Edgy"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by super.rad on 2007-04-04
I've had a few problems sorting out the wireless but finally managed to sort it out the other day, but i have a new problem. Firefox can connect fine (im writing this from it) but when i try to update using synaptic, terminal or add new programs i go to refresh the repositories and it doesnt download the list, i get this error

```
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
```

and then this 

```
An error occured

The following details are provided:

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
```

If i go into software sources the universe, main, multiverse and restricted are ticked, source code isnt ticked and it is set to download from Server For UK and also the cd/dvd isn't ticked.
Can anyone help? Thanks

---

### Post by mssever on 2007-04-05
That looks like the sort of error you get when you try to run multiple package managers at once. Make sure only one is running.

---

### Post by super.rad on 2007-04-05
Ye when those errors came up i had two open, wasnt thinking last night. I still get problems when only one is open though, i tried updating through the terminal this morning and get this
```
em@em-ubuntu:~$ sudo apt-get update
Password:
Err http://gb.archive.ubuntu.com edgy Release.gpg                              
  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://security.ubuntu.com edgy-security Release.gpg                       
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
```

anyone know how to solve this?

---

### Post by ndefontenay on 2007-04-05
I got this kind of problem when I was behind a proxy.

If you are, try this:

```
export http_proxy= http://youripaddress:yourport
```

It worked for me behind a proxy.

---

### Post by super.rad on 2007-04-05
Im not behind a proxy but thanks anyway

---

### Post by zvacet on 2007-04-05
Try to get updates from main server.

---

### Post by super.rad on 2007-04-05
i just tried downloading easyubuntu, it wouldnt work from the terminal but if i pasted the address in firefox it downloaded fine. I then selected a few things for easyubuntu to install and got another error, i have included a screenshot

---

### Post by super.rad on 2007-04-05
> **zvacet said:**
> Try to get updates from main server.

tried that and made no difference. i've also tried loading a few different edgy source lists i found but nothing worked

---

### Post by super.rad on 2007-04-05
thought i'd post some more information incase it helped anyone solve this for me.
this is my /etc/apt/sources.list
```
deb http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb http://packages.freecontrib.org/ubuntu/plf/ edgy free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine
# Ubuntu supported packages
# GPG key: 437D05B5
deb http://gb.archive.ubuntu.com/ubuntu edgy main restricted
deb http://security.ubuntu.com/ubuntu edgy-security main restricted
# Ubuntu community supported packages
deb http://gb.archive.ubuntu.com/ubuntu edgy universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse
# Upstream Opera
deb http://deb.opera.com/opera etch non-free
# Upstream Beryl
# GPG key: ed8a569e
deb http://ubuntu.beryl-project.org/ edgy main-edgy
# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb http://medibuntu.sos-sts.com/repo/ edgy free non-free
#Easyubuntu
deb http://easyubuntu.cafuego.net main easyubuntu

```

what i get when i try sudo apt-get update
```
em@em-ubuntu:~$ sudo apt-get update
Password:
Err http://security.ubuntu.com edgy-security Release.gpg                       
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://packages.freecontrib.org edgy Release.gpg                           
  Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection timed out
Err http://medibuntu.sos-sts.com edgy Release.gpg                              
  Could not connect to medibuntu.sos-sts.com:80 (1.0.0.0), connection timed out
Err http://archive.ubuntu.com edgy Release.gpg                                 
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ubuntu.beryl-project.org edgy Release.gpg                           
  Could not connect to ubuntu.beryl-project.org:80 (1.0.0.0), connection timed out
Err http://deb.opera.com etch Release.gpg                                      
  Could not connect to deb.opera.com:80 (1.0.0.0), connection timed out
Err http://easyubuntu.cafuego.net main Release.gpg                             
  Could not connect to easyubuntu.cafuego.net:80 (1.0.0.0), connection timed out
Err http://security.ubuntu.com edgy-security/main Translation-en_US            
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://packages.freecontrib.org edgy/free Translation-en_US                
  Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection timed out
Err http://medibuntu.sos-sts.com edgy/free Translation-en_US                   
  Could not connect to medibuntu.sos-sts.com:80 (1.0.0.0), connection timed out
Err http://archive.ubuntu.com edgy/main Translation-en_US                      
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ubuntu.beryl-project.org edgy/main-edgy Translation-en_US           
  Could not connect to ubuntu.beryl-project.org:80 (1.0.0.0), connection timed out
Err http://deb.opera.com etch/non-free Translation-en_US                       
  Could not connect to deb.opera.com:80 (1.0.0.0), connection timed out
Err http://easyubuntu.cafuego.net main/easyubuntu Translation-en_US            
  Could not connect to easyubuntu.cafuego.net:80 (1.0.0.0), connection timed out
Err http://security.ubuntu.com edgy-security/restricted Translation-en_US      
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://packages.freecontrib.org edgy/non-free Translation-en_US            
  Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection timed out
Err http://medibuntu.sos-sts.com edgy/non-free Translation-en_US               
  Could not connect to medibuntu.sos-sts.com:80 (1.0.0.0), connection timed out
Err http://archive.ubuntu.com edgy/restricted Translation-en_US                
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]

```

```
em@em-ubuntu:~$ iwconfig

wlan0     IEEE 802.11-DS  ESSID:"G604T_WIRELESS"  Nickname:"okuwlan"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:95:96:47:56   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality=0/0  Signal level=57/255  Noise level=0/0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

em@em-ubuntu:~$ 

```

and finally
```
em@em-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D3:4D:04:EE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:225 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:188 (188.0 b)  TX bytes:188 (188.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:09:5B:30:5A:D7  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fe30:5ad7/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:4397 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4497 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3968855 (3.7 MiB)  TX bytes:532596 (520.1 KiB)

em@em-ubuntu:~$ 

```

if anyone has any ideas please help

---

### Post by Kochin on 2007-04-05
Just today I found out that my Ubuntu (Dapper) installation experiences the same problem when trying to update. All update attempts returned with connection failed messages. 

After searched this forum, the only potential solution I can find is changing the connection protocol from http to ftp in /etc/apt/sources.list. So I modified /etc/apt/sources.list by replacing all http: with ftp:, and now the update works beautifully. 

My Ubuntu machine's network interface and connection are working, and other programs have no problem to connect using http. I wonder whether there is a bug in the http connection code of apt-get and related programs.

---

### Post by super.rad on 2007-04-05
just tried doing that and getting the same problem. no idea whats gone wrong here, tried everything and checked everything. starting to give up now

---

### Post by garybrlow on 2007-04-05
There is no bug in the connection code its working fine on all distro versions. Try checking your router settings, it might be blocking it. Your ifconfig setting do not show a real ip(i.e. 192.168.X.X vs. 208.X.X.X) address only local ones that is possibly leased from a router. If your on a wifi connection to your ISP, possibilities are that they are being blocked by default and you are being routed through their system. You have to set up necessary port forwarding settings to gain direct connection to the Repository Servers.

If you don't have a wifi connection to your ISP just a regular DSL connection etc. and just use a wifi router locally, check if your ports are forwarded properly.

Please give more information about your network connection by the way. :)

Cheers!!!


GaryBrlow :biggrin:

---

### Post by mssever on 2007-04-05
Accordint to the error messages you posted, apt is trying to use the invalid IP address 1.0.0.0. This is often the result a problem using IPv6 (some routers choke on IPv6--maybe some upstream gateways do, too). See [this thread]("http://ubuntuforums.org/showthread.php?t=250149") for more, and also check out [OpenDNS]("http://openDNS.com").

I think that switching to OpenDNS will probably solve your problems.

EDIT: The easiest thing might be to enter OpenDNS's IP numbers into the proper place on your router's control panel (so your router will give out OpenDNS's IPs), then edit /etc/resolv.conf to match. If this doesn't work, try the other suggestions in the thread I linked to.

---

### Post by super.rad on 2007-04-05
thanks for the replies, unfortunatly i cant change anything in my router's settings as everytime i change anything the router loses all of my isp information, i've tried forwading ports before and everytime my router had to be reset and all the info put in again

---

### Post by super.rad on 2007-04-05
also my ifconfig does show my ip address, its a static address 192.168.1.5

---

### Post by mssever on 2007-04-05
In that case, you should be able to edit /etc/dhcp3/dhclient.conf and uncomment the line that begins prepend domain-name-servers. Replace 127.0.0.1 with OpenDNS's numbers (208.67.222.222,208.67.220.220). Then save, exit, and restart your networking ```
sudo /etc/init.d/networking restart
``` If that doesn't do the trick, reboot.

---

### Post by garybrlow on 2007-04-05
A 192.168.X.X(192.168.1.5) IP address is a locally assigned one usually for internal networking commonly known as a private IP. This indicates going through router/ proxy server. I was looking for a ppp0 setting with a live IP address assigned buy the ISP to your modem to indicate direct connection.

Your router should save all the settings. After changing router settings you should reboot the router not reset it. Rebooting the router restarts the router but preserves the settings. Resetting it erases all settings and sets the router to default manufacturer settings (refer to the router manual for more details - note some router manufacturer manuals are not very clear on procedure at times). :p


Cheers!!!


GaryBrlow :biggrin:

---

### Post by mssever on 2007-04-05
> **garybrlow said:**
> A 192.168.X.X(192.168.1.5) IP address is a locally assigned one usually for internal networking commonly known as a private IP. This indicates going through router/ proxy server. I was looking for a ppp0 setting with a live IP address assigned buy the ISP to your modem to indicate direct connection.

Your router should save all the settings. After changing router settings you should reboot the router not reset it. Rebooting the router restarts the router but preserves the settings. Resetting it erases all settings and sets the router to default manufacturer settings (refer to the router manual for more details - note some router manufacturer manuals are not very clear on procedure at times). :p


Cheers!!!


GaryBrlow :biggrin:I'm quite confident that the problem is in the interaction between the router and DNS (witness the IP 1.0.0.0 that apt was trying to use). Some routers include a DNS forwarder that is a bit buggy in its handling of IPv6 addresses and confuses Ubuntu. So the solution is to either disable IPv6 altogether, or simply bypass the router's DNS--hence, OpenDNS.

By the way, the OpenDNS website has fairly comprehensive instructions for switching to their service. They even include Ubuntu-specific amd router-specific directions.

---

### Post by Kochin on 2007-04-05
> **garybrlow said:**
> There is no bug in the connection code its working fine on all distro versions.
Yes, you are right. There is no bug in the code, and I realized my case is different to super.rad's after carefully reviewed his log.

Sorry for intrusion onto this thread. ](*,) 

P.S. Just for the record, I found out that apt-get sends out HTTP request in the form of 
```
GET http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg HTTP/1.1
HOST: us.archive.ubuntu.com
```
While it complies to standard, unfortunately us.archive.ubuntu.com server doesn't like it. Using "GET /ubuntu/dists/dapper-updates/Release.gpg HTTP/1.1" works with that server.

---

### Post by super.rad on 2007-04-05
> **mssever said:**
> In that case, you should be able to edit /etc/dhcp3/dhclient.conf and uncomment the line that begins prepend domain-name-servers. Replace 127.0.0.1 with OpenDNS's numbers (208.67.222.222,208.67.220.220). Then save, exit, and restart your networking ```
sudo /etc/init.d/networking restart
``` If that doesn't do the trick, reboot.

worked perfectly, thanks a lot for the help

---

