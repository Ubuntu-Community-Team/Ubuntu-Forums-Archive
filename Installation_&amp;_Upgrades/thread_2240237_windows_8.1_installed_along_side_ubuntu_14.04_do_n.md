---
title: "windows 8.1 installed along side ubuntu 14.04 do not have boot menu"
date: 2014-08-18
forum: Installation &amp; Upgrades
---

### Post by ScottyDawg on 2014-08-18
HI 

hope you can help, i seem to have done things the wrong way round maybe.....

I have installed Ubuntu 14.04 on my PC 

/efi 
/
swap 
unallocated space 

I have then installed windows 8.1 in the unalloacted space, now when i boot it only boots straight into ubuntu. If i press F12 I then get a menu option to select Cdrom ubuntu and windows. if i select windows it boots into windows. 

this works but should there be a boot menu that i can select either Ubuntu or Windows does this need installing 

can someone point me in the right direction please 

thanks 

SD

---

### Post by oldfred on 2014-08-18
Are both installed in UEFI boot mode? It seems like they would have to be as if Ubuntu is using efi partition that would be gpt partitioned for UEFI boot and Windows only boots from gpt with UEFI.
Are both secure boot or is Ubuntu not secure boot?

Have you run?
sudo update-grub

What model PC?

---

### Post by grahammechanical on 2014-08-18
Because Windows 8 was installed after Ubuntu the Ubuntu boot loader (Grub) does not know of the existence of Windows 8. How could it know? Run the command recommended by oldfred.

Actually I am surprised that Ubuntu is booting at all. When I installed a Windows 8 preview edition it put its boot loader on to both my hard disks. Could not boot Ubuntu on the other hard disk until I fixed the problem.

Regards

---

### Post by ScottyDawg on 2014-08-19
hi both 

Yeah both are installed in UEFI mode, I thought that might be the answer but was not sure due to Ubuntu still booting and like grahammechincal said normally windows install breaks the Grub menu. 

will take a clonezilla and then try your suggestion 

thanks for the quick response

---

### Post by SuperFreak on 2014-08-19
You say yyou have created /Efi, do you mean it is within the root or / partition? It should be in it's own separate partition of about 250MB FAT32 Flagged as boot

Can you get a screenshot from Gparted (using Live Disc or USB)?

---

### Post by ScottyDawg on 2014-08-21
Hi 

Its it own partition, I remember select the option on the format type... will send a screen shot later as I'm at work at the moment

---

