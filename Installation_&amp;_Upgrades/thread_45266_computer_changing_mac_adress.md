---
title: "computer changing mac adress"
date: 2005-06-29
forum: Installation &amp; Upgrades
---

### Post by RadixLecti on 2005-06-29
Hi,

I'm experiencing a bit of a problem, and I´m not sure whether it's hard or software related.

My computer keeps changing mac adresses (or so my ISP tells me), and getting my internet connection shut down. My ISP shuts down a connection once a user has spammed more than 20 different mac adresses. This has happened 3 times now this last month.

My ISP tells me it's due to the ethernet card being close to dying, so I exchanged it with another. Today, 4 days after changing, I was my i-net connection was shut down again.

This is something that never happened while I was running XP (though enough happened to make me migrate to linux).
Every time this happens, my grub goes to hell, as does the filesystem on the partitions that houses ubuntu (strangely, two other partitions I have around for storage are unaffected). 

I've tried fixing grub both via a live CD and via the ubuntu installer, to no use. Maybe due to lack of knowledge, I've been forced to reinstall.

So, my question is two-fold: Is there something in ubuntu that changes mac adresses, or is it more likely that my hardware is to blame?

(I'm very much a linux noob, I have no idea what I should add to this... if there's anything you want to look at, just tell me)

PS. How do I find out the mac adress on a linux OS? DS.

---

### Post by mingus on 2005-06-29
You are sure this is the *mac* address?

The mac address is in the device itself.  It is unique, put there by the manufacturer.  I can't think of any way to change it.  I suppose it's possible for a software transmission that incl the address - it is probably incl in the TCP packets sent from the adapter to the gateway router - to get garbled or intercepted and mangled.   Never heard of that and would be extremely diff to do intentionally.

Or of course, unless the adapter itself is reporting the address erroneously because it is dying, as your ISP suggested.

You can see your network adapter's address easily.  In a terminal do $ifconfig - the mac is the 12-char field labeled "HWaddr".

---

### Post by RadixLecti on 2005-06-29
Thanks for ifconfig.

My ISP uses dynamic IPs, I get a new one as soon as my old one is taken when I start up my comp, so that's not the problem. 
As far as they can tell, it's the mac-adress that changes. Which, admittedly, is odd.

I read somewhere that the kernel can change the mac...? Can this be the case? I know I haven't changed anything, so could it be used by default?

---

### Post by tomchuk on 2005-06-29
It's actually quite easy to change your mac address:
```

thomas@t40 % sudo ifconfig eth1                                                 ~
eth1      Link encap:Ethernet  HWaddr 00:02:8A:EA:59:F0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:1130173 dropped:0 overruns:0 frame:1130173
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1168 (1.1 KiB)  TX bytes:1614 (1.5 KiB)
          Interrupt:9 Base address:0x8000

thomas@t40 % sudo ifconfig eth1 hw ether 00:11:22:33:44:55                      ~

thomas@t40 % sudo ifconfig eth1                                                 ~
eth1      Link encap:Ethernet  HWaddr 00:11:22:33:44:55
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:1130173 dropped:0 overruns:0 frame:1130173
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1168 (1.1 KiB)  TX bytes:1614 (1.5 KiB)
          Interrupt:9 Base address:0x8000

```


Now the question is why the hell would this be happening on it's own? Are you sure nobody is plugging in another computer to your ISP connection? Are you using a switch/hub on the connection with multiple computers?

Here's a little script that will monitor your mac address, it might help to figure out what's going on.

Put this code in a script call mac_monitor.sh and put it into /etc/cron.hourly:
```

#!/bin/sh

DATE=`date`
MAC=`ifconfig eth1 | grep HWaddr | awk '{print $5}'`

echo -e "$DATE \t $MAC" >> /var/log/mac.log

```
and make it executable with "chmod +x /etc/cron.hourly/mac_monitor.sh"

This will record your mac address and the date/time in the file /var/log/mac.log. You can check this periodically to figure out when it is changing, if at all.

---

### Post by RadixLecti on 2005-06-29
Thank you!

And yes, I have a laptop with winXP sharing my internet connection, via a switch, though I can't see how that would affect the MAC adress on the comp running ubuntu...

---

### Post by tomchuk on 2005-06-29
Ah Ha! What's happening is that your Ubuntu PC and Windows PC are both requesting IPs from your ISP- under different MAC addresses. They log this, then shut down your account. You need a router to share the connection, which will do NAT (network address translation) allowing your XP PC and Ubuntu PC to share the same public IP address assigned by your ISP using private IPs behind the router.

You can put an extra network card in you Ubuntu PC, and have it act as a router. There are plenty of guides on how to do this.

---

### Post by mingus on 2005-06-29
[QUOTE=tomchuk]It's actually quite easy to change your mac address[/QUOTE]

