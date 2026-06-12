---
title: "Ubuntu 10.04 duel boot problems"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by pyxylover on 2010-05-14
I have a duel boot hard drive.  Ubuntu is my primary OS and I use Windows XP ( basically only to use my lexmark z22 printer ).

I recently upgraded to Ubuntu 10.04.  After which I had several problems from firefox randomly crashing and a few other minor bugs.  My biggest problem was that after upgrade, my computer wouldn't boot into Windows XP.  Said MBR file was missing.  I burnt an ISO disk of the new upgraded 10.04 thinking I had a bad download, but the disk didn't work either.  After trying that i couldn't get either OS to start up.  So I resorted back to my Ubuntu 9.something install disk.  I reinstalled it and is now at least back on line and everything is working just great....except I still can't boot into windows and I really need to print a few things for work.  

I don't really know where to even start in finding out why Windows won't start.  I have to think the problem is with the Ubuntu or Grub initial boot loader files though.  

I've been using Ubuntu for about 6 months now ( and totally love it and encourage all my friends to try it ) but am still very new to all of this, so I'm sorry I couldn't be a little more clear where I think the problem is.  

I would love some advice on where to start to find the problem.  Once I can find the problem, maybe then it will be easier to find a solution to fix it.

Thanks,
Bradley

---

### Post by darkod on 2010-05-14
Go to the boot info script link in my signature, download it and run it. There are instructions on the page or ask if you get stuck.

Look in the results file towards the top where the partitions with their boot files are listed. If it says you have Grub2 on the XP partition (not the MBR of the disk), then go here for the fix:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You will need to use that fix on your XP partition, for example, /dev/sda1, you need to fix the first partition on disk /dev/sda.

---

### Post by pyxylover on 2010-05-17
OMG that totally worked !  Thank You Thank You Thank You.  
It took me a few minutes after downloading to figure out that you had to open the file with Gedit to read it.  Then a little longer to figure out to change directory to my download directory before running it.  ( Told you I was a total newbie  lol )  But after that I just did what you said and whola.  Now my windows boots again and I can use my printer.  I so wish I could use my printer with linux and get rid of windows all together, but everyone in forums says this model printer just won't run right in linux no matter what I do.  
Thank you again 1,000 times for fixing this for me.
Hope

---

