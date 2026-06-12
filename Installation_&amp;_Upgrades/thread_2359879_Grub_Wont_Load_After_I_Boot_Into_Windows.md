---
title: "Grub Wont Load After I Boot Into Windows"
date: 2017-04-29
forum: Installation &amp; Upgrades
---

### Post by freestylestorm498 on 2017-04-29
Ok here's the deal. I installed ubuntu 17.04 and got into the os and used it. I then powered it off then back on and it allowed me to choose ubuntu or windows boot manager. I choose ubuntu and everything is fine and dandy but when I choose windows I can't get to grub after I turn off the pc and back on. I've messed around and disabled secure boot, used legacy mode and changed the load order. See what I've come to after days of research is that my UEFI or uEFI from what I've seen apparently reverts back to windows manager after I boot into windows via grub. From what I've been told I must change the boot loader in some EFI file where it stores the boot loader. IF that's true could this harm my pc? I also believe there's a relation between my problem and this guys problem [https://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook#666632](https://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook#666632)

---

### Post by kc1di on 2017-04-29
Can't be of much help here, but in a pinch I've found that supergrub 2 will boot almost anything. 
you can get a copy [here]("https://sourceforge.net/projects/supergrub2/files/")

---

### Post by yancek on 2017-04-29
Not enough information but from what you describe, it seems you may have mixed an MBR install with a UEFI install as the problems you report are expected in that situation.  To get more info to post here get the boot repair software from the site below and run it.  Select the option to Create BootInfo Summary and post a link to the output here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2017-04-29
If UEFI hardware, I suggest using UEFI to install. 
Some prefer the now 35 year old BIOS/MBR configuration, just because it is well know. But UEFI has now been around since Apple converted to Intel chips & pc since Windows released Windows 8.

How you boot install media UEFI or BIOS is how it installs, but that may then not be the default way your system is set to boot.

Always boot in UEFI mode or always boot in BIOS Mode.

If you have UEFI, see link below in my signature.

---

### Post by adrian15 on 2017-04-29
Some information it will be useful to know from your system:
[list]
[*] Machine description and UEFI BIOS version
[/list]
As oldfred says I recommend you to make sure that:
[list]
[*] Secure boot is enabled
[*] Legacy mode is not used
[*] You have got the default boot order
[/list]
Then tell us how you booted the Ubuntu 17.04 installation media.

If Ubuntu 17.04 installation media was not boot in UEFI mode then we strongly encourage to reinstall it but, this time, in UEFI mode.

But, before doing that, **make sure 'Fast Boot' is disabled**. It might be causing some problems.

I am also happen to develop a tool to help people on your situation (if it's actually true that your BIOS forbids you to UEFI boot something else than Windows Boot Manager).
However although it does provide Ubuntu boot, if you want it to dual boot into Windows it needs several manual steps from you.
Tell me if you are interested in beta-testing the tool.

I also recommend you to download and put into a usb [Super Grub2 Disk](http://www.supergrubdisk.org/super-grub2-disk/) (needs Secure Boot disabled) if you want to boot into Ubuntu itself . P.S.: Make sure you use a tool that writes the iso directly to the usb (Beware: You will lose Usb contents).

---

### Post by freestylestorm498 on 2017-04-29
I used the tool and it said it fixed it but it did nothing. is there a way to get log data or something similair to troubleshoot it?

---

### Post by freestylestorm498 on 2017-04-29
Here's some further information. 

I have my ubuntu installed on a separate hard drive with a 250GB partition.

I installed it along side windows bootloader option presented in ubuntu. (Should i install it by choosing "install it another way" by creating the partitions in ubuntu?)

I disabled secure boot

I have legacy support enabled. (tried with and without legacy support should I disable it?)

I have an hp motherboard with EFI according to EasyBCD. but I looked at my system info and it lists as UEFI does it matter?.

I have it installed on sata 1 here's a picture of my boot order. When changing the boot order to the drive that ubuntu is installed on I just get a black screen [https://linustechtips.com/main/uploads/monthly_2017_04/20170425_120603.jpg.d968b93b0e3e0c42823910b2b884206a.jpg](https://linustechtips.com/main/uploads/monthly_2017_04/20170425_120603.jpg.d968b93b0e3e0c42823910b2b884206a.jpg)

I have fast boot disabled. 

I'm a little confused as to installing it a different way.

---

### Post by freestylestorm498 on 2017-04-29
should i write the iso to the usb and boot into it through uefi?

---

### Post by adrian15 on 2017-04-29
> **freestylestorm498 said:**
> I used the tool and it said it fixed it but it did nothing.

Can you please describe which specific tool did you use?
And what options or buttons did you trigger on it?

Thank you.

---

### Post by freestylestorm498 on 2017-04-29
super grub 2 works fine haha i have to do it manually but that will be fine for now. But i used the repair tool for grub. One linked above.

---

### Post by yancek on 2017-04-29
If you had selected the option to Create Boot Info Summary when using boot repair as suggested, it would have given you a link when it finished and you could have posted that here.  Not sure why you tried to repair it without gathering any information because without that information, any suggestions here will be pure guesswork.

---

