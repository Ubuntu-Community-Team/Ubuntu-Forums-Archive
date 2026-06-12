---
title: "No SecureBoot with Manual Full System Encryption on 18.04"
date: 2019-02-18
forum: Installation &amp; Upgrades
---

### Post by jon54 on 2019-02-18
I followed the instructions [here]("https://help.ubuntu.com/community/ManualFullSystemEncryption/") and succeeded in installing Kubuntu 18.04 with full-system encryption on a dual-boot system with Win10. Everything works fine until I enable SecureBoot, which prevents me from booting into Ubuntu (Grub starts fine and is able to get me into Win10 or "system setup" just fine also).

When I attempt to boot into Ubuntu, I get the following error messages:

```

error: no such device: <UUID of /dev/mapper/system-boot>
error: no server is specified.
error: you need to load the kernel first.

Press any key to continue...

```

After several seconds it kicks back to the Grub menu, where I can repeat the cycle by choosing Ubuntu, or by successfully booting into Win10 (or system setup).

Any idea why this is happening?  Is this indicative of the bug listed [URL="https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1565950"]here?
[/URL]
Additionally: Would self-signing a binary (which binary though?) with an MOK get me around this problem?  (yes I would have to re-do this each kernel upgrade).
.
.
.
.

---

### Post by oldfred on 2019-02-18
Did you install with Secure Boot on?
That would install the signed kernel & grub's shimx64.efi.
But if you installed with Secure Boot off, you probably do not have the signed kernels.

You may have to separately mount the encrypted volume/unencrypt it, so Boot-Repair can see / in the LVM.
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by jon54 on 2019-02-18
Thanks OldFred, you are correct that I failed to install this system with SecureBoot on.  I do however have both grubx64.efi and shim64.efi in the EFI system partition though, and the system **does** boot into Grub (and Grub is able to launch Windows, just not Ubuntu).    Detaching the signature from the vmlinuz-*-generic file with sbattach shows me that it appears to be signed (Canonical Ltd. Secure Boot Signing).  

What type of error message would show up when attempting to boot an unsigned kernel with SecureBoot enabled
.
.

---

### Post by oldfred on 2019-02-19
You would get some sort of message from UEFI/system saying something like not in Secure boot mode. Most do not boot.

I know they are changing what is signed and what is not, so not sure anymore on name convention.
Just looked in synaptic with my 18.04.
It used to be you had signed & generic.
But now I see unsigned & generic & description of generic is that it is signed.

---

### Post by jon54 on 2019-02-20
Thanks OldFred, I installed synaptic and checked my installed kernel and it was indeed signed.  Just for fun I went ahead and installed with SecureBoot activated, but the same problem persists. 

I went ahead and ran Boot-Repair directly from the OS itself (after disabling SecureBoot), and you can view it [here.](https://pastebin.com/xRyjepZ6)  Note: the only modification I made was to redact the HDD Serial Number with the text "<HDD Manufacturer and S/N ->".

---

### Post by oldfred on 2019-02-20
Script did not show any files in ESP, your sda2?
Do you have /EFI/ubuntu & /EFI/Microsoft folders with .efi boot files?

For Boot-Repair to work, you have to unencrypt your LVM install. It has link and you have the /boot inside the LVM, so nothing can work unless it is unencrypted.

       [SOLVED]Secure boot issue - fix with Boot-Repair LVM with encryption
[https://ubuntuforums.org/showthread.php?t=2350963](https://ubuntuforums.org/showthread.php?t=2350963)
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

---

### Post by jon54 on 2019-02-21
Thanks OldFred, the previous report was generated from within the OS in question, so the encrypted devices were decrypted at boot.  

I went ahead and ran boot-repair as root, and also made sure that /dev/sda2 was mounted (mountpoint /mounts), that can be viewed [here]("https://pastebin.com/2NGLxvUE").      In case it is still not showing up, directory listings of /boot and relevent directories in /dev/sda2 are listed [here]("https://pastebin.com/dnDr46JR").

---

### Post by oldfred on 2019-02-21
Do not know why Boot-Repair is not showing files at least in ESP which is not encrypted.

Boot-Repair also wants you to decrypted LVM volumes before running it. See line 649.

It looks like you do have the normal files in the ESP & /boot partitions.

---

### Post by jon54 on 2019-02-21
Thanks OldFred.  I think I must be confused, wouldn't booting the system with the system's sole Luks key decrypt everything?  The LVM volumes (system-root and system-boot) are contained in the system's single partition (/dev/sda5), and are listed in boot-repair as being mounted.    I must be missing something embarrassingly obvious here...

---

### Post by oldfred on 2019-02-21
I do not know much about LVM.
I agree that one key should be decrypting everything, perhaps a Boot-Repair issue?

I do not use LVM nor encryption, so I can only offer some links. 
If Boot-Repair does not work, then you have to do a full chroot.

       Includes chroot. /home encryption:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)
LVM chroot
[http://askubuntu.com/questions/719409/how-to-reinstall-grub-from-a-liveusb-if-the-partition-is-encrypted-and-there-i?rq=1](http://askubuntu.com/questions/719409/how-to-reinstall-grub-from-a-liveusb-if-the-partition-is-encrypted-and-there-i?rq=1)
LVM & encryption repair & DNS issue with  systemd-resolved
[https://ubuntuforums.org/showthread.php?t=2409754](https://ubuntuforums.org/showthread.php?t=2409754) 
    
       Mount LVM - duckhook
[https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372](https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372)
[https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621](https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621)

First part is mounting, then you can run any repairs you may need like reinstalling grub.
       How to: Mount & Resize an Encrypted Partition (LUKS) also mount for repairs
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)

---

### Post by jon54 on 2019-02-23
I am marking this thread as solved because there is already a thread [(here)](https://ubuntuforums.org/showthread.php?t=2399092) started by the author of the article referenced in OP.

---

