---
title: "No Login Menu on Boot"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by theviking10 on 2010-05-15
Hello all. When I attempted to install 10.04 on my Toshiba A505-S6005 all appeared to go smoothly, but when the system rebooted the splash screen appeared only after a few seconds of a blinking cursor. The default desktop background appeared, and I heard the drumbeats that announce "Hello!" but there was no login menu.

Background: I have struggled to put linux on this laptop, but there have been many compatibility issues thus far. However, once I switched my hard drive controller to AHCI I was able to boot 10.04 live with no trouble. 

On a regular boot I can login via Alt+Ctrl+F1, but even after I run "sudo apt-get upgrade" etc. the login fails to appear.

Furthermore, while poking around in Cli I noticed that my home folder more closely resembled the live environment (i.e, there was an examples.desktop file instead of the usual folders)

I have burned a new CD at a slower rate with a new iso, but this one yielded the same results as the first. Please help, I am currently using Win7, but I would much like to be back on Linux.

---

### Post by theviking10 on 2010-05-15
Perhaps I should also mention that I have attempted to boot with openSUSE 11.2 and Fedora 13 Beta to no avail. I could not even run these distros live.

---

### Post by theviking10 on 2010-05-16
Bumping and updating: After Ctrl+Alt+F1 I keep getting text announcing "unable to enumerate usb device on port 1" and something about "error -110".

---

### Post by robert shearer on 2010-05-16
> unable to enumerate usb device on port 1

Have you a mouse plugged in to  usb ?

also try this in your browser...

```
site:ubuntuforums.org error 110 ubuntu
```

for several hits on these forums about error 110.

such as...
> I had a USB flash card reader that stopped by machine from booting with tha t -110 error. I upplugged the reader and it booted. I went and bought an identical one and all has been fine.


from a quick read it sounds like something plugged into one of your usb ports is stopping boot.
Try unplugging all usb devices and then boot.

---

### Post by theviking10 on 2010-05-17
Thank you - I was booting from USB earlier, will try with a regular disc. 

No mouse plugged in, though, just laptop power cord and ethernet.

Also, thank you for the link.

---

### Post by theviking10 on 2010-05-17
Okay, turns out that none of the USB ports on my laptop work when running live, which I assume is the same when installed.

Is this the reason I'm having trouble installing? 

Also, here is my lspci, if that helps.

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)

00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)

00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)

03:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
03:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)

3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)

3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)

3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)

3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)

3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

---

### Post by theviking10 on 2010-05-21
Still nothing. The latest Arch Linux was not able to boot properly either, and the release candidate for Fedora 13 is not looking good either. 

USB still not working, even after disabling the legacy emulator in my BIOS. Still can only link to SATA with AHCI.

Typing this while booting live from Ubuntu. Any new ideas?

---

### Post by theviking10 on 2010-05-23
Bumping for solutions . . . .

---

### Post by dino99 on 2010-05-23
just have seen your post, give it a try by checking the bios settings to be sure about usb prefs and boot order, maybe check if a newer bios exist too.

sudo update-pciids && update-usbids

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

[COLOR="Red"]you might look here:[/COLOR]  [http://ubuntuforums.org/showthread.php?p=9321225](http://ubuntuforums.org/showthread.php?p=9321225)

[http://www.google.com/search?as_q=+lucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=A505+S6005+&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.com/search?as_q=+lucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=A505+S6005+&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

