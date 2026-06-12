---
title: "Problem with gparted on ntfs windows partition"
date: 2011-08-03
forum: Installation &amp; Upgrades
---

### Post by aeco98 on 2011-08-03
Ok, i don't speak english very good (i'm from mexico) but i need help with gparted.

When i try to resize the only partition i have (it has windows vista installed) and i got a exclamation point in my partition with gparted, something like this:[IMG]http://ubuntuforums.org/attachment.php?attachmentid=97208&d=1229918673[/IMG]

Sorry about the picture but I had to get out of this forum and i don't have any screenshot program.

I need to know how to solve and resize my partition.

---

### Post by Hakunka-Matata on 2011-08-03
Welcome to the forum.

Have you tried using chkdsk in Windows to fix errors?  I use windows tools for working with WindowsOS, and  GParted for working with Linux OS.

---

### Post by Furball588 on 2011-08-03
> **Hakunka-Matata said:**
> Have you tried using chkdsk in Windows to fix errors? 

Agreed.  chkdsk /f should cure that.  

> **Hakunka-Matata said:**
> GParted is not recommended for resizing  windowsOS partitions.

Since when?

---

### Post by Hakunka-Matata on 2011-08-03
> **Furball588 said:**
> Agreed.  chkdsk /f should cure that.  



Since when?

It is what I have seen in many postings read in this forum.  Postings by well known knowledgeable FMs.  

Resize and work on existing WindowsOS partitions with windows tools.  Not to say GParted won't work on NTFS partitions, but if you're resizing an existing WindowsOS partition, they say to use windows tools.

---

### Post by Furball588 on 2011-08-03
Find a reference then...

I can see that as true when dealing with older versions of gparted when the module was still experimental, but not now...and there's always been that caveat of you resize at your risk :) but I don't think that's ever been exactly specific to one file system over another..

---

### Post by Hakunka-Matata on 2011-08-03
[http://ubuntuforums.org/showthread.php?t=1789267&highlight=use+windows+tools](http://ubuntuforums.org/showthread.php?t=1789267&highlight=use+windows+tools)

post # 12.  and there are many, many more

search on "use windows tools" in the forum search box, you'll get many hits

---

### Post by Furball588 on 2011-08-03
I don't see a post # 12, but I see what you're looking at.....so recommending the windows utility over the gparted does not equate into gparted is not recommended for windows file systems.

We can probably setup a whole thread on the finer points of this.  Look at it like this.  The installer is doing something not recommended when it shrinks a partition to install ubuntu...:)

---

### Post by Hakunka-Matata on 2011-08-03
sorry, it's post #2.

I'm not interested in setting up a thread on that subject, I read who I read, and who I read are very good at what they do, I've learned heaps.  I trust them. it all works for me, so thanks anyway

---

### Post by MAFoElffen on 2011-08-04
> **aeco98 said:**
> Ok, i don't speak english very good (i'm from mexico) but i need help with gparted.

When i try to resize the only partition i have (it has windows vista installed) and i got a exclamation point in my partition with gparted, something like this:

Sorry about the picture but I had to get out of this forum and i don't have any screenshot program.

I need to know how to solve and resize my partition.
On Gparted (answer to someone else's comment) I use for Windows, Linux and Unix.  It does have a peculariar limitation of being a little quarky trying to move/resize the partition that you are booted and running off of...

So for multi-boot installs invoving Windows, I boot off of a Gparted LiveCD move/resize my partitions, then continue when finsihed.  One tip when doing this with WIN... they like to run close to the root pf the disk and do strange thigs if they are in the second half of the tree.

Also, if you back off the partition one sector (or unit) off from the start of the disk (and leave that area unallocated), it will save you later headaches that "sometimes" occur with bootloaders such as Grub and LILO.

If you are already having disk errors, fix those first, as you don't want to move bad data... and you might want to use the "verify" option of move/resize to ensure what got moved matches want was there.

---

### Post by Quackers on 2011-08-04
Hakunka-Matata has given you a "heads-up" with regard to resizing Windows partitions with gparted. This is a general recommendation. 
It is intended to save you from the necessity of recovering your system from scratch (or backups), as errors have occurred using gparted in this way. It is particularly true where the Windows versions are Vista or Windows 7.
There is also the fact that you should defragment any Windows Vista/7 system partition before shrinking it. This is probably the reason that problems occurr in the first place. It can be VITAL to take this step.
As you are already in Windows to do this it seems sensible to use Windows Disk Management screen to shrink the partition. It's quick and easy.

Hakunka-Matata has brought this to your attention in an effort to (possibly) save you some work. It is a recommendation only. It is up to you what tools to use on your system, as it's you that will have to repair anything which goes wrong.
It is certainly not encumbent on Hakunka-Matata to find "references", as you put it, in order to justify his/her advice to you. I would have preferred to see a simple thank you, personally. Some more reading on the forum would give you several sources for the advice given.
Take it or leave it. It's up to you.

There are experienced users who choose to use gparted on these systems who have had no problems. Your choice.

---

### Post by Hakunka-Matata on 2011-08-04
Su Inglés es mucho mejor que mi español. ¿Entendió usted las respuestas?  chkdsk /f deberia arreglar las falles del disco

---

### Post by aeco98 on 2011-08-05
well , first of all , thanks for all the atention that i received from us (Hakunka-Matata, Furball588, MAFoElffen, Quackers.) .

1. This forum is much more best than the Ubuntu-es.org that i used for the first time and i don´t received any reply.
2. I used chkdsk with the option fix and the result is [COLOR=Red]that there's no bad sectors or errors in the disk [/COLOR]
3.Due to windows problems that i recently noticed i need to [COLOR=Red]FORMAT (this has no relation with the hdd)
[COLOR=Blue][SIZE=4][FONT=Arial]Sorry , i have to format but finally i will install dual boot (windows-linux)
Finally:
[FONT=Verdana]This is the best forum in the world.

Note : i've been trying to install ubuntu (without flavor)
when formatting i will install ubuntu studio, i need for :guitar: :lolflag: well , goodbye. ([/FONT][/FONT][/SIZE][/COLOR][/COLOR]I will attempt to help others as you helped me[SIZE=4][COLOR=Blue])[/COLOR][/SIZE]

---

