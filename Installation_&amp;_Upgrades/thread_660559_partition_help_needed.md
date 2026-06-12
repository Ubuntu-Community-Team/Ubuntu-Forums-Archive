---
title: "partition help needed"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by vcooke on 2008-01-06
Hello,

I'm trying to install Ubuntu 7.10 onto my toshiba laptop for the first time. I'm just at the point of partitioning, and it doesn't seem to be going well. I chose manual partitioning, and tried to resize the /dev/sda1 partition that had windows in it (just so that I could save all my old files - but at least I also have them backed-up). When I tried to resize the partition, it came back saying that it couldn't resize, that an error was detected. Now it says that there is no memory used in that partition, and when I go to try to edit that partition, the box that pops up only lets me edit: 'use as' (ntfs) and 'mount point' (/windows) - not the size.

What should I do? How can I create a new partition now? Thanks all in advance for your help. And sorry if my explanation isn't too clear - I'm not all that computer savvy.

---

### Post by logos34 on 2008-01-06
try the suggestions here:
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)

---

### Post by vcooke on 2008-01-06
Thank you for the link. I tried to follow those directions. I think the problem is that I've already tried to do the partitioning myself, and I messed it up somehow. I went through manual, and when I tried to resize it, I think I accidentally changed the 'mount'. Now it won't let me resize the partition at all. How do I get around it? Do I need to just erase that partition completely now? Can I do anything to not erase it? I've got all the files backed up, but it would save me a lot of anxiety if I could just resize it without deleting it. 

Thanks again, I am grateful for any help.

---

### Post by logos34 on 2008-01-07
Can you use Gparted on the live cd to shrink it? (system>admin>gnome part. editor).

Try that first and if it works then click on the installer again and tell it to use the freed space.

---

### Post by vcooke on 2008-01-07
Thank you for replying. I just tried that like you said. It says I can't resize it. The name has a warning sign next to it (little exclamation mark) and when I go to resize/move, it won't let me move anything, says that the minimum size is the same as the maximum size. I checked its information. I don't know what to look for, but it says that its not mounted (is that a problem?) and then it gives a long warning that seems to be all about 'checking filesystem consistency' then it says 'cluster accounting failed at 16667 (0x411b): missing cluster in $Bitmap' and then repeats itself... any ideas? I'm completely stumped.

---

### Post by logos34 on 2008-01-07
> but it says that its not mounted (is that a problem?)

that's what you want--not mounted (can't resize a mounted partition anyway)
> 
then it gives a long warning that seems to be all about 'checking filesystem consistency' then it says 'cluster accounting failed at 16667 (0x411b): missing cluster in $Bitmap' and then repeats itself

did you run error checking w/repair option in windows per the link I gave you?  Or just defrag?

> The name has a warning sign next to it (little exclamation mark) and when I go to resize/move, it won't let me move anything, says that the minimum size is the same as the maximum size

Approx. how much free space is there on the windows partiton that you're trying to shrink?

EDIT: You could also try the [Gparted Live CD]("http://gparted.sourceforge.net/livecd.php")--sometimes that works where the version on the ubuntu live install cd fails.

---

### Post by vcooke on 2008-01-19
Wow, thank you so much. I did it and it worked. Then I went back to that link you gave me and tried it from the beginning, and fully installed linux. Thx for everything. Here's to embarking on a new adventure!

---

