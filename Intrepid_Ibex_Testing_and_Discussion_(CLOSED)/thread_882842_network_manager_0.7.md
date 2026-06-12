---
title: "network manager 0.7"
date: 2008-08-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ccw on 2008-08-07
The NM 0.7 branch hit intrepid today: Can someone enlighten me if I'm doing something wrong here before I submit bug reports.

Straight up default dhcp works.

however, NM ignores /etc/network/interfaces including the static IP settings I have.

Whenever I try to add "manual" configs (I assume that means static) in NM, the OK button grays out and I can't save. I think this is somehow relate to consolekit because I never get asked for credentials to escalate my privileges.

---

### Post by phenest on 2008-08-07
Version 0.7.0 works fine here. I just had to re-enter the PSK. But, I have no notification icon, just a blank space. And the BlueTooth icon has also vanished too (related?).

EDIT: Icons turn out to be AWN issue.

---

### Post by Benjamin_Lebsanft on 2008-08-07
had to uninstall it because I couldn't get it to work. Same grey out problem of the ok button here.

---

### Post by caryb on 2008-08-07
I had to uninstall mine as well as I couldn't configure my wireless settings, at the moment there is no KDE front end to configure network mangler so it's kind of useless in Kubuntu.


Cary

---

### Post by Coleop on 2008-08-07
I can also relate to this issue had to start another computer to change my router to enable DHCP.  Works now but rather have it the way it was.

---

### Post by klange on 2008-08-07
Make sure you're entering valid information, especially for the prefix (which is something like 22 or 24 or whatever). I get the "OK" button with "Manual" selected when I enter "192.168.1.105"/"24"/"192.168.1.1", though it doesn't actually seem to do anything.

---

### Post by ccw on 2008-08-08
> **WindowsSucks said:**
> Make sure you're entering valid information, especially for the prefix (which is something like 22 or 24 or whatever). I get the "OK" button with "Manual" selected when I enter "192.168.1.105"/"24"/"192.168.1.1", though it doesn't actually seem to do anything.

Oh... that's CIDR prefix. I was trying to add a mask. The gateway isn't taking though. I type in the GW and hit ok, but then route will produce "0.0.0.0".  I'll go back into NM, and the GW will list "0.0.0.0" and any dns settings will be blanked out.


I personally prefer the CIDR prefix form, but I they should probably go back to mask: 95% of the population probably doesn't understand CIDR.

[http://en.wikipedia.org/wiki/CIDR](http://en.wikipedia.org/wiki/CIDR)

Coleop: if you have a properly formated /etc/network/interfaces you can get connectivity by typing:

sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start

That will bypass NM.

---

### Post by ccw on 2008-08-08
Bug for ignoring /etc/network/interfaces:

LP#256054
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/256054](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/256054)

---

### Post by Kevbert on 2008-08-08
Completely lost network manager in latest updates.  Looks like a Ubuntu 64 bit re-install is in order.

---

### Post by Nullack on 2008-08-09
Hmmm not allowing netmasks in IP4 is a bug in my view. If anyone disagrees please say so as otherwise Ill raise one on this soon.

---

### Post by Kevbert on 2008-08-09
> **Kevbert said:**
> Completely lost network manager in latest updates.  Looks like a Ubuntu 64 bit re-install is in order.

No re-install required.  I connected an ethernet cable to my router, booted into Intrepid.  Was asked for my wireless WPA password and then connected (wired) to router.  Then disconnected cable and wireless works again ????

---

### Post by Gina on 2008-08-09
Not for me - wireless seems connected in iwconfig but it doesn't work.:(

---

### Post by syxbit on 2008-08-09
is nm 0.7 really going to be included this time?

---

### Post by ccw on 2008-08-10
> **syxbit said:**
> is nm 0.7 really going to be included this time?

