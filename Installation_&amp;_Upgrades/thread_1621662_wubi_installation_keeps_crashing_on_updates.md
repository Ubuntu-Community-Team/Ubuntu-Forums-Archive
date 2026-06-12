---
title: "wubi installation keeps crashing on updates"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by Exorbio on 2010-11-14
Hello all, I'm very new to Linux and Ubuntu (about 2 days) and am having a hard time getting Ubuntu to work.  I'm not completely sure that I'm posting in the right forum since I have several issues.  I can't tell what's causing what.

I'm using the wubi installer for version 10.10 (i386 - 32 bit). I have an AMD 64-bit, but the wubi installer for that only crashes when I try to boot it the very first time.  I get a blank screen and my tower is silent.  Version 10.04 does the same.  Version 10.10 is the only one that gets me somewhere.

So, I installed ndiswrapper and the proper driver for my USB adapter. Now I have 2 main problems:

1). the most relevant to this board is that when I use the update manager to get all 135 updates, I'm prompted to reboot to complete the installation.  When I do that, i get the same blank screen and silent tower treatment.  Oddly enough however, when I went back to windows, uninstalled ubuntu, then reinstalled it again using wubi, the update manager said that I already updated an hour ago (!?!?.. I assume it's still reading the old files from the previous install attempt).  Unfortunately I messed it up anyway trying to fix my second problem...

2). my internet connection fails here and there.  I don't know if it's ndiswrapper or the driver or what.  Once it fails, it won't reconnect.  I have to go into ndiswrapper, delete the current driver and reinstall it.  This has happened to me while on the internet (scouring these forums) and while downloading the updates and whenever it feels like it.

Also, the system does freeze up on me here and there as well.  Sometimes when I'm using ndiswrapper.  Sometimes when I'm authenticating myself. Sometimes in update manager and sometimes in synaptic.
Right now it's working.  But I haven't updated yet and I'm afraid to try.

Sorry If I've been too wordy about all of this.
Please help...

---

### Post by bcbc on 2010-11-14
> **Exorbio said:**
> Hello all, I'm very new to Linux and Ubuntu (about 2 days) and am having a hard time getting Ubuntu to work.  I'm not completely sure that I'm posting in the right forum since I have several issues.  I can't tell what's causing what.

I'm using the wubi installer for version 10.10 (i386 - 32 bit). I have an AMD 64-bit, but the wubi installer for that only crashes when I try to boot it the very first time.  I get a blank screen and my tower is silent.  Version 10.04 does the same.  Version 10.10 is the only one that gets me somewhere.

So, I installed ndiswrapper and the proper driver for my USB adapter. Now I have 2 main problems:

1). the most relevant to this board is that when I use the update manager to get all 135 updates, I'm prompted to reboot to complete the installation.  When I do that, i get the same blank screen and silent tower treatment.  Oddly enough however, when I went back to windows, uninstalled ubuntu, then reinstalled it again using wubi, the update manager said that I already updated an hour ago (!?!?.. I assume it's still reading the old files from the previous install attempt).  Unfortunately I messed it up anyway trying to fix my second problem...

2). my internet connection fails here and there.  I don't know if it's ndiswrapper or the driver or what.  Once it fails, it won't reconnect.  I have to go into ndiswrapper, delete the current driver and reinstall it.  This has happened to me while on the internet (scouring these forums) and while downloading the updates and whenever it feels like it.

Also, the system does freeze up on me here and there as well.  Sometimes when I'm using ndiswrapper.  Sometimes when I'm authenticating myself. Sometimes in update manager and sometimes in synaptic.
Right now it's working.  But I haven't updated yet and I'm afraid to try.

Sorry If I've been too wordy about all of this.
Please help...
Please list your hardware including graphics card and wireless. Sometimes you need a workaround to boot with certain graphics cards. this is likely what is happening. And probably also the cause of the intermittent freezing.

PS Update manager always says something like 'last updated 1 hour ago when you install for the first time. It's not very 'intelligent'. E.g. if you open it up yourself it says 'No updates are available' but then you hit Check and only then it finds that there are in fact updates available.

---

### Post by Exorbio on 2010-11-14
AMD Phenom X4 9100-e Quad-core
ATi Radeon HD 3200 Integrated Graphics
Wireless Adapter: ZyXEL G-220 v3

I know about having to check for updates.  Even after the check it was saying that there is nothing to update.

---

### Post by Exorbio on 2010-11-14
oops!  Should be "9100e".  No dash.

---

### Post by bcbc on 2010-11-14
Sorry - I was out for a few hours...

