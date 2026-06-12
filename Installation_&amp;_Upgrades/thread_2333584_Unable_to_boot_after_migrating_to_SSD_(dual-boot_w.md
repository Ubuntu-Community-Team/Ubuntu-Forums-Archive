---
title: "Unable to boot after migrating to SSD (dual-boot with windows)"
date: 2016-08-11
forum: Installation &amp; Upgrades
---

### Post by bomberb17 on 2016-08-11
Initially I had windows 10 + ubuntu 16.04 LTS on a 1TB hdd on my UEFI laptop. The disk was GPT (not MBR) and I was booting using grub.
I migrated my whole disk to a smaller (250GB) SSD, by resizing and moving all partitions to the beginning.
However, after connecting the new disk, I don't get the grub boot loader screen but I get a blue windows screen with the message:
> Recovery

Your PC/Device needs to be repaired

The application or operating system could not be loaded because a required file is missing or contains errors.

File: \windows\system32\boot\winload.exe
Error code: 0xc0000225

You'll need to use recovery tools.


Press Enter to try again.
Press F8 for Startup settings.

I tried Boot-Repair, but it didn't do any good, here's the output: [http://paste2.org/dhtIsJMV](http://paste2.org/dhtIsJMV)
How can I fix this?

---

### Post by oldfred on 2016-08-11
If just Windows boot issue, then you left Windows fast start up on which is hibernation. Grub will not boot hibernated or NTFS needing chkdsk. 
Try booting Windows from UEFI, not from grub and turn off fast start up.
       Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html) 

[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)

With gpt, you have GUID for each partition, in each partition and in the partition table at beginning of drive and at end of drive in backup partition table.
Changing to smaller drive may be the issue.

I would first see what gdisk says. It may just need the w write to repair everything.
       sudo gdisk -l /dev/sda

 repair gpt:
[URL="http://www.rodsbooks.com/gdisk/repairing.html"]http://www.rodsbooks.com/gdisk/repairing.html
      [/URL]sudo gdisk /dev/sda
Command (? for help): 
     Use gdisk and verify partitions are correct with p, or v to review issues,  and use w to write the partition table. If not correct just use q to quit. That should update primary, backup & protective MBR.  [URL="http://www.rodsbooks.com/gdisk/repairing.html"]
[/URL]

---

