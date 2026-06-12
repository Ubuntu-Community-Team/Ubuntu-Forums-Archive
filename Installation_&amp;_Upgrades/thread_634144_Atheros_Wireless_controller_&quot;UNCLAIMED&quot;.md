---
title: "Atheros Wireless controller &quot;UNCLAIMED&quot;"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by Stuart Soloway on 2007-12-07
I am new to Ubuntu, but disgusted with Vista.  So I am trying to install Ubuntu on my Acer 3680-2682 laptop.  In both Feisty Faun (running from a live CD) and Gutsy Gibbon I have this problem:

If I go to the Restricted Drivers Manager, I see the driver "Atheros Hardware Access Layer (HAL)" listed as enabled and in use.  So I think I should be able to access my wireless network.  But then I go to Network Settings and I see only two connections listed, a Wired connection and a Modem connection.  This doesn't see right.  I was hoping to see my wireless device listed as a third connection, along with a way to select a wireless network. 

When I do "sudo lshw", for my wireless controller it says "*-network UNCLAIMED" followed by the description, product, vendor, etc info for my Atheros controller.  I'm hoping this points the way to resolving my problem.

Is what I describe normal?  If so, what do I do to bring up a wireless connection?  If not, can someone help me fix it?  

Thanks in advance for any help.

---

### Post by Pumalite on 2007-12-07
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

---

### Post by Stuart Soloway on 2007-12-10
Thank you.

I went through the "wireless troubleshooting guide" you pointed me to.  The problem seems to lie here:

if I do "iwconfig" it says 

lo     no wireless extensions.

eth0  no wireless extensions


So I conclude that the driver isn't identifying itself as a wireless device to the kernel.  Unfortunately the troubleshooting guide doesn't say what to do when that happens.

When I do "sudo lsmod |grep ath" it says 

ath_pci   97312     0
wlan      204484    1 ath_pci
ath_hal  192592    1 ath_pci

which I take to mean that the "restricted" driver is correctly loaded.  By the way, all the buses seem to be either secondary or subordinate to bus 00, except for bus 0b which is secondary to 0a, which in turn is secondary to 00. 

When I do ifconfig, I see an Eth0 interface and a l0 interface (loopback?), but nothing that looks like a wireless interface. 

Thanks again for any help.

Stu

---

### Post by Stuart Soloway on 2007-12-12
My problem is solved!  "HOWTO: Atheros AR5007EG on Feisty Fawn (with ndiswrapper)"  solved my problem.  I suspect that the driver in Feisty just doesn't support the AR5007GE chip.  See my response over there for any further details.

Stu

---

### Post by Pumalite on 2007-12-12
Congrats.

---

### Post by Stuart Soloway on 2007-12-26
After the fix described above, I ran happily for a while. but then WPA stopped working. My guess is that it was after an update, but I'm not sure which.  I could connect without security, but not with WPA.   I saw a note from someone who had a similar problem with an Acer Aspire using a BCM chip (I'm using an Atheros).   In that case, Gutsy fixed his/her problem, so I upgraded to Gutsy.  I re-did the same procedure (I think) to install the ndiswrapper-wrapped driver, but now the Restricted Drivers Manager says the HAL driver is "enabled" but "not in use", and I have no wireless at all.  Again, I see this text:

  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:03:0A  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 
WICD says  there are no wireless networks.  

I tried removing references to Ath0 in /etc/network/interfaces; I'm not sure how they got there and I saw a note where someone had solved a similar problem in Gutsy that way.  It didn't make any difference.

This is different from my original problem in Feisty in that the Restricted Drivers Manager then said the driver was in use. Also, I seem to remember that the chip wasn't identified as an AR5006EG (which is what it is).

Thanks for any and all advice.

---

### Post by Pumalite on 2007-12-26
Run this:
sudo apt-get install linux-backports-modules-generic
Reboot.
Then, in Terminal:
lshw -C sound
Post the output.

---

### Post by Stuart Soloway on 2007-12-27
All right, you have piqued my curiosity.  What does sound have to do with my wireless problem?

