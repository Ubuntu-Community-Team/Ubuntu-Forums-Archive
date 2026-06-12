---
title: "unable to Make Wired Ethernet Working in Ubuntu tty Session"
date: 2013-11-21
forum: Installation &amp; Upgrades
---

### Post by shravan.vaddadi on 2013-11-21
Hi There,
I Tried to upgrade my Ubuntu 12.04 to 12.10 and in between power lost and due to this it tried for a partial upgrade and installed 1286 Packages
but after Restart I am getting an error Message "Failed to Load Session Ubuntu" .If i am Trying to Login tty2 Session thru Ctrl+Alt+F2 i am able to give the commands 
"sudo apt-get update" but as the Ethernet is not Up and working it is unable to Download or Correct the Errors,Pls help me make the Ethernet Interface Active and when i am booting the same thru ubuntu 12.04 Live CD Ethernet interface is working and i am able to connect to internet.

I Tried searching for some threads ([http://ubuntuforums.org/showthread.php?t=1505697](http://ubuntuforums.org/showthread.php?t=1505697)) but those require an internet connection to solve
Pls find the outputs for some of the commands
lshw -C Network
*-network UNCLAIMED
   description: Ethernet controller
   product: AR8132 Fast Ethernet
   vendor: Atheros Communications Inc.
   physical id:0
I am typing the outputs from another PC.


-Shravan

---

### Post by heir4c on 2013-11-21
Boot up and choose the "recovery mode" in Grub. Then in the menu that you will see you can choose for "root shell with internet connection".

---

### Post by shravan.vaddadi on 2013-11-22
Hi,
When i am Trying to choose "recovery mode" in Grub I am not able to find this Option "root shell with internet connection".

my version of Grub is GNU GRUB version 1.99-21ubuntu3.10
Ubuntu, with Linux 3.5.0-43-generic (recovery mode)
Pls find the output which i am typing from other system

Recover  Menu (filesystem state:read/write)
resume   Resume normal boot
clean     Try to make free space
dpkg      Repair broken packages
failsafeX Run in failsafe grafic mode
fsck       Check all file systems
grub       Update grub bootloader
network  Enable networking
root       Drop to root shell prompt
system-summary System summary

Is there any other option to activate Ethernet in Grub

---

### Post by steeldriver on 2013-11-22
At the main recovery mode menu, try selecting

```
network            Enable networking
```

Once it's done, it should return you back to the menu and you can then select

```
root                Drop to root shell prompt
```

---

### Post by shravan.vaddadi on 2013-11-22
Hi
After Selecting Network its showing a message "Continuing will remount your / filesystem in read/write mode and mount any other filesystem defined in /etc/fstab/
Do you wish to countinue?
After selecting Yes Some messages flashed and disappeared but the Ethernet Interface was not started as i am able to see the LED on the router

I Tried to take a photo of the screen pls find the photo below , the mode of Network thru which i am connecting is thru router and i configured auto dial up in the router, 
[IMG]D:\UP\23112013268.jpg[/IMG]

---

### Post by shravan.vaddadi on 2013-11-22
Hi I have attached the photo in another reply

---

### Post by shravan.vaddadi on 2013-11-23
Hi,
As i am unable to solve the issue i formated it with a old release.
Thanks to heir&steeldriver for trying to help

---

### Post by heir4c on 2013-11-23
> **shravan.vaddadi said:**
> Hi,
When i am Trying to choose "recovery mode" in Grub I am not able to find this Option "root shell with internet connection".

my version of Grub is GNU GRUB version 1.99-21ubuntu3.10
Ubuntu, with Linux 3.5.0-43-generic (recovery mode)
Pls find the output which i am typing from other system

Recover  Menu (filesystem state:read/write)
resume   Resume normal boot
clean     Try to make free space
dpkg      Repair broken packages
failsafeX Run in failsafe grafic mode
fsck       Check all file systems
grub       Update grub bootloader
network  Enable networking
root       Drop to root shell prompt
system-summary System summary

Is there any other option to activate Ethernet in Grub


So, it's changed a little bit.
Why they change that, it was easy to use.
They will learn never. When something is good and works, don't touch it.


I'm glad you got it solved, in a way.

---

### Post by ptrakk on 2013-11-23
put interface up
# sudo ifconfig eth0 up

acquire ip. use one of the three(whatever works):
# sudo dhclient eth0
# sudo  dhclient3 eth0
# sudo dhcpcd eth0

repair your install:
#sudo apt-get update
#sudo apt-get dist-upgrade

---