Well, you can just call me "egg on face" or "learns something new every day" or "dumb @&*%" . . . I'll answer to all of 'em!

---

### Post by The Na Kun on 2005-06-29
[QUOTE=tomchuk]Ah Ha! What's happening is that your Ubuntu PC and Windows PC are both requesting IPs from your ISP- under different MAC addresses. They log this, then shut down your account. You need a router to share the connection, which will do NAT (network address translation) allowing your XP PC and Ubuntu PC to share the same public IP address assigned by your ISP using private IPs behind the router.

You can put an extra network card in you Ubuntu PC, and have it act as a router. There are plenty of guides on how to do this.[/QUOTE]
 It's only ~$40 for a nice netgear switch/router combination :)
Or you could just leave one computer on forever..

---

### Post by RadixLecti on 2005-06-30
Thanks guys. I have two network cards in my ubuntu comp. I'll play around with it, see what I can see.

Heh, just thought of something: what if I changed the mac-address on my ubuntu comp to match that of the laptop? Would that work? (me know small, me bash keyboard)

PS. Mingus... do you answer to kitty? :-P .DS

---

### Post by The Na Kun on 2005-06-30
[QUOTE=RadixLecti]Thanks guys. I have two network cards in my ubuntu comp. I'll play around with it, see what I can see.

Heh, just thought of something: what if I changed the mac-address on my ubuntu comp to match that of the laptop? Would that work? (me know small, me bash keyboard)

PS. Mingus... do you answer to kitty? :-P .DS[/QUOTE]
 Well, if you change the media access control address on the ubuntu computer, it might get ugly.  I suppose you can change the IP too, but then it would act as a hub, which would defeat the purpose of your switch and having two computers. Remember, it's only ~$40 for a nice netgear router/switch combination. :)

---

### Post by RadixLecti on 2005-07-04
It's happened again.

According to my ISP, my having a switch should not be a problem, it's not two mac-adresses being a problem, it's 50 changes over a period of three minutes.

The support guy, who seems to know little beyond activating internetconnections and reading from a win troubleshooting chart, says my ethernetcard might show onething to me and another to the servers at my ISP.

My cards, both in my XP laptop and Ubuntu comp, show the same mac as always.

I haven't yet tried the script tomchuck posted, but I have checked my mac-address often enough. No change. What could be happening?

---

### Post by WildTangent on 2005-07-04
ISP technicians (for the most part, i dont want to offend anyone here who is one, im sure youre smart, because you use linux :P ) are idiots, if your ISP has requirements like mine, all you need to get a job in tech support is a highschool diploma. ive heard some pretty stupid BS from my ISP before. half the techs dont even know what linux is. one time i was asked what OS i was using, windows or mac, i answered linux, and the tech replied that they dont support anything older than windows 95. trust me, take anything they say with a grain of salt

-Wild

---

### Post by RadixLecti on 2005-07-04
I know... I asked if they had any support for linux, and he was quiet for the longest time before saying that no, they didn't. You could actually hear the whooshing sound of the question mark rotating above his head.

But the main question remains. I've tried switching ethernet cards, and still my comp supposedly continues spamming mac-addresses at a rate of up to 50 changes every three minutes. 
The wierd thing is, it doesn't happen as soon as my comp is switched on. It doesn't happen at regular intervals. It can take anywhere from a few days to over a week for it to happen. 

I've tried correlating it with programs I've been running, and the only thing I've come up with is a maybe. MAYBE I've been running Gnome BitTorrent everytime. But then again, MAYBE I've been running Valknut DC and Firefox too. ;) And the terminal.

---

### Post by rplantz on 2005-10-07
[QUOTE=The Na Kun]Remember, it's only ~$40 for a nice netgear router/switch combination. :)[/QUOTE]

Have you had good luck with Netgear?

I have a Windows box, a Macintosh, and my Ubuntu system all connected to an ethernet hub. My wireless dsl ([http://www.cds1.net/](http://www.cds1.net/)) also connects to the hub. My isp provides a separate IP for each machine. So far it's working just fine.

I have run ethernet cable in my house. We do not use laptops, so wireless is not an issue for me.

The problem I'm having is that I would like to make it easier for my home machines to talk to each other. Right now I have to use the dhcp address supplied by my isp, and that changes over time.

So I'm thinking that a router would allow me to isolate my home network from the rest of the world a little better. I could get another network card for the Ubuntu box, but it would have to be on if anybody else wants to use the net.

Another motivation is that I like to learn new things, and I think it would be fun to play with the router.

I was about to buy a Linksys, but I've seen some negative comments about them. Also, Netgear says they support Linux and Linksys only lists Windows.

Any comments about my plans will be very much appreciated.
Bob

---

