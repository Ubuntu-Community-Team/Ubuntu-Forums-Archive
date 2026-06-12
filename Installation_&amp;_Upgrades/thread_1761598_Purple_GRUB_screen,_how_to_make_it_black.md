---
title: "Purple GRUB screen, how to make it black?"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by harbimilan on 2011-05-18
Hi guys,
my problem is simple. I just upgraded from ubuntu desktop 10.10 to 11.04, and I accidentally upgraded the grub bootloader (whatever that means :D ) and the black parts of the screen has become purple.

I may have not used the right words, since I don't know exactly what grub is, so I will attach a picture of the original grub screen (which is black): [IMG]http://2.bp.blogspot.com/_iUiWXo7FLSQ/TNa3PwGlcGI/AAAAAAAAAGU/39C5YvEBoGg/s1600/Ubuntu-10.10_grub.jpeg[/IMG]

this screen has become **[COLOR=Purple]purple[/COLOR]**. How can I make it **black** again?

---

### Post by StrayEddy on 2011-05-18
Check this out, maybe can help ;)
 
[http://fosswire.com/post/2007/12/colour-your-grub-boot-menu/](http://fosswire.com/post/2007/12/colour-your-grub-boot-menu/)

---

### Post by harbimilan on 2011-05-22
> **StrayEddy said:**
> Check this out, maybe can help ;)
 
[http://fosswire.com/post/2007/12/colour-your-grub-boot-menu/](http://fosswire.com/post/2007/12/colour-your-grub-boot-menu/)


Thanks. I formatted ubuntu and installed the older GRUB. But thanks anyway :)

---

### Post by MAFoElffen on 2011-05-22
> **harbimilan said:**
> Thanks. I formatted ubuntu and installed the older GRUB. But thanks anyway :)
Welcome.

LOL... Ah // Okay...

I looked at the picture of your grub "Menu" and ??? The picture is of a Legacy Grub menu with Solaris? (Default theming for Solaris is usually blue with progress bars when it loads by the way...)  Ubuntu 11.04 uses Version 1.99 of Grub2... and uses features of that version that were not in legacy (or in version 1.98 for that matter).

And your problem is what?  I am a little "unclear" on what your problem is and what you want to resolve.  But I'm interesting in trying to help you with that.

 - Does Grub boot?  I am assuming it does from the color you are describing that your grub menu shows.
 - Does the linux Kernel boot?
 - Does a graphical X-Windows session boot?

If it is a grub question on theming and formatting, All we'd need to know is what version grub you are on to be able to point you to the correct defaults file.

Please refer to this sticky:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

**EDIT--** What is *curious* is that you said you upgraded from Ubuntu 10.10 to 11.04 > You said that was a picture of your current grub boot screen > which is all black / Grub legacy/ with no instances of Ubuntu.  You did upgrade Grub during the dist-upgrade which was correct = not accidental.

The purple hue is now "normal."  The new grub environments will try to query and set graphics before the kernel boots > pass on those modesets to the kernel > which in turn passes on those graphical settings to xorg.

There are ways to manually set, reset or disable those grub/kernel/xorg environment settings... If that is what you are asking about and what your goal is.

**Sidenote--** That picture (of Legacy that you posted) would be of a version of Grub that would not turn a purple hue (because is doesn't have those graphical environment variables) and would have problems booting current versions of Ubuntu, as it would have problems reading an ext4 partition (I also run Solaris10, Solaris 11, OpenSolaris Dev builds, other Unix Dev builds, etc...)

---

### Post by harbimilan on 2011-05-25
Wow, thanks [MAFoElffen]("http://ubuntuforums.org/member.php?u=1044547"),
I do not need the answer since I formatted the computer, But I'm marking this thread as solved, if it will help anybody else :)

---

