---
title: "Ubuntu 13.04 with Windows 8 Problems"
date: 2013-06-11
forum: Installation &amp; Upgrades
---

### Post by Necis on 2013-06-11
I built my PC and installed Windows 8 pro on the SSD. Now I am trying to install Ubuntu on it but I am running into a problem. I can get through the installation process perfectly but when I restart the computer after installing ubuntu, then I go to select Ubuntu in the OS list, when it loads it only gives me an orange screen. Then I realized, I need to try the efi trick so then I tried to enable EFI but my bios only gives me the option for EFI for the DVD drive and I dont have an option to disable secureboot. So I figured, whatever, then tried reinstalling Ubuntu. When it booted from the cd, Ubuntu told me that secureboot was disabled(I never disabled it), so then I went to click on reinstall Ubuntu. This time it gave me a white screen that turned Orange but the weird thing is, is that I can see part of the mouse cursor at the very top of the screen when I move it around up there. How can fix this? I would love to use Ubuntu.

---

### Post by gigenieks on 2013-06-11
Hi!

I think you need to provide a bit more details, so it's easier to determine where exactly is the problem.

I don't think SecureBoot is at fault. Why?
*"I can get through the installation process perfectly..."*
> **squakie said:**
> 
The laptop has UEFI and also has Secure Boot enabled.  

I was looking to see what progress has been made (and apparently a lot) on Ubuntu loading without turning Secure Boot off in the BIOS.

I don't think Secure Boot is causing 'orange screen' issue..

It's more likely Ubuntu has some conflict with you graphic card. What do you have?
> 
Ubuntu installs the opensource driver [for your graphic card] by default but you may need the proprietary one to make your model work properly.

[check this thread]("http://ubuntuforums.org/showthread.php?t=2142806")

Hope this helps!

---

### Post by Necis on 2013-06-11
I am using a Radeon HD 6970 2gb

---

### Post by Necis on 2013-06-11
> **gigenieks said:**
> Hi!

I think you need to provide a bit more details, so it's easier to determine where exactly is the problem.

I don't think SecureBoot is at fault. Why?
*"I can get through the installation process perfectly..."*

I don't think Secure Boot is causing 'orange screen' issue..

It's more likely Ubuntu has some conflict with you graphic card. What do you have?

[check this thread]("http://ubuntuforums.org/showthread.php?t=2142806")

Hope this helps!

I took his advice and went into text mode but that just gave me a black screen with no terminal or anyway of putting in commands.

---

### Post by gigenieks on 2013-06-11
It would be much easier to understand what's happening with pictures. Can you do them, please?

---

### Post by Necis on 2013-06-11
> **gigenieks said:**
> It would be much easier to understand what's happening with pictures. Can you do them, please?


At the Grub, everything looks normal

[http://i.imgur.com/VM4td0e.jpg](http://i.imgur.com/VM4td0e.jpg)

What the screen looks like when I select Ubuntu

[http://i.imgur.com/baBVqSJ.jpg](http://i.imgur.com/baBVqSJ.jpg)

There is no point in me taking a picture for when I press ctrl+alt+f1 because it just gives me a completely black screen with no way of doing anything

---

### Post by oldfred on 2013-06-11
Only systems with Windows 8 pre-installed have secure boot turned on.

But you do have to install both Ubuntu and Windows in BIOS mode or both in UEFI mode.

To see details.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

Then you may have video issues as posted above. Have you tried nomodeset or radeon.modeset=0

?

      
 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)


 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

---

### Post by Necis on 2013-06-12
> **oldfred said:**
> Only systems with Windows 8 pre-installed have secure boot turned on.

But you do have to install both Ubuntu and Windows in BIOS mode or both in UEFI mode.

To see details.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

Then you may have video issues as posted above. Have you tried nomodeset or radeon.modeset=0

?

      
 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)


 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

Thanks for the help. I am about to try what you linked, then I will report back.

---

### Post by Necis on 2013-06-12
Using NOMODESET worked. Thank you so much for the help!! :)

---

