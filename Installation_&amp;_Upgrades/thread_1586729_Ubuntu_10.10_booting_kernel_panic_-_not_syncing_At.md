---
title: "Ubuntu 10.10 booting kernel panic - not syncing: Attempted to kill init"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by krstep on 2010-10-02
Here's a picture of the error.
[IMG]http://i.imgur.com/EQ74V.jpg[/IMG]
Fresh burned ISO of 10.10 beta, I have the same problem on 10.04 either [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG].

---

### Post by krstep on 2010-10-10
Bump, anyone ?!

---

### Post by gradinaruvasile on 2010-10-10
Ummm.. First the picture is blurred, second the message is too common to be of any help. What really helps is posting:
1. Hardware specs (computer/mobo make and model), if any proprietary drivers are installed (ati/nvidia etc) - if yes, how were they installed (Hardware drivers, scripts from vendor site etc); Any exotic device attached (external hdd/webcam/ etc)
- if any upgrade was performed, any new kernels installed;
- is it a 32 bit or 64 bit distro;
- the results of a memtest full test (found on the live cd)
2. When does this happens - live cd, after install/upgrade etc.
3. What is before this message (or at least a clear picture of the whole screen - the interesting part is above the very technical short lines).

---

### Post by mariusbm on 2010-10-10
I think I may have the same problem. It happens after a new install of 10.10 desktop amd64 on a HP Probook 4320s. It hangs the system after a while, before X starts.

---

### Post by gradinaruvasile on 2010-10-10
What CPU and video card?

BTW have you tried the 32-bit version?

---

### Post by mariusbm on 2010-10-10
Now I can not reproduce the same error. I just got it the first boot after the install. Now the machine boots, but with no X, then hangs when X is starting.

Intregrated VGA (Intel HD Graphics Dynamic Video Memory Technology 5.0) and celeron 4500.

