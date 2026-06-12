---
title: "Install Issue: Menus Populated with blank white box"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by metafunction on 2011-02-27
Just installed Ubuntu 10.10 Netbook on my Dell Vostro 1000.

Install seemed to go through ok, although I am not connected to the  internet.  When the install completes, I have the default background  image and er... that's it.

Around the edge where the menu should be, the background image is  slightly darker.  If I move the mouse to where the menu items should be,  rather than what I assume would be a text label/description of that  menu item, I get a blank white box instead.  If I click, some of the  applications do indeed open, albeit without titlebars.


I am new to Linux, I decided that it should be about right for me to  make the switch, but encountering such an issue so early on isn't  inspiring me with much confidence.

I have access to this Windows machine for downloading and burning CD/DVDs.  I  also have a WD Passport drive (150Gb) and a USB stick (1Gb).


I really would like to give Ubuntu a fair test.

---

### Post by quixote on 2011-02-28
> I really would like to give Ubuntu a fair test.Good for you! :mrgreen:

Somehow or other, even though your install seemed to go okay, it didn't.  It's missing major components of the desktop*.  Troubleshooting that sort of thing is a nightmare, and only worth doing if otherwise you'll lose vital data.  Since I assume you haven't actually been able to use the system, and so there's no data to lose, the simplest solution is to try a reinstall.  I'd suggest a new download and a new burn of the CD or liveUSB, just in case the problem was with the install media.  

You may also want to try the ["Long term support" version, 10.04]("http://releases.ubuntu.com/lucid/"), instead, just in case there's some incompatibility between your system and 10.10.

You mention not being connected to the internet.  Is that on purpose, or is that another problem with the install?  If it's a problem, that's yet another sign there was a faulty install.  Connectivity has pretty much just worked since Gutsy Gibbon, over three years ago.


*This isn't as stupid as it sounds. :D  I mean missing major components of the array of packages involved in creating a functioning desktop.

---

### Post by metafunction on 2011-03-02
Hi Quixote, I've tried new downloads and different media with the same result; so I shall try out the "Long term support" version, 10.04 and let you know what happens.

With regards to connectivity; would it be best to go in hardwired to my router as I hear Broadcom Wireless cards can be problematic with new system installs?

Thanks again.

---

### Post by metafunction on 2011-03-02
Update:

That version appears to be up and running!  Woop!

Although the Wireless is not detected at all.  I'm currently running through a removal and reinstall of DKMS so we'll see what that does.

Incidently I have no idea what I'm talking about, but I worked in IT many moons ago so i have vague, fundamental understanding.

---

### Post by quixote on 2011-03-02
I put "Dell Vostro 1000" in the Search field, just to see what would come up in the forums, and it sounds like there's plenty of good old Dell barely-compatible hardware in that one, so that may be why you're having problems.

(It's one of my pet peeves that this sort of thing is not the doing of Linux.  The manufacturers refuse to talk to open source developers, so they wind up having to -- legally! -- reverse engineer things to make it work. Broadcom is the classic example.)

What happens if you don't install, just boot with the LiveCD?  I assume then you do have a desktop?  But no wireless, right?  Try booting with a liveCD, and at the screen where it says "Press F2 for boot options" --or something like that-- press it. Select the "safe graphics" option (I think it's under the third set of options??)  Then press F6, the last set of options, to enter your own boot options, and type in```
noapic nolapic
```.

Once it's all the way booted, after a brief rest, it ought to say it's found proprietary drivers for your wireless and do you want to install them.  Say yes.  It won't retain that for the next boot, since you're on a liveCD, but it'll install it for that one session and then you can see whether your Broadcom wireless will work after a regular install.

The graphics may look crude, but don't let that worry you. That gets fixed later.  If everything is there and works, then, when you install, *use those same options*. (If you just go to install after trying it with those options, they'll be in force.)

