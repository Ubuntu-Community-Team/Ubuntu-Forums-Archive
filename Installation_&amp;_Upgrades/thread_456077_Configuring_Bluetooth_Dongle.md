---
title: "Configuring Bluetooth Dongle"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by ascherjim on 2007-05-27
I have a usb Bluetooth dongle and a Bluetooth keyboard. I want to be able to use this keyboard with my Ubuntu desktop. The dongle came with a configuration software cd, which only works for Windows and Mac. Can anyone give me some fairly explicit instructions on how to configure my Ubuntu to be able to achieve this goal? Assuming that Ubuntu has a built-in Bluetooth capability (or can download one), what do I need to do in order to "pair" and utilize the keyboard? Any help or guidance would be appreciated.

---

### Post by dphan on 2007-05-28
OF Dongle, my sol. as follow:
0. install K blustootk client and chat and server / another method, using bluetooth deb for gnome at [http://getdeb.net](http://getdeb.net)
1. plug Dongle in USB
2. reboot sys
3. go to /etc/bluetooth
4. gedit (with sudo) the file hcid.conf
(keep all the same but the PIN (passcode)
5. for more reason, generate /etc/bluetooth/pin file with the same passcode (I dunno this step for wat)
6. save all edited files
7. /etc/init.d/bluetooth restart
8.try to pop-up Kbluetooth client and search devices
note: do not forget to turn on your cell' bluetooth and add new device (Dongle) normally its name is ur-server name-0
9. try to pair with the passcode you generate in hcid.conf file and pin file

hope it helps
D. Phan

---

### Post by ascherjim on 2007-05-28
D. Phan:  Many thanks.  I will give it a try and report back.  Jim

---

### Post by ascherjim on 2007-05-28
D. Phan:  I find I need some clarification.

On your instruction #4:  Where you state "keep all the same but the PIN (passcode),", do I remove (comment out with "#") the passcode entirely, or do I insert a new passcode of my own devising?

On your instruction #5:  When I generate (create) a new /etc/bluetooth/pin file, do I just put in the passcode I have devised by itself on one line of the file, or do I have to have other lines/items in this new file?

On your instruction #8:  How do I "pop-up" the client and search devices?  What command do I enter in order to effect this "pop-up" in order to add my new device?

Thanks in advance for your further help.  Jim

---

