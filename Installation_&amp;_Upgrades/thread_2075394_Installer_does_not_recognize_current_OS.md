---
title: "Installer does not recognize current OS"
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by CAstudent on 2012-10-23
I recently tried to install lubuntu 12.04 from a live CD onto my computer. My computer has one hard-drive that is already split up into three partitions.  One partition has Windows XP installed on it, a second partition is used for data storage and I want to install lubuntu into the third partition.  However when I boot with the CD in the drive the lubuntu installer tells me that it does not recognize any other operating systems and only gives me the options to "Erase the Disk" or "Something Else."  

I canceled the installation because I figured it would be easier to find the solution first instead of trying to fix something later.  How do I get the lubuntu installer to recognize that I have Windows XP installed on one of my partitions?

---

### Post by aabed91 on 2012-10-23
You should make free partition unallocated or space on the hard disk

---

### Post by Mark Phelps on 2012-10-24
> **CAstudent said:**
> [FONT=Times New Roman][SIZE=2]I recently tried to install lubuntu[/SIZE][/FONT][FONT=Times New Roman][SIZE=2] 12.04 from a live CD onto my computer. My computer has one hard-drive that is already split up into three partitions.  One partition has Windows XP installed on it, a second partition is used for data storage and I want to install lubuntu into the third partition.  
You can't install a Linux OS into a Windows filesystem partition -- if that is what you're trying to do.  You need to have unallocated space and use the installer to format that -- using the "something else" option.

> However when I boot with the CD in the drive the lubuntu installer tells me that it does not recognize any other operating systems and only gives me the options to "Erase the Disk" or "Something Else." 
Installer should have given you the option to create another partition -- unless you already have the limit of 4 on your drive.

Boot using the Ubuntu media, go to the desktop, open a terminal, enter "sudo fdisk -lu" (lowercase L, not a one), and post the results back here -- so we can see what partitions you have on your drive. 

> I canceled the installation because I figured it would be easier to find the solution first instead of trying to fix something later.  
Good move!  Too many folks just charge blindly ahead and then come back crying about the damage they did.

> How do I get the lubuntu installer to recognize that I have Windows XP installed on one of my partitions?
Installer should do that.

---

### Post by offgridguy on 2012-10-24
I have been reading everything i can find in the forum, regarding install and partitions
since i am going to do that in the near future, really appreciate the informative reply from
Mark Phelps.
> 
Boot using the Ubuntu media, go to the desktop, open a terminal, enter  "sudo fdisk -lu" (lowercase L, not a one), and post the results back  here -- so we can see what partitions you have on your drive. 


I just wanted to add here, in case you  are not familiar with using the terminal enter sudo fdisk -lu 
minus the quotation marks, ctrl+alt+ t will bring up the terminal,   but you probably already knew this.
Best regards.

---

### Post by CAstudent on 2012-10-25
I got it to work.  I used the "Something else" option to format the partition I wanted to use, then the install worked fine.

> **offgridguy said:**
> 


I just wanted to add here, in case you  are not familiar with using the terminal enter sudo fdisk -lu 
minus the quotation marks, ctrl+alt+ t will bring up the terminal,   but you probably already knew this.
Best regards.

Actually I did not know that.  This is my first time using Linux.  I have a lot to learn so thanks.

---

### Post by Mark Phelps on 2012-10-26
> **CAstudent said:**
> I got it to work.  I used the "Something else" option to format the partition I wanted to use, then the install worked fine.

Great -- so please use the Thread Tools at the top of your post to mark this thread as SOLVED.

---

