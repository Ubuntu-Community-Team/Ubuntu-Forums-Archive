---
title: "Cannot Read USB External Hard Drive Connected to Router"
date: 2014-12-28
forum: MINT
---

### Post by JohnMorrow on 2014-12-28
I have a new Toshiba Canvio Connect USB 1 TB drive which I would like to access through my home network, but I can't read it when booted into Linux Mint 17 (based upon Ubuntu 14.04). I can read the drive using Windows 8.1 and XP. I can also read/write the external drive from linux if it is plugged directly into a USB port on my laptop. My router is a Western Digital "My Net N900". It has two USB ports, and the drive is plugged into Port 1. Any help is appreciated.

John

---

### Post by JohnMorrow on 2015-01-01
A little love here folks, please? Surely somebody else here has had a similar issue? I'm going to assume people need more information than what I have already provided above, so please review the output of the following commands. The last one leads me to think I may have a Samba problem.

john@Joshua ~ $ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
default         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0
192.168.1.0     *               255.255.255.0   U         0 0          0 wlan0
--------------------------------------------------------------------------------------------------------------------------------------------

john@Joshua ~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr 10:c3:7b:bc:27:6a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:551 errors:0 dropped:0 overruns:0 frame:0
          TX packets:551 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:58593 (58.5 KB)  TX bytes:58593 (58.5 KB)

wlan0     Link encap:Ethernet  HWaddr 54:27:1e:b1:a3:7f  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5627:1eff:feb1:a37f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3976 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3755586 (3.7 MB)  TX bytes:791817 (791.8 KB)
-------------------------------------------------------------------------------------------------------------------------------

john@Joshua ~ $ sudo smbclient -L '\\192.168.1.1\' -U test%test
[sudo] password for john: 
Server requested LANMAN password (share-level security) but 'client lanman auth = no' or 'client ntlmv2 auth = yes'
tree connect failed: NT_STATUS_ACCESS_DENIED
-------------------------------------------------------------------------------------------------------------------------------------

Any help is graciously appreciated.
Thanks!

---

### Post by chili555 on 2015-01-01
> john@Joshua ~ $ sudo smbclient -L '\\192.168.1.1\' -U test%test
[sudo] password for john: 
Server requested LANMAN password (share-level security) but 'client lanman auth = no' or 'client ntlmv2 auth = yes'
tree connect failed: NT_STATUS_ACCESS_DENIEDI get that reply, too, for that command. However, I can open the file manager; Nautilus, in my case, click Browse Network and find GBR1, the SSID of my router and find sda1, my 1TB USB harddrive. Have you tried that? What is the outcome?

[ATTACH=CONFIG]258934[/ATTACH]

---

### Post by Bucky Ball on 2015-01-01
*Thread moved to **MINT**.*

Please be aware that the main support areas here are for Ubuntu and it's flavours Kubuntu, Xubuntu, Edubuntu, Lubuntu, UbuntuGnome, Ubuntu Studio, and Mythbuntu. Regardless of the section you are in here, your thread will still appear at the top of the new posts list when it is posted on. 

While you are welcome to post in this section, you might get some joy posting on the Mint forums also. They have an active community and forums.

Good luck with it. ;)

---

### Post by JohnMorrow on 2015-01-01
When I open my file manager, Caja in Mint MATE edition, I can see the router "MYNETN900", but when I double-click on it nothing happens. I can't see the Toshiba external drive connected to the router unless I am booted into Windows. I can't seem to post an image into this forum, but I put the screenshot on my Google Drive, just follow the link below:
[https://drive.google.com/folderview?id=0B9ibopctyv_RUDN6X2FMQmN1UkU&usp=sharing]("https://drive.google.com/folderview?id=0B9ibopctyv_RUDN6X2FMQmN1UkU&usp=sharing")

---

### Post by Bucky Ball on 2015-01-01
Open a browser and put your router IP in the address bar and hit enter. This should take you to the router config page. Perhaps something needs to be tweaked there. You should be able to locate the drive in there and perhaps get some clues as to what's going wrong. 

The router IP is probably something like 192.168.0.1.

(PS: I killed the 'reply deleted' post for ya. ;))

---

### Post by JohnMorrow on 2015-01-02
Thanks Bucky Ball. The router configuration was one of the first things I looked at when I started this adventure. I put two more screenshots in the Google Drive folder linked above. The router storage is configured (has been for awhile), and the router is designated "Master Browser".  I figure I have some sort of network configuration problem, but beats me as to what it is.

John

---

### Post by Bucky Ball on 2015-01-02
I see your screenshots now. Does the external disk require an IP? It is possibly getting set one by the router. You should set a static IP if this is the case (otherwise the router will set different ones when you reboot or reconnect the disk).

