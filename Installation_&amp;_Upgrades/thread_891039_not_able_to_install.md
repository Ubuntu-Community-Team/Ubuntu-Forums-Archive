---
title: "not able to install"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by archie766 on 2008-08-15
I have burnt cds at the slowest speed, Downloaded the iso of ubuntu and Xubuntu and made sure they werent corrupt. But when i tell it to install it shows the Logo and the load bar and the orange bar moves back and forth then stops. I tried the Alternate cd and after i tell it to install it shows 
[    0.000000]ACPI: BIOS age (1999) fails cutoff (2000), acpi= force is required to enable ACPI.

thanks in advance for any help or tips

---

### Post by spiderbatdad on 2008-08-15
so from the startup screen, you press f6 other options. ESC if necessary to get rid of a dialog of options. Then delete the end of the kernel line: quiet splash --, and replace with acpi=force then hit enter.

If the fails, try lapic  or try noapic

---

### Post by archie766 on 2008-08-15
ok tried those and it started running thru, but stop and showed

[sda] Write cache: enabled, read cache: enabled, does n't support DPO or FUA
sda:<4> Driver 'sr needs updating - please use bus_type methods

---

### Post by spiderbatdad on 2008-08-15
thats a common kernel message, and should stop the boot process...for too long...perhaps some other boot options would be more effective:
apic=force nolapic

Not sure, sorry.
maybe:
apic=on apm=on

---

### Post by archie766 on 2008-08-15
well thank for your help, could it be a driver or something? it is an older computer, its a dell dimension xps t450 pentium 3 450 mhz with 576 ram

---

### Post by spiderbatdad on 2008-08-15
It appears a lot of folks have installed Ubuntu on this model, with no troubles. Sorry you are having this problem. You might try 7.10 or 8.10 alpha3.
Keep searching google for possible bios settings for the cpu?

---

### Post by archie766 on 2008-08-15
ok ill try a later version, ill give you the results afterwards, thanks again

---

### Post by archie766 on 2008-08-16
ok it seems to working but then stops and shows 

/bin/sh:can't access tty; job control turned off
(initramfs)

---

### Post by spiderbatdad on 2008-08-19
that looks like grub might be pointing to uuid instead of a partition. Can you boot the live cd and mount your file system manually to edit menu.lst?

Also google your error:/bin/sh:can't access tty; job control turned off
(initramfs)

---

### Post by Pumalite on 2008-08-19
Here are some other boot parameters you might want to try:
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off all_generic_ide vga=0x317
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html) 
To be tried alone or in different combinations.
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)

---

### Post by malayamithun on 2008-09-05
[COLOR="Blue"]I am also getting the same error.Exactly what I can see in the screen is given below[/COLOR]
[B]-----------------------------------------------------------------------
BusyBox v1.1.3(Debian 1:1.1.3-3ubuntu3) Built-in shell(ash))
Can't access tty; job control turned off
(initramfs)
-----------------------------------------------------------------------[/B]
[COLOR="Blue"]I am very new to ubuntu.My system configuration is as follows:
250 GB HDD
1 GB RAM
No Floppy Drive
Wndows XP is installed.

Help required badly.I f anybody have a solution,please let me know.[/COLOR]

---

### Post by ZALinuxDude on 2008-09-05
Hi guys I was hoping you could help me with my Install problems...

trying to install the latest version of Ubuntu LTS (8.04) onto an HP Compaq nx 9010 via a downloaded iso of the distro, the cd bootsup I select install ubuntu I get the progress bar that slides back and forth then get another progress bar that shows the progress from left to right when it reaches the end I get a full screen picture of a heron for a while then everything goes black every 10 minutes or so it alternates between the heron picture and a black screen I've tried this a few times untill 30 minutes into the install and then restart It doesn't seem to be doing anything other then alternate between black screen and heron picture is this normal or is there a problem because if there isn't a problem then i'de like to know how long the install is supposed to take or if i should try an older version of Ubuntu, due to compatability problems, bnyt the way my HP specs are...

P4 2.8Ghz
40 Gb HDD
256mb  Ram

thanks for any help you can give, my knowledge of Linux is beginner level

---

### Post by Pumalite on 2008-09-05
256 MB of RAM>Xubuntu Alternate CD:
[http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/](http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/)

---

### Post by ZALinuxDude on 2008-09-05
Thanks i'll give it a try i'll wait till i'm at work again and have access to T1 to download the iso i'll let you know how it went

---

### Post by ZALinuxDude on 2008-09-06
Hi I took your advice and tried the Xubuntu that you suggested and it works great thanks for the help

---

