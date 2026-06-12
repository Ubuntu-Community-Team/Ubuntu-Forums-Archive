---
title: "Ubuntu 10.04 - Network is dead"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Pastortom on 2010-03-22
Hiya..

Just installed a fresh copy of ubuntu 10.04 on my computer (Asus P7P55Deluxe i5 PC), but network is completely dead.. 

Ive ran lshw -C network

And Ive got a integrated REALtek card.. worked fine with Windows XP and Vista..

also, Ive tried to manually edit /etc/resolv.conf to insert nameserver 192.168.0.1 (router IP)

But nothing..

I also now tried changing 

[ifupdown]
managed=false

to 

[ifupdown]
managed=true

still nothing.. 

Oh, and I removed network manager pretty early when I noticed the errors, following some advice I found on this forum..

Seeing as I cant get internet working on this damn OS, I cant get it back :P

HELP?!

And, I can see that both mask, ip and gateway is all messed up..

Mask is 255.0.0.255 and Gateway is 128.23.0.0 etc.. 

Why is this happening? 

Oh, yeah, every time Ubuntu boots, right before the african-intro-music I hear a SHARP terrible SPARKLE sound coming from my speaker.. How can I fix this?

---

### Post by Pastortom on 2010-03-22
anyone? Im sitting here desperate :(

---

### Post by Pastortom on 2010-03-22
sorry for my spam, Im just so desperate.. Searched through 40 google links,

and the only thing Ive found is that my network card has appearantly been buggy on earlier Ubuntu releases.. 

Its a RTL8111 integrated card on the motherboard..

So, following some hints I got, I tried PCI=nomsi , but then I wont get any bootup picture.. and it just blacks out =/

I think I just have to reinstall Ubuntu, and try some of the commands WITH Network Manager installed :P

I never should have removed it =(

---

### Post by Pastortom on 2010-03-22
Nobody? Cant believe my thread has gone to page 4 already :/

---

### Post by realzippy on 2010-03-22
10.04 is for testing....

should post in testing & discussions.

Or a mod could move this *thread*.....:)

---

### Post by overdriv on 2010-03-22
I have 10.4 to and can not get the network to work either. I have install Ubuntu on a partition of my Mac  which is still working on the internet.  I also have  to manual address my system as I share the network with web servers. 

The gui for the Ubuntu does not work for Networking  but some of the information gets inputed.


Can you go into terminal and run 

ifconfig

see what information was inputed.

---

### Post by Pastortom on 2010-03-22
eth00     LINK encap. ethernet Hwaddr 00:26:18a7:7b:50
      UP BROADCAST MULTICAST MTU:15000 Metric:1
RX Packets:0 errors:0 dropped:0 overruns:0 frame: 0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
Collisions: 0 txqueuelen:1000
RX byes: 0 (0,0 B) TX byes: 0 (0,0B)
Interrupt: 35 Base address: 0x8000


and some l0 information that I cba to type in..


and when I type lshw -C network I get this:

*-network
description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet Controller
vendor: Realtek Semiconductor Co., Ltd.
Pyshical id: 0
bus info: pci@0000:02:00.2
logitcal name: eth0
version: 03
serial: 00:36:18:a8:7b:50
width: 64 bits
clock 33mhz
capabilities: bus_master cap_list rom ethernet physical
configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency= 0 multicast= yes

Sitting on the worst keyboard in history atm..

---

### Post by Pastortom on 2010-03-22
> **realzippy said:**
> 10.04 is for testing....

should post in testing & discussions.

Or a mod could move this *thread*.....:)

This has nothing to do with the fact that Ubuntu 10.04 is for testing..

I just installed Ubuntu 9.10, and same fracking issue there..

Oh, and I just realized, Ive wasted 8 hours of time now, just because of a USB device, the reason I got black screens all the time (other thread) was because of a USB device.. a china clone USB video device.. Go figure.. It shows you a black screen, and wont give image, and its a USB device thats the reason for it.. 

NOT the graphic card, the sound card, the driver, the CD, the flash stick, the harddrive, the computer itself.. NOOOO.. its the tiniest probable frackin thing.. a frackin USB device.. that results in Ubuntu freezing up and giving a black screen.. both 10.04 and 9.10 from DVD, CD, 4 different USB sticks, 2 different USB harddrive, .. 

I wonder why noone has posted that BLACK SCREEN when installing Ubuntu is 8/10 times due to a USB device that Linux has a problem reading..  I think someone should do that..

Oh wait.. I just did that :D

Sorry for my temper.. Im just sincerely pissed right now :P


Anyways..

Im still on Ubuntu, with dead network card.. Its even worse this time on 9.10 then it was earlier on 10.04.. 

But same main problem: 

ping 192.168.0.1
connect: Network is unreachable..

And yeah, the ROUTER doesnt even show a light for the cable being connected.


