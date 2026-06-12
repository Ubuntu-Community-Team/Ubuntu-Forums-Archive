---
title: "Installing ubuntu 8.10 on HP tx2500z"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by edsc86 on 2008-10-31
I'm having problems trying to install Ubuntu 8.10 in my HP pavilion tx2500z, I think is a problem with my hard drive.
When I try to partition the disk is like it doesn't recognize it (the partition looks empty to the partition manager), but if I mount it I can see the data and the partition manager sees the data but I can't partition the disk.
(sorry I wasn't to clear) but I have some pictures..
hope someone can help me.

[[IMG]http://img444.imageshack.us/img444/3052/dsc00017kz7.th.jpg[/IMG]](http://img444.imageshack.us/my.php?image=dsc00017kz7.jpg)
[[IMG]http://img267.imageshack.us/img267/1943/dsc00015sr8.th.jpg[/IMG]](http://img267.imageshack.us/my.php?image=dsc00015sr8.jpg)
[[IMG]http://img444.imageshack.us/img444/4225/dsc00016ye3.th.jpg[/IMG]](http://img444.imageshack.us/my.php?image=dsc00016ye3.jpg)

---

### Post by gali98 on 2008-10-31
Okay first of all, are you trying to keep windows? If so, then you need to boot into windows first and run chkdsk, otherwise (if you just want to scrap windows) then just reformat your whole disk.
Kory

---

### Post by edsc86 on 2008-11-01
yes I want to keep windows (vista), sorry for the confusion.
run chkdsk I'll try that..

---

### Post by gali98 on 2008-11-01
I also suggest defragging before installing ubuntu
do chdsk first
then defrag.
A great program is jkdefrag. It is open source (I think... I know it's free)
It works better than the windows one, and you can track the progress better.
Kory

---

### Post by edsc86 on 2008-11-01
Ok, so I went to windows and made a partition right there and now I'm installing ubuntu(74%:)) on that new partition I created on Win. I still see the warning on the ntfs partition I guess there is something wrong in that partition and I'll look if I can scan the ntfs partition for errors from ubuntu:confused: can that be done?

---

### Post by gali98 on 2008-11-01
No... I would still suggest fixing the windows partion from windows.
The ntfs driver in ubuntu is good, but it would be better to do it in Windows. I suggest going into Windows and running this command.
First click on the start button (the windows button)
right above that in the menu will be a box you can type in. type "cmd" without quotes in it. Now in the menu a cmd option will pop up. Right click on it and select "run as administrator" (may not be the exact wordage but you get the idea)
now use the command:
chkdsk -f -r -b -v -x


from cmd... this should ask you if you want to do it on the next reboot. Type y for yes and then reboot.
This will take quite a while.
Then download this:
[http://www.kessels.com/JkDefrag/JkDefrag-3.36.zip](http://www.kessels.com/JkDefrag/JkDefrag-3.36.zip)
([http://www.kessels.com/JkDefrag/JkDefrag64-3.36.zip](http://www.kessels.com/JkDefrag/JkDefrag64-3.36.zip) if you have 64bit)
and unzip it. Then run the JKDefrag.exe program inside (or JKDefragscreensaver.exe if you want to watch it fullscreen :)) This will take quite a while as well.
Do all that in windows.... Now boot back into ubuntu and try and open the windows drive...
Kory

---

