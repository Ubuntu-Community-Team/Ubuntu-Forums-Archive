---
title: "Bonding Multiple Wireless NICs"
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by kleinric on 2010-11-20
Hi,

I have an Asus R1F laptop with a build in wireless card. I also have 2 USB dongles that we used to use old desktop machines. All of the cards work fine in Ubuntu. 

I'm running Ubuntu 10.10, 2.6.35-22-generic-pae.

The problem is that I have really bad signal on my side of the house and the connection is dropped quite often. I've tried just connecting on the devices at the same time, they all connect fine but nothing actually works. 

I read about bonding interface cards on this [blog]("http://www.ubuntugeek.com/how-to-setup-bond-or-team-network-cards-in-ubuntu-10-1010-04.html") and that would solve all my problems - if a usb dongle could act as a backup for when the normal connection is dropped and while it is reconnecting. 

I tried what was written and also did some Googling, but every way that I try seems to work fine until 2 wireless devices are bonded. When that happens they both disconnect and reconnect like crazy. This happens both with and without network manager running.

Build in card[wlan0]: Intel PRO/Wireless 3945ABG
USB[wlan1]: Cisco LinkSys Compact Wireless-G USB Adapter
USB[wlan2]: Realtek RTL 818713 WLAN Adapter

I load the module:
```
modprobe bonding mode=1 miimon=100 downdelay=200 updelay=200
```Then I've used various methods to bond, but ultimately something like:
```
ifconfig bond0
ifenslave bond0 wlan0 wlan1
```and then things go crazy.

I've also tried adding this to the /etc/modprobe.d/aliases.conf 
```
alias bond0 bonding
options mode=0 miimon=100 downdelay=200 updelay=200
```With my /etc/network/interfaces (network manager disabled):
```

auto bond0
iface bond0 inet dhcp
    bond-slaves none
    bond-mode 1
    bond-miimon 100

auto eth0

auto wlan0
iface wlan0 inet manual
    bond-master bond0
    bond-mode 1
    bond-miimon 100
    bond-give-a-chance 10
    wpa-bridge bond0
    wpa-key-mgmt WPA-PSK
    wpa-proto WPA
    wpa-group CCMP
    wpa-ssid my-ssid
    wpa-psk "my-secret-password" # wpa_passphrase essid

auto wlan1
iface wlan1 inet manual
    bond-master bond0
    bond-mode 1
    bond-miimon 100
    bond-give-a-chance 10
    wpa-bridge bond0
    wpa-key-mgmt WPA-PSK
    wpa-proto WPA
    wpa-group CCMP
    wpa-ssid my-ssid
    wpa-psk "my-secret-password using wpa_passphrase essid"

```But when I run "/etc/init.d/networking restart" it fails and tells me that
```

/sys/class/net/wlan0/master/bonding/primary doesn't exist
/sys/class/net/wlan1/master/bonding/primary doesn't exist

```And they don't :/

Same thing if I try various combinations of the different adapters... 

Can this actually work? Any help would be much appreciated.

Thanks,
Richard

---

### Post by tstebbens on 2010-12-07
Hi Kleinric

I registered because a) I had been meaning to for a while and b) I saw you post and, having been searching for a solution to the same problem myself, I found the answer:

Your two wifi cards are getting the same MAC address and the wireless access point is getting confused. You need to make sure that both cards get different MAC addresses or are not both active at the same time.

I followed the instructions here [http://www.ubuntugeek.com/how-to-setup-bond-or-team-network-cards-in-ubuntu-10-1010-04.html]("http://www.ubuntugeek.com/how-to-setup-bond-or-team-network-cards-in-ubuntu-10-1010-04.html") and got both my wireless NICs working together. I tried mode 0 and mode 1. Eventually I settled on mode 1 as it seemed to work best with my WAP.

Now, if I can figure out how to have it set the IP address via DHCP it will be perfect. Using those instructions sets a fixed IP address.

Terry.

---

### Post by kleinric on 2010-12-14
Hi Terry, 
Thanks for your response :)


Yeah, those are the instructions that I originally followed and had trouble with. The MAC address issue makes sense, but where do you tell it to give them separate MAC addresses? I'd ideally like them both connected, so that when the wireless connection drops on one, my internet will remain interrupted.

Yeah, I'm looking to use Mode 1. My internet is quite slow (384Kbps *bangs head against wall*) so the speed of my wireless really isn't a problem, as long as its connecting.

---

### Post by Mark Larry on 2012-02-14
Hello to all,

I'm trying to do the same and bond two wireless NIC and I'm facing the same problem.

I have already bonded the two wired ethernet interfaces achieving 2 Gb/s of bandwidth with the aggregation of eth1 and eth2 wired interfaces.

Now I was I trying to do the bond of the 2 wireless devices(2 atheros) and I'm facing the same problem that is described here.

Can someone please help me
All advises, comments, etc... will be very much appreciated.

Best Regards
Mark

---

