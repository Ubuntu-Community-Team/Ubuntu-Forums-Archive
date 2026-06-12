---
title: "Windows 7 won't boot after cloning drive"
date: 2012-05-19
forum: Installation &amp; Upgrades
---

### Post by Rbgtag on 2012-05-19
Hey all...

BTW...you all are the smartest people I know.  Does flattery get me anywhere???

I have a new Asus N73sv...has a 750G hard drive.  I used ddrescue to clone my previous hd to the new hardrive on the new laptop.  I can boot into Ubuntu just fine, but when I try to load windows 7, it flashes a BSOD and then reboots.  

The new drive already had windows installed, but I just used -f to overwrite the drive...now I have something like 8 partitions on my drive where the original drive had two.  I still cannot boot windows...need some help...

Here is the copy of my bootscript text...I attached it...

Thanks,

Scott

---

### Post by darkod on 2012-05-19
If the sata mode of your old machine was IDE and on the new AHCI, win7 will not work.

In theory, it can't work if you change the sata mode once it's installed.

In practice, I believe there was a value you can change in the registry so it can accept the AHCI.

Go into the bios first and set sata mode to IDE, then try to boot windows.

Although it's very odd your old computer to be in IDE for win7, usually you would do that for XP.

---

### Post by Rbgtag on 2012-05-19
> **darkod said:**
> If the sata mode of your old machine was IDE and on the new AHCI, win7 will not work.

In theory, it can't work if you change the sata mode once it's installed.

In practice, I believe there was a value you can change in the registry so it can accept the AHCI.

Go into the bios first and set sata mode to IDE, then try to boot windows.

Although it's very odd your old computer to be in IDE for win7, usually you would do that for XP.

I did see that option and I thought I tried that, but I will give it a go again.  I also saw when I tried to re-install windows 7 that it said there was an installation on D drive.  Any way to get that on the C:?  Could that be the issue.

---

### Post by Lisiano on 2012-05-19
You can switch to AHCI (SATA) once you install those drivers separately on Win7. For now return to ATA (IDE) to get it to boot.

Tip to see the BSOD error, hold F8 (If you get beeps, rapidly press it instead) while booting and select something along the lines of "Do not reboot on failure" or something. Don't use English Windows.

---

### Post by Rbgtag on 2012-05-19
> **Lisiano said:**
> You can switch to AHCI (SATA) once you install those drivers separately on Win7. For now return to ATA (IDE) to get it to boot.

Tip to see the BSOD error, hold F8 (If you get beeps, rapidly press it instead) while booting and select something along the lines of "Do not reboot on failure" or something. Don't use English Windows.

Switched to IDE mode...still same result.

BSOD says...

A problem has been detected and windows has been shut down to prevent damage to your computer.

If this is the first time you've seen this stop error screen, restart your computer.  If this screen appears again, follow these steps:

Check for viruses on your computer.  Remove any newly installed hard drives or hard drive controllers.  Check your hard drive to make sure it is properly configured and terminated.  Run chkskd /f to check for hard drive corruption, and then restart your computer.

Technical information:
*** Stop: 0x0000007B (0x80786A58, 0xc0000034, 0x00000000, 0x00000000)

I still think it is an issue with the partitions, but don't know how to fix it.

Thanks again,

Scott

---

### Post by oldfred on 2012-05-19
>     Boot files:        /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD

Windows is not case sensitive like Linux. So you have two bootmgr and 6 BCDs. Windows gets confused as it does not know which is which as they are all identical to Windows. Make backups and test all the combinations with one bootmgr and one /boot/BCD. One combination may work or at least get you to where you can repair it.

---

### Post by Rbgtag on 2012-05-19
> **oldfred said:**
> Windows is not case sensitive like Linux. So you have two bootmgr and 6 BCDs. Windows gets confused as it does not know which is which as they are all identical to Windows. Make backups and test all the combinations with one bootmgr and one /boot/BCD. One combination may work or at least get you to where you can repair it.

How would I go about testing each combination?  Should I just reformat and clone the disk again with ddrescue?

---

### Post by Lisiano on 2012-05-19
Copy off the bootmgrs and bcds to a flash drive (Or Ubuntu (One)) and try different ones, first test the lowercase ones.

---

### Post by darkod on 2012-05-19
You said in your post the new disk had windows and you just used -f to overwrite it.

I don't know that procedure exactly, but I think this is where you went wrong. You should have formatted the destination windows partition and only then copy the backup.

Linux makes difference between capitals and small letters, so by writing the backup on a none-empty partition it might have duplicated much more files than just the boot files.

I would say a much better choice, if you still have that backup, is to format the partition this time and copy the backup again.

Why wouldn't you format the partition and start clean, instead risking doubling up some (or many) files?

---

### Post by Rbgtag on 2012-05-20
> **darkod said:**
> You said in your post the new disk had windows and you just used -f to overwrite it.

I don't know that procedure exactly, but I think this is where you went wrong. You should have formatted the destination windows partition and only then copy the backup.

Linux makes difference between capitals and small letters, so by writing the backup on a none-empty partition it might have duplicated much more files than just the boot files.

I would say a much better choice, if you still have that backup, is to format the partition this time and copy the backup again.

Why wouldn't you format the partition and start clean, instead risking doubling up some (or many) files?

I know you are right...partially because the new drive came with backup partition with the new operating system on it and I could not get the recovery disks to copy, so I was trying to work around them.  You are right, that probably screwed me up.  I will give that a go as well.

Thanks

---

