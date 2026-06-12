---
title: "VPN, Windows Network and Printer"
date: 2004-12-14
forum: Installation &amp; Upgrades
---

### Post by gdeswardt on 2004-12-14
Ok after digging around in the forum I found the solutions for my sound and mount problem. Both of these are fixed now, and still I am yet to do a manually compile. This is fantastic, the best distro I have installed so far. The more i use ubuntu the more i like it. Even setting up my wireless network was no problem what so ever.

I do still have the following questions:


[list=1]
[*]Currently on my windows machine we are using Checkpoint SecureClient to connect to our VPN. What programs are available in Ubuntu to allow me to connect to our VPN?
[*]We are running DHCP on our local network here, and everybody in the office (except me offcourse) is running Windows. Some of my daily requirements is to access our intranet website that is running on a Windows 2003 server with IIS. Due to the DHCP the servers IPAddress changes. When using windows I was able to browse the website by using "http://servername". I can not access it by using the same url but if i use the IP Address it does the same trick. Is there away in Ubuntu to access these resources by the Windows Networking sharing name instead of their IP Addresses?
[*]Our priners in the office is running on and IP port, but just like all the other systems on our office it receives an IP Address by the DHCP server. How will I go about setting up this type of printer. In windows I usual had to go and add a new port of type IP and then set the port number to 9100 and as type raw. This allowed me then to connect to the printer. But dont have a clue how to do this in linux
[/list] 

Any help comments would be much appreciated

---

