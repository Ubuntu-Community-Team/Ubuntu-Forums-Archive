---
title: "Should I try to fix 16.04 or format and restore from backup?"
date: 2017-01-25
forum: Installation &amp; Upgrades
---

### Post by johnspeedster on 2017-01-25
I foolishly left my laptop downloading updates whilst it was not plugged in......got distracted and when I returned the battery had gone flat.When recharged could not start Ubuntu. I get to a screen that ends up by  stating: end Kernel panic - not syncing: VFS: Unable to mount root fs  on unknown-block(0,0). At this point the keyboard is dead with only the  caps lock key flashing. 
I installed 15.05 from a previous live CD but cannot load any repair tools. During the boot up sequence now I still have the option of loading Ubuntu 16.04 (on /dev/sda5) or advanced options for 16.04 but the former still gets to the same screen as above and I don't understand the advanced options screen. 
The question is then, should I just cut my losses and format the hard drive (hasn't been formatted for many years) and restore from a recent backup, or is there a relatively simple way to get 16.04 back? 
Thanks in anticipation....

---

### Post by RobGoss on 2017-01-25
Are you able to boot up to your desktop?

I would try loading another kernel first it's not going to hurt anything, if that fails you can always try Boot repair. I had this same panic error a few days a go I ran boot repair installed the boot loader / grub and all was good

Maybe someone has better knowledge of this issue and can advise accordingly 

I would leave formatting and reinstalling as a last resort

---

### Post by ajgreeny on 2017-01-25
I assume you have installed 15.05? (15.04) alongside 16.04 as a dual boot temporarily, and not overwritten your 16.04; am I correct?

If so use that, but if it will not work either, run a live Ubuntu system from DVD or USB and using that run command ```
sudo e2fsck /dev/sdx#
```where sdx# is the root partition of the installed 16.04 system.

That command could find some filesystem errors and ask if you want to fix them.  Read what the error is and then select to run the fix, and you may find that following that you can at least start the system from the installed OS.

You could, however, still have problems getting to a GUI desktop and if you do, use Ctr+Alt+F1 to get to a command line login.  Having logged in there try running command ```
sudo apt-get install -f
```to fix any broken packages and then ```
sudo dpkg --configure -a
```which will continue the configuration of any packages that were downloaded but not fully configured and setup when the machine went into shutdown or suspend.

As Rob says, it is much too early at this time to rush to a reinstallation, though it may be necessary eventually.

---

### Post by johnspeedster on 2017-01-25
If I could find you two lovely persons I would kiss you both! Firstly I didn't know how to install another kernel, then when I checked for errors, sda5 came back clean. But that made me think a bit more about the messages and I remembered the advanced options. Tried using the most up-to-date version of kernel and got the same panic message. Realised that made sense so used the next newest one, and after pages of scrolling script, bingo, back in action.
 I just love this system where help is so freely given - and where I can learn at the same time. 
I'll check to see how to load the latest version of kernel next, then can someone remind me of the command to check for and delete unattached/unused/broken bits of code. Many thanks again!

---

### Post by RobGoss on 2017-01-25
We're you able to boot in to your desktop?

---

### Post by tech-j on 2017-01-25
Don't forget to mark this post as [Solved] so that they next person can follow the same steps to resolve an issue like this. :)
The commands that you are looking for are in "ajgreeny"'s post.
Another that you will want to run to fix your boot loader / kernel is:
update-grub

Thanks.
-Tech-J

---

### Post by ajgreeny on 2017-01-25
It will help to know what kernel version you are using at present which in 16.04 should be **4.4.0-59**, so what does **uname -a** in terminal show you as output?

If you currently are using a lower numbered version run command ```
sudo apt-get dist-upgrade
```
Do not worry; that will not update to the next Ubuntu version of 16.10, but it will update kernel version to the most recent, which **sudo apt-get upgrade** does not do.

I am not sure what you mean by the "command to check for and delete unattached/unused/broken bits of code."
maybe you are thinking of ```
sudo apt-get autoremove
```which, for example, removes old kernels except the two most recent.

---

### Post by Youngblood52 on 2017-01-26
**ajgreeny** & **RobGoss** ... *Thank You!*

By appending the "Boot Repair" links to the bottoms of your posts, you provided me with the critical Road Sign that I needed to solve some nagging Ubuntu dual-boot & flawed update issues on a couple of my systems.  :)

---

### Post by johnspeedster on 2017-01-29
Back after a short holiday at the beach.
All is good on the laptop!  So to go through the questions and comments above: uname -a gave 47 as  the kernel version - since updated to 59!! Tried to run dpkg and got 50  packages to be updated. This was aborted due to "Temporary failure  resolving ubuntu mirrors.uk2.net. After the update of kernel and running  autoremove, tried again and only 14 packages needed updating, but this  again was aborted "Temp failure NZ archive.ubuntu.com. Anyway, from  turning the laptop on now, it loads directly to the desktop of 16.04  with everything as it was before my mishap. I thank you all for your  help - much appreciated, and I have learnt a lot.

---

### Post by ajgreeny on 2017-01-30
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

