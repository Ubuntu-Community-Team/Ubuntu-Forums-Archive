---
title: "Slow web browsing still a problem in Lucid?"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by LADmaticCA on 2010-03-29
The main bug I wanted squashed from Karmic was the slow browsing/dns lookup. But it is still present on my laptop using the ath5k driver. Is anyone else having this problem as well? Perhaps it's a driver regression? The same laptop on Jaunty works wonderfully. Browsing was swift on my desktop using the rtl8180 wireless driver(until my hard drive died). I have tried a lot of the workarounds with no luck.

---

### Post by bowens44 on 2010-03-29
> **LADmaticCA said:**
> The main bug I wanted squashed from Karmic was the slow browsing/dns lookup. But it is still present on my laptop using the ath5k driver. Is anyone else having this problem as well? Perhaps it's a driver regression? The same laptop on Jaunty works wonderfully. Browsing was swift on my desktop using the rtl8180 wireless driver(until my hard drive died). I have tried a lot of the workarounds with no luck.

Are you sure the problem isn't your browser? After much frustration I solved my apparent slow DNS look up problem  by renaming my .mozilla directory and removing/reinstalling firefox.

Also no problems with chromium feels much faster then firefox.

---

### Post by Omoronovo on 2010-03-29
I had a problem relating to slow browsing, and it was caused by IPV6 - my router was kinda cheap, and despite all the configuration options, it has no way to change default DNS servers. My isp is quite small, and their automatically assigned DNS servers unfortunately do not respond to AAAA requests, so I was forced to disable ipv6 entirely ( add ipv6.disable=1 to grub).

By setting the /etc/resolv.conf to use google's dns or Opendns, the problem remained, which is why I believe my router also has problems specifically relating to IPv6 support.

