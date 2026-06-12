---
title: "Karmic &amp; Wireless &quot;Inconsistency?&quot;"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by moore.bryan on 2009-10-16
I'm not sure if "inconsistency" is the right word for what's happening, but I'm finding my Internet speed to be irregular, at best. One moment, I'll be flying along and the next, sipping coffee seemingly waiting for the Internet to catch-up with me. I've already inserted the *ipv6.disable=1* into grub2 and specified 54M as my wireless rate in /etc/NetworkManager/dispatcher.d/01ifupdown. Am I missing something? I've seen a few other posts with similar, but not exactly the same issue.

Also, and on possibly a side-note, is there any reason why Karmic got rid of the /etc/wpa_supplicant.conf file? I used to use that to set-up my network access without the need for NetworkManager.

---

### Post by wilee-nilee on 2009-10-16
On every Karmic install I do on my own computers I immediately switch to wicd a working manager. With the new Athx5 setup there are still glitches that seem to make the ye old Network Manager unstable for some of us.

---

### Post by moore.bryan on 2009-10-16
I was the same way... for Jaunty, I dumped both altogether, simply using /etc/network/interfaces and /etc/wpa_supplicant.conf to handle my two "regular" connections and network-config for any unexpected connections. Frankly, not real happy Karmic seems to handle that method differently... can't quite seem to figure it out, yet.

For everything before Jaunty, wicd was my go-to manager; I was hoping NetworkManager had some far enough along. I suppose not?

[U]EDIT
[/U]And now, to complicate things even more, I've installed wicd to handle all my wireless stuff and it will *regularly* just drop my connection and then "discover" it again, randomly. WTF!?

---

### Post by jomtois on 2009-10-16
I know what you mean.  I have been frustrated with this as well.

Perhaps you fall into this category too:

