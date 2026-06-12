---
title: "[SOLVED] Installed 8.04 as dual boot but no grub displayed, booting straight to xp.."
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by Johny79 on 2008-11-22
Ok so I've been using Ubuntu on my laptop for quite a while but I'm still a bit of a Linux noob I'm afraid.

Basically I want to have Ubuntu 8.04 setup as dual boot with XP on my desktop system.

Running from the live cd works fine, the install goes through without any errors, but when it restarts it just boots straight into XP with no Grub menu displayed. Frustrating to say the least :(

Anyone got any ideas? Just FYI, the disk is SATA and patitioned as 50GB XP, 30GB Ubuntu, 2GB Swap, 67GB Data if that makes a difference.

Any help appreciated!

---

### Post by Johny79 on 2008-11-22
Ok so I've now tried reinstalling grub using the method shown here...

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

It all completed ok, and reported everything present and installed succesfully but still no grub when I reboot :(

---

### Post by Bucky Ball on 2008-11-22
Can't remember if it is F1 or esc, but press one of them repeatedly at boot and see if that takes you to the grub. Then you can change the configuration once in ubuntu. I have done a couple of installs where the grub has been set to 'hiddenmenu', therefore doesn't show at boot. You can go to

nano /boot/grub/menu.lst

and change this if this gets you in ...

---

### Post by Johny79 on 2008-11-22
I just checked and it's esc, no joy though I'm afraid :(

It would appear that although grub is apparently installed for some reason it's being completely ignored and bypassed.

I even tried installing 7.10 instead thinking I could then upgrade it to 8.04 afterwards but the same thing happened :confused:

---

### Post by Bucky Ball on 2008-11-22
> **Johny79 said:**
> 

I even tried installing 7.10 instead thinking I could then upgrade it to 8.04 afterwards but the same thing happened :confused:

Yea, definately wouldn't advise that. Odd ...

In Windoze, can you check out disk management. It should have your Ubuntu partitions (EXT3) in there, but just simply marked 'healthy' (as Windoze has no idea what they are apart from that). Just make sure they are there and match with what you are expecting.

ps: so when you say no luck, do you mean pressing escape doesn't take you to grub? What does it achieve?
pps: during the install, where are you installing the grub to, exactly?

---

### Post by Johny79 on 2008-11-22
Ok feeling like a bit of a twit here.

I have 2 hard disks, the second being purely data, it would appear that the purely data disk has been detected as hd0 whilst the disk containing both XP & Ubuntu has been detected as hd1.

As a result grub has been installed to the purely data disk instead, which is not the default boot drive and hence xp boots as normal from the other drive.

Thankfully my motherboard has an option to select a boot device without entering the bios so it was just a case of hitting F12, selecting the other disk and voila grub appears!

Interestingly I can now switch back and forth between the default being to boot grub on one disk or straight to xp on the other by pressing a single key when I power on the system!

Anyway, problem solved so I'm a happy man :)

Oh and thanks for the advice! :)

---

### Post by Bucky Ball on 2008-11-22
You're welcome. Could you mark your thread as 'solved' from the top right 'Thread Tools', please. Others may find your thread useful. Have fun.  :)

ps: yea, a beautiful thing about grub, you can take it anywhere and it normally behaves!

---

### Post by Johny79 on 2008-11-23
Done :)

Now I can finally start getting it setup for everyday use, one big step closer to ditching M$ completely! :)

---

