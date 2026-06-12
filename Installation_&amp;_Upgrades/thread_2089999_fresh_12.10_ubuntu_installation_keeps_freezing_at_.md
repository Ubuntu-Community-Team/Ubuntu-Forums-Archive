---
title: "fresh 12.10 ubuntu installation keeps freezing at startup"
date: 2012-11-30
forum: Installation &amp; Upgrades
---

### Post by lornlynx on 2012-11-30
Hello,

I received my new netbook today ([this one]("http://www.amazon.de/gp/product/B006SJ7Q0Y/ref=noref?ie=UTF8&psc=1&s=computers")) and I wanted to install Linux additionally to the windows os because I wanted to get known more to it and because my university only supports linux in my programming classes.

I downloaded 12.10 and created a bootable USB stick, then installed it. The installation ran perfectly fine with no problems whatsoever (I had internet connection the whole time during it), but everytime I try to start Ubuntu now it freezes at the starting up screen where it checks all the subprograms.

It ever freezes at the same point, which would be: "*starting configure virtual network devices". I can do nothing at that point other than heavy restarting my netbook.

edit: okay, it also freezes at another point, which is right after "*stopping save kernel messages"
Oh, and I should probably mention that none of the checks fail, they all have the [OK], it just completely stops at one point and enters sleep state.


I already checked some threads but none of them was any help whatsoever, whenever I tried any of the solutions I just got any error messages.

I tried already:

-starting in failsafe graphic mode: I get asked "Continuing will remount your / filesystem in read/write mode and mount any other filesystem defined in /etc/fstab. Do you wish to continue?" and when I press yes a terminal opens and it prints "fsck from util-linux 2.20.1" and "/dev/sda6: clean, 166403/7610368 files, 1195394/30428928 blocks". I am then stuck in the terminal and can't write any commands or even exit the terminal, I have to hardreset again.

-choosing dpkg for reparing broken packages: same as when trying failsafe graphic mode

-"sudo apt-get install lightdm": Doesn't work and I have no idea why not. print: "W: Not using locking for read only lock file /var/lib/dpkg/lock"; "E: Unable to write to /var/cache/apt/" and "E: The package lists or status file could not be parsed or opened."

-"sudo dpkg-reconfigure lightdm": answer print is "chown: changing ownership of `/var/lib/lightdm`: Read-only file system"

-"sudo dpkg-reconfigure gdm": "dpkg-query: package 'gdm' is not installed and no information is availabe" & "/usr/sbin/dpkg-reconfigure: gdm is not installed"

-reinstalled it twice now

The Windows partition runs perfectly fine.

Why is my partition only read only? I never set this? How can I make it read/write? And does that actually have anything todo with the fact that I ubuntu freezes every startup.


Could anyone please shed some light on this? I am absolutely confused of what just any of these error messages mean, and everytime I try something that seems to have worked for other people, I just get more and more error messages which again tell me absolutely nothing.

---

### Post by gnusci on 2012-11-30
Check 

$ dmesg

I may be a error message in there.

---

### Post by lornlynx on 2012-12-01
> **gnusci said:**
> Check 

$ dmesg

I may be a error message in there.

Looks like it...:

```
...
EISA: Probing bus 0 at eisa.0
EISA: Cannot allocate resource for mainboard
Cannot allocate resource for EISA slot 1
Cannot allocate resource for EISA slot 2
Cannot allocate resource for EISA slot 3
Cannot allocate resource for EISA slot 4
Cannot allocate resource for EISA slot 5
Cannot allocate resource for EISA slot 6
Cannot allocate resource for EISA slot 7
Cannot allocate resource for EISA slot 8
EISA: Detected 0 cards
...
PM: Hibernation image not present or could not be loaded.
...
EDD information not available
...
isapnp: No Plug & Play device found
...
EXT4-fs (sda6): INFO: recovery required on readonly system
EXT4-fs (sda6): write access will be enabled during recovery
EXT4-fs (sda6): recovery complete
EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
...
coretemp coretemp.0: >Unable to read TjMax from CPU 0
coretemp coretemp.0: >Using relative temperature scale!
coretemp coretemp.0: >Unable to read TjMax from CPU 2
coretemp coretemp.0: >Using relative temperature scale!
...
ACPI Warning: 0x00000460-0x0000047f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
Ipc_ich: Resource conflict(s) found affecting iTCO_wdt
ACPI Warning: 0x00000460-0x0000042f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
ACPI Warning: 0x00000460-0x0000042f SystemIO conflicts with Region \SWC1 2 (20120320/utaddress-251)
ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
ACPI Warning: 0x00000500-0x0000053f SystemIO conflicts with Region \GPIO 1 (20120320/utaddress-251)
ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Ipc_ich: Resource conflict(s) found affecting gpio_ich
...
rts_pstor: module is from the staging directory, the quality is unknown, you have been warned
..
[drm] No driver support for vblank timestamp query.
```


Here are screencaps (sry for crappy quality):
[http://i.imgur.com/CnzuF.jpg]("http://i.imgur.com/CnzuF.jpg")
[http://i.imgur.com/U8Qme.jpg]("http://i.imgur.com/U8Qme.jpg")
[http://i.imgur.com/Y5lcp.jpg]("http://i.imgur.com/Y5lcp.jpg")
[http://i.imgur.com/lNba5.jpg]("http://i.imgur.com/lNba5.jpg")
[http://i.imgur.com/PVnQ1.jpg]("http://i.imgur.com/PVnQ1.jpg")


Also it freezed now at "*stopping anac(h)ronistic cron"

---

### Post by lornlynx on 2012-12-01
Nvm, I installed now the 12.04 LTE version which seems to work.

My guess is that the 12.10 version just isn't compatible to some of the hardware of my netbook.

---