[B]What is going on? I was on internet not 10 hours ago, playing STO under Windows 7.. 

Have Windows 7 messed up my Networks card? 

Is this a hardware failure?

Or could it be as simple as that Ubuntu Linux 9.10/10.04 CANNOT at ALL support RTL 8111/8168B network cards? [/B]

---

### Post by Pastortom on 2010-03-22
I am now at a loss...

I think Ubuntu 10.04 has destroyed my built-in Network Card.. permanently destroyed it.. because it used wrong driver or something..

When I turn off my computer, I usually see the network port (NIC) light green and blink orange.. but its only slowly blinking orange now.. 

All the time.. 

Even when Im installing Windows XP now.. 

I just hope to God its not destroyed because of Ubuntu..

I will update you all on it as soon as I know!



I was right, it looks like :(

[http://ubuntuforums.org/showthread.php?t=1436667](http://ubuntuforums.org/showthread.php?t=1436667)

my network card was destroyeed

---

### Post by realzippy on 2010-03-23
Have the same builtin card,it runs well under Edgy/Karmic/Lucid.....

description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:7d:02:ab:4b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.1 latency=0 multi

....do not believe that Lucid had destroyed it....


Edit.

BTW,strange hw address:

serial: 00:36:18:a8[COLOR="Red"]\[/COLOR]7:7b:50

---

### Post by Pastortom on 2010-03-23
> **realzippy said:**
> Have the same builtin card,it runs well under Edgy/Karmic/Lucid.....

description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:7d:02:ab:4b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.1 latency=0 multi

....do not believe that Lucid had destroyed it....


Edit.

BTW,strange hw address:

serial: 00:36:18:a8[COLOR="Red"]\[/COLOR]7:7b:50


Well,

the NIC wont work in Windows nor Ubuntu now.. (worked fine in WIndows XP and Windows 7, for 3 months now, its a completely new PC) The NIC behaves rather strangely after I tried to install Ubuntu on it..

Can I ask you how you managed to get it working? Because it didnt work out of the box, right?

---

### Post by Elfy on 2010-03-23
moved to lucid - next time please do not bump so soon - give people a chance to find it.

---

### Post by ezsit on 2010-03-23
> the NIC wont work in Windows nor Ubuntu now.. (worked fine in WIndows XP and Windows 7, for 3 months now, its a completely new PC) The NIC behaves rather strangely after I tried to install Ubuntu on it..

Did it occur to you that it could just be a hardware failure? I've seen onboard NICs go out once in a while. It has nothing to do with software, or drivers, or operating systems, it just happens to hardware sometimes. Many times I've seen hardware fail but I've never seen software actually CAUSE a hardware failure. 

Years ago, some video hardware could be fried by using the incorrect refresh rates and driving a monitor past its specified range. And there was that issue of some LG cdrom drives with buggy firmware being caused to fail under certain conditions while running Linux. These two examples are the rare exceptions though. There might be others, but the likelyhood of software causing a hardware failure is extremely unlikely.

---

### Post by diebels on 2010-03-23
> **Pastortom said:**
> 

Mask is 255.0.0.255 and Gateway is 128.23.0.0 etc.. 

Why is this happening? 


That netmask won't get far.
> **Pastortom said:**
> 
And yeah, the ROUTER doesnt even show a light for the cable being connected.
Try another cable.  If there is no indicator light, you probably have a hardware problem.

---

### Post by realzippy on 2010-03-24
*"Can I ask you how you managed to get it working? Because it didnt work out of the box, right?"*

...no,it worked out of the box and always used to.
Maybe you messed DHCP up or something...

Start from a LiveCD and see if network runs...


As mentioned,is this ok: (???????????????)

serial: 00:36:18:a8[COLOR="Red"]\[/COLOR]7:7b:50

Who knows about that?


...and,another idea:
have you reset the router meanwhile?

---

### Post by Pastortom on 2010-03-24
> **realzippy said:**
> *"Can I ask you how you managed to get it working? Because it didnt work out of the box, right?"*

...no,it worked out of the box and always used to.
Maybe you messed DHCP up or something...

Start from a LiveCD and see if network runs...


As mentioned,is this ok: (???????????????)

serial: 00:36:18:a8[COLOR="Red"]\[/COLOR]7:7b:50

Who knows about that?


...and,another idea:
have you reset the router meanwhile?



Okey, about that serial, I was dead tired, and used a crappy keyboard, so that was a typo, if you look at the Original Post I have corrected it..



But in general, that made me come to this conclusion that my NIC was FRIED by Ubuntu is as follows (and dare I say I have some knowledge of computers, software and hardware, and I would not say this if I wasnt sure):

1) Windows 7 and Windows XP runs this computer fine, with the NIC 100% fine, surfed the web for 3 months on it, played game, no problems with this NIC connected to my DIR 615 router at all .. before I installed Ubuntu..

2) I install Ubuntu 10.04, the DHCP with the NIC doesnt work at all, Ive tried all different guides out there to fix this problem..

