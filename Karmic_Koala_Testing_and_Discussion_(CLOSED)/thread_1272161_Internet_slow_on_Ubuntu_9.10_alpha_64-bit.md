---
title: "Internet slow on Ubuntu 9.10 alpha 64-bit"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by t2491tom on 2009-09-21
I upgraded a few months ago to Ubuntu 9.10 (64-bit) and then after a few weeks downgraded due to the slow internet. Then today I upgraded again because I missed all the new features such as the new vlc player and especially the new pulse audio. My problem is that the internet is slow.

Anyway my question is as follows; **Is anyone else out there having problems with Ubuntu 9.10's internet? If anyone has a fix for the issue or any suggestions about drivers, it would be greatly appreciated. And the problem is not with Firefox, the internet is slow with all applications. **

I am running an Hp Pavilion with a 1.6 GHz processor and 3gbs of ram (Ubuntu 9.10 64-bit, *latest alpha release* ).

My download speed is 4.63 Mb/s and my upload is 0.63 Mb/s. Don't worry I am aware that that is horrible, but the cable monopoly companies don't have the best speeds/connection. Anyway the speed is plenty sufficient when it comes to web browsing and my only problem is on Ubuntu 9.10. My computer running 9.04 works fine and all my Dad's Windows(yes I'm disappointed too) laptop's internet runs just fine.

This is a preemptive thanks.

---

### Post by sliketymo on 2009-09-21
> **t2491tom said:**
> I upgraded a few months ago to Ubuntu 9.10 (64-bit) and then after a few weeks downgraded due to the slow internet. Then today I upgraded again because I missed all the new features such as the new vlc player and especially the new pulse audio.

Anyway my question is as follows; **Is anyone else out there having problems with Ubuntu 9.10's internet? If anyone has a fix for the issue or any suggestions about drivers, it would be greatly appreciated. And the problem is not with Firefox, the internet is slow with all applications. **

I am running an Hp Pavilion with a 1.6 GHz processor and 3gbs of ram (Ubuntu 9.10 64-bit, *latest alpha release* ).

This is a preemptive thanks.
:confused: If you would be so kind as to include a little more information,such as what kind of connection you have, I am sure someone will offer some possible help.

---

### Post by ptn107 on 2009-09-21
I'm running an updated Karmic Alpha 6 x86_64.  Runs fine here.

---

### Post by aseriesoftubes on 2009-10-03
Web browsing is slow to non-existent for me.

I'm running 32-bit Xubuntu 9.10 beta on an HP d530. The ethernet controller in this machine uses a Broadcom chipset (I don't know which one--is there an easy way to figure it out?).

Web browsing was downright fast on the same machine under 9.04. I'm currently the a Windows partition on the same machine, and web browsing works as expected.

The strange thing is that, under 9.10, I can ping external sites just fine, and even Update Manager and Synaptic run fine, if a little slow. I've checked my settings in Firefox and Epiphany, and everything is exactly as it should be. I've gone through every network troubleshooting guide I can find, to no avail.

I think it's time to file a bug report, but I'm not sure what information is needed. Any advice?

---

### Post by aseriesoftubes on 2009-10-03
I should also mention that I originally installed the beta from 9.04 using update-manager -d. 

When I couldn't solve the networking problem, I broke down and did a fresh install. Same result both times.

I should also mention that I tried disabling ethernet in the BIOS, starting up, restarting, and re-enabling ethernet in the BIOS (in an attempt to force Ubuntu to reconfigure the adapter). That didn't work either.

---

### Post by ronacc on 2009-10-03
no problem here with my amd64 karmic , realtek 8185 wireless or nforce (nvidia) wired . occasionaly the cable chokes and the bottom drops out but thats comcast not my sys :lolflag:

---

### Post by blakamin on 2009-10-03
alt-f2

```
gksu gedit /etc/nsswitch.conf
```


and then change *hosts:* to

```
files mdns4 [NOTFOUND=return] dns
```

Sped things up for me.

It's a known DNS bug but I can't find the link at the moment.

---

### Post by aseriesoftubes on 2009-10-04
Hi blakamin,

Thanks for the tip. I made the change and rebooted, but I still get the same problem.

Any other suggestions?

Thanks!

---

### Post by nhasian on 2009-10-04
I'm not experiencing any internet speed issues here with any apps on Karmic, and i've been using it since alpha4.

---

### Post by ft_ on 2009-10-04
I've heard about ipv6 issues with some access points.
People changed it to ipv4.

---

