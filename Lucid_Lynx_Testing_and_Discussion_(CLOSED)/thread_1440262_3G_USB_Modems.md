---
title: "3G USB Modems"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by phillw on 2010-03-27
Hi,

what have they broken ?

My 3G usb modem used to work (around alpha1 time), I've seen a couple of people flagging up that they don't work so plugged mine in - Yup, it doesn't work.

I'm not the only one affected, but not sure what they broke :-(

I've installed usb-modeswitch to no avail

Any ideas ?

Thanks,

Phill.

---

### Post by vishalrao on 2010-03-27
can you be a little more specific (logs, error messages, steps to reproduce, lsusb/dmesg output etc) when you say "it used to work" and now "it does not work" ? :)

i just tried a couple of 3.1 mbps CDMA RevA EVDO USB devices which need usb-modeswitch and they work well (better in GNOME and good in KDE) - I only tried since Beta1 and now with the latest updates...

---

### Post by phillw on 2010-03-27
Hi, 

well, after much rebooting:

9.10 off the canonical CD with 2.6.31-14 kernel works out of the box
9.10 updated on the hard drive does not.

10.04 alpha1 worked out of the box (I had previously used it)
10.04 updated on the hard drive does not.

> >> Must tell you re usb modem - can't get it work in 9.10 or 10.04 (yet) - so I'm stuck on 9.04 on my laptop
>> It works fine in 9.04 and I have it going on puppy linux, but the later kernels seem to have some conflict
>> It's not a provider issue, there's been some change to the kernel that is causing the issue as far as I can tell
>> I read something about it somewhere - basically it gets recognised as a storage device, rather than a 3g modem, although lsub lists it as modem
>> I tried a few 'hacks' I found, but none worked - there was a script someone wrote that looked promising, but I am a bit sceptical of third party scripts

> I wished Lubuntu would support Huawei E1552 or E160 (as lubuntu identifies it via lsusb). 
When connecting the usb dongle, Network Manager Applet does not recognize the modem.  The CD iso of the modem does not even appear.

What logs would you like me to get ? As I can boot with it working, I would be more than happy to provide any information that may be of help. I don't have my alpha1 image now, but still have my 9.10 disk from Canonical.

BTW, whilst I was 1st alerted via Lubuntu, as it shares the same ubuntu 'core', it was no great surprise to me to find it doesn't work when I tried ubuntu 10.04 'main'. I have 10.04 'main', 10.04 lubuntu and 9.10 on my computer. None of them work.

Regards,

Phill.

---

### Post by vishalrao on 2010-03-27
im no expert but i would think dmesg and lsusb (before and after plugging in the device) to begin with (as i posted above) might help get us started on figuring this one out?

if you manage to create networkmanager connections but dialing/connecting fails then perhaps logs from /var/log (like /var/log/syslog) might help too...

---

### Post by recluce on 2010-03-27
I may have an unrelated problem. When I am in Europe, I am using a Vodafone Germany UMTS (3G) USB stick. Both in Jaunty and Lucid Beta, the stick is recognized out of the box - just plug it in and select the correct provider in the manager that comes up. 

However, while my sessions in Jaunty are rock-stable (I ran one for more than 12 hours), Lucid will "loose" the connection while idling. At that point, only removing/reinserting the device will allow Lucid to use it again. The stick is identified as a Huawei E220 / E270.

If somebody wants to see some logs, let me know what to do. Unfortunately, I can only test the stick until Sunday, since I will be back on my way to Canada on Monday.

---

### Post by vishalrao on 2010-03-27
i wonder if there is that option "send ppp echo packets" might help here...

---

### Post by keithpeter on 2010-04-19
Hello All

I'm testing mobile broadband with Lucid and I'm aware that there are issues with this for some people. My t-mobile web'n'walk modem is a Huawei E220 device. It works fine under Karmic and Jaunty, and windows on this Lenovo T42 Centrino 1.7GHz laptop

In Lucid, the device shows up as a CD-Rom drive (complete with dinky disk icon). Using the procedure posted at

