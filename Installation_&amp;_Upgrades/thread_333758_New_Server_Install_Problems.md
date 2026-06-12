---
title: "New Server Install Problems"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by smd333 on 2007-01-07
New to Ubuntu Server, downloaded server install and completed successfully with basic settings for DNS Server. When booting for first time, without CD in the machine, I did not receive expected text messages, initializations, and command line login prompt. Messages state: Grub Install, please wait... press esc for menu...

Once the timer for menu countsdown to zero, the machine reboots. This repeated several times before I figured this must be an error. [-(  Can anyone help? Is there something I'm missing or could be bad installation CD? I checked the CD Intergrity before install and all check out ok, which was not the case with first couple of downloads from different sites.

Appreciate the advice.

---

### Post by scrooge_74 on 2007-01-07
Open the menu for GRUB before the counter reaches 0 and use the safe boot option and see if you can boot the equipment

---

### Post by smd333 on 2007-01-07
Thanks for the reply scrooge_74. Well I tried what you suggested, however there is not a safe boot option. When system boots i see the following:

Grub Loading Stage 1.5.

Grub Loading, please wait...
Press esc for menu [3,2,1,0]...

if no menu selected, it continues the boot process with Starting Up... and reboots machine. I entered menu as instructed and found the following menu choices:

uBuntu, Kernel 2.6.17-10-Server
uBuntu, Kernel 2.6.17-10-Server [Recovery Mode]
memTest86+

I tried the first one, and received a grub prompt, but not the results I am expecting. I should have the login prompt for the server. :confused: There was no Safe Boot option that I saw. I did try the boot command from the GRUB prompt on the first option and it stated Starting Up... and rebooted. Machine specs below...

[Old Practice Machine] AMD K6-2 450Mhz, 256 RAM, 8Gb hd

---

### Post by scrooge_74 on 2007-01-07
I am sorry I still have some left over vocabulary from XP, you should use recovery mode, the normal boot is the first one you have listed in the GRUB menu

---

### Post by smd333 on 2007-01-08
Ok... I have tried to boot from Recovery Mode and achieved same results, immediate machine restart. I tried to use the CD and boot from it. With no success I reinstalled ubuntu DNS Server on the machine again. All went successful except on first reboot, same results. So I went into the GRUB menu and looked at both the server and recovery mode settings see below.

**uBuntu, Kernel 2.6.17-10-Server**
root(hd0,0)
kernel /boot/vmlinuz-2.6.17-10-server root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-server
quiet
savedefault
boot

**uBuntu, Kernel 2.6.17-10-Server [Recovery Mode]**
root(hd0,0)
kernel /boot/vmlinuz-2.6.17-10-server root=/dev/hda1 ro single
initrd /boot/initrd.img-2.6.17-10-server
boot

Not sure if I have compatability issues or missing some install/update. :-k

---

### Post by az on 2007-01-08
[QUOTE=smd333;1982802
Once the timer for menu countsdown to zero, the machine reboots. This repeated several times before I figured this must be an error..[/QUOTE]

The server kernel (unlike the desktop kernel) needs to run on a pII or better.  Some microprocessors are still only 386-type (VIA C3, for example).  The desktop kernel runs on a P1.  Boot the installer again, chroot into your installed system and install the dektop kernel:

sudo apt-get install linux-386 (for Dapper)
sudo apt-get install linux-generic (for Edgy)

You may want to install the linux-image-386 or linux-image-generic packages instead of the above, to avoid the kernel modules that you probably don't need (linux-restricted-modules).

---

### Post by smd333 on 2007-01-08
Thanks Azz! I also found the same info on: [Joel's Corner]("http://paradigma.pt/ja/slog/index.php/2006/08/ubuntu-server-606-lts-doesnt-boot-if-cpu-686.html")
Apparently, as you stated, the Ubuntu Server Kernel is for 686 and above, so elderly machines like my practice piece can't handle. I did as you and Joel suggested through the install cd's rescue mode and it worked perfectly using:

[B][COLOR="Blue"]apt-get install linux-386;
apt-get remove linux-server;[/COLOR][/B]

Thanks, again and I'd bet this advice would solve 95% of the new install posts because they tend to be on older machines. Just a guess. :mrgreen: 

Later

---

