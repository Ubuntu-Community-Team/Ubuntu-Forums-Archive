---
title: "Macbook Triple Boot Issues"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by cdorrington on 2006-12-07
Hey guys,

I am having some issues setting up a triple boot system on my macbook. I haven't come any answers using the search so hopefully someone can help me out:

- I have refit installed

- After splitting my partitions using diskutil windows was installed without any problems to sda4 (c: drive)

- Next I went through the normal Ubuntu install disk. I had to erase my linux partition and remake it in order to format and proceed with installation. There is no swap partition.

- Was able to sync the tables during install so Grub would install normally.

- Upon rebooting everything looks great. I have choices for Mac, Windows and Linux in the refit menu.

- But, selecting either Windows or Linux loads grub. Is there any way to remove the Grub menu from the windows boot choice?


At this point both Windows and Ubuntu work fine. But, after I boot into Mac osX it screws up my grub installation. I am unable to boot into Windows or Ubuntu after using osX. Just the grub terminal appears. This never happened with my old osX/Ubuntu dual boot configuration using grub,



Is there any way to fix these problems? I see older posts using lilo to boot, but since then grub has been fixed and I see no reason why I shouldn't be able use grub in this configuration.

Thanks for the help.

---

### Post by willnight on 2006-12-09
don't use grub. i tried to but failed miserably. did lilo and works.

try the instructions from here first to try to fix the grub issue:

[http://www.sharealike.org/index.php?m=200605](http://www.sharealike.org/index.php?m=200605)

ignore the kernel bit... go down to where it begins "The installer will fail when it comes time to install LILO...." and pick it up from there.

if that doesn't work for you, do a fresh install and follow the instructions from this how-to:

[http://ubuntuforums.org/showthread.php?t=198453&highlight=macbook+lilo](http://ubuntuforums.org/showthread.php?t=198453&highlight=macbook+lilo)

what i've learn:

- read through once or twice and visualize it in your head first before going in for actual installation.

- have an ethernet connection to the wall, not wireless. you'll need to do a couple installs on-line.

- some instructions leave out some obvious assumptions: after installation, whatever instruction you execute, you want to do it to the partition that you had just installed ubuntu. that means you have to create a directory and mount that partition (sda3) then execute the instructions to affect the new install, not the temporary ubuntu environment which you are currently on. i'm hope i'm making sense here...

- don't forget to create and activate swap --- again, on sda3 while it's mounted.

- sync mbr before booting into other oses. both windows and ubuntu need to be rebooted at least a couple of times after installation to "catch". i have no idea why, but they need to. the screen will go blank. give it a few seconds then reboot. keep rebooting until mbr "figure things out". it will work.

you can tell i'm no linux geek. i just learn through trial-and-error and lots of frustration! hit me up if you run into a snag. maybe i can help walk you through it. good luck!

(it's the greatest f**king feeling once it works for ya!

---

### Post by willnight on 2006-12-09
assumption: you're using dapper drake, *not* edgy eft.

don't use grub. i tried to but failed miserably. did lilo and works.

try the instructions from here first to try to fix the grub issue:

[http://www.sharealike.org/index.php?m=200605](http://www.sharealike.org/index.php?m=200605)

ignore the kernel bit... go down to where it begins "The installer will fail when it comes time to install LILO...." and pick it up from there.

if that doesn't work for you, do a fresh install and follow the instructions from this how-to:

[http://ubuntuforums.org/showthread.php?t=198453&highlight=macbook+lilo](http://ubuntuforums.org/showthread.php?t=198453&highlight=macbook+lilo)

what i've learn:

- read through once or twice and visualize it in your head first before going in for actual installation.

- have an ethernet connection to the wall, not wireless. you'll need to do a couple installs on-line.

- some instructions leave out some obvious assumptions: after installation, whatever instruction you execute, you want to do it to the partition that you had just installed ubuntu. that means you have to create a directory and mount that partition (sda3) then execute the instructions to affect the new install, not the temporary ubuntu environment which you are currently on. i'm hope i'm making sense here...

- don't forget to create and activate swap --- again, on sda3 while it's mounted.

- sync mbr before booting into other oses. both windows and ubuntu need to be rebooted at least a couple of times after installation to "catch". i have no idea why, but they need to. the screen will go blank. give it a few seconds then reboot. keep rebooting until mbr "figure things out". it will work.

you can tell i'm no linux geek. i just learn through trial-and-error and lots of frustration! hit me up if you run into a snag. maybe i can help walk you through it. good luck!

(it's the greatest f**king feeling once it works for ya!

---

