---
title: "can't accees tty while instaling"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by JackRnl on 2007-06-01
I downloaded Ubuntu and checksum proved to be OK.
I started Ubuntu on one PC and it starts up well.

Now i want to install it on another PC and after I select 'start and install ubuntu' t continues but stops soon providing the message

"/bin/sh: can't access tty;  job control turned off" followed by "initnames"

I performed a verify while writing the cd

What is the problem and how can I solve it?

BTW : how can i INSTALL Ubuntu as it STARTED when I ran it on that other system?

---

### Post by pcardout on 2007-06-01
Ubuntu Started on your other system.  Great!  So now that it has started look at the menus at the top and you will see that one of them has the option "Install".  Just do it!  Good luck!  (This is my first night of Ubuntu -- but I've been Debianing for years).

---

### Post by JackRnl on 2007-06-01
> **pcardout said:**
> Ubuntu Started on your other system.  Great!  So now that it has started look at the menus at the top and you will see that one of them has the option "Install".  Just do it!  Good luck!  (This is my first night of Ubuntu -- but I've been Debianing for years).

Thanks for where to find the INSTALL option in the menu, but i don't want to install it on the system it works:( but on the system it DOESN'T work

---

### Post by JackRnl on 2007-06-01
After reading some other posts here I tried one "solution" by inserting a diskette but that didn't work.
But I also tried removing the /quiet from the commandline and adding "pci=noacpi" and "noacpi" and "nolapci"
After those changes installation starts but unfortunally i still have a problem.

It shows lines like
[ 37.316000] hda: dma timeout error : status 0x58 [driveready seekcomplete Datarequest]
[ 37.316000] ide : failed opcode was : unknown
[ 67.332000] hda5<4> hda: dma_timer_expiry : dma_status == 0x21
and similar lines was nrs [67.328000] [ 97.340000], [127.356000] [ 127.360000] and [127.420000]
after that hitting the arrow key(up) leads to showing
(initramfs):

but I don't know what to do.

Seems to me dma could be a problem (what can i do about it?)

also. The harddisk has been formatted NTFS (windows 2000) and SOME of the partitions are being compressed.

Any ideas what to do?

---

### Post by confused57 on 2007-06-01
Maybe something in this thread that will help:
[http://ubuntuforums.org/showthread.php?t=421588](http://ubuntuforums.org/showthread.php?t=421588)

---

### Post by JackRnl on 2007-06-01
I the suggestions provided and read that other thread allthough I did not understand all (as I've not been using unix for about 15 years an just forgot a lot of things in the mean time).

But after entering break=top at the beginning of the options (I also tried putting it AFTER the filename) and with/without the quiet and also with and without pci=noacpi and noapic
not much difference
 But i did notice that
"break=top pci=noacpi" will execute until
[47.697154] Input : AT translated set 2 keyboard as class/input/input1
Spawning shell within the initramfs
Busybox v1.1.3 .......(etc)
and THEN 
the familiar message appeared followed by the (initramfs) prompt
To me it sounds some bells THIS happens .
Could there be a problem bringing 'keyboarddata to tty' or to say it different : could it be initialising the keyboard is the problem ALLTHOUGH characters you enter from the keyboard still appear on the screen.

But in general : it still seems to me unix (Ubunu) is NOT that far evolved from the early 90s as it STILL seems to require guru-knowledge about options and commands, something I HOPED would have disappeared by now.
To me it seems installation should be more or less straightforward without having to enter special parameters. If system findsout 'it doesnt work' it should add thos eparameters ITSELF I believe and try again.
Allthough I installed numerous windows PCs (and also Atari and Apple-II in the far past) THIS type of problem i didn't encouter : the system itself usually WILL install itself into a state the user CAN add 'misisng' or 'better' drivers if needed or desired.
In other words I believe instalation should be straightforward ESPECALLY for newbies and as the problem has been encoutered for quite some time ccording o the posts) wonder why it has not been solved yet.

Anyway , i will be glad with ANY suggestion to make things work.
I (still) want to replace my win2000 with Ubuntu.

Final remark : I AM able to start Knoppix on that same PC (allthough I didn't try to install it)

---

