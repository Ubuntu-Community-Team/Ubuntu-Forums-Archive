---
title: "Ubuntu 11.04 will not work with my USB HDD"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by TerryT on 2011-06-14
I have an external USB HDD enclosure (Rocketfish USB 3.0 2.5" SATA) with a 350GB hard drive installed. The device is detected and operates fine on Windows 7, OS X, and other Linux installations that I've tried (Ubuntu 10.04 and Debian 6 live). However, it does not work on two different Ubuntu 11.04 installations. I get the following sort of syslog entries:

usb 2-1.2: new high speed USB device using ehci_hcd and address 7 scsi10 : uas
scsi 10:0:0:0: Direct-Access     SYMWAVE  HITACHI HTS72503 C70F PQ: 0 ANSI: 4
scsi 10:0:0:0: uas_eh_abort_handler tag 0
scsi 10:0:0:0: uas_eh_device_reset_handler tag 0
scsi 10:0:0:0: uas_eh_target_reset_handler tag 0
scsi 10:0:0:0: uas_eh_bus_reset_handler tag 0
usb 2-1.2: reset high speed USB device using ehci_hcd and address 7
scsi 10:0:0:0: Device offlined - not ready after error recovery
scsi 10:0:0:0: rejecting I/O to offline device
scsi 10:0:0:0: rejecting I/O to offline device

This is using kernel 2.6.38-8-generic x86_64. Any help would be much appreciated.

Thanks,
Terry

---

### Post by dabl on 2011-06-14
What filesystem are you using?

---

### Post by TerryT on 2011-06-14
It is formatted as FAT32.

Here is the full syslog entry:

usb 2-1.2: new high speed USB device using ehci_hcd and address 4
scsi7 : uas
scsi 7:0:0:0: Direct-Access     SYMWAVE  HITACHI HTS72503 C70F PQ: 0 ANSI: 4
scsi 7:0:0:0: uas_eh_abort_handler tag 0
scsi 7:0:0:0: uas_eh_device_reset_handler tag 0
scsi 7:0:0:0: uas_eh_target_reset_handler tag 0
scsi 7:0:0:0: uas_eh_bus_reset_handler tag 0
usb 2-1.2: reset high speed USB device using ehci_hcd and address 4
scsi 7:0:0:0: Device offlined - not ready after error recovery
scsi 7:0:0:0: rejecting I/O to offline device
scsi 7:0:0:0: rejecting I/O to offline device
scsi 7:0:0:1: Enclosure         SYMWAVE  SES              C70F PQ: 0 ANSI: 4
scsi 7:0:0:2: uas_sense_old: urb length 26 disagrees with IU sense data length 510, using 18 bytes of sense data
sd 7:0:0:0: Attached scsi generic sg1 type 0
ses 7:0:0:1: Attached Enclosure device
ses 7:0:0:1: Attached scsi generic sg2 type 13
sd 7:0:0:0: uas_eh_abort_handler tag 0
sd 7:0:0:0: uas_eh_device_reset_handler tag 0
sd 7:0:0:0: uas_eh_target_reset_handler tag 0
sd 7:0:0:0: uas_eh_bus_reset_handler tag 0
usb 2-1.2: reset high speed USB device using ehci_hcd and address 4
sd 7:0:0:0: Device offlined - not ready after error recovery
sd 7:0:0:0: rejecting I/O to offline device
sd 7:0:0:0: rejecting I/O to offline device
sd 7:0:0:0: rejecting I/O to offline device
sd 7:0:0:0: [sdb] READ CAPACITY failed
sd 7:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
sd 7:0:0:0: [sdb] Sense not available.
sd 7:0:0:0: rejecting I/O to offline device
sd 7:0:0:0: [sdb] Write Protect is off
sd 7:0:0:0: [sdb] Mode Sense: 00 00 00 00
sd 7:0:0:0: rejecting I/O to offline device
sd 7:0:0:0: [sdb] Asking for cache data failed
sd 7:0:0:0: [sdb] Assuming drive cache: write through
sd 7:0:0:0: [sdb] Attached SCSI disk

At this point, /dev/sdb[x] cannot be accessed.

---

### Post by dabl on 2011-06-16
> **TerryT said:**
> It is formatted as FAT32.



Ehh -- the most fragile filesystem of them all.

Any chance that you could change it to ext4, or even NTFS?

> 

usb 2-1.2: reset high speed USB device using ehci_hcd and address 4
sd 7:0:0:0: Device offlined - not ready after error recovery
sd 7:0:0:0: rejecting I/O to offline device


There is where it comes off the tracks.  Not sure why -- probably would have to research that Hitachi device.

---

### Post by TerryT on 2011-06-16
Hi,

The problem is not with the filesystem on the drive. The same thing happens regardless of what filesystem is there. It is at a lower level with the USB driver subsystem.

After searching and reading, it appears to me that there has been a regression in the Linux kernel/USB driver ability to handle certain USB HDD devices. In my case, if I plug this drive into any system with kernel 2.6.32, it is detected and mounted fine. So somewhere between kernel 2.6.32 and 2.6.38 (Ubuntu 11.04), this compatibility has regressed. It is also not specific to Ubuntu, e.g., if I boot an earlier live version of Fedora everything is fine. But Fedora 15 (with kernel 2.6.38 ) also fails to mount this drive.

I should file a bug report on this, if anyone can tell me where I should do that it would be much appreciated.

Thanks,
Terry

---

### Post by Petr123 on 2011-07-28
After installing Ubuntu 11.04 I discovered I was not able to mount my external HDD with USB interface. I have solved the problem by not permitting umount to call smart test for this disc. I did the following steps:

1. I have copied the file 80-udisks.rules form the directory /lib/udev/rules.d to the directory /etc/udev/rules.d.

2. I have commented out the following lines in the file /etc/udev/rules.d/80-udisks.rule:

128: KERNEL=="sd*[!0-9]", ATTR{removable}=="0", ENV{ID_BUS}=="usb", ENV{DEVTYPE}=="disk", IMPORT{program}="udisks-probe-ata-smart $tempnode"

131: KERNEL=="sd*[!0-9]", ATTR{removable}=="0", ENV{ID_BUS}=="ata", ENV{DEVTYPE}=="disk", IMPORT{program}="udisks-probe-ata-smart $tempnode"

134: KERNEL=="sd*[!0-9]", ATTR{removable}=="0", ENV{ID_BUS}=="scsi", ENV{DEVTYPE}=="disk", ENV{ID_VENDOR}=="ATA", IMPORT{program}="udisks-probe-ata-smart $tempnode"

The rules in the directory /etc/udev/rules.d override the/lib/udev/rules.d. rules in the directory /lib/udev/rules.d. It is recommended not to edit anything in  /lib/udev/rules.d and to put personal rules into  /etc/udev/rules.d. 

I had the same problem with Ubuntu 10.10 and the same solution was used.

Petr.

---

### Post by Petr123 on 2011-08-02
I tested this solution on two X64 Athlon computers with Suse 11.3 and Suse 11.4 respectively. It works.

Petr.

---

### Post by wrin on 2011-08-11
This did not work for me.  dmesg shows:

> [38528.084160] usb 2-4: new high speed USB device using ehci_hcd and address 5
[38528.225826] scsi5 : uas
[38531.687200] scsi 5:0:0:0: Direct-Access     SYMWAVE  FUJITSU MHW2120B 001C PQ: 0 ANSI: 4
[38538.016105] scsi 5:0:0:0: uas_eh_abort_handler tag 0
[38538.016120] scsi 5:0:0:0: uas_eh_device_reset_handler tag 0
[38538.016127] scsi 5:0:0:0: uas_eh_target_reset_handler tag 0
[38538.016134] scsi 5:0:0:0: uas_eh_bus_reset_handler tag 0
[38538.128204] usb 2-4: reset high speed USB device using ehci_hcd and address 5
[38538.261381] scsi 5:0:0:0: Device offlined - not ready after error recovery
[38538.261458] scsi 5:0:0:0: rejecting I/O to offline device
[38538.261479] scsi 5:0:0:0: rejecting I/O to offline device
[38538.263039] scsi 5:0:0:1: Enclosure         SYMWAVE  SES              001C PQ: 0 ANSI: 4
[38538.263209] scsi 5:0:0:2: uas_sense_old: urb length 26 disagrees with IU sense data length 510, using 18 bytes of sense data
[38538.263786] sd 5:0:0:0: Attached scsi generic sg2 type 0
[38538.264062] ses 5:0:0:1: Attached Enclosure device
[38538.264233] ses 5:0:0:1: Attached scsi generic sg3 type 13
[38569.056078] sd 5:0:0:0: uas_eh_abort_handler tag 0
[38569.056093] sd 5:0:0:0: uas_eh_device_reset_handler tag 0
[38569.056101] sd 5:0:0:0: uas_eh_target_reset_handler tag 0
[38569.056108] sd 5:0:0:0: uas_eh_bus_reset_handler tag 0
[38569.168218] usb 2-4: reset high speed USB device using ehci_hcd and address 5
[38569.301900] sd 5:0:0:0: Device offlined - not ready after error recovery
[38569.302032] sd 5:0:0:0: rejecting I/O to offline device
[38569.302055] sd 5:0:0:0: rejecting I/O to offline device
[38569.302068] sd 5:0:0:0: rejecting I/O to offline device
[38569.302078] sd 5:0:0:0: [sdb] READ CAPACITY failed
[38569.302084] sd 5:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[38569.302094] sd 5:0:0:0: [sdb] Sense not available.
[38569.302107] sd 5:0:0:0: rejecting I/O to offline device
[38569.302118] sd 5:0:0:0: [sdb] Write Protect is off
[38569.302125] sd 5:0:0:0: [sdb] Mode Sense: 00 00 00 00
[38569.302135] sd 5:0:0:0: rejecting I/O to offline device
[38569.302145] sd 5:0:0:0: [sdb] Asking for cache data failed
[38569.302151] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[38569.302558] sd 5:0:0:0: [sdb] Attached SCSI disk

I don't know what else to do.  :(

---

### Post by wrin on 2011-09-26
Is this issue still being looked at?  It still doesn't work for me and I'm really terrible at troubleshooting linux stuff.

---

### Post by alzmich on 2011-10-04
Hi all,

i have exactly the same issue - no idea what could be wrong and how to solve it.
 - the problem exists with ubuntu server 11.04 with kernel 2.6.38-11-server #48-Ubuntu  and #50-Ubuntu.

everytime i attach my external usb disk i get:

[   52.483491] usb 2-1.1: new high speed USB device using ehci_hcd and address 4
[   52.635780] scsi8 : uas
[   52.635896] usbcore: registered new interface driver uas
[   52.639492] Initializing USB Mass Storage driver...
[   52.639526] usbcore: registered new interface driver usb-storage
[   52.639527] USB Mass Storage support registered.
[   56.487174] scsi 8:0:0:0: Direct-Access     Hitachi  Touro Mobile Pro A0D0 PQ: 0 ANSI: 4
[   63.157225] scsi 8:0:0:0: uas_eh_abort_handler tag 0
[   63.157232] scsi 8:0:0:0: uas_eh_device_reset_handler tag 0
[   63.157235] scsi 8:0:0:0: uas_eh_target_reset_handler tag 0
[   63.157238] scsi 8:0:0:0: uas_eh_bus_reset_handler tag 0
[   63.237329] usb 2-1.1: reset high speed USB device using ehci_hcd and address 4
[   63.378749] scsi 8:0:0:0: Device offlined - not ready after error recovery
[   63.378835] scsi 8:0:0:0: rejecting I/O to offline device
[   63.378840] scsi 8:0:0:0: rejecting I/O to offline device
[   63.380112] scsi 8:0:0:1: Enclosure         Hitachi  SES              A0D0 PQ: 0 ANSI: 4
[   63.380340] scsi 8:0:0:2: uas_sense_old: urb length 26 disagrees with IU sense data length 510, using 18 bytes of sense data
[   63.380515] sd 8:0:0:0: Attached scsi generic sg3 type 0
[   63.380615] scsi 8:0:0:1: Attached scsi generic sg4 type 13


interestingly - same hardware other OS (opensuse 11.4 live, or self compiled gentoo - 2.6.38 kernel) - disk is working perfectly.

Any hint?
In my opinion it must have something to do with the ehci / ohci kernel modules...

Maybe someone already solved it?

Thanx.

---

### Post by alzmich on 2011-10-05
Hi,

i also tried another ubuntu-kernel:

2.6.39-02063904-generic.

Problem is still the same....

---

### Post by mjuchli on 2011-10-10
I can confirm that Petr123's solution works on Ubuntu 10.10 x64 with kernel 2.6.35-30-generic. Thanks Petr!

Hopefully the bug is fixed soon so I can get my SMART monitoring back. :(

Edit:
My disk is a Hitachi Touro and the syslog entry is:
[  173.312108] scsi 6:0:0:0: Direct-Access     Hitachi  HDS721010CLA332       PQ: 0 ANSI: 2 CCS

Seems to be a problem with Hitachi controllers?

---

### Post by alzmich on 2011-10-10
Hi,
unfortunately not for me...
tried petr123's solution, no success.

root@host:~# cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

I'm thinking going back to gentoo or other dist on my desktop machines. Have also problems with dhcp switching between networks (home and office) - my resolv.conf never gets written correctly, only if i execute "dhclient" manually after getting an login prompt which makes the use of autohome very difficult :)

---

### Post by Dire NTropy on 2011-10-10
Hi,
I'm also having this problem. I tried Petr123's solution and dmesg outputs:

'sense urb submission failure'
'sense urb submission failure'
'sense urb submission failure'
...

The HDD works in Windows 7.

Thanks!

edit:
Using Kernel: 2.6.38-11
Tried on both 32 and 64 bit 11.04 installations.

---

### Post by mjuchli on 2011-10-11
I just re- enabled the "usb", "ati", and "scsi" lines in /etc/udev/rules.d/80-udisks.rules one at a time and rebooted for each one to see if I could get any SMART reports without breaking the Hitachi. Here are the results:


[LIST=1]
[*]Uncommented "usb" line: Hitachi still worked and showed SMART status healthy in Disk Utility. 3 internal drives had no status.
[*]Uncommented "usb" and "ata" lines: Hitachi still worked and all disks including internal ones showed SMART status healthy.
[*]Uncommented "usb" and "ata" and "scsi" lines: Everything still worked.
[/LIST]

I'm not sure what is going on but all problems are fixed but I don't seem to have done anything since I reversed all my changes. :confused:

---

### Post by alzmich on 2011-10-12
only for information:

tried 5 minutes ago a ubuntu 10.10 test system in my company - there the Harddisk is working...

so seems only a problem with ubuntu 11.04...

---

### Post by alzmich on 2011-10-12
ok, seems to found the reason!
 - not really a solution but a workaround.

it seems to be a kernel module called "uas"
 - so i putted the module in the blacklist.conf
not it works fine... can attach the disk and got be mounted automaticly...

```
root@k:~# more /etc/modprobe.d/blacklist.conf 
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

blacklist uas
```I'll verify it the next few days...

---

### Post by edoapra on 2011-10-12
"rmmod uas" does the trick for me

---

### Post by edoapra on 2011-10-12
Sorry for the duplicate, I have missed Alzmich's update

---

### Post by wrin on 2011-10-17
Alright, for me all of the solutions at once work...sort of.  I have the lines commented out in the rules file, and I have blacklist uas in my config file, but I still have to rmmod uas whenever I boot or it won't work.  It's a great temporary solution because I can use my drive again, but what the heck is going on?

Edit/Update: I finally got mine to work.  There's a bit of a hardware problem in addition to the software strangeness, but basically what did it for me was to "sudo rmmod uas" then blacklist it ala [alzmich]("http://ubuntuforums.org/member.php?u=1167185")'s suggestion above (post 17).  The 80-udisks.rules fix was unnecessary for me.

---

### Post by loverush on 2011-10-24
It works for me with ---> blacklist uas
thank you alzmich!!

---

### Post by alzmich on 2011-10-25
this works stable now for 2 weeks.. - but should be checked by some developers - it looks like a real problem with the uas kernel module...

> **alzmich said:**
> ok, seems to found the reason!
 - not really a solution but a workaround.

it seems to be a kernel module called "uas"
 - so i putted the module in the blacklist.conf
not it works fine... can attach the disk and got be mounted automaticly...

```
root@k:~# more /etc/modprobe.d/blacklist.conf 
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

blacklist uas
```I'll verify it the next few days...

---

### Post by t98907 on 2011-11-19
Thanks, alzmich!

---

### Post by fadyek on 2011-11-28
alzmich you rock! I spent a few days trying to get my Ubuntu to read my Hitachi Touro Desk Pro 3TB. Now I can finally use it thanks to you!

---

### Post by Pimmetje on 2012-02-10
THX ALL (after a few hours of searching :D)

#rmmod uas did it for me (for google other errors i  got)
Test WP failed, assume Write Enabled
reset high speed USB device using ehci_hcd and address 13

EDIT:
I cheered too quickly it solved partly the problem.

---

