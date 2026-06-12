---
title: "Intrepid and Atheros AR242x wireless/wifi"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by tim|mit on 2008-10-06
I've just got a Samsung Q210 and am posting this to help anyone else that has had a problem getting the wireless to work after a fresh install of the lastest Intrepid beta.

Running, 'lspci -v' gives,

02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

Immediately after an install iwconfig didn't show any wireless modules existing. After a lot of googling I finally found the _really_ simple solution to getting this to work,

sudo vi /etc/modprobe.d/blacklist

and append,

blacklist ath_pci
blacklist ath_hal

save and reboot, fingers crossed on startup wireless should be working.

It seems that there are two drivers that are loaded by default, and the first one doesn't work for this card. Not sure if this is something that can be easily rectified during the install process because if it could it would let this computer work pretty much out of the box.

Hope this is helpful to someone

---

### Post by 7he on 2008-10-12
Hi!
I'm very interested in how you managed to get your AR242x chipset working with intrepid ibex.

I can't have the wifi working on intrepid; please have a look at this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/273266](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/273266)

Here's is the result of lspci:
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
Computer: Samsung R20

I tried to blacklist the 2 modules you mentioned but had no result.
What version of the kernel do you use? Did you made any other trick to have the wifi working?


Thanks in advance

---

### Post by inportb on 2008-10-12
I'm guessing that just keeps madwifi from conflicting with ath5k. I've been utilizing the opposite approach: blacklisting ath5k and installing a patched madwifi, and that seems to work quite well too.

---

### Post by Chibone on 2008-10-28
I have an Atheros AR242x and what worked for me was installing the package "linux-backports-modules-intrepid". My laptop is a Compaq F767NR.

Here's the output from lspci -v:

```
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f6000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k_pci
	Kernel modules: ath_pci, ath5k

```

My kernel version is 2.6.27-7-generic and I am running 64 bit Intrepid.

---

### Post by inportb on 2008-10-28
Interesting; I never knew that package existed =p

---

### Post by cash34 on 2008-10-28
THANK YOU!!

this worked perfectly for me.

i have an HP DV6810us 
with an atheros 5007 card

---

### Post by macabro22 on 2008-10-29
Craaap! I can't get mine to work. I tried everything already

---

### Post by tim|mit on 2008-10-29
The latest upgrade (to 2.6.27-7-generic) stopped the fix that worked initially for me from working. 

Strangely even though ath_hal and ath_pci were in the blacklist, ath_pci was being loaded and not working again. I couldn't seem to remove this module, or force ath5k to be used but as Chibone said above installing the linux-backports-modules-intrepid sorted the problem out.

Has anyone else experienced the odd behaviour of saved wpa keys being incorrectly decrypted, every now and then when I start up the key seems to be mangled and is a much much longer hex looking string. If I then restart the correct key is decrypted and I can connect again.


> Craaap! I can't get mine to work. I tried everything already

macabro22, are you doing a restart after trying things, or a full shutdown? The reason I ask is that a full shutdown seems to completely reset the card more so than a restart.

---

### Post by aberke on 2008-10-29
> **Chibone said:**
> I have an Atheros AR242x and what worked for me was installing the package "linux-backports-modules-intrepid". My laptop is a Compaq F767NR.

<snip>

My kernel version is 2.6.27-7-generic and I am running 64 bit Intrepid.

This worked perfectly for me (on a Lenovo ThinkPad T400). Restarting afterwards is necessary as well, I believe.

---

