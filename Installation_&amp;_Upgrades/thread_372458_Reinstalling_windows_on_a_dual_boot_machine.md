---
title: "Reinstalling windows on a dual boot machine"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by Ezabel on 2007-02-28
Hi,

I've got a dual boot set up with Ubuntu 6.06 and Windows XP, and I need to reinstall the windows partition (or upgrade it to vista). Windows is on a separate partition on my 80gb harddisk, and there is a shared Ubuntu/Windows partition for my files. 
Now I was wondering if I can reinstall or upgrade windows without doing damage to any of the Ubuntu partitions.  Right now Ubuntu is my main OS, but I've been told that windows may take over Grub and stop me from starting Ubuntu after reinstall...
Also, would it make any difference if I'd install xp or vista?
Thanks for the help :)!

---

### Post by Kateikyoushi on 2007-02-28
If you install vista or XP your geub is going to get overwritten, so have to follow these steps to reinstall grub.

[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub)

I did not encounter problems when I used vista but that was in the beta age some people had problems adding vista to their grub, but I think it wouldn't matter install whichever you prefer.

---

### Post by orb9220 on 2007-02-28
Be careful I believe to do a install of Vista it wants to format the whole drive.  Be sure to verify this.

But when I do a clean install of xp I have to redo the grub using this thread.
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

### Post by fiShbRaiN on 2007-02-28
Hello all,

uncanny--- sort of....
this is my first post here and this thread is similair to my own issue.

Ive got a 80Gb system HD partitioned with XP and Ubuntu. I originally had XP and repart'd it to put Ubuntu on in a dual boot scenario. Worked fine. As I got more and more into Ubuntu I repart'd a couple of times to take space from XP and add more space to the Ubuntu partition.

But my latest repartition gave me errors before suddenly rebooting. Now XP wont boot at all- command prompt, safe mode, etc. The logo briefly appears, then a bluescreen for a split second, and the machine resets.

When I boot into Ubuntu, usually my "XP-SYS" partition (NTFS) is mounted and appears on my desktop. It's not there. If I try to mount it I get an error.

Is my XP partition dead? 
Is there any Linux/Ubuntu software you recommend that might let me do some data recovery on it?

Cheers,

---

