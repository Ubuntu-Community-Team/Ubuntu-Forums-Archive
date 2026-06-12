---
title: "converting to ext4"
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rplantz on 2009-04-04
My current /home partitions (8.10) is ext3. When I install 9.04,

[LIST=1]
[*]Will I get the benefits of ext4 if I make / ext4 and leave /home ext3?

[*]If I convert /home to ext3, I assume that I will have to:
[LIST=a]
[*]save everything on /home to, say, another disk,
[*]reformat /home as ext4 during installation, and
[*]copy the saved /home files back.
[/LIST]Am I understanding things correctly?
[/LIST]

Edit: Thanks to FuturePilot and BGFG for their answers below.

---

### Post by FuturePilot on 2009-04-04
> Will I get the benefits of ext4 if I make / ext4 and leave /home ext3?
You will get the benefits of having / as Ext4 which means faster boot time, faster loading time of programs and the like. Anything read or written to your /home will not benefit from Ext4.

> If I convert /home to ext3, I assume that I will have to:

   a. save everything on /home to, say, another disk,
   b. reformat /home as ext4 during installation, and
   c. copy the saved /home files back.


No. You can convert Ext3 to Ext4. There's no need to reformat it.

---

### Post by BGFG on 2009-04-05
In this thread, other users helped me with the necessary commands. 

[http://ubuntuforums.org/showthread.php?t=1107027](http://ubuntuforums.org/showthread.php?t=1107027)

A backup is advisable, but I didn't. The entire process took less than 5 minutes.

I did a fresh install with / as ext4 then converted my ext3 /home to ext4

---

