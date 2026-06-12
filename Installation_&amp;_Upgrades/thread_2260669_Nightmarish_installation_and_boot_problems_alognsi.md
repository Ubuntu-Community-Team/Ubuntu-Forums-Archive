---
title: "Nightmarish installation and boot problems alognside windows 7"
date: 2015-01-13
forum: Installation &amp; Upgrades
---

### Post by lion3 on 2015-01-13
I'm brand new to linux/ubuntu and after days of trying to install (14.04) we FINALLY managed to install ubuntu alongside Win 7. (I wouldn't need windows at all if ubuntu ran adobe cc.)

Forgive me if some of what I'm offering here isn't relevant, I figure the more info I fice, the better.

Ubuntu refused to recognize my win 7 installation or install alongside it. We finally installed it with the "something else" option, and it seemed to load and run just fine.

I could access the files on the win partition just fine.

However when it came time that I needed to boot to windows that wasn't a boot option.

I used the windows repair disk and in command prompt ran a bootrec.exe /fixmbr

Well awesome, windows boots now but NOW I don't have the ability to boot ubuntu. EEEEK!

I'm pretty expert with windows 7, but brand new to ubuntu, so PLEASE if you need me to run commands with linux, give as detailed as possible info for a rank newbie.

Thanks for your help!

---

### Post by kansasnoob on 2015-01-13
You should be able to use Boot Repair using the same live media you used to install Ubuntu:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If that fails to get both Ubuntu and Windows to boot please provide the URL for the Bootinfo summary so we can see what's going on.

---

### Post by yancek on 2015-01-13
Not sure why windows 7 wasn't recognized from Grub but a simpler method would have been to boot Ubuntu and open a terminal and run this command:

```
sudo update-grub
```

If you watch output of the command, you should see a windows entry.  If you don't then run this command:

```
sudo os-prober
```

Then repeat the sudo update-grub.  Windows is not capable of booting any Linux and in fact doesn't usually recognize Linux filesystems and cannot read or write to them.  You can get third party software to install on windows to boot Linux and third party software to read/write to Linux.  Never used it so I don't have any idea how well it works.

---

### Post by lion3 on 2015-01-14
@Kansasnoob - Awesome, it took a few tries to get it right (I think I was choosing the wrong options and/or pulling the usb out too soon) but I now have access to Ubuntu again! 

@Yancek And yay! This info made it possible for me to boot both Ubuntu and Windows.

Thanks to both of you!

---

