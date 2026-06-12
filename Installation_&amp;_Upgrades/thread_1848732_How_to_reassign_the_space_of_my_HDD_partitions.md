---
title: "How to reassign the space of my HDD partitions?"
date: 2011-09-23
forum: Installation &amp; Upgrades
---

### Post by xutnubu on 2011-09-23
Ok, I know there may be tons of threads with this question. But not all of us have the exact same partitions.

So, this is my case.

I have a 120GB HDD with 3 physical (primary) partions. From left to right:

dev/sda 16GB for root   -  dev/sda3 102GB for home  -  dev/sda2 2,5GB for swap

I realized that I used to much for root and swap, so I want to take from them and give it to home.
So at the end I would have 10GB for root, 1GB for swap and 109,5 for home.

But, I don't know if I could "damage" any files during the process. I understand that it can be done using Live GParted, which I have ready to use now, on a USB Stick.

But I'd like to read your thoughts on this matter. 

Should I do it? Any precautions?

---

### Post by vinterkind on 2011-09-23
Hi,

I never had any problems with GParted. Give it a go.
But be aware that you should do backups. 
The only hint I can give is, let it do whatever it does. And don't touch it until it's done.

cheers,

---

### Post by garvinrick4 on 2011-09-23
> Should I do it? Any precautions?gparted is a partitioning tool and there is always a chance of something going amiss
when you use one. Back up your personals before using.
Open gparted and take a screenshot of it and post here. Use the paperclip icon and upload
to to your Message box. Easier to see what for you to move. 
I have used gparted quite abit and have not had a bad moment but one never knows.
Just want to let you know that there is always a risk.

---

### Post by ajgreeny on 2011-09-23
Just a final warning, but not for you to be too scared about.

The resizing takes a long time, and I mean a long time, possibly a few hours.  The program runs a full fsck check on the partition prior to resizing, then does the resize, and finally does another full fsck check after the operation has been carried out.  The last time I did it on a large and fairly full partition the whole job took nearly 5 hours, but this is on an old slow machine.  Whatever you do, make sure you don't interrupt the operation, and if this is a laptop, use mains power.

---

### Post by vinterkind on 2011-09-23
that's why i said

> let it do whatever it does. And don't touch it until it's done. :D

an interruption of the process could corrupt the whole filesystem. 
You can imagine what happens afterwards ...

cheers

---

### Post by xutnubu on 2011-09-23
Thanks to all the replys.

I'll do my backup and then proceed.


I've heard that running a defrag software can help, should I do it? I don't know any defrag program for Ubuntu.

This is a pic of GParted, it's in spanish but I think that's not a problem

[ATTACH]202776[/ATTACH]

I don't know why is there 1MiB unassigned between dev/sda3 and dev/sda2...

---

### Post by vinterkind on 2011-09-23
defrag is merely a microsoft related fairy tale to soothe your mind.

linux filesystems don't need that. 
AFAIK there is no one using one...

---

### Post by Elfy on 2011-09-23
Be aware that after you have shrunk the / partition you will need to move it to the left of the /home partition in order to add it to /home.

Personally I'd not bother trying to resize swap but would just delete it and recreate a new one.

You'll likely need to right click and swapoff to do anything to the swap anyway.

Lastly - > Should I do it?that's up to you - but if you were me you'd not be bothering given the amount of space you've got free in /home :)

No need to give any warnigns - they've already been dealt with ...

---

### Post by xutnubu on 2011-09-23
Mission accomplished, guys. Thanks :)

No problems until now, everything works the way it should.

---

### Post by garvinrick4 on 2011-09-23
> **xutnubu said:**
> Mission accomplished, guys. Thanks :)

No problems until now, everything works the way it should.
Hey xutnubu looks like you are going to be a Ubuntu user, welcome to the Forums and will
see you here. Enjoy your Ubuntu. 5 guys told you to be careful I guess you took heed and did a good
job.

---

