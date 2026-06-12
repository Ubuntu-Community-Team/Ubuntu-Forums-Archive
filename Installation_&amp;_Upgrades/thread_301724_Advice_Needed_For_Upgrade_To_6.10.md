---
title: "Advice Needed For Upgrade To 6.10"
date: 2006-11-17
forum: Installation &amp; Upgrades
---

### Post by CKRDBD on 2006-11-17
I am using Kubuntu 6.06.  I haven't been able to get into the Kubuntu forums either in Linux or W2K, hence the reason I am posting here.  Please forgive me if this is the wrong venue.

I tried to upgrade from 6.06 to 6.10 and was not able to use my wireless any longer.  
The odd thing is that my system saw my wireless network, and everything seemed to be configured correctly.  I even did the "iwconfig" and verified that my wireless id and key were correct.  I have temporarily restored my 6.06 partition from a backup image.

My question is this:  Are there critical network files that I can backup prior to the upgrade and if so, what are these?  Could this be a firewall issue with the new upgrade?

One thing I have noticed with dismay is that Kubuntu lacks a basic upgrade function in it's DVD and CDs that the rpm based distros have:  When I used to use Mandriva, Fedora, etc, I was able insert the DVD into the drive, reboot the system and was presented with a GUI that gave me the option of installing a fresh system or upgrading.  Ubuntu/Kubuntu could really use such a feature.  This might resolve a lot of the issues surrounding upgrading that many users are experiencing, particularly with regards to the wireless, which, I've found, is much more difficult to configure on debian based systems than rpm based ones.

Please understand that I am not trying to run Ubuntu/Kubuntu down in any way.  I switched because I was tired of the constant excuses that Mandriva management continued to give it's user base when an advertised feature did not work right after a new release.  I really like Kubuntu and would like to continue to use it for as long as I own my pc.

Any suggestions would be greatly appreciated.  I am quite comfortable followng the command line instructions, as long as they're in plain English.

I tried again to update and now I can't get out on the net.  Here's the output of "iwconfig":

lo     no wireless extensions

wmaster0   IEEE 802.11G Frequency:2:412 GHz

wlan0      IEE 802.11G ESSID: "ACTIONTEC"
           Mode:Managed Frequency:2.412 GHz  Access Point:  Not-Associated
           Encryption key:off

sit0       no wireless extensions.



Here's the information in my /etc/n etwork/interfaces file:

auto wlan0
iface wlan0 inet dhcp
wireless-essid ACTIONTEC
wireless-key  (my wireless key)


auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


I really appreciate everyone for taking the time to read most post and update and I look forward to resolving this problem soon.

---

