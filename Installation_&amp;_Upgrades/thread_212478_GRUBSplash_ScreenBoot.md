---
title: "GRUB/Splash Screen/Boot"
date: 2006-07-09
forum: Installation &amp; Upgrades
---

### Post by coolis on 2006-07-09
I tried adding a new splash screen.

So I put the file in the "/boot/grub/splash.xpm.gz" directory, and add this line into "/boot/grub/menu.lst" :

> splashimage=(hd1,0)/boot/grub/splashimage.xpm.gz

Notice that I put the wrong file name into that line of code.  So it should be "splash.xpm.gz" and not "splashimage...".  I rebooted, and I get a message that says:

> Failed to read splash image ((hd1,0)/boot/grub/splashimage.xpm.gz
Press any key to continue...

So I do.  I can either press "ESC" to go into a menu with several kernel options, or it tries to reboot, which it fails again.  Under this list of kernel options, there are options to press "e" to edit whatever commands before booting, or "c" for a command line.  At this point.  I have no idea what to do, so I load up my Ubuntu 6.06 live CD.

Note: when I try to press "c" during the kernel option screen, it automatically reboots.  "e" takes me to a place that seems like it could help, but I don't know what to do there.

I read somewhere that I can try to reinstall the Live CD and not format the  harddisk.  So I try that method, but the instruction that site gave didn't work because I couldn't load GRUB during the installation process.

Here is what I think I could do but I don't know how:

1) somehow reinstall the boot sector
2) somehow fix the /boot/grub/menu.lst file since I know the name of the splash image
3) get rid of that new line of code I put into /boot/grub/menu.lst
4) change the name of the file so it matches whatever is in the menu.lst file.
5) get into my /boot/grub/ using my Live CD.
6) restore GRUB or the boot process to its original goodness.

Thanks in advance.  If I posted this into the wrong sub-forum, or whatever, just kindly correct me and I'll go wherever I need to.

---

### Post by Dr. Nick on 2006-07-10
when you get the list of kernels after the first error have you tried one of the recovery options?

If you can get into it then you can edit the menu.lst using nano like you did origionally 

**sudo nano /boot/grub/menu.lst**

then remove the bad line

---

### Post by coolis on 2006-07-10
Yes, I have tried that, and that only reboots the system.  so i can't go into recovery mode.

So far, I have taken someone's advice and mounted my hardrive onto the live CD directory system (That's the best way i could explain what i did) and i have proceded to recovering some of my important files.  thankfully i didn't have too much that was important.

edit:

i wish i had more time to fix this, but i got the few files that i needed, and i need my laptop for tomorrow, so i'm reinstalling ubuntu.  too bad, cus this coulda been a good learning experience.

---

### Post by Herman on 2006-07-10
Hello, coolis, sorry I didn't get home in time to help you. 
Here's are a few different solutions to your problem. (For future adventures or for someone else viewing this thread maybe.)

First, here's what to do when you get the GRUB Command Line Interface, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").

You can mount your Ubuntu filesytem (partition) on your hard-disk using the 'Desktop' Live CD  and access your /boot/grub/menu.lst to edit it. Here is an example. [*Click Here.*]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")

You can re-install Grub from the Live CD. [*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

All the best with your future Ubuntuing! Regards, Herman :)

---

### Post by kd5kij on 2006-07-12
Herman, many thanks for you advice. I had the same problem with my laptop after trying to add a custom splash image. Anything I did at the GRUB screen would cause the computer to reboot, except pressing 'e' to go into edit mode. Choosing any of the menu entries, or 'c' for the command line rebooted the computer. I booted to the Live CD and mounted my /boot partition and edited my menu.lst file using the instructions you provided. Finally, I can boot again. Thanks again for your help, people like you make the Linux community enjoyable.

---

