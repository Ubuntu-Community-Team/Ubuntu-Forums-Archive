---
title: "Ubuntu 10.04 beta &amp; VMware Fusion"
date: 2010-04-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by masmullin on 2010-04-01
Hi

I installed Ubuntu 10.04 as a virtual machine using VMware fusion version 3 (Version 3.0.0 (204229)).  After installing everything was ok, however after doing an upgrade the keyboard wasn't working.

Im willing to wait for the official release, but I just thought I should make you aware of the bug.

---

### Post by baylf2000 on 2010-04-05
> **masmullin said:**
> Hi

I installed Ubuntu 10.04 as a virtual machine using VMware fusion version 3 (Version 3.0.0 (204229)).  After installing everything was ok, however after doing an upgrade the keyboard wasn't working.

Im willing to wait for the official release, but I just thought I should make you aware of the bug.

I'm having the exact same problem. Installed Beta 1 in VMware Fusion 3 with no problems, but after upgrading from the Ubuntu upgrade tool and a reboot the login screen will not accept any input from the keyboard. I even tried accessing the login screen using VNC but it still would not accept any input.

VMware is version 3.0.2
OSX is 10.6.3

Hope this helps.

---

### Post by cyberfunk on 2010-04-07
I'm having the exact same problem... 

Did anyone else get a weird stall on the "Grub loading" screen for a few seconds during boot... 

I also noticed a weird Grub dialog on upgrading from 9 that gave me no choice.. .

The weird message on upgrade that tells me i've chosen not to install grub.. and do i want to continue in the fashion ?

and my only options are to click forward or to click the checkbox that says "i understand what i'm doing, dont install grub" and then forward..

When i click forward w/out checking the box it wont let me advance



In either case, I noted that the keyboard works fine AFTER you get past the login screen (use the virtual keyboard to click in your password), but not on the login screen itself.  It still has the same problem after reboot

---

### Post by dcstar on 2010-04-07
> **cyberfunk said:**
> 
.........
In either case, I noted that the keyboard works fine AFTER you get past the login screen (use the virtual keyboard to click in your password), but not on the login screen itself.  It still has the same problem after reboot

I have the exact same thing in a 10.04 VM I created with VMware Player 3 beta - but previous VMs created with VMware Server 1.0.10 work fine!

---

### Post by y@w on 2010-04-09
Same here except when I try to launch the on-screen keyboard it pops up a window for a moment and it disappears :(

---

### Post by PJAMA on 2010-04-09
> **dcstar said:**
> I have the exact same thing in a 10.04 VM I created with VMware Player 3 beta

That's what I have too, But With 10.04 beta 2. I'm seeing if this is fixed on beta 2. :confused:

---

### Post by cariboo on 2010-04-09
Virtualbox had the same problem before it was updated to the latest version. I use the puel version, not the one from the repositories. I would suggest filing a bug with VMWare.

---

### Post by dcstar on 2010-04-10
> **masmullin said:**
> Hi

I installed Ubuntu 10.04 as a virtual machine using VMware fusion version 3 (Version 3.0.0 (204229)).  After installing everything was ok, however after doing an upgrade the keyboard wasn't working.


Installing 10.04 as a VM using the VMware "Easy Install" option doesn't work correctly (it assumes that the HAL exists, it no longer does), use the other option that requires you to do a "normal" install and see what happens.

And have a look at this for a possible solution:

[http://spininfo.homelinux.com/news/VMware_VI3_v3.5_New_Features:_ESX_3i,_ESX_3.5,_VirtualCenter_2.5/2010/04/06/Problem_with_VMware_s_Easy_Install_with_Ubuntu_10.04_%28Lucid%29_-_keyboard_broken](http://spininfo.homelinux.com/news/VMware_VI3_v3.5_New_Features:_ESX_3i,_ESX_3.5,_VirtualCenter_2.5/2010/04/06/Problem_with_VMware_s_Easy_Install_with_Ubuntu_10.04_%28Lucid%29_-_keyboard_broken)

---

