---
title: "External (ntfs) HDD doesn't automount in Lucid (10.04)"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by drewsus on 2010-04-12
Hey all,

I just installed Lucid Beta 2 and I noticed that my external HDD (NTFS) does not automount when plugged into my Acer Aspire One. 
It worked fine in Karmic-- and this is on a fresh install of Lucid B2. 

Any ideas on how to fix this? 
ntfs-3g was installed by default and I tried installing ntfs-config as well. My 4GB USB pen drive mounts fine. 

Thanks in advance,
Drew

---

### Post by drewsus on 2010-04-12
Well, I added the mounter applet to a panel and it is showing that the HDD is plugged in, and I can choose to mount it from there, but its still not automounting. How might I fix this, preferebly without editing fstab

---

### Post by lisati on 2010-04-13
Moved to  Lucid Lynx Testing and Discussion

---

### Post by pedrogfrancisco on 2010-04-14
It isn't just NTFS. It's any external harddrive. And I'd say a USB as well isn't mounted.

---

### Post by cariboo on 2010-04-14
I just did a clean install from yesterdays daily build, I just checked, external drivers auto-mount here, and did before I did the reinstall.

What is the output of dmesg just after you plug your device in? Can you post the output in your next post, use this command:

```
dmesg | tail -n10
```

This will print out the last 10 lines of dmesg. You should see something that looks like this:

```
dmesg | tail -n10
[ 3135.861952] scsi 7:0:0:0: Direct-Access     Generic  External         1.03 PQ: 0 ANSI: 4
[ 3135.863567] sd 7:0:0:0: [sdg] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[ 3135.864493] sd 7:0:0:0: Attached scsi generic sg7 type 0
[ 3135.867449] sd 7:0:0:0: [sdg] Write Protect is off
[ 3135.867455] sd 7:0:0:0: [sdg] Mode Sense: 21 00 00 00
[ 3135.867459] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[ 3135.869926] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[ 3135.869936]  sdg: sdg1
[ 3135.893674] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[ 3135.893680] sd 7:0:0:0: [sdg] Attached SCSI disk
```

As you can see in the output above, my ntfs usb hard drive is seen as /dev/sdg1. If it didn't mount automagically, at least it could have been mounted manually eg:

```
sudo mount /dev/sdg1 /media
```

---

### Post by drewsus on 2010-04-14
so I ran: ```
dmesg | tail -n20
``` and this was the output:

```
[  600.987878] Initializing USB Mass Storage driver...
[  600.990047] scsi2 : SCSI emulation for USB Mass Storage devices
[  600.990787] usb-storage: device found at 3
[  600.990800] usb-storage: waiting for device to settle before scanning
[  600.990866] usbcore: registered new interface driver usb-storage
[  600.992524] USB Mass Storage support registered.
[  605.988426] usb-storage: device scan complete
[  605.989475] scsi 2:0:0:0: Direct-Access     MAXTOR S TM3500630AS           PQ: 0 ANSI: 2 CCS
[  605.994709] sd 2:0:0:0: Attached scsi generic sg1 type 0
[  605.998344] sd 2:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[  605.999331] sd 2:0:0:0: [sdb] Write Protect is off
[  605.999353] sd 2:0:0:0: [sdb] Mode Sense: 34 00 00 00
[  605.999368] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  606.013159] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  606.013178]  sdb: sdb1
[  606.034199] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  606.034225] sd 2:0:0:0: [sdb] Attached SCSI disk
[  614.112156] usb 1-3: reset high speed USB device using ehci_hcd and address 3
[  622.112127] usb 1-3: reset high speed USB device using ehci_hcd and address 3
[  653.100124] usb 1-3: reset high speed USB device using ehci_hcd and address 3
```

So there are 3 extra lines from mine, and the USB drive is present, but not mounted. So, its not a **big** deal, but it would be nice if it automounted. This specific model did in at least Jaunty-Karmic. Im not sure if I had it yet in Hardy.

---