### Post by Joe_Bishop on 2009-10-04
> **t2491tom said:**
> I upgraded a few months ago to Ubuntu 9.10 (64-bit) and then after a few weeks downgraded due to the slow internet. Then today I upgraded again because I missed all the new features such as the new vlc player and especially the new pulse audio. My problem is that the internet is slow.

Anyway my question is as follows; **Is anyone else out there having problems with Ubuntu 9.10's internet? If anyone has a fix for the issue or any suggestions about drivers, it would be greatly appreciated. And the problem is not with Firefox, the internet is slow with all applications. **

I am running an Hp Pavilion with a 1.6 GHz processor and 3gbs of ram (Ubuntu 9.10 64-bit, *latest alpha release* ).

My download speed is 4.63 Mb/s and my upload is 0.63 Mb/s. Don't worry I am aware that that is horrible, but the cable monopoly companies don't have the best speeds/connection. Anyway the speed is plenty sufficient when it comes to web browsing and my only problem is on Ubuntu 9.10. My computer running 9.04 works fine and all my Dad's Windows(yes I'm disappointed too) laptop's internet runs just fine.

This is a preemptive thanks.
What kind of connection do you use? Is it some PPP based protocol (pppoe -- it's called DSL in network manager, pptp, l2tp, etc)?
2.6.31 kernel has huge PPP regression, which leads up to 6 times speed decrease and general instability -- sometimes the kernel is hang up, breaking all IO. It would be funny to see how they would  swear Mark's stuff in the LOR ([http://linux.org.ru](http://linux.org.ru)) because of that. :lolflag:

Try 2.6.30 kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.8/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.8/)
Download headers and image, than install both. The speed should be OK with it, but no sound. I wish they support 2.6.30 too, 2.6.31 made my expirience of karmic horrible, I've never tried such a unusable Linux OS before. And it seems they couldn't improve it to the release, because kernel devs didn't improve that in their latest 2.6.32 rc 1.

---

### Post by Firkløver on 2009-10-04
I have had the same problem for the karmic alphas. Network speed in 9.10 is capped at 100 kB/s for me (my local net is 54 Mb/s and my internet connection is 10 Mb/s). The problem is as far as i've been able to figure out linked to the rt2x00 drivers. I have a wireless card with the rt2500pci chipset. If you run the command "lspci |grep Network" in a terminal it should show you which network card you have.

On the serialmonkey forums i have found this thread that says a fix is on the way (go to the last page, rt2500 speed problems is an old issue that keeps coming back):
[http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=4579](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=4579)

For Ubuntu 9.04 i had to issue the command "iwconfig wlan0 rate 54M" to get the card to go at its intended speed. But for 9.10 no matter what command i issue to the card, the speed of the connection will not exceed 100 kB/s. This includes setting the rate to "fixed". If i stress the network connection and issue the command "dmesg" this error fills the log:

[ 1856.760012] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).

 Just for fun i installed the mainline kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") but even with the 2.6.32-rc1 my network connection speed does not improve.

---

### Post by sliketymo on 2009-10-04
> **t2491tom said:**
> I upgraded a few months ago to Ubuntu 9.10 (64-bit) and then after a few weeks downgraded due to the slow internet. Then today I upgraded again because I missed all the new features such as the new vlc player and especially the new pulse audio. My problem is that the internet is slow.

Anyway my question is as follows; **Is anyone else out there having problems with Ubuntu 9.10's internet? If anyone has a fix for the issue or any suggestions about drivers, it would be greatly appreciated. And the problem is not with Firefox, the internet is slow with all applications. **

I am running an Hp Pavilion with a 1.6 GHz processor and 3gbs of ram (Ubuntu 9.10 64-bit, *latest alpha release* ).

My download speed is 4.63 Mb/s and my upload is 0.63 Mb/s. Don't worry I am aware that that is horrible, but the cable monopoly companies don't have the best speeds/connection. Anyway the speed is plenty sufficient when it comes to web browsing and my only problem is on Ubuntu 9.10. My computer running 9.04 works fine and all my Dad's Windows(yes I'm disappointed too) laptop's internet runs just fine.

This is a preemptive thanks.

I am not using 9.1(sticking with 9.04 for the time being,LOL).Running x86_64,satelite connection,no problems.You might take a look at Link <http://fasterdata.es.net/TCP-tuning>,click the link for your OS,ie Linux.Might help,won't hurt.:guitar:

---

### Post by autark on 2009-10-04
> **Joe_Bishop said:**
>  2.6.31 kernel has huge PPP regression, which leads up to 6 times speed decrease and general instability -- sometimes the kernel is hang up, breaking all IO.

I don't think Karmic should be released with such a glaring regression. What would be missed if Karmic shipped with the 2.6.30 kernel instead?

