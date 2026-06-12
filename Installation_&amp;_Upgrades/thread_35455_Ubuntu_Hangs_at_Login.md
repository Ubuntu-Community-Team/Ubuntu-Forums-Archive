---
title: "Ubuntu Hangs at Login"
date: 2005-05-19
forum: Installation &amp; Upgrades
---

### Post by cheesedogbilly on 2005-05-19
I'm totally new to Ubuntu and have no experience with Linux.  I installed Ubuntu 5.04 on my system with WinXP.  

I have 2 NTFS partitions and then a /swap partion and a / partion.

My system is AMD 64 3200, ASUS A8V-E Deulxe mother board with onboard LAN adapter, 1 GB Ram, 250 GB hard drive, Sapphire ATi Radeon X600 256mb graphics card.

The installation goes fine although the network adapter cannot be autodetected however ASUS has given me drivers i can install in Ubuntu.

The problem is when i login to ubuntu after i enter my password the system totally freezes.  ](*,)  ](*,)   If i press the Session button the system will also freeze.  Any ideas?  I ran memtest86 and all the tests passed.  I'm totally stumped.

***EDIT***
I deleted and reinstalled Ubuntu twice.  The first time i removed the linux partitions in PartitionMagic which gave me an error about two partitions.  Something about crossing cylinders.  And i again used Ubuntu's default partitioning on the remaining unpartitioned part of my HD.  

The second time i removed the linux partitions with PartitionMagic i got the same errors and then GRUB gave me an Error 22 when i tried to reboot into Windows to search for some help.  So i reinstalled Ubuntu with Expert mode.  Skipped over the network config stuff in the hopes that i could configure the network once i had installed the asus drivers.  Now i get a warning after logging in about my computer not being able to connect to something (duh) but it hangs.

Could this be a problem with the partitioning?  Should i create a boot disk and repartition with cfdisk or something similar?

Any advice would be appreciated

---

### Post by w4e on 2005-05-19
Might not be relevant, but I encountered a system freeze after having installed kernel 2.6.11 on hoary. If you've installed that one, you might consider downgrading to 2.6.10, which works perfectly.

---

### Post by testingubuntu on 2005-05-19
[QUOTE=cheesedogbilly]

The second time i removed the linux partitions with PartitionMagic i got the same errors and then GRUB gave me an Error 22 when i tried to reboot into Windows to search for some help.  So i reinstalled Ubuntu with Expert mode.  Skipped over the network config stuff in the hopes that i could configure the network once i had installed the asus drivers.  Now i get a warning after logging in about my computer not being able to connect to something (duh) but it hangs.

Could this be a problem with the partitioning?  Should i create a boot disk and repartition with cfdisk or something similar?

Any advice would be appreciated[/QUOTE]
 The 2.6.11 .. kerel has caused issues with other distros as well  

the error 22 your experiencimng from Partition Magic is because it doesn't understand ext3 the file system.  Best to delete them witht the install and** A** create new partitions or **B** do the auto install deal

---

### Post by cheesedogbilly on 2005-05-19
Ok i reinstalled using the ubuntu installer to delete and then reinstalled all the partitions.  The kernel version is 2.6.10-5-AMD64-Generic.  Installation resulted in system hanging at the splash screen for ubuntu immediately after login.  It hangs at exactly 7 seconds after hitting enter after entering the password.  I've tried leaving the system running to see if it's just working, but after 2 hours the splash screen was still displayed and the system was still stuck.

Perhaps a different distro?

---

### Post by meki on 2005-05-19
wonderful!  \\:D/

---

### Post by alastair on 2005-05-19
Reboot, but don't log in to the graphical screen (GDM).

Switch to a console (CTRL+ALT+F1 say)
Login as your self

cd /etc/X11
sudo cp -p xorg.cong xorg.conf.bak

edit xorg.conf e.g. with vi

sudo vi xorg.conf

Find the line that has "Driver ..." (e.g. for "ati")
Change the driver to "vesa"

i.e.

In "vi" :  

"x" will delete a char
"i" to go to insert mode
type the change
ESC back to command mode
:wq  (i.e. colon,w,q) to quit

restart GDM by going :

CTRL+ALT+F7 - back to login screen GDM
CTRL+ALT+BACKSPACE - to restart GDM/X

Try and log in

---

### Post by cheesedogbilly on 2005-05-19
Alastair,

That fixed it.  Thanks.  Now i can enjoy my first linux desktop.   :)

---

### Post by jory1 on 2005-06-07
newbie here, need some basic help...using the ctrl+alt+f1 to bypass the (gdm) for login.. but instead of getting a command prompt.. receive a message about "mail" and can only interact with the mail reader program... 

how do I escape the mail program.. or bypass??    and access a command prompt to make program edits (ie login hanging... would like to try the edits recommended above.)

cheers and thanks!

---

### Post by Lambert on 2005-06-25
[QUOTE=alastair]

Switch to a console (CTRL+ALT+F1 say)
Login as your self

cd /etc/X11
sudo cp -p xorg.cong xorg.conf.bak

[/QUOTE]

I'm having the exact same problem as here. I tried the fix listed here but when I get to the last command I'm asked for a password.  I type in root password and I get a  line that says.

cp: cannot stat 'xorg.cong : No such file or directory.

Can somebody help me here.

---

### Post by wvslkr on 2005-06-25
@Lambert: check your command syntax. its conf not cong.  Hope thats is all it is. :)

---

### Post by kuno4ever on 2005-08-12
i can't do anything at the login.
the mouse and keybord doesn t work, so i can t do ctrl-alt-f1
how do i get in the bash, shell ?

---

### Post by angro on 2005-08-14
[QUOTE=kuno4ever]i can't do anything at the login.
the mouse and keybord doesn t work, so i can t do ctrl-alt-f1
how do i get in the bash, shell ?[/QUOTE]

Had same problem, next time was the first thing I did before doing anything else, and it worked
[B]
Alastair :[/B]
Got your possible solution (X11 => vesa) and indeed it helps. Doesn't freeze anymore.

You saved my nerves, my computer and my family life (they got malucko whenever i spoke "Linux" ).

---