[https://bugs.launchpad.net/ubuntu/+bug/433972](https://bugs.launchpad.net/ubuntu/+bug/433972)

---

### Post by jomtois on 2009-10-16
I also added this bug:

[https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/453647](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/453647)

Since I wasn't convinced the other one I was looking into was getting at the issue or not.  All I know is that my log files are constantly being written to with messages that I do not understand:
[HTML]
Oct 16 22:24:37 jon-laptop wpa_supplicant[1243]: CTRL-EVENT-SCAN-RESULTS 
Oct 16 22:25:17 jon-laptop wpa_supplicant[1243]: CTRL-EVENT-SCAN-RESULTS 
Oct 16 22:26:17 jon-laptop wpa_supplicant[1243]: CTRL-EVENT-SCAN-RESULTS 
Oct 16 22:27:37 jon-laptop wpa_supplicant[1243]: CTRL-EVENT-SCAN-RESULTS 
Oct 16 22:29:17 jon-laptop wpa_supplicant[1243]: CTRL-EVENT-SCAN-RESULTS 
Oct 16 22:29:48 jon-laptop wpa_supplicant[1243]: WPA: Group rekeying completed with 00:21:91:18:d0:34 [GTK=TKIP]
Oct 16 22:29:48 jon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  completed -> group handshake
Oct 16 22:29:48 jon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  group handshake -> completed
Oct 16 22:29:51 jon-laptop kernel: [100130.601131] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:29:52 jon-laptop kernel: [100131.522750] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:29:53 jon-laptop kernel: [100132.546869] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:29:54 jon-laptop kernel: [100133.570838] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:29:55 jon-laptop kernel: [100134.594839] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:29:56 jon-laptop kernel: [100135.516561] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:29:59 jon-laptop kernel: [100138.998182] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:03 jon-laptop kernel: [100142.055783] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:04 jon-laptop kernel: [100143.094368] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:05 jon-laptop kernel: [100144.055199] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:06 jon-laptop kernel: [100145.142446] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:07 jon-laptop kernel: [100146.166402] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:08 jon-laptop kernel: [100147.055082] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:09 jon-laptop kernel: [100148.154608] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:10 jon-laptop kernel: [100149.238488] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:11 jon-laptop kernel: [100150.262622] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:12 jon-laptop kernel: [100151.184152] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:13 jon-laptop kernel: [100152.208257] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:13 jon-laptop kernel: [100152.824443] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:14 jon-laptop kernel: [100153.232282] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:15 jon-laptop kernel: [100154.563470] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:16 jon-laptop kernel: [100155.485296] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:17 jon-laptop kernel: [100156.611514] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:18 jon-laptop kernel: [100157.533253] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:19 jon-laptop kernel: [100158.557270] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:20 jon-laptop kernel: [100159.581300] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:21 jon-laptop kernel: [100160.605309] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:22 jon-laptop kernel: [100161.629271] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:23 jon-laptop kernel: [100162.653302] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:24 jon-laptop kernel: [100163.558374] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:25 jon-laptop kernel: [100164.599059] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:26 jon-laptop kernel: [100165.623007] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:27 jon-laptop kernel: [100166.851915] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:36 jon-laptop kernel: [100175.557442] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:38 jon-laptop kernel: [100177.399356] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:43 jon-laptop kernel: [100182.519530] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:30:59 jon-laptop kernel: [100199.006521] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:17 jon-laptop wpa_supplicant[1243]: CTRL-EVENT-SCAN-RESULTS 
Oct 16 22:31:28 jon-laptop kernel: [100227.884131] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:29 jon-laptop kernel: [100228.805849] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:30 jon-laptop kernel: [100229.829867] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:31 jon-laptop kernel: [100230.853907] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:32 jon-laptop kernel: [100231.877938] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:33 jon-laptop kernel: [100232.901875] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:35 jon-laptop kernel: [100234.834966] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:36 jon-laptop kernel: [100235.871664] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:37 jon-laptop kernel: [100236.895669] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:38 jon-laptop kernel: [100237.510012] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:38 jon-laptop kernel: [100237.919697] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:39 jon-laptop kernel: [100238.434155] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:39 jon-laptop kernel: [100238.437569] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:39 jon-laptop kernel: [100238.534288] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:39 jon-laptop kernel: [100238.943732] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:40 jon-laptop kernel: [100239.865385] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:41 jon-laptop kernel: [100240.582348] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:41 jon-laptop kernel: [100240.584553] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:42 jon-laptop kernel: [100241.094124] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:43 jon-laptop kernel: [100242.118163] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:43 jon-laptop kernel: [100242.478833] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:44 jon-laptop kernel: [100243.039870] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:45 jon-laptop kernel: [100244.063811] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:46 jon-laptop kernel: [100245.087934] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:47 jon-laptop kernel: [100246.111885] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:48 jon-laptop kernel: [100247.278753] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:49 jon-laptop kernel: [100248.277873] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ed034840
Oct 16 22:31:49 jon-laptop wpa_supplicant[1243]: WPA: Group rekeying completed with 00:21:91:18:d0:34 [GTK=TKIP]
Oct 16 22:31:49 jon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  completed -> group handshake
Oct 16 22:31:49 jon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  group handshake -> completed
Oct 16 22:31:50 jon-laptop wpa_supplicant[1243]: Associated with 00:21:91:18:d0:34
Oct 16 22:31:50 jon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  completed -> associated
Oct 16 22:31:50 jon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  associated -> 4-way handshake
Oct 16 22:31:50 jon-laptop wpa_supplicant[1243]: WPA: Key negotiation completed with 00:21:91:18:d0:34 [PTK=CCMP GTK=TKIP]
Oct 16 22:31:50 jon-laptop wpa_supplicant[1243]: CTRL-EVENT-CONNECTED - Connection to 00:21:91:18:d0:34 completed (reauth) [id=0 id_str=]
Oct 16 22:31:50 jon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> group handshake
Oct 16 22:31:50 jon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  group handshake -> completed
Oct 16 22:33:17 jon-laptop wpa_supplicant[1243]: CTRL-EVENT-SCAN-RESULTS 
Oct 16 22:35:17 jon-laptop wpa_supplicant[1243]: CTRL-EVENT-SCAN-RESULTS 
[/HTML]

---

### Post by moore.bryan on 2009-10-17
I think that's one of my several problems, now. As of this morning, **none** of the following works:

[LIST]
[*]wicd
[*]NetworkManager
[*]editing /etc/network/interfaces to use /etc/wpa_supplicant.conf
[*]running *sudo wpa_supplicant -Dwext -c/wpa_supplicant.conf -iwlan0*
[/LIST]
 **even** for a beta, this is a little ridiculous, no?

I can *sometimes* see my network and other times, it doesn't show-up at all. Then, if it does show-up and I try to connect to it, it will randomly drop and completely disappear from the list. And, still other times, it will connect and not be associated. WTF!!!???

Seriously... I understand it's beta and I've chosen to install it knowing it could/would be unstable; however, I've *always* installed the betas in the past and they were *never*--***never***-- *this* bad, even with Atheros wireless.

---

### Post by novafluxx on 2009-10-17
> **moore.bryan said:**
> I think that's one of my several problems, now. As of this morning, **none** of the following works:

[LIST]
[*]wicd
[*]NetworkManager
[*]editing /etc/network/interfaces to use /etc/wpa_supplicant.conf
[*]running *sudo wpa_supplicant -Dwext -c/wpa_supplicant.conf -iwlan0*
[/LIST]
 **even** for a beta, this is a little ridiculous, no?

I can *sometimes* see my network and other times, it doesn't show-up at all. Then, if it does show-up and I try to connect to it, it will randomly drop and completely disappear from the list. And, still other times, it will connect and not be associated. WTF!!!???

Seriously... I understand it's beta and I've chosen to install it knowing it could/would be unstable; however, I've *always* installed the betas in the past and they were *never*--***never***-- *this* bad, even with Atheros wireless.

Couple weeks ago I updated, and my wireless ceased working totally. I waited a couple days and hooked my desktop ethernet cable into my laptop and updated that way, standing here holding the damn thing lol

---

### Post by moore.bryan on 2009-10-18
> **novafluxx said:**
> Couple weeks ago I updated, and my wireless ceased working totally. I waited a couple days and hooked my desktop ethernet cable into my laptop and updated that way, standing here holding the damn thing lol
:-)