---

### Post by leonarun on 2009-10-05
I'm finding that the internet is really slow on 9.10 beta 64-bit. Seems to work in spurts. IPv6 is not enabled.

Just upgraded from 9.04 and everything else seems to be much improved, but the Internet performance is bad.

---

### Post by Saneless on 2009-10-05
I installed bind9 and resolvconf and that cleared up my slow internet issues.  Not sure why the DNS lookup sucks on 9.10 but it does.  Those two programs help it use a server that doesn't blow goats.

---

### Post by crom.osec on 2009-10-07
I've had same problem and while checking my system configuration I've found that resolv.conf contained some strange entries. You should edit the file and put in your correct dns addresses:
on ubuntu:
gksu gedit /etc/resolv.conf
on kubundu:
kdesudo kate /etc/resolv.conf

---

### Post by markbuntu on 2009-10-07
I did a clean Karmic beta install and have had zero problems with Internet connections, 30MBs down and 18 MBs up with Verizon Fios 15/5 service. Exactly the same as on my Hardy and Jaunty installs. 

Upgrades gave me so many headaches I just don't do them any more.

---

### Post by fxyefx on 2009-10-09
I too am having very slow internet browsing with Karmic.  I'm running 9.10 amd64 beta with a clean install.  It appears to be DNS-related, at least that's what I presume... (the 'Looking up...' portion of loading each web page.)  Just posting in hopes that this gets more attention before final release; I'll be sticking with Windows 7 RC for now.  IIRC I was having a very similar issue with 8.10 in its early life as well.
Other than this showstopper, looks to be a fantastic release!

Cheers

---

### Post by anglergab on 2009-10-10
Hello!
 
I've tried **Ubuntu 9.10 karmic beta** in VirtualBox and my computer, too.
But the internet connection - while browsing in Firefox - is really **slow** in both cases!
In jaunty the speed was OK.
 
I think, this problem is quite widespread.
 
What should we do?
 
Note: Windows 7 will come approx. one week before karmic.
If this problem won't be solved, many new users will not give a try to ubuntu (ever?),
they will simply use Win7.

---

### Post by ljrmorgan on 2009-10-10
I also have this problem - I thought it might be my wireless signal  at first (though I'm using a desktop, so it's in a fixed position, network manager reports full signal, and it's always worked in the past & works on windows).

I then thought it might be chromium, but I also have it in firefox, and trying to ping URLs too. From what I can tell it's DNS related, at least resolving hosts etc. seems to be where the problems start.

I am also on 64-bit. It's very noticeable, my internet fairly frequently just grinding to a halt and eventually working again.

---

### Post by slymi2005 on 2009-10-10
> **Saneless said:**
> I installed bind9 and resolvconf and that cleared up my slow internet issues.  Not sure why the DNS lookup sucks on 9.10 but it does.  Those two programs help it use a server that doesn't blow goats.

I decided to try this and I get the following when I try and install through synaptic and it just hangs there not sure if it's doing anything:
```
* Starting domain name service... bind9
resolvconf: Error: /etc/resolv.conf must be a symlink
invoke-rc.d: initscript bind9, action "start" failed.
```

Update: I decided to just restart the computer because synaptic did not appear to be doing anything and I had to run this and it appears that both bind9 and resolvconf are installed:

```
sudo dpkg --configure -a
Setting up resolvconf (1.44ubuntu1) ...
mkdir: created directory `/etc/resolvconf/run'
mkdir: created directory `/etc/resolvconf/run/interface'
update-rc.d: warning: resolvconf stop runlevel arguments (none) do not match LSB Default-Stop values (0 6)

Setting up bind9 (1:9.6.1.dfsg.P1-3) ...
 * Starting domain name service... bind9                                 [ OK ]
```

---

### Post by slymi2005 on 2009-10-10
It doesn't seem to have done anything, has anyone else found any solutions for this problem?

---

### Post by Firkløver on 2009-10-10
Can i ask those of you with problems what network card you are using? If you don't know, run the command:

lspci | grep Network

and paste the result in here.

---

### Post by W2IBC on 2009-10-10
well I have had the "slow" net issues with 9.04 and 9.10 where I was downloading at say 200 to 300KB/s 

i manually configed the DNS to have the ISP dns into it. which improved it a ton now downloading at 1MB/s+

my connection info looks like this

IP address 192.168.2.2
broadcast address 192.168.2.255
subnet mask 255.255.255.0
defult route 192.168.2.1
primary DNS 68.xx.xx.134  (ISP DNS gave to router)
secondary dns 68.xx.xx.134 (ISP DNS gave to router)

it seems to work wonders for me.

---

### Post by fxyefx on 2009-10-10
W2IBC's fix worked for me!
Under IPv4 settings I changed to Method: Automatic (DHCP) addresses only; edited to the DNS IP my router got automatically from Comcast, and the DNS queries are back to (almost) instantaneous.  In contrast, before doing this my connection info showed the Primary DNS as being the IP address of the router.  Now if only karmic could have made this adjustment out-of-the-box... :P
Thanks for the tip!

---

### Post by ljrmorgan on 2009-10-10
> **Firkløver said:**
> Can i ask those of you with problems what network card you are using? If you don't know, run the command:

lspci | grep Network

and paste the result in here.

Here's mine:
05:06.0 Network controller: RaLink RT2561/RT61 802.11g PCI

I think when I bought it I checked that it would work with linux, it hasn't been a problem before.

Could it possibly be a dhcp problem?

---

### Post by slymi2005 on 2009-10-10
lspci | grep Network
01:07.0 Network controller: RaLink RT2561/RT61 802.11g PCI

Hey fxyefx where would I go to find my isp dns?

---

### Post by Firkløver on 2009-10-11
Well it might be that i am barking up the wrong tree here. But to me it still seems like the rt2x00 driver is the core of my problem.

If anyone is running a ralink card and don't have a problem with wireless speed, could you post here, please?

---

### Post by mwolfer1 on 2009-10-11
Firkløver, I believe it's not your NIC driver, it appears that the problem is widespread across (I had the same problem with an Intel chipset, W2IBC's suggestion fixed it for me). I can't explain why response to/from a DNS server internal to your private network should be slower by magnitudes than an external resolve call. I was wondering whether it might be the connected with the type of router? I have a DLink DGL-4500. Anyone else?

