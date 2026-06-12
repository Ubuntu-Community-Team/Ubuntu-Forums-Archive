---
title: "Grub reinstall problems"
date: 2015-06-10
forum: Installation &amp; Upgrades
---

### Post by Luk_Michalec on 2015-06-10
Hello everybody!
Here is full story:
I got new notebook (Acer Aspire with windows 8.1) and i need Linux for my work. 
So i divided main windows partition (400GB) on 200GB for windows and 200GB clean space.
200GB free partition, i futher divided on 10GB SWAP, 190GB /ROOT
Installation was completed and windows boot loader was replaced by grub. BUT! Grub doesnt find windows :(
So i followed many many tutorial and nothing helped. :(
So, i manually added entry to grub for windows. When i try to boot windows i got error: "Invalid signature".
So, again, i follow many and many tutorial for that error, i reinstall grub.
Now, grub doesnt work and after bios boot, i got grub rescue console :(
I have Linux Mint live USB, and i tried to repair grub, but no success :(
Any second, i will upload screenshot from gParted (hope it will help).
Any advice? Thanks a lot! I am very desperate :(

[IMG]http://i62.tinypic.com/w2oheb.png[/IMG]

---

### Post by Luk_Michalec on 2015-06-10
I successfully installed grub on /dev/sda and its working again.
But no windows 8 entry. It still doesnt find it :(

---

### Post by Luk_Michalec on 2015-06-10
Now i added entry to /etc/grub.d/40_custom:

menuentry "Windows 8" {
 set root='(hd0,gpt2)'
 chainloader /efi/Microsoft/Boot/bootmgfw.efi
}

the file bootmgfw.efi is there, i check it.
In grub, when i select "Windows 8" i got "invalid signature" :( And i think this is a dead end :(

---

### Post by westie457 on 2015-06-10
Hi, this is a quick fix to see if things work.
In the UEFI Settings pages disable Secure Boot, exit saving changes then try booting into Windows.

---

### Post by grahammechanical on 2015-06-10
It is my understanding that if a machine comes with Windows 8.1 pre-installed then Windows was installed in EFI mode. And that means that Ubuntu must also be installed in EFI mode otherwise we get into a situation where we can load one or the other but not both OS.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode. What is important is below:  

if  the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too.

Regards.

---

### Post by oldfred on 2015-06-11
The bios_grub partition indicates you installed in CSM/BIOS mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

UEFI & BIOS are not compatible. You have to reboot and possibly turn on/off UEFI or CSM settings to change boot mode (many auto switch now once set up). Or you cannot from grub in CSM mode chain load to Windows in UEFI mode.
You can only use grub to dual boot for systems installed in same boot mode, or both UEFI or both BIOS/CSM.
But you should be able to dual boot from UEFI boot tab, or if settings allow from one time boot key often f10 or f12.

Better to install Ubuntu in UEFI mode, Boot-Repair can convert your install to UEFI, by uninstalling grub-pc(BIOS) and installing grub-efi-amd(UEFI).

If you totally reinstall, read major caution in link below in my signature and be sure you have full backups of Windows. Do not run any auto install, even one that says only replacing Ubuntu. Only use Something Else.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

