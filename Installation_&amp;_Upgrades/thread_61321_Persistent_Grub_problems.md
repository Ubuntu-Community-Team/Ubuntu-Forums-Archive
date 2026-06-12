---
title: "Persistent Grub problems"
date: 2005-08-31
forum: Installation &amp; Upgrades
---

### Post by j.hill on 2005-08-31
I'm trying to restore/reinstall Grub.  I know there are several threads on the topic, but they're either too technical for my n00b mind or their methods haven't worked for me, or both.  Moreover, people seem to have stopped looking at the older threads.  So I'm starting a new thread.

The situation:  Grub lets me boot into Ubuntu, but not into Windows, in which case I get Error 11 (unrecognized device string).  Playing with menu.lst has not helped, so someone has suggested that I reinstall Grub.

So far I have tried restoring Grub from the Live CD (typing "grub" in a terminal produced an error message) and reinstalling Grub with apt-get (looked like it was working, but I still can't boot into Windows).

The GNU Grub manual advises against apt-get (I was feeling lucky) and recommends a procedure that involves a floppy disk (unfortunately, I lack a floppy disk drive).

On another thread I saw this procedure:

> 1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
.....

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer
I haven't tried this yet, but it seems like my last hope.  My questions, for any n00b-savers out there:

1.  Is this procedure really going to reinstall only Grub, and not erase my whole setup?

2.  If I used the "expert" install the first time around, and told it to partition on the "desktop" scheme (instead of using one big partition), do I need to do that again (or, since it's not really repartitioning, does it not matter)?

3.  Aren't the partitions
/
/home
/swap

and not 
/
/boot  
/swap  

as the procedure above suggests?

4.  What's the worst thing that can result from following this procedure?

Thanks for your help, whoever you are....

---

### Post by frodon on 2005-08-31
I used this method without any problem when i reinstalled windows on my computer. So i confirm this method works and is not too hard to follow.

---

### Post by j.hill on 2005-08-31
This is good to know.  Here are some questions, though, about this partitioning business:

1.  I have the option to "initialize the partition table" for my disk.  Is this what I want to do?

2.  If so, what type of partition table do I want?  "MSDOS" is highlighted, but somehow that doesn't look right to me.  :)  The full list of options is:

bsd
gpt
,ac
dvh
msdos
pc98
s390
sun
amiga
loop

What else do I need to know about the partitioning, since that seems to be the crucial step in this process?  the original procedure talks about mounting partitions, and the installer says I can edit mount points, but I can't even see where the mount points are, much less how to edit them.

---

### Post by frodon on 2005-09-01
You must write somewhere the name of the partitions which contain your /home and your /swap (hda1 and hda3 for me), then in the partitioning step make the partitions for ubuntu, put hda1 (in my case) for /home and hda3 (again in my case) for /swap just don't choose to format these partitions (when you choose to format a partition there's a small logo which represent a head of death). Then save the change and don't take care of the errors, then follow the next steps of the HOWTO.

It's all i can remember. I hope it will solve your problem, in my case i reinstalled the GRUB because when you install windows after linux your GRUB is overwritten by windows and the computer boot only with windows, but in your case you have the invert problem however i think reinstalling GRUB will solve the problem.

good luck  ;-)

---

### Post by j.hill on 2005-09-01
It didn't work.  I'm starting to feel desperate.  Nothing's changed.  I'm getting exactly the same error message I got before.  What is going on here?  What other options do I have for fixing it?  Why does this method work for everyone except me?

EDIT:  What about the "rootnoverify" command?  Someone else, in a different thread, suggested using this to allow Grub to boot Windows.  Might that work here?

---

### Post by banjo04414 on 2005-09-01
OK try this. Insert the Ubuntu disk in your drive and boot up. You will come to the boot "prompt". Type in "rescue" without the ". It will then give you access to a prompt at the bottom of the screen. Chroot into the drive your Ubuntu is in. "Chroot /dev/xxx".Then type "dir". It should show your tree. "cd boot", "cd grub" "more menu.lst" or "gedit menu.lst". This puts you into the boot.conf of Grub. Check it to see if the following is there.
title       Microsoft Windows XP Professional
root       (hdo,o)
savedefault
makeactive
chainloader +1

 It should be under "Other Systems"
 The Winxp Pro is what I have, just put in which Windows name you have. Save it. Then either "Grub update" or Grub install /dev/hd0,0. The second command I'm not sure of but it is in the HowTo's file under Grub. Hope this helps and works for you.

---

### Post by j.hill on 2005-09-01
Is this the Live CD or the Install CD?

---

### Post by banjo04414 on 2005-09-01
Install cd.

---

