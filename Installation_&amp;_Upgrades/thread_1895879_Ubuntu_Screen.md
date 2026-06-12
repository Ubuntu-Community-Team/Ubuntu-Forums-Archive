---
title: "Ubuntu Screen"
date: 2011-12-15
forum: Installation &amp; Upgrades
---

### Post by sindorei9009 on 2011-12-15
I install ubuntu 11.10 on my computer, everything works fine until i upgrade and reboot. Once i reboot, my computer gets frozen on the purple ubuntu screen. I've tried re installing, i've tried a different type of boot but nothing works. Please help!

                                       Sincerely,
                                           Me

---

### Post by fantab on 2011-12-16
> **sindorei9009 said:**
> I install ubuntu 11.10 on my computer, everything works fine **until i upgrade and reboot**. Once i reboot, my computer gets frozen on the purple ubuntu screen. I've tried re installing, i've tried a different type of boot but nothing works. Please help!


[LIST]
[*]What do you mean by "upgrade and reboot"? Do you mean Ubuntu UPDATES?
[*]Can you see the GRUB MENU?
[*]What kind of a computer you are using?
[*]Are you dual booting with windows?
[*]How did you Partition your HDD? Post a screen-shot.
[/LIST]

---

### Post by MAFoElffen on 2011-12-16
> **sindorei9009 said:**
> I install ubuntu 11.10 on my computer, everything works fine until i upgrade and reboot. Once i reboot, my computer gets frozen on the purple ubuntu screen. I've tried re installing, i've tried a different type of boot but nothing works. Please help!

                                       Sincerely,
                                           Me
Welcome to Ubuntu!

By saying your "computer gets frozen at the purple ubuntu screen." I'm assuming that you mean the Ubuntu Splash (called plymouth splash) that has the alternating white / red dots... Right?

Do you know what video your computer has? Does it boot into the Desktop of the LiveCD? If, while locked up, If you press <Cntrl><Alt><F2>, does the screen change to a login of a text-based Virtual Terminal (vt-tty2)?

---

### Post by sindorei9009 on 2011-12-16
> **fantab said:**
> 
[LIST]
[*]What do you mean by "upgrade and reboot"? Do you mean Ubuntu UPDATES?
[*]Can you see the GRUB MENU?
[*]What kind of a computer you are using?
[*]Are you dual booting with windows?
[*]How did you Partition your HDD? Post a screen-shot.
[/LIST]


yes
no
compaq presario CQ62
no
all of it under ubuntu

---

### Post by MAFoElffen on 2011-12-16
> **sindorei9009 said:**
> yes
no
compaq presario CQ62
no
all of it under ubuntu
Intel *Graphics* Media Accelerator 4500M

What if you use "nomodeset i915.modeset=0" as boot options using these instructions:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][B][Temporarily Editing Grub Menu for Boot Options]("http://ubuntuforums.org/showpost.php?p=11491229&postcount=812")

[/B][SIZE=2]...if it works, make it permanent using the instructions in post 1 of that same sticky-- Then open a bug report at launchpad. That chipset should be supported by xserver-xorg-video-intel (intel gives it's opensource for that}... but you're one of quite a few that all of a sudden / in a short time span that have started having problems again with this same chipset series.[/SIZE]
[/SIZE][/COLOR][/SIZE][/COLOR]

---

### Post by sindorei9009 on 2011-12-16
> **MAFoElffen said:**
> Welcome to Ubuntu!

By saying your "computer gets frozen at the purple ubuntu screen." I'm assuming that you mean the Ubuntu Splash (called plymouth splash) that has the alternating white / red dots... Right?

Do you know what video your computer has? Does it boot into the Desktop of the LiveCD? If, while locked up, If you press <Cntrl><Alt><F2>, does the screen change to a login of a text-based Virtual Terminal (vt-tty2)?

yes i mean the ubuntu splash. i have a raedon hd 5000. it does not boot into the livecd. and idk if it canges

---

### Post by MAFoElffen on 2011-12-16
> **sindorei9009 said:**
> yes i mean the ubuntu splash. i have a raedon hd 5000. it does not boot into the livecd. and idk if it canges
Okay then... The modesets you want to try with that card are:
```

radeon.modeset=0
nomodeset
vga=791 

```
Try one at a time from the Grub Menu using these instructions:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Temporarily Editing Grub Menu for Boot Options]("http://ubuntuforums.org/showpost.php?p=11491229&postcount=812")**[/SIZE][/COLOR][/SIZE][/COLOR]

When you do find one of those that work... remember it. Then you could use the same boot option with a LiveCD using these instructions:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Modesetting and the LiveCD]("http://ubuntuforums.org/showpost.php?p=10740097&postcount=3")**[/SIZE][/COLOR][/SIZE][/COLOR]

---

