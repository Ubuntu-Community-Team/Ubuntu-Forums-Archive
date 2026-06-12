---
title: "Dual boot windows 8, ubuntu won't show up."
date: 2013-10-18
forum: Installation &amp; Upgrades
---

### Post by kees2 on 2013-10-18
Help me! I wanted to install ubuntu alongside my current operating system, windows 8. I have windows 8 with UEFI. This, i disabled and then i installed ubuntu from a cd. Now, it's supposed to ask me what operating systems to launch. It does not. It just goes straight to windows 8. I searched the web and these forums but nowhere i can find the answer. Please help me. It would mean the world to me.

[IMG]http://ubuntuforums.org/images/icons/icon9.png[/IMG]

---

### Post by dariomgsilva on 2013-10-18
remove boot secure on BIOS

---

### Post by Muhammad_Mudassir on 2013-10-19
I am having the same problem.
How will i remove boot secure on bios

---

### Post by oldfred on 2013-10-19
@Muhammad_Mudassir
Please start your own thread and not hijack some one elses.

Did you install Ubuntu in UEFI mode or BIOS/CSM mode? Best to see details.
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

