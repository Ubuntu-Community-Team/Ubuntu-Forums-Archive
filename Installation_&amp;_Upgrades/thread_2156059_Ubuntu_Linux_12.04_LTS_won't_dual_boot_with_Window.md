---
title: "Ubuntu Linux 12.04 LTS won't dual boot with Windows 7"
date: 2013-06-20
forum: Installation &amp; Upgrades
---

### Post by psychephia on 2013-06-20
Hi, 


Can anyone help me? I'm confused and don't know what to do. I had installed Ubuntu Linux 12.04 LTS (from CD) side by side with windows 7. But everytime I shut down or restart my laptop, I do not see any bootloader that pops up that would help me choose the two OS (Win7 and Ubuntu). It automatically loads to Windows 7. So now, I'm going through the installation again from the CD, wondering what would be the best thing to do to make it dual boot. Should I reinstall again Ubuntu, partition drive or what? What would be the best thing to do to make it dual boot with Windows?

Thank you. Your help is greatly appreciated.


[IMG]http://i29.photobucket.com/albums/c281/cyberchic/profile%20add%20ons/Screenshotfrom2013-06-20220656.png[/IMG]

---

### Post by oldfred on 2013-06-20
You do not have to reinstall but just install grub2's boot loader to the MBR of your drive.

You can add Boot-Repair to your install in live mode or download a full repair ISO.
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