Similar here... now, at least, NetworkManager works, but I'd really *rather* use /etc/network/interfaces and /etc/wpa_supplicant.conf to setup my wireless, but that method doesn't seem to work in Karmic... either because of the ath5k driver or my Atheros card. Shame we haven't figured this one out.

Okay... spoke too soon. *While *posting this, my connection remained strong and connected, but Internet just wouldn't work What the hell is that all about?

---

### Post by moore.bryan on 2009-10-18
Let's further complicate things... I've put something up on Launchpad ([https://answers.launchpad.net/ubuntu/+question/86234](https://answers.launchpad.net/ubuntu/+question/86234)) and the suggested fix was in these fora ([http://ubuntuforums.org/showthread.php?t=419020](http://ubuntuforums.org/showthread.php?t=419020)). Now, I've tried all the different formations in that thread to no avail.

I **need** network access, so I reinstalled wicd to see if I could get anything and am greeted with a network disconnection every 30 seconds-or-so. So, here's my summation:

[LIST=1]
[*]/etc/network/interfaces & /etc/wpa_supplicant.conf **does not **work and doesn't look like it will anytime soon.
[*]Wicd **loses** my connection every 30 seconds, reconnects after each drop, by makes network connection similar to a teenager trying to learn to drive a manual transmission auto.
[*]NetworkManager connects after a long wait and keeps my connection, but won't allow the connection rate to be more than 11M, no matter what settings I have.
[/LIST]
I'm hoping *someone* out there can shed some light on my issue. Please let's not have the ultimate decision be a reinstall of Jaunty.

---

### Post by moore.bryan on 2009-10-18
Alright, here's an update. I decided to spend some hours and go line-by-line through both possible /etc/network/interfaces and /etc/wpa_supplicant.conf combinations. It now seems I have achieved success, although I'm leery to even say that because I risk "jinxing" myself.

I rewrote my /etc/network/interfaces file to look like this:
```

# LOOPBACK INTERFACE
auto lo
iface lo inet loopback

# ETHERNET
allow-hotplug eth0
iface eth0 inet dhcp

# WIRELESS
auto wlan0
iface wlan0 inet dhcp
    wpa-conf /etc/wpa_supplicant.conf    
    wireless-rate 54M

```
The eth0 *allow-hotplug* was a long-shot because I notice when set to *auto*, wireless wouldn't load and the network would just keep trying eth0 instead.

Then, I changed my /etc/wpa_supplicant.conf to this:
```

ctrl_interface=/var/run/wpa_supplicant

network={
    ssid="HOME"
    scan_ssid=1
    key_mgmt=WPA-PSK
    psk="PASSWORD"
}

network={
    ssid="WORK"
    key_mgmt=NONE
    wep_key0=WEPKEY
}

```
Now, and so far, I've rebooted five times and it's worked each time; which, is clearly better than before.

Like I wrote, though... I'm leery to call this a *fix* or *solution* because it hasn't been tested long-term yet. Still, I'm frustrated and irritated at the possible reasons *why* this was so problematic.

---