If you know the IP of the disk you could perhaps try pinging it and see what happens. In a terminal:

ping ***.***.***.*** (IP of disk)

If you can ping it, you could install Filezilla and see if you can communicate with it via FTP.

Another thing I notice is that it is in the domain 'WORKGROUP'. This is a default with Windows and indicates you might be connecting via samba, but not sure that's installed by default in Ubuntu. If you are attempting to connect with samba and it's not installed, could be the problem. Also, if your computer is in a different domain, won't pick up the external disk.

Edit your wireless connection and create a static IP for your machine and put it in the domain 'WORKGROUP'. Not sure if you can set the domain without creating a static IP, but you could do that to if possible on your OS.

Hope that helps. ;)

---

### Post by Morbius1 on 2015-01-02
> **JohnMorrow said:**
> When I open my file manager, Caja in Mint MATE edition, I can see the router "MYNETN900", but when I double-click on it nothing happens. I can't see the Toshiba external drive connected to the router unless I am booted into Windows. I can't seem to post an image into this forum, but I put the screenshot on my Google Drive, just follow the link below:
[https://drive.google.com/folderview?id=0B9ibopctyv_RUDN6X2FMQmN1UkU&usp=sharing](https://drive.google.com/folderview?id=0B9ibopctyv_RUDN6X2FMQmN1UkU&usp=sharing)
I looked at the user manual for your router and it's designed to work with a mac ( OSX ). You should be able to open a terminal and run:
```
caja smb://mynetn900.local
```
Then you can bookmark it. Don't forget the ".local" at the end.

Note: Even though the user manual I'm looking at is for the mynetn900 the hostname appears to be mynetn900c.local - with a "c" after the 900. You might want to try both. Or run this command to find out what it's name is:
```
avahi-browse -at | grep IPv4
```
[COLOR=#0000cd]**EDIT**[/COLOR]: This is from page 66 of the router's manual. It shows how the mac can connect to the samba server on the router:
[ATTACH=CONFIG]258949[/ATTACH]
If the mac can access the server by a *some-host-name*.local so should Linux since they share the same underlying technology.

---

### Post by JohnMorrow on 2015-01-02
Morbius1, you had the answer, or at least part of it. The command "caja smb://mynetn900.local" allows me to see the drive. I am (inconsistently) getting some read/write errors when trying to copy or play some files across the network. When trying to copy the highlighted "Data6..." directory, I got an "invalid argument" error, see the 'Copy Error Screenshot" image on Google Drive, here[https://drive.google.com/folderview?id=0B9ibopctyv_RUDN6X2FMQmN1UkU&usp=sharing]("https://drive.google.com/folderview?id=0B9ibopctyv_RUDN6X2FMQmN1UkU&usp=sharing")

---

### Post by Morbius1 on 2015-01-03
That part of the problem I cannot answer especially the intermittent nature of the problem. 

It sounds like a file permissions problem on the drive itself but I don't have your router and have to rely solely on the user manual and it's not at all clear how it manages these external drives or if it manages these drives. 

Did a quick search on the WD forums and there's a number of perplexing questions like these:
[http://community.wd.com/t5/My-Net-Networking-Devices/External-Hard-Drive-access-thru-My-Net-N900/td-p/528841](http://community.wd.com/t5/My-Net-Networking-Devices/External-Hard-Drive-access-thru-My-Net-N900/td-p/528841)
[http://community.wd.com/t5/My-Net-Networking-Devices/My-Net900-and-3TB-external-drives/td-p/833340](http://community.wd.com/t5/My-Net-Networking-Devices/My-Net900-and-3TB-external-drives/td-p/833340)
[http://community.wd.com/t5/My-Net-Networking-Devices/N900-and-USB-Drive-Failures/m-p/686451/highlight/true#M4195](http://community.wd.com/t5/My-Net-Networking-Devices/N900-and-USB-Drive-Failures/m-p/686451/highlight/true#M4195)

---

### Post by JohnMorrow on 2015-01-06
You may be right about the permissions aspect, but I'm thinking of a new approach. Buy a Pogoplug box, and access my Toshiba USB drive through that.

$20 Pogoplug here
 [http://www.amazon.com/gp/product/B006I5MKZY/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B006I5MKZY&linkCode=as2&tag=nerdvitt-20&linkId=SJ4GFXLO7XRDB67R]("http://www.amazon.com/gp/product/B006I5MKZY/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B006I5MKZY&linkCode=as2&tag=nerdvitt-20&linkId=SJ4GFXLO7XRDB67R")

Instructions here
[http://tuxtweaks.com/2013/06/mount-your-pogoplug-on-linux/]("http://tuxtweaks.com/2013/06/mount-your-pogoplug-on-linux/")

Your thoughts?

---

