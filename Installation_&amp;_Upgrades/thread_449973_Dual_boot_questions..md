---
title: "Dual boot questions."
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by Maniac Matt on 2007-05-20
Okay, so i am fairly new to linux, and i would like to dual boot with windows xp. Im not sure if i am going to use feisty, or dapper yet. 

1) what is the best way to install a dual boot?...... Manualy? (and if manualy, how do i go about that?) Or can I just use the "resize the partion hda1 and use freed space". If I choose the "resize and use freed space" option can i share files with windows?

2) how do you share files betweem Linux and Windows? (I think i read somewhere you need a Fat32 partition, and if that is so, do i have to edit that manualy, or can i choose an option that creates a Fat32 partion for me?)

3) lastly are there any good Howtos for dual booting Kubuntu and Windows?

---

### Post by merlinus on 2007-05-20
> **Maniac Matt said:**
> Okay, so i am fairly new to linux, and i would like to dual boot with windows xp. Im not sure if i am going to use feisty, or dapper yet. 

1) what is the best way to install a dual boot?...... Manualy? (and if manualy, how do i go about that?) Or can I just use the "resize the partion hda1 and use freed space". If I choose the "resize and use freed space" option can i share files with windows?

Be sure to defrag your windows partition before trying to resize it.  The live cd will then create the two needed Ubuntu partitions from the freed space, / and /swap.  You probably will also want to create a /home partition as well.
> 
2) how do you share files betweem Linux and Windows? (I think i read somewhere you need a Fat32 partition, and if that is so, do i have to edit that manualy, or can i choose an option that creates a Fat32 partion for me?)

I use ntfs-3g to read and write from NTFS partitions, and ext2ifs to read and write to ext3 partitions from windows, all with no problems.
> 
3) lastly are there any good Howtos for dual booting Kubuntu and Windows?

You might check some of the Ubuntu resource websites such as [http://www.ubuntu.com/support](http://www.ubuntu.com/support)

Good luck!

-merlin

---

### Post by Noahsconundrum on 2007-05-20
I just downloaded edgy 6.06 LTS and burned the iso 

Restart

Boot from cd ISO 

open terminal, type sudo gparted

resize my Windows NTFS partitions down leaving about 1/2 the free space available

then reboot  from cd ISO. install on the free space thereby PRESERVING your windows stuff.

Cheers

---

### Post by Maniac Matt on 2007-05-20
> **merlinus said:**
> Be sure to defrag your windows partition before trying to resize it.  The live cd will then create the two needed Ubuntu partitions from the freed space, / and /swap.  You probably will also want to create a /home partition as well.


I use ntfs-3g to read and write from NTFS partitions, and ext2ifs to read and write to ext3 partitions from windows, all with no problems.


You might check some of the Ubuntu resource websites such as [http://www.ubuntu.com/support](http://www.ubuntu.com/support)

Good luck!

-merlin



I am pretty new to this so i am sorry to say i don't know exactly what you mean.. How do i defrag windows? and when you say ntfs-3g and such, i dont know what you mean. sorry i am a newb.



and to Noahsconundrum, If i follow your instructions, how do i share files between Windows and Linux?



sorry for the trouble...i am so bad at this.. :( 

thank you- matthew

---

### Post by merlinus on 2007-05-20
Look for help in windows about defragmenting drives.  In Win2000, if you open My Computer, right-click c: and go to properties, you will see a tab for tools, and defrag is one of them.  Don't know about XP.

ntfs-3g is a driver available once you install Ubuntu in Applications/Add-Remove that allows linux to read and write to NTFS-formatted partitions.

ext2if is a driver that can be downloaded from their website that will allow windows to read and write to ext3-formatted partitions, which is what is generally used in linux.

-merlin

---

### Post by jerrylamos on 2007-05-20
It's not that you're bad at it, it's just that Windows is so bad about allocating files in their partitions, using the "scatter" algorithm.

I don't have XP up at the moment, but from memory, push the little windows key on the keyboard, select Programs, Select Accessories, select System, and look for defrag.  It's pretty slow.  When it eventually finishes it is supposed to re-organize the files and gather them together however it is not good at leaving nice space at the top.  Push Details and try to estimate if the free space at the top is enough for Linux & Swap.  Swap can be 512 MB plus a Linux partition might be 8 GB.  I usually use between 4 GB and 20 GB.

Now it may happen that there is a big blop of a file high in the partition as seen on Defrag Details.  If it is in the way, it is likely to be XP's paging space.  You can do Settings, System, ... Virtual Storage ... and make the paging space 0.  Remember to restore it after doing the Linux resize.

Now on Linux Install I always do Manual Partitioning, and try resize moving the high end of the XP partition toward the left, a little less than the free space you estimated from Defrag Details.  Then you can create a 512 MB swap partition and a partition for Linux, format ext3, mount point /
Install will give you a couple chances to see that things are as you might expect.  For install to complete correctly, it will have to format the swap and the / partition but no other partitions.

You might want to get the book "The Official Ubuntu Book" from your friendly bookseller or Amazon.

Do note Dapper 6.06 and Edgy 6.10 have been out a while and are less likely to have bugs than Feisty 7.04 which has a bunch of new function which is still in debug.

Cheers, Jerry

---

### Post by Maniac Matt on 2007-05-20
Thank you merlin. I really appreciate it. 

Now to Jerry, I would also like to thank you. And i would also like to mention, that I am doing this on a new hard drive, so i dont think i will need to defrag windows. I also stumbled upon this HOWTO.  [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/) and i think i will give it a shot. 

The one thing i don't quite understand is how you can share files. Lets say i make a Fat32 partition, and i want to be able to share music between Windows, and Kubuntu... meaning i would like to be able to access it on both OS's, How would i do that? Could I save the music to the Fat32 Partition? and then somhow be able to access it?

thank you again. 

-Matthew

---

