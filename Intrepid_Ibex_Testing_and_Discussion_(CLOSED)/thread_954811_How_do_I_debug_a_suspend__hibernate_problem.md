---
title: "How do I debug a suspend / hibernate problem?"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by shane19174 on 2008-10-21
I'm sorry to start a new thread for this, but all of the suspend/hibernate-related issues I've seen here differ in some respects from mine.

Basically, my laptop (Dell Latitude C810) starts to suspend or hibernate by fading to black, but it never really seems to complete the action. It just stops: the screen is black--but not OFF!: you can see the backlighting there. There's even sometimes a cursor blinking in the upper left-hand corner.

Needless to say, the computer can't resume from this (non-)state.

My question, then: Short of anyone being able to tell me what's wrong and how to fix it, can anyone at least tell me where I should start looking to identify the problem?

I'd really appreciate your help on this.

Thanks,
Shane

---

### Post by infinito on 2008-10-21
Here you can find info on debugging suspend.

[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)

---

### Post by shane19174 on 2008-10-21
Thank you very much, but if I read that page correctly, it's really about debugging problems with resume. In other words, it assumes that suspend actually occurs, and that you just can't restore the former state. In my case, though, suspend never completes.

Any other ideas?

Thanks,
Shane

---

### Post by beercz on 2008-10-21
What do your logs say when you try to suspend/hibenate?

System->Administration->System Log

Have a look in kern.log, messages, system log

---

### Post by shane19174 on 2008-10-22
Hmm, can you give me an idea what I should be looking for?
Thanks,
Shane

---

### Post by shane19174 on 2008-10-22
OK, maybe someone else can make something of this, but I don't see any useful info in the logs. The only log that makes any reference to my attempt to suspend or hibernate is syslog. Here is an excerpt from an attempt to suspend:

> Oct 22 13:19:58 shane-laptop NetworkManager: <info>  Sleeping... 
Oct 22 13:19:58 shane-laptop NetworkManager: <info>  (eth0): now unmanaged 
Oct 22 13:19:58 shane-laptop NetworkManager: <info>  (eth0): device state change: 2 -> 1 
Oct 22 13:19:58 shane-laptop NetworkManager: <info>  (eth0): cleaning up... 
Oct 22 13:19:58 shane-laptop NetworkManager: <info>  (eth0): taking down device. 
Oct 22 13:19:58 shane-laptop NetworkManager: <info>  (wlan0): now unmanaged 
Oct 22 13:19:58 shane-laptop NetworkManager: <info>  (wlan0): device state change: 8 -> 1 
Oct 22 13:19:58 shane-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 37). 
Oct 22 13:19:59 shane-laptop NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 5592 
Oct 22 13:19:59 shane-laptop kernel: [ 2646.515417] wlan0: disassociating by local choice (reason=3)
Oct 22 13:19:59 shane-laptop NetworkManager: <info>  (wlan0): removing resolv.conf from /sbin/resolvconf 
Oct 22 13:19:59 shane-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess  
Oct 22 13:19:59 shane-laptop avahi-daemon[4689]: Withdrawing address record for 192.168.178.25 on wlan0.
Oct 22 13:19:59 shane-laptop avahi-daemon[4689]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.178.25.
Oct 22 13:19:59 shane-laptop avahi-daemon[4689]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct 22 13:19:59 shane-laptop NetworkManager: <info>  (wlan0): cleaning up... 
Oct 22 13:19:59 shane-laptop NetworkManager: <info>  (wlan0): taking down device. 
Oct 22 13:19:59 shane-laptop avahi-daemon[4689]: Withdrawing address record for fe80::20e:2eff:fee7:2fb2 on wlan0.
Oct 22 13:21:46 shane-laptop syslogd 1.5.0#2ubuntu6: restart.
Oct 22 13:21:46 shane-laptop kernel: Inspecting /boot/System.map-2.6.27-7-generic
Oct 22 13:21:47 shane-laptop kernel: Cannot find map file.
Oct 22 13:21:47 shane-laptop kernel: Loaded 50255 symbols from 98 modules.

As you can see, it tries to go to sleep, but then it stops until I do a hard reboot 2 minutes later. (I've waited longer, but it doesn't make any difference.)

Here's an excerpt from an attempt to hibernate:

