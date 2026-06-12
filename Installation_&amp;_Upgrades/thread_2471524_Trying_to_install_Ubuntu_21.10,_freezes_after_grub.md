---
title: "Trying to install Ubuntu 21.10, freezes after grub menu"
date: 2022-02-01
forum: Installation &amp; Upgrades
---

### Post by mathkochi on 2022-02-01
I have a desktop with NVME SSD(with RAID option) and NVidia Graphics card. Currently Windows 11 is working fine. Was trying to install Ubuntu 21.10 alongside Windows 11.
So I downloaded the ISO and verified it. After that used Rufus with GPT, UEFI and Persistent parameters to create a bootable Live Hard disk. 
Then used the Live Hard disk for booting. The Grub menu appears. I selected the Safe Graphics option and still the screen was blank.
Again tried with xforcevesa option in GRUB. This time it started with the message UEFI: Secure Boot enabled and froze.
Again I disabled Secure Boot. But this time it freezes after displaying the first line 'Running commands'.

---

### Post by MAFoElffen on 2022-02-02
What 'is' the PC make and model?

Nothing except Windows work with SATA "RAID mode". The BIOS needs to be set to SATA AHCI mode for anything else besides Winodws to be able to read the NVMe. Windows runs fine on SATA AHCI mode. In fact during warranty repairs, if a user needed to reinstall, Winodws 11, I would ensure that they reinstalled in that mode.

