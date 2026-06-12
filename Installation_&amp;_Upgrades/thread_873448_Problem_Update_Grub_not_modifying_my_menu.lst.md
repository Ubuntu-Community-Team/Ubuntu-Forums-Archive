---
title: "Problem: Update Grub not modifying my menu.lst"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by DemaSRV on 2008-07-29
After some searching I've found my problem is the exact same as found here: [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/202009](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/202009)

Is there any known fix for this?  At one point I told something to keep my old kernel and I'm assuming like in the comments that this is why update-grub is not changing my menu.lst at all.  Is there some option somewhere I can go change to get update-grub working again?

---

### Post by DemaSRV on 2008-07-29
bump

---

### Post by webkris on 2009-04-14
I'm disappointed that no one has touched this...
**[COLOR="SeaGreen"][SIZE="4"]Here are some answers:[/SIZE][/COLOR]**

First there is a known bug where under some circumstances the **update-grub** command fails to put in the new kernel. 
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/202009](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/202009)

The quick fix is to delete the menu and have update-grub recreate it. There should already be a backup in your boot/grub folder called menu.lst~  What you have to do is delete the menu.lst

Here we go: 
```
sudo rm boot/grub/menu.lst

```

Now that it's deleted, run update-grub to create a fresh one.
Hit YES when prompted:
```
kris@phobosx:/boot/grub$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

Now take a look at the grub menu.lst (gedit boot/grub/menu.lst) and see if your new kernel is there:

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		8018534e-46c0-492f-8ae2-a935019756b3
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8018534e-46c0-492f-8ae2-a935019756b3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

**YEAH!**
Hopefully they will fix update-grub soon.
I guess not booting the correct kernel of your OS is not too important. :p
- Kris

---

### Post by A_M_S on 2009-09-14
I  know that this is an old tread but Tnx for the tips! 
I was with this annoying issue for some time.
Deleting the menu.lst worked for me! :)

---

### Post by pretzel5555 on 2010-03-03
Hi to all,
I`m using Ubuntu 9.10, Grub 2 v.1.97 beta 4.

I have met the same problem, but deleting menu.lst could not be made:

```
pretzel@pretzel-laptop:~$ sudo rm boot/grub/menu.lst
[sudo] password for pretzel: 
rm: cannot remove `boot/grub/menu.lst': No such file or directory
pretzel@pretzel-laptop:~$ sudo rm /boot/grub/menu.lst

```
Did anyone know where & what to check?

---

### Post by presence1960 on 2010-03-03
> **pretzel5555 said:**
> Hi to all,
I`m using Ubuntu 9.10, Grub 2 v.1.97 beta 4.

I have met the same problem, but deleting menu.lst could not be made:

```
pretzel@pretzel-laptop:~$ sudo rm boot/grub/menu.lst
[sudo] password for pretzel: 
rm: cannot remove `boot/grub/menu.lst': No such file or directory
pretzel@pretzel-laptop:~$ sudo rm /boot/grub/menu.lst

```
Did anyone know where & what to check?

9.10 does not use menu.lst unless you did a dist-upgrade from 9.04. if you did a clean install of 9.10 you have GRUB2 which is totally different from GRUB Legacy? Exactly what is it you want to accomplish?

If you want to refresh your GRUB menu open a terminal and run ```
sudo update-grub
```

---

### Post by pretzel5555 on 2010-03-03
> **presence1960 said:**
> 
If you want to refresh your GRUB menu open a terminal and run ```
sudo update-grub
```

All right. This written in Grub 2 manual. I have clean install of 9.10. I need to change default entry and when I change it, I run ```
sudo update-grub
```. After it I receive information, that founded 3 OS, 0 errors, etc. Then I reboot and see, that nothing changed. 
> **presence1960 said:**
> 
9.10 does not use menu.lst
As I understood from docs, menu.lst generates automaticaly by command "update-grub" and used for menu, is not it?

---

### Post by presence1960 on 2010-03-03
> **pretzel5555 said:**
> All right. This written in Grub 2 manual. I have clean install of 9.10. I need to change default entry and when I change it, I run ```
sudo update-grub
```. After it I receive information, that founded 3 OS, 0 errors, etc. Then I reboot and see, that nothing changed. 

**_As I understood from docs, menu.lst generates automaticaly by command "update-grub" and used for menu, is not it?_**

Not for GRUB 2. You are reading docs for Legacy GRUB 0.97. It is obvious you need to read up on how GRUB 2 works. See here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by pretzel5555 on 2010-03-03
Thanks for this link, but I already read it. Look, I had changed the parameter *GRUB_DEFAULT=0* to *GRUB_DEFAULT=2* in the */etc/default/grub* and succsesfully saved it. Then I typed a command *sudo update-grub* and it finished also succsesfully. But in menu nothing has changed after reboot! Default entry  remain as with parameter *GRUB_DEFAULT=0*! Did you know how to change it?
Also after if I open */etc/default/grub* I see that parameter *GRUB_DEFAULT=2*

Relative to
> As I understood from docs, menu.lst generates automaticaly by command "update-grub" and used for menu, is not it?
I confused. I thought and wanted to write grub.cfg generates automaticaly by command "update-grub" and used for menu.

---

### Post by t1m3 on 2011-01-22
- following the steps above didn't work EXACTLY but it got me to a solution.

my situation: I had all my operating systems installed but grub wasn't working correctly.

after i:

- loaded the live CD
* with either 'acpi=off' or 'nolapic' f6 option on..

- went to the terminal

- mounted the linux drive
i.e. sudo mount /dev/sda1 /mnt
*1 is for first partition (where linux was for me)

- uninstalled grub
i.e. sudo apt-get remove grub

reinstalled grub
- i.e. sudo apt-get install grub

removed the: boot/grub/menu.lst (lower case 'L')
- sudo rm menu.lst

updated grub
- sudo update-grub

--------------------------

- it didn't include any of the other kernels of linux, or windows 7.

- i continued to reboot
i.e. sudo shutdown -r now
- and i took the disk out.

- and it booted right into linux!

- from there I went to the terminal and updated grub
i.e. sudo update-grub

- and this time it included ALL the kernels and windows 7

- so, if anyone needs to break this down do it because this truly was a slightly random bunch of steps. but the end result was a success.

good luck.

---