### Post by p!=f on 2004-12-14
[QUOTE=gdeswardt]
[*]Currently on my windows machine we are using Checkpoint SecureClient to connect to our VPN. What programs are available in Ubuntu to allow me to connect to our VPN?
[/quote]
I don't know here exactly so bare with my answer. :)
[http://www.checkpoint.com/techsupport/downloads_sr.html](http://www.checkpoint.com/techsupport/downloads_sr.html)
[http://secureknowledge.checkpoint.com/pub/sk/docs/public/firewall1/4_1/pdf/fw-linuxvpn.pdf](http://secureknowledge.checkpoint.com/pub/sk/docs/public/firewall1/4_1/pdf/fw-linuxvpn.pdf)
[QUOTE=gdeswardt]
[*]We are running DHCP on our local network here, and everybody in the office (except me offcourse) is running Windows. Some of my daily requirements is to access our intranet website that is running on a Windows 2003 server with IIS. Due to the DHCP the servers IPAddress changes. When using windows I was able to browse the website by using "http://servername". I can not access it by using the same url but if i use the IP Address it does the same trick. Is there away in Ubuntu to access these resources by the Windows Networking sharing name instead of their IP Addresses?
[/quote]
Seems like you don't have appropriate entry in /etc/resolv.conf of your DNS server or turn on WINS client support in /etc/samba/smb.conf.
[QUOTE=gdeswardt]
[*]Our priners in the office is running on and IP port, but just like all the other systems on our office it receives an IP Address by the DHCP server. How will I go about setting up this type of printer. In windows I usual had to go and add a new port of type IP and then set the port number to 9100 and as type raw. This allowed me then to connect to the printer. But dont have a clue how to do this in linux
[/quote]
CUPSYS - point your browser to [http://localhost:631/admin](http://localhost:631/admin) and add the network printer.

---

### Post by gdeswardt on 2004-12-14
> I don't know here exactly so bare with my answer.
[http://www.checkpoint.com/techsupport/downloads_sr.html](http://www.checkpoint.com/techsupport/downloads_sr.html)
[http://secureknowledge.checkpoint.c...fw-linuxvpn.pdf](http://secureknowledge.checkpoint.c...fw-linuxvpn.pdf)

Thanks for the info, seems like there is alot of manually config needed for this, with a possible source build. So I am leaving this to investigate till later (Dont want to stop the momentum now  :D )

> Seems like you don't have appropriate entry in /etc/resolv.conf of your DNS server or turn on WINS client support in /etc/samba/smb.conf.

We are a small office I dont have a Window DNS Server setup. I did enable the Windows Networking option in the Compture/System Configuration/Networking on the General Tab but this still does nothing. I also had a look in the samba config file but could only find the section to enable WINS server option and not WINS Client. Could you please point me in the right direction.

> CUPSYS - point your browser to [http://localhost:631/admin](http://localhost:631/admin) and add the network printer.

Cant not logging would not accept my username and password (the same that allows me to login in the system) Is there a default username password for this? Or do you need to add a user to an apache like authentication file?

---

### Post by p!=f on 2004-12-14
> **gdeswardt]
We are a small office I dont have a Window DNS Server setup. I did enable the Windows Networking option in the Compture/System Configuration/Networking on the General Tab but this still does nothing. I also had a look in the samba config file but could only find the section to enable WINS server option and not WINS Client. Could you please point me in the right direction.
[/quote]
Sure  said:**
> 
Cant not logging would not accept my username and password (the same that allows me to login in the system) Is there a default username password for this? Or do you need to add a user to an apache like authentication file?
Check if you're in adm and lpadmin group:
```

[~] > groups
pef adm dialout cdrom floppy audio src video staff users plugdev lpadmin

```

---

### Post by gdeswardt on 2004-12-14
Thanks mate,

Changed the setting to 193.168.2.255

I got this IP Address from running nmblookup. Here is the code and response

```
# nmblookup -R aspenconnect
querying aspenconnect on 193.168.2.255
193.168.2.229 aspenconnect<00>
```

During this it picked up the correct ip address but when i try and do a ping after adding the the IP Address I get the following error:

```
# ping aspenconnect
ping: unknown host aspenconnect
```

This would suggest that this still did not work. Is there another setting I can change so that samba will use the nmblookup to resolve the host names to ipaddresses?

---

### Post by p!=f on 2004-12-15
[QUOTE=gdeswardt]
During this it picked up the correct ip address but when i try and do a ping after adding the the IP Address I get the following error:

```
# ping aspenconnect
ping: unknown host aspenconnect
```
This would suggest that this still did not work. Is there another setting I can change so that samba will use the nmblookup to resolve the host names to ipaddresses?[/QUOTE]
Did you restart SAMBA?
Can you try to ping the host with fully qualified domain name? (ie ping aspenconnect.mydomain.org)
Don't you have any firewall set up? If so, take a look at ports 137-139, both TCP and UDP and open them.
cat /etc/resolv.conf and cat /etc/hosts here please.

---

### Post by gdeswardt on 2004-12-16
Cant ping the full domain name cause we dont have a Domain Name Server setup only a workgroup with computers joining the webgroup.

---

### Post by p!=f on 2004-12-16
[QUOTE=gdeswardt]Cant ping the full domain name cause we dont have a Domain Name Server setup only a workgroup with computers joining the webgroup.[/QUOTE]
You already mentioned that. My bad. :)
Could you post your /etc/samba/smb.conf here?

---

### Post by gdeswardt on 2004-12-16
> You already mentioned that. My bad.
Could you post your /etc/samba/smb.conf here?

Hi p!=f

Would love to post my config file, but unfortantly I am unable to login into my Ubuntu system. This happened after I installed the NVidia grpahics drivers as specified in the gaming forum. On restart X Server failed to start and disabled itself due to some config failures. So i get the old text mode login. But when i type in my username and password that has worked for me so many times before in GDM,  i get an invalid user or password message. So now I am kind of stuck cause I can not configure my x server not even manually not even to mention to output my Samba config file.

I actually have post running in another forum about this and sooning as i do get this sorted out I will output my config file here. Thanks for all your help so far much appreciated.

---

### Post by gdeswardt on 2004-12-16
This has nothing to do with my samba problem but more with my previous post. Was just wondering if you would be able to help with this one as well.

As mentioned after I installed NVidia drivers my XServer fails to start up and it looks like I can not log into text mode. So I tried to boot up using the (Recovery Mode) which logs me in as root.

But when i try to execute ```
sudo dpkg-reconfigure xserver-xfree86
``` I do get the following error. ```
No such pseudo-hash field "l" at /usr/share/perl5/Debconf/Config.pm line 35, <DEBCONF_CONFIG> chunk 1
```

Any ideas of how to configure my Xserver in recovery mode?

---

