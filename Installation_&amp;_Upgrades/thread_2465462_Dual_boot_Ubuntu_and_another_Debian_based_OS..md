---
title: "Dual boot Ubuntu and another Debian based OS."
date: 2021-08-02
forum: Installation &amp; Upgrades
---

### Post by robert71 on 2021-08-02
Hi Everyone, 

      Currently im using Ubuntu and Windows in a dual boot configuration pretty nicely without any issues. 
Recently my ESXi server crashed and is not recoverable. I use those VMS for work and need them as well as my  PC. 

I took out the HD's and put them on my desktop with the dual boot config. 

I would like  to install proxmox to get access to my VMs and keep my dual boot configuration. 
Online and in proxmox documentation it says its debian based just like Ubuntu. 

So my request for help is: 

1. Would installing proxmox on another drive cause me to lose access to my Ubuntu / Windows dual boot configuration. 

2. If yes to #1, is there a way to install it that i can boot either OS. 
    (Perhaps copying and pasting the config from my Ubuntu boot config files to the newly installed proxmox boot config files ?)
 If anyone can shed some light i would be most grateful. 

If anyone would like me to post any info e.g grub conf please let me know and i will 

thanks and regards,

---

### Post by tea for one on 2021-08-02
> **robert71 said:**
> 1. Would installing proxmox on another drive cause me to lose access to my Ubuntu / Windows dual boot configuration. 

Remove, isolate, de-activate any drive which you want to protect.
Only have the [COLOR="#0000FF"]target[/COLOR] drive available.

Hopefully, your existing systems are in UEFI mode with GPT because this makes booting via UEFI nice and easy and you do not have to constantly worry about grub.

If you have multiple drives, I would recommend that each OS is installed on a separate drive.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by grahammechanical on 2021-08-02
> 1. Would installing proxmox on another drive cause me to lose access to my Ubuntu / Windows dual boot configuration.

The answer to that would be yes, until you reconnect the other drive(s) and the run in promox

```
sudo update-grub
```

Grub will then detect all the operating systems and re-configure the Grub boot menu to show all the operating systems. You will need to continue to boot from the promox drive. If you choose to boot from the Ubuntu drive then run that command in Ubuntu.

Regards

---

### Post by robert71 on 2021-08-02
> **tea for one said:**
> 
Hopefully, your existing systems are in UEFI mode with GPT because this makes booting via UEFI nice and easy and you do not have to constantly worry about grub.


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I read through the link you posted and ran the following commands: 


[LIST]
[*=left][FONT=inherit][ -d /sys/firmware/efi ] && echo "Installed in UEFI mode" || echo "Installed in Legacy mode"[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT]
[/LIST]
 2. [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 


They both indicate that the system is installed and boots in UEFI mode.


 However in Ubuntu i can see /boot/grub/grub.cfg 

so  what do you mean by 

 > **tea for one said:**
> 
Hopefully, your existing systems are in UEFI mode with GPT because this makes booting via UEFI nice and easy and you do not have to constantly worry about grub.


is it that UEFI manages GRUB, or is it that grub isnt used because i can edit the grub files to give me a longer counter on OS selection etc so it is being used i think....

Sorry im a little confused 

anyone can explain please

---

### Post by tea for one on 2021-08-03
Yes, UEFI together with Grub and Windows Boot Manager is complicated.
Assuming that all systems are installed in UEFI mode with GPT:-

_One OS on one disk_

You can boot the disk via UEFI one time time boot screen.
You will need Grub or Windows Boot Manager to manage booting earlier kernels, recovery mode or safe mode etc.

_Multiple OS on one disk_

You can boot the disk via UEFI one time time screen.
Some UEFI iterations allow booting of individual partitions via UEFI shell instructions. 
Some UEFI iterations [COLOR="#FF0000"]do not[/COLOR] allow booting of individual partitions via UEFI shell.
It depends on the Vendor's configuration of UEFI firmware.
You will need Grub (or equivalent) to manage the OS selection.
Updates from any OS in a dual-boot or multi-boot configuration can give interminable boot problems (as these forums will testify)

As you have multiple disks, I would seriously consider each OS on a separate disk to avoid updates affecting the loading of other systems.
I would certainly keep Windows on a separate disk as sometimes it can be an unfriendly neighbour.

Of course, you can still mount separate disks after an OS has booted to allow access to your data.

Scroll down to Recommendations in this explanation:- [https://www.happyassassin.net/posts/2014/01/25/uefi-boot-how-does-that-actually-work-then/](https://www.happyassassin.net/posts/2014/01/25/uefi-boot-how-does-that-actually-work-then/)

I have two disks in my PC
My main OS is Ubuntu 20.04 LTS on a NVME disk
I have a separate partition on the NVME disk containing a VM of Windows 10 (very rarely used in earnest, only for understanding some forum questions)
The second disk (2.5" SSD) has the latest Ubuntu (21.04 right now soon to be 21.10 in October 2021)

I can still use Grub to control the booting of both disks.
However, each disk has an EFI partition (ESP), and in the event of a Grub difficulty, I have the fallback position of booting either disk via UEFI.

---

### Post by robert71 on 2021-08-03
@Tea For One 

Wow thanks for taking the time to explain. 

And thanks for the link. Will definitely be checking it out in detail as i get home from work. 

Much appreciated. Have a nice day :)

---

### Post by ActionParsnip on 2021-08-03
If the VMs are for your job...why are they not backed up? Is your job not important to you.....?

---

