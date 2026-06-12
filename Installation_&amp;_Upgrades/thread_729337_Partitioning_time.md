---
title: "Partitioning time"
date: 2008-03-19
forum: Installation &amp; Upgrades
---

### Post by Dexter00 on 2008-03-19
Hi,

I'm using GParted from the live CD of Ubuntu 7 to partitioning my hard disc that contains Win XP.

**The estimated time is 6 hours**, I'm on a P IV, 1 Go of Ram, and 160 Go, I want to reduce the XP partition to 152 Go.

Is it too long ?

---

### Post by Herman on 2008-03-19
6 hours! 
That's way too long, six minutes would be more like what I'd expect.

---

### Post by mattk132 on 2008-03-19
dude, use a program called partition magic.  Or you can go to windows and go to control panel.  Then go to administrative tools.  After that simply go to computer management.  There is a tab in that menu that you can use to shrink your xp partition.:)

---

### Post by Dexter00 on 2008-03-19
What's the reason for that long partitioning time ?

If I cancel the partitioning operation, I can lose my filesystem...

---

### Post by Herman on 2008-03-19
Partition Magic and Windows Disk Management are great for Windows-only computers, but they don't seem to mix well with Linux. I don't know why.

I'm not sure if it's advisable to cancel a resize operation while it's in progress. You will be taking a risk. 

By the way, what's a 'Go' and how does that compare to a GB? 
1 GB of RAM should be plenty.

I'm wondering if your BIOS has the old 137 GB hard drive limit? 
Was your PC made before around September 2001 or earlier? If so then maybe that's why GParted is stuck. It could be that GParted is trying to work on an area of your hard disk that's not even accessible. I'm not sure about that, still thinking that over...

---

### Post by Dexter00 on 2008-03-19
> **Herman said:**
> 
By the way, what's a 'Go' and how does that compare to a GB? 
1 GB of RAM should be plenty.

I'm wondering if your BIOS has the old 137 GB hard drive limit? 
Was your PC made before around September 2001 or earlier? If so then maybe that's why GParted is stuck. It could be that GParted is trying to work on an area of your hard disk that's no accessible. I'm not sure about that, still thinking that over...

I mean GB by GO.

No, my computer is a new one...

---

### Post by Herman on 2008-03-19
Flip a coin, if it's heads, interrupt the process and take control of your computer back again.
If it's tails, wait a while longer and see if it finishes. Give it a set time limit.

Something's wrong for sure, maybe nothing's happening at all, or it finished ages ago but for some reason is just stuck.

---

### Post by Dexter00 on 2008-03-19
The progress bar is progressing, and the "time left" is also progressing "100 GB from 149 GOB"...

---

### Post by Herman on 2008-03-19
Oh, gosh, I don't know... 
Weird things do go wrong sometimes. I guess it depends on how much of a hurry you're in to use the computer again.
You might just need to wait a few more minutes and it'll finish, but by the sounds of things you might be waiting forever.

If you decide to interrupt it, and it does corrupt your partition table, you should be able to rebuilt it with TestDisk. If it damages the file system, that would be a lot worse, but you might be able to fix it with a file system check, and if that doesn't work you might need file recovery tools like PhotoRec, if you don't have your files backed up.
Or maybe it has finished and everything's fine. or maybe it hasn't done anything and everything's fine.
Who knows.

---

### Post by Herman on 2008-03-19
> The progress bar is progressing, and the "time left" is also progressing "100 GB from 149 GOB"... If it is making progress then it's probably okay and it would be best to wait.
What do you mean the 'time left' is progressing? Do you mean it's increasing?, or decreasing?

---

### Post by Dexter00 on 2008-03-20
@Herman: it was decreasing.

The partitioning is finished with errors. I rebooted without CD, Win XP did a scan, and ran correctly.

What I have done is resizing windows partition. If I do delet all partitions (win's partition) and create from blank a partition for Ubuntu, and an other for Win, all with GParted (from the live CD), this will go faster ? But I'll have to reinstall Win...

Thanks.

---

### Post by Herman on 2008-03-20
If Windows booted  and ran CHKDSK, and seems to be working okay I'd say it's probably alright.
If you really feel like re-installing Windows, that's up to you.

I don't know if GParted will be faster if you delete all partitions and make a new one for Windows and one for Ubuntu. It should only take you a few minutes. It depends what's wrong. I think the only way you'll be able to find out for sure will be to try it and see what happens. If it's quick this time then maybe it was slow because it was trying to del with errors or some kind of problems last time.
Maybe this time it will be quick, (it should be), but if there is something about your hardware that's making GParted slow down then it might still be slow, but I don't think that's likely.

Regards, Herman :)

---

