---
title: "Is there a way to boot a USB from Minimal BASH?"
date: 2017-04-11
forum: Installation &amp; Upgrades
---

### Post by heema-d on 2017-04-11
I tried to install Lubuntu on my laptop (HP Stream 11 2015) last night, and it didn't go too well. When I start up, I get greeted with and error message and imediatly go to the Minimal BASH screen. 
I downloaded Lubuntu only, not a dual boot. I didn't thing UEFI would be different but I found out the hard way it is.
How can I boot from a USB from the BASH screen?

This is the first time in a few years I'm using Linux again, so consider me a noob.

---

### Post by Bashing-om on 2017-04-11
heema-d; Hello;

Show us what you are working with -
post back:
```

sudo parted -l
sudo fdisk -lu

```
from that live environment .

See what it is going to take to get you booted .

[INDENT][INDENT]it is, what it will be
[/INDENT][/INDENT]

---

### Post by heema-d on 2017-04-11
I cannot access terminal. I am stuck in Minimal BASH only.
When I type that in I get error: can't find command 'sudo'
I have a feeling Secure Boot may have something to do with my problem

---

### Post by Bashing-om on 2017-04-11
heema-d; Hey;

My thought process was to boot up the installer - liveDVD(USB) .
If you no longer have it we can try and get the info from that grub prompt . laborious and time intensive but can do .
At that grub prompt what returns from grub command:
```

ls

```
We are looking at where grub has it boot files located . AND the procedure (MBR EFI ??) required then to boot this system.
We then go chasing down the rabbit hole .
Tell grub where it's files are and enable grub to tell the kernel what to do .


[INDENT][INDENT]it is a thing
[/INDENT][/INDENT]

---

### Post by yancek on 2017-04-11
When you are at the grub prompt, you are using the bootloader and there is no operating system so the commands referenced will not work.
It doesn't have anything to do with Secure boot in all likelihood.
In your first post, you indicate when you boot, you get an error but you don't post what that error is???
Also, you make a reference to UEFI.  Did you installing using UEFI rather than the older MBR?  Did you select the Erase disk and install Lubuntu option?  You don't mention any other OS installed?  Was there previously a windows install on the computer?  If so, was it UEFI?

When you boot and get to the grub prompt, type in the following:  ls  (Lower case Letter L in the command) and watch the output and make a note of it.   You should see output similar to this:

> grub> ls
(hd0) (hd0,msdos1) (hd0,msdos2)

Try selecting one of the partitions to boot it. 

> set root=(hd0,msdos1)  (hit the Enter key)
chainloader +1  (hit the Enter key)
boot  (hit  the Enter key)

Repeat the process for each entry you see such as (hd0,msdos1)

If you have an EFI partition, I doubt this will work.

---

### Post by heema-d on 2017-04-11
When I type that in I get
(hd0) (hd1) (hd2,gpt3) (hd2,gpt2) (hd2,gpt1) (hd3) (hd4) (hd5)

I also have two USBs plugged in:
(hd0,msdos1) this is Lubuntu and (hd1,msdos1) this one is Boot Repair

with: ls (hd2,gpt2)/ I get lost+found/ boot/ ect/ -I think these are the Ubuntu files
With: ls (hd2,gpt3)/efi/

I've tried to use this [https://ubuntuforums.org/showthread.php?t=1599293](https://ubuntuforums.org/showthread.php?t=1599293) and I keep getting errors because of secure boot

sorry the error is
Failed to open \EFI\Microsoft\Boot\grub64.efi -Not Found
Failed to load image \EFI\Microsoft\Boot\grub64.efi: Not Found
start_Image() returned Not Found

when trying the above I get error: invalid EFI file path.

Ok let me try to explain this better. My laptop had windows 8.1 on it. I used a Lubuntu USB to install the OS and delete windows, and it was UEFI. When I tried to install it, I got and error with the grub installation.
I used Boot Repair to fix it and then when I rebooted it again I got the error messages

Failed to open \EFI\Microsoft\Boot\grub64.efi -Not Found
Failed to load image \EFI\Microsoft\Boot\grub64.efi: Not Found
start_Image() returned Not Found

Then it does straight to grub>promp

when I try to load modules I get this error-
error secure boot forbids loading module from

---

### Post by yancek on 2017-04-11
Did you install Lubuntu UEFI?   If you installed Grub to the MBR (/dev/sda on the installer) then the EFI files are not used.  My understanding is that HP does not conform to the UEFI standards so I'm not sure what you should expect to see if you are booting UEFI.  Since you have boot repair, run it again and just select the option to Create BootInfo Summary and when it finishes it will give you a link to the output.  Post that link here.

---

### Post by heema-d on 2017-04-11
I would like to thank you guys for your help. I found out if I spamed the f10 key I could get into BIOS/UEFI setting.

---

### Post by Bashing-om on 2017-04-11
heema-d; That is just ---- Great

Sometimes all it takes is a bit of hand holding.


[INDENT][INDENT]seek and ye shall find
[/INDENT][/INDENT]

---

