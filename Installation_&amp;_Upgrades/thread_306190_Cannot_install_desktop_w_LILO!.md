---
title: "Cannot install desktop w/ LILO!?"
date: 2006-11-24
forum: Installation &amp; Upgrades
---

### Post by zambizzi on 2006-11-24
I've got a PC I'm working on that Grub simply *does not* work on - it never has whether it be SuSE, Gentoo, and now Ubuntu.

Doing the straight 6.10 graphical install, I can't see that I have the option to choose LILO over Grub.  So, I downloaded the "alternative" cd and did both a text-mode and OEM install and chose LILO...but both times ended up with a command-line system w/ no X and Gnome installed.

I *simply* need a desktop install WITH Lilo as the boot manager...how can this be done?

Keep in mind I *did* try the alternative and *was* able to boot the system...but X was not installed...and if it involves then manually installing X and doing a bunch of work there...I don't think I can bother.

Is there any way to achieve this?

Thanks in advance!

EDIT: boop!  Sorry to bump but I haven't gotten a single reply in more than 24 hrs.  Thanks!

---

### Post by theelf530 on 2006-11-27
hey i'm havin a similar problem to yours: 

1. Comp stalled when loading ubuntu with the GRUB bootloader
2. Tried LILO...but all it gives is a text command line

if this is what happened to you, go here: 
[http://ftp.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/apcs03.html#id2519878](http://ftp.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/apcs03.html#id2519878)

[http://ftp.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/](http://ftp.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/)

the installation guide is for the warty version. But I assume many of the initial setup commands and parameters are similar from version to version. I'm using the Dapper Drake. 

after logging in...i followed the instructions and typed in: 

sudo aptitude -y install '~tubuntu-desktop'
(it'll ask you for the root password...so you'll need this, most likely the password that you used during the original setup) 

it then proceeded to begin installing something (i'm assuming its the desktop files). It's not completed yet, but i'll let you know when its complete and what happened. Hopefully it works. And hopefully this helps!

---

