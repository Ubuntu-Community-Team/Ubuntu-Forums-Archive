---
title: "Windows crashed, tried to run Ubuntu to recover my files..."
date: 2011-12-16
forum: Installation &amp; Upgrades
---

### Post by shaq237 on 2011-12-16
Hello,

Yesterday after I installed some Windows updates my computer shut down. When I restarted, it went to a System Recovery screen. The System Recovery says 

Problem Event Name: StartupRepairOffline
Problem Signature 01: 0.0.0.0
Problem Signature 02: 0.0.0.0
Problem Signature 03: unknown
Problem Signature 04: 0
Problem Signature 05: unknown
Problem Signature 06: 1
Problem Signature 07: unknown
OS Version: 6.1.7600.2.0.0.256.1
Locale ID: 1033

I can't get into Windows Safe Mode. I burned Ubuntu onto a CD and  went to try Ubuntu without any change to your computer. It isn't finding my hard drive. I am trying to recover my documents, music and pictures from my hard drive. What am I doing wrong?

The computer is a Dell and I was running Windows 7.

Thanks so much for the help.

---

### Post by BC59 on 2011-12-16
First priority is to save your files.

From a Live CD is not so obvious where is the HDD. You should check the top of the left panel, Devices, for any name with numbers.

If not, open a terminal with CTRL+ALT+T and paste those 2 commands:

```
sudo parted /dev/sda print
sudo fdisk -l
```

Then post the result.

---

### Post by BC59 on 2011-12-16
To recover your Windows installation, download a Windows 7 .iso from here:

[http://www.mydigitallife.info/windows-7-iso-x86-and-x64-official-direct-download-links-ultimate-professional-and-home-premium/](http://www.mydigitallife.info/windows-7-iso-x86-and-x64-official-direct-download-links-ultimate-professional-and-home-premium/)

and burn it to a DVD. Then boot and follow the instructions:

[http://windows.microsoft.com/en-US/windows7/Start-your-computer-from-a-Windows-7-installation-disc-or-USB-flash-drive](http://windows.microsoft.com/en-US/windows7/Start-your-computer-from-a-Windows-7-installation-disc-or-USB-flash-drive)

---

### Post by shaq237 on 2011-12-17
I have the Windows 7 Reinstallation DVD but System Restore doesn't work and Memory Diagnostics isn't picking up any errors. When I try the System Repair through the Windows 7 Reinstallation DVD I also get some kind of error.

These are the results of those 2 commands...

[IMG]http://i3.photobucket.com/albums/y60/shaq237/2011-12-17_00-06-54_588.jpg[/IMG]
[IMG]http://i3.photobucket.com/albums/y60/shaq237/2011-12-17_00-07-13_964.jpg[/IMG]

Thanks for the help so far.

---

### Post by BC59 on 2011-12-17
Looks like Windows is still there. Retry with System Repair at least 3 times. Did you manage to save your data through Ubuntu?

---

### Post by lisati on 2011-12-17
The command is **fdisk -l** with a small L. :D

---

### Post by shaq237 on 2011-12-23
Sorry, I was away for a few days. I am still unable to access the files through Ubuntu. System Repair also isn't working. It just restarts my computer but doesn't repair anything. 

I re-ran the second command, screen shot attached.

---

### Post by BC59 on 2011-12-23
Boot from the Live Cd you have. From Ubuntu now open a nautilus which is the Ubuntu file explorer. From the upper left pane Devices click on the devices existing. One of them is the Windows partition. From there you can backup your files.

---

### Post by shaq237 on 2011-12-23
When I go to devices all I see is something called OS. There isn't really anything inside that. Does this mean that I won't be able to get into my hard drive?

---

### Post by darkod on 2011-12-23
> **shaq237 said:**
> When I go to devices all I see is something called OS. There isn't really anything inside that. Does this mean that I won't be able to get into my hard drive?

It definitely doesn't sound good. All partitions ubuntu can discover are listed under Devices. If you had a name set up, the name of the partition would be there. If not, it might say like 500GB filesystem, or similar.

But the point is, if it can discover it correctly, it should be there.

Try to mount it manually, just to see what happens. In terminal:

sudo ntfs-3g /dev/sda3 /mnt
ls /mnt

If the second command can list the files/folders, there is hope.

If it still continues not recognizing it, you can try testdisk to scan the disk for it:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

