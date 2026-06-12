---
title: "multiple linux distros on one box"
date: 2008-09-19
forum: Installation &amp; Upgrades
---

### Post by Ric1501 on 2008-09-19
help needed for me - a newbie

need to know if I can install Debian on my system that already dual boots with Ubuntu (all flavors updated) anf Vista Ultimate. plenty of run with 320 hdd, just wondering if I install into same partion with existing Ubuntu or do I have to make separate partion for Debian

awaiting anyone's reply if this is a go or suggest another feasible means to compare these two distros

thanx in advance - ric

---

### Post by Herman on 2008-09-19
> need to know if I can install Debian on my system that already dual boots with Ubuntu (all flavors updated) anf Vista Ultimate.  Yes, you can.
> plenty of run with 320 hdd, just wondering if I install into same partion with existing Ubuntu or do I have to make separate partion for DebianYou can't install in the same partition. You should be able to resize one of your existing partitions and create a new partition for Debian though. 
Both distros can share the same swap area, unless you plan on using 'hidernate' mode instead of shutting down. In that case, make a swap area for Debain.
If you have a separate /home partition, both distros can share the same /home partition.

---

### Post by Ric1501 on 2008-09-19
H - so yes it is okay to install with Ubuntu ? I will use the same swap, same home, but cannot split ubuntu partition because you can only have four 1- vista 2-ubuntu 3-/home and swap.  

any ideas?  ric

---

### Post by Herman on 2008-09-19
You can only have four primary partitions.

If you make one of your primary partitions into an 'extended' partition though, you can make more partitions inside it called 'logical ' partitions.

The best way might be to resize one of your partitions and delete your swap area.
Make a new 'extended' partition (4), and then make a new swap area (5). 
Your new / for Debian can be (6). :)

---

### Post by Ric1501 on 2008-09-19
think my last reply was lost into the void - second time to reconfirm:

leave vista part alone, delete swap, resize / and create logical part, leave /home alone ...

? will I loose whatever was upgraded or updated within Ubuntu when I do this ?

---

### Post by Ric1501 on 2008-09-19
ic - del swap, resize / , leave /home alone (lol), load debian into logical of / and finally recreate swap ... ? though: will I loose everything I upgraded (updated) to within my Ubuntu ...

---

### Post by Herman on 2008-09-19
> ic - del swap, resize / , leave /home alone (lol), load debian into logical of / and finally recreate swap ... ? though: will I loose everything I upgraded (updated) to within my Ubuntu ...Well, I'm not exactly familiar with your particular partitioning details, you could post a copy of the output for 'sudo fdisk -lu', or a screencap from Gnome Partition Editor (GParted).
If I could see something like that I would be able to comment more, but vaguely it sounds like you have the idea. 
It would be more normal to leave / alone and resize /home.

I can't imagine how you would lose anything you installed in Ubuntu by deleting your swap area. The swap area is like a page file in Windows, (for your memory), except it's in a partition instead of just a file.

Later, you would need to edit /etc/fstab with a new UUID number for the new swap area, so your Ubuntu will find it and use it.

---

### Post by Ric1501 on 2008-09-19
as requested

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   411649559   205824748+   7  HPFS/NTFS
/dev/sda2       411649560   440952119    14651280   83  Linux
/dev/sda3       440952120   622599074    90823477+  83  Linux
/dev/sda4       622599075   625137344     1269135   82  Linux swap / Solaris
r@ub1501:~$

---

### Post by Herman on 2008-09-19
:) Okay, thank you.

You have Windows Vista Ultimate in partition number 1, size 210 GB.

I don't know for sure if partition number 2 is / or not, but I guess probably it is. on 15 GB. That's probably a little more than is really needed for / , but it's okay.

Your partition 3 is 93 GB, so I would presume that would be /home.
That's the one to resize to make room for Debian.
Assuming that's /home, it's also the one you can share with Debian if you want (optional and maybe a little advanced).

If you do want to share the same /home, you could probably resize the 93 GB partition around 10 GB or so smaller.
10 GB or so would be enough for Debian's /
Make your new swap area 1 or 1.3 GB again.

