---
title: "Grub Problem After Ubuntu 10.10 Upgrade?"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by stuck_tom on 2010-10-24
Hi all. I recently performed a network upgrade from 10.04 to 10.10. During the installation, it asked me if I wanted to replace my menu.lst file and I said no. When I boot the computer now, I get the option to boot into Windows 7 (which works) or Ubuntu 10.04 (the previous installation I had). If i try to use 10.04 the displays simple turns off after a few seconds.

I've tried installing grub2 using instructions on a different forum but nothing changed (do I need to get rid of original grub or something?...I'm clueless sorry). One last piece of information, if I act like I'm going to install 10.10 using the live cd, I can see the windows partition and an ubuntu 10.10 partition in the installer.

Thank you for any thoughts you might have

---

### Post by mörgæs on 2010-10-25
Hi, welcome to the forum.

You could try this:
[https://wiki.ubuntu.com/Grub2#Restore%20GRUB2%20-%20Recovering%20from%20a%20Windows%20XP%20/%20Vista%20/%207%20Reinstallation](https://wiki.ubuntu.com/Grub2#Restore%20GRUB2%20-%20Recovering%20from%20a%20Windows%20XP%20/%20Vista%20/%207%20Reinstallation)

using a 10.10 CD and not 10.04, as it reads in the guide.

---

### Post by kansasnoob on 2010-10-25
> **stuck_tom said:**
> Hi all. I recently performed a network upgrade from 10.04 to 10.10. During the installation, it asked me if I wanted to replace my menu.lst file and I said no. When I boot the computer now, I get the option to boot into Windows 7 (which works) or Ubuntu 10.04 (the previous installation I had). If i try to use 10.04 the displays simple turns off after a few seconds.

I've tried installing grub2 using instructions on a different forum but nothing changed (do I need to get rid of original grub or something?...I'm clueless sorry). One last piece of information, if I act like I'm going to install 10.10 using the live cd, I can see the windows partition and an ubuntu 10.10 partition in the installer.

Thank you for any thoughts you might have

Since you mention a menu.lst you may not even have grub 2. The best way to troubleshoot this is for you to post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternate instructions:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Edit: obviously you'll have to use a Live CD to do so. It can be any older Ubuntu Live CD. I would like to know what Live CD you use.

---

### Post by Drewbladez on 2010-10-25
I have a similar problem and am new to all this. I've been self educating myself so I thank you in advance. 

I Dual booted my Netbook ASPIRE ONE with Ubuntu 10.10.
everyhings been running smoothly for 2-3 weeks now until saturday night. there were some updates available for applications so I did the upgrades. 

Well now when I boot up I get this GRUB Ubuntu cmd like screen. How Do I boot to Ubuntu? and if I need to reinstall, how do I go about this. I made a THUMB Drive with the installation setup but my netbook wouldn't boot that way so I ended up installing from windows and partitioning 18G there (thats what it recommended). 

Soo What do i do? Thank for any direction you can give.

---

### Post by houseworkshy on 2010-10-25
I suspect your GUI hasn't started, I had the same problem with 10.04. If that is what is going on then "sudo start gdm" should get you to your desktop ( also called GUI for "graphic user interphase" ) a few passwords down the line. 

As a learner the most useful command I know is "man" ; typing it in front of any command brings up its manual page, "q" quits the manual and returns you to the command line.  To use command lines when your GUI is running use the terminal ( which is under accessories ).  Opening a terminlal can be compaired to "opening a dos window" in the older versions of windows.  Try it out on "apropos" "info" and "help" to discover some of the excellent built in help.

In theory you could use your pc without ever touching the command line, in practice ( especially when using recent .0 distributions of Ubuntu ) you have to know a little as you will be spending time in there after new installs and the occasional update.  After you have got to your desktop I'd recommend "sudo ufw default deny" and "ufw enable".  In other words setup and turn on your firewall ( because though it is part of your distro it is not turned on by default )

Good luck with it and remember that 10.04 will be the long term support version for a while so if 10.10 is too much to fix you can go back to the lts.  10.04.0 was very buggy on releace so get a recent 10.04.1 iso if you choose to go the lts route.

Good luck with it all.

---

### Post by oldfred on 2010-10-26
Drewbladez it sounds like you have wubi which is not related to this thread. Please start a new thread. And if wubi mention that as only a few here know much about it.

If you upgraded and did not let it upgrade grub's menu whether grub legacy or grub2, you only have the old kernel and it will not boot. There were instructions in one of the release notes (maybe last version??) that said you have to manually edit the grub menu to get it to boot. The assumption is that you did not upgrade since you have customized it so much you did not want it modified. But now you have to modified it to boot. 

From the boot script we will find exact info on grub and what kernel verisons you have. You then can use that info to use e on the grub menu if new grub or use liveCD to edit old grub to get you into system, then you can update it. sudo update-grub.

---

