---
title: "Installing Vodacom Mobile Broadband Lite in Ubuntu 10.04LTS"
date: 2012-01-18
forum: Installation &amp; Upgrades
---

### Post by nmoyefelix on 2012-01-18
Hi Everyone,
Pls I am a newbie in this, so forgive my ignorance.
I need help for on installing of Vodacom Mobile Broadband Lite in Ubuntu 10.04LTS.
I just bought a USB modem ZTE K3772 - Z.

---

### Post by vagiq on 2012-02-21
I have exactly the same problem, but for Maverick (10.10). It's not listed in the usb_modeswitch data file for Maverick or Natty, but it does appear in Oneiric's one:

# Vodafone (ZTE) K3772-Z
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="1179", RUN+="usb_modeswitch '%b/%k'"

but given this info, how to change usb_modeswitch to recognise this modem? I checked out the maverick backports site, someone requested it but no response yet. Short of installing the latest usb_modeswitch and risking clobbering something else, what to do? 

Please help
Vagiq

---

### Post by querolus on 2013-02-12
Hi

I'm having the same trouble... has any of you been able to solve it? If so, could you share the solution?

Thanks

---

### Post by querolus on 2013-02-12
Ok i did it...

it's pretty easy in fact if you have a double boot set up:

1. Boot with windows and install the Vodafone Mobile Broadband following instructions
2. Without unplugging the USB stick, re-start the computer and boot with Ubuntu
3. Click on the network icon and add a GSM network
4. Follow the steps for your country and finish setting up connection
5. Re-boot again and then it should work

If you want more details please let me know

---

