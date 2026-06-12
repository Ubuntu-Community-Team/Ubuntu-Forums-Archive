---
title: "unistall ubuntu and grub"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by dan171717 on 2007-05-27
i need to uninstall ubuntu and grub because my ubuntu partion is too small so i need to cut windoze back remove grub and ubuntu then install ubuntu again. when i install ubuntu i was stupid and layed it ould like in the screenhot.


please note that my ubuntu partion is ext3 not ext5 ext5 is a waste of space that i am going to use as virtual machines.

---

### Post by Herman on 2007-05-27
[GParted -- LiveCD]("http://gparted.sourceforge.net/")
If you get yourself a GParted LiveCD you will be able to resize your partitions. That would probably be a lot easier.
Regards, Herman :D

---

### Post by dan171717 on 2007-05-27
i cant move a partion backwards and i need to thats why i need to get rid of ubuntu and put it back on after i have messed with the partons

---

### Post by Herman on 2007-05-28
Hello dan171717,
Okay then, if you don't have very much installed software and you don't mind going through all your adjustments and settings and fine tuning all over again you can just delete Ubuntu and re-install it, resizing that NTFS partition as you re-install to make room for a larger Ubuntu partition beginning further towards the start of the disk. There would be no need to worry about doing anything with Grub that way. Your new Ubuntu install will install Grub's IPL again to MBR, so you won't have to worry about a thing. That's one way to do things, but it could possibly be a lot of work getting Ubuntu back to how you like it.

Another way to do things if you are using GParted in the Ubuntu Live CD is to shrink that NTFS partition until you have enough room to copy your Ubuntu partition and paste it further towards the start of your disk. You already have three primary partitions and one externded, so you would need to delete your swap area to make that possible. That would allow you new copy of Ubuntu to take the partition number of 4. Then after you delete your old Ubuntu you can make a new swap area, so it will be number 3. You would have to re-install Grub and edit /etc/fstab with the changes to the partition numbering.
Unless of course you delete your swap, copy and paste your Ubuntu partition somewhere in the middle first, then delete the old one, then copy it a second time and paste it where you finally want it. Tehn make a new swap area. That would give you your original partition numbers back again, in which case you wouldn't need to re-install Grub or edit /etc/fstab.

Easiest at quickest of all, you could download yourself a copy of  [GParted -- LiveCD]("http://gparted.sourceforge.net/"), which has had the ability to move Linux partitions around since over a year ago now. That makes the job so much easier! GParted LiveCD is free you know, and only a 45 MB download I think. Really, I mean -why do things the hard way when there is an easy way?

But it's up to you. Do whatever you think will make you happiest. I have to admit something now, I actually don't mind re-installing and setting everything up again from scratch too much myself, actually I kind of enjoy it. It's kind of fun.  If you like doing things that way maybe you'll like a link to my [Back Up and Restore]("http://users.bigpond.net.au/hermanzone/p13.htm") page then . so you can save all your email, calendar, memos, tasks and addressbook from evolution, and transplant them into your new install. Firefox bookmarks too. That link explains all that. Enjoy Ubuntu, whatever you decide to do. :D

Regards, Herman  :D

---

### Post by dan171717 on 2007-05-28
so are you saying i can move an ext3 partion backwards cos if i can then that would be heaven.

i will get the gparted livecd.

thanks

---

### Post by dan171717 on 2007-05-28
i got the gparted cd and i put it in mylaptop. it came up with grub stage 2 and a comand line. i dont know what to do here. to test the cd i put it in  my old computer and it worked fine. how do i load gparted  on mylaptop


p.s. my old computer has win98 and no linux (yet!!)

---

### Post by dan171717 on 2007-05-28
i will probbly back up a bit more and do the first option. i dont have mutch to dowload toget it back. say 150mb (that includes kde core buti dont use it mutch)

---

### Post by Herman on 2007-05-28
Hello dan171717,
I'm sorry GParted LiveCD didn't boot in the computer you need to use it in. I don't know why, but yes, GParted LiveCD is great, it can move Linux partitions and resize them from the start of the partition very nicely. It is very convenient since that should be what most people would want to do, the same as you.
Well I guess re-installing will be okay then, it probably won't take you very long. One of the things I like best about Ubuntu is that it is so easy to make a good backup from it and restore it again, including all my emails and everything. Ubuntu is really great for that. 

As you might see, that link I gave you earlier begins explaining how to back up for beginners (using GUI) and progresses to intermediate skill level where you use a script to make your backups and restore instantly. 
Don't forget you need to start evolution in your new system and configure it before you'll be able to restore it from the backup.

I would make a good backup on another media first, then leave my old partition there for now and install a new one in front of it. You can mount the old partition in your new install (if it doesn't already do that automatically for you), and transfer everything directly from your old partition right into your new one. I would leave the old system there for a few days in case there is anything more I forgot to transfer before deleting it and resizing the new partition to fill the disk.  Gparted from the Ubuntu LiveCD can do that okay.

---

### Post by dan171717 on 2007-05-28
hello.

i just installed feisy

i did the first option. i put all my docs on a cd and have little apps so am happy. like u said grub works but slightly differently (i know how to edit it)

---

