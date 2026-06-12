---
title: "Dual boot ubuntu with windows 10, error : grub.chenal not found"
date: 2018-12-01
forum: Installation &amp; Upgrades
---

### Post by kanic on 2018-12-01
Hi. So I recently fomrated my laptop (Dell inspiron 3543) and now I'm trying to dual boot ubuntu 16.04 alongside windows 10.
I followed the steps from here ([https://www.tecmint.com/install-ubuntu-16-04-alongside-with-windows-10-or-8-in-dual-boot/](https://www.tecmint.com/install-ubuntu-16-04-alongside-with-windows-10-or-8-in-dual-boot/))
shrunk my hard drive's size to create a partition for ubuntu. Then I burned the downloaded image in a usb drive with universal usb installer.
My system is using bios not uefi. 

Afterwards I restart with my usb inserted and in the bootup screen I get two choices to install ubuntu. Neither of them work and both give the same error
Error 15: http//grub4dos.chenall.net/e/15 file not found.  I saw certain threads here but none of them seem imediately related to my situation (at least to my knowledge)
What is that file for? 
What am I doing wrong and what must I do?

Thanks in advance

---

### Post by oldfred on 2018-12-01
Ubuntu does not use the very old grub4dos which your error is from

That is probably because you are using EasyBCD which we know little about. Some with BIOS, did use it when primarily Windows users, but grub2 then has to be installed to a partition. And grub2 says not to install to a partition as it is then not as reliable.
       [https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/) 
    
All new systems with Windows 10 pre-installed in last 5 years are UEFI. And with UEFI, there is no need for EasyBCD, so little use now.

---

### Post by jonty16117 on 2018-12-01
So are you suggesting to run boot repair from live installer...?

---

### Post by kanic on 2018-12-01
Just like oldfred suggested I converted from bios to uefi and proceeded normally

---

### Post by yancek on 2018-12-01
> So are you suggesting to run boot repair from live installer...?         

Use the 2nd option for using boot repair at the link below.  Take a look at the second link below which discusses dual booting windows 10 and Ubuntu.  I'm not sure what you are doing to get the grub4dos message?

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

