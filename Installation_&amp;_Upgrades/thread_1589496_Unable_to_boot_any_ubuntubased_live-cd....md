---
title: "Unable to boot any ubuntubased live-cd..."
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by p10 on 2010-10-06
Returning from my vacation, I tried to boot my Mint8 KDE today. After the usual bios-screen, instead of Mint booting up, I ended up with a marker blinking in the top left of the screen... Several reboots later I opted for a live-cd to get access to my documents. It started up OK, but after the grub-screen the message "crc error --- system halted" showed up on the screen. I also tried booting from an USB-stick, but it would just go into an endless loop of rebooting right after the grub-screen.

The funny thing is, I am unable to boot into any Linux Mint or Ubuntu live-cd. Even older ones that I know works. Have also tested all the live-cds on other PC and they do work there.

However, I was able to boot into, and install, Mandriva without any problem!

Anyone got a clue to why this is happening??

---

### Post by Rubi1200 on 2010-10-06
There are a number of possible causes; drive failing, faulty RAM, kernel inconsistencies etc.
[http://en.wikipedia.org/wiki/Cyclic_redundancy_check](http://en.wikipedia.org/wiki/Cyclic_redundancy_check)

Are you able to enter Recovery Mode?

If Ubuntu is the only OS, hold down Shift as you boot and try to bring up the GRUB menu.

You should be able to use a LiveCD; maybe try Knoppix and see if that works to boot the computer and rescue your data.

---

### Post by p10 on 2010-10-06
> **Rubi1200 said:**
> There are a number of possible causes; drive failing, faulty RAM, kernel inconsistencies etc.
[http://en.wikipedia.org/wiki/Cyclic_redundancy_check](http://en.wikipedia.org/wiki/Cyclic_redundancy_check)

Are you able to enter Recovery Mode?

If Ubuntu is the only OS, hold down Shift as you boot and try to bring up the GRUB menu.

You should be able to use a LiveCD; maybe try Knoppix and see if that works to boot the computer and rescue your data.

I am unable get recoverymode to work. Have tried launching the live-cds in compatibility mode, but that did not help. I have installed Mandriva One 2010.1, but I want to get back to Ubuntu and Linux Mint. However, as I wrote in the first post. Non of the live-cds containing Ubuntu or Ubuntu-based systems work!

---

### Post by Rubi1200 on 2010-10-06
Did the Mandriva install overwrite whatever was previously there?

What file-system were you using for Mint and Ubuntu; the default Ext4 or something else?

---

### Post by p10 on 2010-10-06
> **Rubi1200 said:**
> Did the Mandriva install overwrite whatever was previously there?

What file-system were you using for Mint and Ubuntu; the default Ext4 or something else?

The Mandriva install overwrote my "/"partition, but as I have a separat "home"-partition, my documents survived. The "/"-partition was, and still is, ext4. "Home"-partition is ext3 since it's been around since before ext4 was default!

---

### Post by Rubi1200 on 2010-10-06
I don't know what to tell you. My understanding of the crc error is that it may indicate a failing drive or errors with the kernel such as a mismatch in values.

However, if you can install and run Mandriva then things may be alright.

I would still consider running some checks to see if the drive is healthy. I don't know what tools come with Mandriva, but, as you know, in Ubuntu there is the Disk Utility.

Anyway, good luck :)

---

### Post by p10 on 2010-10-06
> **Rubi1200 said:**
> I don't know what to tell you. My understanding of the crc error is that it may indicate a failing drive or errors with the kernel such as a mismatch in values.

However, if you can install and run Mandriva then things may be alright.

I would still consider running some checks to see if the drive is healthy. I don't know what tools come with Mandriva, but, as you know, in Ubuntu there is the Disk Utility.

Anyway, good luck :)

Thanks! I am researching and testing as we speak! Just found that Crunchbang based on Ubuntu 9.04 will run as a live-system, but Ubuntu 9.04 will not!

---

### Post by p10 on 2010-10-08
This problem is puzzeling. I can install openSUSE, Mandriva, and Crunshbang, but not Ubuntu or Linux Mint. The live-cd's or usb-sticks won't even boot, but they work fine on other systems. 

I am thinking about removing the hd from my laptop and hooking it up to my desktop. First of all to backup all my workdocuments and emails. Might try to install Ubuntu or Mint while I got it hooked up this way.

---

### Post by Rubi1200 on 2010-10-08
> **p10 said:**
> This problem is puzzeling. I can install openSUSE, Mandriva, and Crunshbang, but not Ubuntu or Linux Mint. The live-cd's or usb-sticks won't even boot, but they work fine on other systems. 

I am thinking about removing the hd from my laptop and hooking it up to my desktop. First of all to backup all my workdocuments and emails. Might try to install Ubuntu or Mint while I got it hooked up this way.
Very interesting and very odd at the same time!

I have not found any additional information for you yet about this, but it seems your idea may be worth pursuing.

Good luck!

---

### Post by p10 on 2010-10-08
But if I install to the hd while it is hooked up to my desktop, wouldn't that result in a system made for the hardware in my desktop, and not my laptop?

---

### Post by p10 on 2010-10-08
This problem just keeps getting stranger and stranger. I was able to install Linux Mint 7 x64, although the standard Mint 7 would not work. I am now trying to upgrade to Mint 9 via Mint 8 (arms, legs and fingers crossed). 

Could the fact that it is a x64 version have something to do with it?

---

