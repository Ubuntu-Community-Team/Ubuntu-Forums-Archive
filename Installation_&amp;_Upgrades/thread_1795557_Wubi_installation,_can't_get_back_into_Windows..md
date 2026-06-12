---
title: "Wubi installation, can't get back into Windows."
date: 2011-07-02
forum: Installation &amp; Upgrades
---

### Post by CyberAlyMan on 2011-07-02
I've been a bit stupid. This is all in a bootcamp partition on my MacBook Pro so it's totally undo-able should worst come to worst, but i'd rather save myself some hassle, so here we go...

I installed windows via bootcamp, and on top of that i've got an Ubuntu installation through Wubi, 11.04. I could have triple booted I guess but I just thought this would be easier. Anyway I was using Ubuntu more and more so I decided to make it skip the question of wether I wanted to use Windows or Ubuntu, so in Windows I went to System Settings or whatever it's called and I unticked the box which made the bootloader count down from 10, so now instead of giving me a choice between Ubuntu and Windows it just goes straight for Ubuntu.

What I didn't consider was how i'd undo this! I want to get back into the Windows installation but I don't have any time to choose it before it starts booting ubuntu. Choosing Windows from GRUB only resets the loop and I end up straight back in GRUB. Is there a button I can hold to freeze the windows bootloader? Is there I way I can edit the Windows system settings from inside Ubuntu? Is there any way I can forgive myself for being this stupid?

Thanks in advance for any advice you can give me!

---

### Post by Rubi1200 on 2011-07-03
Hi,
this is theoretically fixable, but we need to know which version of Windows you are using and whether you have the installation/recovery disks for it.

Thanks.

---

### Post by CyberAlyMan on 2011-07-03
I'm using Windows 7 Home Premium and I do have the recovery disc.

---

### Post by Rubi1200 on 2011-07-03
Okay, that is great news because here is what you need to do to fix this:

If you have the Windows 7 Rescue Disk boot from it. 

Do not choose to restore anything. 

Open a command window and run "bcdedit"; this will list the BCD info. 

In the "Windows Boot Manager" section I assume that the timeout value is 0. To change it to 30 seconds you would run "bcdedit /timeout 30" (without quotes; also for the first command). 

Exit the command window and reboot. 

You should have the boot menu again.

---

### Post by CyberAlyMan on 2011-07-03
Good news! It worked perfectly, thanks!

To elaborate on the instructions, you have to choose your keyboard language, press 'Repair My Computer' instead of 'Install Now', choose your Windows partition and hit Next, then you'll be given five options, and command prompt is the bottom one. From there follow the previous instructions.

Thanks for the help again.

---

### Post by Rubi1200 on 2011-07-03
Firstly, thanks for providing the additional information about the correct procedure; appreciated.

Second, great that this worked for you :-)

Please mark this Solved using the Thread Tools near the top of the page.

Enjoy!

---

