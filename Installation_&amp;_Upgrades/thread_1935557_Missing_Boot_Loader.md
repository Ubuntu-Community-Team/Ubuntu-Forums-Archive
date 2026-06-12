---
title: "Missing Boot Loader"
date: 2012-03-04
forum: Installation &amp; Upgrades
---

### Post by Tinky Winky on 2012-03-04
[SIZE=2][FONT=Verdana]Fo[/FONT][/SIZE][FONT=Verdana][SIZE=2]lks,

I've just installed Ubuntu 12.04 and after re-staring my machine, the boot loader I was expecting failed to appear and as a consequence the computer boots up one of MS's finest.[/SIZE][/FONT][FONT=Verdana][SIZE=2]  Obvious I would prefer to use Ubuntu and I was wondering if anyone would be so kind to assist me in resolve this minor problem.

In an attempt to resolve the issue I used ‘Easy BCD’ to create an appropriate booting option and selected the partition where Ubuntu resides.  However, when I select Ubuntu the machine told me there no associated booting file available but the partition has Ubuntu correctly installed in it.[/SIZE][/FONT] [FONT=Verdana][SIZE=2]

Any advice gratefully received.[/SIZE][/FONT] [FONT=Verdana][SIZE=2]

Kind regards[/SIZE][/FONT] [FONT=Verdana][SIZE=2]

Tinky Winky[/SIZE][/FONT] 
  [FONT=Verdana][SIZE=2]
[/SIZE][/FONT]

---

### Post by darkod on 2012-03-04
You can't simply add the ubuntu partition to the windows bootloader. For that to work, grub2 needs to be installed onto that partition, on the PBR. But this is not recommended anyway since grub2 can't fit on the PBR and during updates this setup can easily get broken.

If you have more than one hdd, grub2 maybe was installed on another disk? In this case try setting in BIOS to boot from another disk and see what happens.

Another option is that grub2 didn't install at all, in which case you can try to add it manually.

---

### Post by Tinky Winky on 2012-03-06
Thanks for the advice, I attempted this but unfortunately this did not work.  I re-install Ubuntu for a second time and again the same issue remains any other suggestions would be appreciate!

---

### Post by darkod on 2012-03-06
Do you have more than one hdd? In that case grub2 might be on another hdd and you simply have to change in BIOS from what disk you are booting.

Alternatively, you can just add grub2 to your current install.

To make sure what you have and where, run the boot info script from the link in my signature and post the results here as explained there. It will show more details. After that we will see what can be done.

---

### Post by Tinky Winky on 2012-03-07
Darkod,

Thanks for the link, please find the results of the script in the attached file.

Incidentally, before I ran the script, I used Easy BCD to deleted the boot option that I had created then re-installed Ubuntu as this should have amended the boot loader as part of the Ubuntu installation, but unfortunately this is not the case.

Kind regards

Tinky Winky

---

### Post by darkod on 2012-03-07
You should have mentioned you are trying to install wubi, not a proper dual boot. It works in different way.

I don't use wubi and have no idea why would it not create the entry in the windows bootloader. Don't use EasyBCD because I think it can't help with wubi. You have to be careful when reading instructions because most things working with ubuntu are not exactly the same with wubi.

One thing you could try is when starting the wubi install, don't do it with a simple double-click. Instead, try right-click and Run As Administrator. Sometimes with win7 you need to use that for maximum rights.

Now go into Programs in Control Panel, remove Ubuntu (wubi), and try installing once more with the above method.

---

### Post by Tinky Winky on 2012-03-07
Thanks for highlighting the difference of WUBI, I had noticed that recent versions of Ubuntu were significantly different from other distros and previously released versions of Ubuntu.  If there is a current version of Ubuntu but with the old GRUB loader, then this would solve all my problems as I know how to work with this.  However, WUBI is a mystery to me.

---

### Post by darkod on 2012-03-07
Wubi doesn't relate to the bootloader. Ubuntu since 9.10 comes with grub2 as bootloader. Earlier it was grub1.

Wubi means sort of a virtual ubuntu installed inside windows. It doesn't have its own linux partitions, it install onto ntfs.

In this case the install process should add an entry in the windows bootloader for wubi (ubuntu) but it seems it doesn't.

Maybe you can add only the entry manually, I have never tried that. But I'm not sure if something else is missing too.

So you can try removing ubuntu from Programs (wubi can be removed like any other program in windows), and installing once more with the Run As Administrator option mentioned above. In vista and 7 you need to execute wubi.exe with that option.

Alternatively you can install ubuntu as a proper dual boot which I always prefer. But for that option you need to plan your disks and where to make unpartitioned space for ubuntu because it doesn't install on ntfs partitions. You need to create unpartitioned space by shrinking some of the partitions.

---

### Post by Tinky Winky on 2012-03-07
I've had enough of the WUBI version, it simple does not work for me. 
 
I am in the process of downloading a non-WUBI version and hopefully this will work.
 
Regards
 
Tinky

---

### Post by Tinky Winky on 2012-03-08
Darkod,

Thanks for all your help, between downloading another version of Ubuntu and using your advice, I have managed to get Ubuntu 12.04 installed and working properly.

From the short time I have been using Ubuntu and in comparison to other distros, I am very impressed.

Thanks for your help.

Regards

Tinky

---

### Post by darkod on 2012-03-08
No problem. Glad you got it running and you like it.

Just note that 12.04 is still in development, so maybe minor issues might happen. The final release is due late April.

You can mark the thread Solved in Thread Tools above the first post.

---

