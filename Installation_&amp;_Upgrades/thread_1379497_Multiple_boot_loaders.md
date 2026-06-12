---
title: "Multiple boot loaders"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by sh00t on 2010-01-12
I dual boot winXP and ubuntu 9.10 and I have 2 boot loaders, which is annoying.
The first one lists windows xp first, then ubuntu,the second one (grub) list ubuntu 9.10, ubuntu recovery, and windows.
I want to get rid of the first one and edit grub and add windows safe mode, safe mode with networking...you get the drift.
Anyone have a similiar experience? How did you deal with it and could you point me in the right direction...

---

### Post by phillw on 2010-01-12
> **sh00t said:**
> I dual boot winXP and ubuntu 9.10 and I have 2 boot loaders, which is annoying.
The first one lists windows xp first, then ubuntu,the second one (grub) list ubuntu 9.10, ubuntu recovery, and windows.
I want to get rid of the first one and edit grub and add windows safe mode, safe mode with networking...you get the drift.
Anyone have a similiar experience? How did you deal with it and could you point me in the right direction...


Hi,

I'd head over here --> [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)  Section 13 and do a re-install of Grub. 

Doing it that way, that will set you as one boot loader & auto find your operating systems.

The only other thing to note, if you have more than one hard drive - is the boot order in BIOS - Post back if that is something you need to sort out.

Regards,

Phill.

---

### Post by raymondh on 2010-01-12
If Phil's link did not solve your issue, let's have a better look at your set-up.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Boot into your ubuntu liveCD and go live session (try ubuntu...).  In live session, download the above-linked boot-info-script and save it to desktop.  After downloading, access a terminal (you're still in live session) and type

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will output a RESULTS.TXT file to the live session desktop.  Come back to this thread and copy/paste that file in your next post.  

Oh, by the way, that file can be long so do us a favor.  Once you've pasted the file in your post, highlight it and wrap it in codes to make it manageable.  The codes button is the # in the toolbars.

Regards,

Raymond

---

### Post by presence1960 on 2010-01-12
Run the boot info script please so we can see exactly your setup and boot process. From your explanation it sounds like you have a wubi install. if in fact that is how you installed ubuntu (via wubi by booting windows and putting the Live Cd in the optical drive from within windows) there is no way to change that as ubuntu is installed inside of windows and must use the windows bootloader. Once you select Ubuntu then it passes onto GRUB which you can then choose your ubuntu kernel to boot.

---

