---
title: "Intrepid Atheros AR5007EG stoped after upgrade from beta to release candidate"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sanone on 2008-10-25
I have an Acer Aspire 5315-052G12Mi on which I run Ubuntu for a while. This latest version of ubuntu makes the install a lot easier that previous releases ([see my tutorial]("http://ubuntuforums.org/showthread.php?t=610603")).

I installed intrepid beta on this notebook and all but wifi (Atheros AR5007EG) worked out of the box. On IRC I got the tip to remove the linux-restricted-modules* packages. After the reboot I had fully working wifi!

Now I recently upgraded to the "Release Candidate" of intrepid. I'm sure it fixed a lot of issues but it broke my wifi! On a suggestion I installed linux-backports-modules-intrepid-generic, linux-backports-modules-2.6.27-7-generic and linux-backports-modules-intrepid. This brings the device back in the network manager applet but it doesn't work.

I could some help here. Why did a working driver get ditched. And why didn't I get at least a warning / info text explaining what to do to get it working again.

Thanks in advance,
San

---

### Post by radox1912 on 2008-10-26
i got exactly the same problem as you. my asus F5VL AR5007EG has stopped workin since i installed some updates.(from beta to RC)
now i cannot acces wifi networks anymore and have to stick to that stupid Vysta again :(

---

### Post by radox1912 on 2008-10-26
hi, i found a solution in other thread

sudo apt-get install linux-backports-modules-intrepid
then reboot and it should be working
at least it worked for me.

---

### Post by Nublet on 2008-10-26
the other solutions didn't work for me, but installing the snapshot seems to do:
[http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3861-20080903.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3861-20080903.tar.gz)
see also:
[http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

---

### Post by ryawn on 2008-10-26
> **radox1912 said:**
> hi, i found a solution in other thread

sudo apt-get install linux-backports-modules-intrepid
then reboot and it should be working
at least it worked for me.

right on! that fixed the problem for me.

---

### Post by kswick on 2008-10-27
Okay, I've been attempting to find these backports and so far have been unsuccessful. I've modified /etc/apt/sources.list I thought were the appropriate paths but it did not work. Any suggestions?

Thanks

kswick@boann:/etc/apt$ sudo apt-get install linux-backports-modules-intrepid*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-intrepid*
kswick@boann:/etc/apt$ sudo apt-get install linux-backports-modules-intrepid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-intrepid

---

### Post by kswick on 2008-10-27
> **kswick said:**
> Okay, I've been attempting to find these backports and so far have been unsuccessful. I've modified /etc/apt/sources.list I thought were the appropriate paths but it did not work. Any suggestions?

Thanks

kswick@boann:/etc/apt$ sudo apt-get install linux-backports-modules-intrepid*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-intrepid*
kswick@boann:/etc/apt$ sudo apt-get install linux-backports-modules-intrepid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-intrepid

Solved it. Too simple.

apt-get update

---

### Post by bobpaul on 2008-10-30
I've been getting "wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)" on bootup and ath_pci/ath_hal modules are loaded, but no wifi device shows. Since I updated from hardy to intrepid alpha, it's been using ath5k, but like others noted, after updating to the beta it's no longer working (Acer Aspire 3050). I can goto System->Admin->Hardware Drivers and turn on "Support for Atheros 802.11 cards" but that doesn't seem to work. Installing the linux-backports-modules-intrepid-generic also hasn't helped.

What changed from Alpha to Beta that might cause this?

**Solution**
Added "blacklist ath_pci" to /etc/modprobe.d/blacklist, installed linux-backports-modules-intrepid-generic, enabled Support 5xxx Series Atheros" in Hardware Drivers, and everything worked on reboot. I'm still curious why this was all necessary.

---