If and when it installs correctly, then you can bring the graphics up to speed with better drivers. Usually, it will pop up suggested drivers, like it does for the wireless.  My favorite for Nvidia graphics is the nouveau driver (search for "nouveau" in System > Administration > Synaptic), but others swear by Nvidia's own drivers.  Search the forums for "Nvidia" and "Dell Vostro 1000" to see what other people's experiences have been.

I hope it starts cooperating for you! In my experience, once you're free of all the bloatware, the virus onslaught, and have the repositories of programs at your beck and call, you'll never look back. :D (Linux has had "app stores" for years, except they're free.)

---

### Post by quixote on 2011-03-02
We seem to both be in the ether at the same time!

dkms is a package that helps load kernel modules. Useful.  and essential if you want to run virtualbox.

Good to hear it finally worked!

---

### Post by quixote on 2011-03-02
Re the wireless not being detected, I'd suggest searching the forums for your model of Broadcom chip and your model of computer.  Those can be a bear to troubleshoot.  Meanwhile, there's ethernet cables.:D

---

### Post by metafunction on 2011-03-03
Hey thanks for all that.  I'm floating about the ether from northern England if you wanna see how far the coincidence goes!

OK so I downloaded the Dell network drivers for my machine just in case they'd come in useful at any point.  They're sat in a folder on my new Ubuntu desktop :).

I'm in Hardware Drivers and the message says 
*No proprietary drivers are in use on this system*.

In the box below are two options:
Broadcom B43 wireless driver
Broadcom STA wireless driver

When I click to activate the B43 driver the search comes back with
[I]SystemError: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter_012-1build1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter_012-1build1_i386.deb) Could not resolve 'archive.ubuntu.com'
[/I]
When I click to activate the STA driver the search comes back with
*SystemError: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb) **Could not resolve 'archive.ubuntu.com'*

---

### Post by metafunction on 2011-03-03
I found an ethernet cable, plugged in, booted up, but it isn't connecting.  Light on router says it's all good.

---

### Post by metafunction on 2011-03-03
[SIZE=4]ARRRRRRRRRRRRRRRRRRRRRRRRRRRRRRGH!



[SIZE=2]I've been installing and removing and rebooting but no, no damn ethernet or wireless.  Nothing.  Nada.  [/SIZE][/SIZE]

[SIZE=2]I manually downloaded the Broadcom drivers, I tried installing but apparently it's already installed.[/SIZE]

[SIZE=2]So I went into [/SIZE][SIZE=2][SIZE=1][SIZE=2]Synaptic[/SIZE][/SIZE], completely removed bcmwl-kernel-source AND dkms.Then I reinstalled bcmwl-kernel-source.  Rebooted.  I'm still unable to activate the damn Broadcom card.


[/SIZE]

---

### Post by metafunction on 2011-03-03
OK, I've calmed down a bit now.

So I have just tried the following:
sudo apt-get --purge remove firmware-b43-installer
sudo apt-get --purge remove dkms
sudo apt-get --purge remove bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
sudo reboot

It didn't work.  So I tried:
System>Preferences>Network Connections - was going to go into Edit the connections but Wireless isn't appearing.  The ethernet appears to have come up as something along the lines of Auto Eht0, I edited this and made sure it was connecting automatically (unticked, applied, re-edited, ticked, applied).

It didn't work.  So I tried:
sudo rfkill unblock all
rebooted
Still no connection so I went back to try and activate the drivers and 
When I click to activate the B43 driver the search comes back with
[I]SystemError: Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...uild1_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter_012-1build1_i386.deb") Could not resolve 'archive.ubuntu.com'
[/I]
When I click to activate the STA driver the search comes back with
*SystemError: Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...untu3_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb") **Could not resolve 'archive.ubuntu.com'*


So a lot of fiddling with absolutely nothing happening.  I'm considering getting the lump hammer from the garage.

---

