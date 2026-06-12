---
title: "Dual booting Ubuntu 12.10 and Windows 8"
date: 2013-01-05
forum: Installation &amp; Upgrades
---

### Post by Bowen369 on 2013-01-05
Hello,

I've recently bought a new laptop: HP DV6 7295ex, with a pre-installed version of Windows 8 (64 bits).

After installing Ubuntu 12.10 (64 bits) and running Boot-Repair (separate boot partition: /dev/sda6), I could boot to Ubuntu but not to Windows (incorrect entries: errors related to drivemap and incorrect EFI path). I've tried to manually add a couple of entries, but to no avail.

Note that everything is UEFI (firmware, Windows and Ubuntu installations), and I disabled SecureBoot from the BIOS.

I tried once to create a new Microsoft/Boot/ folder in /boot/efi, and manually added bootmgfw.efi in that folder (I copied it from [Windows partition]/Windows/Boot/EFI/). That added an entry to Grub, which led me to a Windows 8 error page (error code 0x00000f, files corrupted or not found, don't remember).

Link to Boot-Repair log: [http://paste.ubuntu.com/1499991/](http://paste.ubuntu.com/1499991/)
I have also attached a screenshot of gparted below.

Does anybody know what's wrong with my setup, and how to fix it?

---

### Post by YannBuntu on 2013-01-05
Hi
you don't have any Windows EFI files, which means:
- either your Windows has been installed in Legacy mode
- or you have deleted the EFI partition by mistake.

I would recommend:
1) set up your BIOS in Legacy (not UEFI) mode
2) run Boot-Repair's Recommended Repair. Indicate the new URL that will appear if any problem.

---

### Post by Bowen369 on 2013-01-05
New URL: [http://paste.ubuntu.com/1500222/](http://paste.ubuntu.com/1500222/)

Enabled Legacy mode, ran Boot-Repair, and restarted:

```
error: file `/grub/x86_64-efi/normal.mod` not found.
grub rescue>
```

And that's normal, because UEFI has precedence over Legacy boot.
So restarted again, this time hitting F9 and changing boot to start from hard drive.

Both Windows entries displayed this error:

```
Windows Boot Manager: Windows failed to start.
File: \Boot\BCD
Status: 0xc000000e
Info: The Boot Configuration Data for your PC is missing or contains errors
```

Although Ubuntu still runs fine.

---

### Post by YannBuntu on 2013-01-05
ok
1) use a Windows disc this way: [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader) until you get direct access to Windows
2) then use Boot-Repair to recover your GRUB menu

if still not good, switch to the other mode (Legacy/ or UEFI), then redo 1) then 2)

---

### Post by oldfred on 2013-01-05
Because you have gpt partitions, Windows will only boot in UEFI mode. So it looks like you deleted the efi partition that probably was sda2 and the Microsoft Reserved partition that as probably sda3. Microsoft requires the MSR to be just before main install or c: "drive". 

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)


You may be able to create the correct partitions. efi partition is supposed to be first per UEFI, but Windows makes it second which works. But if creating new efi partition be sure to delete old one and move "boot" flag to new one. Boot flag in UEFI only means it is the efi partition.


       
 Windows UEFI install should  have backup of bootmgrw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

---

### Post by Bowen369 on 2013-01-05
Thank you for the links.
So I suppose I should skip trying to fix it with a recovery disk, and instead try to restore the correct partitionning?

If so, I could really use some help:

> **oldfred said:**
> 
You may be able to create the correct partitions. efi partition is supposed to be [COLOR="Red"]first per UEFI[/COLOR], but Windows makes it second which works. But if creating new efi partition be sure to delete old one and move "boot" flag to new one. Boot flag in UEFI only means it is the efi partition.

(Didn't quite understand what's quoted in red).
I'm not sure how to proceed.

I do have the bootmgfw.efi here: C:\Windows\Boot\EFI\bootmgfw.efi
How should I partition my hard disk now? (I can wipe out Ubuntu drives if needed).
Once I've created a new /boot/efi partition, what should it contain?

---

### Post by YannBuntu on 2013-01-05
> **oldfred said:**
> Because you have gpt partitions, Windows will only boot in UEFI mode.

Fred, I am nearly sure this statement is wrong, because I saw several Windows computers with GPT disc and with files for both MBR (Windows MBR + /bootmgr /boot/BCD) and UEFI (EFI Windows files) boots.
Eg Bowen369's system has UEFI but also /bootmgr /boot/BCD files which are for MBR boot...

However, i agree that generally such computers's BIOS are set up in UEFI mode by default, so Bowen369 probably deleted his ESP.

---

### Post by oldfred on 2013-01-06
@YannBuntu
I have seen the BIOS boot files in the main Windows partition on some new UEFI computers. Still not sure why they are there or if just left over from an image they used to create new system.
Mac's require Windows in the MBR portion or first 4 partitions of a Mac with hybrid partitioning gpt/mbr. But the Macs use an older efi spec that does not really work with the new UEFI 2+ spec that Windows & Linux are now using.
Many more knowledgeable than I have said Windows only boots from gpt with UEFI. 

