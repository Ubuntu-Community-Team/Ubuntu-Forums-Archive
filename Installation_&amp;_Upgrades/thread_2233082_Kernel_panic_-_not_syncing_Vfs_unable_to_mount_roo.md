---
title: "Kernel panic - not syncing: Vfs unable to mount root Ubuntu 12.04LTS"
date: 2014-07-06
forum: Installation &amp; Upgrades
---

### Post by Suparno on 2014-07-06
[SIZE=3][FONT=microsoft sans serif][COLOR=#333333]Hi everyone,

I know this question has been asked a lot of times in this forum but i didn't find any particularly suited to my situation yet (if there are feel free to redirect me to them). I am using Ubuntu 12.04 for quite some time now and it's the only OS I have. It was quite stable and never gave me any serious problems. Recently i updated my R (CRAN) version, and after that I was show a message that there might be some inconsistencies with the grub file, I couldn't make out what it meant and ignored it.[/COLOR]
[COLOR=#333333]The next time I restarted it failed to boot and showed me this [http://i61.tinypic.com/nnkvpf.jpg](http://i61.tinypic.com/nnkvpf.jpg)

[/COLOR]
[COLOR=#333333]I tried in the safe mode from the grub menu as well its still showing me this message [http://i57.tinypic.com/5k55x1.jpg](http://i57.tinypic.com/5k55x1.jpg)

[/COLOR]
Now my first priority is to recover the data from the drives ( i have read it can be done by live usb/cd but not sure how ? ) and second to get it back to the previous state if possible. This kernel panic has surely got me panicking !! The computer had a lot of my thesis work and it will be great if someone can help me out here.




Thanks,


Suparno


PS:- My grub menu looks like this [http://i60.tinypic.com/2m4ahds.jpg](http://i60.tinypic.com/2m4ahds.jpg)[/FONT][/SIZE]

---

### Post by Bashing-om on 2014-07-07
Suparno; Hi ! My Welcome to the forum.

Recovering your files should not be a big deal if required. 
Boot the liveDVD and activate ubuntu's file manager 'nautilus' ( the folder icon in the launcher ) - with a USB thumb drive plugged in - . On the left side pane of 'nautilus' are all the file systems that the system is aware of. Open another instance of a window in 'nautilus' and open it on the usb drive. Drag and drop the files you want to copy between the windows.

Fixing the present install ...
Well, I am not familiar with the application 'R' (CRAN). What is it, where did you get it and how did you install it ?
Let's get an idea of what condition the install is in, as you are unable to boot to the GUI, let's see what results when booting the install to a text terminal.
Boot your install to that Grub boot menu, here press the 'e' key for edit mode -> boot parameters screen; Arrow down and across to the terms "quiet splash" and replace them with the term "text" -with out the quotes- ( this line similar: root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff ); key combo ctl+x to continue the boot process to that text terminal (TTY1). Here enter your username and password ( when entering the password there is no response to the screen, security reasons).

If you can boot to the text terminal we will proceed in one direction, else will do something else. We will find out what condition the system is in, one way or another.
Once known what the problem is it becomes fixable,

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Suparno on 2014-07-08
Sorry for the bit late reply. I ran into a different problem related to recovering the data using a usb/drive. Which in short is a problem i am facing because my previous OS was on a hard disk which was part of RAID i presume. I created a separate thread because i thought it's a bit unrelated to this problem but you can have look [http://ubuntuforums.org/showthread.php?t=2233252](http://ubuntuforums.org/showthread.php?t=2233252). If you can help with that as well then great :) . In any case i will continue with what you suggested and let you know what happens.

---

### Post by Suparno on 2014-07-08
Okay just tried that . Didn't work :( 

Showed the same error kernel panick - not syncing unable to mount root. I can post a screenshot as well if needed.

---

### Post by Bashing-om on 2014-07-08
Suparno; Hello,

If you can not boot that "known" good liveDVD(USB) - Or I am not understanding the situation - .. then there is a problem at the hardware level and/or bios.

IF you can boot the liveDVD and not able to mount the partitions on the hard drive, then we are looking at file system errors - and we will see what ubuntu's file system check utility reveals.

Raid will complicate things, and if raid is no longer being used, should be removed ( server tools to do that). I go check the raid thread see what that status is.
-----------------------
EDIT: Raid is being used, and is the HUGE factor:
I have looked at your raid thread, and it appears to me the better course of action here is to reassemble that raid array. Now that my friend is above my skill set. All my aboves no longer apply as The attempt will be to reassemble the raid array.


[INDENT][INDENT]it's all a process ->
[INDENT][INDENT][INDENT]one step at a time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