### Post by quixote on 2011-03-03
The only way I've gotten Broadcom drivers to work is using that nice little ubuntu box that offers to install the broadcom drivers for you. It's usually Broadcom 43. If you type "lshw" in a terminal it'll tell you more than you ever wanted to know, but buried in there, in one of the network sections, it'll tell you exactly which wireless hardware you have.

However, since ethernet isn't working either, the problem isn't just a bad wireless driver.  You mention downloading drivers.  Was that on another computer?  Or the same computer using another router?  Also, type "ifconfig" in a terminal, and copy the output to your answer here.

The "System failed to fetch" error probably is there because there's no connection.  You can also get that when the server you're trying to access is down, when a firewall is interfering in some way, and sometimes I've even got it when I was missing a public key.

It's a shame that your first experience with linux is so "thrown in at the deep end"! Sometimes it's effortless. Honest!

---

### Post by metafunction on 2011-03-03
I'm using a different laptop via the same wireless router to download and communicate with the outside world!

ifconfig
eth0     
Link encap: Ethernet HWaddr 00:1d:09:b5:5f:a0
inet6 addr:f80::21d:9ff:feb5:5fa0/64 Scope: Link
UP BROADCAST RUNNING MULTICAST MTU1500 Metric:1
RX packets:3522 errors:0 dropped:0 overruns:0 frame:0 collisions:0 txqueuelen:1000
TV packets:22 errors:0 dropped:0 overruns:0 frame:0 collisions:0 txqueuelen:0
RX bytes:1181943 (1.1 MB) TX bytes 6028 (6.0 KB)
Interupt 21

lo
Link encap : Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr:1/128 Scope:Host
UP LOOPBACK RUNNING MTU:19436 Metric:1
RX packets:144 errors:0 dropped:0 overruns:0 frame:0 collisions:0 txqueuelen:0
...TX packets:144 errors:0 dropped:0 overruns:0 frame:0 collisions:0 txqueuelen:0
RX bytes 10944 (10.9 KB) TX bytes 10944 (10.9 KB)
Interupt 21



I actually found this in my travels: 
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) - drivers
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt) - instructions

[FONT=Arial][SIZE=2]
But if you look at the readme file I fall at the first hurdle [/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial][SIZE=2][I]If you try to build this module but get an error message that looks like 
this:

make: *** /lib/modules/"release"/build: No such file or directory. Stop.[/I]


I haven't a clue how I would install the files.  I downloaded them anyway and evenb chanced a look at them, but it beats me.
[/SIZE][/FONT]

---

### Post by metafunction on 2011-03-03
I just ran:

sudo dhclient -r
[I]Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:1d:09:b5:5f:a0
Sending on   LPF/eth0/00:1d:09:b5:5f:a0
Sending on   Socket/fallback[/I]

and then sudo dhclient
[I]Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:1d:09:b5:5f:a0
Sending on   LPF/eth0/00:1d:09:b5:5f:a0
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
[/I]
Then ifconfig
[I]eth0      Link encap:Ethernet  HWaddr 00:1d:09:b5:5f:a0  
          inet6 addr: fe80::21d:9ff:feb5:5fa0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2845325 (2.8 MB)  TX bytes:10957 (10.9 KB)
          Interrupt:21 

eth0:avahi Link encap:Ethernet  HWaddr 00:1d:09:b5:5f:a0  
          inet addr:169.254.7.235  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15936 (15.9 KB)  TX bytes:15936 (15.9 KB)[/I]

---

### Post by metafunction on 2011-03-03
Tried [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

But failed at 3.6.  The wireless just doesn't seem to be being picked up now :(

---

### Post by metafunction on 2011-03-04
Wireless works with the LiveCD... hmmm

---

### Post by metafunction on 2011-03-04
I'll mark this as solved and then open a new thread for the wireless issue.

---

### Post by quixote on 2011-03-06
Sorry it took me so long to resurface.  Real life, and all that.  The fact that wireless works with the LiveCD means it's not your hardware (obviously).  It's something about the setup.  Hmm.  Hope you have an answer in the new thread!

---

