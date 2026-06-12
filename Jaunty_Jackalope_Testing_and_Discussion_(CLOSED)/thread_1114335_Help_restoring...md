---
title: "Help restoring.."
date: 2009-04-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Aflack on 2009-04-02
I have linux mint, but it install no differently so i'm just goingg to post here since I like this community it's more active and kind. 

So i have windows vista, 7, and Linux Mint. It's 4 partitions... using GRUB. 

I want to erase linux mint and just have 7 and vista on the vista bootloader. How do i go about doing such akshunz?

---

### Post by Aflack on 2009-04-02
aw come on man.

---

### Post by coffeeaddict22 on 2009-04-02
For sticky Mint, I find putting the offending object through the washing machine usually does the trick...
You're probably asking in the wrong place.  We're all trying to make Linux work.  If you want to make a different OS work, I'd suggest their friendly forums.

---

### Post by Aflack on 2009-04-03
Windows Forums lol?

---

### Post by nystire on 2009-04-04
You could try booting off the Windows 7 install DVD and telling it to rebuild the boot sector. I'm not sure if it will see your Vista install and add that to it's boot menu, however. Basically: Good luck, you're on your own for this one, I'm afraid. :)

---

### Post by coffeeaddict22 on 2009-04-05
OK, the honest answer:
The Windows and Linux partitioners don't talk nicely to each other.  I'm not a guru, but in my rather frustrating experience if you want to create a partition for another OS of any sort, boot into the OS you're going to remove/ shrink partitions from.  For Vista, there's a partitioner built in- but you only find it by using the help or search menus.  For Linux, it's usually in your system folder, but you may need to install gparted to get it.  For XP, I'm not sure, but I think you're looking at an outlay of about 50- 100 dollars for something that will change the partitions on your hard drive without trashing all the data on it.  Haven't used 7, although it'd surprise me if the owners have omitted another chance to make money off you...

If you're deleting Linux, there's a few million people on this forum who think you need help of a sort we can't offer.  As a rule, if a PC is part of the question, Linux is the best answer.  However, if you disagree, run gparted and delete all the partitions you don't want.  Don't replace them (leave the disc space empty), reboot and you're away.  Although the first thing you may want to do is open the partitioner of the OS you're keeping and expand it's partition(s) into the empty space you just created.

---

