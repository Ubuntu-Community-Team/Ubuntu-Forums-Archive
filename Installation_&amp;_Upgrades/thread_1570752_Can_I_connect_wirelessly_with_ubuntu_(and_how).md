---
title: "Can I connect wirelessly with ubuntu (and how)"
date: 2010-09-08
forum: Installation &amp; Upgrades
---

### Post by Lakeside5 on 2010-09-08
Well, I figured I would start a new thread, as I think the title should change.  But this is what I've gone through so far:  [http://ubuntuforums.org/showthread.php?t=1558822&page=2](http://ubuntuforums.org/showthread.php?t=1558822&page=2)

Since then I have purchased a new cable and connected the desktop to the router with it.  I have renewed the ip address (in dos command).  I have a connection (even shows it on the icon,  eth0 and it says it's connected but I can't surf the net. My local Staples didn't even have the regular pci (ipc...not sure what it's called, just the regular ethernet card, as my machine is about 5 years old) but they did have a wireless one, which against my better judgement I bought.  It is a usb port one, just plugs in, so not hard to install.  Before I open it, making it non returnable,  should I even use it?  I read that ubuntu has issues, and so, must be connected physically to the router initially, and won't connect wirelessly right off the bat.  If someone advises me though, that it CAN connect wirelessly, would they be able to tell me how to do that please? Like what are the commands in the terminal? thanks very much.

---

### Post by JBAlaska on 2010-09-08
Please post the make/model of your wireless usb device.

---

### Post by Lakeside5 on 2010-09-08
Thank you JBAlaska, I just bought it and haven't opened it yet in case it is not the right one.  It is a D-link Wireless N 150 USB Adapter.

---

### Post by JBAlaska on 2010-09-08
Sorry It took me so long to get back to you. As far as I know the "N 150" refers to the speed of the device, it should have a designation starting with "DWA" as an example the "DWA-125" which uses a Ralink chipset and the rt3070sta driver.

---

