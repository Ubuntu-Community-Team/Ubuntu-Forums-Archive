---
title: "Dell Inspiron 1764 no video during and after install"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by jokeronthego on 2010-02-08
I have a brand new Dell:

Inspiron 1764
Intel Core i5
M430 2.27GHz
4 GB Ram
Onboard Intel Graphics Media Accelerator HD
Currently running Win 7 Pro

I have been running Unbuntu 8.01 for 2 years. When I run the wubi install everything goes fine; however, when it reboots to the Unbuntu, to finish the install my screen goes black. Ubuntu complete the install complete with welcome music but I still can't see anything. 

I've tried the 32bit, 64bit CD/DVD and even tried it booting it from a USB stick.

Does any one have a suggestion and a fix?

Thanks in advance

---

### Post by Moon-e on 2010-02-09
Hi There. I bought a 1764 from BB this past weekend, hoping to
create a dual boot win7/fedora machine out of it.  I  used
the win7 disk utility to free up space in D:


The fedora live installation CD would load but quickly become 
stuck with a black black screen, similarly with the fedora dvd.  
I have not tried ubuntu, but it sounds like you're having the
same problem.



Opensuse faired better, it installed grub but not a working
linux system.  I tried restoring win7 using the disk image 
on the hard drive with no luck.  I guess I'll have to try 
reinstalling the [URL="http://www.computing.net/answers/linux/linux-mint-display-not-loading-on-install/30469.html#"][COLOR=blue][COLOR=blue ! important][FONT=Verdana][COLOR=blue ! important][FONT=Verdana]operating [/FONT][/COLOR][COLOR=blue ! important][FONT=Verdana]system[/FONT][/COLOR][/FONT][/COLOR][/COLOR][IMG]http://kona.kontera.com/javascript/lib/imgs/grey_loader.gif[/IMG]
[/URL]  from the CDs provided
by dell.    I wonder if linux having trouble with the display or
graphics card?


I would be very much interested in hearing your progress in
installing linux on your i1764, since it's the primary reason
I bought the laptop.

---

### Post by jokeronthego on 2010-02-11
I just tried to boot a live CD of Dream Linux, it didn't like the video card either.

---

### Post by tammersalem on 2010-02-14
I have the same problem - just purchased Dell 1764 with Intel i5 and video is not wokring (or not supported most likely).

After some investigation I found out that the graphics card is an Intel (I believe it's embedded). It's called Intel GMA HD and I've attached a text file with the specs (it has the exact version numbers).

Intel definitely does not have a linux driver, so it looks like one has to be developed.

---

### Post by jokeronthego on 2010-02-15
The only solution I have found that worked it to run it using VMware and loading it there. So far it's working good; however, I hope soon there is a release that will work with this Dell 1764. Let me know what you guys think.

I tried, Dream Linux, gOS, Ubuntu Studio, and a earlier versions of Ubuntu. VMware  is the only way now.:D

---

### Post by jokeronthego on 2010-02-15
I just got done with an online chat Dell support. The Inspiron 1764 got on the market 07jan10, at this point, Dell does not offer a variant of the Ubuntu source code to support the onboard video chip for the Inspiron 1764. We may be out of luck until either Dell supports it or the next version of Ubuntu comes out. 

Just gotta wait and see and live Ubuntu through VMware

---

### Post by Moon-e on 2010-02-17
Gosh, I really wish I would have held off on the 1764 purchase.  The laptop is
not very useful for me until I get a full version of linux installed (Fedora is my
preferred flavor).

---

### Post by manishmahabir on 2010-02-22
i have recently bought an inspiron from dell with core i5 and intel onboard graphics card...tried to boot from pen drive in karmic...no video..but login sound is audible...has anyone tried the lucid lyx?

---

### Post by Moon-e on 2010-02-23
Hi Manishmahabir, that was a good suggestion.  I just downloaded and tried
out the lucid alpha live cd.  It booted into full screen resolution (I heard the login
sound, too).  The machine locked as soon as I tried to pull down a menu but
it gave me confidence that the 1764 will be supported by the next stable version
of ubuntu.  That is really good news!

-M

---

### Post by hvackevin on 2010-02-24
To get Karmic running on the 1764, install from the Live CD in safe graphics mode.  This will give you a low resolution screen on start-up.  With some configuring, you can get the resolution set but you cannot use Compiz at all or it will lock up on mouse movement or menu drop.

---

### Post by manishmahabir on 2010-02-27
Why don't you guys provide your feedback at this launchpad bug...

[https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/518938](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/518938)

---

### Post by opiec123 on 2010-03-09
Solution:
:KSInstall works fine, hit F4 on live CD. Select safe graphics mode.:KS
Resolution comes up as 1024 x 768 at first.

---

### Post by Moon-e on 2010-03-09
I beg your pardon, I've installed Ubuntu on my 1764 in safe graphics
mode but I don't know how to now proceed to configure Xwindows into
the full graphics mode.  Could you point me towards the appropriate
web resources?    Many thanks if you can.

---

### Post by march3123 on 2010-03-11
Here are the steps I took to get a working 9.10 system.  

**Install**
As mentioned in this thread, on the installation screen hit f4 and select Safe Graphics then the installation should work.

**Wireless**
Odds are your wireless is not working as there is a bug with the Broadcom wireless detection during install.  To fix the problem, plug your computer into a wired connection and update the machine (System->Administration->Update Manager).  After the machine is fully updated (and rebooted), enable the Broadcom driver.  (System->Administration->Hardware Drivers).   The wireless should work now.

**1600x900**
Make sure your ubuntu install is fully updated.  I had problems with "Visual effects" crashing the system once higher resolutions were restored so disable it (System->Preferences->Appearance->Visual Effects and select  "None"). To restore 1600x900 resolution, back up and remove the file "/etc/X11/xorg.conf" (or simply rename it) .  Reboot.  Your system should start up in 1600x900.  

There are probably better ways to do this, but everything seems to be working fine.  Cheers!

---

### Post by Moon-e on 2010-03-11
Thank you, your instructions worked flawlessly.

---

### Post by gstanden on 2010-03-28
Just wanted to add that I tested the lucid lynx 10.04 beta using wubi and the GMA HD video appears to be supported - as I had high resolution video support.  I had the same problem described in this thread when I tried out 9.10 karmic with the Dell i1764. So, I'm waiting patiently now for the lucid lynx release on April 29...

---

### Post by simonmeaden on 2010-03-29
*I also have a Dell Inspiron 1764 and after trying virtually everything else I installed the new Fedora 13 Alpha *release which works with the display out of the box. admitedly it tells me that it is NOT for use, only for test purposes at least it shows that we will soon have a viable system.

---

### Post by blecha on 2010-03-30
This thread was great help for my installation of Ubuntu 9.10. Since this is the only one dealing with Dell 1764 and some comments are slightly misleading I will  summarize my story.
I installed from the CD on Dell 1764 with Windows 7 factory installed (Note that upgrading from 8.04 will be a different story). I used the F4 key and Safe Graphic mode as described by march3123 to start  the installation. 

When reaching partitionning I had scary message about the unability to write on the Linux partition and the system crashed. Next time it went ok. Note that I am not sure I answered correctly. I just mention this event for completeness. 

GRAPHIC CARD

I had no other problems and the machine rebooted in 1024x768 resolution. The /etc/X11/xorg.conf showed the “vesa” driver installed. I moved this file to xorg.conf.orig and rebooted. Then I had the full choice of resolution and machine booted in 1600x900. Note that  if you upgrade from 8.04 (I did this on the backup USB drive) you have directly the 1600x900 resolution. Useful quick look to: 

head /var/log/Xorg.0.log



X.Org X Server 1.6.4

Release Date: 2009-9-27

X Protocol Version 11, Revision 0

Build Operating System: Linux 2.6.24-23-server i686 Ubuntu

Current Operating System: Linux husa 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686

Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-21-generic root=UUID=8a5dcf4c-153c-439b-8c5a-683c9feec25b ro quiet splash

Build Date: 04 March 2010  09:56:47AM

xorg-server 2:1.6.4-2ubuntu4.2 (buildd@) 

	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)


