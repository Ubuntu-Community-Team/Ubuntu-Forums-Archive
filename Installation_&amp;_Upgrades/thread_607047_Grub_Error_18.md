---
title: "Grub Error 18"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by negzero7 on 2007-11-08
I installed Gutsy Gibbon successfully but when I rebooted it came up with 
GRUB Loading Stage 1.5.

GRUB loading, please wait...
Error 18

I searched the forums and found nothing and then I googled it.  Seems to be a problem that my BIOS is too old and my hard drive too new and big.  I have an HP Pavilion with 256 ram and a Maxtor 300gb hard drive.  When I installed I told it to use the entire disk for partition. 

From what I've read the boot kernel is too deep in the hard drive and the BIOS can't find it.  If someone could please give me a step by step explanation on what to do, I would be so thankful!  Also, This is the only OS on this computer so there is no DOS or windows to do anything from, so if I need to change anything, please tell me how.  All I have is a Ubuntu Gutsy Gibbon boot cd and the error above.

---

### Post by Pumalite on 2007-11-08
256 MB of RAM or less> Xubuntu Alternate CD:[http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)

---

### Post by bulldog on 2007-11-08
Take a look here.
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Specially this part

[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

---

### Post by Pumalite on 2007-11-08
256 MB of RAM is still too little for Ubuntu 7.10

---

### Post by negzero7 on 2007-11-08
Thanks for the replies but I am still confused. The links posted explained a lot about what the problem could be but they didn't really provide any instruction on exactly what to do, other than set up a partition for the kernel to boot from.  So....how do I do that?  I have no idea really about partitioning drives in Linux and can't figure out what to do from here.  Help!

---

### Post by bulldog on 2007-11-08
This is an exellent opportunity to learn some thing.
It's described in the links I provided,read them carefully,there are certain solutions,but no guarantees.
To help you with this issue forces me to read and learn something I probably never have to use.
Maybe there comes someone around who has dealed with this problem,so you can wait till this happen,or try it yourself.

I'm sorry I can't be of more help to you.

---

### Post by Pumalite on 2007-11-08
Need to update BIOS if possible and probably a smaller hard drive. Follow carefully the link re: error 18 that the other poster gave you. When your BIOS and your hard drive are matched, you can use Gparted Live CD to partition.

---

### Post by negzero7 on 2007-11-08
Here's my problem, the BIOS update from HP requires Windows 98/Me/2000/Xp to install and a floppy disk drive to temporarily hold data Im assuming...I have none of that.  The floppy drive in the pc took a crap a long time ago so I cannot update the BIOS. The Ubuntu Live CD runs fine, is there a way from the CD I can fix the partition?  I tried going through the install process and manually partitioning the drive, but honestly I had no idea what to do.  It said I needed a partition for the /root directory but under the filing system (FAT16, FAT32, ext2 and ext3)  I tried several but I had no idea what I needed.  I've played with different settings and couldn't figure out what to do.

---

### Post by confused57 on 2007-11-09
> **negzero7 said:**
> Here's my problem, the BIOS update from HP requires Windows 98/Me/2000/Xp to install and a floppy disk drive to temporarily hold data Im assuming...I have none of that.  The floppy drive in the pc took a crap a long time ago so I cannot update the BIOS. The Ubuntu Live CD runs fine, is there a way from the CD I can fix the partition?  I tried going through the install process and manually partitioning the drive, but honestly I had no idea what to do.  It said I needed a partition for the /root directory but under the filing system (FAT16, FAT32, ext2 and ext3)  I tried several but I had no idea what I needed.  I've played with different settings and couldn't figure out what to do.
A separate /boot partition at the beginning of the hard drive may be all that you need...you can make it around 200-300 Mb, just in case there are several kernel updates, ext2 or ext3 should be just fine for the filesystem(Gentoo install recommends using ext2, I'm sure they have a good reason?).

---

### Post by sandman887 on 2007-11-09
I'm trying that right now, thanks Bulldog. That's a great page. How did you come across such a great reference?

---

### Post by bulldog on 2007-11-09
> **sandman887 said:**
> I'm trying that right now, thanks Bulldog. That's a great page. How did you come across such a great reference?

Look for postings from Herman,it's his site and he has great knowledge about those matters.
Comes around on this forums on a regular base.

[http://ubuntuforums.org/showthread.php?t=603673&highlight=Herman](http://ubuntuforums.org/showthread.php?t=603673&highlight=Herman)

@TS
I'll post a link to the topic of sandman887 and how he solved this problem maybe it is of some use for you.

[http://ubuntuforums.org/showthread.php?t=607492](http://ubuntuforums.org/showthread.php?t=607492)

---

### Post by Herman on 2007-11-10
Hello negzero7,  sandman887, Pumalite, bulldog and all,

negzero7 said:
> Thanks for the replies but I am still confused. The links posted explained a lot about what the problem could be but they didn't really provide any instruction on exactly what to do, other than set up a partition for the kernel to boot from. So....how do I do that? I have no idea really about partitioning drives in Linux and can't figure out what to do from here. Help!So I have been working on that GRUB error 18 link today and I made a new how-to that the GRUB error 18 explanation links to now, about how to make a separate /boot partition.
Here is the error 18 link again, [     Grub error 18]("http://users.bigpond.net.au/hermanzone/p15.htm#18").
...and in it you will now find this new link, [How to make a separate /boot partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition").

Thank you very much for pointing out where  can improve my website for anyone who might need it. 
Please let me know if the new how-to needs more editing. I have tested it of course, and it works for me. 
Actually, I am worried that it might be a little bit difficult for the average user.
For a new install without any files or software added to it yet, re-installing would be easier, probably, and tell the installer to make a separate /boot partition. But there might be times when someone will want to make their separate /boot partition without having to re-install, and it will be those people who the how-to is made for.

Maybe I need to work on explaining how to make a separate /boot partition during an install (or a re-install. It isn't difficult at all when you know how, I just need to think over how to explain it....
I think it will be obvious enough when you try it anyway. This web page illustrates how to set up partitions when installing with the 'Alternate' CD, [Separate /home]("http://users.bigpond.net.au/hermanzone/p14.htm"),  but most people use the Live CD to install with. 
I think it's even easier with the Live CD installer, aysiu's website is about that, here, [U][B][COLOR=#3333FF][B][http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
[/B][/COLOR][/B][/U]I'm not sure how to explain that briefly, ummm, I'll work on it....

Regards, Herman :)

---

### Post by MQMike on 2007-11-10
Hi Herman and everyone –

The topic happened to catch my eye this morning.  Seems lost of folks get the GRUB Error 18.

IMHO, FWIW, Herman, your explanation how to make a separate /boot partition is excellent – plenty of cross references and I noticed your attention to the details & subtle issues for beginners.  As is always the case, people doing this and other command-line work—all of us--should go slow and easy, step by step.  You’ve made it very do-able!

--Mike

---

### Post by Pumalite on 2007-11-10
+1

---

### Post by negzero7 on 2007-11-28
Hey herman, thanks for the great write up.  Sorry it took so long for me to write back but I just moved states and got to play with the desktop some more.  I changed my version from Ubuntu to Xubuntu because of my low system resources but still got the GRUB error 18 (no surprise), but then when I tried to follow your tutorial in terminal, something funny happens.  Everytime I try to open terminal, it kicks me to the log in screen.  I tried the username and password I set up through the original install but they dont work (since its running from LiveCD), so I just hit enter.  The desktop reloads and I try to open terminal, and it happens all over again.  Im so frustrated with this lol!

---

### Post by Herman on 2007-11-29
:) Hello negzero7, 
> Everytime I try to open terminal, it kicks me to the log in screen. I tried the username and password I set up through the original install but they dont work (since its running from LiveCD), so I just hit enter. The desktop reloads and I try to open terminal, and it happens all over again. Im so frustrated with this lol! That's really strange, I have never heard of that type of behaviour before. :confused:

:idea: Okay, what happens when you press 'Ctrl'+'Alt'+'F1' keys then? 

Your 'Ctrl'+'Alt'+'F1 or F2, or F3... , through to F6' keys should give you a 'tty' which is pretty much the same thing as a terminal and can be used instead.
To return to your desktop, (GUI), just press 'Ctrl'+Alt+'F7' keys. :-D

Regards, Herman :wink:

---

