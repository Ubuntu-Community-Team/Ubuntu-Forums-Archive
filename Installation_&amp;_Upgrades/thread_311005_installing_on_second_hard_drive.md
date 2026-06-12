---
title: "installing on second hard drive"
date: 2006-12-02
forum: Installation &amp; Upgrades
---

### Post by STREETURCHINE on 2006-12-02
i have a second hard drive that is currantly set up with dapper 6.06 as a slave,now i would like to change this and run a nother linux os ,
so do i have to unmount it ,
when i go to load up the outher os do i need to unplug my master hdd.
answers to these and anything else that may be relevant would be appreciated thanks.:-k :-k

---

### Post by bulldog on 2006-12-02
Everything you want to know you can find here,

[http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by STREETURCHINE on 2006-12-03
not quite everything it does not tell me how to unmount the second hard driveand i am a complete noob so it is not simplified enough for me to atempt without a more detailed how to.so i guess it will not get done.but thanks for your reply..

---

### Post by bulldog on 2006-12-03
You want to replace your ubuntu for another OS is that correct?

If you want to resize or repartition or what ever,download the Gparted live cd [25MB].
Burn it to a cd-r and boot from it.
Now you can change what ever you want to your hard drives.[be carefull and read well before applying anything]

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by STREETURCHINE on 2006-12-03
here is my senario,on hda1 200 gig i have dapper 6.o6 .
loaded as a slave for hda1 is my second hdd, 80gig hdb1
 now i wish to detach hdb1 from hda1 and load breezy or edgy on to it,
but i have tried to do this by diconnecting the primary hdd but hdb1 wont run on its own(i cant get it to read the install disc for breezy).
so i figure i have to unmount hdb1,but i am having trouble doing this,
i may be using the wrong commands i am not very good with them yet,

 when you get to my age learning new stuff takes a bit longer.

so that is what i am trying to do i wish to run dapper 6.o6 on hda1
and lets say breezy on hdb1

---

### Post by bulldog on 2006-12-03
Don't know your age,but I'm 54 years of age :D 

Well basically you don't have to disconnect any hard disk.
Just use gparted live cd and choose the right hdd to partition and format.

Then fire up the install cd and choose when you come to the partition part,manual partition,and mount your already made partitions to / [root] ,swap as swap and maybe /home as /home.

That's all to it,and the install should run fine.

You can run afterwards the ```
sudo update-grub
```command to update GRUB.

---

### Post by STREETURCHINE on 2006-12-03
thanks bulldog i shall give it a try,

i am only 48 but i have only just got my first computor 12 months ago had windows installed but got sick of there crap real quick ,
the tech who built my computer give me a disk with breezy on it ,and i loved it ,
i upgraded to dapper no real problems ,except for no printer.
 so i thought i would put breezy back on one hard drive.

 any way thanks for all your help i will post here if i run into any trouble

---

### Post by STREETURCHINE on 2006-12-04
well bulldog i have edgy 6.10 loaded on second hdd.
i had to unhook the primary drive ,because i was not sure about gparted,so i just took the safe option.
i tried to install breezy but my disk was damaged and would not load,shame i would have liked to put it back on i liked breezy.

i ended up downloading the edgy 6.10 disk (took 2 hours) and installed it this morning.
seems to be working fine,but i am yet to have a play with it yet,so i could break it soon.lol

 so thanks for the help...\\:D/

---

### Post by bulldog on 2006-12-05
If you are looking for java,flash,Opera,multimedia codes and a lot more,you should have a look at automatix2.
This application can install it for you with a minimum input from your side.
I can recommend this.

[http://getautomatix.com/wiki/index.php?title=Installation#Easy_Direct_Installation](http://getautomatix.com/wiki/index.php?title=Installation#Easy_Direct_Installation)

---

