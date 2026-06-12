---
title: "Grub install fails, Help Please, Linux newbie here."
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by KnightEdge on 2007-03-23
Hi, I´m new at using linux, I have tried to install ubuntu edgy like 5 times, I have windows XP installed and I want to dual boot, I have tried to install it on different partitions, but the problem is with GRUB, it always fails to install giving me a fatal error message. I have tried to install it on a secondary primary partition (hd0,1) and also I have tried to install it a floppy (fd0) and always happens the same. I have burned 2 ubuntu CD´s  on 2 CD-RW media, to see if the first copy got the GRUB installer corrupted, but it happens the same with both. Can anyone help me please?

---

### Post by wonk-o-matic on 2007-03-23
Did you run the CD validation test?

What is the exact fatal error message?

---

### Post by ffxr on 2007-03-23
u can try the alternate install cd, it allows you to install grub in other locations rather than the MBR...

[http://mirror.letsopen.com/os/ubuntu-ISO/edgy/](http://mirror.letsopen.com/os/ubuntu-ISO/edgy/)

---

### Post by KnightEdge on 2007-03-23
I havent run that test, what does that test do?. Also It doesnt specify on the error, it just says that this is a fatal error.

---

### Post by ffxr on 2007-03-23
the validation test, checks the CD for errors i believe, uve tried 2 different cd's so id say its unlikely there corrupted in the same place..

try the alternate cd..

---

### Post by ajgreeny on 2007-03-23
You can also try the following to install grub where you want it.  Don't worry that it may seem rather difficult; it really isn't that hard to do, and may just solve your problem.

Boot into the ubuntu live CD
open a terminal and run :
command:-
    "sudo grub"

then:
command:-
    "find /boot/grub/stage1"

replace the question marks in the following command with the output of the last command :
command:-
    "root (hd?,?)"
If you have more than one linux install, use the one that you want the grub to run from. [like : root (hdo,1) ,probably]
then:
command:-
    "setup (hd0)"  This will put grub on the MBR of windows so if you want it somewhere else specify that here.  In my opinion it is much easier to use the windows MBR for grub, and not bother about putting it somewhere else.  If you reallyb want to you cvan move it later on to which ever partition you like, but frankly that just complicates things unnecessarily.

and
command:-
    "quit"

Reboot.

Good luck, I hope it works.

---

### Post by KnightEdge on 2007-03-23
I did the validation test and the result was 0 checksums failed, so theres no problem with the disc. I will have to try the other suggestion. Another question is, how can I bypass the grub install when installing ubuntu?

Bypassing it will allow me to install it manually.

---

### Post by ajgreeny on 2007-03-23
I don't think you can bypass the grub install with the live install CD, you need the alternate install CD to do that.

---

### Post by KnightEdge on 2007-03-23
ajgreeny, I did what you told me, but now my system boots directly to grub. And I dont know what to do. I cant enter my windows install.

---

### Post by ssican on 2007-03-23
Do you have one or two HDs ?  Perhaps this link help: [http://www.ubuntuforums.org/showthread.php?t=389714](http://www.ubuntuforums.org/showthread.php?t=389714)

EDIT: In this link, on Post 9, the end solution was ReInstall Edgy.

---

### Post by ffxr on 2007-03-23
KnightEdge, what is it stopping you selecting winodws in the grub menu? can you be anymore specific as to what your seeing?

---

### Post by KnightEdge on 2007-03-23
I have 2 HD's with multiple NTFS partitions. On the first HD there is a Primary NTFS partition and a second Primary ext3 partition. In the same HD there is a extended partition with 1 linux swap partition, 1 FAT32 partition and 4 NTFS partitions. On second HD just have 4 NTFS partitions.

---

### Post by KnightEdge on 2007-03-23
> **ffxr said:**
> KnightEdge, what is it stopping you selecting winodws in the grub menu? can you be anymore specific as to what your seeing?

Grub loads as a command line interface, just like "Sudo Grub" in the terminal.

---

### Post by KnightEdge on 2007-03-23
My 2 HD's are SATA. I dont have any IDE HD's.

---

### Post by ssican on 2007-03-23
(On Grub Menu) Did you try to use the arrows  to select Linux or Windows?  After select it is necessary press ENTER.

---

