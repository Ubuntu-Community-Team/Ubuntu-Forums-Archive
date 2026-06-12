---
title: "Network interfaces not working on Toshiba Satellite C855-S5347 dual boot"
date: 2013-03-07
forum: Installation &amp; Upgrades
---

### Post by berniejv on 2013-03-07
Hey everybody,

So I just bought a toshiba satellite C855-S5347 with the intention of using it primarily as a unix laptop.

I set it up as a dual boot with the pre-installed windows 8.  I disabled the secure boot from the UEFI interface, installed 12.04.2 LTS, but then had my hopes crushed...

 While the install went smoothly, when I booted up  in Linux it recognizes _neither_ network interface, wired or wireless!  

 The Ethernet card is a Qualcomm Atheros AR8162/8166/8168 (NDIS 6.30)

 The wireless is a Realtek RTL8723AE

 No clue how to proceed other than to trade this thing in...

 Thanks in advance for the help,

 -Joel

---

### Post by ubfan1 on 2013-04-13
Networking is an issue, with neither ethernet Atheros 8161 nor wireless Realtek 8723AE working.  Googled for info on the RTL8723 and found that while
nothing is available directly from Realtek, a dropbox tarball ostensibly from a Realtek technician did have the source for the driver and its firmware --
rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz

  Put the tarball on a USB data drive, bring it to the Toshiba, and unpacked it.  Looked at the code, added -m64 to my driver Makefile since I know it is for a 64 bit system (but that's probably not necessary, try without and if it doesn't work, add it), and made the driver

   make

 and installed it:

   sudo make install

Reboot or add the module yourself
  sudo modprobe rtl8723e

Now network-manager should start scanning, and give you a list of access points.

Once connected, update the system, and the new kernels will include the alx driver for the ethernet.

    sudo apt-get update
    sudo apt-get upgrade

---

