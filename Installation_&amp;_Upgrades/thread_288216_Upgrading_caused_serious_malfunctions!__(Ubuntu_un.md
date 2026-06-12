---
title: "Upgrading caused serious malfunctions!  (Ubuntu unusable)"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by daFoos on 2006-10-29
I upgraded my amd64 Dapper Kubuntu to Edgy today using the download instructions from the main site.

Now the desktop won't even load!  I get this weird screen of primary shapes and colors!  How can I fix this?!

I need this stuff quick!

---

### Post by victor_c26 on 2006-10-29
This is happening to everyone who upgrades from 6.06.

Right now it's advisable to just start from scratch with Edgy Eft. As upgrading from 6.06 will cause major bugs and instability.

---

### Post by daFoos on 2006-10-29
well that's sorta comforting I guess...

so what do you mean start over from scratch?  Where do I put 6.10 on my hard drive and will it still be able to access my Dapper partition? 

thanx for you quick reply.

---

### Post by Aikon- on 2006-10-29
> **daFoos said:**
> well that's sorta comforting I guess...

so what do you mean start over from scratch?  Where do I put 6.10 on my hard drive and will it still be able to access my Dapper partition? 

thanx for you quick reply.

That's not comforting **at all**!! Compared to Ubuntu's track record, this release appears to be a serious blunder.. I still can't get the Live CD to load X, and from what I've been reading if I force the install using the Alternate CD, then when I go to actually boot, I ***still*** won't be able to load X!

---

### Post by DJ Wings on 2006-10-29
> This is happening to everyone who upgrades from 6.06.
Not me... I got a kewl splash screen with the Xubuntu logo. Saying "Xubuntu" on it would be nice, though... This happened when I tried the testing version a month ago or so. I figured they'd have it worked out by now, but noo... It's like that paperclip! It keeps... coming... BACK! ](*,) [/rant]

---

### Post by daFoos on 2006-10-29
so how can I make *some* version of ubuntu usable or at least have access to the files on that partition (not just command-line either).

---

### Post by victor_c26 on 2006-10-29
> **daFoos said:**
> well that's sorta comforting I guess...

so what do you mean start over from scratch?  Where do I put 6.10 on my hard drive and will it still be able to access my Dapper partition? 

thanx for you quick reply.

Meaning Reformat and install edgy eft. That's the only way to install edgy without encountering massive problems.

---

### Post by daFoos on 2006-10-29
what do you mean by reformatting and what does it do?

---

### Post by victor_c26 on 2006-10-29
Erasing everything, and installing the OS again as if you were installing the OS for the first time on that hard drive.

Basically loading the install disc, and telling it to erase everything to continue with the installation.

---

### Post by Aikon- on 2006-10-29
> **daFoos said:**
> what do you mean by reformatting and what does it do?

Reformatting means (essentially, in this context anyway) to 're-partition' your hard drive. You will lose **all data** stored on that drive. Then, to Ubuntu, this will look like a fresh drive with nothing on it and you can set up the new partition table the way you want it.

---

### Post by DJ Wings on 2006-10-29
Note that "You will lose **all your data**" part. Back everything up. If you don't have a USB drive, now's the time to get one. An iPod'll work fine.

---

### Post by daFoos on 2006-10-29
is there any way to access my Kubuntu partition from Windows?

I have a dual-boot going and am currently in Windows.

---

### Post by DJ Wings on 2006-10-29
If you're using ext2 or 3, use [Explore2fs](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm), which is somewhat easy to use, but annoyingly slow. Otherwise, can't help you there.

---

### Post by daFoos on 2006-10-29
I do have a USB drive, but how would I back things up on it (if I can NOT access the partition in Windows) when I can only access the command line in Kubuntu?

---

### Post by DJ Wings on 2006-10-29
Mount it with "sudo mount -o rw -t vfat /dev/sda1 /media/sda1" (might be a bit different for you). Then, save stuff to /dev/sda1 with "sudo cp -r {directory to save} /media/sda1".

---

### Post by daFoos on 2006-10-29
alright, thank you very much for your help!  that application works very well and it seems this incident will be no more than an annoyance until I can devote time to re-formatting my hard drive (maybe when I upgrade to Vista?).

One last question- how DO you reformat your hard drive?  Do you have to Boot n Nuke first?

---

### Post by DJ Wings on 2006-10-29
No, you can just use the Partition Manager to wipe it. Delete your Linux partition and make a new one from the free space. You can leave your swap alone if you have any.

---

### Post by daFoos on 2006-10-29
Follow-up to last question :D : so I could leave my windows partition unharmed then?

---

### Post by DJ Wings on 2006-10-29
Of course. This is a Linux problem. Linux and Windows are separated at as low a level as possible, so that even if you completely ruin your Linux system, only a GRUB failure can knock out Windows. And vice-versa (of course).

---

### Post by daFoos on 2006-10-29
ok, thank you for your help very much.

Hopefully I'll have time to resolve the problem by the end of the week.

:biggrin:

---

### Post by DJ Wings on 2006-10-29
No problem at all (hopefully not for your system, either). I'm glad to help someone who needs it.

---

