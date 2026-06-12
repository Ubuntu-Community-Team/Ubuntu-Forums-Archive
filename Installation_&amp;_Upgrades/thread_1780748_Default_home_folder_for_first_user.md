---
title: "Default home folder for first user"
date: 2011-06-12
forum: Installation &amp; Upgrades
---

### Post by leo128 on 2011-06-12
hi all!

when installing ubuntu, the installer asks for username/login/password of the first user which will be allowed to sudo and administer the system... let's call that user "ubuntu"

what if I want to:

1) Automate those answers (which preseed variables should I set if any?)

2) Change the default home directory only for that user... let say I want it to be /ubuntu instead of /home/ubuntu (because I want /home/ to be empty after setup).

I know I could tweak /etc/passwd after setup (before first reboot) but I would like to know if there is a "clean way" to do that.

Thank you!

---

### Post by Herman on 2011-06-12
You should research how to use the Ubuntu 'Alternate Installation' CD, I think you can use that for at least some if not all of the purposes you mentioned.

**The advantages of using the 'Alternate' install CD** (compared with the better known 'Desktop' Live/Install CD) are that more choices are available for people who want to do something special with their install.

With the 'Alternate' Install CD you can,

[LIST]
[*]install Ubuntu in a LUKS fully encrypted file system,
[*]set up Ubuntu with LVM or software RAID,
[*]perform an 'expert' install (for coping with machines with difficult hardware),
[*]install ubuntu as a server, (without any 'GUI' (desktop),
[*]the 'Alternate' CD's partitioner will work in a computer with 128 mb of memory and maybe less.
[*]choose between GRUB and LILO boot loaders, or even install with no boot loader at all,
[*]create pre-configured OEM systems,
[*]set up automated deployments,
[*]upgrade an older installation without network access.
[/LIST]
I think the second and third last items in the above list would be something along the lines of what you want to do.

I have some web pages (see my sig link) illustrating basic uses of the 'Alternate Installation' CD, but for your more advanced needs you will probably need to look for further information in '**[Official Ubuntu documentation]("http://help.ubuntu.com/")**', and ** [Ubuntu Community documentation]("https://help.ubuntu.com/community/") **.

---

