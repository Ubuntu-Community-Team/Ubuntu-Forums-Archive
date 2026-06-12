---
title: "ACPI &amp; grub-efi-amd64-signed package failed to install into target error"
date: 2018-06-08
forum: Installation &amp; Upgrades
---

### Post by marcvanduyn on 2018-06-08
Hello

I have several issues regarding the installation of ubuntu 18.04. My system specs are:

intel i5 8400
nvidia gtx 1060
16 gb ram
motherboard ASUS ROG Strix B360-F

First I want to point out that I am having this issue for a while now and have tried many solutions of similar problems.
This forum is my last resort because i don't see a solution to my problem. So first things first:

I created a live usb on windows with Ubuntu 18.04 with the program rufus. I have windows 10 running on a separate ssd and want to install Ubuntu on a different ssd.
I have tried many different configurations regarding motherboard settings and install options. I will outline some of them below:

**ATTEMPT 1:** Motherboard default settings, uefi boot usb.

The default motherboard settings are secure boot with cml disabled.
Also I will boot with the usb in uefi mode, because this is the only option available. When I boot I get a black screen with the general options of install, try, etc. I think the reason I get a black screen instead of the purple screen is of the uefi mode.

Normal installation will give me an ACPI error, and let me not install the system :[ATTACH=CONFIG]280044[/ATTACH]
Installation with "acpi=0ff" will get me to the install screen, but with some kind of error on the startup but let's me install:
[ATTACH=CONFIG]280045[/ATTACH]



Now I will get the second problem, where I get the error** "grub-efi-amd64-signed package failed to install into target"**.
I have tried two configurations:
[B]
Normal installation[/B]
This was fairly straightforward, just using the normal installation. I get the grub error at the end of the installation.

**Something else option**
I make the following configuration regarding partitions.

[LIST]
[*]    efi partition of 500mb 
[*]    swap partition of 16000 mb 
[*]    everything else ast ext4 mounted on "/" with formatting enabled 
[/LIST]


This will also give me the same grub error:
[ATTACH=CONFIG]280043[/ATTACH]

Side note, my pc is connected to the internet during installation.

**ATTEMPT 2**: Motherboard secure boot disabled & CML enabled, boot normal usb.

I disabled secure boot and enable CML. The options I tried are the same as with attempt 1, but now with the usb in normal mode, I also set acpi=off. However now I get a different install screen, maybe this is because I boot in legacy mode. I get the normal purple install screen.
I did do an error check on the installation usb, and it said everything was correct (one of the options available).

Now when I boot, it doesn't give me an install window, it just get stuck on a black screen.

I also tried with the settings "acpi=off, " but then i get the screen that says "(initramfs)unable to find a medium containing a live file system".
[ATTACH=CONFIG]280046[/ATTACH]
**ATTEMPT 3**: Motherboard secure boot disabled & CML enabled, boot uefi usb.

Same as attempt 2, but now with usb in uefi mode. Now I get the black install screen, set "acpi=off" and partition my disk as in attempt1. Again I get the grub error.


Conclusion
I am out of options and I don't know how to proceed further. Does anyone had a similar problem where the given solutions don't work. I think is has something to do with my motherboard and my graphics card.

---

### Post by oldfred on 2018-06-08
Have you checked and if needed updated UEFI from Asus?
Black screen almost always is related to nVidia card/chip issues.
And then using nomodeset works.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
    
You will also need nomodeset on first boot or until you install the proprietary driver from Ubuntu repository. You may also need the ppa to get newest driver available from nVidia but configured for Ubuntu.
[https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336](https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336)

You do want to install in UEFI mode. Most systems need CSM/Legacy/BIOS mode off. A few want it on, but you still boot in UEFI mode.
Often better to have UEFI secure boot off, and you will need it off to install nVidia proprietary driver as Ubuntu cannot guarantee what nVidia has done, so secure boot chain is not certified.


Some very new systems like yours need the very latest kernel & support software. And that may not be in a standard distribution immediately.
       Asus B350M-A needs newer kernel that 18.04 default
[https://ubuntuforums.org/showthread.php?t=2391892](https://ubuntuforums.org/showthread.php?t=2391892)
MSI Tomahawk B350 with Ryzen R5 1600 New UEFI required
[https://ubuntuforums.org/showthread.php?t=2390475](https://ubuntuforums.org/showthread.php?t=2390475)
ASUS PRIME B350M-E major issues
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux)
ryzen acpi=off only 1 cpu, needs nomodeset & then nVidia driver instead
[https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu](https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu)

---

### Post by marcvanduyn on 2018-06-12
Thanks, you helped me out alot. These are the steps I did to fix my problem.

First, I updated my bios. There was a bios update available from the asus website. Then I booted in UEFI and with NOMODESET. This allowed me to install the system without the "grub-efi-amd64-signed package failed to install into target error". When everything was working I first downloaded the latest nvidia drivers. Now my system is working perfectly. 

Regarding the kernel update, this is the kernel it is currently working on: Linux marc-ubuntu 4.15.0-23-generic #25-Ubuntu SMP Wed May 23 18:02:16 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
Do I need to upgrade?

---

