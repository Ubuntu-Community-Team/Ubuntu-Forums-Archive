---
title: "Instaling alongside windows 7"
date: 2013-09-15
forum: Installation &amp; Upgrades
---

### Post by darykiri1 on 2013-09-15
Hello, I'm a total beginner in linux I have just installed ubuntu alongside windows 7 and it doesn't show any option to boot ubuntu It just only boot windows 7

---

### Post by arkan01d on 2013-09-15
You should be a bit more detailed in the steps you've taken to get to this point. It depends on the order you installed them and the configuration of your system...
Answer a few questions to help us help you: 

[LIST=1]
[*]Did you install Windows first?
[*]Are both OS sharing the same drive?
[*]If No to both of those questions: Did you set the drive with Ubuntu installed as the first boot option in your BIOS?
[/LIST]

---

### Post by darykiri1 on 2013-09-15
I have installed first windows and then ubuntu I selected the option to install ubuntu alongside windows and I set both OS in the same hard drive

---

### Post by squakie on 2013-09-15
Do you know if the BIOS in your PC is set to EFI/UEFI and possible secure boot?

---

### Post by oldfred on 2013-09-15
May be best to see details.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by squakie on 2013-09-15
Thanks OldFred - all the things you've posted on this is what made me think that something else, perhaps efi, was going on, but I'm way over my head trying to figure any of it out.

---

### Post by mastablasta on 2013-09-16
as mentioned post the link from boot info. things might be simpler to solve than you think.

---

### Post by darykiri1 on 2013-09-16
Here is the link from bootinfo: [http://paste.ubuntu.com/6114415/](http://paste.ubuntu.com/6114415/)

---

### Post by darykiri1 on 2013-09-16
nevermind I have solved the problem, thanks

---

### Post by Bucky Ball on 2013-09-16
*Thread moved to **Installation & Upgrades**.*

You might have more luck here and as you've stated you're a total beginner with Ubuntu, helpers will be gentle. ;)

---

