---
title: "Dual boot problem on new Dell Latitude E5470"
date: 2017-02-11
forum: Installation &amp; Upgrades
---

### Post by eddugo on 2017-02-11
Hi;  I am a 9 year used and have dual booted Ubuntu on many machines but I can't get this one right.  I have read and tried just abut every tutorial out there and I guess my problem is even though I am starting the install drive in windows UEFI, it loads the Ubuntu in legacy.  I can start Ubuntu 16.10 - 64 by going to the F12 boot menu and going to legacy and that would be fine with me except I do not get a grub menu so I have no diagnostics or safe mode.  What should I do?  Here are the stats on the laptop;  
Dell Latitude 14 5000 Series E5470 
* Processor: Intel Core 6th Generation i5-6440HQ Processor (Quad Core, 2.60 GHz, 6M Cache, 35W) 
* Operating System: Windows 10 Pro, 64-bit 
* Memory: 8GB 2133MHz DDR4 Memory Non ECC; up to 2 slots supporting up to 16GB 
* Display: 14 inch HDF (1366x768) Non-Touch Anti-Glare LCD Display 
* Hard Drive: 500 GB SATA Hard Drive (7200 RPM) 
* Graphics Card: Intel Integrated Graphics; 
* Manufacturer Warranty: 1 Year Hardware Service with Onsite/In-Home Service After Remote Diagnosis from Dell** 
* Optical Drive: External Options Only 
* Connectivity: 10/100/1000 Ethernet; Dell Wireless 1820 802.11AC Dual-Band Wi-Fi + BT 4.1 Wireless Card; 
* I/O Ports: 3 USB 3.0 (one with PowerShare), HDMI, VGA; Network connector (RJ-45), external SIM card tray option; SD 4.0 Memory card reader; Headset/mic combo jack; Two M.2 Expansion slots: 1 WWAN/HCA and 1 WLAN/BT/WiGig; EDock port; Lock slot 
* MultiMedia : High Quality Speakers; Headset/mic combo jack; Noise reducing array microphones; HD video webcam; 
* Dimensions: (H x W x D) Inches/(cm) 0.9 x 13.2 x 19.1 /(2.32 x 33.49 x 23.11) 
* Minimum Weight (lbs/kg): 3.88/1.76
 
**Thank you in advance for any advice.**

---

### Post by ajgreeny on 2017-02-11
We need to know more about the current installation of both OSs so go to Boot-Repair in my signature below and follow the instructions there to run the Boot-Info-Script.	 

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system setup, not the hardware but the software.

To get the system running as you want it is necessary to have both OSs installed in the same mode, ie, in your case UEFI and the report from Booty-Repair will suggest how best this should be done.

---

### Post by eddugo on 2017-02-13
Hello again;
Hopefully this is what you want;
[http://paste2.org/NUec7vgw]("http://paste2.org/NUec7vgw")

Thank you

Ed

---

### Post by oldfred on 2017-02-13
You have Ubuntu installed in BIOS/CSM/Legacy boot mode.
And Windows is in UEFI boot mode.

UEFI and BIOS are not compatible, once you start booting in one mode from UEFI boot menu you cannot change. Or from grub menu you can only boot other systems in same boot mode.

Since grub only sees Ubuntu as it cannot boot Windows, you do not get grub menu. You should be able to press escape just after Dell logo to get grub menu.
But if you have fast boot in UEFI on, then you may not have any or much time to press escape. 
Best to have UEFI fast boot off. Or set to off or full system startup mode, if full system shutdown. Or fast boot only on reboot.

You can use Boot-Repair to convert from BIOS to UEFI boot of Ubuntu.
But you need to boot Ubuntu in UEFI mode from live installer. It should boot whether UEFI Secure boot is on or off, but may be better with Secure boot off. 
You may also have to turn on in UEFI allow USB boot.

You also need to turn off Windows fast start up or always on hibernation.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Vendor UEFI are similar across models. So even if not exactly same model, users may have posted info that will help you.

 Dell XPS 8910  16.04.1 works, 16.04 did not
[https://ubuntuforums.org/showthread.php?t=2351949](https://ubuntuforums.org/showthread.php?t=2351949) 
Older Ubuntu, 16.04 should have most of older Dell fixes.

 Dell LATITUDE E5450  LInks to Dell fixes for 14.04
[http://ubuntuforums.org/showthread.php?t=2270275](http://ubuntuforums.org/showthread.php?t=2270275)

---

### Post by eddugo on 2017-02-13
I did the repair and got an error message and a new paste address: [http://paste2.org/XFWIUcPW]("http://paste2.org/XFWIUcPW")

The error report is attached - I think although i don't see it.

It did reboot to a GRUB with both op systems.

DO you need to review the error or should i mark this "solved"

Thank you

Ed[ATTACH=CONFIG]273687[/ATTACH]

---

### Post by oldfred on 2017-02-13
Linux tools see errors on unformatted partitions. And it looks like Boot-Repair then tries to mount as NTFS. But the Microsoft reserved & bios_grub are both required to be unformatted. So any errors related to them can be ignored.

It looks like now you have entry for the efi partition in fstab, so configured for UEFI boot.
You still have the old BIOS grub in MBR, but now it should not work, or if you attempt to boot in BIOS mode you will get grub errors, not UEFI boot errors.

Does system boot in UEFI mode?

---

### Post by eddugo on 2017-02-13
Yes it boots in uefi mode

---

### Post by oldfred on 2017-02-13
Then I believe you can change to solved.

If you have other issues, please post a new thread on that issue.

---

### Post by eddugo on 2017-02-14
Thank you very much for your help.  I see you are in SW Florida -Tallahassee here.  Take care.


Ed

---

