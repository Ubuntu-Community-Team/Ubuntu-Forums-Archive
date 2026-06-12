---
title: "Installed Grub, now it won't let me boot into windows"
date: 2007-07-14
forum: Installation &amp; Upgrades
---

### Post by Paktu on 2007-07-14
I installed Grub because I was planning to try out Ubuntu, but I can't figure out how to boot into Windows.  The commands available in the program seem a bit arcane to me, and I do not really understand the included documentation.  How do I boot into Windows?

---

### Post by merlinus on 2007-07-14
Can you be more specific about what you did?

For example, did you install ubuntu?  If not, then how did you install grub?

Does the grub menu appear?  If so, what are the options?

Etc., etc.

-merlin

---

### Post by Vajra Vrtti on 2007-07-14
> I installed Grub because I was planning to try out Ubuntu
What exactly do you mean? 
Did you installed Ubuntu or only Grub? 
How did you install?
What happens when you boot?

---

### Post by Paktu on 2007-07-14
I installed grub and not ubuntu.  The only option in the boot menu is ubuntu 5.10.

Is there a way to simply uninstall grub?

---

### Post by Vajra Vrtti on 2007-07-14
Why don't you install Ubuntu 7.04 and let it take care of the problem. You will be able to boot Ubuntu or XP at will. Otherwise you will have to restore you MBR in order to boot XP.

---

### Post by Paktu on 2007-07-14
> **Vajra Vrtti said:**
> Why don't you install Ubuntu 7.04 and let it take care of the problem. You will be able to boot Ubuntu or XP at will. Otherwise you will have to restore you MBR in order to boot XP.

I had believed that grub would allow me to install the iso from another hard drive in the computer- i do not have a cdrom drive currently installed.

how difficult is it to restore the MBR?

---

### Post by Skidpad on 2007-07-14
> **Paktu said:**
> I had believed that grub would allow me to install the iso from another hard drive in the computer- i do not have a cdrom drive currently installed.

how difficult is it to restore the MBR?
Do you have your XP disc?  If you do, insert it, reboot, and "fixmbr". ([Microsoft Knowledge Base Article)]("http://support.microsoft.com/kb/314058/en-us")

---

### Post by Vajra Vrtti on 2007-07-14
> how difficult is it to restore the MBR?
Huston, we have a problem!
It's not difficult to restore the MBR, but you need the XP installation CD to do that.

---

### Post by Paktu on 2007-07-14
> **Vajra Vrtti said:**
> Huston, we have a problem!
It's not difficult to restore the MBR, but you need the XP installation CD to do that.

well, i do own a cd rom drive, it just isn't installed.

i'll put in the cd rom drive and nstall ubuntu tomorrow afternoon and hopefully all will be well.

---

### Post by bluknight on 2007-07-14
> **Paktu said:**
> I had believed that grub would allow me to install the iso from another hard drive in the computer- i do not have a cdrom drive currently installed.

 Why not just boot the iso file directly from another location, say /dev/sdb2 such as the following menu.lst from my grub folder:

title 	Ubuntu CE-2.2 6.10
kernel (hd0,1)/boot/vmlinuz fromiso=/dev/sdb2/ubuntu.iso root=/dev/sdb2 ro quiet splash 
vga=791 resume=/dev/hdb6
initrd (hd0,1)/boot/initrd.img


how difficult is it to restore the MBR?

In windows if you can get a dosprompt do a >fdisk /MBR

---

### Post by Vajra Vrtti on 2007-07-14
> **Paktu said:**
> i'll put in the cd rom drive and nstall ubuntu tomorrow afternoon and hopefully all will be well.
You will need the CD drive. Probably installing Ubuntu will fix everything but, if you still need to recover the MBR, see the link provided by Skidpad about the Recovery Console and use the **fixmbr** command.

---

