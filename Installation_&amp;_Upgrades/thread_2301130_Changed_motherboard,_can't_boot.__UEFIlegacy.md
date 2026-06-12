---
title: "Changed motherboard, can't boot.  UEFI/legacy"
date: 2015-10-30
forum: Installation &amp; Upgrades
---

### Post by Yippee38 on 2015-10-30
I'm running Mythbuntu 14.04.  I lost power, and when the power came back on, the machine would not boot.  I went through hell diagnosing the problem, including replacing the motherboard and cpu.  It turned out that the problem was the monitor.  I put the original motherboard back in, however, I never noted which HDD was plugged into which SATA socket.  So now the same drives are plugged in, in the wrong order, and my machine will not boot.  At all.  

My motherboard is a UEFI motherboard, but I've had secure boot disabled from the start.  When I try to boot any HDD (whether I use the UEFI or the SATA entry), it get the flashing cursor forever.  If I try to boot from the Ubunut 14.04 disk, I get the purple screen with a keyboard = <man in circle>.  Any key I hit does nothing, and after that screen changes, I get a blank screen.

Can anybody tell me how I can get my system working again?  Just to be clear, the only thing that has changed is that my drives have been plugged into different SATA ports than they originally were plugged into.

---

### Post by grahammechanical on 2015-10-30
If you have more than one hard drive you need to enter the UEFI to tell the motherboard which hard drive to find a boot loader on. When we install Ubuntu all the hard drives and partitions are given a unique identification number. And it is that number that the boot loader uses to identify which drive and which partition to look for the Linux kernel and not whether it is labelled sda or sdb.

Please check that the CPU, the RAM chips, the video card and the hard drives are all seated and connected properly. Check that the fans are working. Taking the motherboard out and putting it back in can disturb things.

The fact that the Try session does not fully load seems to indicate that it is a hardware issue. That purple screen with the human in a circle is the first screen. After that the Live session should investigate the hardware to determine what drivers modules are to be loaded. The session is not getting that far.

You could try switching on with both drives disconnected. You should see some Power on Self Test (POST) messages and a message that says "insert disk with OS on." Can you enter the UEFI settings utility? 

Regards.

---

### Post by Yippee38 on 2015-10-31
Let me clarify.  It POSTS, but the OS won't boot.  I can access the UEFI (BIOS) screen and select a drive to boot.  It isn't finding an OS though.

I suspected that because I plugged the drives into the wrong spots, it would mess with drive IDs.  I can't figure out how to fix it though.  I know which drive the has the boot loader on it, but when I point UEFI to it, either as UEFI or as SATA, it doesn't load.  Is there a way I can get the boot loader to give me on screen display of what it's doing so I can see where it's hanging up?

---

### Post by Dennis N on 2015-10-31
O.K, how about this? The file grub.cfg in the EFI system partition has a specific hard drive designation, in addition to the UUID:

Line from grub.cfg:
```
search.fs_uuid 03b23fbb-b24a-4830-81e6-711ec55140a6 root [COLOR="#FF0000"]hd1,gpt2[/COLOR]
```

Here hd1 refers to drive #2. If the drive position is switched, the UUID remains the same, but the drive that was hd1,gpt2 is now hd0,gpt2 to the UEFI firmware. hd1,gpt2 no longer has this UUID and the boot fails (**hd0**,gpt2 would now be correct). Does the partition with this UUID have to match the indicated hd and gpt number in order to boot? I have never tested this, but it might. If so, the solution would be to switch the drive connections (or edit the file).

Otherwise, as grahammechanical suggests, look to a hardware problem?

---

### Post by Yippee38 on 2015-10-31
> **Dennis N said:**
> O.K, how about this? The file grub.cfg in the EFI system partition has a specific hard drive designation, in addition to the UUID:

Line from grub.cfg:
```
search.fs_uuid 03b23fbb-b24a-4830-81e6-711ec55140a6 root [COLOR="#FF0000"]hd1,gpt2[/COLOR]
```

Here hd1 refers to drive #2. If the drive position is switched, the UUID remains the same, but the drive that was hd1,gpt2 is now hd0,gpt2 to the UEFI firmware. hd1,gpt2 no longer has this UUID and the boot fails (**hd0**,gpt2 would now be correct). Does the partition with this UUID have to match the indicated hd and gpt number in order to boot? I have never tested this, but it might. If so, the solution would be to switch the drive connections.

Otherwise, as grahammechanical suggests, look to a hardware problem?

That's kind of in line with what I was thinking.  I think I might try Knoppix and see if I can look at that file.

---

### Post by Dennis N on 2015-10-31
If this theory is correct, then just editing the file should do it - easier than switching the cables! I edited my post to mention this. I will be curious to find out if it is.

---

### Post by oldfred on 2015-10-31
When you disconnect a drive UEFI forgets its own boot entries that it had remembered. 
You may just need to reboot a time or two so it does a full configuration again.

UEFI has a fast boot setting (different than Windows fast startup) that assumes system has not changed and boots quickly without checking for hardware changes. 
But you need a full cold boot to get UEFI to totally reset.

UUIDs should override any incorrect setings and then a sudo update-grub once booted will reset them correctly. If the entry in the grub.cfg in the ESP - efi system partition is incorrect that may require a sudo grub-install /dev/sda

---

### Post by Yippee38 on 2015-10-31
I've made progress.  I was able to use rEFInd on a CD to access my install via "recovery".  That showed some fsck errors.  I fixed those.  I was able to examine grub entries.  It had to the boot disk as /dev/sdc, so I changed my cabling to match that (plugged the boot drive into SATA3).  The EFI files are screwed up though.  If I try to boot to the UEFI boot record or whatever it's called, it gives me the black screen.  I know I've got quick boot enabled, so I'll disable that and see if that helps.  I also want to try to boot, using the rEFInd  CD into my normal system as opposed to recovery and see if that works.  I didn't last night because it got too late.  If that works, I can, at worst, install rEFInd and use that as my boot menu.

I'm going to test those two things, then spend some time reading up on how UEFI works, include the link oldfred posted.  Then I can hopefully restore my EFI boot records and get the system working properly.  I'll update with results.

---