If you're not going to share the same /home, (easier if you're feeling cautious and if you're not too experienced with Linux), then it depends in which distro you will want to store the most files.
You might want to divide the Ubuntu installation in half or some other portion, it's up to you.
Maybe it won't matter very much, as either operating system can easily mount the other one for access to the same files anyway.
Personally, I prefer to install each distro in it's own integral / partition, with the /home folder inside /, so that each installation is independant when I'm multi booting (which is all the time).

The swap area is partition 4, and size: 1.3 GB, but you will need to delete it to free up a primary partition number so you can make an extended partition number 4.

---

### Post by Ric1501 on 2008-09-19
you are correct

sda 1	vista ultimate
sda 2	/
sda 3	/ home
sda 4	swap

will do the following  after my cup of coffee

delete 4 (swap)
resize 3 ( 40G /home and  40G debian )
create swap with remainder

? is - after I install debian as planned, do I create a home (/home) or 
just make all of it debian (do I need to create another /home)

also, been to your websites and sure do like them
looks like you are the guru downunda
being retired military, spent some time there
received good hospitality and such ...
appreciate all guidance given, 
jus had to confirm both would co-exist before actual input 

many, many thnxs - ric

---

### Post by Herman on 2008-09-19
> ? is - after I install debian as planned, do I create a home (/home) or 
just make all of it debian (do I need to create another /home)***During*** your Debian installation, you will come to a partitioning menu. 

The simplest thing to do is just to install Debain in it's own single integral / (root) partition with it's own /home directory (folder) inside it.

The next simplest thing to do would be to divide up the free space and make another / (root) and another separate /home for Debian. (I don't know why you would want to do that though).

The slightly more advanced/adventurous thing to do would be to make a new partition as / (root), and select the 93 GB partition (or the one that used tobe 93 GB before it was resized), and register it as /home. **Do not format it**. You should be able to allocate it as your /home partition somewhere in the Debain installer's partitioning menus.
8-) In  my opinion, it would be kind of cool if you decide to do it this way, since you already have one separate /home made anyway.  (If you want to).

I beleive the Debain installer is still quite similar to the Ubuntu 'Alternate' CD's installer, shown in some of my web pages. (See my sig link for details).
Or. more accurately maybe, the Ubuntu 'Alternate' CD installer is somewhat similar to the Debain installer, since Ubuntu is based on Debian.
Also see: [How The Installer Works]("https://help.ubuntu.com/7.04/installation-guide/i386/ch06s01.html") - Ubuntu documentation.

---

### Post by Ric1501 on 2008-09-20
it worked - I now have vista ultimate (soon to go), ubuntu 8 (all flavors), debian 4,
suse and fedora - gonna try all to see which one I like the most. ubuntu (gnome) seems to be my first choice as of now. wondering if there is a graphic interface with debian - it booted into cmd line - no window environment ! did I miss something during install? anyways - thanxs for taking the time to ponder if multiple linux programs can all be run on one laptop - yep, a laptop. think I forgot to mention this in my first query ... Dell 1501 Inspirion  with usb cable connect cellphone (sprint rzar3) for www access ... 

will be checking your sites for info and reading - keep up the excellent tutorials and such

thanxs again - ric

---

### Post by Herman on 2008-09-20
:) Yay!  I'm glad you're having fun with Linux. 
Well done! Congratulations!

Debian should have a GUI.
Maybe it didn't set itself up correctly for your graqphics card or something. Sometimes you can run 'sudo dpkg-reconfigure xserver-xorg' from the command prompt, and it will then set up it's xserver better. Then you type 'startx' and the xserver might start.

Otherwise, try this command to see what video card you have,
```
lspci -x | grep -i "vga\| display"
``` Or, you can shine a light inside your computer case and take a look around. - Oh! It's a laptop. Well, you might find it easier to find out some other way like checking the manufacturer's website,you should be able to find that kind of information there too.
As soon as you know, you can go to Debian Web Forums and look for a how-to on setting up Debain with your kind of video card.
> will be checking your sites for info and reading - keep up the excellent tutorials and such He-he, okay, thanks, keep on having fun and enjoying Linux! 

Regards, Herman :)

---

