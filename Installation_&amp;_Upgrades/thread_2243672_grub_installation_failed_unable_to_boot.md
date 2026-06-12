---
title: "grub installation failed unable to boot"
date: 2014-09-10
forum: Installation &amp; Upgrades
---

### Post by edwin12 on 2014-09-10
Hello guys, I'm new to here, I meet a problem.
I got a SSD with dual boot ( Windows 7 and Ubuntu)
My grub seem has some problems then I try to boot-repair, but when it installing the grub after remove it, it failed and then I restart the pc, after that it cannot boot into either Ubuntu or Wins 7.
It keeps shows :-

loading operating system
error: no such device : 353db..........................
Entering rescue mode... 
grub rescue>

I tried the "try Ubuntu" to boot-repair and Windows 7 bootrec /fixmbr, both said successful but when I reboot the pc, it still show grub rescue.

so I decided to format whole drive and I found that the drive is unallocated, and also I cannot add new partition or format, keeps show error.

I try to install Windows 7 again, it did not shows the SSD instead the HDD which is the storage drive.

Then I used the OCZ toolbox (My ssd is OCZ Vector) and it say no supported drive found.

Is my SSD failed? or the grub failed then made those problem?

Sorry for my bad english ;) I need help.

---

### Post by oldfred on 2014-09-10
We need more info.
If you can boot live installer and run Boot-Repair, run the BootInfo report and post the link it gives to the pastebin.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by edwin12 on 2014-09-10
You mean this? 
[http://paste.ubuntu.com/8309611/](http://paste.ubuntu.com/8309611/)

---

### Post by oldfred on 2014-09-10
That is not really showing sda at all.
Do you have two flash drives plugged in?

Does BIOS show SSD or sda correctly?
Is BIOS set for AHCI, not RAID nor IDE?

---

### Post by edwin12 on 2014-09-10
Yes, I have 2 flash drive.
1 for Try Ubuntu, 1 for Windows 7 disk

BIOS does sometime show SSD and sometime no,
I'm set BIOS to IDE because when I set it to AHCl it will bluescreen when boot into Windows 7.

---

### Post by oldfred on 2014-09-10
Windows 7 needs AHCI drivers which you should install. 
And much better for both Windows & Ubuntu to use AHCI.

---

