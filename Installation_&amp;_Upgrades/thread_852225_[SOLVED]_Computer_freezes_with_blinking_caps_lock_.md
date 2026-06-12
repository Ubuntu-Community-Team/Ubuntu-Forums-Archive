---
title: "[SOLVED] Computer freezes with blinking caps lock and scroll lock leds"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by peterdm on 2008-07-07
I've attempted to install Ubuntu Hardy on an older PC. The live CD works, but as soon as I install and boot from HDD, the system becomes very sluggish until it freezes with 2 blinking keyboard leds: the caps lock and the scroll lock. I've already attempted some boot options as hinted by some threads on misc forums, but no such luck. More specifically, I've attempted various combinations of "noacpi", "noapic", "irqpoll" to no avail. Most of the time I am still able to log in, but the system is so sluggish I can't even open the logs. Opening a terminal takes ages, and typically I can't type anything. Eventually it gets into the blinking keyboard led state sooner or later.

The system:

Intel P3-450MHz (slot-A)
Asus P3B-F with BIOS 1006 (there is a later version 1008 but it's still beta, I haven't dared try it yet)
3Dfx Voodoo 3 graphics board
3 x 256 PC-133 RAM
1 wired ethernet card (some common Realtek chip)
1 wireless ethernet card (a more recent chip, dunno which one but the retail box was a D-Link)

Any ideas?
What do the blinking keyboard leds actually mean?

---

### Post by peterdm on 2008-07-07
I believe it has something to do with the wifi. When I boot from the livecd everything works fine until I try to enter a wireless network connection for the wifi. While booted from the livecd, I was able to take a peek into /var/log/messages on the hdd and it was filled with network error messages. Imho the wifi remains a major pain point in hardy... Even if updates were available, ss long as I don't have network I can't download any updates, which leaves me with a chicken-and-egg situation...

---

### Post by peterdm on 2008-07-08
Yes, it's definitely the wifi card that's the problem: it's a Texas Instruments ACX 111... Still no solution though... I'm going crazy trying to fix this installation, the system always freezes before I can do anything useful to try and fix it...

---

### Post by overdrank on 2008-07-08
> **peterdm said:**
> Yes, it's definitely the wifi card that's the problem: it's a Texas Instruments ACX 111... Still no solution though... I'm going crazy trying to fix this installation, the system always freezes before I can do anything useful to try and fix it...

