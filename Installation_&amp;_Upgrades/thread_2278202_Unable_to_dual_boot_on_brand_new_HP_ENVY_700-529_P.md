---
title: "Unable to dual boot on brand new HP ENVY 700-529 PC with pre-installed windows 8.1"
date: 2015-05-14
forum: Installation &amp; Upgrades
---

### Post by Subhamoy_Mahajan on 2015-05-14
Firstly Thanks in advance .

My HP ENVY 700-529 came with pre-installed windows 8.1 and I was unable to install Ubuntu as a secondary OS. I read many threads, I followed the instructions and enabled legacy, disabled secure boot and disabled fastboot in my BIOS. I am trying to install it from a USB. My system is able to detect the pen drive and I get to the screen where it asks me to install Ubuntu or try  Ubuntu, but when I choose either of those I end up with a black screen.

Please tell me what to do.
P.S. I dont have another hard disk and I have to keep my windows 8.1 as Its my lab computer I am not allowed to remove it.

Update:: Now I was able to install Ubuntu with the help of a LIVE CD (I have no clue why a bootable USB didnt work) but now I am unable to choose my OS on startup. I have tried installing it 3 times result is the same.

---

### Post by QIII on 2015-05-14
"Allowed"?

This is not a computer you own?

---

### Post by ajgreeny on 2015-05-14
Setting aside the question of machine ownership for the moment, it will be totally impossible to boot to Windows 8.1 in the way you have currently set up the computer as Windows will not run using GPT partitions in legacy BIOS mode and of course you can not change the 
Windows partitions to msdos/MBR without reformatting and reinstalling Windows 8.1.

So, you will have to install Ubuntu again, but this time in UEFI mode; there is no real choice if you have to keep Windows 8.1 as it is on the machine.

See [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI") for more info on UEFI etc etc. and come back again for more info if this does not make sense to you.

---

### Post by Subhamoy_Mahajan on 2015-05-19
**Update:: I used a LIVE CD to install ubuntu and now I am not able to choose ubuntu as I am not getting the option to choose.** 

@QIII that is my computer for 3 months.

@ajgreeny I am only able to boot windows 8.1 now. In windows I partitioned my C drive and then deleted the partition that resulted in free unallocated  space, that way I was able to install Ubuntu.

---

### Post by QIII on 2015-05-19
So, you are using it temporarily as a "loan" from a school or business?

---

