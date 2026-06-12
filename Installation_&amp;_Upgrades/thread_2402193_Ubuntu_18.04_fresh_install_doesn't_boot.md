---
title: "Ubuntu 18.04 fresh install doesn't boot"
date: 2018-09-27
forum: Installation &amp; Upgrades
---

### Post by cristobaltirado on 2018-09-27
Hi everyone, I'm fairly new to Ubuntu. I used to use it several years ago, but my current laptop is not actually mine, but my company's, and it came with windows. I have persuaded my manager to install Ubuntu, and he has agreed, but I think I might have messed up with "his" laptop...
I have downloaded Ubuntu 18.04, booted in USB mode and performed a clean installation. I chose the option "erase my disk", because my laptop only has a 30GB eMMc hard drive and that didn't give me enough space for a dual boot or similar. There was a message saying the installation would create an EPS partition and a ext4 partition with the 30 GB of rom assigned. Then there was a message saying I needed to unmount a drive in order to proceed.
 
Then the installation seemed fine but I can't boot, my laptop can't pass the initial manufacturer screen (Acer, in this case), it stays there for two seconds and then there is a couple of lines on top of the screen that disappear so fast that I can't even read them. 
I have reinstalled twice, but the problem persists. I have even tried to install the Ubuntu based distro Linux Mint 19, but I have exactly the same situation. So I don't have a OS, because I deleted Windows (and I don't want it back, to be honest) in order to install Ubuntu.

I would really appreciate if I could fix it myself, I don't want to face the situation of telling him we need a technician because I broke his laptop... you know...

Any advice, please?

---

### Post by westie457 on 2018-09-27
Which version of Windows did the machine come with?

When you booted the USB did you get a four line menu or a graphical interface?

Did you change any settings in BIOS/UEFI settings pages before trying the installation?

The fix is dependent on your answers to the questions.

---

### Post by cristobaltirado on 2018-09-27
Hey, first of all, thank you so much for answering, I really appreciate it. As for your questions, these are the answers:

The machine came with windows 10.

To boot the usb stick, the laptop showed a four line menu, not a graphical interface.

In the Bios I only changed the device boot order when I first tried the installation, set it to usb first, then eMMc second. I have, however, reversed it and now my eMMc is first in the list. If I plug the usb stick, it boots the live version of Ubuntu. Without the stick, there's the bootloop...

Thanks one more time for your help!

---

### Post by westie457 on 2018-09-27
Some Acer machines need a BIOS update, check the Acer website for your machine to compare versions.

Only update the BIOS if the following does not work.

All Acer machines need 'Trust' set on a boot file or 'Secure Boot' disabled. A (relatively) simple matter of setting a supervisor password in the BIOS security page and setting secure boot to 'off'. 
To set trust once the password has been set.
In the security page the 'Trust' option is now active, select this and press Enter for each of the highlighted options. When completed Save the Changes and reboot.

ps Secure Boot is disabled to allow installation of 'unsigned' kernel-drivers in the future.

---

### Post by cristobaltirado on 2018-09-27
Ok, I'll try that in a couple of hours when I get to the office and will report back. Thanks a million!

---

### Post by cristobaltirado on 2018-09-27
Hey, I've tried the BIOS options you gave me before. 
I can disable the secure boot. I can also set administrator password in the security tab, but I cannot access the "trust" options. And the problem persists...sadly.

What else can I do? What do I need to do to be able to edit the "trust" options? Shall I change any of the other options?

---

### Post by cristobaltirado on 2018-09-27
> **westie457 said:**
> Some Acer machines need a BIOS update, check the Acer website for your machine to compare versions.

Only update the BIOS if the following does not work.

All Acer machines need 'Trust' set on a boot file or 'Secure Boot' disabled. A (relatively) simple matter of setting a supervisor password in the BIOS security page and setting secure boot to 'off'. 
To set trust once the password has been set.
In the security page the 'Trust' option is now active, select this and press Enter for each of the highlighted options. When completed Save the Changes and reboot.

ps Secure Boot is disabled to allow installation of 'unsigned' kernel-drivers in the future.

Hey, I've tried the BIOS options you gave me before. 
I can disable the secure boot. I can also set administrator password in  the security tab, but I cannot access the "trust" options. And the  problem persists...sadly.

What else can I do? What do I need to do to be able to edit the "trust" options? Shall I change any of the other options?

PS Sorry for repeting the message, but I just realized that I did not quote your answer. I am in no way trying to put pressure on you, more on the contrary, I am so thankful for your help.

---

### Post by cristobaltirado on 2018-09-27
PROBLEM SOLVED.

I followed this tutorial: [https://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](https://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

It's for dual boot, but if you ignore the dual boot things and just follow the steps, it solves the problem just nicely.

Thanks!

---

