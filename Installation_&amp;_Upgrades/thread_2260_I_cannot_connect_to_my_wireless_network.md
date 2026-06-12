---
title: "I cannot connect to my wireless network"
date: 2004-10-26
forum: Installation &amp; Upgrades
---

### Post by chumpchous on 2004-10-26
I've managed to configure the drivers for my wireless card, and it is working well with the system, but I cannot get it to connect to my wireless network.

I have obviously tried setting it up directly through the GUI, but when I try to activate it, it simply sits for a moment and then deactivates. 

It is finding my network, iwlist scan shows:

Address: 00:11:24:04:3F:8B
                    ESSID:"jedit"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412GHz (channel 1)
                    Quality:0/100  Signal level:-43 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Extra:bcn_int=100
                    Extra:atim=3

I've tried disabling the encryption, and it still wont connect. 

My /etc/network/interfaces file:

auto wlan0
iface wlan0 inet dhcp
name Wireless LAN card
wireless_essid jedit
wireless_key thekey (this isnt in hex, should it be?)

Is there any other relevant information? The card is a linksys wireless-G USB adapter, and my router is an apple airport extreme. 

Thanks.

---

### Post by beesee on 2004-10-26
Have you tried setting [COLOR=Blue]wireless_mode[/COLOR] in /etc/network/interfaces?  I'm not sure it'll make a difference for you, but in gentoo I had to explicitly set the mode to managed to get my wireless to work.

---

### Post by chumpchous on 2004-10-27
Tried it, didnt work. Thanks for trying, though!

---

### Post by jamaas on 2004-10-27
I've spent many hours trying to get this to work so can understand your frustration!!  It seems to be very hardware specific, but if you have relatively common and new hardware, the kernels now are pretty good at configuring them automatically

Do you have both wireless and an ethernet cable connections?  If so, try unhooking the ethernet cable, andreboot.  Most of the time the kernel finds your hardware and sets it up automatically ....  cold comfort!

Otherwise try google search for keywords like "linux" and your wireless card number or wireless router number, might find something recent.  Otherwise repost here with more specifics about your hardware and you will get help from those much more knowledgeable than me ....

Good Luck

Jim




[QUOTE=chumpchous]I've managed to configure the drivers for my wireless card, and it is working well with the system, but I cannot get it to connect to my wireless network.

I have obviously tried setting it up directly through the GUI, but when I try to activate it, it simply sits for a moment and then deactivates. 

It is finding my network, iwlist scan shows:

Address: 00:11:24:04:3F:8B
                    ESSID:"jedit"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412GHz (channel 1)
                    Quality:0/100  Signal level:-43 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Extra:bcn_int=100
                    Extra:atim=3

I've tried disabling the encryption, and it still wont connect. 

My /etc/network/interfaces file:

auto wlan0
iface wlan0 inet dhcp
name Wireless LAN card
wireless_essid jedit
wireless_key thekey (this isnt in hex, should it be?)

Is there any other relevant information? The card is a linksys wireless-G USB adapter, and my router is an apple airport extreme. 

Thanks.[/QUOTE]

---

### Post by chumpchous on 2004-10-27
Well, I've made some progress, but I still dont have it running. It seems to be that card configured with ndiswrapper dont like running through /etc/network/interfaces. 

```
by running sudo iwconfig essid (id) key s:(key) mode managed channel 11, I get iwconfig to connect to my router:

wlan0     IEEE 802.11b  ESSID:"jedit"
          Mode:Managed  Frequency:2.462GHz  Access Point: 00:11:24:04:3F:8B
          Bit Rate:54Mb/s   Tx-Power:32 dBm
          RTS thr:2432 B   Fragment thr:2432 B
          Power Management:off
          Link Quality:100/100  Signal level:-37 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:6696   Missed beacon:0

```
But still, no internet connection. I'm not so sure what the bottom 6 designations are for. And I have a wireless G router, so I'm not sure why it is coming up as IEEE 802.11b. But it coming up with an access point so I must be close.

Any more advice?

---

### Post by chumpchous on 2004-10-27
Okay, i've gotten it going, You were right, beesee, I needed to add some things to my interfaces file. Just in case anyone else runs into this problem, I had to change two things:

One, I needed to add wireless_mode managed BEFORE setting my essid in the interfaces file. From what I've read, sometimes you need essid first, other times you need wireless mode first, hard to say.

Second: I had to add the prefix s: to my wireless key, otherwise you need to input it in hex form. 

Here is my interfaces file:

iface wlan0 inet dhcp
name Wireless LAN card
wireless_mode managed
wireless_essid myessid
wireless_key s:mynetworkkey

wireless_channel 11
auto wlan0

And there you have it, everything running smoothly!

---

### Post by easy_target on 2005-02-13
Nice going! I was having the same problem with a DWL 520+ and with your solution everything is runnig smoothly now. Maybe you can make a HOW TO out of that. Also the developers could implement those fixes to the GUI configurator so it really "just works" with those kinds of network cards out of the box.

Cheers

---

### Post by Epithett on 2005-06-21
chumpchous, I have a Linksys Wireless-G USB adaptor on my computer that will be running Ubuntu when I receive the disks.  I am 100% new to Linux so after reading your directions, I know that I will not be able to figure it out myself but also, there are certain things you said and did that I don't understand because of my lack of experience.  Would you mind giving me your email or aim screen name(s) so that when the problem arises, I can get help from you?  I have two topics running asking for help on this same issue and have gotten no responses like what you have just said.  Any help would be appreciated, thanks!

---

