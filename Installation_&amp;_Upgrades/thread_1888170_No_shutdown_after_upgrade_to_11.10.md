---
title: "No shutdown after upgrade to 11.10"
date: 2011-11-28
forum: Installation &amp; Upgrades
---

### Post by GDR! on 2011-11-28
After upgrading my Kubuntu to 11.10 (about a month ago), my computer does not turn off after shutdown and I need to unplug it. It's a regular desktop PC, I was using all versions since 10.04 on this hardware with no issues. It was purchased with Ubuntu compatibility in mind so I doubt it's a driver issue.

Any ideas where I can look for process that's blocking the shutdown?

```
gdr@gdr-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

---

### Post by bluexrider on 2011-11-28
so to clarify.... 

you use the Quit Button and Shut Down but the computer does not turn off?

have you checked the Power Management settings? 

what happens if you press the power button on your box?

---

### Post by GDR! on 2011-11-29
> **bluexrider said:**
> so to clarify.... 

you use the Quit Button and Shut Down but the computer does not turn off?

It only happens with sudo halt. Quit button/shut down seems to work, I didn't try it before, but I need working sudo halt. I often use my machine via SSH and need to be able to shut it down remotely.

> **bluexrider said:**
> have you checked the Power Management settings? 

I haven't found any relevant settings in Power Management.

> **bluexrider said:**
> what happens if you press the power button on your box?

A pop-up asks me if I want to shut down my system.

---

### Post by bluexrider on 2011-11-29
> **GDR! said:**
> After upgrading my Kubuntu to 11.10 (about a month ago), my computer does not turn off after shutdown and I need to unplug it. It's a regular desktop PC, I was using all versions since 10.04 on this hardware with no issues. It was purchased with Ubuntu compatibility in mind so I doubt it's a driver issue.

Any ideas where I can look for process that's blocking the shutdown?




I didn't see anything here that mentioned that you were looking for CLI sudo halt issue using SSH?

mean what you ask and ask what you mean!

**shutdown command**

shutdown  arranges for the system to be  brought down in a safe way.  All logged-in users are notified that the  system is going down and, within the last five minutes of TIME, new  logins are prevented. The shutdown utility provides an automated  shutdown procedure for supersers to nicely notify users when the system  is shutting down, saving them from system administrators, hackers, and  gurus, who would otherwise not bother with such niceties.
**How do I use shutdown command?**

The  shutdown command can be used to turn off or reboot a computer. Type the  command as follows to shutdown server / computer immediately:
 $ sudo shutdown -h now
 OR
 $ sudo shutdown -h 0 
**How do I shutdown compute at specific time?**

To shutdown computer at 6:45pm, enter:
 $ sudo shutdown -h 18:45 "Server is going down for maintenance" 
 At 6:30pm message will go out to all user and 6:45 system will shutdown.
Please note that you can also use halt or poweroff or reboot command for stopping and restarting the system:
 $ sudo halt
 OR
 $ sudo poweroff
**How do I reboot computer?**

Simply use reboot command:
 $ sudo reboot
 OR
 $ sudo shutdown -r 0

You may want to try this

---

### Post by GDR! on 2011-12-15
> **bluexrider said:**
> I didn't see anything here that mentioned that you were looking for CLI sudo halt issue using SSH?

mean what you ask and ask what you mean!


I did not realize it was different. I have been using 'sudo halt' on a local terminal since the time I ran Debian 2.0 on an Amiga 1200 and it always worked the same as shutdown from menu.

Of course you're right and I should have stated that. I didn't even try if the shutdown from menu worked when I asked this question - it did.

Anyway, using **sudo poweroff** instead of sudo halt fixed the problem. Thank you.

---

