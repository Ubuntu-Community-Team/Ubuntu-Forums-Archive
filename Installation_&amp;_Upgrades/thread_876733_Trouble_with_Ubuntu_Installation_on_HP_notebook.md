---
title: "Trouble with Ubuntu Installation on HP notebook"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by jp2485 on 2008-08-01
Hello.
I received my laptop earlier today, and after fiddling with Vista and a couple thousand "useful" programs provided by HP, I decided to install Ubuntu.
I'm currently having problems with the Ubuntu installation.
The Ubuntu 8.04 LTS Desktop Edition continued to bring me to a command prompt stating that an error had occurred before the installation started; I decided to download and use the alternate-CD.
I'm further along now but, the GRUB installation continues to fail along with LILO.
I was wondering if anyone could help me with my situation.

HP Pavilion dv5z series
S/N: KS878AV
(Be happy to provide further details if needed.)

Did I mention that I'm relatively new to the whole GNU/Linux thingy?  Expect a lot of questions. >_>

Thanks in advance.

---

### Post by luken8r on 2008-08-02
Were you able to get any furhter with this?  Im in the same boat; Vista blows and HP doesnt offer drivers for XP for the DV5Z

---

### Post by LoungeAct on 2008-08-03
Just wanted to post that I had the exact same problem trying to install Hardy.  Hope someone figures out a fix soon...

---

### Post by LoungeAct on 2008-08-05
I was able to install 64-bit (amd64) Hardy on my machine.  I haven't had time to tinker with it too much yet but the wireless card doesn't work off the bat.  

If anyone is interested I can post more info on my experience as I get more time to play around.

---

### Post by highlandsun on 2008-08-22
I just installed 8.04LTS on my new dv5z a couple days ago. No problems doing the install, but there are a couple of problems...

I have the a/b/g/n wifi card, which is not supported out of the box. Windows identifies it as an AR5009. In fact, going on the PCI ID (0x002a) it matches up with AR9280 which is supported by the new ath9k driver. It's a bit of a chore to get that to compile on a released kernel because the ath9k driver is only in the 2.6.27 testing trees right now. (I got it working fine now, hacking it into the compat_wireless tree.)

The ACPI/DSDT on this laptop checks the operating system that's running, and disables certain features if it's not "Windows 6 SP1". One result of this is that the ACPI thermal_zone driver fails to initialize, because two of the entry points return without passing back a result (which violates the ACPI spec). Since I like being able to see what temperature my CPU is running at, I patched my DSDT to fix these bugs as well.

I also got the 56k modem, because I'll be traveling to a few places where wifi/high speed networking aren't available. Unfortunately it's an Agere softmodem. There is a Linux driver for it but only for 32 bit, because it uses a proprietary blob. So, until someone manages to hack together a 64 bit wrapper for that blob, I can't use it. I have to either switch to 32 bit Linux, or back to Vista. (gag...)

The notebook does not resume from standby, it just hangs. It can hibernate and resume successfully but the color palette is not restored correctly, so colors on high-depth images and videos are wrong. (The colors of desktop widgets and such still seem ok.)

This thing definitely runs hot, at least 15C warmer than my 4 year old Pentium-M laptop. I'll be looking into undervolting it to see if I can cool it down and extend the battery life a bit more.

---

### Post by Terralthra on 2008-08-26
Can you provide a how-to on hacking ath9k into the compat-wireless tree? I need the same thing on my tablet.

---

### Post by highlandsun on 2008-08-28
Actually, it looks like someone has already done the work for the ath9k driver.

If you read here
[http://ubuntuforums.org/showthread.php?t=883731](http://ubuntuforums.org/showthread.php?t=883731)

and follow to here
[http://ubuntuforums.org/showpost.php?p=5545069&postcount=5](http://ubuntuforums.org/showpost.php?p=5545069&postcount=5)

there's a shell script you can download that contains the complete source tarball, just run it and it will build the driver and package it for you.

Otherwise, you can start by getting the compat-wireless stuff from here
[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

Then apply the patch I posted here
[http://marc.info/?l=linux-wireless&m=121990907531656&w=2](http://marc.info/?l=linux-wireless&m=121990907531656&w=2)

You'll also need to copy the ath9k source from the wireless-testing tree, which you can get by following the directions here
[http://linuxwireless.org/en/developers/Documentation/git-guide](http://linuxwireless.org/en/developers/Documentation/git-guide)

After you copy the drivers/net/wireless/ath9k directory from the wireless-testing tree into the compat-wireless tree, and apply my patch to the compat-wireless tree, you should be able to just type "make" and all the drivers will be compiled.
Read the rest of the compat-wireless README from there...

---

