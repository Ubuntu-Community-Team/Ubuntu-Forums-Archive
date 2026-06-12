---
title: "need HELP on a HOW TO..."
date: 2005-09-28
forum: Installation &amp; Upgrades
---

### Post by narmenia on 2005-09-28
I kinda like to have a dual boot Windows and Ubuntu... i want my PC to automatically boot my Ubuntu like its the only one installed... BUT! have an option to "press any key" before Ubuntu starts up to load Grub and have an option to Boot to windows... IS that even possible???

example:
>  Booting UBUNTU in 5 seconds... press any key to load GRUB...
*i press a key*
*menu pops-up*
> Select OS to boot:
Ubuntu
Windows XP

kinda like that...

THANX A MILLION!!!

*EDIT: OMG!!! sory i missed the top thread for not posting questions here...
kindly delete this... thnx... new thread @ [http://ubuntuforums.org/showthread.php?p=375088#post375088](http://ubuntuforums.org/showthread.php?p=375088#post375088)

---

### Post by narmenia on 2005-09-28
I kinda like to have a dual boot Windows and Ubuntu... i want my PC to automatically boot my Ubuntu like its the only one installed... BUT! have an option to "press any key" before Ubuntu starts up to load Grub and have an option to Boot to windows... IS that even possible???

example:
>  Booting UBUNTU in 5 seconds... press any key to load GRUB...
*i press a key*
*menu pops-up*
> Select OS to boot:
Ubuntu
Windows XP

kinda like that...

THANX A MILLION!!!

---

### Post by tombeharrell on 2005-09-28
It can work like this if you turn on hiddenmenu, which hides the grub menu. You press Escape to show the menu and choose a different kernel or OS. 

It's only set up like this by default if you're not dual booting.. so what you need to do is edit your menu.lst file by typing

```
sudo gedit /boot/grub/menu.lst
```

And make sure you have the following, without a # in front of hiddenmenu

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```

---

### Post by narmenia on 2005-09-28
WEEEEEEEEEEEE!!! THANX A MILLION!!!

***one more question... how do i configure Ubuntu not to display the Windows partition??? so no one won't know that i even have Windows on my PC...:cool:

---

### Post by Biased turkey on 2005-09-28
If your windows partition is not listed in the /etc/fstab, it shouldn't be visible

---

### Post by mlomker on 2005-09-28
Edit the /boot/grub/menu.lst file and change the default and the timeout values.  It is documented in the file.

---

### Post by FLeiXiuS on 2005-09-28
[QUOTE=narmenia]WEEEEEEEEEEEE!!! THANX A MILLION!!!

***one more question... how do i configure Ubuntu not to display the Windows partition??? so no one won't know that i even have Windows on my PC...:cool:[/QUOTE]

May I ask why you would want to do this?

---

### Post by FLeiXiuS on 2005-09-28
[QUOTE=Biased turkey]If your windows partition is not listed in the /etc/fstab, it shouldn't be visible[/QUOTE]

That's not true.  It'll be visible regardless.  You can't "hide" partitions.

---

