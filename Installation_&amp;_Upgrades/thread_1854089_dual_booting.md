---
title: "dual booting"
date: 2011-10-03
forum: Installation &amp; Upgrades
---

### Post by nichos on 2011-10-03
I was dual booting my Acer netbook XP & Ubuntu 11.04 for 5-7 months when it all went wrong.

Luckily on the last reboot I noticed a linux menu with 4-5 option, & one was "Acer eRecovery Management" which did the XP installation all on its own giving the option to save & install all files & programs. 

Then, I went & installed Ubuntu 11.04 from my USB stick but, now on boot-up it does not give the XP boot.ini Menu I had before but, the "GNU GRUB" menu with 11 choices for Ubuntu (default) or XP, which is very complicated.

The rub now is how do I change the default to XP?

Any easy way?

---

### Post by oldfred on 2011-10-03
If you have that many choices you may just want to house clean out some of the older kernels. Best to keep one older & of course the current one.

HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
The Grub 2 Guide (formerly Grub 2 Basics) manual way
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by nichos on 2011-10-04
SOLVED

by These:-
You can change the default menu 
entry to boot by either going to the 

/boot/grub/grub.cfg file and near the top of the file changing the entry: set 

default="0" to another number. Count the menuentry lines until you get to xp. 

Put that number in the set default. Grub counts in this case from zero, so if 

your xp is the 5tn entry, put a 4 there.

To keep grub with default boot set to XP, you may use the GRUB_DEFAULT option 
on /etc/default/grub (as already said by yancek) or change the 
/etc/grub.d/30_os-prober file order.

Then :-
_sudo gedit /etc/default/grub  _...This brings up grub in editor & change to what ever No. you require.

_sudo update-grub       _..........this in a new terminal updates Grub.

---

### Post by Mark Phelps on 2011-10-04
Just so you know, when you ran "sudo update-grub" you OVERWROTE any changes you manually made in grub.cfg file -- which is why it is, except for limited testing, a BAD idea to edit that file.  

If you notice when you open it, there is even text in the file telling you NOT to edit it.

---

