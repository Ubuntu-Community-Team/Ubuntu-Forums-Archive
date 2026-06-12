---
title: "How can I install the Raspberry Pi version of Ubuntu Server 20.10 on an SSD drive"
date: 2021-03-07
forum: Installation &amp; Upgrades
---

### Post by bobfraser1 on 2021-03-07
I've got a Raspberry Pi 4 with 8GB mem and 500GB SSD drive. There appears to be an easy way to install Ubuntu Server to a flash card. How can I get the same OS installed on a bootable USB SSD drive?

---

### Post by grahammechanical on 2021-03-07
Can you not follow the instructions for installing on a microSD card?

[https://ubuntu.com/tutorials/how-to-install-ubuntu-desktop-on-raspberry-pi-4#1-overview](https://ubuntu.com/tutorials/how-to-install-ubuntu-desktop-on-raspberry-pi-4#1-overview)

See the section for the Raspberry-PI 4

[https://ubuntu.com/download/raspberry-pi](https://ubuntu.com/download/raspberry-pi)

Regards

---

### Post by QIII on 2021-03-07
You might also have a look [here]("https://www.raspberrypi.org/documentation/hardware/raspberrypi/bootmodes/msd.md") in the section "Raspberry Pi 4B".

I'd think once you got the EEPROM bit set, you'll be able to choose to boot from the card (on which you should have the installation .iso) and then install to the SSD.

Since the disk interface will be USB, you might want to read up on UASP, USB and the TRIM command.

---

### Post by bobfraser1 on 2021-03-07
I thought the imager only worked on MicroSD cards. I plugged the external SSD into my Mac and the imager saw the SSD and put an image on it. I'll pull the Micro SSD from the Pi and attach the SSD and boot and see. I've got a very recent Pi 4B so I'm hoping that the EEPROM and boot order are all ready to go.

---

### Post by bobfraser1 on 2021-03-31
This almost worked. I updated the network-config. I can boot fine with monitor, mouse, and keyboard. I saw cloud init run and got the login prompt. Changed my password and logged in. No networks. Rebooted still no networks. How do I debug cloud init / netplan to get the networks working?

---

### Post by bobfraser1 on 2021-03-31
User error. I had some bad edits in the network-config that passed the boot test, but failed downstream.

---