I would recommend to try this if all else fails (perhaps contact your ISP to see if their infrastructure supports ipv6 - almost no isp's have it implemented yet fully, except some larger ones).

---

### Post by LADmaticCA on 2010-03-29
Thanks for the replies.

I have tried firefox, opera, and chromium. All suffer the same. There are moments where these browsers operate as fast as they should, but eventually the hangs start up again. It also affects my ability to install programs using apt-get. I get a lengthy "waiting for headers" message before it finally starts.

I've tried open dns, google dns, disabling ipv6 in the kernel and browser. None of it worked. I guess it may be a router issue.:(

---

### Post by _h_ on 2010-03-29
Have you contacted your ISP about it? :P

---

### Post by v1ad on 2010-03-29
chrome or chromium? chrome does miracles on the speed when i compared it to other browsers. but its probably your isp.

---

### Post by sgosnell on 2010-03-29
Try using openDNS for a DNS server, instead of whatever your ISP is using.  Using OpenDNS is one of the best decisions I've made.

---

### Post by LADmaticCA on 2010-03-29
^^
Both. With my current living situation, I am not in charge of the ISP account...I believe they're on comcast. Thanks all for the replies, this is really unfortunate.

---

### Post by sgosnell on 2010-03-30
You can use OpenDNS regardless of whether you're in charge of the account, in fact you can use it on any connection anywhere.

---

### Post by Scruffynerf on 2010-03-30
Also try disabling IPv6 in the Firefox about:config area. Often the delay can be multiple timeouts relating to IPv6 requests.

---

### Post by LADmaticCA on 2010-03-30
I've tried Open DNS and disabling ipv6 in firefox's about:config still no luck.

---

### Post by psyke83 on 2010-03-30
> **LADmaticCA said:**
> The main bug I wanted squashed from Karmic was the slow browsing/dns lookup. But it is still present on my laptop using the ath5k driver. Is anyone else having this problem as well? Perhaps it's a driver regression? The same laptop on Jaunty works wonderfully. Browsing was swift on my desktop using the rtl8180 wireless driver(until my hard drive died). I have tried a lot of the workarounds with no luck.

In my experience, all the advice to change DNS servers, disable IPv6, and to tweak network settings in specific applications, were all red herrings.

You should subscribe to [bug #94940]("https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940"). It is possible to eliminate the slow dns  lookups if you disable mdns lookups (which breaks avahi-daemon, but at least you can confirm if this is your issue). See [comment #48]("https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940/comments/48") for specific instructions.

If, however, this doesn't help, then you're suffering from a driver bug. You could try getting hold of Windows drivers and using them through ndiswrapper to see if there's any improvement.

---

### Post by LADmaticCA on 2010-03-31
> **psyke83 said:**
> In my experience, all the advice to change DNS servers, disable IPv6, and to tweak network settings in specific applications, were all red herrings.

You should subscribe to [bug #94940]("https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940"). It is possible to eliminate the slow dns  lookups if you disable mdns lookups (which breaks avahi-daemon, but at least you can confirm if this is your issue). See [comment #48]("https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940/comments/48") for specific instructions.

If, however, this doesn't help, then you're suffering from a driver bug. You could try getting hold of Windows drivers and using them through ndiswrapper to see if there's any improvement.

Thanks for the response. Unfortunately the mdns thing didn't work either. I'll try the ndiswrapper and see if it helps.

---

### Post by JW3 on 2010-04-01
Hi,

here is how I solved the problem (based on [https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940]("https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940")):

1) deinstall libnss-mdns package:
```
sudo apt-get remove libnss-mdns
```

2) make sure that the file /etc/nsswitch.conf does not contain the line
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
but instead has the line:
hosts:          files dns
```

What is strange is that editing the nsswitch.conf (and restarting) did not in itself suffice (as I would expect).

j.

---

### Post by wkulecz on 2010-04-01
>  From the 94940 bug thread:

As said before, the problem occurs when you use mDNS combined with a broken DNS server. If your DNS server is not broken, you will not have any delays. (Unfortunately the DNS relays on several cheap home routers are broken...)

Some ways to solve this:
* try to detect broken DNS servers & configure Ubuntu to not use them
  * use a local DNS server on the system instead? (contra: significantly increases the load on the root servers?)
  * configure Ubuntu to use a proper DNS server (either one run by Canonical or one provided by a 3rd party like Google?)
  * disable mDNS when broken routers (or other broken DNS servers) are detected (breaks other things though)
* current approach with patched glibc (which breaks several applications, so far from optimal)
* ... ?

One problem with detecting broken DNS servers is that that might change depending on where you connect your laptop of course, so it would have to be dynamic...


I verify this bug on 10.04Beta1.

I submit that when Windows and Mac machines have no DNS delays on the same subnets, blaming the problem on "broken DNS servers or routers" will be a tough sell to the powers than be.

I also submit that 7-15 second delays in website link clicks will have Windows users running immediately back to Windows and never looking back.

If this is not a priority problem to have fixed the final, dreams of Linux on the desktop are dying.

A followup question, what exactly is lost by disabling libnss-mdns that the Windows user trying Ubuntu might notice?

--wally.

---

### Post by wkulecz on 2010-04-01
I can confirm that the instructions from JW3 about removing libnss-mdns does nothing about making DNS lookups (using nslookup) or Firefox faster, typically 10+ seconds on 10.04Beta1. (Yes I rebooted, and verified the /etc/nsswitch.conf hosts line is only: files dns)


On Windows I can launch a book mark I haven't used in a long time (unlikely to be in dns cache) in a new tab and have it loading in 2-3 seconds. 

On Ubuntu 8.04 (same subnet)nslookup on an obscure site is maybe 1 second, just a noticible pause, this is matching Windows dns speed or maybe even a tad better.


There is a performance issue in 10.04beta1 that on some systems will make Ubuntu less than usefull and quickly uninstalled.

Since nslookup is slow, the solution is likely in the system, not the apps like Firefox.

--wally.

---

### Post by LADmaticCA on 2010-04-01
I tried to find a Windows driver for my Atheros AR2413 but was unsuccessful. Last night I did a basic Arch Linux install on the laptop just to see how it performed. To my surprise, I was having the same issue with browsing. It's got to be a driver regression of sorts. Is this only affecting Atheros users? Is it exclusive to wireless also? I don't have a hardline to test it.

---

### Post by wkulecz on 2010-04-01
My systems are all wired 100BaseTX.

What is Arch Linux based on?  I have the same issue in 9.10, although it seems perhaps worse in 10.04Beta1

How is your speed at getting a DNS response with: nslookup site_not_in_cache ?

--wally.

---

### Post by sant on 2010-04-01
If you are using auto eth0,edit the connection manually.

---

### Post by LADmaticCA on 2010-04-01
> **wkulecz said:**
> My systems are all wired 100BaseTX.

What is Arch Linux based on?  I have the same issue in 9.10, although it seems perhaps worse in 10.04Beta1

How is your speed at getting a DNS response with: nslookup site_not_in_cache ?

--wally.

My arch install is using the 2.6.32 kernel. Tried nslookup and it's good, under a second on the arch install.

---

### Post by LADmaticCA on 2010-04-05
The more I read on this, the more it seems to be a kernel issue. I've read something similar on the arch forums, where using an older kernel fixed the problem. Kinda makes sense seeing how with the older kernel in jaunty everything works fine. Now if I can find out how to install an older kernel.

---

### Post by swoll1980 on 2010-04-06
Your routers IP address is being added to your list of name servers in your resolv.conf. This causes name resolution to be painfully slow. The easiest way to fix this is to click the network manager applet, click edit connections...,choose your card and click edit, click the ipv4 Settings tab, next to method choose Automatic (DHCP) addresses only, enter your dns address, click apply, enter password.

If you still have a version of the network manager that doesn't have the address only feature. Edit the resolv.conf
```
sudo nano /etc/resolv.conf
```delete the line that has "nameserver 192.168.x.x"
hit ctrl +x to save the edited file.
```
sudo chattr +i /etc/resolv.conf
``` This will keep network manager from re-editing your resolv.conf. If you ever need to change the file again you will have to unlock it. 
```
sudo chattr -i /etc/resolv.conf
```
Hope this helps some people out.

---

### Post by freeball1 on 2010-04-06
> **swoll1980 said:**
> Your routers IP address is being added to your list of name servers in your resolv.conf. This causes name resolution to be painfully slow. The easiest way to fix this is to click the network manager applet, click edit connections...,choose your card and click edit, click the ipv4 Settings tab, next to method choose Automatic (DHCP) addresses only, enter your dns address, click apply, enter password.

What exactly do you mean by "your dns address"?
Some public servers like in [_-> this <-_]("https://store.opendns.com/setup/device/ubuntu/") guide?

---

### Post by swoll1980 on 2010-04-06
> **freeball1 said:**
> What exactly do you mean by "your dns address"?
Some public servers like in [_-> this <-_]("https://store.opendns.com/setup/device/ubuntu/") guide?

They are provided by your ISP. Your computer would have received them dynamically, and listed them in your resolv.conf to view them do
```
cat /etc/resolv.conf 
```There should be two listed, though you will only need one. Choose the one on top. They will be the ones that don't start with 192

---

### Post by LADmaticCA on 2010-04-09
My resolv.conf didn't list any other nameservers. I tried looking up the DNS for my ISP and using it, but still no luck. Looks like I'll have to stick with jaunty on this laptop. Lucid works great on my desktop at least. I wish I had another wireless adapter to try on this laptop.

---

### Post by jaunbanaun on 2010-04-10
Can confirm that I'm experiencing the same problem with my fathers laptop (Toshiba Satellite L30). When using the wireless connection and trying to use web browsers like firefox and chrome there's a very slow or non-responsive behavior.

Weird is that when using the links text browser everything loads lightning fast and there's no problem using firefox or chrome when connecting LAN-cable or establishing 3G-connection.

Possible fix anyone?

```
09:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
	Subsystem: Askey Computer Corp. Device 7094
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 168 (2500ns min, 7000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at c0110000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k
	Kernel modules: ath5k
```

---

### Post by grandtoubab on 2010-04-10
> **LADmaticCA said:**
> The more I read on this, the more it seems to be a kernel issue. I've read something similar on the arch forums, where using an older kernel fixed the problem. Kinda makes sense seeing how with the older kernel in jaunty everything works fine. Now if I can find out how to install an older kernel.

from here 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

get the kernel you want. 3 files in a folder of your choice
 linux-headers-xxxxxxxxxx.deb
 linux-headers-xxxxxxxxxx-**all**.deb
 linux-image-xxxxxxxxxxxxxxxxx.deb

then from the folder in xterm
```
sudo dpkg -i linux*.deb
```

that's it :lolflag:

You can see the result in
/usr/src

---

### Post by Ali_Taimur on 2010-04-10
Just wanted to add that I am experiencing extremely slow DNS lookup as well. I hope it gets resolved soon coz its almost impossible to browse the web

---

### Post by ebe326 on 2010-04-11
Add me to the list. Extremely painful web experience.

---

### Post by Digikid on 2010-04-11
This is a problem with Ubuntu and NOT with your ISP or any browser.  Canonical needs to get off their butts and fix this issue that has been around since the 8 series of Ubuntu.  Disabling IPV6 does not help the problem at all regardless of what others are saying sadly.

The only thing that we can do is wait for Canonical to fix it...if they ever do.

---

### Post by lvleph on 2010-04-11
I am going to add myself to this list. My wife started using windows again after 2 years of linux!

---

### Post by LADmaticCA on 2010-04-11
> **grandtoubab said:**
> from here 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

get the kernel you want. 3 files in a folder of your choice
 linux-headers-xxxxxxxxxx.deb
 linux-headers-xxxxxxxxxx-**all**.deb
 linux-image-xxxxxxxxxxxxxxxxx.deb

then from the folder in xterm
```
sudo dpkg -i linux*.deb
```

that's it :lolflag:

You can see the result in
/usr/src

Hey thanks for that info. I tried the older Jaunty kernel, but Lucid won't boot with it...it just hangs.

---

### Post by lvleph on 2010-04-11
The old Jaunty Kernel cannot mount ext4 file systems, so that is probably the problem.

---

### Post by grandtoubab on 2010-04-11
> **LADmaticCA said:**
> Hey thanks for that info. I tried the older Jaunty kernel, but Lucid won't boot with it...it just hangs.
So you can boot to another kernel,thanks to Grub, and then remove the bad one through synaptic and ...choose another one:) Karmic is ok with ext4
Another way to check your DNS is to use [http://code.google.com/p/namebench/](http://code.google.com/p/namebench/)
by the way nice Art on your website

---

### Post by LADmaticCA on 2010-04-11
Thanks for the compliment:). I just tried the 2.6.31 kernel. It boots but the issue is still there.

---

### Post by sgosnell on 2010-04-11
Regressing to an older kernel is seldom, if ever, a good idea.  Lots of stuff in Lucid depends on having a newer kernel.  The [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc3-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc3-lucid/) kernel seems to be very good on mine, if you feel the need for a different kernel than the default one.

---

### Post by meeples on 2010-04-11
currently using my xp partition because of this.

UGH! xp doesnt have facebook chat or twitter :(

---

### Post by LADmaticCA on 2010-04-11
Alright, tried yet another kernel (2.6.34rc3) still no luck. Strange how it seems to be on certain sites, like deviantart.

---

### Post by Asraniel on 2010-04-11
isn't there in the webkit based browsers a debug console or so that shows you what took how long to load? i think rekonq has that console, you might want to check it out, perhaps you will be able to see what exactly takes so long to load

---

### Post by LADmaticCA on 2010-04-12
Alright, I think I'm on to something. Turns out I didn't have a java-runtime environment installed for my browsers. Installing one fixed some of the sites. Also the firfox add-on, NoScript, allows sites that use to hang...now open immediately. So it looks to be an issue with scripts.

---

### Post by psyke83 on 2010-04-12
LADmaticCA,

Right-click on the NetworkManager applet, choose "Connection Information". In the window that pops up, please provide the following details:

[LIST=1]
[*]Default route
[*]Primary DNS
[*]Secondary DNS
[/LIST]

---

### Post by c00lwaterz on 2010-04-12
do you always get slow? or maybe sometimes? how slow is your connection? in our country the internet service is not good. sometimes fast, most of the time slow and sometimes super slow.

---

### Post by grandtoubab on 2010-04-12
what about your MTU ?

I fixed it at 1492

right click on network-maager icon
select modify
select auto eth0 click on modify

---

### Post by LADmaticCA on 2010-04-12
> **psyke83 said:**
> LADmaticCA,

Right-click on the NetworkManager applet, choose "Connection Information". In the window that pops up, please provide the following details:

[LIST=1]
[*]Default route
[*]Primary DNS
[*]Secondary DNS
[/LIST]

Default route 192.168.1.1
Primary DNS 4.2.2.4
Secondary DNS 4.2.2.5

@c00lwaterz
My speed varies on the laptop. It's plenty fast enough when it actually does connect. But my desktop on the same wireless network is much better...running Jaunty

@grandtoubab
I'll try that, but things do seem to be better once enabling NoScript. Problem is NoScript tends to block some useful items and I have to toggle it on and off.

---

### Post by meeples on 2010-04-12
i just disabled ipv6 in firefox and everything is loading great. 

but cant seem to disable ipv6 for the whole system, all the guides i can find are for karmic and earlier.

how does it work in lucid?

actually i would be happy just being able to disable it in chrome..

---

### Post by sgosnell on 2010-04-12
You can disable it for each network connection.  Right-click on the network manager icon, select Edit Connections, and for each connection, edit it and on the IPv6 tab set it for Ignore.  I have no idea how to do it inside Chrome, I don't use it.  I tried it and didn't like it at all.

---

### Post by rjbennett on 2010-04-13
This issue of slow wireless connections ought to be a top priority for Canonical, but apparently it isn't. I have the impression that this issue has been around for a couple of YEARS or so. In order to solve this problem on my laptop, I've tried nearly all of the suggestions listed in this forum and other places, and nothing works.

If I run a cable to my laptop from my router, I get the speed I'm paying my ISP for - 20 Mbps. If I try to use Ubuntu's wireless connection. I get around half that, and sometimes much less.

I was curious to see what would happen with Windows 7. As test, after backing up my Ubuntu configuration, I installed Windows 7 on the laptop and the wireless connection works like a dream.

What is WRONG with Canonical? There are so many good things about Ubuntu, but this slow wireless connection problem is going to kill Ubuntu for me and a lot of other people.

Fast, efficient wireless connections ought to be an integral part of Ubuntu, as in Windows.

Sorry to go on and on like this, but this is a serious issue with me - and with a lot of other people as well.

---

### Post by lvleph on 2010-04-13
> **rjbennett said:**
> This issue of slow wireless connections ought to be a top priority for Canonical, but apparently it isn't. I have the impression that this issue has been around for a couple of YEARS or so. In order to solve this problem on my laptop, I've tried nearly all of the suggestions listed in this forum and other places, and nothing works.

If I run a cable to my laptop from my router, I get the speed I'm paying my ISP for - 20 Mbps. If I try to use Ubuntu's wireless connection. I get around half that, and sometimes much less.

I was curious to see what would happen with Windows 7. As test, after backing up my Ubuntu configuration, I installed Windows 7 on the laptop and the wireless connection works like a dream.

What is WRONG with Canonical? There are so many good things about Ubuntu, but this slow wireless connection problem is going to kill Ubuntu for me and a lot of other people.

Fast, efficient wireless connections ought to be an integral part of Ubuntu, as in Windows.

Sorry to go on and on like this, but this is a serious issue with me - and with a lot of other people as well.
If it is a driver issue, then it is very difficult to get drivers for every possible card out there, unless the companies producing them start to make drivers for linux. In the case of drivers it is not Canonical's fault.

---

### Post by grandtoubab on 2010-04-13
some say that Wicd is best manager than network-manager for wi-fi
[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)

---

### Post by wkulecz on 2010-04-13
As you can see DNS resolution is slow ~5 seconds, and from duplicate resolutions not an external caching issue:

```
wally@U-10:~/gst-learn$ date && nslookup msdn.com && date
Tue Apr 13 13:45:50 CDT 2010
Server:		128.157.5.23
Address:	128.157.5.23#53

Non-authoritative answer:
Name:	msdn.com
Address: 207.46.197.32
Name:	msdn.com
Address: 207.46.232.182

Tue Apr 13 13:45:55 CDT 2010


wally@U-10:~/gst-learn$ date && nslookup msdn.com && date
Tue Apr 13 13:45:58 CDT 2010
Server:		128.157.5.23
Address:	128.157.5.23#53

Non-authoritative answer:
Name:	msdn.com
Address: 207.46.232.182
Name:	msdn.com
Address: 207.46.197.32

Tue Apr 13 13:46:03 CDT 2010
wally@U-10:~/gst-learn$ 

```

Switching to opendns.com doesn't change anything.  

> wally@U-10:~/gst-learn$ date && nslookup msdn.com 208.69.38.150 && date
Tue Apr 13 13:53:41 CDT 2010
Server:		208.69.38.150
Address:	208.69.38.150#53

Non-authoritative answer:
Name:	msdn.com
Address: 207.46.232.182
Name:	msdn.com
Address: 207.46.197.32

Tue Apr 13 13:53:46 CDT 2010
wally@U-10:~/gst-learn$ 


Page loading is fast after the DNS delay.

---

### Post by psyke83 on 2010-04-13
> **LADmaticCA said:**
> Default route 192.168.1.1
Primary DNS 4.2.2.4
Secondary DNS 4.2.2.5

Can you give this a try? 

[LIST]
[*]Right-click on the Network Manager applet and choose Edit Connections.
[*]Edit your active internet connection, and go to the IPv4 Settings.
[*]Change 'Method' to 'Automatic (DHCP) addresses only'
[*]Enter into the 'DNS servers' field: 192.168.1.1
[*]Leave the 'Search domains' and 'DHCP client ID' entries blank.
[/LIST]

Restart your connection and let me know if it helps at all.

Note: to revert these settings, simply change the 'Method' back to 'DHCP'.

Here are two bugs which you should check out:
[Bug #417757]("https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/417757")
[Bug #94940]("https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940")

---

### Post by tjeremiah on 2010-04-13
> **LADmaticCA said:**
> Thanks for the replies.

I have tried firefox, opera, and chromium. All suffer the same. There are moments where these browsers operate as fast as they should, but eventually the hangs start up again. It also affects my ability to install programs using apt-get. I get a lengthy "waiting for headers" message before it finally starts.

I've tried open dns, google dns, disabling ipv6 in the kernel and browser. None of it worked. I guess it may be a router issue.:(

Im know im super late to the thread but the same thing has been happening to me since Karmic. It cant be my ISP because this only happens when running Ubuntu.

---

### Post by LADmaticCA on 2010-04-14
> **psyke83 said:**
> Can you give this a try? 

[LIST]
[*]Right-click on the Network Manager applet and choose Edit Connections.
[*]Edit your active internet connection, and go to the IPv4 Settings.
[*]Change 'Method' to 'Automatic (DHCP) addresses only'
[*]Enter into the 'DNS servers' field: 192.168.1.1
[*]Leave the 'Search domains' and 'DHCP client ID' entries blank.
[/LIST]

Restart your connection and let me know if it helps at all.

Note: to revert these settings, simply change the 'Method' back to 'DHCP'.

Here are two bugs which you should check out:
[Bug #417757]("https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/417757")
[Bug #94940]("https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940")

Thanks, but I have tried that already. I've added my information and have been watching those bugs a few days now, but I don't think they apply.

I threw Debian stable on this laptop, just to test performance on another old release, and as expected the internet works fine, very fast. I also tried the live cd of the latest Crunchbang alpha1, internet hangs again. So far all new distros with newer kernels perform badly.

---

### Post by psyke83 on 2010-04-14
> **LADmaticCA said:**
> Thanks, but I have tried that already. I've added my information and have been watching those bugs a few days now, but I don't think they apply.

I threw Debian stable on this laptop, just to test performance on another old release, and as expected the internet works fine, very fast. I also tried the live cd of the latest Crunchbang alpha1, internet hangs again. So far all new distros with newer kernels perform badly.

You could probably install a (recent, ext4-enabled) Debian kernel on your Ubuntu installation - then at least you can tell if it's a kernel issue, or configuration/userspace. Conversely, you may want to try the Lucid kernel on your Debian stable installation to see if there's any difference.

---

### Post by rjbennett on 2010-04-14
> **lvleph said:**
> If it is a driver issue, then it is very difficult to get drivers for every possible card out there, unless the companies producing them start to make drivers for linux. In the case of drivers it is not Canonical's fault.

I understand that, and I'm sorry I ranted about this issue. It's just that I think Ubuntu is terrific in so many ways that it's a real shame that so many people - like me - are having problems establishing a fast wireless connection on their laptops, when they use Ubuntu (the problem doesn't occur using Windows 7). I would have thought that something so crucial to using Ubuntu would be a top priority for Canonical, something that they would try to resolve somehow, unless those having this connection problem are only a very tiny minority - but even then.

Incidentally, I have a question. In one of the bug reports, this comment was made: "After searching around the system I found an entry in /etc/nsswitch.conf that caused me a little concern." The writer then goes on to explain how he changed a line in that configuration and was able to resolve the problem.

I know very little about Ubuntu, so my (stupid) question is this: I assume that "/etc/nsswitch.conf" is accessed on the terminal, but how? If I just type in "/etc/nsswitch.conf" (with no quotes), I get the response "Permission denied." So what do I do?

---

### Post by lvleph on 2010-04-14
> **rjbennett said:**
> 
Incidentally, I have a question. In one of the bug reports, this comment was made: "After searching around the system I found an entry in /etc/nsswitch.conf that caused me a little concern." The writer then goes on to explain how he changed a line in that configuration and was able to resolve the problem.

I know very little about Ubuntu, so my (stupid) question is this: I assume that "/etc/nsswitch.conf" is accessed on the terminal, but how? If I just type in "/etc/nsswitch.conf" (with no quotes), I get the response "Permission denied." So what do I do?

You will want to open this with an text editor by typing the following in CLI
[code]
sudo gedit /etc/nsswitch.conf
[code]
sudo tells it to give you super user permissions
gedit is the text editor
/etc/nsswitch.conf is the file to edit

---

### Post by psyke83 on 2010-04-14
> **rjbennett said:**
> I know very little about Ubuntu, so my (stupid) question is this: I  assume that "/etc/nsswitch.conf" is accessed on the terminal, but how?  If I just type in "/etc/nsswitch.conf" (with no quotes), I get the  response "Permission denied." So what do I do?

Yes, you need to open in a text editor.

If you're not comfortable with the terminal or editing configuration files, then a beta release may not be suitable for you.

---

### Post by wkulecz on 2010-04-14
I don't see how it can be a driver issue since all other network access is very fast, its only DNS lookups that are slow.

The nsswitch.conf or IP4/IP6 stuff did nothing for me, beyond wasting time trying.

This will be a showstopper for my wife's computer if it affects my home ISP.

---

### Post by LADmaticCA on 2010-04-14
^^ I actually experience this while using apt-get as well. "Waiting for headers" stays at 0% for a good 2 minutes before it starts fetching.

---

### Post by tjeremiah on 2010-04-14
I have tried every option given here in this thread without a solution. Browsing in Ubuntu is very frustrating. I can be looking to do the simplest of things like check email but I cant because it stalls and forces me to wait over 2 minutes sometimes to completely load. Sometimes it doesnt load at all. Right now its not a HUGE problem to send me running back to Windows 7 but if this keeps up, it just might.

---

### Post by Digikid on 2010-04-14
> **rjbennett said:**
> This issue of slow wireless connections ought to be a top priority for Canonical, but apparently it isn't. I have the impression that this issue has been around for a couple of YEARS or so. In order to solve this problem on my laptop, I've tried nearly all of the suggestions listed in this forum and other places, and nothing works.

If I run a cable to my laptop from my router, I get the speed I'm paying my ISP for - 20 Mbps. If I try to use Ubuntu's wireless connection. I get around half that, and sometimes much less.

I was curious to see what would happen with Windows 7. As test, after backing up my Ubuntu configuration, I installed Windows 7 on the laptop and the wireless connection works like a dream.

What is WRONG with Canonical? There are so many good things about Ubuntu, but this slow wireless connection problem is going to kill Ubuntu for me and a lot of other people.

Fast, efficient wireless connections ought to be an integral part of Ubuntu, as in Windows.

Sorry to go on and on like this, but this is a serious issue with me - and with a lot of other people as well.

They are just not listening to us.  Pure and simple.  It is way easier to point the finger at other companies drivers I guess.

This issue and the fact that it has been around for so long is pretty much got me tell ppl to NOT go with Ubuntu and to try something else instead.

Saddening. :roll:

---

### Post by psyke83 on 2010-04-15
> **LADmaticCA said:**
> Thanks, but I have tried that already. I've added my information and have been watching those bugs a few days now, but I don't think they apply.

I threw Debian stable on this laptop, just to test performance on another old release, and as expected the internet works fine, very fast. I also tried the live cd of the latest Crunchbang alpha1, internet hangs again. So far all new distros with newer kernels perform badly.

Sorry, but I disagree. From the descriptions you are giving of your system, it appears that you're suffering from the eglibc regression (and possibly also the mdns problem as well).

From bug #417757's [description]("https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/417757") (emphasis mine):
> 
In Karmic, DNS lookups take a  very long time with some routers, because glibc's DNS resolver tries to  do IPv6 (AAAA) lookups even if there are no (non-loopback) IPv6  interfaces configured. **Routers which do not repond to this cause the  lookup to take 20 seconds (until the IPv6 query times out).**
 *** PLEASE DO NOT COMMENT ON THIS BUG unless you have something  constructive to say. Everything that can be said has already been said,  and if you comment, you are just adding noise. Please let those that  actually know what they are doing concentrate on fixing this bug from  now on. ***
 **If disabling IPv6 or using good DNS servers like openDNS fixes the  problem, you are not dealing with this bug. **Please refrain from  complaining here in that case

Within the comments of the bug, it is mentioned that the timeout can vary (so the 20 second statement may be a generalization, and you could see shorter or longer timeouts). The above description fits your symptoms.

---

### Post by psyke83 on 2010-04-15
> **Digikid said:**
> They are just not listening to us.  Pure and simple.  It is way easier to point the finger at other companies drivers I guess.

This issue and the fact that it has been around for so long is pretty much got me tell ppl to NOT go with Ubuntu and to try something else instead.

Saddening. :roll:

Canonical did not write every piece of software included in Ubuntu, and sometimes, when upstream release new versions of software, they contain regressions when compared to previous versions. Since this "Canonical" entity (that you are so angry at) may not have created the original piece of software which is causing this problem, *and* they don't have intimate knowledge of the source code compared to the actual developers of said software, it can take time to identify and fix such issues. *Deal with it*. 

Instead of complaining, I suggest that you take some time to learn about open-source development and learn about the difference between upstream and downstream development.

---

### Post by Digikid on 2010-04-15
> **psyke83 said:**
> Canonical did not write every piece of software included in Ubuntu, and sometimes, when upstream release new versions of software, they contain regressions when compared to previous versions. Since this "Canonical" entity (that you are so angry at) may not have created the original piece of software which is causing this problem, *and* they don't have intimate knowledge of the source code compared to the actual developers of said software, it can take time to identify and fix such issues. *Deal with it*. 

Instead of complaining, I suggest that you take some time to learn about open-source development and learn about the difference between upstream and downstream development.

:lolflag::lolflag::lolflag::lolflag::lolflag:

Riiiight......PO mate.

Read my post again....they think about the part about it being YEARS that this bug has been around.

---

### Post by psyke83 on 2010-04-15
> **Digikid said:**
> :lolflag::lolflag::lolflag::lolflag::lolflag:

Riiiight......PO mate.

Read my post again....they think about the part about it being YEARS that this bug has been around.

The OP's post may be different to yours (the two main candidates being the mdns and eglibc bugs). If you read those reports you will see that one is actually a regression, and another appears to be an inherent flaw in the way that mdns works.

Saying that the bug has been around for years is hyperbole, and again, may not be within Canonical's control to fix without help from upstream.

---

### Post by LADmaticCA on 2010-04-15
> **psyke83 said:**
> Sorry, but I disagree. From the descriptions you are giving of your system, it appears that you're suffering from the eglibc regression (and possibly also the mdns problem as well).

From bug #417757's [description]("https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/417757") (emphasis mine):
Within the comments of the bug, it is mentioned that the timeout can vary (so the 20 second statement may be a generalization, and you could see shorter or longer timeouts). The above description fits your symptoms.

Interesting. But why would my desktop also running lucid not be affected, if it is indeed the eglibc regression? Is it specific to certain wireless chipsets?

---

### Post by psyke83 on 2010-04-15
> **LADmaticCA said:**
> Interesting. But why would my desktop also running lucid not be affected, if it is indeed the eglibc regression? Is it specific to certain wireless chipsets?

I don't recall that you mentioned having a desktop running Lucid, I'll have to re-read the whole thread. No, the regression would not relate to wired or wireless chipsets. Have you tried using the ethernet connection of your laptop to see if the problem also exists?

On my laptop, my wireless network was very slow due to the buggy rt2500pci driver *and* the mdns bug (the driver causing low throughput and delays, and the mdns problem causing even slower DNS resolution). Using a Windows driver and editing /etc/nsswitch.conf as mentioned in the bug report, solved all the problems for me.

If you can connect your laptop using ethernet and experience no delays, then you can consider it confirmation that it's either your wireless driver, or router's wireless support that's buggy.

---

### Post by LADmaticCA on 2010-04-16
> **psyke83 said:**
> I don't recall that you mentioned having a desktop running Lucid, I'll have to re-read the whole thread. No, the regression would not relate to wired or wireless chipsets. Have you tried using the ethernet connection of your laptop to see if the problem also exists?

On my laptop, my wireless network was very slow due to the buggy rt2500pci driver *and* the mdns bug (the driver causing low throughput and delays, and the mdns problem causing even slower DNS resolution). Using a Windows driver and editing /etc/nsswitch.conf as mentioned in the bug report, solved all the problems for me.

If you can connect your laptop using ethernet and experience no delays, then you can consider it confirmation that it's either your wireless driver, or router's wireless support that's buggy.

Do you know if there's a Windows driver for Atheros cards? I tried finding one before but was unsuccessful, probably because my card is older AR2413. 

Could everyone else still having a problem post what driver their card is using?

```
lshw -C network
```

Check the last row where it says, configuration.

---

### Post by psyke83 on 2010-04-16
> **LADmaticCA said:**
> Do you know if there's a Windows driver for Atheros cards? I tried finding one before but was unsuccessful, probably because my card is older AR2413. 

Could everyone else still having a problem post what driver their card is using?

```
lshw -C network
```Check the last row where it says, configuration.

The AR2413 chipset seems to be generally labeled as AR5005G (see [here]("http://www.atheros.com/pt/AR5005G.htm")). You can find Windows XP drivers on [this]("http://www.atheros.cz/download.php?atheros=AR5005G&system=1") page.

---

### Post by LADmaticCA on 2010-04-16
^^ Hey thanks for that! I'll see if I can get ndiswrapper going and test the results.


Edit* Wooo! That appears to have done it. I've got the Windows driver running and so far no hangs! Thanks again psyke83.

---

### Post by rjbennett on 2010-04-16
> **rjbennett said:**
> This issue of slow wireless connections ought to be a top priority for Canonical, but apparently it isn't. I have the impression that this issue has been around for a couple of YEARS or so. In order to solve this problem on my laptop, I've tried nearly all of the suggestions listed in this forum and other places, and nothing works.

If I run a cable to my laptop from my router, I get the speed I'm paying my ISP for - 20 Mbps. If I try to use Ubuntu's wireless connection. I get around half that, and sometimes much less.

I was curious to see what would happen with Windows 7. As test, after backing up my Ubuntu configuration, I installed Windows 7 on the laptop and the wireless connection works like a dream.

What is WRONG with Canonical? There are so many good things about Ubuntu, but this slow wireless connection problem is going to kill Ubuntu for me and a lot of other people.

Fast, efficient wireless connections ought to be an integral part of Ubuntu, as in Windows.

Sorry to go on and on like this, but this is a serious issue with me - and with a lot of other people as well.

I want to apologize for my earlier rant (quoted above) about Ubuntu and Canonical. I was completely wrong. I discovered the reason why my WLAN connection was so slow, and I corrected the problem. My wireless connection works perfectly now - 20 Mbps - with Lucid Lynx. The problem had absolutely nothing to do with Ubuntu or Canonical.

For the information of anyone interested, the problem was this: I noticed that Ubuntu Network Manager listed two wireless connections, my normal one and another that somehow became listed there when a friend of mine plugged his computer into my router at home, in order to communicate with his office. Even though I wasn't using that connection, the fact that it was there interfered with Ubuntu's capability of connecting to my router at full speed. When I removed that second connection from the list shown by Network Manager, leaving only my normal WLAN connection, I discovered I can connect wirelessly to my router with Lucid Lynx at the expected speed, 20 Mbps.

Again, I was wrong to be so critical, and again I apologize.

---

### Post by psyke83 on 2010-04-16
> **LADmaticCA said:**
> ^^ Hey thanks for that! I'll see if I can get ndiswrapper going and test the results.


Edit* Wooo! That appears to have done it. I've got the Windows driver running and so far no hangs! Thanks again psyke83.

Glad to hear it - has the Windows driver resolved the slow browsing speed?

If I were in your position, I would try some experiments with the ath5k driver to isolate the problem. Using the Windows driver is a good workaround, but it would be ideal if you could discover your issue and report a bug, so that the speed problem can get fixed in the open driver.

Look at the module parameters for ath5k:
```
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           all_channels:Expose all channels the device can use. (bool)

```It's possible that the chipset's built-in hardware encryption is slow/buggy, so disabling it may improve speed.

Here's how to manually unload ndiswrapper/ath5k and reload the ath5k module with the parameter:
```
$ sudo rmmod -w ndiswrapper ath5k
$ sudo modprobe ath5k nohwcrypt
```Or if you later discover that encryption is disabled by default, this will enable it:
```
$ sudo rmmod -w ndiswrapper ath5k
$ sudo modprobe ath5k nohwcrypt=false
```

---

### Post by tjeremiah on 2010-04-17
> **LADmaticCA said:**
> ^^ Hey thanks for that! I'll see if I can get ndiswrapper going and test the results.


Edit* Wooo! That appears to have done it. I've got the Windows driver running and so far no hangs! Thanks again psyke83.

Can you specify which you downloaded and how you managed to install it, please :)

---

### Post by razorbuzz on 2010-04-17
> **psyke83 said:**
> Can you give this a try? 

[LIST]
[*]Right-click on the Network Manager applet and choose Edit Connections.
[*]Edit your active internet connection, and go to the IPv4 Settings.
[*]Change 'Method' to 'Automatic (DHCP) addresses only'
[*]Enter into the 'DNS servers' field: 192.168.1.1
[*]Leave the 'Search domains' and 'DHCP client ID' entries blank.
[/LIST]

Restart your connection and let me know if it helps at all.

Note: to revert these settings, simply change the 'Method' back to 'DHCP'.

Here are two bugs which you should check out:
[Bug #417757]("https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/417757")
[Bug #94940]("https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940")


Psyke83 - That corrected my problem instantly.  Full DHCP had the extended (anywhere from 10-30second delay in lookups), as did setting a static IP.  Automatic (DHCP) Address Only is the only way working without the long delay, but my need for a static IP on this machine creates a problem. 

Is this the regression in glibc, or something else?  Thoughts?

-RB

---

### Post by grandtoubab on 2010-04-17
[http://ubuntuforums.org/showpost.php?p=9107465&postcount=34](http://ubuntuforums.org/showpost.php?p=9107465&postcount=34)
[http://code.google.com/p/namebench/](http://code.google.com/p/namebench/)

---

### Post by dentaku65 on 2010-04-17
> **LADmaticCA said:**
> Thanks for the replies.

I have tried firefox, opera, and chromium. All suffer the same. There are moments where these browsers operate as fast as they should, but eventually the hangs start up again. It also affects my ability to install programs using apt-get. I get a lengthy "waiting for headers" message before it finally starts.

I've tried open dns, google dns, disabling ipv6 in the kernel and browser. None of it worked. I guess it may be a router issue.:(

Silly suggest try here, for Firefox:
Edit -> Preferences -> Network -> Connection -> Settings
Select "No Proxy" option and restart firefox

---

### Post by LADmaticCA on 2010-04-17
@psyke83
Sure I'll try that and see what happens. How did you view the parameters for the module?

@tjeremiah
I just downloaded the driver on [this page]("http://www.atheros.cz/download.php?atheros=AR5005G&system=1"). and followed the directions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

---

### Post by psyke83 on 2010-04-17
> **LADmaticCA said:**
> @psyke83
Sure I'll try that and see what happens. How did you view the parameters for the module

```
$ modinfo ath5k
```

---

### Post by psyke83 on 2010-04-17
> **razorbuzz said:**
> Psyke83 - That corrected my problem instantly.  Full DHCP had the extended (anywhere from 10-30second delay in lookups), as did setting a static IP.  Automatic (DHCP) Address Only is the only way working without the long delay, but my need for a static IP on this machine creates a problem. 

Is this the regression in glibc, or something else?  Thoughts?

-RB

That was just a hunch and I'm not sure if it's related to either of those bugs.

My router (DI-524 B4) is configured with two DNS servers. However, when I connect to it via NetworkManager, it assigns the first DNS server from the router configuration, and then assigns the router's address as the second DNS server (and thus ignores the second DNS server in the router configuration).

I think this should not happen; NetworkManager should have assigned the first and second DNS servers from the router's configuration. However, as you can see, using your router's IP address as the sole DNS server works fine.

---

### Post by LADmaticCA on 2010-04-18
> **psyke83 said:**
> ```
$ modinfo ath5k
```

Dude you're too good. From my tests so far, the nohwcrypt parameter has a definite effect on the browsing performance. If I do *modprobe ath5k* with no parameter, I get those hangs I was experiencing earlier. If I do *modprobe ath5k nohwcrypt* while a page is hanging, it will automatically load as it should. :) Great job! Now I just need to find out how to make my ath5k module automatically load with that parameter on boot. I'll keep testing it to be certain.

---

### Post by psyke83 on 2010-04-18
> **LADmaticCA said:**
> Dude you're too good. From my tests so far, the nohwcrypt parameter has a definite effect on the browsing performance. If I do *modprobe ath5k* with no parameter, I get those hangs I was experiencing earlier. If I do *modprobe ath5k nohwcrypt* while a page is hanging, it will automatically load as it should. :) Great job! Now I just need to find out how to make my ath5k module automatically load with that parameter on boot. I'll keep testing it to be certain.

You may want to consider one more diagnostic step: install the backported wireless drivers to see if a newer version solves the problem:

```
$ sudo apt-get install linux-backports-modules-wireless-lucid-generic
```Reboot and try the ath5k driver *without* any custom module parameters and see if the problem still exists.

Anyway, once you've decided that you want to keep using the "nohwcrypt" option, you just need to create a new file in /etc/modprobe.d/ with the text "options ath5k nohwcrypt".

This should do it for you automatically:
```
$ sudo sh -c "echo 'options ath5k nohwcrypt' >/etc/modprobe.d/custom-wireless.conf"
```You should also ensure that you have removed the ndiswrapper driver, as it would override the ath5k kernel module.

I recommend that you check Launchpad to see if a similar bug is already filed, then add your findings. If no similar bugs exists, create a new one... :)

---

### Post by krazyd on 2010-04-18
Hi LADmaticCA

I've had the same issue since karmic (also using ath5k). It's definitely down to ath5k, because disabling that module and using my wireless USB stick works fine (rt73usb chip). I believe i'm seeing this bug:
[https://bugzilla.redhat.com/show_bug.cgi?id=506372](https://bugzilla.redhat.com/show_bug.cgi?id=506372)

Pinging my router resulted in up to 60% packet loss, with minimum latency of ~50ms!

Neither nohwcrypt nor linux-backports-modules-wireless-lucid-generic improved the situation - the only thing which worked was installing the 2.6.33 kernel from the mainline kernel-ppa.

I now get 0% packet loss with <5ms latency. Give it a shot.

---

### Post by LADmaticCA on 2010-04-18
> **psyke83 said:**
> You may want to consider one more diagnostic step: install the backported wireless drivers to see if a newer version solves the problem:

```
$ sudo apt-get install linux-backports-modules-wireless-lucid-generic
```Reboot and try the ath5k driver *without* any custom module parameters and see if the problem still exists.

Anyway, once you've decided that you want to keep using the "nohwcrypt" option, you just need to create a new file in /etc/modprobe.d/ with the text "options ath5k nohwcrypt".

This should do it for you automatically:
```
$ sudo sh -c "echo 'options ath5k nohwcrypt' >/etc/modprobe.d/custom-wireless.conf"
```You should also ensure that you have removed the ndiswrapper driver, as it would override the ath5k kernel module.

I recommend that you check Launchpad to see if a similar bug is already filed, then add your findings. If no similar bugs exists, create a new one... :)

Okay, I tried the backports with the generic ath5k and the problem was still present. I created the custom wireless file and removed the ndiswrapper, now all is working well. :) Thanks again! And thank you to everyone else that had suggestions. I will check launchpad for an existing bug.

---

### Post by MarkieB on 2010-04-19
no longer participating in ubuntuforums.org

---

### Post by Agent0013 on 2010-04-20
> **JW3 said:**
>  
 
1) deinstall libnss-mdns package:
```
sudo apt-get remove libnss-mdns
```2) make sure that the file /etc/nsswitch.conf does not contain the line
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
but instead has the line:
hosts:          files dns
``` 

 I have had painfully slow web browsing for months an a work computer that I put Ubuntu on. I tried all of the ipv6 disabling in firefox and in the kernel without success. I also tried the Open DNS and other fixes. Eventually I started using firefox in a Windows XP virtual machine and that was faster than the local browser. Other browsers were just as bad.  

Anyway, the fix listed above has worked for me. This is a wired connection, so it isn't only for wireless problems. Thanks for pointing me into the correct location.

---

### Post by Digikid on 2010-04-23
> **MarkieB said:**
> it's unfortunate that there are so many posts close to the top of the thread calling the Firefox ipv4/ipv6 setting a 'red herring' - well it may be for some people :)

Me it eventually bugged me sufficiently to look for the answer, one of the top results was a Mozilla forums result, that refers to the about:config setting
```
network.dns.disableIPv6
```as people have said, it looks as though many ISP's have very limited support for ipv6, notably including Orange in France, possibly the largest ISP in the country! :P

ps that google DNS optimization tool seems not to check ipv6 support either

so even though it may be a red herring for some, it may be worth trying

Best regards

[now happily browsing at normal speed]

Problem is....that does not work.

---

### Post by wkulecz on 2010-04-23
On 8.04 (where I'm typing from) dns is near instataneous (usually under 1 second) on obscure (non-cached) sites.  I have the line:

files mdns4_minimal [NOTFOUND=return] dns mdns4

in my /etc/nsswitch.conf file.



But with the same hardware and network connection (dual boot) and dns lookups run ~5 secondsas measured by:

date && nslookup obscure.site && date

when I'm in Lucid.


I've removed the nsswitch package and have only 

hosts     files, dns

in my 10.04 /etc/nsswitch.conf file.


I've no idea what is going on here, it is not confined to Firefox as the commandline timing of a dns lookup shows.

---

### Post by wkulecz on 2010-04-23
Follow up.

I just rebooted into 10.04Beta and there were a lot of updates waiting for me after two days of this box running 8.04 and my date && nslookup obscure.site && date DNS lookup times are now back under 1 second, so perhaps its fixed now!

---

### Post by DodgeV83 on 2010-04-23
Here was my solution for the same problem in 9.10.  I haven't experienced this problem in 10.04 yet, so maybe it's fixed...

This 100% fixed my problem! Posted by mikio at

[http://ubuntuforums.org/showthread.php?t=1283146](http://ubuntuforums.org/showthread.php?t=1283146)


1. In /etc/dhcp3/dhclient.conf add the following line:

prepend domain-name-servers 208.67.222.222,208.67.220.220;


2. In /etc/nsswitch.conf edit this line

hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4

to this

hosts: files dns

I'm not sure which one of these did it to be honest, but it's fixed!

Note:  To edit those files, open a terminal and type "sudo gedit" then the file:

```
sudo gedit /etc/dhcp3/dhclient.conf
```

```
sudo gedit /etc/nsswitch.conf
```

Edit:  Then reboot the machine.

---