### Post by Lakeside5 on 2010-09-08
lol  that`s ok. I should have said, it is a DWA-125  JBAlaska, come baaaack lol

---

### Post by JBAlaska on 2010-09-09
It seems that wireless adapter will work with Ubuntu. You might get lucky and have it work "out of the box" or it may require you to blacklist other drivers and install the ralink rt3070sta driver(you should NOT need Internet access for this).

If you decide to use this adapter, I can help you make it work if you have a problem.

I'm using a WUSB600N that uses a similar ralink chipset and I'm very happy with the reception and speed.

---

### Post by Lakeside5 on 2010-09-09
I really REALLY appreciate your help on that JBAlaska. I actually wanted to have a regular adapter installed but they didn't seem to have one, and also the way my box was built for me, the adapter tha's in there now doesn't look familiar like the ones I saw in the tutorials showing how to replace them, mine is some small box shaped thing that I wouldn't want to try and mess with, and can't afford to pay anyone right now. Also Staples didn't have one for my machine! So I have to use the wireless flash and hopefully with your help I can get it to work. Thanks.

---

### Post by oldfred on 2010-09-09
Most of the wired adapters nowadays are built into the motherboard, so you do not have a separate board plugged into the pci slot. Are you sure the wired is not working. It will be faster and easier to use. 

I alway plug my portable into a wired connection to get updates as it is a lot faster on large downloads. Just surfing the net is about the same speed as I do not type any faster whether the connection is wired or not.:)

---

### Post by Lakeside5 on 2010-09-09
Well  I'm still wondering about that because the wired adapter worked before when I had Hardy Heron on it.  After I installed 10.04 I'm haing problems.  I haven't opened the wireless usb network adapter yet, so it's still returnable. I was walked through a few things by my isp helpdesk to ty and fix the connection, so the idea about the internal adapter not working was through process of elimination I guess. If you can think of other things to test, or edit, please let me know.  I would like to use the original adapter (the one in my computer) too. thanks

---

### Post by ronparent on 2010-09-09
.....and sometimes the plug in is the only way to get the wireless driver you need to connect.

---

### Post by Lakeside5 on 2010-09-09
So then, what should I do next, guys? I bought a brand new cable,(connectiong desktop to router) and a wireless usb adapter  (still in box) and have a connection showing (eth0) which I edited, but maybe incorrectly, and that's about it lol

---

### Post by oldfred on 2010-09-09
What do these show.

ifconfig
sudo ethtool eth0

I do not recommend posting HWadd, so edit that out when you paste it.

---

### Post by Lakeside5 on 2010-09-09
I tried 'sudo ethtool eth0 twice but it says command not found.  Also, I can't cut and paste as I'm on the laptop now responding to this.  There's a lot of output, what are the main things you need me to show? thanks.
*oops, I just read some other threads, and maybe I don't have ethtools installed, and have to install them to run that command?  Or, maybe does it mean that my ethernet card is dead? Should I open the new wireless plug-in adapter and put it in the usb slot?

---

### Post by ronparent on 2010-09-09
To install ethtool open a terminal and enter:

> sudo apt-get install ethtool

Then continue as oldfred suggested.:)

---

### Post by Lakeside5 on 2010-09-09
D'oh!

---

### Post by Lakeside5 on 2010-09-09
Ran the command, then 'building dependency tree, Reading state infromation..done  E: Couldn't find package ethtool'
*edity* I read elsewhere and decided to to  'apt-get update' thinking maybe I could get ethtools that way and..it spewed out many lines, about each missing package, they all say 'something wicked happened resolving 'security.ubuntu.com http(-5 No address associated with hostname' (each line of course with a different package lie 'ca.archive.ubuntu.com:http' etc.  What does that mean?

---

### Post by oldfred on 2010-09-09
D'oh!

If you are not on INTERNET it will not update from internet. But I thought it was already installed.

What does any of these commands show. Also link to another thread where pytheas22 seems to know a lot.

Lots of config advice by pytheas22
[http://ubuntuforums.org/showthread.php?t=1505697](http://ubuntuforums.org/showthread.php?t=1505697)
cat /etc/network/interfaces
cat /etc/NetworkManager/nm-system-settings.conf
dmesg | grep -e eth0 -e bcm
ifconfig -a
lspci -nn

To see drivers used:
lshw -C Network

---

### Post by Lakeside5 on 2010-09-09
Yes I was kind of thinking that (no internet-no update, no update, no internet lol)  For the first two commands you listed I got 'No such file or directory',  and for dmesg|grep... I got:
[2.004177] eth0: VIA RHINE II at 8a:00:30, IRQ23
[2.004895]eth0: MII PHY found at addres1, status, 0x786d advertising 05e1 Link 41e1
[14.045367] eth0: link up 100Mbps, full-duplex, 1pa 0x41E1
[24.18015] eth0: no IPv6 routers present

the next two commands list a loto f things, not sure what is pertinent, the lspci one lists a lot of hardware (audio contoller, Ethernet controller etc.) and lshw -C Network shows:  description: Ethernet interface
product: VT6102 (Rhine-II
vendor: VIA Technologies, Inc
physical id: 12
bus info: pci@0000:00:12.0
logical name: eth0
version: 78
serial: 00:12:8f:8a:00:30
width: 32 bits
clock: 33MHz
capabilities: bus_mastger cap_list ethernet physical
configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.1.156 latency=32 maxlatency=8 mingnt=3 multicast=yes
resources: irq:23 ioport:e800(size=256)memory:febffc00-febffcff

---

### Post by oldfred on 2010-09-09
This says it is working:
 eth0: link up 100Mbps

Now it may be misconfigured. 

Did you change from DHCP to fixed address?
ip=192.168.1.156

My system uses 50 address' starting at 100 for DHCP.

This was my fixed settings:

---

### Post by Lakeside5 on 2010-09-09
That was something I tried way back.  I went into the connection (eth0) and edited it at ipv4, using the 'manual' option for drop down box, and entered 192.168.1.156 for ip address (was 192.168.1.100 on the wireless laptop when I checked with ipconfig (windows) and someone told me to use a value just outside of the router's range, the router's range was  192.168.1.1-149, so I chose 156, maybe there is a better number? The weird thing that bothers me, and may be the problem, is that when I enter the last box, the gateway, 192.168.1.1, it never STAYS.  All the other numbers stay, but it keeps defaulting to 000.000.000.000.  I don't know why. Does it have something to do with my not being able to get updates?

---

### Post by oldfred on 2010-09-09
That should be the router address. Are you sure the default range for DHCP was 1-149? You also may want to look at router settings. That address cannot be zeros.

I might try DHCP again. Does router otherwise work if not, try reseting router.

---

### Post by Lakeside5 on 2010-09-09
I just went into my router,  it says 'start address: 192.168.1.100,  and 'number of ip addresses: 50,  and DHCP range: 100-149,(sorry, was a typo before, had said 1-149 but meant 100-149)  and the ip address is 192.168.1.1
The router works, I guess, becaue my laptop (which I'm using to post to you) is connecting wirelessly to it, so I am really stumped. What I meant about the 000.000.000  is that, that is what keeps showing up in the 'gateway' box when I edit the eth0 connections.  The other numbers stay, like ip address, and dns servers and netmask, but not that one (gateway) Time and time again I go in to set it to 192.168.1.1 and it keeps showing up later as all zeros! grrrrrrrrrr

---

### Post by oldfred on 2010-09-09
I used to compare ipconfig in windows command line and ifconfig in Ubuntu and see what differences there were. They are not quite identical but give a lot of the same info.

---

### Post by Lakeside5 on 2010-09-10
For Windows ip address says: 192.168.1.100, and for ubuntu it says  192.168.1.156 (which is what I set it to in 'edit connections',  windows subnet mask is 255.255.255.0 which is the same for ubuntu (only it calls it 'mask') and for the windows gateway it is 192.168.1.1 of course, and in Ubuntu it doesn't show anything called 'gateway', but there is a 'Bcast' that is 192.168.1.255,  if that helps any.

---

### Post by oldfred on 2010-09-10
If windows has .100 then it is using the DHCP. Have you tried that again?

Also have you right clicked on the icon with a plug on the upper right top panel?

---

### Post by Lakeside5 on 2010-09-10
I just tried that a few hours ago, switched it from 'manual' to DHCP and it still says 'can't load page' when I try to surf.  Just don't know what to think.

---

### Post by oldfred on 2010-09-10
When you right click on the icon on the upper right in the top panel, What does connection information show.

---

### Post by Lakeside5 on 2010-09-11
I will have to tell you when I get home tonight (a few more hours) as I've been babysitting since 8 this morning and I'm still here lol  Going to try it and post then, it is 12:41 am here now, so about 3 am maybe, few hours from now.
CONNECTION INFORMATION (from icon): interface:   Ethernet:           (eth0)
                                                 hardware address: O0:13:8f:8A:0      
                                                 Driver:           via-rhine
                                                 speed:             100Mb/s
                                                  
ip Address: 192.168.1.156
Broadcast Address: 192:168:1:255
Subnet Mask:       255:255:255:0
Primary DNS:       216:211:26:14

I've tried changing the ip address and gateway, I changed the ip address to 192.168.1.200 and the gateway to 192.168.1.11, which is what shows up when I right click the connection icon for info about the connection. And I have a working connection, but for SOME reason I still can't get web pages.

---

### Post by Lakeside5 on 2010-09-11
Just a thought, but should I uninstall the ubuntu (just a thought) and download another one, and reinstall? Just a thought (and also, how would I uninstall, not sure) Another thing I noticed, was that the clock icon at top right corner, shows tht wrong time.  When I was instlling ubuntu and had to set my local time, there is a map that you pick your area, and a drop down, so I was on the right place on the map, and picked my town which was listed, BUT the current time that it showed as being the time for that area, was not the time it was here, but I picked it anyway as that was my town.  Maybe I can't surf the net because the clock it wrong?  I just have no idea >.<

---

### Post by oldfred on 2010-09-12
Sometimes a reinstall is the solution. Make sure the md5 sum is correct and burn at the slowest speed your CD burner allows. I now like using USB keys are they are reusable.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Lakeside5 on 2010-09-12
Thanks Oldfred, I think I'll try. But there is no working dvd drive, burner etc.  I used a flash drive to install.  Also, I'm not sure now to uninstall the whole thing that's in there now and start over. I didn't have this problem when I installed the server edition before (hardy) just this Lucid desktop one.

---

### Post by oldfred on 2010-09-12
You do not have to uninstall, just use manual install and choose the same partition for / (root). You then reformat and the old one is gone.

---

### Post by Lakeside5 on 2010-09-12
k, I will try that, wish me luck.
When I used Hardy, it was 64-bit I think. this time I used the 32-bit. I was never sure which one to use, even asking for advice because I got lots of replys explaining why I should use either one. I  don't know if that would cause problems?

---

### Post by Lakeside5 on 2010-09-12
Never mind my previous posts, I kept rebooting and now somehow I am at the 'install screen', reading to go through the 7 steps.  Hope I do it right!
Whoo hooooo!!! At the risk of jinxing, all is well. I have it installed on this computer and was instantly 'surfing' after a restart.  That's right I am posting in this forum on this computer using Lucid Lynx 10.04 :)  It was almost too easy, as it was just 7 simple steps, and I didn't have to enter any 'numbers' or edit connections or ANYTHING.  So THAT kinds has me worried but anyway..Now I guess I have to start another thread to get this desktop distro to handle webserving lol  I am so grateful for all the patient and helpful people (as is found on this forum) especially to oldfred.  I learned at bit more this time. Thanks.

---

### Post by oldfred on 2010-09-12
Glad you got it working. :)

Cannot help you on web serving, suggest the new thread as someone here can help.

---

### Post by Lakeside5 on 2010-09-13
Already found a great ubuntu link for that. Should go ak (crosses fingers lol)

---

