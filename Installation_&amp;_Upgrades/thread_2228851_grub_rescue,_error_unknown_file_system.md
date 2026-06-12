---
title: "grub rescue, error: unknown file system"
date: 2014-06-09
forum: Installation &amp; Upgrades
---

### Post by Master_Glink on 2014-06-09
Alright so I was in the middle of troubleshooting this PC, I had recently restored it (Windows 7). And networking performance was not what it used to be (before restoring). I tried to install a partition with ubuntu gnome on it to see if Windows was the problem, but I had no luck. Not even using an USB adapter. So I decided to try restoring it again...

I wanted to partition 60GB for C:, some system reserved space and the factory recovery partition and D: drive with the remaining space which I would re-partition later to make a partition for a Linux distro and a shared data partition. I let the recovery do its thing and after it reboots I get the error:

error: unknown filesystem.
Entering rescue mode...
grub rescue>

Now, I don't know how to proceed... The computer has no other recovery media other than the recovery partition. I have access to two other PCs, but the manufacturer only provides DVDs and those are $50. So I'm hoping that I can somehow still salvage some of my plan and get back to having Windows and Linux dual-boot, this time with a shared data partition.

---

### Post by Master_Glink on 2014-06-10
Success, I was able to solve it. I'll go ahead and document what worked and what didn't here to help anyone having a similar problem:

I tried SuperGrub2Disc from a 2GB USB drive formatting it completely using pendrive linux utility in Windows. I was able to reach a boot menu from this but there wasn't much I could do from it. I could boot into my recovery partition, at least confirming that it still existed, and into the soon to be new Windows partition. However the Windows 7 installation couldn't advance for some reason, and gave me a message that Windows wasn't compatible with my hardware. My one theory for this was that since I was booting from the USB drive, it was also going to try to install in that drive. And being that it was only 2GB in size, and entirely allocated to the SuperBoot2Disc utility, it failed.

Then I found this thread through some google sleuth work:

[http://answers.microsoft.com/en-us/windows/forum/windows_7-windows_install/i-bought-a-sony-vaio-computer-that-didnt-come-with/27b353cb-fc01-455f-b5a4-99d225c0f1a7](http://answers.microsoft.com/en-us/windows/forum/windows_7-windows_install/i-bought-a-sony-vaio-computer-that-didnt-come-with/27b353cb-fc01-455f-b5a4-99d225c0f1a7)

From there I downloaded a Windows 7 ISO. I was hoping that I could repair the recovery partition somehow, though I was prepared to install completely using this image since I still had the Windows Key on the bottom of the laptop. The automatic repair option that was offered didn't do anything unfortunately, as it did not detect any errors. However following this guide:

[http://www.tomshardware.com/news/win7-windows-7-mbr,10036.html](http://www.tomshardware.com/news/win7-windows-7-mbr,10036.html)

I ran the command prompt and executed the commands to fix boot and the mbr:

bootrec.exe /FixMbr

bootrec.exe /FixBoot

Then I rebooted without the disc and although Windows wasn't able to continue the previous installation, I was able to access my recovery partition and begin a new one that is currently underway. Once this completes I'll be able to see if the networking issue was fixed (Third time restoring Windows to fix this thing). And hopefully install Linux again in a more permanent fashion.

Definitely a lesson learned, though. Just one thing... Can anyone clear up what the correct order to perform this process would have been? Though I hope I never have to go through such a thing again in the future, I'm certain it's more likely than not.

---

### Post by oldfred on 2014-06-10
You must have had Ubuntu on it before. As you had grub in the MBR.
Best to reinstall Windows boot loader to MBR before reinstalling Windows. The recovery restore seems to assume MBR is ok and does not often restore that.
You can install Windows boot loaders to MBR with Windows (fixMBR) or most Linux live systems for a Windows work alike boot loader like syslinux or lilo.

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

Was system before your reinstall of Windows gpt partitioned? Windows only installs in UEFI mode with gpt partitioning. And Windows install in BIOS mode does not correctly fully convert to MBR. It leaves the backup gpt partition table.

Also only use Windows own partition tools to shrink a Windows NTFS partition. And then reboot so it can run chkdsk. If you create partitions it may convert to dynamic which will not work with Linux nor some Windows repair tools.

---

