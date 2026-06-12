---
title: "Error Booting after Today's Update"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by WriYeDannii on 2009-12-06
So I installed the Updates today through the update manager as normal, when prompted to restart I did so.
Now whenever I try to load Ubuntu i get the following menu
 
'GNUGRUB version 1.97~beta4
minimal BASH-like line editing is supported. For the first word, TAB lists possible commands completions. Anywhere else TAB lists possible device/file completions.'
 
Any help would be appreciated as I have no idea what to do from here to get it to load into Ubuntu.
 
Thanks

---

### Post by darkod on 2009-12-06
Did you install ubuntu or wubi with wubi.exe?

---

### Post by WriYeDannii on 2009-12-06
I did it through the windows installer onto a seperate hhd. Vista is on c: Ubuntu on d:

---

### Post by darkod on 2009-12-06
First of all, instead of the [ubuntu] mark for the thread you should have used [wubi], it's in the options too. It makes a difference.

Look at post number #10 here:
[http://ubuntuforums.org/showthread.php?t=1339203](http://ubuntuforums.org/showthread.php?t=1339203)

That will help you. If you are sure ubuntu is on another hdd and not just another partition on the same hdd, in the instructions instead of /dev/sda1 use /dev/sdb1 (that means first partition on second drive). If it doesn't work, try other values depending where you have wubi installed.
I hope it can help you.

---

### Post by WriYeDannii on 2009-12-06
Sorry.
Okay will try that Thanks

---

### Post by darkod on 2009-12-06
> **WriYeDannii said:**
> Sorry.
Okay will try that Thanks

No problem, common mistake. But for example if I knew it was wubi I wouldn't have to ask you the question first. :) I hope the instructions will get you going.

---

### Post by WriYeDannii on 2009-12-06
I tried the #10 on that thread to no solution. havign changed the Dev/sda1 to sdb1 i went up to sdb5 and still nothing. It keeps telling me that the file is not found.
Any other ideas?
Thanks for your help

---

### Post by darkod on 2009-12-06
Are you sure it's on another PHYSICAL drive? The letter D: doesn't mean another hdd. You said it's on another hdd.

In windows open Disk Management (windows button + R, type diskmgmt.msc, hit Enter) and see where D: is. If you can boot into windows.

---

### Post by WriYeDannii on 2009-12-06
On disk management I get
Disk 0 which gives me acer c: and Data d: along the same line.
I take this means they are both on the same disk, so are partitions?
If so then sorry my mistake..again. Not so good with computers at the moment

---

### Post by darkod on 2009-12-06
Ok, then use /dev/sda2 (second partition on first hdd). That should work.

---

### Post by WriYeDannii on 2009-12-06
Just tried dev/sda2 and sda3 but neither worked. is the following code the right one?
set root=(loop0)
Linux /boot/umlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
 
When i get to here it tells me the file is not found.

---

### Post by darkod on 2009-12-06
> **WriYeDannii said:**
> Just tried dev/sda2 and sda3 but neither worked. is the following code the right one?
set root=(loop0)
Linux /boot/umlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
 
When i get to here it tells me the file is not found.

Well that's what the instructions say. I am not using wubi myself. Go into windows and check whether on D: you have the ubuntu/disks/root.disk file.
Also if ubuntu/boot/umlinuz-2.6.31-14 file is there, depending which file is missing. Maybe you need to use 2.6.31-15 or similar, depending which files are there.
Not exactly sure where they should be since I'm not using wubi, look around on D: in ubuntu folder if there is boot folder, etc. When you find the files remember the path and adjust the command as needed.
The /dev/sda2 should be definitely correct because D: is your second partition on Disk0.

PS. The FILE NAME is vmlinuz, not umlinuz. Which did you try?

---

### Post by WriYeDannii on 2009-12-06
I've just checked the D partition and I have the ubuntu/disks/root.disk but without the 'ro' on the end.
I don't have anything inside the boot folder except an empty folder called grub.

---

### Post by darkod on 2009-12-06
I also noticed error in the code you wrote. It's not umlinuz, should be vmlinuz. What did you use?

---

### Post by WriYeDannii on 2009-12-06
I think i used Um so i will try it with Vm
 
Tried doing this and it worked. Then i got a screen that said 
'ALERT! /host/ubuntu/disk/root disk does not exist. dropping to shell!
busybox v1.13.3(ubuntu 1.1.13.3-1ubuntu7) built-in shell(ash)
enter help for a list of built-in commands
(initramfs)
 
any ideas?

---

### Post by WriYeDannii on 2009-12-06
Bump. Please help.

---

### Post by darkod on 2009-12-06
root disk or root.disk? Be very careful with typing because I don't know what is what. If you typed root disk in your commands it should be with '.' Just type the commands exactly as they are in the link I provided, and use /dev/sda2.

---

### Post by WriYeDannii on 2009-12-06
root.disk is what i used and also what came up as not existing.
No idea what to do next.

---

### Post by darkod on 2009-12-06
Sorry, me too. :(

---

### Post by phillw on 2009-12-06
I don't know if this posting can help - I had a go with it last nite - and they have a couple of other suggestions - it also has a link to page7 of another thread which is also current

[http://ubuntuforums.org/showthread.php?t=1339203](http://ubuntuforums.org/showthread.php?t=1339203)

Phill.

---

### Post by WriYeDannii on 2009-12-06
I have tried all of the advice on your link to no solution. Any ideas?

---

### Post by WriYeDannii on 2009-12-06
Bump. Anyone have any other ideas?

---