---

### Post by Firkløver on 2009-10-11
Thank you for the response, but the problem is that my DNS is configured the way you suggest. Still my network speeds are very slow. My router is a Netgear branded one. My Vista installation is unaffected and my previous 9.04 install also worked fine.

I hope this issue gets resolved soon. If anyone has another idea, i will be very thankful if you voice it here.

---

### Post by Db77 on 2009-10-11
> **t2491tom said:**
> I upgraded a few months ago to Ubuntu 9.10 (64-bit) and then after a few weeks downgraded due to the slow internet. Then today I upgraded again because I missed all the new features such as the new vlc player and especially the new pulse audio. My problem is that the internet is slow.

Anyway my question is as follows; **Is anyone else out there having problems with Ubuntu 9.10's internet? If anyone has a fix for the issue or any suggestions about drivers, it would be greatly appreciated. And the problem is not with Firefox, the internet is slow with all applications. **

I am running an Hp Pavilion with a 1.6 GHz processor and 3gbs of ram (Ubuntu 9.10 64-bit, *latest alpha release* ).

My download speed is 4.63 Mb/s and my upload is 0.63 Mb/s. Don't worry I am aware that that is horrible, but the cable monopoly companies don't have the best speeds/connection. Anyway the speed is plenty sufficient when it comes to web browsing and my only problem is on Ubuntu 9.10. My computer running 9.04 works fine and all my Dad's Windows(yes I'm disappointed too) laptop's internet runs just fine.

This is a preemptive thanks.
I'd encountered the same slow DNS lookup problem with the Karmic Koala beta (netbook remix version). I solved it by replacing the native network connection manager with the open source network manager Wicd  [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) 
Now the DNS lookup and Web connections are instantaneous. Wicd seems like an excellent network manager that Canonical might consider as a default.
D

---

### Post by hendrikwout on 2009-10-14
Same issue here.

I've running karmic koala in virtualbox. The dns is then 10.0.2.3, which is added to /etc/resolv.conf automatically by network-manager. It seems 'dig' can resolve things like 'google.com' with this setting, but firefox, wget, and problably some other CAN'T. If I put the main domain name server of my ISP in /etc/resolv.conf, then firefox, wget etc. CAN resolve things like 'google.com'.

In my opinion, this is a very important bug, as 'internet' is a basic functionallity. Many users who don't have direct internet access (I tried a direct non-virtualbox install and had the same problem because my wireless router is the dns in that case), will not have internet working in karmic koala. This bug should be fixed and should not be worked around by ubuntu-users.

I tried to make a bug report in launchpad for this, but didn't work. Someone can?

---

### Post by kickwin on 2009-10-14
> **t2491tom said:**
> I upgraded a few months ago to Ubuntu 9.10 (64-bit) and then after a few weeks downgraded due to the slow internet. 

