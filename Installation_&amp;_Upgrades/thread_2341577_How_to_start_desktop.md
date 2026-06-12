---
title: "How to start desktop?"
date: 2016-10-29
forum: Installation &amp; Upgrades
---

### Post by VanillaMozilla on 2016-10-29
I just upgraded to Ubuntu 16.04 32 bit.  It's a little scary, because at least once the computer booted but the desktop failed to start.  The computer seems unusually slow to start, and logging in is slow.  My fear is that it could become a permanent problem, with no functioning desktop.

In case this happens, does anyone know the command to start the desktop?  I assume I could just start it manually.  At that point I would be grateful for either the Unity or fallback desktop.

I don't think it's a hardware problem.  I don't have a log, or at least I haven't checked for one.

---

### Post by ajgreeny on 2016-10-29
I see you are using a 32 bit system which leads me to query your hardware specs; Ubuntu with unity needs a fairly high spec machine, particularly graphics, so I wonder if you are at the edge as far as hardware is concerned.

If you are not totally sure show us the output of terminal command```
sudo lshw -short
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by VanillaMozilla on 2016-10-30
> **ajgreeny said:**
> I see you are using a 32 bit system which leads me to query your hardware specs; Ubuntu with unity needs a fairly high spec machine, particularly graphics, so I wonder if you are at the edge as far as hardware is concerned.

For what it's worth, I don't use the Unity desktop.  And I don't think hardware specs. are on the edge.  But in any case, here you go.
```
H/W path           Device      Class       Description
======================================================
                               system      Inspiron 530s
