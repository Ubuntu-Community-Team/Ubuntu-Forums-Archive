---
title: "How do I make a snapshot of my system?"
date: 2006-11-24
forum: Installation &amp; Upgrades
---

### Post by tigershark on 2006-11-24
I don't know if snapshot is the thing that I want to do here.

My situation is that I have 10 computers which has the same hardware and should be configured the same.

I have removed a lot of programs and installed new ones plus a whole lot of tweaking!

And I don't want to do that on every single machine, instead of doing that I only want to create an iso-file, or whatever, of my customized system and installing it on the other ones.

---

### Post by MJN on 2006-11-24
[www.partimage.org]("http://www.partimage.org") should do nicely!
 
(There are many other, similar, methods/tools however I've used this and can recommend it)
 
Mathew

---

### Post by taurus on 2006-11-24
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by tigershark on 2006-11-27
Thank you both very much!

I haven't been able to read all of the guides jet and I'm just wondering if either one of the ways contains a method to create a disk with the backup on.

So that I can boot with the disk on a computer that contains nothing on it and it just works?

Beacause when I quickly read through the guides it seemed that I must first have a installed system with partimage installed and then you can restore the backup, is it like that or can you just restore the backup on an empty computer?

---

### Post by MJN on 2006-11-27
The usual way would be to run Partimage from a LiveCD that already has it installed - I can recommend 'SystemRescueCD' - [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page).
 
It's a handy thing to have around and can quickly boot into a text mode with a whole load of useful tools (e.g. Partimage) at your fingertips. There is also a graphical mode should this be required.
 
You could always follow the instructions at [http://www.partimage.org/Partimage-manual_Boot_root_disks](http://www.partimage.org/Partimage-manual_Boot_root_disks) to create bootable floppies, however I'd still suggest the SysResCD option for the other benefits it provides.
 
Mathew

---

### Post by tigershark on 2006-11-27
Forgive me for being stupid here...

So I can with help from SystemRescueCD create an image snapshot of my system and create an installationcd of it to use to install it on my other computers?

And if that is correct, do I need SystemRescueCD when I install ubuntu on the other computers or could I just boot with the CD I just created and everything i being made automatically??

Again, sorry for being stupid :-| 

Joacim

---

### Post by MJN on 2006-11-27
No such thing as a stupid question... apart from the one you don't ask.
 
As far as this situation is concerened, SysResCD merely contains the Partimage program and an OS to run it in. Hence, to take a snapshot of your machine you could boot from the CD, create a mount point and mount a partition to store an image of the partition you're backing up. Then run Partimage and backup your partition. You could then burn the image to a CD/DVD.
 
To restore on a second PC, just boot with SysResCD and mount your CD/DVD. Then re-run Partimage and restore the mounted image to a new partition on the disk.
 
Does that make any sense? In case you're coming at this from a Norton Ghost background, Partimage is not quite as feature-packed and one such omission is the ability to burn directly to a bootable CD which has all the necessary files to perform a restore with that disc alone.
 
Mathew

---

### Post by tigershark on 2006-11-27
Ah good to know :) 

Okey, then it makes much more sense.

I've checked out [g4u]("http://www.feyrer.de/g4u/") and I'm gonna try that out first.

I'm looking for someting that is a little bit "easier" that Partimage.

Because all I want to do is a pure copy of the harddrive and then clone it to the other computers.

But thanks for all the info!!

Joacim

---

### Post by tigershark on 2006-12-01
Can just say that I've tried [g4l]("http://freshmeat.net/projects/g4l/?branch_id=48255") and it worked like a charm! :D
Real simple and has the ability to backup to an ftp-server which was exactlly the way I wanted it to do.

Just boot up with the iso, either burned to a disk or on a usb-memorystick, and follow the steps. Done!

---

