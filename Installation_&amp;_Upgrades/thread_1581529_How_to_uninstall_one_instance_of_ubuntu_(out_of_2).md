---
title: "How to uninstall one instance of ubuntu (out of 2) ?"
date: 2010-09-25
forum: Installation &amp; Upgrades
---

### Post by sl789 on 2010-09-25
I have triple boot : WinXP, ubuntu 10.04 and couple of days ago I also installed ubuntu 10.10 alongside them to try it out.

Now I would like to remove  10.10 (I'll wait until to official release). I've never uninstalled one instance of ubuntu out of 2. What is the best way to do it ?

Would it be enough to simply delete its partition and then run update-grub or I need to do more ?

---

### Post by Rubi1200 on 2010-09-25
If you put 10.10 on its own partition, use GParted from the LiveCD to delete it.

I assume you installed 10.10 after 10.04?

If so you will have to reinstall GRUB since 10.10 would have done that unless you chose not to install the bootloader.

If you did not install the bootloader simply run ```
sudo update-grub
``` in 10.04

To reinstall GRUB:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by sl789 on 2010-09-25
Hi Rubi !

Thanks a lot for a quick reply. I have Gparted so to delete partition with 10.10 is not a problem. One additional question regarding GRUB re installation ( I realize it might be a stupid one) This is considering

> I assume you installed 10.10 after 10.04?
> If so you will have to reinstall GRUB since 10.10 would have done that unless you 
> chose not to install the bootloader.


On my harddrive the order of OS is as follows (indeed I installed 10.10 after 10.04)

First is small DEllUtility partition -                           **sda1 **
then  NTFS partition with WinXP                             **sda2** 
After it a another small partition called DellRestore** sda3.**
That's how my Dell Desktop was when I bought it.

 Then extended partition which I created - **sda4 **prior to 10.04 install
under which are 
Linux swap                         **sda5**
Ubuntu 10.04                     ** sda6** and finally
Ubuntu 10.10                      **sda7** which is last and which I manually created  to install 10.10 couple of days ago

If I am in ubuntu 10.04 (sda6 partition) - I have Gparted installed there and I use it to delete sda7 with 10.10, does it remove Grub ? I thought it's part of 10.04 install.

Regarding bootloader, as far as I understand (and I am pretty sure) I do have a bootloader and it is located in WinXP partition.

---

### Post by Rubi1200 on 2010-09-25
GRUB would have been installed with 10.04 but if you let 10.10 install without selecting to not install the bootloader then GRUB is now part of the 10.10 install.

If you remove 10.10 you will also remove GRUB.

The solution is to use a LiveCD and reinstall GRUB (not a complicated process).

When you reinstall you need to mount sda6 and install the bootloader to sda.

The bootloader on the Windows partition will be the Windows bootloader (quite separate from GRUB).

If you are unsure and want to play it safe, post the results of the bootscript linked to at the bottom of my post. You can do this from within Ubuntu if you wish. I can then explain to you what the results mean.

Let me know and I will continue offering help as you need it.

---

### Post by sl789 on 2010-09-25
Rubi , thanks a lot for the clarification. 

I do have a recollection now that when I installed 10.10 I have chosen to install bootloader.

so that, I am going to try what you've recommended tomorrow morning  (it's 1.30am my time)  and I'll definetely publish the result. 

Again, many thanks for explanation and for offering help.

---

### Post by Rubi1200 on 2010-09-25
No problem, you are more than welcome :)

---

### Post by sl789 on 2010-09-25
Hi Rubi, 

Thanks for the explanations and especially for the link to
BootInfoScript, this was most useful. I wish I had this script before.
I didn't have any problems today but I run it prior and after just to see the results.
Now I know what to do first in case of any boot problems - just run it to see exactly what's going on.

I've deleted partition and reinstalled GRUB from LiveCD with no problem just few minutes ago

---

### Post by Rubi1200 on 2010-09-25
> **sl789 said:**
> Hi Rubi, 

Thanks for the explanations and especially for the link to
BootInfoScript, this was most useful. I wish I had this script before.
I didn't have any problems today but I run it prior and after just to see the results.
Now I know what to do first in case of any boot problems - just run it to see exactly what's going on.

I've deleted partition and reinstalled GRUB from LiveCD with no problem just few minutes ago
Excellent! I am glad you got it sorted out :)

The bootscript is a fantastic tool and many of us here use it not only to help troubleshoot problems, but also to do as you did and run before and after versions; very nice!

Please mark this thread Solved using the Thread Tools near the top of the page.

---