> Oct 22 13:36:06 shane-laptop NetworkManager: <info>  Sleeping... 
Oct 22 13:36:06 shane-laptop NetworkManager: <info>  (eth0): now unmanaged 
Oct 22 13:36:06 shane-laptop NetworkManager: <info>  (eth0): device state change: 2 -> 1 
Oct 22 13:36:06 shane-laptop NetworkManager: <info>  (eth0): cleaning up... 
Oct 22 13:36:06 shane-laptop NetworkManager: <info>  (eth0): taking down device. 
Oct 22 13:36:07 shane-laptop NetworkManager: <info>  (wlan0): now unmanaged 
Oct 22 13:36:07 shane-laptop NetworkManager: <info>  (wlan0): device state change: 8 -> 1 
Oct 22 13:36:07 shane-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 37). 
Oct 22 13:36:07 shane-laptop NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 5540 
Oct 22 13:36:07 shane-laptop kernel: [  902.655184] wlan0: disassociating by local choice (reason=3)
Oct 22 13:36:07 shane-laptop NetworkManager: <info>  (wlan0): removing resolv.conf from /sbin/resolvconf 
Oct 22 13:36:07 shane-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess  
Oct 22 13:36:07 shane-laptop avahi-daemon[4691]: Withdrawing address record for 192.168.178.25 on wlan0.
Oct 22 13:36:07 shane-laptop avahi-daemon[4691]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.178.25.
Oct 22 13:36:07 shane-laptop avahi-daemon[4691]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct 22 13:36:07 shane-laptop NetworkManager: <info>  (wlan0): cleaning up... 
Oct 22 13:36:07 shane-laptop NetworkManager: <info>  (wlan0): taking down device. 
Oct 22 13:36:07 shane-laptop avahi-daemon[4691]: Withdrawing address record for fe80::20e:2eff:fee7:2fb2 on wlan0.
Oct 22 13:36:08 shane-laptop kernel: [  904.090389] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
Oct 22 13:36:08 shane-laptop kernel: [  904.090411] PM: Basic memory bitmaps created
Oct 22 13:38:30 shane-laptop syslogd 1.5.0#2ubuntu6: restart.
Oct 22 13:38:30 shane-laptop kernel: Inspecting /boot/System.map-2.6.27-7-generic
Oct 22 13:38:30 shane-laptop kernel: Cannot find map file.
Oct 22 13:38:31 shane-laptop kernel: Loaded 50255 symbols from 98 modules.

This time it looks like it might be more promising, with the "Basic memory bitmaps created", but again it just waits until I do a hard reboot (i.e., hold the power button on my laptop till it shuts off, then restart). In contrast to the suspend attempt, a cursor blinks the whole time it's trying to hibernate.

Again, I would really appreciate any help anyone can offer here.

Thanks,
Shane

---

### Post by beercz on 2008-10-22
Are you using compiz?

If so, does your machine hibernate/suspend when not running compiz?

Also, have you reported a bug?

[Here is a list bugs]("https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=hibernate+dell+latitude&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=") reported to launchpad for suspend/hibernate issues with similar laptops.

Do any of these help?

---

### Post by shane19174 on 2008-10-23
OK, I've made some progress, but I'm not there yet.

First of all, beercz (or Ian), thanks again for your help on this. To answer your questions: 

No, I'm not running compiz (still waiting for a 96 series nvidia driver compatible with the new Xorg. And even then, my machine is far too slow to support any effects...)

No, I haven't reported a bug yet. I'm not confident yet that I have enough info to file one usefully. But almost now, thanks in part to the list of bugs you posted...

One of the bugs somewhere mentioned that suspend and hibernate work if no USB devices had been in use, so I tried without any. What do you know? both suspend and hibernate worked! Then, thinking about the network-manager stuff in the syslog I posted, I thought it might just be my USB wireless stick. I plugged in my USB mouse and left out wireless, and it also worked. I have been able to reproduce this now: suspend and hibernate fail with my RT8187B USB wireless device (which only became supported with the 2.6.27 kernel). 

