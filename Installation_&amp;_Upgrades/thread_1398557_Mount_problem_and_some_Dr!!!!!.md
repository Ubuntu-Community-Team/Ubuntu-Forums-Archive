---
title: "Mount problem and some Dr!!!!!"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by emma00 on 2010-02-04
My ubuntu 9.10 is acting strange nowadays,when my grub comes a command line interface came and is shows some error of mount problem and after entering help command and doing some mount command it showed something fscl command don't remember it now then have to press Y and i did it my ubuntu booted but now when i started my transmission client it shows this error:

Couldn't open "/home/emma/.config/transmission/lock": Read-only file system

 and sometimes i get Dr opping to shell!!!!  on my command line interface

can not find the root and list goes on.........

I know one thing for sure that this happens when power goes off,as its common in my part of country,sorry for borring talk:o but any ideas what to do??????

---

### Post by Herman on 2010-02-04
:D Yeah, I know what you mean, the power where I live is a little shakey too, especially at this time of the year when we often have thunder and lightning storms around. Also, my dog sleeps under the table and once in a while manages to accidentally uplug my computer wires from the wall. 

To run a file system check, boot your Ubuntu Live CD and open a terminal and run 'sudo blkid', or 'sudo fdisk -lu' to see what hard disks and partitions you have and pick out the disk and partition number for your Ubuntu installation. 
It should look something like '/dev/sda2' or '/dev/sdb3', or something like that.
```
sudo blkid
```When you find right device location, use a command like this, 
```
sudo e2fsck -C0 -p -f -v /dev/sda1
```That will run a safe but effective file system check and fix most ordinary problems in your ext series file system which you have Ubuntu installed in.
If your problems are more serious and that file system check can't fix it with thosse options, it will give you feedback to let you know and advise you what other options you should use to run another file system check.

An easier way to do it if you are afraid to use the command line is to open GParted partition editor in the Live CD, right-click on the partition and click 'check'. Then click the 'apply' icon and click the 'Apply' button in the confirmation dialog that will pop up.
GParted will run your file system check for you.

---

### Post by emma00 on 2010-02-05
I think you know that much because of your dog unplugging your wires often ;-),at least you got to know something its different in my country due to loadsheding anyway thanks a lot and one more question how i go to terminal when ubuntu live cd is in because the installation menu comes and thanks again :popcorn:   :lolflag:

---

### Post by Nebelhom on 2010-02-05
I'm assuming he means:

Choose "Try Out Ubuntu Without Any Change To Your Computer" in the install menu

Load up the test gui

then press Alt+Ctrl+F2 to open a virtual terminal

do your shenanigans

then press Alt+Ctrl+F7 to go back to the gui 

(if you can't go back <- unlikely; sudo reboot)

---

### Post by Herman on 2010-02-05
:D Yes, Nebelhom is right, it depends if you're using the Ubuntu 'Desktop' Live CD which most people use now or the 'Alternate Installation CD that is mainly for special installations.

I'm guessing you would have the 'Desktop' Live CD but now I'm confused about that because you say 'an installation menu comes up'? 

If you are using the 'Desktop' Live/Install CD then you can do it the same way as Nebelhom suggested.
Or another way would be to boot into your Ubuntu Live CD system and open a terminal by going 'Applications'-->'Accessories'-->'Terminal', but Nebelhom's way would be quicker probably.

If you are talking about the 'Alternate Installation CD' then you can boot it into ;Rescue Mode', I think, and use the terminal that way. It will run you through a series of questions first about which is your / (root) partition. Probably that would be a little more tricky if you're new, but maybe you can do it. When I first got Ubuntu it was the only method we had. It has been a while since I have tried those features out myself so I'm not sure how to do it exactly with the 'Alternate Installation' disk. If you need me to let me know and I'll pop one in and run through the procedure myself for you first and take notes so I can advise you.

---

### Post by emma00 on 2010-02-05
Thanks Herman and Nebelhom  :D :D

 i will give it a try and will let you know and yes by the installation menu i meant the options came as going to install ubuntu.[URL="http://ubuntuforums.org/member.php?u=495543"]
[/URL]

---

