---
title: "Lucid/KDE problems"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by xeddog on 2010-04-10
I didn't really know which is the proper forum to post this, but it involves either Lucid Beta 2, or KDE 4.4.2.  

I had installed Ubuntu Lucid Beta 1 on my machine (see below for details) and had been keeping up with the updates.  It was working fine with no major problems except for the wheel on my microsoft mouse wasn't working.  Other than that, all was good.  Then I did something that I normally don't do.  Two things at once.  First, I installed the latest round of updates which should have brought me up equivalent to Beta-2

I also read about KDE 4.4.2 being out and some people really liked it, and since I had not tried KDE in some time, I thought I'd give it another shot.  SO I updated my sources with the ppa information and installed KDE 4.4.2.  THEN I rebooted.

All was ok for a while.  I think there were some issues with the nVidia driver, but I worked through them and had things pretty much the way I wanted them.  I was messing with some of the panels, and trying to get compositing working so I could use Docky when my display just went ape poop.  Ended up with the secondary display being blank, and the primary display had the Kubuntu desktop on it, but split in half vertically and reversed.  The left half of the screen was supposed to be on the other side.

I rebooted and selected my Gnome desktop again, but the display was still hosed.  I noticed when logging out and back in again that on the login panel after I put in my userid, the "Failsafe Gnome" desktop was pre-selected.   I could select to boot into the Gnome desktop, but things just didn't seem right.  When I logged out and went back to the login panel, "Failsafe Gnome was pre-selected again so it seems like I am stuck with the failsafe mode.

Anyway, I rebooted into recovery mode, went to the root console, and re-installed the nVidia 195.36.15 driver.  I rebooted to the Gnome desktop again and the display was back to normal again, but I had no network connectivity.  Well, I had a little.  I was able to mount an nfs share that was on another computer, but that is all.  There was two other computers that I still could not mount, and I had no apparent Internet connectivity.  


I ran:
> sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:24:1d:c4:ce:50  
          inet addr:10.1.1.35  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fec4:ce50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:78 errors:0 dropped:0 overruns:0 frame:0
          TX packets:212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17924 (17.9 KB)  TX bytes:22947 (22.9 KB)
          Interrupt:30 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:161 errors:0 dropped:0 overruns:0 frame:0
          TX packets:161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13136 (13.1 KB)  TX bytes:13136 (13.1 KB)

and as you can see, it looks ok except for the error counts.  I also ran:
> route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         10.1.1.1        0.0.0.0         UG    100    0        0 eth0


which also looks good.  I did some pings and found that if I used an ip address I could ping, but if I used a name then I could not.  So I looked at /etc/resolv.conf and the resolver address was nfg.  Fixed that and now I seem to be back online again.  

So after all of this, I guess there are some reported problems with the nvidia drivers using KDE.  I still need to research this more, but why did my /etc/resolv.conf get hosed, why isn't network manager being displayed in the notification area, and why am I stuck using Failsafe gnome desktop?  I am wondering if I am going to have all of these same problems if I start KDE again.

xeddog

Machine stats:
GigaByte EX58-UD3R motherboard
Intel I7-920 CPU with 6GB DDR3 memory
Nvidia Geforce 9500 GT PCI-Express graphics
Dual monitors - Primary is 23" LCD widescreen, secondary is 4:3 CRT
Drive sda is 1TB sata, and sdb is 300GB IDE
Ubuntu Lucid 64-bit installed on sda, and KDE added on it.
Ubuntu Lucid 64-bit also installed on sdb, but no KDE and it has not been affected.

---

### Post by howefield on 2010-04-11
Ask a staff member to move it to this one...

[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

Edit:
On second thoughts, perhaps not, if all was well with Lucid, and the problems only started when you were messing around with other stuff, probably as well in here.

---

