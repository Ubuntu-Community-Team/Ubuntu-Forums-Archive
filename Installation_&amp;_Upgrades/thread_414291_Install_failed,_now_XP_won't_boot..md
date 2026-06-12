---
title: "Install failed, now XP won't boot."
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by c_fraser_hopewell on 2007-04-19
Hi,

I am having problems after a failed install of 7.04

During install I elected to resize my current XP partition and install Ubuntu in the remaining space.  Shortly after the install began I got an error message saying that there was an error on the disk and that the install would be canceled (i'm sorry I can't remember the exact wording).  The installer quit and put me back to the live CD desktop.

After quitting Ubuntu and restarting I then got a message saying "error loading operating system" during boot and the system hung.  I tried to do a repair install of XP, but still get the same message before the system is able to boot into the repair install.

I rebooted into the Ubuntu Live CD to see what I could see on the drives and it appears that all the original XP install is there, along with a couple of new partitions that appear to contain Ubuntu files.  If I try to run the installer now, the only options I am offered are complete formats of the two drives - no option to repartition.

Can anybody suggest anything that I might try before I have to resort to a full reinstall of XP?

Thanks,

Charlie.

---

### Post by IDK on 2007-04-19
You need a boot loader.  Reinstall Ubuntu and see if it completes an install.  After you get grub installed you should be good to go with your windows partition.

---

### Post by cogadh on 2007-04-19
If you want to get back to the way things were, just boot up your XP install disk, select the Repair option, select your Windows drive, then type "fixmbr" at the command prompt. Reboot and Windows should load normally.

---

### Post by c_fraser_hopewell on 2007-04-20
Thank you both for your suggestions.

I did try another re-install, but the installer only gives me the option to use the whole of either of the drives, whereas there was an option to create a smaller partition before.  I don't really have the confidence to start messing about with the "manual" option at the moment - I'm a bit of a linux noob you see! :) 

I'll give the repair option a go and see what happens.

Thanks guys.

---

### Post by c_fraser_hopewell on 2007-04-20
Ok, I tried fixmbr, but to no avail.  I still get the same "error loading operating system" message.

When  I use the map command in recovery console I can see the windows partition and then 2 other partitions (ubuntu and it's swap file?).  

Is the problem bring caused by Ubuntu's bootloader being damaged due to the failed install and thus causing the system to hang during boot?

---

### Post by rich.bradshaw on 2007-04-20
Boot from Windows repair disk as you did, 

fdisk /mbr

it wont say anything, but when you reboot it will go into Windows. This removes GRUB, so to get back into Ubuntu you will have to reinstall (or get grub back - not sure how to do that from Ubuntu CD).

---

### Post by c_fraser_hopewell on 2007-04-20
Oh dear, I think my messing about with fixmbr has knackered the partition tables, i can't seem to access the c: drive at all now :(   All I get is "An error occured during directory enumeration" when I try to call up the directory.

Looks like I am going to have to do a clean re-install and then try a data recovery tool to see what can be salvaged.  

Thanks to everyone who offered their advice though.

---

### Post by allforcarrie on 2007-04-21
google for NTLD fix. its hte windows version of grub.

---

