---
title: "Dual boot install"
date: 2012-06-22
forum: Installation &amp; Upgrades
---

### Post by mayagrafix on 2012-06-22
[IMG]http://i16.photobucket.com/albums/b1/mayagrafix/binaryes/GpartedScreenie.png[/IMG]

Here is a screenie of gparted showing my HD with Ubuntu 12.04 installed on sda1.

My question is: Where is Windows? 

This is a new HD (500 Gib) where I first instaled windows on C:\ (or sda1) and made a second partition for Ubuntu (sda6) but when I fired up the Ubuntu installer, it said: "You already have Windows Vista installed, would you like to install Ubuntu along side?

I thought I would point out the second partion at some point later, etc.

Windows boots up nicely, thank you very much, and Ubuntu 12.04 boots up great also, but...

Are they both on C:\ (sda1)? on the first partiton? how does this work? will I be over wrtitng files at some point?

---

### Post by oldfred on 2012-06-22
I do not understand question.

You have Windows in the NTFS formated partition sda1 and Ubuntu in sda6. They are separate. Windows will not see the Linux formated partition nor swap, but Ubuntu will see the NTFS partition. They are separate.

Many of us suggest a separate NTFS partition for shared data that you may want in both systems. Since Windows does not have a lot of used GB you can shrink it with Windows tools if Vista or 7 and create sda2 in the unallocated space. That then can be a shared NTFS data partition. 

Windows for whatever reason does not seem to like a lot of writing into its root or system partition, but reading is ok. Also Ubuntu shows all the hidden files & folders that Windows hides to prevent you from accidentally damaging system, so set sda1 ( or c: ) as read only if you mount it in Ubuntu and use a data partition as read/write.

---

### Post by mayagrafix on 2012-06-23
Thanks for your patience. After some sleep, I can see now that you are right. Ubuntu did get instaled corectly in the second partition (sda6) and windows resides in the principal partition (sda1). There is a colum in screen cap that notes used and unused space on both partitions (duhhh!).

Now I want to ask if it is ok to copy some files from an external NTFS HD to the sda1 (NTFS partition) using Ubuntu 12.04.

The external NTFS HD does not show up in Windows OS, but Ubuntu OS recognices it and I can access files on it from with in Ubuntu 12.04 (using Unity or Nautilus file manager).

So I want to recover files from the external HD via Ubuntu. Will there be any problem for Ubuntu to write files into NTFS partition (sda1) of HD?

Thanks, as always this board has been a great help. :p

---

### Post by nipunshakya on 2012-06-23
> **mayagrafix said:**
> Thanks for your patience. After some sleep, I can see now that you are right. Ubuntu did get instaled corectly in the second partition (sda6) and windows resides in the principal partition (sda1). There is a colum in screen cap that notes used and unused space on both partitions (duhhh!).

Now I want to ask if it is ok to copy some files from an external NTFS HD to the sda1 (NTFS partition) using Ubuntu 12.04.

Its totally good to copy files from an external NTFS using ubuntu 12.04.

> **mayagrafix said:**
> The external NTFS HD does not show up in Windows OS, but Ubuntu OS recognices it and I can access files on it from with in Ubuntu 12.04 (using Unity or Nautilus file manager).

So I want to recover files from the external HD via Ubuntu. Will there be any problem for Ubuntu to write files into NTFS partition (sda1) of HD?
Thanks, as always this board has been a great help. :p
  If i were you, i wouldn't want to mess up with the drive(sda1) by copying files there. Just a worse case scenario, if your windows partition fails, it would be difficult for you to get back your data that you will be copying...isn't it? 

In my opinion, your windows partition(sda1) doesn't need that much space. Why don't you shrink your c: to around 92 gb first, and then create another NTFS partition out of the extra 200gb of space that comes out of c:. This way, your new partition could be used as a repository for both c: and ubuntu as well... 
If you want to do that, u can do it from 'disk management' application software in windows. **Don't forget to restart to windows atleast once after you are done with arranging your partitions in** [B]its c:.

[/B] If you want to use gparted, boot into livecd, run gparted from there and see the link below, which has a step-by-step guide to resize your partitions....

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Happy Linuxing

---

### Post by mayagrafix on 2012-06-23
Thanxs!!

---

### Post by nipunshakya on 2012-06-23
Welcome... If your problem is solved, please mark it as [SOLVED] from the thread tools on top right

---

### Post by oldfred on 2012-06-24
+1 on WinuxUser's suggestion of a separate shared NTFS data partition.

---

### Post by mayagrafix on 2012-06-24
Great! have a new shared partition for data waiting to be filled, thanks to great advice from you guys :p

One more question: is there a program taht will take care of copying files from on HD to another or is drag n' drop good to go?

---

### Post by nipunshakya on 2012-06-24
Its good to just do a ctrl+c and crtl+v rather than drag and drop... though no problem with drag and drop too....

Happy Linuxing

---

### Post by mayagrafix on 2012-06-27
[IMG]http://i16.photobucket.com/albums/b1/mayagrafix/binaryes/ParticionesWin-Ubuntu2.jpg[/IMG]

Here is a screencap from the Windows disk manager. It shows the partition Ubuntu used to install itself (nice install manager, congrats Ubuntu team! it figured out all by itself that the unformated empty space was for Ubuntu). Windows resides on the C:\ (sda1), Ubuntu is on the 71.21GB volume that has no name, and the other two logical drives are shared data NTFS volumes I made with Gparted as per thread sugestions. So far so good ...

However, is there a way I can blend the 2 NTFS (volumes G + F) shared data logical drives into one? G is a primary partition and F is Logical volume... its kinda problematic to have to deal with the two separate storage areas (G: is 200 gigs and F: is almost a 100 gigs).

Why is one a Primary partition and the other a Logical partiton? did I screw up when using Gparted?

Also whats up with the 3.24GB primary partion space left over at the end? no name either. Is it a Linux memory swap thing or something?

Thanks a million for your great help and wonderfull advice. I should have learned all of this by now but I only get to practice every once in a blue moon, that is to say every so many years. ):P

---

### Post by oldfred on 2012-06-27
Linux's gparted shows all the partitions better. :)

The partition at the end is probably swap. If you encrypt /home gparted will not show it either as it cannot see the encryption.

It is a bit of work to move partitions around. It becomes like the old slide puzzles. You do need good backups as you will be using gparted to move data and any power failure or interruption corrupts partition(s).

Partitions do not make sense to me, as even the logical partition has to be in the extended which counts as one of the 4 primary. Is both swap and the 100GB in the extended?

Maybe best to post screenshot from gparted. You can upload screen shots with the paperclip icon in the edit panel above your message.

---

### Post by nipunshakya on 2012-06-27
From your disk manager screenshot, it can be clearly told that the first three drives(c:, g:, ubuntu installation drive) are primary partitions... on top, the last partition u used for swap is also marked primary partition(Particion primaria) which is a bit confusing here because windows can have 4 primary partitions only (or 3 primary partitions and one logical partition) at one time of partitioning... However, the f: is being mentioned as a Logical partition as well.. so i am getting a bit confused here....
[B]
you cannot merge a primary and a logical partition.[/B] 

so if u want to merge now, you have to format the logical drive, which i dont suggest because you have to move your partitions here and there, (described well in post #4's link i gave u)
my suggestion: run gparted, print the o/p image of your partition and share it here...
gparted is available at the software center btw...

So far it looks that everything is fine and no tweak arounds are required... the more you format the drive, the more you create bad sectors in it... beaware of that too buddy...

Lets c your gparted scheme for partitions first...


Goodluck.
Happy Linuxing

---