The next test, then, was to replace the 8187B with a PCMCIA wireless card. Unfortunately suspend and hibernate also fail with it, but the symptoms are different. Whereas the computer just remained in limbo with a blinking cursor with the USB wireless, it appears to face a kernel panic with the PCMCIA card. (Blinking caps lock and scroll lock lights are a symptom for kernel panic, aren't they?) Here is where I need to gather some more info: how do I confirm that this is indeed a kernel panic? And how do I identify the exact model number of the PCMCIA card.

One last peculiarity: When no networking device attached, as I said above, both hibernate and suspend work, meaning that the computer actually goes to sleep, and I can actually resume where I left off. However, while hibernate seems to work flawlessly, suspend leaves the screen completely white. I don't mean I get a white screen of death on resume, not at all. I mean, *while the notebook is suspended*, the screen remains white. I first noticed it because I manually told the computer to suspend via the new fast user switcher panel thing, and left the screen open. But then I set the power manager settings to suspend when I close the lid, did so, and looked through the crack to see a white glow within. This doesn't seem like a very energy-efficient state, nor do I suspect it will prolong the life of my notebook's display...

Anyway, it looks like I've got several bugs to report here. I would really appreciate it if someone could give me some pointers on how to go about reporting them. In other words, which problems should be filed as which bugs against which packages, and what info do I need to supply?

Thanks in advance,
Shane

---

### Post by shane19174 on 2008-10-23
Anyone have any ideas?

On the one hand, I could live with having to unplug my wireless device before suspending or hibernating. It's not an elegant solution, but if it works...

On the other hand, I don't want to get a kernel panic just because I forget to pull out a PCMCIA card before closing the lid of my laptop...

Also, I've searched the forums for this white screen on suspend problem, but all I can find is people facing a white screen of death on resume. Again, this is not my problem. Instead, assuming I remove all wireless devices, suspend works perfectly but a white screen remains the entire time the computer is suspended, right up until I resume. And resume works fine. I tested by suspending my laptop for 8 hours, and the white screen doesn't go away!

Any suggestions would be appreciated.

Thanks,
Shane

---

### Post by Seq on 2008-10-23
> **shane19174 said:**
> Anyone have any ideas?

On the one hand, I could live with having to unplug my wireless device before suspending or hibernating. It's not an elegant solution, but if it works...

On the other hand, I don't want to get a kernel panic just because I forget to pull out a PCMCIA card before closing the lid of my laptop...

the file _/etc/defaults/acpi-support_ has a line called MODULES that specifies modules to unload/load on suspend/resume. I'm not sure if it is still honoured with the dbus (non "legacy") suspend in Intrepid, but it is worth a shot.

Before messing with config files, I'd try manually unloading modules used for your network card, then suspending (with the card plugged in), and go from there.

This is probably bug worthy ("Fail to suspend when XYZ card is connected")

---

### Post by shane19174 on 2008-10-24
OK, this sounds like a good idea. So how do I find out which modules are used by my network card? And how do I manually disable them?

Thanks,
Shane

Oh, and against what package should I be filing a bug?

---

### Post by Seq on 2008-10-24
> **shane19174 said:**
> OK, this sounds like a good idea. So how do I find out which modules are used by my network card? And how do I manually disable them?

How I would normally do it (this may not work for USB or PCMCIA devices...)
```
lspci -nn -v
```

That will give you a lot of information, you'll want to scroll through it till you see an "Ethernet Controller" that describes your wireless device. At the end of that list, it has a "Kernel Modules" line that tells you the module name.

Since USB and PCMCIA are removable, I'd just plug in your device and run 'dmesg' after a few seconds. Your device will be at the bottom of the log talking about probing and associating, etc.

```
[timestamp] _module_: message
```

> **shane19174 said:**
> Oh, and against what package should I be filing a bug?

Probably 'linux' as it is provided from the kernel.

---

### Post by shane19174 on 2008-10-24
OK, sorry to ask you guys to hold my hand on every step of this (I know: what's someone like this doing in the Development & Programming forum?), but here goes anyway.

After plugging in my USB device, dmesg gives me this:

```
[ 1300.066421] sd 0:0:0:0: [sda] Starting disk
[ 1300.093807] PM: resume devices took 1.652 seconds
[ 1300.093849] PM: Finishing wakeup.
[ 1300.093852] Restarting tasks ... done.
[ 1304.377362] eth0:  setting half-duplex.
[ 1304.377965] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1320.456054] usb 1-2: new full speed USB device using uhci_hcd and address 5
[ 1320.638404] usb 1-2: configuration #1 chosen from 1 choice
[ 1321.707845] rtl8187: 8187B chip detected. Support is EXPERIMENTAL, and could damage your
[ 1321.707855]          hardware, use at your own risk
[ 1321.707869] rtl8187: inconsistency between id with OEM info!
[ 1321.721644] phy1: Selected rate control algorithm 'pid'
[ 1321.724769] phy1: hwaddr 00:0e:2e:e7:2f:b2, RTL8187BvB(early) V0 + rtl8225z2
[ 1352.172946] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1355.859146] wlan0: authenticate with AP 00:11:92:5e:d8:e2
[ 1355.867213] wlan0: authenticated
[ 1355.867226] wlan0: associate with AP 00:11:92:5e:d8:e2
[ 1355.904199] wlan0: RX AssocResp from 00:11:92:5e:d8:e2 (capab=0x421 status=0 aid=1)
[ 1355.904216] wlan0: associated
[ 1355.905558] wlan0: disassociating by local choice (reason=3)
[ 1367.599728] wlan0: authenticate with AP 00:1c:4a:4d:90:92
[ 1367.602870] wlan0: authenticated
[ 1367.602894] wlan0: associate with AP 00:1c:4a:4d:90:92
[ 1367.607139] wlan0: RX AssocResp from 00:1c:4a:4d:90:92 (capab=0x411 status=0 aid=1)
[ 1367.607158] wlan0: associated
[ 1367.607477] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1377.932073] wlan0: no IPv6 routers present
shane@shane-laptop:~$ 


```

So the device in question is registering as rtl8187, right? (And not RTL8187B, correct?) So that's what I should try disabling before suspend/hibernate? Or what about wlan0, which, if I'm not mistaken, would cover either the USB or the PCMCIA device?

More fundamentally, though: How do I manually disable a module to complete the test?

Thanks,
Shane

---

### Post by Seq on 2008-10-24
```
[ 1321.707845] rtl8187: 8187B chip detected. Support is EXPERIMENTAL, and could damage your
[ 1321.707855]          hardware, use at your own risk
[ 1321.707869] rtl8187: inconsistency between id with OEM info!
```

That is your driver, rtl8187.

```
[ 1355.859146] wlan0: authenticate with AP 00:11:92:5e:d8:e2
[ 1355.867213] wlan0: authenticated
(...)
```

The driver loaded, found a device, and named it wlan0. That is just basically a cardid (a second would be wlan1, etc).

> **shane19174 said:**
> 
So the device in question is registering as rtl8187, right? (And not RTL8187B, correct?) So that's what I should try disabling before suspend/hibernate? Or what about wlan0, which, if I'm not mistaken, would cover either the USB or the PCMCIA device?

More fundamentally, though: How do I manually disable a module to complete the test?

You are correct about the module name. 

modprobe -r rtl8187

then after you resume:

modprobe rtl8187

---

### Post by shane19174 on 2008-10-24
Thanks, that works! That is, doing a modprobe -r rtl8187 before either a suspend or hibernate succeeds. I will file a bug for this, and I'll try this out with my PCMCIA card as well. 

In the meantime, how can I set things up so that I don't have to do a manual modprobe before and after each suspend or hibernate? Seq, you mentioned /etc/default/acpi-support. Can you give me some detail on how to edit it?

Thanks again,
Shane

---

### Post by Seq on 2008-10-24
> **shane19174 said:**
> Thanks, that works! That is, doing a modprobe -r rtl8187 before either a suspend or hibernate succeeds. I will file a bug for this, and I'll try this out with my PCMCIA card as well. 

In the meantime, how can I set things up so that I don't have to do a manual modprobe before and after each suspend or hibernate? Seq, you mentioned /etc/default/acpi-support. Can you give me some detail on how to edit it?

Thanks again,
Shane

There is a similar bug regarding a different driver. See this comment within it:

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/23092/comments/14](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/23092/comments/14)

---

### Post by shane19174 on 2008-10-24
Thanks again, Seq, for leading me in the right direction. I looked around a little and found that my exact bug (concerning rtl8187) has already been filed, and a very similar workaround to the one you referenced has been suggested. For anyone interested, here is the bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/279798]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/279798").

Now I've got to try out this workaround. I'll post back on the outcome...

Shane

---

### Post by shane19174 on 2008-10-24
Yes, I can confirm that this workaround works for me:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/279798/comments/14]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/279798/comments/14").

Hopefully this helps someone else, and hopefully there will be a more permanent fix at some point.

---

