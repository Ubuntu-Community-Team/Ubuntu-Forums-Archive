---
title: "WG111v2 And Intel 4965 And Aircrack"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by rosscoloco on 2008-05-01
So I have a little predicament. I installed Linux just a while ago, so you could say I'm somewhat new~ although I'm familiar with sh and unix..........anyhoo!

I have read and re-read bunches of posts on this forum and Backtrack's forums (the 2 linux disros I installed)

I have 1 goal - to have a wireless card that works in Ubuntu that can connect to the internet AND packet inject with Aircrack

I have a Dell M1330

In Ubuntu my Intel 4965 card (built in) works with the built in wireless manager, but aircrack does not support this card, and won't be supporting it for a while it seems.

So, I have internet with that card, but no injection or even monitor mode.

In Backtrack, I boot up and that card can not inject, but can monitor, and can connect to internet 

In Ubuntu, my WG111v2 USB card does not work at all. I get:

> [ 3038.452000] usb 7-1: new high speed USB device using ehci_hcd and address 9
[ 3038.588000] usb 7-1: configuration #1 chosen from 1 choice
[ 3038.644000] mac80211: exports duplicate symbol ieee80211_stop_queue (owned by ieee80211_rtl)
[ 3038.648000] rtl8187: Unknown symbol ieee80211_free_hw
[ 3038.648000] rtl8187: Unknown symbol ieee80211_alloc_hw
[ 3038.648000] rtl8187: Unknown symbol ieee80211_register_hw
[ 3038.648000] rtl8187: Unknown symbol ieee80211_tx_status_irqsafe
[ 3038.648000] rtl8187: Unknown symbol ieee80211_unregister_hw
[ 3038.648000] rtl8187: Unknown symbol ieee80211_register_hwmode
[ 3038.648000] rtl8187: Unknown symbol ieee80211_rx_irqsafe
[ 3038.648000] rtl8187: Unknown symbol ieee80211_rts_duration


out of the dmesg command

The WG111v2 does not work at all. Ubuntu will not even recognize it as a wireless device.

So, Backtrack fully supports this card for injection and connection~ it works great all around.

My question: why the heck should I have to use some crazy thirdparty program like ndiswrapper just to get my WG111v2 working when it works fine in another Linux Distro? Plus, even if I do use ndiswrapper, packet injection seems like it will not work...........ahhhhhhh!

I like Ubuntu for it's interface and compatibility with my system, but when it comes the WG111v2 it seems like I'll never get packet injection working within Ubuntu.........I know the simple answer is to just boot into Backtrack...........but who wants to do things simple ;)

Anyway~! Thanks for any information you can give!

---

### Post by Alacrity on 2008-05-08
First thing you should do is confirm the chipset of your USB dongle.  That determines what driver & patch you use in Ubuntu.

Google a little bit.  Google on "WG111v2 chipset".  My quick google showed:

The Netgear WG111 v2 USB card, contains a Realtek chipset. The card works with linux, but you need a 2.6.x kernel! Before you can use this card, you need to disable the IEEE80211 framework that comes wit the kernel. the driver comes with an own IEEE80211 Framework that is not compatible with the one in the kernel.
Take care to load the modules in the correct order, otherwise the card won't work:
ieee80211_crypt_rtl
ieee80211_crypt_wep_rtl
ieee80211_crypt_tkip_rtl
ieee80211_crypt_ccmp_rtl
ieee80211_rtl
r8187

But a new easier method once you know it is the 8187 chipset is to use the Airdriver-ng function within the Aircrack-ng suite to install your chipset into Aircrack-ng.

Check with the aircrack-ng.org web site and read a little bit.  Ubuntu works fine with your USB unit and injects as well.

These are the drivers supported for full injection in aircrack-ng/airdriver-ng:

Following drivers are supported:
0. ACX100/111 - IEEE80211
1. ADMtek 8211 - IEEE80211
2. ADMtek 8211 - mac80211
3. Atmel at76c50x - IEEE80211
4. Atmel at76_usb - IEEE80211
5. Broadcom 4300 - IEEE80211
6. Broadcom 4300 - mac80211
7. Cisco/Aironet 802.11 - IEEE80211 Softmac
8. HostAP - IEEE80211
9. Intel Pro Wireless 2100 B - IEEE80211
10. Intel Pro Wireless 2200 (B/G)/2915 (A/B/G) - IEEE80211
11. Intel Pro Wireless 3945 A/B/G - IEEE80211
12. Intel Pro Wireless 3945 A/B/G - raw mode
13. Intel Pro Wireless 3945 A/B/G - mac80211
14. Intel Pro Wireless 4965 A/B/G/N - mac80211
15. Lucent Hermes and Prism II - IEEE80211
16. Madwifi[-ng] - IEEE80211
17. Prism54 - IEEE80211
18. Prism54 - mac80211
19. Ralink rt2400 (legacy)
20. Ralink rt2400 (rt2x00) - IEEE80211
21. Ralink rt2400 (rt2x00) - mac80211
22. Ralink rt2500 (legacy)
23. Ralink rt2500 (rt2x00) - IEEE80211
24. Ralink rt2500 (rt2x00) - mac80211
25. Ralink rt2570 (legacy)
26. Ralink rt2570 (rt2x00) - IEEE80211
27. Ralink rt2570 (rt2x00) - mac80211
28. Ralink rt61 (legacy)
29. Ralink rt61 (rt2x00) - IEEE80211
30. Ralink rt61 (rt2x00) - mac80211
31. Ralink rt73 (legacy)
32. Ralink rt73 (rt2x00) - IEEE80211
33. Ralink rt73 (rt2x00) - mac80211
34. Realtek rtl8180 - custom
35. Realtek rtl8187 - custom
36. Realtek rtl8187 - mac80211
37. WLAN-NG - IEEE80211
38. Xircom Creditcard Netwave - IEEE80211
39. ZyDAS 1201 - IEEE80211 Softmac
40. ZyDAS 1211 - IEEE80211 Softmac
41. ZyDAS 1211rw - IEEE80211 Softmac
42. ZyDAS 1211rw - mac80211



Enjoy:)

---

### Post by iipochi on 2010-01-15
bump ..

hi everybody ..

instead of opening up a new thread i thought i would continue my problem in this thread.

my situation is similar i have built-in wireless card that is not supported by aircrack and so i have netgear wg111v2 usb wireless stick which i assume works perfectly fine with aircrack both monitor mode and  packet injection.

however i cannot get it to work for packet injection...hence i would like ur help.

i m someone who has been on and off with the linux OS ...hence i m not good at it.

if someone can write a detailed explanation of how to patch the the driver to get to work for packet injection that would be really helpful.

and also after that how to crack WEP tutorial...oh and btw Os is Ubuntu Jaunty(9.04 i guess)


thankx in advance.

Imran



thannk you...

---