Hi and please do not make multiple threads on the same issue.
[http://ubuntuforums.org/showthread.php?t=853098](http://ubuntuforums.org/showthread.php?t=853098)
If you have a wired connection can you try and update hardy 8.04 and maybe solve the issue. I had a similar issue with a desktop and wireless and I had to remove the card to install and then reinstall and worked fine after the updates.

---

### Post by peterdm on 2008-07-08
Sorry about the multiple threads... When I realized it was a networking issue I wanted to move this thread to a more appropriate forum so I started a new thread in the networking forum. From now on I'll just stick to this one.

Removing the wireless indeed fixes the problem (and allows me to update and investigate the system), but when I put it back in the problem reappears. But at the very least this allowed me to investigate the system some more. 

First I wanted to check if the firmware update during had happened successfully. I remember having read something about this somewhere on the sourceforge project homepage of the acx 111 driver. So in /var/log/messages I grepped the lines containing "firmware": 

> Jul  8 22:25:04 dolphin kernel: [   67.939055] acx: Loaded combined PCI/USB driver, firmware_ver=default
Jul  8 22:25:04 dolphin kernel: [   67.939073] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
Jul  8 22:25:04 dolphin kernel: [   67.950596] acx: loading firmware for acx1111 chipset with radio ID 16
Jul  8 22:25:04 dolphin kernel: [   84.011878] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===

So at least the firmware seems to have been updated correctly. So then I grepped for "wlan0":

> 
Jul  8 12:44:59 dolphin kernel: [ 5923.028757] wlan0: association FAILED: peer sent Status Code 1 (Unspecified failure)
Jul  8 12:45:01 dolphin kernel: [ 5925.528308] wlan0: association FAILED: peer sent Status Code 1 (Unspecified failure)
Jul  8 12:45:04 dolphin kernel: [ 5928.027868] wlan0: association FAILED: peer sent Status Code 1 (Unspecified failure)
Jul  8 12:45:06 dolphin kernel: [ 5930.527455] wlan0: association FAILED: peer sent Status Code 1 (Unspecified failure)
Jul  8 12:45:09 dolphin kernel: [ 5933.026980] wlan0: association FAILED: peer sent Status Code 1 (Unspecified failure)
Jul  8 12:45:18 dolphin kernel: [ 5941.881909] wlan0: association FAILED: peer sent Status Code 1 (Unspecified failure)
Jul  8 12:45:19 dolphin kernel: [ 5943.381206] wlan0: association FAILED: peer sent Status Code 1 (Unspecified failure)
Jul  8 12:45:22 dolphin kernel: [ 5945.880771] wlan0: association FAILED: peer sent Status Code 1 (Unspecified failure)
Jul  8 12:45:25 dolphin kernel: [ 5949.644277] wlan0: association FAILED: peer sent Status Code 1 (Unspecified failure)
Jul  8 12:45:27 dolphin kernel: [ 5950.879879] wlan0: association FAILED: peer sent Status Code 1 (Unspecified failure)
Jul  8 12:45:29 dolphin kernel: [ 5953.379421] wlan0: association FAILED: peer sent Status Code 1 (Unspecified failure)
Jul  8 12:45:32 dolphin kernel: [ 5955.879015] wlan0: association FAILED: peer sent Status Code 1 (Unspecified failure)
Jul  8 12:45:33 dolphin kernel: [ 5957.203299] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  8 12:49:54 dolphin kernel: [ 6218.048205] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success)
Jul  8 12:49:54 dolphin kernel: [ 6218.048233] wlan0: issue_cmd(cmd:0x0016) FAILED
Jul  8 12:50:50 dolphin kernel: [ 6274.277272] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success)
Jul  8 12:50:50 dolphin kernel: [ 6274.277301] wlan0: issue_cmd(cmd:0x0002) FAILED
Jul  8 12:50:50 dolphin kernel: [ 6274.278714] wlan0: configure(type:0x1010) FAILED
Jul  8 13:40:40 dolphin kernel: [   80.667304] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.24-19-generic
Jul  8 13:40:45 dolphin kernel: [   95.730670] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  8 13:41:37 dolphin kernel: [  148.227338] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success)
Jul  8 13:41:37 dolphin kernel: [  148.227367] wlan0: issue_cmd(cmd:0x0002) FAILED
Jul  8 13:41:37 dolphin kernel: [  148.228839] wlan0: configure(type:0x1010) FAILED
Jul  8 13:46:10 dolphin kernel: [  420.607875] wlan0: association FAILED: peer sent Status Code 1 (Unspecified failure)
Jul  8 13:47:05 dolphin kernel: [  476.104064] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success)
Jul  8 13:47:05 dolphin kernel: [  476.104093] wlan0: issue_cmd(cmd:0x0002) FAILED
Jul  8 13:47:05 dolphin kernel: [  476.105588] wlan0: configure(type:0x1010) FAILED
Jul  8 13:48:57 dolphin kernel: [  587.722015] wlan0: association FAILED: peer sent Status Code 1 (Unspecified failure)
Jul  8 13:56:16 dolphin kernel: [  202.588909] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.24-19-generic
Jul  8 13:56:21 dolphin kernel: [  217.908444] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  8 14:01:44 dolphin kernel: [  540.796687] wlan0: association FAILED: peer sent Status Code 1 (Unspecified failure)
Jul  8 14:03:36 dolphin kernel: [  652.478505] wlan0: association FAILED: peer sent Status Code 1 (Unspecified failure)
Jul  8 14:05:28 dolphin kernel: [  764.488712] wlan0: association FAILED: peer sent Status Code 1 (Unspecified failure)
Jul  8 14:07:19 dolphin kernel: [  876.263793] wlan0: association FAILED: peer sent Status Code 1 (Unspecified failure)
Jul  8 14:09:11 dolphin kernel: [  988.056553] wlan0: association FAILED: peer sent Status Code 1 (Unspecified failure)
Jul  8 14:11:03 dolphin kernel: [ 1099.627934] wlan0: association FAILED: peer sent Status Code 1 (Unspecified failure)
Jul  8 14:15:12 dolphin kernel: [   81.319388] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.24-19-generic
Jul  8 14:15:17 dolphin kernel: [   96.775035] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  8 14:16:06 dolphin kernel: [  145.305730] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success)
Jul  8 14:16:06 dolphin kernel: [  145.305759] wlan0: issue_cmd(cmd:0x0016) FAILED
Jul  8 14:18:10 dolphin kernel: [  270.078054] wlan0: association FAILED: peer sent Status Code 1 (Unspecified failure)
Jul  8 14:20:03 dolphin kernel: [  382.281409] wlan0: association FAILED: peer sent Status Code 1 (Unspecified failure)
Jul  8 14:21:55 dolphin kernel: [  494.181441] wlan0: association FAILED: peer sent Status Code 1 (Unspecified failure)
Jul  8 22:25:04 dolphin kernel: [   84.013189] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.24-19-generic
Jul  8 22:25:08 dolphin kernel: [   99.420797] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  8 22:27:25 dolphin kernel: [  235.805649] wlan0: association FAILED: peer sent Status Code 1 (Unspecified failure)


