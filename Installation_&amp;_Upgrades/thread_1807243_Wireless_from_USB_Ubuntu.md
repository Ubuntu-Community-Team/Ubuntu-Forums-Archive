---
title: "Wireless from USB /Ubuntu"
date: 2011-07-18
forum: Installation &amp; Upgrades
---

### Post by bayouoldguy on 2011-07-18
I have a quick question regarding running Ubuntu 11.04 from a USB stick. Can I set up a wireless network or access my network from the USB stick ?. I think the trial download does not have the "firmware" for my wireless router, ( Linksys E2000 ). Loaded page indicates "no firmware"....could not seem to download or update the USB loaded program.....Any thoughts Ubuntu fans ???...
...."G"    ( Running a Dell D620 w/Windows Vista Business , works fine thru Windows/Linksys & can "hardwire" to the internet on the USB/Ubuntu load).

MY SOLUTION :
i tried to access & set up Ubuntu 11.04 & my wireless net. was not able to "enter" any terminal commands changing the wireless setups. If I re-booted, I lost the settings in the USB stick.
Saw all the problems of others trying to get Wireless up & came to this conclusion:
I stopped trying to use the USB/Ubuntu 11.04 stick & went back and reloaded Ubuntu 10.04LTS. Was able to get up & running on Wireless after uninstalling "bcmwl-kerne--source" & "bcmwl-modaliases", then installing "b43-fwcutter", re-booting, configuring my Wireless SSID, Security as: WPA & WPA2 Personal & putting in the passcode. A re-boot started up the Wireless & showing ALL neighborhood nets !.
Therefore: I installed Ubuntu 10.04LTS on my Dell D620 until
the Ubuntu Team/users correct the Driver situation !..."G"

---

### Post by bayouoldguy on 2011-07-19
I found the Help page : [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx?](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx?)
There is a listing for: "LiveCD/LiveUSB" setups, now I need to
go & try this to setup the wireless. Will post a "solved" comment if I get it running....."G"   7:00PM CDT 07/19/11  :)

---

### Post by bayouoldguy on 2011-07-22
Update 07/22/11 after some attempts to get a wireless working.
On page 3 :Step 3: "Instead of a computer restart, in a terminal
issue the following commands:
  ~$ sudo modprobe -r b43 ssb wl
  ~$ sudo modprobe wl
I could not get the terminal to accept an "Enter" command,
then the "restart" type of function could not be performed.
Any suggestions Ubuntu community ?....G

[I found the Help page : [https://help.ubuntu.com/community/Wi...river/bcm43xx?]](https://help.ubuntu.com/community/Wi...river/bcm43xx?])
 ( Running a Dell D620 w/Windows Vista Business , works fine thru Windows/Linksys E2000 & can "hardwire" to the internet on the USB/Ubuntu load).

---

### Post by bayouoldguy on 2011-08-08
Re: Dell Latitude d620 Wireless issue
Re: Dell Latitude D600 Problem
Look what I found !....

[url]https://launchpad.net/ubuntu/maverick/i386/firmware-b43-installer
& listed file:

firmware-b43-installer_4.150.10.5-4_all.deb (5.1 KiB)

I downloaded the file to the "Downloads" folder, & commanded to "extract".
It installed.....found my Wireless & is up & running from the USB stick !!.
I installed the b43-fwcutter package from the Synaptic Package manager first. The wireless apt always showed me "no firmware", & the "apt-get install firmware-b43-installer" command would not execute.

Now I guess I can upgrade to the 11.04 version !......"G"

All you guys having Dell D6XX series laptops with the Broadcom BCM4311
802.11 b/g Wlan wireless card may want to try this......

---

### Post by gordintoronto on 2011-08-09
Just to clarify, your problem had nothing to do with your router, and everything to do with the wireless adapter in your computer. If you open Accessories/Terminal, and enter the command lspci, it will tell you exactly what adapter is in your computer.

To have changes apply across a reboot with a USB stick, it must be "persistent."

---

### Post by bayouoldguy on 2011-08-09
> **gordintoronto said:**
> Just to clarify, your problem had nothing to do with your router, and everything to do with the wireless adapter in your computer. If you open Accessories/Terminal, and enter the command lspci, it will tell you exactly what adapter is in your computer.

To have changes apply across a reboot with a USB stick, it must be "persistent."
gordintoronto :
Thanks for the reply....did not mean to imply that I had a router problem. I realized that the wireless card was the "gorilla".....take it to the next step, how do you get a flash drive to be "persistent". Always like to learn something new...."G"

---

### Post by gordintoronto on 2011-08-09
I use Multisystem to make a persistent flash drive. It's not perfect, but the result is OK.

See Full Circle Magazine, issue 45, for more details.

---