/0                             bus         0RY007
/0/0                           memory      128KiB BIOS
/0/4                           processor   Intel(R) Core(TM)2 Duo CPU     E8300 
/0/4/a                         memory      32KiB L1 cache
/0/4/b                         memory      6MiB L2 cache
/0/4/0.1                       processor   Logical CPU
/0/4/0.2                       processor   Logical CPU
/0/24                          memory      4GiB System Memory
/0/24/0                        memory      2GiB DIMM DDR2 Synchronous 800 MHz (1
/0/24/1                        memory      DIMM [empty]
/0/24/2                        memory      2GiB DIMM DDR2 Synchronous 800 MHz (1
/0/24/3                        memory      DIMM [empty]
/0/1                           processor   
/0/1/0.1                       processor   Logical CPU
/0/1/0.2                       processor   Logical CPU
/0/100                         bridge      82G33/G31/P35/P31 Express DRAM Contro
/0/100/1                       bridge      82G33/G31/P35/P31 Express PCI Express
/0/100/2                       display     82G33/G31 Express Integrated Graphics
/0/100/19          eth0        network     82562V-2 10/100 Network Connection
/0/100/1a                      bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1a/1        usb3        bus         UHCI Host Controller
/0/100/1a.1                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1a.1/1      usb4        bus         UHCI Host Controller
/0/100/1a.2                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1a.2/1      usb5        bus         UHCI Host Controller
/0/100/1a.2/1/1                input       B015-000 R0.75 USB to PS2 adapter.
/0/100/1a.7                    bus         82801I (ICH9 Family) USB2 EHCI Contro
/0/100/1a.7/1      usb1        bus         EHCI Host Controller
/0/100/1a.7/1/6                bus         HighSpeed Hub
/0/100/1a.7/1/6/4              printer     Pro9000II series
/0/100/1b                      multimedia  82801I (ICH9 Family) HD Audio Control
/0/100/1d                      bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d/1        usb6        bus         UHCI Host Controller
/0/100/1d.1                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.1/1      usb7        bus         UHCI Host Controller
/0/100/1d.2                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.2/1      usb8        bus         UHCI Host Controller
/0/100/1d.7                    bus         82801I (ICH9 Family) USB2 EHCI Contro
/0/100/1d.7/1      usb2        bus         EHCI Host Controller
/0/100/1e                      bridge      82801 PCI Bridge
/0/100/1f                      bridge      82801IR (ICH9R) LPC Interface Control
/0/100/1f.2                    storage     82801IR/IO/IH (ICH9R/DO/DH) 4 port SA
/0/100/1f.3                    bus         82801I (ICH9 Family) SMBus Controller
/0/100/1f.5                    storage     82801I (ICH9 Family) 2 port SATA Cont
/0/2               scsi0       storage     
/0/2/0.0.0         /dev/sda    disk        500GB WDC WD5000AAKS-7
/0/2/0.0.0/1       /dev/sda1   volume      47MiB Windows FAT volume
/0/2/0.0.0/2       /dev/sda2   volume      272GiB Windows NTFS volume
/0/2/0.0.0/3       /dev/sda3   volume      3380MiB Windows FAT volume
/0/2/0.0.0/4       /dev/sda4   volume      189GiB Extended partition
/0/2/0.0.0/4/5     /dev/sda5   volume      187GiB Linux filesystem partition
/0/2/0.0.0/4/6     /dev/sda6   volume      2925MiB Linux swap / Solaris partitio
/0/3               scsi1       storage     
/0/3/0.0.0         /dev/cdrom  disk        DVD+-RW AD-7200S
/0/3/0.0.0/0       /dev/cdrom  disk        
/0/5               scsi3       storage     
/0/5/0.0.0         /dev/sdb    disk        500GB WDC WD5000AAKX-7
/0/5/0.0.0/1       /dev/sdb1   volume      465GiB EXT4 volume

```

---

### Post by ajgreeny on 2016-10-30
OK, nothing there that is an obvious problem to me; a dual core Intel CPU and 4GB of ram, using the integrated Intel graphics should work fine as far as I can see.

You say you're not using unity desktop, so what are you using instead?

---

### Post by him610 on 2016-10-30
Why do the entries that address memory,
> ```
/0/24                          memory      4GiB System Memory
/0/24/0                        memory      2GiB DIMM DDR2 Synchronous 800 MHz (1
/0/24/1                        memory      DIMM [empty]
/0/24/2                        memory      2GiB DIMM DDR2 Synchronous 800 MHz (1
/0/24/3                        memory      DIMM [empty]

```
show empty DIMM slots?

Could it be the memory is misconfigured? That it should be 4*1GB DIMMs instead of 2*2GB DIMMs plus two empty memory slots which the BIOS does not recognize because it expects 4*1GB.

Does anyone else have an opinion on this?

---

### Post by ajgreeny on 2016-10-31
Your motherboard obviously has 4 ram ports on it and they are possibly paired as 0 & 2, and 1 & 3.
I doubt that has anything to do with the problem, unless there is something that we are both unaware of.

Do you have a computer manual for that machine which gives any information on the ram ports?
Is it a desktop or laptop, and can you open it to move the ram chips around?

---

### Post by him610 on 2016-10-31
How about running this  command from the command line...
```
 hwinfo --memory
```
It shows are different view of your memory.

---

### Post by VanillaMozilla on 2016-10-31
Thanks for the replies.  It's time for a status report and some clarification.

There are two problems here.  The first problem is that the GUI fails to start.  (I said "desktop", but I meant "GUI".)  Normally a login prompt is briefly displayed in text mode, and then the GUI is supposed to start automatically.  (I think I have GRUB 1, which may give a different boot sequence from what you all are used to.)  Since the problem only occurred about twice shortly after the upgrade, the problem may not be as serious as I feared.

*If any of you happens to know how to start the GUI manually, that information would be most welcome.  I'm not asking for research here.*  :)  (I'm using GNOME Flashback Metacity, but I think it's the x session -- or whatever it's called -- that needs to be started.)

The second, relatively minor problem is slow login (with either GNOME Flashback Metacity or Unity) and slow shutdown.  It happens on this computer, but not on an older, slower one.  I have a fairly generic setup, with little customization.  This doesn't warrant heroic effort at this time, especially since I haven't given you much to go on.  (I suspect it could be a network problem, but I want to defer that for another time.)

I really don't think there's any hardware problem.  I have not tested recently, but the hardware has always been flawless, and everything worked well until this update.  Memory is supposed to be configured in slots 1 and 3 first (numbered 0 and 2 in the report); 2 and 4 can be empty.  It is configured correctly.  I'll supply more info about memory later, when I have that computer available.

---

### Post by him610 on 2016-10-31
From the command line...
```
startx
```
Good luck

Note: I have an E7200 with 4GB RAM. It is my main machine; still runs great.

---

### Post by ajgreeny on 2016-10-31
Unfortunately, I don't think the startx command will work any more with 16.04 using systemd instead of upstart; I think you will have to use the command ```
sudo service lightdm start
``` assuming **lightdm** is your display manager, which I am uncertain about if using fallback desktop or unity.  Change that command to start whichever dm your system uses.

---

### Post by VanillaMozilla on 2016-11-01
Lightdm is my display manager, as far as I can tell.

hwinfo is not installed, so will not pursue that further.

Thanks very much for thoughtful replies.  For now I'm inclined to put this on the back burner so I don't waste too much of your time.  The system is actually working fairly well now, and little clues are still presenting themselves.  I may try again when I know more.  It's odd that both upstart and systemd are running and remain running.

For the record, the start commands did not quite work.  On my system:
startx
starts only the generic pink background and a big 'x' mouse cursor.
service lightdm start
gives a nonfunctioning login screen with a warning that the system is still booting.
service gdm start
gives an error message but no GUI (I have lightdm).

---

### Post by VanillaMozilla on 2016-11-08
Update:  I'm not going to mark this as solved, but for whatever reason, I haven't had any more problems.

And it's still slow to start, but that's probably because it uses over 400 MB, whereas it used to used about 200 MB.  The funny thing is, in spite of 200 MB of "improvements", it still works about the same as always, or maybe not quite as well.  Oh, well.

---

