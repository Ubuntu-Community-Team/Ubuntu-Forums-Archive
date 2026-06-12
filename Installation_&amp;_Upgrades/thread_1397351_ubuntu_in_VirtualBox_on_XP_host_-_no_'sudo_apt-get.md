---
title: "ubuntu in VirtualBox on XP host - no 'sudo apt-get update'"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by elionescu on 2010-02-03
Hello Word!

On a Xp host I installed last version of VirtualBox and I created a 9.10 Ubuntu 'guest'.
While I can surf the net, I cant 'sudo apt-get update' nor do a 'reload' from 'Synaptic Package Manager'.

I would appreciate any hint, suggestion, ideea!

Regards
E.Ionescu

PS Here are some facts:
<<
Host: 
  PC: 
  Thinkcenter 9640-7BG
  Network adapters:
    - BroadCom NetLink
    - VirtualBox Host-Only Ethenet Adapter
  The pc is part of a company network that uses a proxy !
  OS: VP Prof, SP 3 up to date will all 'High-priority updates'
  TrendMicro OfficeScan Client 10
  VirtualBox-3.1.2-56127 
  Guest: Ubuntu 9.10
  Network config for the Ubuntu guest: tried NAT and Bridged adapter (PCnet-Fast III)
  - With each of them I can surf the Internet or 'ping' ONLY after setting the proxy
  - With none of them I cant 'sudo apt-get update' nor do a 'reload' from 'Synaptic Package Manager'
  
$ ping archive.ubuntu.com
PING archive.ubuntu.com (91.189.88.30) 56(84) bytes of data.
64 bytes from jackass.canonical.com (91.189.88.30): icmp_seq=1 ttl=57 time=53.2 ms
..
$ ping 91.189.88.45
PING 91.189.88.45 (91.189.88.45) 56(84) bytes of data.
64 bytes from 91.189.88.45: icmp_seq=1 ttl=57 time=58.0 ms
..
$ sudo apt-get update
[sudo] password for ...: 
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg    
  Could not connect to archive.ubuntu.com:80 (91.189.88.45), connection timed out [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_US
  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US
>>

---

### Post by gmargo on 2010-02-04
If you can surf the net then the problem isn't with apt-get. Change your archive host to a mirror. See:
[http://www.ubuntu.com/getubuntu/downloadmirrors#mirrors](http://www.ubuntu.com/getubuntu/downloadmirrors#mirrors)

---

### Post by doas777 on 2010-02-04
reboot and try again in a few minutes. usually what i find when i get that error, is that it is a fleeting thing, and gone 20 min later, or that i have a bad repo in my sources.lst

---

### Post by steveneddy on 2010-02-04
If you mounted the Live CD image instead installing you would get the same error.

---

### Post by elionescu on 2010-03-17
Thank you all for your advices!

Unfortunately .. I didn't get a working 'synaptic package manager':

[using 'Synaptic Package Manager']
From menu: Seting / Repositories 
In the combo 'Download from:' I select 'Other...' and click "Select Best Server"
After 'compliting' 325 tests I've got the message:
"No suitable download server was found / Please check your Internet connection."

But I don't know what to change. 
[installation was not done from a live cd but from an .iso]

Regards,
Emanuel

---

### Post by gmargo on 2010-03-17
> **elionescu said:**
> 
On a Xp host I installed last version of VirtualBox and I created a 9.10 Ubuntu 'guest'.
While I can surf the net, I cant 'sudo apt-get update' nor do a 'reload' from 'Synaptic Package Manager'.

  **The pc is part of a company network that uses a proxy !**
**... I can surf the Internet or 'ping' ONLY after setting the proxy**


How are you setting the company mandated proxy in the Ubuntu guest?

Update: If you set the network proxy through the Gnome menu: System -> Preferences -> Network Proxy, then Synaptic will use that proxy setting.  I tested this under 9.10 Karmic by blocking outbound port 80 with the ufw firewall, with squid on another machine acting as the proxy.

---

### Post by elionescu on 2010-03-18
Hello gmargo!

I choose 'Automatic Proxy configuration', with the 'usual' 
[http://proxy/proxy.pac](http://proxy/proxy.pac)
This configuration works well when it comes to internet browsing (I am editing this post from the very virtual machine) and even 'ping' to all tcpip addresses displayed when I issue 'sudo apt-get update'.
So I think there should be a 'secret' port that needs to be opened for this more special request that 'ordinary' ping or http(s)

Regards,
Emanuel

---

### Post by gmargo on 2010-03-18
> **elionescu said:**
> I choose 'Automatic Proxy configuration', with the 'usual' 
[http://proxy/proxy.pac](http://proxy/proxy.pac)

Can you post that file?

---

### Post by elionescu on 2010-03-22
-- this is proxu.pac; companyName is not the real one - sorry for this secrecy...


function FindProxyForURL(url, host)
{
// variable strings to return
var proxy_yes = "PROXY proxy.companyName.ro:8080";
var proxy_no = "DIRECT";

// Bypassed direct to proxy
// [http://www.squid-cache.org/mail-archive/squid-users/200703/0210.html](http://www.squid-cache.org/mail-archive/squid-users/200703/0210.html)
if (!isResolvable(host))
{ return proxy_yes; }

//PlainHostName
if (isPlainHostName(host))
{ return proxy_no; }

//https
if (url.substring(0, 6) == "https:")
{ return proxy_no; }

//Company Intranet networks
if (isInNet(host, "127.0.0.1", "255.255.255.255") ||
isInNet(host, "192.168.0.0", "255.255.0.0") ||
isInNet(host, "172.16.0.0", "255.192.0.0") ||
isInNet(host, "10.0.0.0", "255.0.0.0")
) { return proxy_no; }

//Exchange server access
if (isInNet(host, "216.166.12.0", "255.255.255.0")
) { return proxy_no; }

//Send to proxy for others
return proxy_yes;
}

---

### Post by gmargo on 2010-03-22
Ok, good information, thanks.

Here's how to get apt-get (or aptitude) on the command line working. Add this line to **/etc/apt/apt.conf** (create the file if it does not exist):
```

Acquire::http::Proxy    "http://proxy.companyName.ro:8080/";

```Here's how to get Synaptic to work.  Open Synaptic (System -> Administration -> Synaptic Package Manager) and navigate its menu (Settings -> Preferences -> Network) and click Manual proxy configuration and enter the HTTP proxy address proxy.companyName.ro and port 8080.

---

### Post by elionescu on 2010-03-30
Hello gmargo,

Your answer was perfect: it was short and completely fixed the problem!
Thank you very much!

Regards,
Emanuel

---