3) I install Ubuntu 9.10, same prolem, wont work

4) I tried connecting the ADSL modem directly to the computer, thereby skipping the Router completely, doesnt work..

5) The NIC light blinks ORANGE slowly, even during PC bootup, and even with Windows XP /Windos 7 installed after Ubuntu..

6) I tried switching cables, didnt work

7) I notice that the router wont acknowledge the cable as active (no active-light on the port I use)

8) Ive tried RESETTING pc bios, didnt fix things

9) Ive tried updating pc bios, didnt fix things

10) Ive tried updating windows drivers, didnt fix things

11) Ive tried updating Ubuntu drivers (and fixing the 8187 driver to 8186, which is aknown issue, that ubuntu automatically chooses a faulty driver for the 8111/8186 RTL NIC), didnt fix things..



Now.. BEFORE I started with Ubuntu on this computer, I had Windows XP and WIndows 7 running with this NIC 100% fine..

THEN.. I installed Ubuntu 10.04 , NIC doesnt work, pestered about it for 8 hours, tried installing Ubuntu 9.10, NIC still doesnt work.. Giving up, going back to Windows XP, NIC suddenly doesnt work.. going back to Windows 7, NIC doesnt work at all.. The NIC gives the same slow orange light, and no green activity light, nor does the Router give any active-connection-light on the cable.. 

So, with all my experience and knowledge with computers in general, my conclusion is one of these 2 possible answers to what happened:

A) It could be 100% coincidental that my NIC gave up RIGHT when I try to install Ubuntu, even though it worked fine 100% to the minute before installing Ubuntu.. so just worn out, after 3months, not caused by Ubuntu

or..

B) Ubuntu's drivers in either 10.04 or 9.10 messed up the NIC in such a way, that it became corrupt with certain things (I have no idea if NIC's have an internal memory of some kb's or what, or an internal BIOS, no clue).. either way, got completely wasted by Ubuntu's faulty drivers.. 


Now.. does anyone knoe how I can possibly RESET the NIC? if possible? I have tried resetting the BIOS, tried updating the BIOS, but nothing..

Atm, Im using a LAN to USB adapter I bought from Dealextreme a while back for only 5 dollars, it works like a charm with Ubuntu :)

---

### Post by realzippy on 2010-03-24
mistyped...

---

### Post by realzippy on 2010-03-24
Does

```
ping localhost
```

work??


You have seen this thread ?:

[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

---

### Post by Pastortom on 2010-03-24
> **realzippy said:**
> Does

```
ping localhost
```

work??


You have seen this thread ?:

[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

Havent tried that :)

Will do, and let you guis know what happens..

It might be that Ubuntu drivers has turned something in the NIC off, which results in Windows having troubles using it.. that might explain everything, tbh..

:)

---

### Post by ezsit on 2010-03-24
There is a bug report on kernel.org for your Realtek 8112L chipset and kernel 2.6.32 here:

[https://lists.linux-foundation.org/pipermail/bugme-new/2009-December/023571.html](https://lists.linux-foundation.org/pipermail/bugme-new/2009-December/023571.html)

and here:

[https://bugzilla.kernel.org/show_bug.cgi?id=14798](https://bugzilla.kernel.org/show_bug.cgi?id=14798)

Maybe the same problem?

---

### Post by i22yb on 2010-04-12
I've got the same chipset with similar problems.  Had no problems with 9.10, but it's been majorly flakey in 10.04.  I dual boot to Win 7 and have no problems there.  Before the last kernel update, I could disable and re-enable the network and it would come back up (until the next reboot).  Just as you stated, none of my lights on the card come up (or the light on the router that the cable is plugged into); however, if I reboot to Win 7 the LAN port works just fine.

I'm assuming, as the bug reports noted above, that this must be a driver/kernel issue.  It's VERY annoying; however, I know i'm dealing with a beta so I'm just praying for an update soon that will fix it.  Until then, my Belkin wireless USB stick is getting some use.

Other than this headache of an issue, 10.04 is looking pretty good!

---

### Post by i22yb on 2010-04-13
Another solution may be found here:
[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

I'm about to give this a try.  Your chipset is a bit different than mine, so this might not be your problem, but it sounds similar.

---

### Post by i22yb on 2010-04-13
Well, that solution worked for me.  I had to disable and re-enable the card in Windows after changing the wake-on-lan setting - then the card started working in windows and as soon as I rebooted to Ubuntu it was working again.  Hope it works for you!

---

### Post by paliyoes on 2010-04-13
I have solved the same problem (Network dead on Windows and Ubuntu) running the live cd and restarting.

---

