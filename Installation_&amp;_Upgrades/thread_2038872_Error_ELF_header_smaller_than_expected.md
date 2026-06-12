---
title: "Error: ELF header smaller than expected"
date: 2012-08-07
forum: Installation &amp; Upgrades
---

### Post by alioz on 2012-08-07
[FONT=Times New Roman][SIZE=3]Hi guys,[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]I find myself in a somewhat similar situation and my brain has run out of ideas...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]I got hold of an old Eee pc. I don t remember which Windows was on it but I have tried to install Ubuntu 12.04 with a live usb as a dual-os. Everything went ok and both os were working pretty well. (quick question: is it normal that if I remove the usb driver (live usb), then the computer does not show a grub screen and boot straight into windows??)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Anyway, here is my real problem, I am not certain what I have done but everything was alright, I think I was trying to find a solution to completely delete windows or something that would help me to work on Ubuntu without the USB but keeping both os….and paffff I can’t use the computer anymore!!! Now, as soon as I turn it on, I get a black screen with the following:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Error: ELF header smaller than expected[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]grub rescue>[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]I have tried many things from the internet but impossible to solve it, I can’t even reinstall Ubuntu, impossible to get another screen whether I use the USB or not. The computer does not reach the BIOS so I can t set him to boot on the USB. I can t login as root, since it does not recognize the command su or sudo. I know there has been many posts on this stuff but still could not find anything that suits my issue. I would be more than greatful if anyone could help me out or even redirect me somewhere that might be helpfully HELPFUL!! :)[/FONT][/SIZE]
[SIZE=3][FONT=Wingdings][FONT=Wingdings][/FONT][/FONT][/SIZE] 
[SIZE=3][FONT=Wingdings][FONT=Wingdings][/FONT][/FONT][/SIZE]

---

### Post by coffeecat on 2012-08-07
Moved to its own thread and given suitable title.

@alioz, please use the default font and size, except for highlighting or emphasis purposes.

---

### Post by alioz on 2012-08-07
hey sure, sorry for that. Thanks for your help!

Also I am not a complete noob but defo not an expert...

Cheers

---

### Post by alioz on 2012-08-13
can anyone help pls??

---

### Post by oldfred on 2012-08-13
I just might reinstall grub2. Something is missing. If Boot-Repair does not fix it, then post link to Boot-Info report.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

