---
title: "Anyone any good with Clonezilla? Basic question pls!"
date: 2012-12-29
forum: Installation &amp; Upgrades
---

### Post by listerdl on 2012-12-29
Thanks for reading this. 

If I have made a copy of my linux box - am I able to simply re-install the entire image on just a blank ex4 partitioned drive? Simple as that? 

I am asking because from a windows enviornment you have to install Windows before you can install a previous image - thanks for all help.

Id try but I dont have a spare hard drive to test this on....

So, again, all I need is a clean ext4 hard drive and then magically clonezilla will clone the image?

Thanks!!!

---

### Post by VinDSL on 2012-12-29
It's almost that simple...  :)

I explained how to do it over here:

[INDENT][http://forums.anandtech.com/showthread.php?t=239309](http://forums.anandtech.com/showthread.php?t=239309)[/INDENT]

Might want to check it out.

---

### Post by ibjsb4 on 2012-12-29
Your clone will have the same uuid as the original and needs to be changed if you intend to keep the second hdd on line.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=change+uuid&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=change+uuid&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by listerdl on 2012-12-29
thanks everyone - i guess best thing to do is just try! Ill test with a 2.5 HDD that i will liberate from an old machine.

---

### Post by haqking on 2012-12-29
> **listerdl said:**
> Thanks for reading this. 

If I have made a copy of my linux box - am I able to simply re-install the entire image on just a blank ex4 partitioned drive? Simple as that? 

I am asking because from a windows enviornment you have to install Windows before you can install a previous image - thanks for all help.

Id try but I dont have a spare hard drive to test this on....

So, again, all I need is a clean ext4 hard drive and then magically clonezilla will clone the image?

Thanks!!!

YES.

And on a windows system you dont need to reinstall windows at all.

You can take a clone of any OS  you like and restore it from a Live CD/USB

it wont do anything magically though, it will require you to make the right choices and read the drives properly, also the destination needs to be the same size or larger than the source obviously

---

### Post by listerdl on 2013-01-01
> **ibjsb4 said:**
> Your clone will have the same uuid as the original and needs to be changed if you intend to keep the second hdd on line.

OK thanks - very helpful advice.

But - what would happen if I did have the same UUID twice? Would that cause problems with updating repos or PPA's or things like that?

I did have a look at Google/ Wikipedia (kinda briefly) and it seems that the answer is "no".

["Linux now prefers to use UUID (Universally Unique Identifier), LABEL, or symlinks to identify media storage devices on a system."]("https://help.ubuntu.com/community/UsingUUID")

So I guess the answer is that having two identical UUID wouldnt actually really be an issue or am I wrong?

---

### Post by ibjsb4 on 2013-01-01
> **listerdl said:**
> So I guess the answer is that having two identical UUID wouldnt actually really be an issue or am I wrong?

Wrong  :)  Your system will try to access both.  You can try it and you will see what I mean, just don't make any changes.

---