You can't just go into BIOS and change the mode without doing other things first. If you do, then Windows will fail to boot. Follow these instruction first:
[https://support.thinkcritical.com/kb/articles/switch-windows-10-from-raid-ide-to-ahci](https://support.thinkcritical.com/kb/articles/switch-windows-10-from-raid-ide-to-ahci)

Then you change the BIOS settings for SATA to change it to be in "AHCI Mode" and when it boots into safe mode, and continues (with those instructions) will start using the Windows AHCI drivers...

Not sure what your boot problem might be yet, but that it the first step before you do anything. Next would be to try to boot a USB LiveCD and use "Try" to see if it runs stable. Being it has NVMe, I would think that hte hardare is recent and you should have very little problems with that, but you haven't said anything about what that hardware is, so.... More information needed.

---

### Post by mathkochi on 2022-02-03
The make is HP and model is SLim S01-PF2008IN


Processor    Intel(R) Core(TM) i5-10400 CPU @ 2.90GHz   2.90 GHz
Installed RAM    16.0 GB (15.7 GB usable)
System type    64-bit operating system, x64-based processor
Pen and touch    No pen or touch input is available for this display

It also has Gigabyte GEFORE GT710 2GB DDR3 Graphics Card.

I tried running the System info script from Windows11. But I could not trace the output directory

---

### Post by mathkochi on 2022-02-03
Also I treid to boot Live Ubuntu Hard disk. It works with acpi=off and xforcevesa and safe graphics.

---

### Post by ajgreeny on 2022-02-03
What NVidia graphics card does the machine have; maybe you need the ***nomodeset*** boot option in order to get a low resolution GUI to start and then install an nvidia driver?

I've never used nvidia so may be very out of date with requirements.

---

### Post by tea for one on 2022-02-03
> **mathkochi said:**
> Also I treid to boot Live Ubuntu Hard disk. It works with acpi=off and xforcevesa and safe graphics.

Now that you have booted into a live session, you should check that all your hardware works OK.
i.e. sound, wifi, bluetooth, usb devices etc.
Your display probably needs Nvidia drivers (which can be added after installation)

If you decide to install Ubuntu, it is advisable to use Windows (Disk Management) tools to reduce Windows partition size and create free space.
Also reboot Windows to allow chkdsk to run.

---

### Post by mathkochi on 2022-02-03
Have run Windows chkdsk. Also I have changed the SATA to ACHI in BIOS. Please see below the system-info script output and guide me:

[https://paste.ubuntu.com/p/S24yTfxxyy/](https://paste.ubuntu.com/p/S24yTfxxyy/)

---

### Post by tea for one on 2022-02-03
We know that you will need Nvidia drivers after installation.
Other than your display, did you check that your hardware works in a live session?

---

### Post by mathkochi on 2022-02-03
Here there are some hardwares like USB Audio device. Is there any command to check whether the hardware devices are working properly? And also to check as to why we need a acpi=off and xforcevesa at boot time?
Previously I had installed Ubuntu with acpi=off and xforcevesa options. However when booting from the installed version, it caused NVIDIA IRQ problems and was unable to boot.

---

### Post by tea for one on 2022-02-04
> **mathkochi said:**
>  However when booting from the installed version, it caused NVIDIA IRQ problems and was unable to boot.

Now that you have installed Ubuntu, it would be better to start a new thread with each problem.

---

### Post by MAFoElffen on 2022-02-04
> **mathkochi said:**
> Here there are some hardwares like USB Audio device. Is there any command to check whether the hardware devices are working properly? And also to check as to why we need a acpi=off and xforcevesa at boot time?
Previously I had installed Ubuntu with acpi=off and xforcevesa options. However when booting from the installed version, it caused NVIDIA IRQ problems and was unable to boot.
At the Grub Boot Menu of the installed system boot... If you edit the linux boot line of the menu,and add nomodeset, does it boot?

If it does not, then got to Advance Options > Menu option with recovery > Boot with Safe Graphics...

Then Activities > Updates & Software > Additional Drivers Tab... Select an appropriate Graphics driver...

---

### Post by mathkochi on 2022-02-05
I tried to boot using nomodeset option but it hangs after scanning the usb drives. Samething happens in recovery mode. Have taken snap of the message. Please use link below to see snapshot.
[https://drive.google.com/file/d/18bDH8YXNDAl2P2UvE77Yzo1Bra8rNevR/view?usp=drivesdk](https://drive.google.com/file/d/18bDH8YXNDAl2P2UvE77Yzo1Bra8rNevR/view?usp=drivesdk)
Please guide.

---

### Post by MAFoElffen on 2022-02-05
All your Video and USB info is in your posted 'system-info" report. Thank you. If any else asks questions about your settings and hardware, please ask them to look at the link in Post #7 first.

Your video:Intel APU UHD Graphics 630

Your USB Questions are shown their via lsusb:
That Realtek based USB Device is shown as connected on USB Port 14, Dev 4, If's 0 & 1. That doesn't mean that is is working correctly, that the driver is working properly, but at least it is being shown as logically connected.

In your BIOS, is there a setting for graphics, where it selects between the NVidia and Intel Graphics as the primary? I believe so, and it is showing that the NVidia is selected a primary... But I don't see where it is using any graphics driver (yet).

One thing you might do... If booted to recovery, then Advanced > Mount Filesystem with Networking... Then Drop to Root Prompt. Then you should be able to use
```

ubuntu-drivers autoinstall

```
for it to query the graphics card and install an appropriate driver... from the command-line..

---

### Post by mathkochi on 2022-02-05
As of now, I followed your instructions and was able to login recovery mode with acpi=off and xforcevesa. Then ran ubuntu-drivers autoinstall command.
Now I am able to login recovery mode with acpi=off and xforcevesa and using intel graphics.
Also Nvidia is primary graphics card in Bios.
Now when I turn on machine one error comes saying invalid parameter etc . Then 
Grub menu appears. When i select normal mode. It starts displaying message. After five minutes the below screen appears and system hangs
https://drive.google.com/file/d/18li8BJnEM5e_nNcEPsxnDUweJ-5gBgGv/view?usp=drivesdk

https://drive.google.com/file/d/18li8BJnEM5e_nNcEPsxnDUweJ-5gBgGv/view?usp=drivesdk

Please guide.

---

### Post by MAFoElffen on 2022-02-06
That is the same error you posted from Post #1 isn't it? Where it is hanging just after that PixArt HP 125 USB Optical Mouse... 

For just a test: What happens if you unplug all your USB devices from your computer and try to boot? I understand that you will have no keyboard or mouse, but just ruling those out as possible problems...

EDIT: 
Questions... You said you can get to recovery mode > Mount Filesystem with Networking, then drop to a Root Prompt from there, right? Can you confirm that?

If so, then what do you get from this:
```

sudo lsusb -vvv | more
sudo lsusb -t -vvv | more

```

---

### Post by mathkochi on 2022-02-06
Now tried to boot in normal mode with Nvidia primary in BIOS. It shows blank screen. Tried removing usb devices. But no success.
In recovery mode it hangs after hid-generic wired keyboard on usb.....
It boots in recovery mode with acpi=off and xforcevesa options.
I ran the lsusb commands from root. Output is attached.
[https://drive.google.com/file/d/19JSkphCoIbaxK0U4qxJG2p2FvmwZ8qqv/view?usp=drivesdk](https://drive.google.com/file/d/19JSkphCoIbaxK0U4qxJG2p2FvmwZ8qqv/view?usp=drivesdk)
[https://drive.google.com/file/d/19GOPJenrDno4dXP24mF7yhmJQ8FtESz3/view?usp=drivesdk](https://drive.google.com/file/d/19GOPJenrDno4dXP24mF7yhmJQ8FtESz3/view?usp=drivesdk)

Also tried to repair dpkg package. It had a partial error zsys daemon

Thanks for your patience.

---

### Post by MAFoElffen on 2022-02-06
[SIZE=4]Caution!!![/SIZE] [COLOR=#ff0000]Never[/COLOR] try to repair or reinstall dpkg or apt systems on a live / installed system without a reinstall. I guaranty that will break your system. I know of no way to recover from that... 

If you meant that you were trying to repiar another package or system, fine... But those 2 systems are deeply rooted and cannot be screwed with. Just saying.... Bad JuJu!

---

### Post by MAFoElffen on 2022-02-06
Curious: What are the available USB setting options in your BIOS firmware?

---

### Post by mathkochi on 2022-02-06
I used the dpkg repair broken package option in the recovery menu. Hope it had not damaged the system.

Also the following are the snapshots of USB BIOS options.

[https://drive.google.com/file/d/19YMEs-REsOKAzNiw-Gw3KQ36Ark1xGYl/view?usp=sharing](https://drive.google.com/file/d/19YMEs-REsOKAzNiw-Gw3KQ36Ark1xGYl/view?usp=sharing)
[https://drive.google.com/file/d/19_z8pcU9hzKYpK90nodQwghfD3mt0O2v/view?usp=sharing](https://drive.google.com/file/d/19_z8pcU9hzKYpK90nodQwghfD3mt0O2v/view?usp=sharing)

---

### Post by MAFoElffen on 2022-02-07
Oh... That should be fine, using "dpkg to repair a package"... I thought you said you were repairing 'dpkg' itself... That would have been "bad".

I don't see anything there out of the ordinary... But shouldn't there also be a USB compatibility setting somewhere there? Like for Legacy USB spec's? USB 2 and USB3? Just wondering...

---

### Post by mathkochi on 2022-02-08
I am unable to see the Legacy USB setting. The Bios version is F 15. Contacted HP support, but they say HP supports only Windows. So any guidance to proceed further?

---

### Post by MAFoElffen on 2022-02-08
The person was mistaken... I you ever call HP Support again, Have fun with them. Remind them that they sell HP computers with not just Linux, but Ubuntu Pre-installed. HP Support even has HP Branded Ubuntu Installation media on USB... I am still certified for HP Warranty On-Site Service. I have been called out to on-site service to calls with pre-installed Ubuntu. Ask the person how not knowing that reflects on their personal service rating.

Unfortunately...The real "correct answer" they should have given you, was that they support the hardware they sell. HP Support does not actually support "Windows", nor any Operating System, specifically. They have a script of common answers. If not on their script, and not specifically related to hardware, then they are supposed to refer the customer on to Microsoft Support, or this Forum.

I just posted a link to the HP Support Linux FAQ in a recent post...

EDIT:
I found it: [https://support.hp.com/us-en/document/c00269588](https://support.hp.com/us-en/document/c00269588)

---

### Post by mathkochi on 2022-02-11
Now I am able to boot into regular ubuntu with acpi=off and nouveau driver(open source). I read in some articles that acpi=off option may reduce the lifetime of components and increase the power consumption. So, is it safe to use the computer in this acpi=off mode?
Also there is only one display resolution i.e. 1024 x 768. And I am unable to change the resolution. 
Further the suspend option is also not working.
Please guide.

---

