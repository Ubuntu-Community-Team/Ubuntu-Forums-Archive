---
title: "No wlan after kernel update, Broadcom 43"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by amityak on 2008-08-03
Hello People!

I've recently reinstalled ubuntu 7.10, thats because i thought it would ran frictionless. It actually did work almost perfect from the box (except for some xorg.conf twiches)

It installed almost automatically the needed firmware for my BC4318 and all was goody good.

Then i did some updates including the kernel to 2.6.22-15

since then wireless stops responding.

As i have no LAN connection but just wireless at home i reboot to the 14 version and now its working fine.

any ideas what might have gone wrong?


####SOME MAYBE NECCESARY QUETES:####

lspci:

00:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Unknown device 17f9:0006
        Flags: bus master, fast devsel, latency 64, IRQ 20
        Memory at d0000000 (32-bit, non-prefetchable) [size=8K]


ill try to get now the iwconfig output from the kernel version 15 and then reboot to report if here.

Thank you all!



###EDIT### ::

Been back from the darkness and here are the outputs from the newer kernel:

jts@jake:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


#######################################################################    

jts@jake:~$ modprobe -l | grep ipw
/lib/modules/2.6.22-15-generic/kernel/drivers/usb/serial/ipw.ko
/lib/modules/2.6.22-15-generic/kernel/drivers/net/wireless/ipw2100.ko
/lib/modules/2.6.22-15-generic/kernel/drivers/net/wireless/ipw2200.ko
/lib/modules/2.6.22-15-generic/ubuntu/wireless/ipw3945/ipw3945.ko

#######################################################################    


10x all!!

---

### Post by amityak on 2008-08-03
no comments?

---

### Post by lwfinger on 2008-08-16
I'm interested in your problem. It seems that you may have been bitten by a bug related to an SPROM coding problem. If you want to help, please run the following commands in a terminal with module ssb loaded:

SPROM=$(find /sys -name ssb_sprom)
echo $SPROM

The first of these may spit some warnings, but as long as the second looks something like /sys/devices/pci0000:00/0000:00:0d.0/0000:04:00.0/ssb_sprom
it is OK. Next do

sudo cat $SPROM > sprom.dat

This will read out the contents of your SPROM. Please post the contents of sprom.dat here, or attach the file.

BTW, wht brand does this card have on it? The official list of PCI vendors does not contain the code 0x17F9.

Larry

---

### Post by amityak on 2008-08-16
Hey

thanks for the reply.
i will try and see how it works.
at the moment i can get wlan, though sometimes it works and sometimes not. cant really explain it.

---

