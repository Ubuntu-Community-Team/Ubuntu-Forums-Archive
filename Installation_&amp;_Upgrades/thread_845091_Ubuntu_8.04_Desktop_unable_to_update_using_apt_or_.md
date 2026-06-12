---
title: "Ubuntu 8.04 Desktop unable to update using apt or synaptic."
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by oceallaighm on 2008-06-30
Hi,

Over the past 2 days I have been unable to update using either apt or synaptic. This first happened when I tried to do an update in Synaptic following receipt of notification that an update was available.

Let me be totally clear about my set-up so as not to cause confusion. I am running Ubuntu 8.04 as a guest OS in VirtualBox 1.6.2 on Windows Vista host. Networking is working via the default nat setup that VirtualBox provides and I have Internet access both with Firefox and Evolution. The system has been up and running following a clean install 3 weeks ago and I have have had several updates since then.

The error message is as follows ( I will then explain what I have down so far to track down the problem):

Err [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_IE
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_IE
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_IE
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_IE
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_IE
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_IE
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_IE
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_IE
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_IE
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_IE
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_IE
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_IE
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_IE
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_IE.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_IE.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_IE.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_IE.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_IE.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_IE.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_IE.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_IE.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_IE.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_IE.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_IE.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_IE.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_IE.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_IE.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_IE.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_IE.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_IE.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_IE.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_IE.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_IE.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_IE.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_IE.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_IE.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_IE.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_IE.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_IE.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

I have done the following having looked at some older threads yesterday.

apt-get update
apt-get clean
apt-get autoclean
apt-get check

None of the above make any difference to the problem. 

In Synaptic, Settings, Repositories, Download from, I have both changed to the Main Server and Select Best Server, the latter has returned the following 'No suitable download server was found Please check your Internet connection.' Note I am on the Internet at the moment as I write this.

System, Administration, Network,Hosts Tab, as per earlier thread I have checked 127.0.0.1 is local host and 127.0.1.1  is followed by MyComputerName, note nothing extra after it.

ifconfig -a gives the following:-

eth0      Link encap:Ethernet  HWaddr 08:00:27:4d:ac:d9  
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe4d:acd9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38605 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35795 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33240738 (31.7 MB)  TX bytes:4649434 (4.4 MB)
          Interrupt:11 Base address:0xc020 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:530 errors:0 dropped:0 overruns:0 frame:0
          TX packets:530 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22260 (21.7 KB)  TX bytes:22260 (21.7 KB)

This looks ok to me.

Does anyone have any suggestions?

---

### Post by upchucky on 2008-06-30
If this is your system,

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host

then it looks like it is trying to connect to itself instead of the remote repositories,

Err [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused) 

check your sources list for proper address entries if they are ok then
perhaps you have wireshark installed or etherape? if so trace the packets.


Oops, just saw the Vista host u mentioned, amazing how the mind can block out things it does not like.

Vista security setting is prolly the problem.

---

### Post by Pumalite on 2008-06-30
Are you able to navigate the Internet?

---

### Post by oceallaighm on 2008-06-30
> **Pumalite said:**
> Are you able to navigate the Internet?

As per post I have Internet access both with Firefox and Evolution, I can browse the Internet and send and receive e-mails and am on the Internet as I type this.

---

### Post by oceallaighm on 2008-06-30
> **upchucky said:**
> If this is your system,

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host

then it looks like it is trying to connect to itself instead of the remote repositories,

Err [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused) 

check your sources list for proper address entries if they are ok then
perhaps you have wireshark installed or etherape? if so trace the packets.

Vista security setting is prolly the problem.

I don't have either wireshark or etherape, I will look and see if there are some .deb files that I can download with Firefox and install manually. 

I don't believe that the problem is security on the Vista host as everything has been working out of the box for over 3 weeks and no changes have been made on the host platform which does nothing more that run VirtualBox with Ubuntu 8.04 or XPSP3 as guests.

I will try the above and see if I can figure something out.

---

### Post by upchucky on 2008-06-30
Hope it works, remember that windows has a habit of doing stuff to your system without asking you or even telling you about it.

---

### Post by oceallaighm on 2008-07-02
> **upchucky said:**
> Hope it works, remember that windows has a habit of doing stuff to your system without asking you or even telling you about it.

The problem was me, partially resolved as follows.

Strange discovery, 

I rechecked the contents of my hosts file, it is as follows:- 

127.0.0.1 localhost 
127.0.1.1 UbuntuLaptop 

# The following lines are desirable for IPv6 capable hosts 
::1 ip6-localhost ip6-loopback 
fe00::0 ip6-localnet 
ff00::0 ip6-mcastprefix 
ff02::1 ip6-allnodes 
ff02::2 ip6-allrouters 
ff02::3 ip6-allhosts 

The hosts file looked ok to me, they appear to be the initial settings that I got having installed Ubuntu 8.04 Desktop into the VM. 

Why aren't Firefox and Evolution also being redirected to port on the local host? 

Just tried the following:- 
wget [http://files.zimbra.com/downloads/5.0.6_GA/zcs-5.0.6_GA_2313.UBUNTU6.20080522130240.tgz](http://files.zimbra.com/downloads/5.0.6_GA/zcs-5.0.6_GA_2313.UBUNTU6.20080522130240.tgz) 
Error parsing proxy URL [http://localhost:4001](http://localhost:4001) : Bad port number. 

This error reminded me that I am using Foxyproxy in Firefox set to use proxy default for all urls. Obviously Foxyproxy depends on other software to run and this is setup outside of the browser environment. I know that when I used Tor in the past in Windows XP, I had to manually configure the applications to use it. It would appear that in Linux the proxy is configured differently and perhaps less transparent. 

So I had both Tor and Privoxy running, but technically I was not using them with the exception of Foxyproxy in the browser. Firefox and Evolution continued to work without being configured to use them. 

Privoxy was most likely installed when I installed Tor, but I had paid no attention to it. In Synaptic I went to the Network tab and entered the manual proxy settings for Privoxy. Et voila, Synaptic worked again. I have still not found out what application is redirecting to localhost:4001 as Privoxy uses port 8118 and Tor uses 9050 for socks. I still have to find out also where to change the equilavent settings for apt, but I will get there. 

Since I am now able to download files I have installed Wireshark and I will try to use that to see what is really running on port 4001.

---

### Post by oceallaighm on 2008-07-02
I have run Wireshark on lo: I got the following result.

Transmission Control Protocol, Src Port: newoak (4001), Dst Port: 59500 (59500), Seq: 1, Ack: 1, Len: 0

A search of Google with all of the above gives nothing.

A search of Google using only newoak TCP 4001 gives a lot of links, It would appear that from the sites I have browsed that this process is normal for this port. Though I can find no indication as to what application is using it.

My only other thught is the firewall Firestarter, though so far I have not managed to get it to run automatically on startup, so unless I deliberately choose to start it and enter the administrater password it is not running. And I don't see this as a process in System Monitor.

---

