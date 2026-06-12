---
title: "Ubuntu Installer not working Nouveau"
date: 2017-06-14
forum: Installation &amp; Upgrades
---

### Post by brucelats on 2017-06-14
> **oldfred said:**
>  Help please :(


Ok guys. I am linux noob and i am already stuck for 2 days on instaling my Ubuntu 16.04 on my brand new hardware.

1. I bought new pc and i managed after some tries to finaly install my ubuntu 16.04.
2. After short time i decided to go for ubuntu server 14.04 to try some things for GPU Ethereum farming. It successfully instaled but it didnt rly work on server so i decide to go back to Ubuntu 16.04
3. I try to install Ubuntu 16.04 again, like i did first time, from Bootable USB-drive but i just cant get it to work... 
4. I tried UEFI and "Other OS", that's how it's written in BIOS to boot and both times after i click on Install Ubuntu or Try Live i am bounced back to black screen and i see some "noveau E [    [COLOR=#000000]failed to create kernel channel, -22"




[/COLOR][https://ubuntuforums.org/showthread.php?t=2319613](https://ubuntuforums.org/showthread.php?t=2319613) - This is what happens to me also.


There are 2 scenarios. Once i get purple screen with little keyboard on bottom, when i try to press anything it just bounces to black screen described in 4.
And other scenario is i have black screen with few options to select - Instal ubuntu or try live, check disc for errors OEM install and such, and as soon i select any of those i get bounced back to black screen already mentioned.


PLEASE HELP ! :(((((

---

### Post by oldfred on 2017-06-14
Please do not post your issues to another thread. It gets too confusing on who is answering what issue. And boot issues almost always are different as users have different hardware and configurations.

Do you want UEFI or BIOS.
BIOS boot is the tiny accessiblity icons at bottom of screen, you can press any key when they show to get to set more boot options like nomodeset.
UEFI has grub menu, and you have to manually add boot options by pressing e.

Have you tried nomodeset? 
If it is saying nouveau issues that most often is related to your nVidia card/chip. 
What video card/chip do you have?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]https://wiki.ubuntu.com/Kernel/KernelBootParameters

[/URL]
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

If you have newer UEFI hardware often better to install in UEFI boot mode to take advantage of the newer features. See link in my signature.

[URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]
[/URL]

---

