---
title: "eeepc 1101HA cannot boot from Ubuntu USB stick; Puppy does boot"
date: 2015-02-27
forum: Installation &amp; Upgrades
---

### Post by Huib123 on 2015-02-27
I have tried in vain to boot eeepc 1101HA with Ubuntu live USB stick (12.04 and 14.04), same with Xubuntu 14.04; these sticks worked fine on Acer netbook and also used another brand of USB stick without results. Using the same USB stick with Puppy Linux works fine.
With the Ubuntu family the proces shows the (X)Ubuntu logo and freezes after about two minutes. I have tried fail safe mode (F4) with all possible options, no success. With the verbose mode (F8) an overwhelming amount of info passes without showing any fatal errors.
I welcome any suggestions.

---

### Post by roger_1960 on 2015-02-27
Hi

Not sure if its the same for your model, but have you disabled "Boot Booster" in the BIOS boot settings. I seem to recall I had to do this.

---

### Post by Huib123 on 2015-03-01
Thanks, but strangely the option "Boot Booster" in the BIOS menu has disappeared since I updated BIOS to version 323

---

### Post by mörgæs on 2015-03-01
Please post all hardware details.

---

### Post by Huib123 on 2015-03-01
Thank you for your willingness to help; please find below a dump from Puppy

```
-Computer-
Processor        : 2x Intel(R) Atom(TM) CPU Z520   @ 1.33GHz
Memory        : 1017MB (277MB used)
Machine Type        : Physical machine
Operating System        : tahrpup - 6.0.2
User Name        : root (root)
Date/Time        : Sun 01 Mar 2015 04:25:27 PM CET
-Display-
Resolution        : 1366x768 pixels
OpenGL Renderer        : Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
X11 Vendor        : The X.Org Foundation
-Audio Devices-
Audio Adapter        : HDA-Intel - HDA Intel MID
Audio Adapter        : PC-Speaker - pcsp
-Input Devices-
 Lid Switch
 Sleep Button
 Power Button
 AT Translated Set 2 keyboard
 USB Optical Mouse
 Video Bus
 USB2.0 UVC 1.3M WebCam
 SynPS/2 Synaptics TouchPad
 PC Speaker
-Printers (CUPS)-
CUPS-PDF        : <i>Default</i>
-SCSI Disks-
ATA Hitachi HTS54321
```

---

### Post by mörgæs on 2015-03-01
The most important part, the graphics processor, is missing from the output.
Anyway, have you tried the [alternate Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")?

---

### Post by mattharris4 on 2015-03-01
^ According to this link  [http://www.notebookcheck.net/Review-Asus-Eee-PC-1101HA-Netbook.20041.0.html](http://www.notebookcheck.net/Review-Asus-Eee-PC-1101HA-Netbook.20041.0.html) this computer came with a GMA 500 integrated graphics and an Atom Z520 CPU.  I doubt with the design of these little netbooks that the graphics adapter has been replaced or augmented with an additional graphics adapter.

This computer only runs 1GB of RAM so along with the cheap low-powered CPU I would suggest trying Lubuntu if you wish to use a Canonical OS.  From what I have read these Atom CPUs are mainly meant for tablets and probably cannot run the heavier Canonical OSes.  If I understand correctly the live CD/USB uses more CPU power than an install but I still think you would have trouble if it did install and you attempted to use the heavier OSes.  Puppy Linux is a very light OS that will run on just about anything made in the past 15 years (at least boot up, anyway) so I am not surprised that it will run on this.  Frankly from my trial of Xubuntu I don't think you would be happy with it on this computer even if it did install, to actually do anything online it used a minimum of .8-1.0GB of RAM and spiked as high as 1.3GB at times.  Just with the OS running without any other program up it used 0.7-0.8GB of RAM.  You can forget Ubuntu on this machine, it runs as high as 2.5GB of RAM and routinely will chew up 1.4-1.5GB with even light use (as I type I am running four tabs of this forum, one tab from Notebook Check and my system monitor and am using 1.4GB of RAM on Edubuntu, these are lighter sites that don't use a ton of RAM in the first place).  If you are depending on swap space on your HD to allow you to use Ubuntu or Xubuntu don't, in my experience with Ubuntu/Edubuntu once a computer goes into swap it slows down to a crawl.  However, if you get this computer working and the battery isn't bad you should have great battery life with that 2 watt CPU, my new Toshiba 15.6" laptop's AMD E1-2100 CPU uses 9 watts (and was designed with power conservation in mind) and my mother's Emachines 15.4" laptop's CPU made in 2010 uses a whopping 35 watts (and has a weak Celeron 900 2.2GHz processor that maxes out easily in Win 7, boy would it run better with Lubuntu but she will probably never let that happen)!

Good luck and please let us know how this turns out for you.

---

### Post by Huib123 on 2015-03-02
Thanks for suggesting Lubuntu, I tried 14.04 without success. As you mentioned that playing live from stick may involve more processor power, I tried installing straightaway (F4, installing) also no success. The ubuntu logo freezes within 2 minutes, full stop.
I am surprised that the Ubuntu's take so much RAM and processor power; I am running a few years now Ubuntu 12.04 on my Acer One (1 gb, atom N270) no swapdisk and 8 gb SSD). All I have to do is removing old kernels and I still have 2 gb on my SSD.
From several bulletins I get the impression that others have succeeded in installing recent Ubuntu versions on eee pc 1101HA so I distrust the hardware but then how can Puppy run smoothly?

---

### Post by yozgoesdigital on 2015-03-02
Hi Huib,
As the previous owner of this machine, I can acknowledge the hardware is still original and indeed has the GMA500. In the past I got it to work with Lubuntu 12.04  (I think) using the alternate cd. I do not remember how I did it, and could not redo this a few weeks ago. I also tried a specialized Bentoo version for the 1101HA but also that one was not successful. If it would be hardware 1) interesting that puppy works 2) it used to work fine before reinstalling, so than it would have broken down during installation process, not impossible, but I think also not very likely?

