---
title: "Empty EFI folders -  no shimx64.efi - no /EFI/ubuntu"
date: 2017-12-03
forum: Installation &amp; Upgrades
---

### Post by lemmer on 2017-12-03
Hello, I open a new thread because this problem is specific and the actual installation I asked about in the other post is working.

I need to copy the efi files in order to grant the secure boot, I suppose.

I cannot find the shimx64.efi file anywhere, nor the /efi/ubuntu folder in which it should be.

I am running Ubuntu 16.04.3 Live on a USB stick, /dev/sda. On /dev/sdb there is the external SSD disk on which I performed the installation. I mounted /dev/sdb1 (ESP, flagged boot, esp) to /mnt but a ls in /mnt gives nothing.

From the live, I checked the / folder of the Live (which I suppose is the same of /sda, being that the live usb stick). In /boot there is only a ./grub folder, which contains gfxblacklist.txt,  grubenv,  unicode.pf2.
if I open /cdrom, where /dev/sda is actually mounted (I have no cdrom drive), I get a boot folder and a EFI folder, plus a ubuntu file. In the boot folder there is a grub folder which contains efi.img  font.pf2  grub.cfg  loopback.cfg  x86_64-efi.
 In the EFI folder there is a BOOT folder which contains BOOTx64.EFI and grubx64.efi.

I also have an internal SSD which I don't know how to mount/see actually and where there is an install of Windows 10.

Where can I find the folders and files? (I also don't know how to see them, copy them and so on)

---

### Post by oldfred on 2017-12-03
If external drives, you do not boot using grubx64.efi or shimx64.efi, but using /EFI/Boot/bootx64.efi.
The copy of /EFI/Boot/bootx64.efi in the installer is a smaller version of grub for Secure boot and just configured for the necessary files for the installer.

The full install normally have /EFI/ubuntu folder in ESP. But newer versions mount it in fstab /boot/efi with permissions 0077 or no access. Boot-Repair converts that to defaults so it can update. 
But I assume reason for change was security. FAT32 does not support any of Linux ownership & permissions, so standard/default mount would give a rogue process access to your UEFI boot file. With 0077 permissions that is not possible, unless you have physical access to system.

I do not (yet) use Secure Boot, and also manually change mount of ESP so I can modify it. In future I may change that.

You should be able to boot live installer and then mount the ESP on your install. Then you would have access to it. Boot-Repair also copies shimx64.efi to /EFI/Boot/bootx64.efi. It may do it in all cases now or you may check 'Use the standard efi file' option in advanced options.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by lemmer on 2017-12-03
I am afraid I still don't get it. 

Shall I perform the procedure ubfan1 told me in the other thread by using Boot-repair?

---

### Post by oldfred on 2017-12-03
Please explain further what you want to do.

Best to see details of actual install from Boot-Repair's summary report.

If system is working what is issue?

---

### Post by lemmer on 2017-12-04
I am going to post details soon.

What I want to do is to achieve a correct boot configuration:

1. If no external drive is connected to the pc, I would like Windows to boot without the grub prompt and having to type "exit"
2. I would like Windows to set the correct hour automatically, which it stopped doing since I did the dual boot
3. When the external SSD is achieved I would like grub to come up (which it does), and let me boot Ubuntu (which it did, now not anymore due to the alloc error I posted in a new thread), or let me boot Windows (it never let me did that)
4. I would like to let Secure Boot active in all of this.

---

### Post by oldfred on 2017-12-04
With UEFI Secure boot on, you cannot install any proprietary drivers for video or Internet. Does your system need those or does it work fine without proprietary drivers?

Time issue is separate, I have seen many threads on resolving that, but do not know details.
       Time issues fix changed:
[URL="http://ubuntuforums.org/showthread.php?t=2321876"]http://ubuntuforums.org/showthread.php?t=2321876
[/URL]
 [https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts](https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts)
time, UEFI, windows 8  - several posts by sudodus  
[http://ubuntuforums.org/showthread.php?t=1769482&p=12608648#post12608648](http://ubuntuforums.org/showthread.php?t=1769482&p=12608648#post12608648)[URL="http://ubuntuforums.org/showthread.php?t=2321876"]
[/URL]
You want to have external drive first in boot order and Windows second in boot order.
I believe in previous thread was the discussion of UEFI only boots external drives from /EFI/Boot/bootx64.efi. So for UEFI to boot external first it must have that file. And you copy from your ESP on internal drive twice to USB drive's ESP. You do have ESP on external drive?

---

