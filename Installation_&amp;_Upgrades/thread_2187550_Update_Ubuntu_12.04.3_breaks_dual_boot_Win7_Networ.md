---
title: "Update Ubuntu 12.04.3 breaks dual boot Win7 Network"
date: 2013-11-12
forum: Installation &amp; Upgrades
---

### Post by glenvr22 on 2013-11-12
Hi There, 

I was hoping someone could help me. 

I installed Ubuntu 12.04 alongside Windows 7 without any problems. 

I had everything setup when I decided to update and upgrade in my terminal. 

After the process was complete my network wouldn't work on Ubuntu or Windows. 

On my Windows side the network adapter completely vanished. Trying to re-install the driver tells me no network devices found. System Restore didnt help either.

On my Ubuntu side I tried installing my Linux LAN Drivers again but it wouldnt pick anything up. 

Is there something I can do to solve the problem? I have never encountered this before.

---

### Post by glenvr22 on 2013-11-12
.

---

### Post by glenvr22 on 2013-11-13
.

---

### Post by oldfred on 2013-11-13
Bit of a unusual issue. Might even be co-insidence failure of network hardware? As both Windows & Linux not working should be unrelated. But I saw similar issue years ago and we all said it was not possible that Window or Linux was interfereing with the other after a full cold boot.
In that case the network card saved settings and either Linux or Windows changed settings and did not reset it correctly. I think the only final solution was a bug fix in Linux to work around Windows and force setting changes that would not normaly be required. 

I do not know network issues but what card? Can post all of this:
Copy to flash drive and upload if necessary.
lspci > ~/abs-network.txt
lsusb >> ~/abs-network.txt
ifconfig >> ~/abs-network.txt
iwconfig >> ~/abs-network.txt
Attach (via the paperclip in advanced edit menu) the abs-network.txt file which will be in your home folder.

---

### Post by charlie99 on 2013-11-13
? can you boot the system from a LiveCD  that has some 'diagnostic' oriented distros ? I was recently impressed by grml on LXF177 cover disc...(also has LXLE 12.04.3 ).

Use the lspci -vvv command and the output can prove whether your LAN card is still recognized or not (ie enumerates on the PCI-* bus); if it does NOT, that suggests that whatever non-volatile memory on the card held the config/id info has been wiped (happened to me once, due to a problem with the NV memory chip).

I also recall a similar issue with a WiFi card (but separate Linux & Windows discs); one bad version of the Linux WiFi driver messed up something in the BIOS NV RAM so Windows would not see the WiFi card either...fixed that by some sequence like removing the card, booting into Windows Safe mode, power-off, re-boot to normal mode, power off, replace card, reboot... (each time look in device manager for any signs of the card driver, & remove anything found.).

---

