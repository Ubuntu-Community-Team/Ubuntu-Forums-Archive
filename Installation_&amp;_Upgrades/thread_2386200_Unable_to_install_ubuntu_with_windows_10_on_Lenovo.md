---
title: "Unable to install ubuntu with windows 10 on Lenovo Z"
date: 2018-03-02
forum: Installation &amp; Upgrades
---

### Post by mgoodwin on 2018-03-02
I've had unbunutu installed on this computer before but then upgraded my hard drive to a SSD.  I'm trying to install it again.

First, I had to turn on legacy-mode and set legacy first before EFI to get it to detecct the bootable USB I created.

I'm pretty sure windows is on EFI but I am unable to boot from USB if I switch to EFI

I was able to successfully install ubuntu from the bootable USB in Legacy-mode.
I could not use "Install next to Windows" option because it did not detect windows.
So, I used the "something else" option to custom installed it at the end of my drive 

The install succeeded, but when I cannot get my computer to boot to anything but windows.

If I switch to EFI mode and then hold shift + restart, then try to "Boot from USB" I get an error saying USB is not enabled for this system try something else(not verbatim)
I know that USB is enabled from the bios.

Finally, I tried to use boot repair from the bootable USB I created, but it requires me to be in EFI mode.

Here is a pastebin of the results
[http://paste.ubuntu.com/p/4G5V25X38d/](http://paste.ubuntu.com/p/4G5V25X38d/)

one thing to note.  I have a lot of partitions.  I have the normal C: but also a W: for work and G: for games in addition to a couple that windows created.  Is this an issue? I've read there is a max of 4 but when I just looked at my old hard drive, it had 5-6 partitions total including linux

---

### Post by panditax on 2018-03-02
When you boot usb in legacy mode then you're installing system in legacy mode as well.

---

### Post by ajgreeny on 2018-03-02
> **panditax said:**
> When you boot usb in legacy mode then you're installing system in legacy mode as well.
^^ +1 ^^

This is an important point to make as you will create several problems for yourself in a dual boot system if you have Windows installed with UEFI and Ubuntu as BIOS.

How did you create the USB you used to install the Ubuntu system?

---

### Post by mgoodwin on 2018-03-02
I was unable to boot from usb in UEFI mode.
I used Rufus to create the USB.  
If it matters, i put 16.04.4-AMD64 on to the usb.

As I mentioned, I could boot USB in legacy but not UEFI.  So is it the USB?

---

### Post by ajgreeny on 2018-03-02
Could be the way you made the USB but I do not know Rufus, though I believe it's a Windows only application, and it should be able to create a UEFI USB.

See [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) for lots of hopefully useful info about USB creation.

---

### Post by oldfred on 2018-03-02
Most often the issue is settings in UEFI. Or is this an older system with upgrade from Windows 7 to 10?

Almost all will not let you boot flash drive unless you turn on a setting in UEFI to allow USB boot. Some have settings that only allow USB as data devices.
Often also tied to UEFI Secure Boot as allowing any thing else to boot is not Secure. Is Secure Boot on or off. Better to be off.

Also have you updated UEFI? Lenovo did have issues with some models, I think mostly Yoga small systems.
Are drive(s) set for AHCI, not IDE nor RAID (Intel SRT) in UEFI.

Only the old BIOS/MBR configuration has the 4 primary partition limit. And then extended & logical partitions to allow more. Or other work arounds like Windows dynamic or Linux LVM.
With gpt partitioning used with UEFI, the limit is 128 partitions, but user can reconfigure partition table to allow more.

---

### Post by mgoodwin on 2018-03-02
As I mentioned, I can boot from USB in legacy mode, but not UEFI.
I have turned off secure boot and fast boot.

I just updated my UEFI.
I double checked, drive is set to AHCI not IDE.

When I try to "boot from UEFI USB" option after holding down shift and hitting resart, I get an error that says "This Sysstem has no USB option" and then I am given the choice between my hard drive or network.  The network option started showing up after I updated UEFI.

---

### Post by oldfred on 2018-03-02
No USB option sounds like a setting in UEFI to not allow USB boot. My UEFI says full initialization, in one place and legacy USB on another page.
Setting may even be in more than one page of UEFI settings as there are a lot.

---

