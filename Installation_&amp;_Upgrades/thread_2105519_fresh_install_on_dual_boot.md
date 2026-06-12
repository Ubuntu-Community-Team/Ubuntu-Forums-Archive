---
title: "fresh install on dual boot"
date: 2013-01-16
forum: Installation &amp; Upgrades
---

### Post by dbcityl on 2013-01-16
hi there,

recently, precise won't let me install, uninstall or upgrade without error messages.(more info[ [COLOR=DarkOrange]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2104618"), if needed)
I'd like to freshly install 12.04 over existing precise. ( I backed up all I needed in precise)
It's a dell lattitude 5520m Dual boot running win7 as well. It's not a wubi version.

I'd like to be more certain win7 stays operative the way it is. Hate it, but
need it for some programs and they are running well in current config

I've searched the forum and online, but still have some questions, as i've lost some confidence in 'just trying' since the mess I got into.

1. can I just perform a clean install on 12.04? or do I need gparted ?
2. what info do I need to get this done? partition size or are they named in a certain way?

Just want to get this right as I don't have a confident idea on what I'm doing,
in case things don't work out as expected.

thanx for your time&help

---

### Post by zvacet on 2013-01-16
Yes,you can do fresh install of 12.04 Precise.You will not need gparted if you decide to install on partition on witch is your previous ubuntu install.Of course you will have to mark partition as /root and format it as ext4.If this is not complete answer,just ask want do you want to know.

---

### Post by irv on 2013-01-16
Maybe it would help to watch this video where you can chose to install over the top of the 12.04 you already have installed.
[http://www.youtube.com/watch?v=ba9Wv-XU_4M]("http://www.youtube.com/watch?v=ba9Wv-XU_4M")

---

### Post by dbcityl on 2013-01-16
@ irv: thanx for the video-link. It's exactly what I was missing in terms of "confidence"
very helpfull indeed! 

@ zvacet: thanx for that info. I will look for the 135 GB Ubuntu partition i'm using currently . If I delete it, there will be 135 GB free space. I'll add that as a new partition, wich I must use as "Ext4 journaling system"
But then, how do I "mark it as /root". In the [video]("http://www.youtube.com/watch?v=ba9Wv-XU_4M") (at 1:33) I can see the option for: "mount point" where you can select " /boot" . but that's not the same, i suppose?

---

### Post by dbcityl on 2013-01-16
ok, think it struck me..... If I choose mounting point:  "/" it will be root, right?

---

### Post by irv on 2013-01-16
> **dbcityl said:**
> ok, think it struck me..... If I choose mounting point:  "/" it will be root, right?

Yes boot is sda if that is where you have your grub, and "/" is your mount point for Ubuntu. It is your ext4 partition.

---

### Post by zvacet on 2013-01-16
@ **dbcityl**

In my opinion 135 GB is to much for /root.It will be better to give 10-15 GB to /root and few gb for swap and rest for /home partition.That way your files will be safe in case of reinstall,fresh install...For this scenario is best to create one extended partition and inside of it make logical partitions like /root ,/home swap.

---

### Post by dbcityl on 2013-01-17
Thanx again for reassuring me & the extra info. It gave me enough info to look up the details myself. I will try to perform the install now, since it seems you can quit it without changements, as long as you don't click " install".

I think I'll try ubuntu studio 12.04 as music is more what i'm interested in anywayz , and the installer seems the same. 
I'll make one extended partition with logical partitions: 15gb for /root;  4gb for swap and the rest for /home partition.

 I'll let you know what happened & hopefully mark the post as "solved"

---

### Post by irv on 2013-01-17
I have Ubuntu Studio installed on one older laptop for my sound system, and it does a good job. But for my everyday working laptop I use Ubuntu 21.10 with Unity DE, which I like much better. If you want to use it for sound and music you can install any desktop you want and then just install all the sound software that fits your needs.

---

### Post by dbcityl on 2013-01-17
I see what you mean. 
Been fiddling around with ubuntu studio on a pendrive just now,
and I prefer unity as well, I think. Bit too MS for me, at first sight. But  the usb boot is a nice way to get to know what programs I do like about it, and add them to ubuntu later. 

And with the /home partition, a change won't be a big thing, if decided upon later  ;)

I just have to check if the differences in kernel really make up for that big of a difference in latencies. If not,standard Ubuntu seems better for me. I'll consider 12.10, since you seem to like it.

---

### Post by irv on 2013-01-17
> **dbcityl said:**
> I see what you mean. 
Been fiddling around with ubuntu studio on a pendrive just now,
and I prefer unity as well, I think. Bit too MS for me, at first sight. But  the usb boot is a nice way to get to know what programs I do like about it, and add them to ubuntu later. 

And with the /home partition, a change won't be a big thing, if decided upon later  ;)

I just have to check if the differences in kernel really make up for that big of a difference in latencies. If not,standard Ubuntu seems better for me. I'll consider 12.10, since you seem to like it.

12.10 has some improvements over 12.04, but 12.04 has LTS. And that means it will be supported for 5 years on this release.
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases]("http://en.wikipedia.org/wiki/List_of_Ubuntu_releases")
Check the chart midway down this page for support dates.

---

### Post by dbcityl on 2013-01-17
Just installed 12.04! And it seems like everything works as it should!
thanks for helping, guys

Didn't get to choose between primary or logical partition, though... the option simply wasn't presented.
So I just made a small swap-partition; a root (ext4 with mount point:"/") of 15gb and another ext4 with mount point "/home")

If anyone should be looking for answers in this thread, here's another nice explanation :

[http://askubuntu.com/questions/179362/how-to-create-partitions-in-ubuntu-while-installing](http://askubuntu.com/questions/179362/how-to-create-partitions-in-ubuntu-while-installing)

---

