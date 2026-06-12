---
title: "Can't install Ubuntu on newish Lenovo G850"
date: 2013-08-25
forum: Installation &amp; Upgrades
---

### Post by sanderella on 2013-08-25
I'm just a little old lady who has been using Ubuntu for several years. Now I cannot install it on my new laptop. I have looked at the help pages on 
*'Installing Ubuntu Quickly and Easily via Trial and Error' *but I can't understand it. Is anyone going to make it easier to install Ubuntu for non-geeks like me?
I don't want to have to use Windows 8, and give up Ubuntu.

---

### Post by zhangjiaoshen on 2013-08-25
hello,i am a ubuntu fans too,and i also get in trouble many many times. To get more help you should describe the more detail of the errors, pictures maybe better .I think many people would see and help you to solve the problem.
sorry for my bad english.

---

### Post by oldfred on 2013-08-26
If you have a new system with Windows 8 pre-installed it has become more complicated. With BIOS you could only boot with BIOS mode.

Now with UEFI, you have UEFI with secure boot which is Windows default, you have UEFI without secure boot and you have CSM which is BIOS emulation to use an old hard drive that was BIOS.

The Ubuntu install disk is configured for all three and will install in the version you boot from UEFI menu with.
So if secure boot is on, Ubuntu will install with secure boot. If CSM is on it will install in BIOS mode but then cannot easily dual boot with Windows.

Best to turn secure boot off, if your Windows will still boot in UEFI with secure boot off. Some systems only boot with it on. 
You must turn fast boot off or the always on hibernation that Windows has.
Then use Windows 8's disk tools to shrink the Windows main partition to make unallocated space for Ubuntu and reboot a couple of times to let Windows run chkdsk and make repairs to recognize its new size.

Depending on Video you may also have issues that are not related to UEFI and need nomodeset or other settings.
Best to test live installer in live mode to see if your system has any issues.
Sicne UEFI is new, hardware is new, it is better to use the very newest version of Ubuntu or 13.04 or 12.04.3 which now has some of the internals of 13.04. You must use the 64 bit version.
What video card/chip do you have?

After Ubuntu install you will need Boot-Repair to fix some dual boot issues with os-prober.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

    
More info and good links to examples with screen shots on installing in the link in my signature.

---

### Post by sanderella on 2013-08-27
Thank you for your helps. I intend to go to our next LUG meeting for more assistance.

---

