---
title: "Boot Device Not Found"
date: 2020-01-01
forum: Installation &amp; Upgrades
---

### Post by dan3712 on 2020-01-01
Hello, all. Thanks in advance for any help I can get with this. I apologize for how long-winded it is.

I purchased a new HP DY-1023DX laptop with Windows 10. I created an Ubuntu 19.10 USB Boot disk. I believe the BIOS is UEFI. (And I'm not sure if I am correctly saying that.) When I ran the installation, I selected the 256GB disk to install instead of the 14GB disk. I'm pretty sure this was a very bad decision. During the installation, an error window flashed that had some variation of 'fatal error' written in it. But the installation process continued, and it prompted me to reboot after removing the boot USB. After doing so, I received the screen, "Boot Device Not Found. Please install an operating system on your hard disk. Hard Disk - (3F0)."

So I redid the process, selecting the 14GB disk. And the installation completed without the 'fatal error' message window. The process completes to the point of prompting to reboot without the USB disk inserted. However, after rebooting, the same screen appears with the "Boot Device Not Found... " message.

There is an option to perform system diagnostics. When I run the Hard Drive Check on the 14GB disk, the results are "SMART Check PASSED, Long DST NOT AVAILABLE". The 256GB Disk passes both tests.

I initiated the live session, using the same USB Boot disk. (As a side note, if I now try to install during a live session, the system tells me that the computer currently has Ubuntu 19.10 and Ubuntu 19.10(19.10) on it.) I can't run Boot-Info because Ubuntu Live says "No Wi-Fi Adapter Found. Make sure you have a Wi-Fi adapter plugged and turned on."

My questions are:
1. Based on this information, do you know if I have damaged my disk? If so, is this repairable?
2. How do I get Wi-Fi connectivity in a live session to run Boot-Info?
3. If my current set-up can be rescued, should I remove the 19.10(19.10) installation? If so, how? (And what does that mean?)

I've looked through UEFI Installing tips threads, and don't see any solutions to this problem. I've also searched for threads related to the Wi-Fi adapter. I have not seen anything I know how to do myself (yet). Again, thank you for any help you can offer. 

Dan

---

### Post by oldfred on 2020-01-01
If you are seeing 14GB (usable) is that really just your USB flash drive installer and not the drives in your system?
Many systems need UEFI update & SSD firmware update.
And many need drives changed from RAID or Intel RST to AHCI. But if still using Windows you must install Windows AHCI driver first.

       Windows AHCI instructions - some have found safeboot method better
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571)
[https://askubuntu.com/questions/1148120/ubuntu-18-0x-not-detecting-windows-ssd-during-installation](https://askubuntu.com/questions/1148120/ubuntu-18-0x-not-detecting-windows-ssd-during-installation) & 
[https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on#963100](https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on#963100)

If you installed to your installer, you may have to recreate the installer flash drive.

You also have 3 choices in UEFI for UEFI Secure Boot, UEFI, & CSM (UEFI/BIOS mode). You typically want UEFI and not CSM and often easier to have Secure Boot off.
And how you boot install media which is a separate choice is then how it will boot once installed. You should have two choices to boot installer flash drive if Secure boot is off, one UEFI:Flash and other just "flash" where "flash" is name or label of flash drive. Mine shows UEFI:PMAP or PMAP.

If you can plug in a hardwired Ethernet connection during install that may also give a choice or let you easily install a WiFi driver if yours does not work with live installer, otherwise.

---

### Post by dan3712 on 2020-01-23
On the right path now. Here's what I did.

Without an ethernet port or wireless access, bluetooth was the lifeline. The bluetooth was working with the v18.04 installation. I downloaded SecureTether Client v0.9 from the PlayStore. The app performed as advertised when I followed the multi-screen instructions to connect the laptop to the Internet. (I will be donating to these guys' cause for sure.)

After connecting to the Internet, I was able to follow the installation instructions for the BrosTrend AC1200 Wireless USB Adaptor, which I purchased from Amazon. (Their customer service was also very responsive too.) The installation was a single line terminal command and the driver installation took a while (maybe about 10 minutes or so).

With wireless now available, I was able to run 'sudo apt update' and 'sudo apt upgrade', and the laptop is working well so far (good screen resolution; connectivity; etc.). So I'm off to be productive until the next issue arises.

I'm not sure about the 14GB installation I mentioned previously. But I think it may be a drive partition designed for system restoration or some other such utility. If I find an answer to that, I'll be sure to post it.

---