I started to work and after few minutes screen freezed. I rebooted and removed the VisualEffects (System->Preferences->Appearance->Visual Effects and select "None") and I was done with screen installation.

WIFI

Few problems here. I have U.S.*Robotics Wireless MAXg ADSL Gateway with  beta-release firmware necessary to make the integrated wireless print server working under CUPS (Version: 3.10L.01.08 (Thu 26 Jun 2008 02:45:00 PM CET) 1445_062608-3.10L.01.A2pB023c.d20e). I use fixed IP's on my LAN and have security WPA (PSK) with TKIP and AES encryption in my router. I set WPA & WPA2 under wireless security (Preferences  - Network Connection - Wireless – Edit – Wireless Security) in UBUNTU. It seems that there is not standard notation of various security setups. If you have problems try first without security. I experienced some problems to enter my IP address under IPv4 Setting (should hit “Enter”  key after the entry of each field of the “Addresses” line). It would be nice to have  usual help button on “ Network Connection” tool.

The WIFI worked after that but I had no access to the WAN Internet. I added my WAN and LAN (192.168.1.1) routers to the DNS IPv4 Setting which solved the problem. WARNING: do not edit /etc/resolv.conf by hand as suggested by some threads ! The “Network Connection” tool will overwrite this file.

KEYBOARD

I am using US keyboard but I also need to type the foreign characters. In 8.04 I used the left-Win key as  a “Compose” key. The Keyboard - Preferences – Layouts – Layout option – Compose key position tool gives the possibility to configure that, but I had no success. Only the “Right-Alt” key works as the Compose correctly. I used Dell laptop Inspiron 6xxx/8xxx keyboard model config and this is probably the reason of my problem.
 
SOUND

I did not found the way to suppress the Login music. I tried the 
sudo -u gdm gconftool-2 --set /desktop/gnome/sound/event_sounds --type bool false
but it did not help

---

### Post by markusf21 on 2010-04-18
Just yesterday my brother and I went shopping for his new laptop. We picked up a Dell Inspiron 1764. I tried both the 32 and 64 bit Karmic CDs. Could not start Live CD or installer. I decided to try the Lucid Beta 2 CD. Live CD worked pretty well. Installed just fine. There was no sound at first boot. I ran update manager and restarted. Now we have sound and the correct video resolution. All in all pretty painless. I have not tested to see if the built in webcam works. But what he uses works perfectly.

---

### Post by Moon-e on 2010-04-20
> **simonmeaden said:**
> *I also have a Dell Inspiron 1764 and after trying virtually everything else I installed the new Fedora 13 Alpha *release which works with the display out of the box. admitedly it tells me that it is NOT for use, only for test purposes at least it shows that we will soon have a viable system.

I think I ideally would like to turn my 1764 into a dual-boot win/Fedora setup.  A while back I
installed karmic ubuntu using the helpful advice from people on this thread but I was unable
to install some rpm packages that are vital to my work.

Has anyone tried out a Fedora 13-beta install on the dell 1764?  I tried last night but I was
not successful.

-Mike

---