[https://launchpad.net/ubuntu/+source/network-manager](https://launchpad.net/ubuntu/+source/network-manager)

Its in Intrepid now.

---

### Post by plun on 2008-08-10
**The Road to NetworkManager 0.7**

[http://blogs.gnome.org/dcbw/2008/07/20/the-road-to-networkmanager-07/](http://blogs.gnome.org/dcbw/2008/07/20/the-road-to-networkmanager-07/)

> This list is by no means complete.  But in the interest of not being a black hole let’s get the stuff out in public and hey, maybe some patches will even show up on networkmanager-list@. 


Works just fine for myself, both wired and wireless, not tested mobile broadband and I am using a blu-tooth connection which comes in ver 7.1...

---

### Post by Gina on 2008-08-10
With wireless not currently working, I can only test Intrepid on one machine without running a long cable from router to other room (or with laptop, carrying it to the router).  There are three different chipsets affected - bcm4306, rt2500 and rt73 all of which work fine with Hardy.

I'm hoping the fix won't be too long coming.

---

### Post by Kevbert on 2008-08-10
> **Gina said:**
> With wireless not currently working, I can only test Intrepid on one machine without running a long cable from router to other room (or with laptop, carrying it to the router).  There are three different chipsets affected - bcm4306, rt2500 and rt73 all of which work fine with Hardy.

I'm hoping the fix won't be too long coming.

My BCM4306 Rev03 seems to work OK (see post #11).

---

### Post by Gina on 2008-08-10
My BCM4306 rev3 doesn't work though (see post #12)

---

### Post by BC7333 on 2008-08-10
> **Gina said:**
> With wireless not currently working, I can only test Intrepid on one machine without running a long cable from router to other room (or with laptop, carrying it to the router).  There are three different chipsets affected - bcm4306, rt2500 and rt73 all of which work fine with Hardy.

I'm hoping the fix won't be too long coming.

Tried this yet?  [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

---

### Post by Gina on 2008-08-10
Unfortunately I don't think this is in the best interests of testing Intrepid.

---

### Post by syxbit on 2008-08-11
when is the actual release of nm 0.7 gonna be?
cause it's been coming out for a long time.

i'm really looking forward to being able to do ad-hoc (something mac and windows have always been able to do)

---

### Post by plun on 2008-08-11
> **syxbit said:**
> when is the actual release of nm 0.7 gonna be?
cause it's been coming out for a long time.

i'm really looking forward to being able to do ad-hoc (something mac and windows have always been able to do)

Well... URL again
[B]
The Road to NetworkManager 0.7[/B]

[http://blogs.gnome.org/dcbw/2008/07/20/the-road-to-networkmanager-07/](http://blogs.gnome.org/dcbw/2008/07/20/the-road-to-networkmanager-07/)

Please read and test....and file bugs  :)

---

### Post by Kevbert on 2008-08-11
> **Gina said:**
> My BCM4306 rev3 doesn't work though (see post #12)

Hi Gina,
Do you have the latest Broadcom drivers ?  You can get them [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13")
I know there was some problems in early July regarding these drivers, hence updates were required.  All I did was to boot up with the ethernet cable in place so that a wired connection to my router was made.  Once this had occurred the connection was removed and a wireless connection was immediately attempted.  Prior to doing this, when I booted, no wireless connections were shown (only wired connections were available to be set up).

---

### Post by Gina on 2008-08-11
Thank you - I'll try that :)

---

### Post by joske on 2008-08-11
> **Gina said:**
> With wireless not currently working, I can only test Intrepid on one machine without running a long cable from router to other room (or with laptop, carrying it to the router).  There are three different chipsets affected - bcm4306, rt2500 and rt73 all of which work fine with Hardy.

I can confirm rt2500 not working. What's up with this driver? The old drivers were not working with NM (didn't exist at the time), but they offered good performance and stability. Gutsy broke this by including the new rt2x00 drivers, which didn't work at all, hardy had the rt2x00 working, but with abysmal performance, and now we're back at not working at all :-(

---

### Post by syxbit on 2008-08-14
> **plun said:**
> Well... URL again
[B]
The Road to NetworkManager 0.7[/B]

[http://blogs.gnome.org/dcbw/2008/07/20/the-road-to-networkmanager-07/](http://blogs.gnome.org/dcbw/2008/07/20/the-road-to-networkmanager-07/)

Please read and test....and file bugs  :)
i'm aware of the URL, but no release date is mentioned.
since this has been 'almost released' for so long, I'm just hopnig it really is coming out this time.
it shipped (cvs, obviously) with Fedora 8. That was AGES ago. Even back then it was almost released, and was expected for Hardy.

Still, when it finally does get released, it should be a huge improvement

---

### Post by BC7333 on 2008-08-14
Having some difficulty trying to get nm-applet to start/run

brian@brian-laptop:~$ sudo nm-applet

** (nm-applet:27688): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:27688): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed


Anyone seen this?  

Something possibly related here [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/37128](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/37128)

What's a computer with wireless problems worth these days.. practically nothing.  Been around since Feisty and it hasn't improved much.

I love ubuntu but am jealous when my son with the same model laptop, riding in the car can spot a zillion networks and find one we can connect to.. with win...... I have trouble staying connected at home.

..wireless somehow stops, open nm, uncheck roaming, add router and dhcp, won't connect, reboot, change back to roaming and connects for another while.. repeat 10 times a day..

---

### Post by Nullack on 2008-08-17
Ive reported this bug:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/258743](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/258743)

Custom MTU's are not applied and are in fact lost

Someone please confirm the bug in launchpad thanks

---

### Post by tawmas on 2008-08-19
From time to time, NM forgets the manual settings for my wired connection and reverts to auto (i.e., DHCP)... Might be at every reboot, but I didn't play enough attention, so I'm beginning to track it down now.

Does this happen to someone else? If there's no bug open for this, I'll open one as soon as I can confirm if it happens consistently at reboot.

---

### Post by tawmas on 2008-08-19
I've just reported [bug 259539]("https://bugs.edge.launchpad.net/ubuntu/+source/network-manager/+bug/259539") about the manual settings not sticking after reboot.

BTW, while investigating the issues above I found (unrelated) errors about a missing /usr/sbin/nscd. Looks like the nscd package is not installed on my PC. Should I install it? Is it normally installed?

---

### Post by dupondje on 2008-08-19
I made a bug report of this already yesterday ... don't make duplicate bug reports plz :(

[https://bugs.edge.launchpad.net/bugs/259214](https://bugs.edge.launchpad.net/bugs/259214)

---

### Post by seeker5528 on 2008-09-19
Just adding my information for those who follow. At the time of this posting this is what I'm using:

Networkmanager Version: 0.7~~svn20080908t183521+eni0-0ubuntu2
WPA Supplicant version: 0.6.4-2
wireless card: 00:0c.0 Network controller: RaLink RT2561/RT61 802.11g PCI
wireless driver: rt61pci (the in kernel driver)
resolvconf Version: 1.42ubuntu2

If I don't touch network manager at all, opting to configure things in /etc/network/interfaces, static configuration, on a fresh boot checking the network configuration with ifconfig shows wireless has not been configured. If I ifdown/ifup wlan0, I have an ipaddress, gateway, etc... but something happens with the authentication/encryption that results in a dissassociation from the access point.

I have not tried WPA with the 2.6.27 kernel in Ubuntu Intrepid, but it fails for me in Debian with 2.6.26. If I purge all the network manager stuff either of the 2 following WEP type configurations work for me:

config 1, standard WEP config
```

iface wlan0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 68.87.85.98 68.87.69.146
wireless-essid [my ssid]
wireless-key [my WEP key]

```

Config 2, WEP using the WPA supplicant
```

iface wlan0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 68.87.85.98 68.87.69.146
wpa-ssid [my ssid]
wpa-key_mgmt NONE
wpa-wep_key0 [my WEP key]

```

Based on my research while attempting to get WPA to work in my Debian installation and the fact that the above config 2 works, I am assuming that for a basic WPA configuration the following should work:

Config 3, WPA
```

iface wlan0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 68.87.85.98 68.87.69.146
wpa-ssid [my ssid]
wpa-psk  [text passphrase or 64 character hex key]

```

Later, Seeker

---

### Post by syxbit on 2008-09-21
is there still no official release date for the FINAL network manager 0.7 ??
this is ridiculous. This has been more delayed than Vista!

(i wouldn't mind delays so much- as it's free software-, if the devs would communicate properly, it's been 'almost' released for well over a year)

i don't use ubuntu on my dekstop & laptop anymore, so i care more about when the FINAL 0.7 will come out, and not another svn fedora style in intrepid

---

### Post by go7Ul1ai on 2008-09-21
I want to scale down my panel to 19px (I'm using an eee PC and have used smaller fonts) but when I do, the Network Manager icon is blurry and doesn't look very good. So I have to keep my panel at 24 px. Any chance this can be fixed soon?

Lee

---

### Post by RAOF on 2008-09-22
> **lee.jarratt said:**
> I want to scale down my panel to 19px (I'm using an eee PC and have used smaller fonts) but when I do, the Network Manager icon is blurry and doesn't look very good. So I have to keep my panel at 24 px. Any chance this can be fixed soon?

Lee

Have you filed a bug?  That looks like it should be fairly easy to fix, but unless the devs are aware of the problem it will never get fixed (or, at least, will only get fixed by accident).

---

### Post by knarf on 2008-09-22
I have the panel set to 17 px (the minimum) without the icon being overly blurry. This is with network-manager-gnome  0.7~~svn20080907t033843-0ubuntu2 on a Thinkpad T23

---

### Post by american.swan on 2008-10-20
I am getting the expressed feeling that if I want to update to this beta, I should uninstall NM then try setting my static IP data.

Am I correct?

Maybe I should wait until the final release to upgrade, but I am unsure that will solve this issue.

---

### Post by yakumo9275 on 2008-10-20
does anyones network manager applet work at all? Mine hasnt worked for weeks. Mine is afflicted with the "Updating connection failed: nm-ifupdown-connection.c.82 - connection update not supported (read-only).." bug...

I saw new updates hit tonight but it was just translations.. I'm guessing nobody is working on this particular bug..
(which I think is [bug 279867]("https://bugs.edge.launchpad.net/ubuntu/+source/network-manager/+bug/279867")

hmm looking at the buglist for network manager 0.7 is.. damn scary. one could come to the conclusion NM0.7 is a pile of garbage and needs to be yanked coz I dont see it being stable by the time intrepid will ship

---

### Post by ShirishAg75 on 2008-10-21
Hi all, 
 Is this configuration correct?

```

auto lo
iface lo inet loopback

iface eth1 inet static
    address 192.168.1.3
    netmask 255.255.255.0
    gateway 192.168.1.1
    dns-nameserver 61.1.96.69 61.1.96.71    

```

It seems I'm being configured using auto dhcp . I have been trying all sorts of things since 2 hours but come no closer. Attaching the last 1000 lines of syslog so you guys can take a peek and lemme know. 

My /etc/NetworkManager/nm-system-settings.conf managed state is put to true 

```

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

```

---

### Post by linux6994 on 2008-10-21
I would have the gateway and dns as the same address that way if you are going to have a local samba share network that the router does everything, its just simpler that way.Your router will pass along the dns stuff. My network manager works on some of my pc and not on others. If you are running static like you are then just uninstall it. I did it was messing up ff.

gateway 192.168.1.1
    dns-nameserver 192.168.1.1

---

### Post by ShirishAg75 on 2008-10-21
did that, although not doing any samba stuff or anything. Its a simple wired connection using the router as my modem to connect to the internet.

Also I have another query . Does user have to be part of the netdev  group in 0.7 anymore, with consolekit being there now?

```
adduser $USER netdev
``` 

Looking forward for additions to the same.

---

### Post by hyper_ch on 2008-10-21
I stopped using the network manager a long time ago and did only manually config the network... but I have discovered wicd and it does all I want it to. maybe you want to give it a shot also.

---

### Post by american.swan on 2008-10-21
> **hyper_ch said:**
> I stopped using the network manager a long time ago and did only manually config the network... but I have discovered wicd and it does all I want it to. maybe you want to give it a shot also.

I'm with you.  How can I update to beta and set up wicd while removing or disabling Network Manager?  That would be great.

---

### Post by hyper_ch on 2008-10-21
add the wicd repository: [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

use

```

deb http://apt.wicd.net intrepid extras

```

and then import they key and then install wicd :)

---

### Post by karlatsaic on 2008-10-22
But be careful about using wicd if you need vpn connections. I have vpn working perfectly using Network Manager on Harday 8.04, along with wireless as well. I'll just wait until Intrepid settles down and then try the upgrade. I once tried installing wicd and, although it did have a nice feel for easily connecting in public places, it was really quite useless for me on my work laptop where wireless vpn is a must.

---

### Post by Gina on 2008-10-22
I had network manager working on my laptop until yesterday then last night I found it wouldn't connect to my wireless network.  I ended up rebooting into Hardy!  This is NOT GOOD at this stage in the development :(

---

### Post by Gina on 2008-10-22
Very strange! When I tried it on my laptop this afternoon it connected perfectly with Intrepid.

---

### Post by natros on 2008-10-22
I have a few annoying problem with nm. I have two "Auto eth0": one with dhcp and the other manual. Is there a way to get rid of dhcp? Removing from Network Connections works till next reboot. 
Another annoying thing is the "System setting" checkbox. NM cannot remember the selected option.

---

### Post by american.swan on 2008-10-22
Unless you absolutely need Network-manager.... which I don't.... so I followed this posters modular suggestion.   Remove Network-manager n install wicd.

[http://ubuntuforums.org/showpost.php?p=6004827&postcount=14](http://ubuntuforums.org/showpost.php?p=6004827&postcount=14)

---

### Post by wgrant on 2008-10-22
> **american.swan said:**
> Unless you absolutely need Network-manager.... which I don't.... so I followed this posters modular suggestion.   Remove Network-manager n install wicd.

[http://ubuntuforums.org/showpost.php?p=6004827&postcount=14](http://ubuntuforums.org/showpost.php?p=6004827&postcount=14)

Or, you know, report the bugs so that we can fix them&#8253; Workarounds are not solutions.

---

### Post by jheaton5 on 2008-10-22
> **syxbit said:**
> i'm aware of the URL, but no release date is mentioned.
since this has been 'almost released' for so long, I'm just hopnig it really is coming out this time.
it shipped (cvs, obviously) with Fedora 8. That was AGES ago. Even back then it was almost released, and was expected for Hardy.

Still, when it finally does get released, it should be a huge improvement

syxbit,

I just checked my Network Manager Version.  It is 0.7.0.  I'm running Intrepid beta.

---

### Post by caryb on 2008-10-22
I have a very annoying "feature" In Knetworkmanager (don't know if the problem is in network manager or the gui wrapper knetworkmanager) but If I connect via wireless I have to right click on the panel icon & tell it to connect! I have the box selected to autoconnect. Is this the same in Ubuntu:confused:


Cary

---

### Post by klange on 2008-10-22
> **caryb said:**
> I have a very annoying "feature" In Knetworkmanager (don't know if the problem is in network manager or the gui wrapper knetworkmanager) but If I connect via wireless I have to right click on the panel icon & tell it to connect! I have the box selected to autoconnect. Is this the same in Ubuntu:confused:


Cary
No, definitely sounds like a bug... Have you checked for a report / reported it?

--

I'm actually quite enjoying NM 0.7 now that it works. It makes connecting to my school network (which doesn't use DHCP) so much easier - on wired and wireless. I just wish NM would pay attention when my wireless comes online like it did in the 0.6 days.

---

### Post by tahina on 2008-10-25
Hi!

After updating and rebooting a couple of minutes ago, wireless doesn't work on my eeepc 701 again.

Are others experiencing problems too?

---

### Post by Teamgeist on 2008-10-25
> **tahina said:**
> Hi!

After updating and rebooting a couple of minutes ago, wireless doesn't work on my eeepc 701 again.

Are others experiencing problems too?

If this uses an Atheros Wireless chipset install linux-backports-modules-intrepid

```
sudo apt-get install linux-backports-modules-intrepid
```

---

### Post by tahina on 2008-10-25
> **Teamgeist said:**
> If this uses an Atheros Wireless chipset install linux-backports-modules-intrepid

Does this still apply when the wireless was working fine before the update? 

To get it working in the first place, all I had to do was disable the use of Atheros wireless in "System>Administration>Hardware Drivers" and reboot...

edit: Thank you! I installed it and now wireless works again. I don't understand why updating should require me to install a new package to retain functionality, though. (I don't understand a lot of things, so I'm not saying this is wrong.)

---

### Post by anthro398 on 2008-10-25
I'm disappointed to find that the new Network Manager respects split tunnel VPN configuration.  It used to be that, in spite of the configuration pushed by the Cisco or OpenVPN server, Network Manager would route all traffic over the VPN.  That was pretty handy on unsecured wireless networks.  I plan to look into adding my own route statements to counteract this, but haven't had time to look into it.  I wish this were an option in the GUI.

---

