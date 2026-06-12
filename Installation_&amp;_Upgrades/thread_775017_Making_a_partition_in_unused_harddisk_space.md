---
title: "Making a partition in unused harddisk space"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by hitspace on 2008-04-29
Hello out there . Ive had ubuntu for a while now i had it installed on the sole partition on my pc. Now i need a dual boot with windows but i have a dilemma i have some files i can not move or back up so i was wondering , is it possible to form a partition on ubuntu using a block of unused hard drive space without reformatting and losing any files on my harddrive  ? If so is there anyway i could force all the files in my harddrive into a single block so i could use the rest of it ? I really appreciate any help anyone can give me . Thanks

---

### Post by mikewhatever on 2008-04-29
I don't think what you want is possible, but you can either resize one of the existing partitions to make space for Windows or install it in a virtual machine.

---

### Post by Rallg on 2008-04-29
I am not sure what you mean when you say that you cannot move files. If you cannot make a backup, that is also a problem.

But if you wish to take the risk, you can use GParted to move and re-size partitions. I do it using the "System Rescue CD" which is a form of live Linux. Maybe you can do it from Ubuntu live, too, but the advantage to System Rescue CD is that you won't confuse it with anything else.

My understanding (such as it is) is that when you re-size a partition to something smaller, the paritioner moves the files "closer together." However, beware of moving the starting position of any bootable partition. Depending on how you boot, the loader can get lost if it looks for the wrong start point on the hard drive. In particular, once you install Windows, I advise you not to move the start point of its partition. Apparently the Windows registration code validation is unhappy if you do that.

---

### Post by hitspace on 2008-04-29
Well you see I "could" make a back up but i have no storage device that can hold 20 gigs of video files .... Unless on a side note does anybody know if i can compress video files to with a good compression ratio say in this case by half ? 

Anyway i used windows for a long time i was pretty good at it . I remember the disk defragger and i remember how it lets you bring all the files into a single block of used space on your hard disk . Is there something that will do something like that except a bit more extreme ? So that i can use that unused space and partition it ?

---

### Post by xzero1 on 2008-04-29
You video files are already compressed. You could transcode them to another possibly more efficient format probably h.264 but the playback requirements are higher for this format. You could also sacrifice quality and save more space. How much space you gain depends on the current format of your files.

---

### Post by hitspace on 2008-04-29
Well are there any programs that let you see how your files are organized in your harddrive . I mean if there was a chance that my files were organized in that manner couldnt i essentially partion it ?

hitspace

---

### Post by xzero1 on 2008-04-30
> Well are there any programs that let you see how your files are organized in your harddrive . I mean if there was a chance that my files were organized in that manner couldnt i essentially partion it ?
Sorry, I don't understand the question.

---

