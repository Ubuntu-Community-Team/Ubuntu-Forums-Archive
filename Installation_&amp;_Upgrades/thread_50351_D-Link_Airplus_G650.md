---
title: "D-Link Airplus G650"
date: 2005-07-20
forum: Installation &amp; Upgrades
---

### Post by tacogy3 on 2005-07-20
I know this topic has been posted many times, i have tried reading through all the forums and trying to find an answer but i am unable to get my wireless card to work.

here are some errors i recieve


 # sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

# /tmp/fr-xXWzUc/ndiswrapper-1.2/utils/ndiswrapper -l
Installed ndis drivers:
5211    invalid driver!
inffile invalid driver!
net5211 invalid driver!


I have tried and followed all the steps for setting up a wireless card but can not get it to work. Help would be appreciated.

---

### Post by audax321 on 2005-07-20
What is the H/W Ver? If its a PCMCIA card, it should say it on the back. I have H/W Ver. B4 and it worked without installing anything. I just had to set up the security and tell it to connect to my wireless network.

Does ifconfig (after a fresh reboot if you made any changes) show ath0???

And I think you should be using the madwifi driver unless you have a different version, in which case I have no idea..

EDIT:

According to this: [http://madwifi.sourceforge.net/dokuwiki/doku.php?id=compatibility_list#dwl-g650](http://madwifi.sourceforge.net/dokuwiki/doku.php?id=compatibility_list#dwl-g650)

Madwifi supports revisions B1, B2, B3, B4, B5, and C2.. if you have one of those ubuntu should detect it itself.


and if you do find ath0 do the following:

1. go to System >> Administration >> Networking (enter your root password if prompted)

2. Click on the wireless connection entry and then click properties.

3. In the new window that pops up, check 'This device is configured', enter the netword essid (this is the name your wireless router has for your network, and the WEP key for the security key your wireless router uses... I think you can use WPA as well, but the setup is more complicated and I never really cared enough to do it... good game laziness.

4. For the connection settings keep DHCP if your router will give you your IP address  otherwise enter the IP Address, Subnet Mask, and Gateway Address as needed and click OK.

5. Back at the original Network settings window highlight the wireless connection and click Activate (you may need to go into the console and run sudo dhclient after this to get the network card an IP address).

---

### Post by tacogy3 on 2005-07-20
I have version B5. I do not have madwifi driver. I have dont most of those steps you have listed in the edit post. 

> enter the netword essid (this is the name your wireless router has for your network, and the WEP key for the security key your wireless router uses... I think you can use WPA as well, but the setup is more complicated and I never really cared enough to do it... good game laziness. 

i do not have those options. I also do not have the option to Add a new network


What appears when i type ifconfig

root@ubuntu:/home/rich # ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:56:B5:D9
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe56:b5d9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:378 (378.0 b)
          Interrupt:21 Base address:0x3000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:13410 (13.0 KiB)  TX bytes:13410 (13.0 KiB)




root@ubuntu:/home/rich # iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


Ok, i will try those drivers

---

### Post by audax321 on 2005-07-20
Try opening a terminal and typing:

sudo ifconfig ath0 up

then re-run ifconfig and see if ath0 shows up again. Also is this an upgrade to Hoary from Warty or a fresh install?

the Madwifi driver should be included with Ubuntu and you don't have to install them yourself... your revision is supported. BUT, the firmware should be 2.54... if it isn't you may need to upgrade the firmware on your card from D-Links website.

---

### Post by tacogy3 on 2005-07-20
> sudo ifconfig ath0 up 

I did do that, nothing


This is a fresh install


My firmware is updated to the latest

I have DWL-G650

---

### Post by audax321 on 2005-07-20
Also I should have asked this before, but is your model DWL-G650 or DWL-AG650?

Just want to make sure because only revisions A2 and B2 work with DWL-AG650...

---

### Post by funkydan2 on 2005-07-20
Also, make sure that your card is a DWL-650 and not a DWL-650+.  They use a different chipset and thus need different drivers (modules).

---

### Post by tacogy3 on 2005-07-20
The card says this exactly.

D-Link AirPlus
DWL-G650

---

### Post by audax321 on 2005-07-20
In that case, I have no idea what is going on because I have the exact same card, just a different revision, and it worked without me having to install any drivers. Are you sure the PCMCIA slots on the computer are recognized... it could be that there is a problem with the slots rather than the card. I don't know how you would check this though... unless you have another card you can put in and see if the computer detects it.

---

### Post by kleeman on 2005-07-20
It could be that your firmware is too recent for the madwifi driver. I have this card and it
happened to me..... 
What does 
dmesg | grep ath

give?

If this is the problem then I have a work around here

[http://www.ubuntuforums.org/showthread.php?t=36800](http://www.ubuntuforums.org/showthread.php?t=36800)

Be warned however it requires mucking around with kernel modules

---

### Post by tacogy3 on 2005-07-20
thank you kleeman

i followed everything exactly on your howto and i got it work.

---

### Post by darius_underhill on 2005-10-12
[QUOTE=tacogy3]I know this topic has been posted many times, i have tried reading through all the forums and trying to find an answer but i am unable to get my wireless card to work.

here are some errors i recieve


 # sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

# /tmp/fr-xXWzUc/ndiswrapper-1.2/utils/ndiswrapper -l
Installed ndis drivers:
5211    invalid driver!
inffile invalid driver!
net5211 invalid driver!


I have tried and followed all the steps for setting up a wireless card but can not get it to work. Help would be appreciated.[/QUOTE]


You may want to try this link:

[HOWTO: Using D-link AirplusG+ DWL g650+ with ndiswrapper]("http://ubuntuforums.org/showthread.php?p=403606")

---

### Post by wisdoms on 2006-03-05
Hello, I'm "using" the D-Link DWL -650+ wireless card, but something strange happens.

# iwconfig wlan0
wlan0     IEEE 802.11b+  ESSID:"heimsuesheim"  Nickname:"acx_100"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=11 Mb/s   Tx-Power=18 dBm   Sensitivity=176/255
          Retry min limit:7   RTS thr:off
          Encryption key:2673-CCAD-C868-7305-46FB-7B18-A0   Security mode:restricted
          Power Management:off
          Link Quality=28/100  Signal level=21/100  Noise level=8/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:0

there's no access point MAC address! but

# iwlist wlan0 scan
wlan0     Scan completed :
      .....
      Cell 04 - Address: 00:11:95:3E:85:E7
                    ESSID:"heimsuesheim"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=67/100  Signal level=54/100  Noise level=0/100
                    Encryption key:on
                    Bit Rate:54 Mb/s
     ....

# ping web.de
PING web.de (217.72.195.42) 56(84) bytes of data.

I have tried to use the ndiswrapper but recalling Synaptic I've got this message "Su returned with an error"!!!
Help pls!

---

### Post by wisdoms on 2006-06-06
The problem was completely solved by using the new Kubuntu 6.06!

---

