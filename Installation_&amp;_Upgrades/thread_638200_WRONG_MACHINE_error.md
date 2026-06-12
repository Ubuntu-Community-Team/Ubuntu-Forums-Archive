---
title: "WRONG MACHINE error"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by pbfreak212 on 2007-12-11
i used the wubi installer to install ubuntu on my toshiba laptop. i installed it using wubi on my desktop and it went perfectly. i thought this was going well too, but when it restarted my computer it went to boot up and i got a big full screen error message WRONG MACHINE. anyone know whats wrong or how to solve it?

---

### Post by stego_s_aurus on 2007-12-11
Thats the error that the Toshiba Recovery CD gives when it detects the wrong machine: Are you trying to use an existing hard drive? Try a clean hdd that has nothing on it instead.

---

### Post by pbfreak212 on 2007-12-12
is there anyway i can undo what i did, all it does is have that error and if i hit ok it restarts? I have alot of programs for my school on that hdd. i would really hate to lose it.

---

### Post by kaervos1024 on 2007-12-12
There was probably a recovery partition on the hard drive... many computer manufacturers leave a partition on the disk for recovery purposes. I suspect the contents of that partition may be the same as a Toshiba recovery CD, as Stego says. Sounds like it is trying to boot off that recovery partition.

Personally, if you have data on the disk you don't want to loose, I'd boot the machine with a Ubuntu Live CD, mount the partition with your data on it and then copy your critical data off it onto a USB flash drive or something of the sort.

After that, to fix the machine I would either edit or reinstall GRUB... do you get a GRUB menu when your machine boots before the WRONG MACHINE error appears?

---

### Post by kaervos1024 on 2007-12-12
Oh, I'm sorry I didn't see what Wubi was. So you definitely don't have GRUB installed, Wubi apparently tries to use the Windows boot loader NTLDR to launch the new Ubuntu install.

I've never had much luck using NTLDR to boot into Linux. I suspect the Wubi installer got confused and somehow configured NTLDR to boot off the recovery partition. Do you get the windows boot menu at all?

Either way, I'd first try to get any critical data you have onto  a USB drive / CD / DVD using an Ubuntu Live CD, so you won't have that to worry about.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Just get 7.10 desktop, and thats what I mean by a "Live" CD.

I can't offer any suggestions about getting Wubi installed right... I hadn't heard it of it before now. I'd try using the Live CD to install after you save your data off. Its really quite straight-forward.

---

### Post by pbfreak212 on 2007-12-16
ok, thanks for your help,
I booted into the live cd, and went into gparted.
The toshiba recovery partition was active, so i switched it back over to my c drive.
when i booted up again, i got windows boot manager and it had both xp and ubuntu, so i tried ubuntu and it got some errors, didnt really feel like dealing with that so i just booted into xp and uninstalled wubi.
Now it works like i did before. thanks

---

### Post by kaervos1024 on 2007-12-17
Glad you got your machine back up and running PBFreak, but I'm sorry your first excursion into Linux was a bad experience.

I hope you give Ubuntu a second try at some point, perhaps this time using the Ubuntu Desktop CD instead of Wubi. The freedom that comes with Linux really is exhilarating.

If you are all set, you should mark this thread solved.

Enjoy the season!

---

