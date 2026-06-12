---
title: "dual install went horribly wrong"
date: 2015-11-08
forum: Installation &amp; Upgrades
---

### Post by luitjan on 2015-11-08
dear all, any help appreciated! I just installed Ubuntu on a pc that already had windows 10 installed. During the install, it was detected that wibndows 10 was already there, and I chose the default option to have ubuntu installed along with windows. After the install was finished, I was prompted to restart, removing the dvd. I did that, and after restarting I had a screen where I could choose to start ubuntu, or windows. So far everything fine. I chose windows, logged on to windows (so it was till there) , I saw everything was still there,yeey, and then I hit restart, to try out ubuntu... and then my computer stayed on the restart screen...  it just said "restarting", not "configuring" or anything else... after a few minutes I lost patience and went for a hard shutdown. Now when I turn my computer on, I get immediately a screen saying "Gnu grub version 2.02 beta2-9ubuntu1.3   Minimal BASH-like line editing is supported (...)  followed by a command prompt grub>

Unfortunately, I cannot type anything at that command prompt, no  matter what key I hit .. apparently it hasnt detected my usb-keyboard or not loaded its driver. 
I also do not get the typical startup screen with the "American megatrends" logo and those options to hit f2 or del to enter setup, it goes straight to the grub prompt. 
Is there anything I can do? without being able to type anything at that prompt probably not much..
I have tried inserting the ubuntu dvd and the windows 10 dvd, hoping it would start from those, but no luck... just the grub command prompt. 
Any ideas? Many thanks in advance.

---

### Post by yancek on 2015-11-08
If you have windows 10, you might be using UEFI.  If that is the case, you would have needed to select the option to install Ubuntu in UEFI.  I don't know if that will happen if you choose the auto-install method, "Install Alongside" which it seems you did?  If you can check that and post the info it might help.  You might also google "boot repair ubuntu" and go to the site and download and run it from your installation medium.  Select the Create BootInfo summary option and do not try to make any repairs.  Post the link to the output here and someone with more knowledge of UEFI should be able to help.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by luitjan on 2015-11-09
Thanks for your reply. I indeed chose the "install alongside" option.  I have tried to boot on a boot repair usb stick as you suggested, but it didn't work. I just get the bash command prompt and it ignores the usb. I have decided to call in a technician, pay the bill, etc. I guess it's the only way out, But thanks again for helping!

---

### Post by yancek on 2015-11-09
You need to change the boot priority in the BIOS before it will boot from the usb.  Usually when you boot, you will see a manufacturers logo and at the bottom of the screen it should tell you which key to press to "enter setup".

Most technicians don't know anything about Linux but you might get lucky.  Usually the repair they do will be to use a recovery CD to set windows to default or reinstall windows.  Make sure that if you have data on the drive you want you try to back it up or let the technician know you need it and have him/her do it.

If you decide to try Ubuntu again, reading the documentation at the page below should help with UEFI.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