@Bowen369
The UEFI spec says the efi partition should be first. But Windows suggestions have been to make the Windows repair partition first, then the efi, then the MSR, then the main Windows install with the vendor recovery last. 
One user did have the efi installed like you now have far into the disk. I though perhaps the UEFI FAT32 driver had some limits on how far into drive it could find the boot files like some old BIOS systems have had. But I have not seen any that had a valid efi partition that did not boot. But almost all systems have had efi partition close to the start of the drive.

You can reorganize partitions, but it might just be easier to reinstall. Sometimes we learn more about systems by experimenting :) and others just want a system that works.


Of course if experimenting backups are even more important.

---

### Post by Bowen369 on 2013-01-09
I couldn't manage to recover boot via recovery disks, so I've sent back my laptop to HP to get a full factory reset.

Now we're back to square one. I just want to make sure I get this right this time:

[LIST]
[*]Step 1: Backup everything
[*]Step 2: Disable SecureBoot
[*]Step 3: Boot from liveUSB, install Ubuntu 12.10 x64 (automatic, or manual partitionning?)
[*]Step 4: Restart and select "Try Ubuntu" from live USB
[*]Step 5: Run recommended settings of Boot-repair
[*]Step 6: Restart & enjoy?
[/LIST]

Does Windows and Ubuntu share the same EFI boot partition?

One more thing: I want to know the difference between standard Ubuntu .iso, and the secured-remix version, besides having a pre-installed Boot-repair?

Thank you for your patience.

---

### Post by oldfred on 2013-01-09
Also disable Fast Boot or quick boot in UEFI. Some computers only can get back into UEFI menu from Windows with Fast boot on and if you cannot get into Windows.....

How you partition is totally up to you. Default auto install is just / (root) & swap. 
I prefer to know the sizes and what partitions are used (but I have many). Often we suggest the separate /home to keep files separate from system to make reinstall a bit easier. But if dual booting or multi-booting another NTFS data partition probably makes sense so you can share data between systems and not write into system partitions. I have both a NTFS data partition from when using XP and Linux formatted data partition as I multi-boot several Ubuntus.

UEFI only boots from one efi partition and that is designed to let you have boot files for many systems installed into their own folders for booting.

I though secure remix was the addition of Boot-Repair and some other features, but do not know details.
[https://help.ubuntu.com/community/UbuntuSecureRemix#Functionalities](https://help.ubuntu.com/community/UbuntuSecureRemix#Functionalities)

---

### Post by Bowen369 on 2013-01-09
So here's what I did:

Manual install of Ubuntu (since somehow, it didn't detect that Windows was installed):
I've setup 3 partitions: root, swap and /boot (not sure if this one was needed).

Then I followed the steps I've mentionned in my last post, and success, I can finally dual-boot properly!

Although there's still one minor detail I'd like to change before closing this thread:
Upon restarting the PC, I will always be sent to Windows 8 bootloader, unless I hit F9 and specifically ask to boot from EFI. Is there any way to change this?

---

### Post by Hendry on 2013-01-09
As the laptop is brand new isn't it the quickest way to just recover the Windows 8 OS and give installation of Ubuntu another try after recovery finished?

---

### Post by Bowen369 on 2013-01-09
> **Hendry said:**
> As the laptop is brand new isn't it the quickest way to just recover the Windows 8 OS and give installation of Ubuntu another try after recovery finished?

That's what I ended up doing, yes.

---

### Post by oldfred on 2013-01-09
I do not understand, if booting from UEFI you should have ubuntu or Windows. And from ubuntu the grub menu should then let you chain load back to the Windows efi entry.
If not the case, run a new BootInfo report & post link.

---

### Post by Bowen369 on 2013-01-10
> **oldfred said:**
> I do not understand, if booting from UEFI you should have ubuntu or Windows.

That's the problem: My PC automatically goes to Windows bootloader.
If I want to boot to Ubuntu, I have to hit F9 (change boot order), and select "Boot from EFI file", at /boot/efi/EFI/ubuntu/grubx64.efi file.

Here's the BootInfo URL: [http://paste.ubuntu.com/1516626/](http://paste.ubuntu.com/1516626/)

---

### Post by oldfred on 2013-01-10
Some computers only boot Windows. One was checked in detail and it turned out it also booted Redhat??
       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

    Boot-Repair has a work around and some users have manually changed file names. Not sure exactly where it is now on Boot-Repair as it was automatically backing up Windows and renaming grub's shim file to the efi boot file for secure boot. But I guess that caused issues on some other UEFI systems, so it is not first choice. Others have just renamed files manually.

Backup entire efi partition first.
      
Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file (shimx64.efi).    
      
How Boot-Repair works with UEFI systems - post 687 Dec 15, 2012
[http://ubuntuforums.org/showthread.php?t=1769482&page=69](http://ubuntuforums.org/showthread.php?t=1769482&page=69)
How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)

    sony vaio laptop error: symbol not found: `grub_efi_secure_boot'.
[http://ubuntuforums.org/showthread.php?t=2102083](http://ubuntuforums.org/showthread.php?t=2102083)> 
So this time I installed 12.10, then I booted again from liveCD, made backup of (efi part)/EFI/microsoft/boot and copied all files from /EFI/ubuntu into it. Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi. And it works

     UEFI boot live-usb bricks SAMSUNG 530U3C,np700z5c laptop - fix released
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)

---