This doesn't look too good... I probably should try to pin-point the logging at the time the system freezes, but I've had enough for today, I'll start digging again tomorrow...

Ciao,

Peter

---

### Post by peterdm on 2008-07-09
Pheeew, I finally got it fixed thanks to hints in [this]("http://ubuntuforums.org/showthread.php?t=808205&highlight=ACX+111") thread.

This is what I did to get a stubborn acx 111 (branded D-Link AirPlusG+ DWL-G520+) working with WPA-PSK:

[LIST=1]
[*]Unplug the wireless card from the pci slot preventing the system freezes
[*]Disable network manager as explained [here]("https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager#Disabling%20NetworkManager")
[*]Create a /etc/wpa_supplicant.conf file as explained [here]("http://ubuntuforums.org/showthread.php?t=263136") (needed for wpa-psk)
[*]Edit the /etc/network/interfaces as explained by nick_h [here]("http://ubuntuforums.org/showthread.php?t=808205&highlight=ACX+111")
[*]Plug the wireless card back in the pci slot
[/LIST]

Reboot and tadaa! Wifi works!

---

### Post by peterdm on 2008-07-09
It seems I've cheered too soon... What is good is that my system does not freeze anymore and it gets an ip address. What is not so good is that it's an alien ip address not originating from my router. Internet still does not work. Since I'm on manual internet now (network manager disabled), I double-checked the /etc/network/interfaces and they contain only the wpa settings for my router, I have no idea where it picks up other settings.

Which tools can I use to inspect the ssid etc. of my current connnection?

---

### Post by peterdm on 2008-07-09
I finally got wireless working. It took me 2 days to figure it out, but I think I finally understand Ubuntu networking a little bit better. Let me summarize it for you, so one day it may save someone else some time:

My quest: to connect to the internet through a wireless router, using PSA-PSK as wireless authentication protocol. The network card is a **D-Link AirPlusG+ DWL-G520+** PCI card, which has a **Texas Instruments ACX 111** chipset. There is also a wired network card with a Realtek chipset in the same system, but that is not very relevant here since I really want to get the wireless to work.

Where it went wrong: after installation, I wanted to switch to the wireless interface. I had tried enabling WPA-PSK via System->Administration->Network, but as soon as I did that the system froze. It kept on freezing upon reboot.

Linux is about choices. The problem is that it's not always clear what the choices are and which ones to make. So here is a guide:

