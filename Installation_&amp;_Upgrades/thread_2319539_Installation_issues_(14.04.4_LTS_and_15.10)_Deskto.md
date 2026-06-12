---
title: "Installation issues (14.04.4 LTS and 15.10) Desktop 64bit"
date: 2016-04-05
forum: Installation &amp; Upgrades
---

### Post by stefan41 on 2016-04-05
Hi,
I've stucked on strange issue with installation from USB stick.
When it gets to:
[COLOR=#6A6A6A][FONT=arial]**evm**[/FONT][/COLOR][COLOR=#545454][FONT=arial]: [/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**HMAC attrs**[/FONT][/COLOR][COLOR=#545454][FONT=arial]: [/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**0x1**[/FONT][/COLOR][COLOR=#545454][FONT=arial] 
[/FONT][/COLOR][FONT=arial][FONT=arial]it get stuck. There is only blinking cursor and no further action. I used the same stick on different pc and everythnig went well.
[/FONT][COLOR=#000000]
I've already tried different configuration (i.e. nomodset) and different apps from bootable usb stick ([/COLOR][/FONT][COLOR=#000000]LiveUSB Install, YUMI, Universal USB Installer), and two versions of OS.
Same situtaion for all cases. Any gueses?[/COLOR]

---

### Post by grahammechanical on 2016-04-05
HMAC = Hash Message Authentication Code

[https://en.wikipedia.org/wiki/Hash-based_message_authentication_code](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code)

greymech guess = corrupted burn of the ISO image to the USB stick.

Regards

---

### Post by RobGoss on 2016-04-05
Are you having trouble with both distributions if so I would have to say it must be that USB drive causing the issues you might want to use a different one. When I sometimes try installing Ubuntu I run into problems installing on my older machines but I don't give up and it finally installs.

---

### Post by stefan41 on 2016-04-05
Yeap, issue is same on both distributions. I's also consider USB stick if on the other PC it wouldn't work, but it does. I'll try to burn CD or net install when I'll get home.

---

### Post by RobGoss on 2016-04-05
Yes what works on some won't work on others but at the end im successful with my installation 99% of the time. That's what mates Ubuntu so enjoyable.

Is this a new machines or an older one. I ask because I don't see specs posted.

---

### Post by stefan41 on 2016-04-11
I'm really dozed and confused. Got same issue on Ubuntu 14 and 15 and Mint using USB and CD. Changing boot options is not helping. ISO file is not corrupted.

[IMG]http://i.imgur.com/PqsuarZ.jpg[/IMG]


Here's how it looks like. It suppose to print magic number here but it does not. Same USB was used to install OS on other laptop and there where no problems.
I assume that it's some hardware issue. But HDD is fine (checked) memory is fine (checked). Rest is working properly on Win7.
Any suggestions?

---

### Post by kansasnoob on 2016-04-11
The No TPM chip found message makes me think your BIOS' APIC (Advanced Programmable Interrupt Controller) is acting flaky so I'd try either the **noapic** or **nolapic** boot parameters and see what happens. I've found the latter of the two to be quite helpful with some dual/multi-core processors. Then if that works to get things installed you can dink around in BIOS and try to find a real solution.

---

### Post by hectorortiz on 2016-07-27
Hi, I also have the same problem as stefan, I also tried different configuration, usb sticks, live cds, bootable usb stick apps and the noapic boot parameters and I still have the same issue, I've also try different versions of OS, 16.04 x64, x86, 15, ubuntu mate, linuxmint... And the same result. Does any one have an idea of this issue?

I'm trying to install ubuntu in a ASUS F50xs, 4Gb RAM, SSD 128GB, core 2 duo@2.4Ghz

Thanks

---

### Post by Pierre1976 on 2016-11-01
It happened twice to me with notebooks, and the fix was always found within the BIOS: try disabling everything that you can in the BIOS, even Wireless or Ethernet, whatever.

Then install Ubuntu: surprisingly enough, the installation process will proceed without issue.

Then enable stuff in the BIOS again, one by one, and see that everything works.

I know it lacks precision and elegance but the fact is that it always worked for me.

---

### Post by mastablasta on 2016-11-02
hardware? BIOS or UEFI?  
[SIZE=2]have a look: [https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)
[/SIZE]

---

