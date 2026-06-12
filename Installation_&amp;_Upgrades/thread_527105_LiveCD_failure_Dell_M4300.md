---
title: "LiveCD failure Dell M4300"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by JonathanWright on 2007-08-16
When attempting to boot a ubuntu 7.04 LiveCD on a Dell Precision M4300 I end up at a prompt:

/bin/sh: can't access tty; job control turned off
(initramfs)

There is a file "casper.log" which says (amongst other things):

/init: /init: 1: cannot open /dev/sda: No such file
/init: /init: 1: cannot open /dev/sda1: No such file
/init: /init: 1: cannot open /dev/sda2: No such file
[then repeats many times:]
mount: Mounting /dev/sda2 on /cdrom failed: No such device
... then says:
Unable to find a medium containing a live file system

This seems strange as I thought I saw it saying things were OK for the harddisk in the stuff which flew by earlier on (said writable for a disk I think). Presumably the CD hard ware was good enough to generate the splash screen on the first attempt also.

I have tried adding options: "no apic no lapic acpi=noirq pci=noirq irqpoll", with quiet and splash removed. It seems to be stopping after saying:
"[  5.096000] usb 5-1.2: configuration #1 chosen from 1 choice"

It says the same thing if I only remove the quiet and splash.

I have tried adding "break-top" and then "modprobe piix", "exit" and the initramfs prompt. It stops saying:
cp: unable to open `/root/var/log': No such file or directory
...
Target filesystem doesn't have /sbin/init

I have used this same ubuntu 7.04 CD to successfully install on a Latitude D600 (so I think the CD is still OK). I can boot the Precision M4300 using a system rescue CD (sysresccd) in order to run GParted. It has:
/dev/sda1 fat16 94.10 MB, 86.16 MB Free
/dev/sda2 ntfs label="system" 30 GB, 20.22 GB free, flags="boot"
unallocated 81.70 GB

The latter space was for ubuntu + a windows/linux  shared partition. I intend to keep the windows partition intact. 

The device information says: Model ATA FUJITSU MHW2120B for the hard disk. In windows xp it seems to say the machine has 2GB ram, an intel core duo 2 cpu @ 2 GHz and that the DVD/CD-ROW drive is a TSSTcorp DVD+-RW TS-L632D. The display is an NVIDIA Quadro FX 360M.

Any tips would be appreciated. Thankyou!

---

### Post by okey666 on 2007-08-16
Do you have a SATA cd drive? I have a similar problem and I think it is because of that. I will let you know if I find a solution

---

### Post by JonathanWright on 2007-08-16
Yes, I think so...

In the XP device manager I have:
+ PCI Bus
  + Intel(R) ICH8M Ultra ATA Storage Controllers - 2850
    + Primary IDE Channel
       + TSSTcorp DVD+-RW TS-L632D

Thanks for your response!

---

### Post by okey666 on 2007-08-16
After waiting for about 45mins I ended up with the same message you got:
/bin/sh: can't access tty; job control turned off (initramfs)

Then the screen went black

Could we have the same problem?

---

### Post by JonathanWright on 2007-08-16
There is no long wait for me - about 30 seconds - using the defaults. 

I can get a frozen display if I add "break-top" to the end of the options (f6) without removing the splash and quiet. Then "modprobe piix" at the (initramfs) prompt followed by "./init". For about a minute it whirrs the CD drive. Then the wibbly orange bar gets corrupted, and it starts bleeping. Then the screen goes blank, wait a few more minutes and it starts bleeping again. After about 10 more minutes of silence I pressed the power button and booted back into windows. 

Do you get the blank screen and long wait if don't change any options? Is it still there if you remove the "quiet splash" from the options using f6? Normally there should be a load of text flying by...

---

### Post by okey666 on 2007-08-17
I have managed to fix my problem.....
I am writing this message from a fully installed Ubuntu!

It appears that for some reason Linux (or it could be a setting in my bios) can only boot from the first SATA drive. So I simply put my cd drive first and then my hard drive. After installing I switched them back again.

I don't know if you can do it, but the advice I got that solved it was to unplug my hard drive altogether and just run it live CD.

See if that fixes it.

---

### Post by JonathanWright on 2007-08-20
The CD drive is first in the boot sequence. I have not quite understood about unplugging the hard drive. If you remove it, how do you install on it? Do you have to remove it to get the CD drive to be "first" in a sequence?

Thanks for any tips

---

### Post by okey666 on 2007-08-24
> **JonathanWright said:**
> The CD drive is first in the boot sequence. I have not quite understood about unplugging the hard drive. If you remove it, how do you install on it? Do you have to remove it to get the CD drive to be "first" in a sequence?

Thanks for any tips
I unplugged the hard drive, then when it worked I shut down the PC plugged the hard drive in the second SATA plug, and it just worked! After I did that I somehow managed to corrupt the system, so when I reinstalled it I used an external USB drive which worked fine as well? I think my system is weired though because no other distro will boot!

---

### Post by JonathanWright on 2007-08-30
Seems the 6.06 and 7.10 both boot up and then both get into trouble with the NVIDIA Quadro FX 360M card. Works if I put "vesa" into xorg.conf... continuing to get the nvidia driver there with gutsy. 

Thanks for the help

---

