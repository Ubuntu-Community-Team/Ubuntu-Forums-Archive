---
title: "Ubuntu 10.10 installation hangs on 5 dots screen"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by WikiLeaks on 2010-12-11
I am trying to install Ubuntu 10.10 in a relatively old system, but installation hangs on 5 dots screen. My DVD drive LED keeps on while HDD LED goes off. I have tried various options like acpi=off, noapic, nolapic, i915.modeset=1 etc without any luck. Following are my system specifications.

Dell Dimension 3000 Series
CPU: Intel Pentium 4, 3 GHz
RAM: 1 GB
HDD: ST3160021A
DVD: ASUS DVD-E616A
Graphics Controller: Intel 82865G 
Network Adapter: TP-LINK 802.11b/g Wireless Adapter

I even tried Ubuntu 10.10 alternate disk, I was able to install successfully through it but system kept on hanging randomly after boot-up.

---

### Post by ajgreeny on 2010-12-11
What about the **nomodeset** boot option?  That may do it.

---

### Post by WikiLeaks on 2010-12-12
> **ajgreeny said:**
> What about the **nomodeset** boot option?  That may do it.

Same result, no luck. I am not sure how I can track the real cause of this problem. Can anyone guide my how I can track this problem?

---

### Post by kansasnoob on 2010-12-12
Is there an existing OS on it?

If so does it still run?

Do you have access to any other Live OS discs?

Give us some history please, and what do you have available.

Also, to be sure it's not a defective CD/DVD drive, do you have a spare flash drive?

---

### Post by kansasnoob on 2010-12-12
BTW, very bad choice for a username! I do a bit of political blogging and wikileaks is bad news right now!

---

### Post by Rubi1200 on 2010-12-12
If Ubuntu is installed, you need to use the i915.modeset parameter at boot.

Press "e" to highlight the entry in GRUB then navigate with the cursor to the line that ends with quiet splash. 

Remove quiet splash and type  i915.modeset=1 followed by "Ctrl" + "x" to boot.

This also provides more information:
[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

---

### Post by WikiLeaks on 2010-12-20
> **kansasnoob said:**
> Is there an existing OS on it?

If so does it still run?

Do you have access to any other Live OS discs?

Give us some history please, and what do you have available.

Also, to be sure it's not a defective CD/DVD drive, do you have a spare flash drive?

Yes, I have Windows XP installed on this machine and it runs fine. I also tried Ubuntu 9.04 with same result. I also tried alternate CD for 10.10, I was able to install the OS successfully, once I log into to Ubuntu desktop, machine kept on hanging often so I un-installed it. I have also tried the USB disk option with 10.10 with same result. Recently I tried Fedora 10 (in an attempt to try some other Linux flavor) but it also hangs during installation.

---

### Post by WikiLeaks on 2010-12-20
> **kansasnoob said:**
> BTW, very bad choice for a username! I do a bit of political blogging and wikileaks is bad news right now!

Agreed, but you know there are three reasons. First I am from Pakistan, second my name is Waqar (Wiki goes to Waqar), third it is eye catching now a days ;). Three good reasons.

---

### Post by WikiLeaks on 2010-12-21
> **Rubi1200 said:**
> If Ubuntu is installed, you need to use the i915.modeset parameter at boot.

Press "e" to highlight the entry in GRUB then navigate with the cursor to the line that ends with quiet splash. 

Remove quiet splash and type  i915.modeset=1 followed by "Ctrl" + "x" to boot.

This also provides more information:
[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

Yeah, I read it somewhere earlier but I did not removed "quiet splash" while adding the i915.modeset at that time. Secondly it was recommended to try either i915.modeset=1 or i915.modeset=0. Can you please tell me what's the difference in both?.

---

### Post by nathatanu0 on 2012-01-10
[size="4"][color="black"]do just one thing, reboot the system, and when the violate screen just appear, that is before the appearance of dots, press "esc" and then the menu will appear, choos the options... Now everything will be fine [/color][/size]

---

