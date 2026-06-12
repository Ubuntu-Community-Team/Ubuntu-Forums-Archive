---
title: "Is &quot;Breezy&quot; a hurricane?"
date: 2005-09-13
forum: Installation &amp; Upgrades
---

### Post by banasw01 on 2005-09-13
I downloaded and burned the CD of Ubuntu 5.10 Preview.  I put the CD in while running xorg and it asked me if I want to upgrade.  I said sure.

The upgrade went well except for getting some perl and GTK warnings about locale or something.

I rebooted, 2-3 services failed to start and Xorg did not want to start.  One of the services was something about fonts.

Anyway, Xorg says that the kernel part of my nvidia driver was compiled for a different kernel.  I try to run the NVIDIA-blah-blah.sh but it says that I don't have source for my kernel.  I try apt-get install kernel-source, still no luck.

I try to reconfigure Xorg to use a generic driver, but xf86setup or xf86config do not work!!!....  At this point I just want to get Xorg up any way I can.

Instead I finally found that I am supposed to use "dpkg-reconfigure xserver-xorg" to get a ncurses configuration program for xorg!?!?  Now, WHO WAS THE GENIUS WHO CAME UP WITH THAT COMMAND???!!!  This is supposed to be a user-friendly command? Can't we use some simple one word command like... xsetup or something?  How about linking "xf86setup" or "xf86config" to "dpkg-reconfigure xserver-xorg"??? How about asking the user if they want to configure the Xserver when the user types in startx or Xorg?

While making things user friendly can't we also change what happens when we type "help" and press enter?  Getting the bash help screen is not very user-friendly either.... did not help me that's for sure.

Man... what a nightmare.  I think I will just do a clean reinstall.  When inserting the 5.10 CD into the computer there should be a message saying "Please do not upgrade 5.4 to 5.10 using this CD or stuff will break, thank you."

---

### Post by debenham on 2005-09-13
If you make sure that 'linux-restricted-modules-686' (or whatever your machine is) the nvidia kernel module will be included.  This way you wouldn't have needed to try all the fiddling around with X and dpkg-reconfigure.

As for changing what happens when you type 'help' at the bash prompt, The hope is that normal users will never need to see a bash prompt and so help is only there for advanced users.

Could you check that linux-restricted-modules-* is installed for your kernel by running
"dpkg -L linux-restricted-modules-`uname -r`"
And then what happens when you run "modprobe nvidia" ?

---

### Post by banasw01 on 2005-09-13
I installed 5.10 on a fresh partition. I choose RaiserFS and Grub would not boot it.  I reinstalled with ext3 and installation worked fine.

I like the new add/remove programs in 5.10, but I miss not being able to use the ubuntusetup.sh by ubunt-geek:
[http://www.ubuntuforums.org/showthread.php?t=22646&highlight=ubuntusetup.sh](http://www.ubuntuforums.org/showthread.php?t=22646&highlight=ubuntusetup.sh)

I think I will just wait for the final version of 5.10

---

### Post by angkor on 2005-09-13
[QUOTE=banasw01]I downloaded and burned the CD of Ubuntu 5.10 Preview.  I put the CD in while running xorg and it asked me if I want to upgrade.  I said sure.

The upgrade went well except for getting some perl and GTK warnings about locale or something.

I rebooted, 2-3 services failed to start and Xorg did not want to start.  One of the services was something about fonts.

Anyway, Xorg says that the kernel part of my nvidia driver was compiled for a different kernel.  I try to run the NVIDIA-blah-blah.sh but it says that I don't have source for my kernel.  I try apt-get install kernel-source, still no luck.

I try to reconfigure Xorg to use a generic driver, but xf86setup or xf86config do not work!!!....  At this point I just want to get Xorg up any way I can.

Instead I finally found that I am supposed to use "dpkg-reconfigure xserver-xorg" to get a ncurses configuration program for xorg!?!?  Now, WHO WAS THE GENIUS WHO CAME UP WITH THAT COMMAND???!!!  This is supposed to be a user-friendly command? Can't we use some simple one word command like... xsetup or something?  How about linking "xf86setup" or "xf86config" to "dpkg-reconfigure xserver-xorg"??? How about asking the user if they want to configure the Xserver when the user types in startx or Xorg?

While making things user friendly can't we also change what happens when we type "help" and press enter?  Getting the bash help screen is not very user-friendly either.... did not help me that's for sure.

Man... what a nightmare.  I think I will just do a clean reinstall.  When inserting the 5.10 CD into the computer there should be a message saying "Please do not upgrade 5.4 to 5.10 using this CD or stuff will break, thank you."[/QUOTE]

I agree with you on the 'dpkg -reconfigure xserver-xorg' part. It would be nice for some if they'd have an graphical Xsetup tool. 

But it isn't really a strange command. Dpkg is used to manage packages, the -reconfigure parameter speaks for itself and x-server-xorg is the package.

About stuff breaking in Breezy...you should have expected that. It *is* called a preview. If you prefer a stable Breezy, you just need to be patient for another month or so.

---

### Post by banasw01 on 2005-09-13
It took me a while to find this command.  A Linux newbie without working Xorg is pretty helpless.

I am just writing comments from a real newbie perspective.  I know that for people who spent years with Debian Ubuntu is a piece of cake.  A few simple modifications can save users from frustration and prevent people from using forums to ask questions like "How do I reconfigure my Xorg?"

---