[LIST=1]
[*]Choose the driver for your card. There is an open-source driver for the chipset: [http://acx100.sourceforge.net/]("http://acx100.sourceforge.net/"), but the current version does not support WPA-PSK. The alternative is to use the ndiswrapper [http://ndiswrapper.sourceforge.net/joomla/index.php?/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/"), which is a Linux wrapper around the Windows driver. It requires you to download and unzip the windows drivers, but it works with WPA-PSK.
[*]Choose how you want to manage the network. Network manager [https://help.ubuntu.com/community/NetworkManager]("https://help.ubuntu.com/community/NetworkManager") is the default in Ubuntu, unfortunately it is still beta and it does not work well with this hardware in combination with WPA-PSK (it freezes the system). Network interfaces under control of network manager will show up as "Roaming" under System->Administration->Network. So the alternative is to disable network manager and manually manage the **/etc/network/interfaces**. The downside is that the nifty network status icons in the top right bar are gone. Check out the link to see how it's done.
[*]Choose the wireless authentication protocol. WPA offers better security than WEP, so I'll go for WPA. For WPA-PSK in combination with the ndiswrapper driver, you need wpa_supplicant [http://hostap.epitest.fi/wpa_supplicant/]("http://hostap.epitest.fi/wpa_supplicant/"). This means manually editing **/etc/wpa_supplicant.conf** and **/etc/network/interfaces**.
[/LIST]

```

peter@dolphin:~$ cat /etc/wpa_supplicant.conf 
ctrl_interface=/var/run/wpa_supplicant

network={
	ssid="myssid"
	scan_ssid=1
	proto=WPA
	key_mgmt=WPA-PSK
	pairwise=TKIP
	group=TKIP
	psk=thisisakeyinhex
}

```

```

peter@dolphin:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
pre-up wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

```

---

### Post by peterdm on 2008-07-21
Wireless interface only works as long as the wired interface is also connected... Not sure why???

---

### Post by ingeon on 2011-03-19
My problem is slightly different. 
Ubuntu Lucid_x64.

PC will has randomly start flashing Caps Lock and hang, then have to force a reboot.
Even did it before loading login screen today (while displaying boot splash)
I dont have a wireless device.
Read about Google chrome doing this but my Sync is disabled/not used.

What else could it be ?
I upgraded the latest stable kernel etc.

MSI P45 Neo-F
Core 2 E8500
8GB Ram
Nvidia GTX460

---

### Post by jwmck10 on 2011-03-19
I have the same problem but it has nothing to do with wireless or internet at all.  It does not matter what I am doing on my laptop.  Online or not, listening to music or not, the computer screen goes black, the computer freezes, and only the caps key blinks.  I have to disconnect the power and restart and as soon as it starts back up it does it again.  I have done a complete wipe and install of ubuntu 10.10 more than once.  It will run fine for about an hour then it will crash.   This is not a wireless or internet problem for me because it does this whether or not I try to get online.  I've also turned off my wireless card and it does the same thing.  Please help.

---

### Post by fabioportes on 2011-05-02
I turn my laptop (Dell Vostro 3300) on and just after GRUB it freezes and start blinking CAPS and SCROLL leds.
Then I have to hold the power button to turn it off.
Recently I upgraded to 11.04 and a set of problems started.
Damn...

---

### Post by fabioportes on 2011-05-02
> **fabioportes said:**
> I turn my laptop (Dell Vostro 3300) on and just after GRUB it freezes and start blinking CAPS and SCROLL leds.
Then I have to hold the power button to turn it off.
Recently I upgraded to 11.04 and a set of problems started.
Damn...
Root cause detected.
Using recovery mode I see VFS: Cannot open root device.
Unfortunately it seems I lost my partitions. ;(
Starting forensic...

Thanks,
fp;

---

### Post by fabioportes on 2011-05-02
> **fabioportes said:**
> Root cause detected.
Using recovery mode I see VFS: Cannot open root device.
Unfortunately it seems I lost my partitions. ;(
Starting forensic...

Thanks,
fp;
I tried booting from a previous kernel version and voilá!
OMG Ubuntu...
At least my documents are safe.

---

### Post by John_Rose1 on 2011-08-05
Hi, I have a Dell Vostro 3700 running Ubuntu 10.04 and Windows XP Professional under dual boot with Grub2. For a small percentage (2-3%?) I get a similar phenomenon as **fabioportes**: boot fails with caplock and scrolllock lights blinking. When I turn off manually and reboot, the machine invariably boots normally (I don't remember a case of this happening two times in a row). I am sure that at least some of the events are happening on launch of Grub2, but it is possible (I will check carefully) that some are after selection of Ubuntu in Grub2 menu (almost certain that none occur after selection of Windows in Grub2 menu). Otherwise Ubuntu is working fine. Since this is a rare and thus far unpredictable event, hard to see how to debug. I note that **fabioportes** mentioned "VFS: Cannot open root device" and wonder if this applies and if there is anything to do, any advice?
Best regards, John

---

### Post by stewieflow on 2012-02-08
I had similar problem after making regular update on Ubuntu Lucid 10.04
I have D-Link Wireless N 150 Pico USB Adapter
Dlink provides a Linux driver for that. It was working like a charm until Ubuntu was updated.

I solved it by simply blacklisting unnecessary drivers as suggested in
[http://kaustav.codebinders.com/2011/10/install-dwa-125-wireless-driver-on-ubuntu-11-10.html](http://kaustav.codebinders.com/2011/10/install-dwa-125-wireless-driver-on-ubuntu-11-10.html)


**************
Blacklist unnecessary drivers
Edit /etc/modprobe.d/blacklist.conf and add these lines:

blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb

**************

---

### Post by stewieflow on 2012-02-09
I solved my problem. All I had to do is to access Realtec website and install the latest driver compatible with the last Ubuntu Linux kernel update.

> **stewieflow said:**
> I had similar problem after making regular update on Ubuntu Lucid 10.04
I have D-Link Wireless N 150 Pico USB Adapter
Dlink provides a Linux driver for that. It was working like a charm until Ubuntu was updated.

I solved it by simply blacklisting unnecessary drivers as suggested in
[http://kaustav.codebinders.com/2011/10/install-dwa-125-wireless-driver-on-ubuntu-11-10.html](http://kaustav.codebinders.com/2011/10/install-dwa-125-wireless-driver-on-ubuntu-11-10.html)


**************
Blacklist unnecessary drivers
Edit /etc/modprobe.d/blacklist.conf and add these lines:

blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb

**************

---

