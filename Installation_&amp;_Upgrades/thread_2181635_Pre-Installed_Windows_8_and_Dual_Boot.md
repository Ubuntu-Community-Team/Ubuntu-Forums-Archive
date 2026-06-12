---
title: "Pre-Installed Windows 8 and Dual Boot"
date: 2013-10-18
forum: Installation &amp; Upgrades
---

### Post by w1yo262-da7g7l-lo8mzs0 on 2013-10-18
Hello friends,


I recently purchased a new Toshiba Satellite, which comes with the hideous and horrible Windows 8 pre-installed. I am not too sure exactly what "pre-installed" means in this case... it is true that the Windows 8 operating system seems to load very fast upon starting the computer.

Of course, I immediately created a live USB with a 64 bit Ubuntu ISO and very happily attempted to install Ubuntu with the idea of not deleting the stupid Microsoft product, but instead to use a Dual Boot. 

Dual Boot has worked beautifully in many other computers which I have used before... nevertheless, in this case the problem is that the Ubuntu installer [B]DOES NOT RECOGNIZE THE EXISTENCE OF WINDOWS !!!

[/B]Then, what does this mean? If I install Ubuntu will the Windows be deleted? How is it possible to install a dual boot?
What are the experiences of other users regarding this issue?

Thank you !!!

---

### Post by oldfred on 2013-10-19
Is this an Ultrabook with a small SSD? Those use Intel SRT which causes issues.
Have you turned off secure boot and does Windows still boot? Some do not, but all should.
Did you turn off fast boot?

See more info in my signature, but these are the most important parts.
 Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