So for wireless - I found this link [http://ubuntuforums.org/showthread.php?t=1309018](http://ubuntuforums.org/showthread.php?t=1309018) (but it sounds as if you've already done this).

For the HD3200 did you go to System, Admin, Hardware drivers and see if there is a driver to enable?

---

### Post by Exorbio on 2010-11-14
Yeah, I've done that.  Thanks though!

As for System > Admin > Hardware Drivers....
Do you mean in Windows 7? Ubuntu? Gnome Terminal?  Or maybe the boot menu?
I'm thinking you mean Ubuntu.  If it's what I think it is then yes.  But I'll double check.  I need to switch over to Ubu.
(BTW, I don't know hardware really, so I'm not sure if this matters, but it is an integrated graphics card.  However, I know there are drivers in the device manager for win7.)

---

### Post by bcbc on 2010-11-14
> **Exorbio said:**
> Yeah, I've done that.  Thanks though!

As for System > Admin > Hardware Drivers....
Do you mean in Windows 7? Ubuntu? Gnome Terminal?  Or maybe the boot menu?
I'm thinking you mean Ubuntu.  If it's what I think it is then yes.  But I'll double check.  I need to switch over to Ubu.
(BTW, I don't know hardware really, so I'm not sure if this matters, but it is an integrated graphics card.  However, I know there are drivers in the device manager for win7.)
Yes I meant in Ubuntu.

What's the machine brand/model?

---

### Post by Exorbio on 2010-11-14
The make and model:
Gateway DX4200-09

However, I believe you have definitely helped me at least in part and hopefully completely.  I know I checked that driver menu before and got nothing.  However, this time there was a download for ATi drivers.  After having ndiswrapper drop the USB Adapter driver again, I had to reinstall that first.  When I downloaded that ATi driver, that was one of the longest progress bars in my LIFE!!  Haha.

Now before I get all happy, I'd rather stay skeptical.  When I was prompted to restart Ubu, I did so and got some weird behavior.

I kept getting this output on the whole screen when I selected Ubuntu:

```

hub 2-0:1.0: cannot reset port 3 (err = -108)
hub 2-0:1.0: cannot enable port 3. Maybe the USB cable is bad? 
hub 2-0:1.0: hub_port_status failed (err = -108)
BUG: soft lockup - CPU#3 stuck for 61s! [ntos_wq:643]
Process ntos_wq (pid:643, ti = f1a34000 task  = f2928cb0 task .ti = f1a34000
Stack:
Call Trace:
Code: 90 e4 92 5d c0 89 86 8c 01 00 00 8d 43 04 e8 2d bc 46 c8 31 c0 c7 03
01 00 00 00 89 73 1c ba 01 00 00 00 87 17 85 d2 74 09 f3 90 <83> 3f 00 74 f3
eb f7 8b 1c 24 8b 74 24 04 8b 7c 24 08 89 ec 5d
INFO: task ureadahead:340 blocked for more than 120 seconds

```

over and over again. it also mentioned a command I could type to disable the message (though I couldn't type anything anywhere) and made some mention about not being able to start ndiswrapper.  I don't know if everything there is accurate.  I was scrambling to write it down.

Since it was stuck like that, I turned off the tower and rebooted into Ubuntu...  

It came up this time! The ATI Catalyst Control Center shows in System > Preferences.  I have more resolution options and the colors look better.  This has helped a lot.

So, you think that this was causing my crashes and (hopefully) my issues with ndiswrapper? I am getting better signal strength now, but that could be coincidental.  I'll remain cautious for awhile.  I still need to try to download the updates.

In any case things seem to be getting better.  THANK YOU!!

---

### Post by Exorbio on 2010-11-15
Actually, I am still have problems with ndiswrapper.  I still lose access and have to uninstall and reinstall the USB adapter driver... but I haven't crashed yet:)

---

### Post by bcbc on 2010-11-15
I searched around and there are other bug reports with the soft lockup on ntos_wq - it's related to ndiswrapper. But they are all for older Ubuntu releases and none I found were resolved (e.g. [https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/380186](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/380186))

How did you install ndiswrapper? 

PS it might be a good idea to create a thread in the Networking and Wireless subforum and get some expert help.

---

### Post by Exorbio on 2010-11-15
I'll take a look at that later.  I have an exam.

I installed ndiswrapper from the install cd.

As for making a topic in the other section, I did that shortly after I made this topic.  No one ever responded though.  I'll have to bump it.

---

### Post by bcbc on 2010-11-15
> **Exorbio said:**
> I'll take a look at that later.  I have an exam.

I installed ndiswrapper from the install cd.

As for making a topic in the other section, I did that shortly after I made this topic.  No one ever responded though.  I'll have to bump it.

I wonder whether you should create a bug...
ubuntu-bug ndiswrapper

I suppose you could try the 32-bit ubuntu again - you might be able to get it to boot by trying a workaround e.g. adding nomodeset to the boot up parameters. [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Exorbio on 2010-11-21
bug?  You mean reporting my problem as a bug?

I don't think I need to reinstall.  I've already done that many times.  The system isn't crashing anymore thanks to installing the ATi driver.  My only problem now is with ndiswrapper.  But no one from the wireless forum will respond to my topic...:sad:

---

### Post by bcbc on 2010-11-22
> **Exorbio said:**
> bug?  You mean reporting my problem as a bug?

I don't think I need to reinstall.  I've already done that many times.  The system isn't crashing anymore thanks to installing the ATi driver.  My only problem now is with ndiswrapper.  But no one from the wireless forum will respond to my topic...:sad:

Yes, it seems like you've found a bug in ndiswrapper. I know that it works (I use it on one comp), but maybe there's something about your setup that's a problem. And if not, maybe someone who knows something will see it and help you.

Just run 'ubuntu-bug ndiswrapper' and it should collect all the log files etc. that'll be needed for someone to figure it out.

---

