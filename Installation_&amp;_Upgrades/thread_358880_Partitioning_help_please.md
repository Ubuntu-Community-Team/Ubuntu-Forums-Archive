---
title: "Partitioning help please"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by Poman on 2007-02-11
Hi,

I've just tried Ubuntu from the live cd, and it seems to work fine. My hardware seems to support it for the most part. I really like it as well. Now I'm trying to install it on a partition of one of my hard drives, but I'm afraid to go ahead because I've had problems in the past with Suse9 messing up my partitions. I'd like to dual boot to WinXp whenever necessary and don't want to lose any information on the drives. 

I've got two hard drives. One is 160Gb SATA, partitioned in winxp as c: (30Gb) and e: (130Gb). Those numbers are rough, and the other is an older 40Gb drive named d:

I don't understand why it seems that Ubuntu needs to "mount" something on apparently every single partition. Can't I just format e: and put Linux on that? I forget how it worked in Suse, but this system sounds familiar. I just don't want to mess up.

I'll continue running it off the CD for now, though your help would be greatly appreciated. I'm happy to start using something other than WinXp, and will never upgrade to Vista! I just need to make the "move" to Linux sloooowly. My main interest is digital photography, and e-mail. :) 

Thanks!

---

### Post by Herman on 2007-02-11
Hello Poman,
How much information on your drives would you be risking and how important is it to you?
What media, (CDs, DVDs, external hard disk, friend's computer, etc), would you have around that you can make a backup of it all with?

You will be taking a risk no matter how safe the disk partitioning program is, and the only way to make sure is to back up all your data.

Ubuntu is great for digital photography and email.  I recommend it for email and the  internet because it isn't vulnerable to viruses and spyware. For digital photography, we have lots of good programs, probably GIMP will be good. I use GIMP often. (Gnu Image Manipulation Program).

However, I think you should wait and keep on using the Live CD until you can find some way of backing up your data. 

Regards, Herman :)

---

### Post by mikewhatever on 2007-02-11
> Can't I just format e: and put Linux on that?
This is exactly what you should do, but you'd still need to mount the partitions to have access to them. Use [THIS GUIDE]("http://psychocats.net/ubuntu/installing") for mounting. It has nice pictures. :) 
Basically, your Linux/Ubuntu partition is mounted as </>, 
swap partition as <swap>,
and windows partition as </media/sda1>

The first two must be mounted like that, but the third one can be mounted differently. I'd suggest to stick to defaults if not sure. You can read more about mount points here: [http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)
Post back if you need more help.

---

### Post by Poman on 2007-02-11
wow, this is some great help! I will definitely do some backing up and reading up before fully installing, though it seems to be pretty simple once I learn a few basics.
Thanks again!

---

### Post by Poman on 2007-02-12
I'm impressed! Ubuntu is now running side by side with winxp on 80Gb of that partition e: drive I mentioned. I backed up some stuff and zigzagged a bit, to make sure I understood what "mounting" meant, and before finalizing the install process, but I got it all installed just right it seems. Ubuntu seems to be really stable, and I haven't lost any data. I feel that I'm happily getting into Linux again!

I made three partitions for Ubuntu: /documents - 68Gb, /swap - 2Gb, and / (root) 10Gb, in that order. Root is at the end, I hope that's ok. I followed the example in the install tutorial.

Everything seems to be running perfectly, and Grub allows me to dual boot at startup. I just have one problem...

Firefox is not displaying images at their full resolution, and I've had this problem whenever running Firefox in the past, even in Windows. I just can't figure out if I need to install some extension or add-on. Websites just don't look as good as they do in ie7, even fonts can be a little garbled if I don't decrease their size. It seems to be something basic that I haven't figured out yet, and I've so much to learn now about Ubuntu.

Thanks for the help,

---

### Post by Herman on 2007-02-12
Try (in Firefox), going 'edit'-->Preferences'-->(contents tab), and look for the fonts and colors area there in the middls of the window. You should see a spinbox there where you can increase or decrease your default text size. Try adjusting that setting and see if it helps.

Apart from that, it depends on what browser the website is made for. People who are advanced at making websites seem to know all the tricks to be able to make their website look good in any browser. These may be trained professionals doing it for a living, probably in advertising. Websites made by ordinary people like me who are more interested in getting the content in and not so well informed about presentation tend to have websites that look okay in some browsers and not so good in others. it's the website owner's fault in those cases. I admit it, I'm one of those website makers, sorry. Mine should look okay in Firefox, 

Regards, Herman :)

---

### Post by Poman on 2007-02-12
Thanks for the help, but I have a bad feeling that it's because I'm running the version for AMD64. This version of firefox doesn't support flash player it seems. I'm also looking on the firefox website. Maybe I'll give Mozilla a shot.

---

### Post by Poman on 2007-02-12
No, somebody just told me that images in Firefox look normally faded, and that my fonts aren't True Type most likely. I need to figure out how to live with this.
Cheers! :)

---

