---
title: "Unable to boot Ubuntu"
date: 2022-08-27
forum: Installation &amp; Upgrades
---

### Post by pankajrai87 on 2022-08-27
I could not boot into Ubuntu 20.04 after I tried to resize a partition using Ubuntu 22.04 live USB. I tried the [ Boot repair ]("https://help.ubuntu.com/community/Boot-Repair") using live USB, but had no success. The Boot-info is available at [https://paste.ubuntu.com/p/Q2XMFcr3h2/](https://paste.ubuntu.com/p/Q2XMFcr3h2/). 
I want to ask what should I try next.
Thanks

---

### Post by yancek on 2022-08-27
Line 34 of boot repair shows an entry for Linpus Lite, is this an Acer computer?  Line 15 tells the whole story.   Boot repair did not detect 'any' OS so apparently everything is gne.  Did you download the boot repair iso file and put it on a USB.  You might be better off using the 2nd option on the boot repair page from the live Ubuntu usb as it is generally more up to date.  It may not make any difference though.

It seems you deleted anything on the computer..  Beginning at line 34, it shows the EFI entries which include only Linpus and windows, no sign of Ubuntu.  What exactly did you try to do and how did you try to do it?  Was the partition you were trying to resize on windows?  Did you ever have Ubuntu or any Linux OS installed?  If it was a windows partition, you would be better off resizing it using windows Disk Management.

---

### Post by pankajrai87 on 2022-08-27
1. This is not an Acer laptop, this is a Lenovo V15 laptop which came with DOS. 
2. Yes, I did download the boot repair iso file and made a live USB.
3. There was no windows or dual boot on the system, there was just Ubuntu 20.04.
4. I was trying to resize the root partition using a Ubuntu 22.04 USB.
Correction: In the post I had mentioned ubuntu 20.04 USB, it was 22.04. I have corrected the post.
Is there anything I can try apart from live Ubuntu USB, if not, is there a way I can save the data from the drive.

---

### Post by tea for one on 2022-08-27
> **pankajrai87 said:**
> Is there anything I can try apart from live Ubuntu USB, if not, is there a way I can save the data from the drive.

As a final check, boot into a live session and run 
```
sudo parted -l
```
Post the output in code tags for legibility.

From the boot-repair report, where no partitions were found, it looks like a re-installation and restore from backup is the next step.

---

### Post by yancek on 2022-08-27
>   There was no windows or dual boot on the system, there was just Ubuntu 20.04. 

Is this a used computer?  Lines 34 and 35 show BIOS EFI boot entries for Linpus Lite and Windows which would indicate both were installed at some point.  Whatever you did from the Ubuntu live USB seems to have deleted everything.  Post the output of parted -l and see what that shows.  The only software that I am aware of that might be able to recover the data is TestDisk.  I put a link below so make sure you read the instructions under Documentation as it is not simple to use.  There is a link on that page for Step by Step instructions.

[https://www.cgsecurity.org/wiki/TestDisk](https://www.cgsecurity.org/wiki/TestDisk)

---

### Post by oldfred on 2022-08-27
In UEFI settings, is another drive shown?

Did you also do an UEFI/BIOS update and that reset UEFI settings to defaults.
That may make drive disappear, as you have to redo the settings you originally changed.

---

### Post by pankajrai87 on 2022-08-28
I have not made any BIOS update.

---