I don`t think I got the same error as krstep.

---

### Post by gradinaruvasile on 2010-10-10
Log in text mode (press ctrl-alt-f1) and type:
cat /var/log/Xorg.0.log

What does it say in the last lines?

---

### Post by mariusbm on 2010-10-10
The computer hangs so CTRL+ALT Fx do not work, but I got in using safe mode option. I tried to repair the X conf but it fails when I try to use the option for making a new config. It just loops, asking same question over and over. I am using the computer now, with VESA driver in safe mode...



Full log: [http://pastebin.com/MhvJf7jz](http://pastebin.com/MhvJf7jz)

Last couple of lines:

[   973.542] (II) UnloadModule: "intel"
[   973.542] (EE) Screen(s) found, but none have a usable configuration.
[   973.542] 
Fatal server error:
[   973.542] no screens found
[   973.542] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[   973.542] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   973.542] 
[   973.549]  ddxSigGiveUp: Closing log

---

### Post by dino99 on 2010-10-10
remove xorg.conf, now its drived by kernel

sudo rm -f /etc/X11/xorg.conf

then reboot and check driver activation: system admin additional driver

your package is xserver-xorg-video-intel, and might be activated

---

### Post by mariusbm on 2010-10-10
I only got a xorg.conf.failsafe file, no regular xorg.conf.
The driver admin tool shows only Broadcom STA, as installed and in use.

apt-get install xserver-xorg-video-intel show package as installed.
WLAN is acting up alot, disconnect every couple of minutes. Might be more problems after install then just the VGA problem I guess...

---

### Post by gradinaruvasile on 2010-10-10
Here is a bug report that looks like your issues:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605667](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605667)

PS. I never upgraded Ubuntu until 1-2 months have passed after a release (now i use Debian BTW).

---

### Post by krstep on 2010-10-16
So the problem is a bug?

I can't get any command line, it's booting from live CD when I get that error.
The compupter has Windows 7 installed on it, so I wanted to try Ubuntu.
If you need more info on the PC's specs ask me and I will provide them.
Hope I can solve this somehow.

BTW, the error is not just in 10.04. The same error appears when I try to boot 9.04 and 7.10.

---

### Post by unuu on 2010-10-20
I am having the same problem. I am also running dual booting system along side with Windows 7 and I can not boot using any of the other kernels. :(

---

### Post by jreher on 2010-10-23
I upgraded via internet from 10.04, upgrade went fine. succesfully got to reboot your system to complete the upgrade.

It hasn't booted ubuntu since. kernal panic, complaining about some hardware failure.

It runs windows xp just as fine as it ever did.

I burned a copy of the 10.10 live cd. It won't boot either, it does display the new boot screen with dots changing color, but that's all it does.

Trying 64 bit version now, as it's an amd64 bit cpu.

here's my system info. It's a compaq presario R3000Z circa 2004.

Motherboard:
      CPU Type                                          Mobile AMD Athlon 64, 1800 MHz (9 x 200) 3000+
      Motherboard Name                                  Compal 08A0
      Motherboard Chipset                               nVIDIA nForce3 150, AMD Hammer
      System Memory                                     1280 MB  (DDR SDRAM)
      BIOS Type                                         Phoenix (04/28/05)
      Communication Port                                Bluetooth Communications Port (COM10)
      Communication Port                                Bluetooth Communications Port (COM9)
      Communication Port                                ECP Printer Port (LPT1)

    Display:
      Video Adapter                                     NVIDIA GeForce4 440 Go 64M  (64 MB)
      Video Adapter                                     NVIDIA GeForce4 440 Go 64M  (64 MB)
      3D Accelerator                                    nVIDIA GeForce4 440 Go 64M
      Monitor                                           Plug and Play Monitor [NoDB]  (14431040127337)

    Multimedia:
      Audio Adapter                                     nVIDIA MCP2 - Audio Codec Interface

    Storage:
      IDE Controller                                    NVIDIA nForce3 Parallel ATA Controller
      Disk Drive                                        WDC WD2500BEVE-00WZT0  (232 GB, IDE) 
      Optical Drive                                     HL-DT-ST RW/DVD GCC-4243N  (DVD:8x, CD:24x/24x/24x DVD-ROM/CD-RW)
      SMART Hard Disks Status                           OK

---

### Post by oneindelijk on 2011-01-10
I seem to have a similar problem, at least partly.
It looks as if the problem isn't due to hardware since I can boot another partition which has also 10.10.

My situation:
Upgrade from 9.10 to 10.04 ==> Mostly fine, just some networking problems, which mostly solve by enabling networking through nm-applet or with ```
ifconfig eth0 up & dhclient eth0
``` 

Upgrade from 10.04 to 10.10 ==> kernel panic, something with root not synching. I tried ```
set root=(hd0,gpt4)
linux /vmlinuz initrd=/initrd.gz root=/dev/sda4
boot

```This results in a different error (can't recall it, I might post it later)

*I know upgrades are not recommended, but it might reveal a different angle of tackling the problem and I was just being lazy*

However, I can still boot my system using the older kernel from the grub menu, but now I have a problem with my wireless adapter (bcm4311 chipset) not showing up anymore (although visible in System Profiler)

I have another partition on which I put a clean amd64 version of 10.10 and this one boots fine (although it also suffers from the wireless problem since kernel 2.6.35.24 (.22 and .23) were okay...

---

### Post by oneindelijk on 2011-01-10
I tried again, this time executing the grub commands as I found them after grub-mkconfig
```
set root=(hd0,gpt4)
linux /boot/vmlinuz-2.6.35-24-generic
initrd /boot/initrd.img-2.6.32-27-generic
boot
```
By doing that I noticed there wasn't an initrd.img with the same version as the kernel, so using these parameters I ended up in a busybox, which is a alien environment for me and it wasn't all that unexpected anyway.

So I checked the grub.cfg and saw there wasn't even an entry for the initrd in the section 'Ubuntu, with Linux 2.6.35-24-generic' ?
I compared the grub.cfg from the freshly installed copy which does mention the correct initrd entry, but the file itself is missing, while initrd.img-2.6.35-23-generic and initrd.img-2.6.35-22-generic are present.

It seems like the update went awry somehow ;-)

---

