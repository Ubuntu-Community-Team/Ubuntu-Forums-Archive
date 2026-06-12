---
title: "Wireless card not working after upgrade!!!!!!!!!!!"
date: 2006-08-03
forum: Installation &amp; Upgrades
---

### Post by kvalis on 2006-08-03
Installed 6.06 yesterday, but system stopped during reboot. Not being able to wait for replies, I took my Ububtu 5.10 install CD and installed it. I had to find out if my DLink DWL-G520+ was working under Ubuntu - I have tried so many distros with no luck.

I was so pleased that it worked straight after reboot. I was in heaven. So, what do we do - yes, we upgrade to 6.06 over the net.
Time consuming yes, but that did not matter.

Alas, after the upgrade and reboot was done - my wireless card is no longer working.

Could that be that the old drivers are replaced??? 

Any good ideas??? If it involves any code, please supply it.

Thank you in advance.[COLOR="black"][COLOR="black"]****[/COLOR][/COLOR]

---

### Post by Dr. Nick on 2006-08-03
The 5.10 to 6.06 update included installing a new kernel, all the drivers are supplied by the kernel.

If you reboot look at the initial grub screen that appears, You will see a list with several choices on what to boot, Pick the older kernel version from that list and see if your card works after that.

If it works run this command and save the output to a text file or something

lsmod

then reboot into the default (new) kernel and re run lsmod and compare the outputs. 

lsmod list what drivers are running

May also look here
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by kvalis on 2006-08-03
Dr.Nick

Did as requested, tried both 2.6.12-9-386 and 2.6.12-9-386 *recovery mode,
but the lamp did not light up on any of the 2 tries, and no wireless device came up when I typed in iwconfig.

The card lights up with the current kernel, and I have copied it for you all to see. Had to activate eth0 to send this to the forum.

> tore@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"Nytun"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=48/100  Signal level=27/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

tore@ubuntu:~$

What now?

---

### Post by Dr. Nick on 2006-08-03
well according to iwconfig it looks like its working

How do things look in system-administration-networking?

I have always had better luck disabling eth0 to use wireless, Do you have any wep enabled that could cause a error?

---

### Post by kvalis on 2006-08-03
Interface name = wlan0
ESSID = Nytun
Key type = hexadecimal
Connection = DHCP

No WEP

---

### Post by kvalis on 2006-08-07
Have not yet got a solution to this - 3 days are gone. Can you assign an access point manually - and how do you go about it??

Have gone through a troubleshooting guide - but no closer to solving it.

I think I will go back to Ubuntu 5.10 - there my wireless card worked straight away. Are there any config files I should save for later so that I can compare these config files with those 0f 6.06 after I have upgraded again??

Please help me.

Kvalis

---

### Post by Dr. Nick on 2006-08-07
You can set it manually in the networking gui i believe, or maybe look into the interfaces file "/etc/network/interfaces"

the config file

/etc/network/interfaces

may be helpful. Also you could install 5.10 and then only update parts of it. You can go into synaptic and lock packages that you do not want to upgrade. I would reccomend locking the kernel "linux-image-2.6xx" is the name. That is usually what controls all drivers


Sorry I couldnt be more helpful, I have never had my card disapear like this

I would compare "lsmod" outputs between them aswell to see if it is using a difernet dirver

---

### Post by kvalis on 2006-08-07
Thanks for feedback Dr.Nick

Checked /etc/network/interfaces and it goes like this:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.


# The primary network interface
iface wlan0 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid Nytun

iface eth0 inet dhcp

auto wlan0

_Please note wireless-mode managed!!_

When I run wifi-radar, the program lists it as auto.

Is it a matter of changing the config file to auto instead of managed, could it be as easy as that????


Kvalis

---

### Post by Dr. Nick on 2006-08-07
You could try that I suppose, I just checked my interfaces file and do not even have the line tier at all. that may be because I am not on a wireless conection at the moment though

---

### Post by kvalis on 2006-08-07
I have just reinstalled to 5.10, and my wireless card is working fine. This time the iwconfig looks like this for wlan0.

wlan0     IEEE 802.11b+/g+  ESSID:"Nytun"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:A5:03:64:04
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=48/100  Signal level=27/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

A different driver this time, so I have copied iwconfig and lsmod into a text file, so that I have a bit more info after I have updated to 6.06 again.

Now it is time for a sleep!

Kvalis

---

