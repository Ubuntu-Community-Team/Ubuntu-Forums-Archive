---
title: "bual boot - windows/ubuntu. no boot manager"
date: 2012-11-03
forum: Installation &amp; Upgrades
---

### Post by eightshot on 2012-11-03
this is what i have done so far:

formatter HD
installed Win 7
parted of 50% of the drive space
installed Ubuntu on the empty half
rebooted

on reboot the computer took me straight though to windows, bypassing ubuntu completely.

i have checked around the net, i have the "time out" on the boot manager set to 30 seconds. so that isnt the issue.

any help would be much appreciated as im new to ubuntu (really sick of windows).

thanks

---

### Post by spideryada on 2012-11-03
The simple way was to not partition the drive in the first place and install side by side with windows. The option, to install to a partition, is more difficult as you would have had to make a small partition that was formatted as a swap file. You would have to do a custom install. I'm not sure what you did.

---

### Post by oldfred on 2012-11-03
Welcome to the forums.

If you are booting Windows, then grub2's boot loader did not get installed to the MBR.

Post the link to the BootInfo report that this creates. It may also fix your issue by offering to install grub2's boot loader to the MBR.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by eightshot on 2012-11-03
thanks for the advice, iv managed to get it going now, as you said the GRUB didnt install correctly for some reason.

i wanted to keep the two installs very seperate so that my linux stuff was difficult to access from windows.

Only issue i have now is that linux is running deathly slow.

---

### Post by eightshot on 2012-11-03
scratch all that, im not using an OS that has THAT much adverting built in, ever.

its supposed to be a free OS. ill stick with windows.

---

### Post by tlhIngan on 2013-01-05
> **eightshot said:**
> scratch all that, im not using an OS that has THAT much adverting built in, ever.

What are you talking about?

---