### Post by Yarrgh on 2010-04-14
This was also posted here [http://ubuntuforums.org/showthread.php?t=1437344](http://ubuntuforums.org/showthread.php?t=1437344)

If doesn't get automounted its you can easily mount it by either typing in the command or go to the places menu, then computer. Just double click on the device and it'll mount it and open it.

I have the same problem with my 8.0 GB flash drive.

---

### Post by pedrogfrancisco on 2010-04-15
It doesn't automount and it doesn't appear on Dolphin's left panel to click on it and get Dolphin to mount.

I believe something is wrong with the hotplug system on my computer, as my USB 3G dongle modules sometimes aren't loaded when I plug it in after boot, but the pen works if plugged before booting.

---

### Post by dino99 on 2010-04-15
have you "usbmont" installed ?
MountManager might help you.

---

### Post by amano on 2010-04-15
Did you try to install the ntfs-config package? That installs a nice GUI that offers the option to automatically mount external drives. I  don't have one, thus I can just guess that this will work.

---

### Post by drewsus on 2010-04-15
> **amano said:**
> Did you try to install the ntfs-config package? That installs a nice GUI that offers the option to automatically mount external drives. I  don't have one, thus I can just guess that this will work.

I tried ntfs-config earlier on, but it put an entry in fstab and would not let me unmount the USB drive so I had to manually remove the entry from fstab and reboot.

[QUOTE=dino99]have you "usbmont" installed ?
MountManager might help you.[/QUOTE] 

MountManager seems to be installed by default, but usbmo**u**nt was not! So, I have installed that and now it just takes a lot longer to show up unmounted.... (I was really hoping this would work ha)

---

### Post by Yarrgh on 2010-04-15
I just barely updated to the lastest updates that were rolled out and for me my usb now automounts and opens automatically. Try updating your software and then try again.

---

### Post by drewsus on 2010-04-15
Just did a full update and restarted. Computer is still behaving the same as always. 
Still outputs "**reset high speed USB device using ehci_hcd and address 3**" x3 when "**dmesg | tail -n20**" is run in terminal.

---

### Post by pedrogfrancisco on 2010-04-16
Also not working.

```
[ 2944.270215] sr1: scsi-1 drive
[ 2944.273966] sd 10:0:0:0: Attached scsi generic sg3 type 0
[ 2944.274863] sd 10:0:0:0: [sdb] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[ 2944.276196] sd 10:0:0:0: [sdb] Write Protect is off
[ 2944.276201] sd 10:0:0:0: [sdb] Mode Sense: 34 00 00 00
[ 2944.276204] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 2944.278484] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 2944.278491]  sdb:
[ 2953.849484]  sdb1 sdb2 sdb3 sdb4 < sdb5 sdb6 >
[ 2953.898274] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 2953.898281] sd 10:0:0:0: [sdb] Attached SCSI disk
[ 2962.112187] usb 2-1: reset high speed USB device using ehci_hcd and address 7
[ 2970.100222] usb 2-1: reset high speed USB device using ehci_hcd and address 7

```

Reporting bug.

---

### Post by clhsharky on 2010-04-16
HI

Have you tried this

Ubuntu Script To Automatically Mount NTFS Drives On Startup
[http://www.webupd8.org/2010/04/ubuntu-script-to-automatically-mount.html](http://www.webupd8.org/2010/04/ubuntu-script-to-automatically-mount.html)

Sharky

---

### Post by drewsus on 2010-04-17
No clhsharky, thats not really what I am looking for, but thanks. Thats more for internal HDDs. 

The fact of the matter is that this should (and has for a long while - at the very least back to 8.04, and even before that iirc) work right out of the box. 

Further points of interest, I was using my roommates external HDD and it has 4 partitions. 3 are fat32 and one is NTFS. The 3 fat32 mounted automatically and the NTFS did not. 

Again, SD cards and USB mount automatically, but I am sure that is because they are fat32.

---

### Post by smdeep on 2010-04-17
This seems to fix the error for me:

[https://bugs.launchpad.net/oem-priority/+bug/548513/comments/20](https://bugs.launchpad.net/oem-priority/+bug/548513/comments/20)

---

### Post by drewsus on 2010-04-17
> **smdeep said:**
> This seems to fix the error for me:

[https://bugs.launchpad.net/oem-priority/+bug/548513/comments/20](https://bugs.launchpad.net/oem-priority/+bug/548513/comments/20)

I read through comment #20 from that bug report and I was ready to implement the suggested workaround, but decided to read all the comments first. 

Comment #44 from Bug #548513:
[QUOTE=Launchpad Janitor  wrote on 2010-04-16]

This bug was fixed in the package hdparm - 9.15-1ubuntu8

---------------
hdparm (9.15-1ubuntu8) lucid; urgency=low

  * Don't apply default APM policy to Firewire or USB devices when running
    from udev (LP: #515023, #548513).
 -- Colin Watson <cjwatson@ubuntu.com> Fri, 16 Apr 2010 16:19:29 +0100
[/QUOTE]

So, it seems the bug was fixed lastnight. 
I checked and my external NTFS USB drive is auto mouting. 

Thanks for all the help people!

--Marking as solved--

---

### Post by dubski on 2010-04-19
You guys rock.  That great.  Fix it for me.  Although shouldn't this be automatic?

---

### Post by pedrogfrancisco on 2010-04-20
My problem was [#548513]("https://bugs.launchpad.net/ubuntu/lucid/+source/hdparm/+bug/548513"). Fixed.

---

