---
title: "Windows won't boot"
date: 2012-11-30
forum: Installation &amp; Upgrades
---

### Post by mstang on 2012-11-30
OK, I got a new Sony Vaio with Windows 8 installed and installed Ubuntu on it.  Except that it wouldn't boot the Ubuntu.  I messed with that for awhile and finally gave up.

So, instead, I put VirtualBox on Windows and installed Ubuntu there.  Then this morning Windows rebooted for some update and up comes Ubuntu!  That would be great but it doesn't recognize my new netgear wifi.  So, I don't have internet access.  Instead, I am using my netbook to post this.

So, when I try and boot into Windows I get:

error: can't find command 'drivemap'
error: invalid EFI file path.

press any key to continue

So, without internet access, how do I get it to boot into Windows.  Mind you I do have internet access through my netbook and a pretty big thumb drive.

So, what is the easiest way to fix this?

---

### Post by oldfred on 2012-11-30
Welcome to the forums.

With UEFI grub2's os-prober creates an older BIOS type chain load entry. But Boot-Repair can add a correct efi chain entry automatically. If this is the case you should add to the reported bug as they seem to prioritize based on numbers. 

       Wrong style chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

Or you can manually add a entry to 40_custom
       
 [http://ubuntuforums.org/showthread.php?t=1934773](http://ubuntuforums.org/showthread.php?t=1934773)

If you still have wifi issues best to post a thread on that, with title that will attract those who know that issue better. Have you updated drivers with Ethernet connection as that usually works.

---