In the interest of full disclosure, I should point out that I installed Alsa driver, lib, tools, and utils version 1.0.15 before I upgraded from Feisty to Gutsy.  I also made an unsuccessful attempt to install Madwifi; I gave up when my make had a bunch of errors.

Also note: I have ath_pci blacklisted as per the procedure I used to install the ndiswrapper-wrapped driver.

Stu


stuart@stuart-laptop:~$ sudo lshw -C sound
[sudo] password for stuart:
  *-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
stuart@stuart-laptop:~$

---

### Post by jken146 on 2007-12-27
Have you tried madwifi?

---

### Post by Pumalite on 2007-12-27
[http://hamzakc.wordpress.com/2006/12/11/atheros-wireless-setup-ubuntu/](http://hamzakc.wordpress.com/2006/12/11/atheros-wireless-setup-ubuntu/)

---

### Post by Stuart Soloway on 2007-12-27
Regarding Madwifi, it depends on what you mean by "try".   I downloaded it, did a make clean, and a make.  The make got a bunch of compiler errors, at which point I gave up.  I would have used the Synaptics Package manager, but I couldn't find a package that looked like Madwifi.  

I won't try to hide the fact that I know little about Ubuntu and Linux; I have been working on vague memories from when I used Unix many years ago.

I will try the link you pointed me to.

Thanks,
Stu

---

### Post by Pumalite on 2007-12-27
Good luck!

---

### Post by Stuart Soloway on 2007-12-27
I tried that link to install Madwifi. Things went perfect until I said "svn checkout [http://svn.madwifi.org/trunk](http://svn.madwifi.org/trunk) madwifi".  Turns out there is no "trunk" directory there.  There is a Madwifi directory and an Ath5k directory; I tried svn checkout [http://svn.madwifi.org/Ath5k/trunk](http://svn.madwifi.org/Ath5k/trunk) madwifi.  (I have heard there is a patch for my chip that hasn't been or can't be included in the mainline.)

Anyway, when I did the make it got a bunch of errors; here is where they started:

  CC [M]  /home/stuart/Madwifi_drivers/madwifi/base.o
In file included from /home/stuart/Madwifi_drivers/madwifi/base.h:49,
                 from /home/stuart/Madwifi_drivers/madwifi/base.c:57:
/home/stuart/Madwifi_drivers/madwifi/ath5k.h:244: error: redeclaration of enumerator ‘MODE_ATHEROS_TURBO’
include/net/mac80211.h:105: error: previous definition of ‘MODE_ATHEROS_TURBO’ was here
/home/stuart/Madwifi_drivers/madwifi/ath5k.h:246: error: redeclaration of enumerator ‘MODE_ATHEROS_TURBOG’
include/net/mac80211.h:107: error: previous definition of ‘MODE_ATHEROS_TURBOG’ was here
/home/stuart/Madwifi_drivers/madwifi/base.c:183: error: ‘PCI_VENDOR_ID_ATHEROS’ undeclared here (not in a function)
/home/stuart/Madwifi_drivers/madwifi/base.c:188: error: ‘PCI_VENDOR_ID_3COM_2’ undeclared here (not in a function)
/home/stuart/Madwifi_drivers/madwifi/base.c:285: warning: ‘enum set_key_cmd’ declared inside parameter list

---

### Post by Stuart Soloway on 2007-12-28
I may have made some progress, but it still doesn't work.  On [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679) there is a link to the source for a version with a patch to support my chip.  I was able to make clean, make, and make install successfully, and do the modprobes.  After rebooting, the restricted driver manager shows it enabled and in use.  But when I look at wicd it shows no wireless networks.

---

### Post by Stuart Soloway on 2007-12-28
I finally got it to work!  It turns out that my one remaining problem was in Wicd; it needed to be configured to use the Madwifi WPA supplicant driver and the ath0 wireless interface name.  

Thanks for pointing me in the right direction.

---

### Post by Pumalite on 2007-12-28
You are welcome. I'm very glad you got it working.

---