---

### Post by Huib123 on 2015-03-02
My attempts include as suggested by Mörgaes (thanks!) alternate Lubuntu - mini.iso - which succeeded in installing everything on one of the partitions but after the necessary reboot it stalled again after a couple of minutes with the message 'perf samples too long' and reduced the sample frequency in several steps by 100 and stalled. I understand that 'perf samples too long' is not a fatal error but it discontinued.

---

### Post by mörgæs on 2015-03-06
Which versions of the alternate ISO did you try?
Did you apply updates and reboot before receiving the error message?

---

### Post by sudodus on 2015-03-06
I think

```
OpenGL Renderer        : Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
```

indicates ATI/AMD/Radeon graphics, which might cause your problems. If problems with Lubuntu 14.04 LTS, you can try some boot options. Start with **nomodeset**.

If still no success, try a community re-spin based on Ubuntu 12.04 LTS (with a light desktop environent), for example ***Bento, Bodhi*** or ***LXLE***. These have older versions of the graphics drivers, and may work better in your computer. [COLOR=#696969]Ubuntu 12.04 LTS itself needs more CPU horsepower and more RAM to work well.[/COLOR]

But Tahrpup is working, and it is a good alternative :-)

---

### Post by Huib123 on 2015-03-07
I have tried 14.04 Trusty Tahr[  32 bit mini ISO]("http://archive.ubuntu.com/ubuntu/dists/trusty/main/installer-i386/current/images/netboot/mini.iso") downloading seemed to have been successful and after the necessary reboot it stalled again.
[TABLE]
[TR]
   [TD][/TD]
[/TR]
[/TABLE]

---

### Post by sudodus on 2015-03-07
I'm rather sure that the mini.iso should run in your computer.

Did you check the md5sum?

How did you flash it to the pendrive?

There should be no problems with graphics in the text mode of the mini.iso. But there might be problems with the wifi.

It might help to connect the computer via wired internet (ethernet). The mini.iso needs a working connection to an Ubuntu server to download the necessary program packages.

---

### Post by Huib123 on 2015-03-07
Thanks, the owner tried Bento Ubuntu 12.04 without any luck, I will try LXLE as well.

---

### Post by Huib123 on 2015-03-07
No I did not check the md5sum, I am not sure how to. And yes I had a wired internet connection and saw tons of downloads coming in.
I could not flash with Startup Disk Creator on my Ubuntu 12.04 machine and used Unetbootin instead.
At first the reboot did not work at all and after updating Grub with Puppy the reboot of Lubuntu 14.04 started but stalled in 2 minutes.

---

### Post by sudodus on 2015-03-07
The Ubuntu flavour md5sums can be found at this link [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Run the command

```
md5sum file.iso
```
for example
```
md5sum mini.iso
```
and the result should match the listed string

The 14.04 Trusty Tahr[  32 bit mini ISO]("http://archive.ubuntu.com/ubuntu/dists/trusty/main/installer-i386/current/images/netboot/mini.iso")  might be bad. Use the following one instead

32 bit:  [http://archive.ubuntu.com/ubuntu/dis...mages/netboot/]("http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/installer-i386/current/images/netboot/")[URL="http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/installer-i386/current/images/netboot/"]
[/URL]
with the following md5sum
```
389809bbb6c77e82f4a4efd4679b2555  ./netboot/mini.iso
```according to [http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/installer-i386/current/images/MD5SUMS](http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/installer-i386/current/images/MD5SUMS)

---

### Post by Huib123 on 2015-03-07
Thanks for explaining, I have succeeded in the mean while with LXLE Ubuntu 12.04, a major step forward, all seems well but the brightness setting (GMA 500) and some other function keys. I have tried changing by the menu, changing the grup file line (GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"), tried echo X > /sys/class/backlight/acpi_video0/brightness and backlight in terminal, no luck so far. Will continue coming days. I saw some suggestions on tty setting will try those.
Anyhow thanks everone!

---

### Post by sudodus on 2015-03-07
I'm glad that you have a full installed system running now. Congratulations :KS

---

### Post by Huib123 on 2015-03-11
After installing LXLE Ubuntu 12.04 the reboot failed. Using grub4dos in Puppy made the distro bootable, set the boot flag with Gparted,  and with Boot Repair I managed to install a proper Ubuntu boot.
I have not solved the issue of adjusting screen brightness with Fn 5 & 6, the workaround    [https://wiki.archlinux.org/index.php/poulsbo#Set_backlight_brightness](https://wiki.archlinux.org/index.php/poulsbo#Set_backlight_brightness)  is functional so I will return the pc to the owner; one more happy Ubuntu user!
The Ubuntu Forum has helped me greatly, thanks everyone.

---

### Post by sudodus on 2015-03-11
Thanks for sharing your result :-)

---