Sorry for the off-topic query. But could you tell me how I can downgrade to 9.04 from 9.10. 9.10 appears to be a memory hog on my Dell Inspiron laptop and my touchpad doesn't work.

---

### Post by DodgeV83 on 2009-10-20
This 100% fixed my problem!  Posted by mikio at

[http://ubuntuforums.org/showthread.php?t=1283146](http://ubuntuforums.org/showthread.php?t=1283146)

1.  In /etc/dhcp3/dhclient.conf add the following line:

prepend domain-name-servers 208.67.222.222,208.67.220.220;

2.  In /etc/nsswitch.conf edit this line

hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4

to this

hosts: files dns

I'm not sure which one of these did it to be honest, but it's fixed!

---

### Post by P-I H on 2009-10-20
I have a D-Link Dir-655 Router. When I removed the "DNS Relay" setting, performanced improved a lot.
Before it took about a minute to load newspaper sites in 7 tabs in Firefox. After the change it takes about 12 sec.
The setting did not impact performance in Jaunty.

---

### Post by foxy123 on 2009-10-21
rt5000 issue with a new kernel (2.6.31) is quite annoying. I read on the serialmonkey forum that the fix had been released and allegedly is implemented in 2.6.32, but I have not heard of anyone who compiled the testing kernel and got it fixed :(

---

### Post by slymi2005 on 2009-10-22
My wireless internet is no longer working on my desktop after trying dodge's fix and it is also not working on my netbook which I did not change any settings on. 
(Desktop)
lspci | grep Network
01:07.0 Network controller: RaLink RT2561/RT61 802.11g PCI

Netbook is eeepc 1000ha.

Is anyone else's internet out?

---

### Post by Firkløver on 2009-10-22
I am sure there are ipv6 dns issues for some, but it seems to me there is also a genuine problem with the rt2x00 driver shipping with karmic. Some of us are experiencing <1 Mbit transfers (even with low latencies) that are probably linked to the following kernel bug:

[http://bugzilla.kernel.org/show_bug.cgi?id=13362](http://bugzilla.kernel.org/show_bug.cgi?id=13362)

The bug has not been resolved in the mainline kernels (up to 2.6.32-rc5) that i have tested either. 

If Ubuntu 9.10 launches with this bug, I implore all of you to think before just posting the dns fix for people who come to the forums for help. Ask for the make and model of the card first, (alternatively lspci | grep Network) and point them to the bug if they have a ralink card. I really hope the bug is limited to a few rt2x00 cards only or this could get ugly.

---

### Post by Oak37 on 2009-10-24
W2IBC's tip also worked for me.

I checked /etc/resolv.conf and had three entries for nameserver, the first being my router while the other two referenced the DNS addresses supplied by my ISP. After deleting the reference to my router my internet speed is now flying!!

Thanks!

---

### Post by dayzed2 on 2009-10-26
I was also experiencing stalled and slow loading of webpages in Firefox using x86_64 on 9.10. By using my ISP's DNS servers in my /etc/resolve.conf instead of my routers IP Address fixed this problem. If your router is set to use "DNS Relay" then DHCP will pass on the routers IP address as the DNS address instead of the ISP's DNS servers. This is usually the way things work unless you run a DNS server locally on your LAN. Either the Kernel has a bug somewhere or the Ubuntu developers missed something.

Hope this helps someone.

---

### Post by Crunchy the Headcrab on 2009-10-26
> **dayzed2 said:**
> I was also experiencing stalled and slow loading of webpages in Firefox using x86_64 on 9.10. By using my ISP's DNS servers in my /etc/resolve.conf instead of my routers IP Address fixed this problem. If your router is set to use "DNS Relay" then DHCP will pass on the routers IP address as the DNS address instead of the ISP's DNS servers. This is usually the way things work unless you run a DNS server locally on your LAN. Either the Kernel has a bug somewhere or the Ubuntu developers missed something.

Hope this helps someone.
Yeah, I had to do the same thing except every time I rebooted resolve.conf would revert to it's old ways, so I had to change it using the network manager and now it works fine.

---

### Post by kyle.wright@gmail.com on 2009-10-27
Same issue here. Editing resolv.conf and removing nameserver entry for my router fixed the issue.  However, each time I reconnect I have to go in and edit resolv.conf again.

Are there other fixes?

---

### Post by Kleist on 2009-10-28
00:19.0 Ethernet controller: Intel Corporation 82567V-2 Gigabit Network Connection


I'm running 9.10 RC, and having the same problem: slow internet connection. 

Also, I notice my adblock plus firefox plugin doesn't work. Is it related to this? 

I'm going to try some of the advise given here and report. :(

---