[http://ubuntuforums.org/showthread.php?t=1448711](http://ubuntuforums.org/showthread.php?t=1448711)

I get the following...

dmesg

```
[   66.142876] Initializing USB Mass Storage driver...
[   66.142929] usbcore: registered new interface driver usb-storage
[   66.143565] USB Mass Storage support registered.
[   67.352055] usb 3-2: new full speed USB device using uhci_hcd and address 3
[   67.511756] usb 3-2: configuration #1 chosen from 1 choice
[   67.532665] scsi4 : SCSI emulation for USB Mass Storage devices
[   67.537155] usb-storage: device found at 3
[   67.537159] usb-storage: waiting for device to settle before scanning
[   71.802330] end_request: I/O error, dev fd0, sector 0
[   71.802338] __ratelimit: 9 callbacks suppressed
[   71.802342] Buffer I/O error on device fd0, logical block 0
[   72.537353] usb-storage: device scan complete
[   72.540394] scsi 4:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[   72.567310] sr1: scsi-1 drive
[   72.569306] sr 4:0:0:0: Attached scsi CD-ROM sr1
[   72.569931] sr 4:0:0:0: Attached scsi generic sg2 type 5
[   84.866554] end_request: I/O error, dev fd0, sector 0
[   84.866571] Buffer I/O error on device fd0, logical block 0
[   97.934709] end_request: I/O error, dev fd0, sector 0
[   97.934727] Buffer I/O error on device fd0, logical block 0
[  110.998313] end_request: I/O error, dev fd0, sector 0
[  110.998329] Buffer I/O error on device fd0, logical block 0

```

lsusb

```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

uname -a

```
Linux t42 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
```

Fresh install of Ubuntu Beta 2 and updated today.

Questions

I installed usb-modeswitch but nothing special seems to be happening. Do I have to *do* anything to get modeswitch to do something, type a terminal command or what?

I walk through the System | Preferences | Network Connections dialogue and fill in the three stage procedure for mobile broadband after I've disconnected the local wifi. What do I click on to start a connection? I can't see anything obvious. In Jaunty and Karmic the network manager icon had a setting to 'connect' t-mobile that appeared in the menu in the notification area. Under lucid, I can't see anything similar.

Cheers...

---

### Post by Ibidem on 2010-04-19
First, note that I do not have experience with this.  These are the best ideas I have...
What you have done is not the solution, it is "data collection".
See post #10 in the thread you linked to--
"sudo eject sr" might be what you need, but I don't know.  Maybe run "mount|grep sr"?

Then there's post 11--did you restart after installing usb-modeswitch?

---

### Post by keithpeter on 2010-04-19
Thanks for reply

> **Ibidem said:**
> 
What you have done is not the solution, it is "data collection".


Yup, if I had the solution, I would not need to post.

> **Ibidem said:**
> 
See post #10 in the thread you linked to--
"sudo eject sr" might be what you need, but I don't know.  Maybe run "mount|grep sr"?

Then there's post 11--did you restart after installing usb-modeswitch?

```
keith@t42:~$ sudo eject sr
eject: unable to find or open device for: `sr'
keith@t42:~$ mount|grep sr
keith@t42:~$ 
```

Part of my problem is that I don't know what I'm supposed to find if it was connecting properly! The user interface seems to be very different to Jaunty/Karmic.

And, yes, I did restart after installing usb-modeswitch, but I have no idea what I'm supposed to see.

---

### Post by StuartN on 2010-04-19
> **keithpeter said:**
> Do I have to *do* anything to get modeswitch to do something, type a terminal command or what?

You may need to do **sudo usb_modeswitch** to force it to run, as described here [http://www.blogcatalog.com/blog/iwrite-2/dbbfb38ae5ef9ccef8540aad7f9edbd6](http://www.blogcatalog.com/blog/iwrite-2/dbbfb38ae5ef9ccef8540aad7f9edbd6).

You also need to check that the vendor id and product id (from **lsusb**) are in your usb_modeswitch.conf file - the latest version claims e220 support [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/) and offers some troubleshooting tips.

---

### Post by keithpeter on 2010-04-19
> **StuartN said:**
> You may need to do **sudo usb_modeswitch** to force it to run, as described here [http://www.blogcatalog.com/blog/iwrite-2/dbbfb38ae5ef9ccef8540aad7f9edbd6](http://www.blogcatalog.com/blog/iwrite-2/dbbfb38ae5ef9ccef8540aad7f9edbd6).

You also need to check that the vendor id and product id (from **lsusb**) are in your usb_modeswitch.conf file - the latest version claims e220 support [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/) and offers some troubleshooting tips.

Hello StuartN

Well, there is not a file at /etc/usb_modeswitch.conf, but there is a directory at /etc/usb_modeswitch.d/ and that has the file with name /etc/usb_modeswitch.d/12d1:1003 which has the right kind of things in it...

```
########################################################
# Huawei E220, E230, E270, E870

DefaultVendor= 0x12d1
DefaultProduct=0x1003

TargetClass=0xff

CheckSuccess=20

HuaweiMode=1
```

Should I be making a usb_modeswitch.conf file like here

[http://blog.pew.cc/blog/Getting+the+Huawei+E160+to+work+/](http://blog.pew.cc/blog/Getting+the+Huawei+E160+to+work+/)

Progress: rebooting the laptop with the *Huawei modem plugged in* and disconnecting the wifi results in a working connection, so I know the issue is one of getting the device to be recognised as a modem and not a cd-rom drive rather than any problem with Ubuntu not recognising the device.

I shall continue to google. I'm hoping that the 'just plug it in and it works' functionality we had in previous Ubuntu versions can be restored.

---

### Post by phillw on 2010-04-19
Hi,

I've a few plays with the huwaei device i have & gotten royally fed up. I'm wishing you all the very best & hope you get a working solution to what quite evidently is a regression that should have been corrected. :-\ There are bug reports, but they have put them on hold as there is no 'crash & burn' logs to go with them.:confused:

Just have to wait for all hell to break loose when the 'public' all start flooding them with the same error, they cannot say they have not been warned 

Regards,

Phill.

---

### Post by StuartN on 2010-04-19
> **keithpeter said:**
> Should I be making a usb_modeswitch.conf file like here

[http://blog.pew.cc/blog/Getting+the+Huawei+E160+to+work+/](http://blog.pew.cc/blog/Getting+the+Huawei+E160+to+work+/)

No, I do not think so - it looks like the latest usb_modeswitch configuration is different from that article. It obviously can function, but is not being triggered when the device is plugged in after bootup. Manually running **sudo usb_modeswitch** should work around it (I have a desktop script with just this command in it, in 9.10).

---

### Post by keithpeter on 2010-04-20
> **StuartN said:**
> No, I do not think so - it looks like the latest usb_modeswitch configuration is different from that article. It obviously can function, but is not being triggered when the device is plugged in after bootup. Manually running **sudo usb_modeswitch** should work around it (I have a desktop script with just this command in it, in 9.10).

Hello StuartN

I'll have a proper read of the documentation when I get some time later this week, and I'll try sudo usb_modeswitch and see what I can find in the logs after doing so. At least I know the modem actually works with Lucid after a fresh boot, so its not an incompatibility, just a question of convincing Lucid that this is a modem and not a cd-rom!


Hello Phillw

It does strike me as odd that we have an LTS release that may not 'just work' with popular makes of mobile broadband internet modem in the same way that a previous (non-LTS) version of Ubuntu did. That sends an unfortunate message about 'backward compatibility' doesn't it?

I'll record a bug about not being able to connect after having created the network-manager profile and attach appropriate logs and see what happens. Perhaps the issue can be dealt with in a post launch patch.

---

### Post by thecityofgold2006 on 2010-04-20
The e169 also has problems. There are many bug reports, with the advice I was given at the end being 'update the modem firmware using a Windows PC'. I had to laugh.

---

### Post by keithpeter on 2010-04-20
> **thecityofgold2006 said:**
> The e169 also has problems. There are many bug reports, with the advice I was given at the end being 'update the modem firmware using a Windows PC'. I had to laugh.

Hello thecityofgold2006 (nice account name there). If I reboot the laptop with the E220 in place, then it connects fine with the 'default' settings for my service provider (UK t-mobile). The issue I'm having is that the E220 is identified as a storage device when it is plugged in during a session. I'm not sure that is going to be solved by any firmware upgrade, but I'll check out the bug report and see.

If anyone has a simple explanation of what has changed since 9.04 when this same modem 'just worked' I'd love to read it.

---

### Post by phillw on 2010-04-20
> **keithpeter said:**
> 

If anyone has a simple explanation of what has changed since 9.04 when this same modem 'just worked' I'd love to read it.

Also worked fine with 9.10 and alpha1 of 10.04, they broke something. If i boot from the 'official' 9.10 cd, it works fine - but not an updated system. ditto with 10.04 - I've tried to explain this but my pleas seem to fall on deaf ears :-(

[http://ubuntuforums.org/showthread.php?t=1352578](http://ubuntuforums.org/showthread.php?t=1352578) Was when I had it working with 10.04

It is very frustrating :confused:

Phill.

---

### Post by phillw on 2010-04-20
bump and request to be joined to [http://ubuntuforums.org/showthread.php?t=1458103](http://ubuntuforums.org/showthread.php?t=1458103)

That is as much information as I can give.

Regards,

Phill.

---

### Post by keithpeter on 2010-04-20
> **phillw said:**
> Also worked fine with 9.10 and alpha1 of 10.04, they broke something. If i boot from the 'official' 9.10 cd, it works fine - but not an updated system. ditto with 10.04 - I've tried to explain this but my pleas seem to fall on deaf ears :-(

Well, that is something to work from. A list of changed packages focussing especially one ones to do with usb, storage, and, I guess, responding to events might reveal what has changed.

What an update breaks, an update will restore, and if enough people report problems with modems not being recognised like this I'm sure there will be effort focussed on the problem!

Note: running sudo usb_modeswitch results in an error message about missing the /etc/usb_modeswitch.conf file. I'm using the version of usb-modeswitch in the Lucid repository. I'll start reading the docs and see where we are with the release candidate live disc.

---

### Post by phillw on 2010-04-20
I've asked that [http://ubuntuforums.org/showthread.php?t=1440262](http://ubuntuforums.org/showthread.php?t=1440262) be merged with this one, as it has all I have managed to find in the absence of being asked anything further.

Phill.

---

### Post by phillw on 2010-04-20
Can we herd all the bugs over to [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/529794?comments=all](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/529794?comments=all)

We stand a chance that someone may notice them.

Regards,

Phill.

---

