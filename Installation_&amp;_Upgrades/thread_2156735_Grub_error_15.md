---
title: "Grub error 15"
date: 2013-06-22
forum: Installation &amp; Upgrades
---

### Post by LadyHypatia on 2013-06-22
I'm trying to install unbuntu on a partition of my thinkpad T410.

I created a USB with the live image 64-bit amd. The problem is that when I use the USB to boot, I get:[INDENT]GRUB loading
stage 1.5

error 15
[/INDENT]

And that's where everything stops. I tried two different images:
ubuntu-12.04.2-desktop-amd64
and
ubuntu-13.04-desktop-amd64

There are other ideas on here with this error, but they involve a started installation. This won't even go forward.

---

### Post by FloW95 on 2013-06-22
What about installing Ubuntu via CD/DVD?

---

### Post by LadyHypatia on 2013-06-22
I don't actually have a CD handy and nothing's open tomorrow.

Do you think this would make a difference?

---

### Post by FloW95 on 2013-06-22
I think you should give it a try, and maybe you should try the 32-Bit versions too. But I don't know what's wrong with your laptop, I just wanted to tell you that you didn't try everything. ;)

---

### Post by LadyHypatia on 2013-06-22
Why would booting from a usb create a GRUB error?

The usb just has the ubuntu image on it.

---

### Post by oldfred on 2013-06-23
How old is system? How much RAM?

Grub error 15 is from grub legacy. Did you have an old install on system as Ubuntu has not used grub legacy since 9.10, although if you had an old install you could keep the old boot loader. 
So it seems grub2 never fully installed.

If older system 32 bit Lubuntu may be better choice. But my laptop is 6 years old and does run the 64 bit full Ubuntu but I do not use Unity as that requires more graphics power than old system really has.

You can download Boot-Repair into your live installer or download the repairCD version which can also be on a flash drive. If your system boots flash drives that is usually a better way to install. A bit quicker and flash drive is then reuseable.

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

### Post by LadyHypatia on 2013-06-23
The laptop only has Windows 7 on one partition. The other partition has not been formatted yet. The USB key has the ubuntu image on it.

---

### Post by LadyHypatia on 2013-06-23
The system is not that old. It's running an Intel Core i7 CPU @2.67GHz, 4GB of RAM.

I've checked the BIOS and there's nothing there.. and there was no previous GRUB on the system.

---

### Post by oldfred on 2013-06-23
Live installer should not have grub legacy.

Download Boot-Repair into live version or download the secure remix as it is an installer with Boot-Repair already installed. For newer systems and flash drive install.

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

