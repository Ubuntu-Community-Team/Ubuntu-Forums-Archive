---
title: "Boot Repair (boot-Info summary) Help request"
date: 2023-11-07
forum: Installation &amp; Upgrades
---

### Post by skeitch on 2023-11-07
Hello all,

i am very new to Ubuntu and the whole community.

I have a dual boot system which worked fine until a Windows update crashed the grub loader it seems.
A friend told me to try Boot repair to fix my problem.

Right now boot repair is running a recommended repair since an hour or more. Sometimes the progress bar stops and starts over again.
my pastebin is: [Ubuntu Pastebin]("https://paste.ubuntu.com/p/PvnkVZsZNg/") (paste.ubuntu.com/p/PvnkVZsZNg/)

Is it normal it takes this long or do i need to use some advanced options ?
Maybe someone finds time to help me.

Thank you very much in advance

regards
Dominik

---

### Post by tea for one on 2023-11-07
This boot file [COLOR="#0000FF"]/efi/ubuntu/grubx64.efi[/COLOR] is missing from nvme0n1p1

[COLOR="#0000FF"]Line 266[/COLOR] - nvme0n1p5/etc/grub.d/31_linux_proxy
Have you installed grub-customizer?

---

### Post by skeitch on 2023-11-07
Hi tea for one

Yes i think i installed grub-customizer in the beginning to change the boot order so the laptop starts in Ubuntu by default not windows.

Can i add the boot file by hand ? so its back where it belong and is needed ? 
If so how is the best way to do it for a absolute beginner like me because boot-repair seems to be stuck in process.

Thank you 
regards
Dominik

---

### Post by tea for one on 2023-11-07
> **skeitch said:**
> Can i add the boot file by hand ? so its back where it belong and is needed ? 
If so how is the best way to do it for a absolute beginner like me because boot-repair seems to be stuck in process.
Unfortunately, grub-customizer has complicated matters by adding a layer of proxy files.
Here is some more info (although probably not what you want to read) [https://easylinuxtipsproject.blogspot.com/p/grub-customizer.html](https://easylinuxtipsproject.blogspot.com/p/grub-customizer.html)

---

### Post by skeitch on 2023-11-07
Okay this kills my vibe .......
i read it and i see what you want to tell me but maybe someone else got another idea or experience (no doubt about your skill or knowledge @tea for one !!!! thank you) ? 

Re-installing Ubuntu is not difficult and seems like the easiest way to get it running again but i would really like to keep my actual installation because i am no skilled user and had some help get it like i wanted it ^^

grub-customizer will be a no go for now if its a cause for problems because the benefits are quite "low".

Lets see and hope for a wonder ;-)

---

### Post by tea for one on 2023-11-07
I've never used grub-customizer, so I do not know any tried and tested solution, but try this:-

Create a rEFInd Boot manager installed on a USB stick.
[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)
[https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html) > A USB Flash Drive Image File
A USB with rEFInd for emergency use may help to find and boot an OS (if Grub is damaged/not responding)

Select to boot the kernel directly (similar to below) - i.e. avoiding grub.
Boot boot\vmlinuz-6.2.0-35-generic from 30 GiB ext4 volume

---

### Post by oldfred on 2023-11-07
What did you select in Boot-Repair?
Boot-Repair has advanced options and there you can choose to totally uninstall grub (system then not bootable) and totally reinstall grub. That would remove all the proxy files and restore grub to defaults. 
Note that references to grub really are to grub2, and grub is the very old version.

If you manually edited any of /etc/default/grub or any other system wide settings in /etc or installed any server apps like database or web, you need to back those up. Then a list of installed apps and backup of /home should let you quickly restore system after reinstall.

If Boot-Repair does not work, you can chroot into your system and run the commands to uninstall customizer & totally reinstall grub.
Note that grub has three versions on repository, grub which really is the old one (not sure still available), grub-pc which is for BIOS/CSM/legacy installs & grub-efi-amd64 for 64 bit PCs. When you install from command line you have to specify correct grub.

UEFI chroot, must include ESP - efi system partition
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)

---

