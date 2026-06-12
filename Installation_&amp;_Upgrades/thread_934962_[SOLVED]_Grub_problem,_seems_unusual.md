---
title: "[SOLVED] Grub problem, seems unusual?"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by sidneylopsides on 2008-10-01
I got a new laptop yesterday, it came with Vista home basic installed, the hard drive split into two 30GB partitions, one with Vista, one blank. There is also a 10GB recovery partition.

I installed Ubuntu on the blank space, splitting a 2GB swap partition during install.
Ubuntu boots fine, and Grub shows two Vistas, the first one is the recovery system and that launches fine. 

The second one must be Vista proper, but when I select that it shows Grub stage 2 then restarts Grub, complete with countdown to auto start top option. 

I've been searching around but not found anything about this problem, there are no errors to look for, and searching for Grub restarting is just giving me results for rebooting issues. 
Any ideas guys? I'm still new to the world of Linux so not sure what to do!

---

### Post by caljohnsmith on 2008-10-01
> **sidneylopsides said:**
> I got a new laptop yesterday, it came with Vista home basic installed, the hard drive split into two 30GB partitions, one with Vista, one blank. There is also a 10GB recovery partition.

I installed Ubuntu on the blank space, splitting a 2GB swap partition during install.
Ubuntu boots fine, and Grub shows two Vistas, the first one is the recovery system and that launches fine. 

The second one must be Vista proper, but when I select that it shows Grub stage 2 then restarts Grub, complete with countdown to auto start top option. 

I've been searching around but not found anything about this problem, there are no errors to look for, and searching for Grub restarting is just giving me results for rebooting issues. 
Any ideas guys? I'm still new to the world of Linux so not sure what to do!
The behavior you describe typically happens when you accidentally install Grub to the boot sector of your Windows partition; in order to boot Windows, Grub (or any other boot loader you might use) simply "chain loads" or tries to boot the boot sector of the Windows partition. It is the Windows partition boot sector that knows how to actually boot Windows by booting the correct Windows files. So on start up, when you get the Grub menu, if you try and boot a Windows partition which has Grub in its boot sector, Grub merely boots itself and you end up going back to the Grub menu like you did. :)

Bottom line, to correct the issue, you need to reinstall Vista's boot sector. Since you have a Vista recovery partition, if when you boot into it you can somehow get a command line prompt, the command you want to run is:
```
bootrec /fixboot
```
I'm not sure your recovery partition will even have that command, so if it doesn't, you an download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/") and do it from the CD. Let me know how it goes.

---

### Post by sidneylopsides on 2008-10-01
Thanks, that makes sense!
I couldn't get to a command prompt, it's Acer software...
So I decided to run a recovery and see whatw happened, and of course I lost the grub loader.
Then I remembered I had an Ubuntu LiveCD with me, looked in my bag to find my Windows disc too... oops.
Now just need to get grub on again.


edit: fixed!

---

