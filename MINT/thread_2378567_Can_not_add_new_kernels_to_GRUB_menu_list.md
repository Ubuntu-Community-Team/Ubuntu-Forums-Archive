---
title: "Can not add new kernels to GRUB menu list"
date: 2017-11-24
forum: MINT
---

### Post by pchokola on 2017-11-24
I have Linux Mint (Based off of Ubuntu) installed on my laptop alongside Centos 7, but after updating the kernels on both OS's, I can't get the new kernels to show up in the bootup menu list.

Here is my configuration

[COLOR=#333333][FONT=&quot]I have the following setup on a T470.[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]NVME SSD (Drive #1) = Windows 10 (No problems here. Everything running OK)[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]SSD (Drive #2)[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]First two partitions = Centos 7. (I installed this first).[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Fourth partition = Linux Mint 18 - 64 bit Cinnamon.[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]I use the BIOS boot menu to pick which drive I want to use and then pick th OS I want. 

[/FONT][/COLOR]So this all works fine and I can select each OS.  However after updating the kernels on Centos and Mint, I can't get the new kernels to show up on the grub boot menu.  I have tried a couple commands like grub-mkconfig and it adds the new kernels to the grub file, but they don't show up in the menu list.  Maybe I just don't know which grub is being used or the proper command.

---

### Post by deadflowr on 2017-11-24
*Thread moved to **MINT***

---

### Post by jeremy31 on 2017-11-24
Boot into Linux Mint and open terminal, run
```
sudo update-grub
```
Then see if the kernels show in the list correctly

---

### Post by pchokola on 2017-11-24
Well, it found all the kernels in Mint at least, but the bootup menu has not been updated.  Not sure, but I am leaning to believe that the grub in Centos needs to be updated, but I have not been able to do that.

---

### Post by Dennis N on 2017-11-24
Updating grub in Linux Mint is not going to update the Mint kernel versions that show in the CentOS grub menu. You will have to boot into CentOS, and update grub again. And vice-versa. The os prober in each needs to be working when grub is updated.

---

### Post by pchokola on 2017-11-24
> **Dennis N said:**
> Updating grub in Linux Mint is not going to update the Mint kernel versions that show in the CentOS grub menu. You will have to boot into CentOS, and update grub again. And vice-versa. The os prober in each needs to be working when grub is updated.

Yes I am aware of that.  I am trying to find out the proper command to update the GRUB in Centos.  I have tried the grub2-mkconfig command, and it adds the new kernels to grub, but they still don't show up in the menu, so trying to find out why.

---

### Post by jeremy31 on 2017-11-24
If Linux Mint was the last distro installed the command will have to be run there, unless you reinstall grub from Centos and update grub.  The last Distro to install grub has control of it

---

### Post by pchokola on 2017-11-24
[COLOR=#333333][FONT=&quot]I tried the following in Centos:

grub2-mkconfig -o /boot/grub2/grub.cfg, 

and all the kernels show up from Centos and Mint in the file /boot/grub2/grub.cfg, but they are still not in the boot up menu.

I do notice that there is a separate and older dated /boot/grub.cfg with the current menu list.

Am I now supposed to copy /boot/grub2/grub/cfg into /boot/grub/cfg and everything will work? If that works it seems like something is not set up properly or I am running the wrong command.[/FONT][/COLOR]

---

### Post by oldfred on 2017-11-24
Does Centos have a full grub.cfg in /EFI/centos? In the ESP - efi system partition.
Ubuntu only puts a configile (chain type) entry in /EFI/ubuntu which then loads a full grub.cfg from the install partition.

---

### Post by pchokola on 2017-11-24
Well originally I came across this:

[https://wiki.centos.org/HowTos/Grub2](https://wiki.centos.org/HowTos/Grub2)

and tried

grub2-mkconfig -o /boot/efi/EFI/centos/grub.cfg

But after doing that I lost any entry for Linux Mint and couldn't get in at all.  At that point I restored both OS's from an image backup. So, now there is no entry there and I am trying other things.

---

### Post by pchokola on 2017-11-30
SOLVED:

After playing around a bit......

1) Booted up intoLinux Mint and ran


update-grub


2) Booted up intoCentos and ran


grub2-mkconfig -o/boot/grub/grub.cfg

---

