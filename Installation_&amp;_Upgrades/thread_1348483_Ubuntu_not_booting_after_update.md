---
title: "Ubuntu not booting after update"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by rpares on 2009-12-07
Hello there!

I am completely new to the Ubuntu environment. I just installed on my computer (which also has Windows)and love it.
However, this is the second time that after doing requested Updates and restarting, I am getting the "terminal" with a message:

[COLOR="Red"]GNU GRUB version 1.97 beta 4

[ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible/device/file completions. ]

sh:grub>[/COLOR]

Can anyone out there help me to fix this problem. This is the second time it happen and is frustrating. 
I am an Architect. Have no clue about operating systems. I am doing this move to ubuntu due to its good reputation. I really want to make it work for me.

PLEASE PLEASE, if you try to help me and answer this, be very basic. I don't have knowledge of it. (Imagine you are talking to your grandfather about it; whatever he won't be able to understand, I won't either) LOL!

Thank you very very much for any help on this issue. 

Best Regards,

Ruben

---

### Post by namok on 2009-12-07
Please follow the ['Boot Info Script: How to']("http://ubuntuforums.org/showthread.php?t=1291280") and put the results.txt file in your next post.

---

### Post by rpares on 2009-12-07
Thank you  very much for your response. I tried to you what you said; way too complicated for me. I can't go into this. It is not my field of expertise. Looks like Ubuntu is for people that are really into programing. 
I will have to remove it.
Thanks anyways.
Ruben

---

### Post by darkod on 2009-12-07
This problem was usually happening to people that installed wubi. Did you install from within windows using wubi.exe or you booted with the ubuntu cd and did it like that?

---

### Post by rajesh88 on 2009-12-07
hello,
i have installed ubuntu 9.10 through wubi. After doing updates i am also facing the problem.

---

### Post by darkod on 2009-12-07
> **rajesh88 said:**
> hello,
i have installed ubuntu 9.10 through wubi. After doing updates i am also facing the problem.

Flollow the instructions in post #10 here:
[http://ubuntuforums.org/showthread.php?t=1339203](http://ubuntuforums.org/showthread.php?t=1339203)

If you know on which partition you installed wubi you need to replace /dev/sda1 with the correct partition. If you don't know either try to explain in which partition it is, or if you have only one hdd keep trying with /dev/sda1, then /dev/sda2, etc.

In the instructions for XP be careful there is typing mistake in /boot/initrd.img-26.31 it should be 2.6.31

---

### Post by rajesh88 on 2009-12-07
hello,
thanks you for your quick reply. I solved my problem. but on boot screen i am seeing so many options like generic 14, 15, 16, (normal and recovery mode) and also vista. I am not able to load 16. how to disable this screen and tell me how to avoid this kind of problems? thanks in advance

regards,
rajesh

---

### Post by darkod on 2009-12-07
Leave them for the moment.
As for how to prevent happening in future, I don't know. And I don't want the wubi camp here to start jumping on me if I say don't use wubi.
I recommend you read about the difference between wubi install and ubuntu side-by-side dual boot install because it's not the same.
Yes, installing wubi trough windows is very easy but the result is not the same as installing by booting with ubuntu cd and selecting Install Ubuntu. There are good and bad things for both ways. I personally don't use wubi, but that's up to you.
As long as you are aware there is another way to install, use what ever is working fine for you.

---

### Post by rpares on 2009-12-07
I solved my problem.
Best fix ever: reinstall ubuntu from scratch!

Don't do updates! It will stop your computer from working fine and will take lot of time and effort of your valuable time.

Best Regards and thankkksss!

Ruben

---

### Post by darkod on 2009-12-07
> **rpares said:**
> I solved my problem.
Best fix ever: reinstall ubuntu from scratch!

Don't do updates! It will stop your computer from working fine and will take lot of time and effort of your valuable time.

Best Regards and thankkksss!

Ruben

If you don't want to spend some time diagnosing your problem, that's fine. But please don't give misleading advice to someone else reading this thread. I have done all the updates and it all works fine, the same for plenty of other people.

---

### Post by DDMacon on 2011-09-23
I just spent a couple hours upgrading to Ubuntu 10.10 since the Update Manager said it was new for me and available.  After finishing the install, I was prompted to re-start to complete the changes.  However, all I get is a black screen with the white hyphen cursor flashing in the upper left-hand corner of the screen.  
 
I had the old version partitioned with Windows XP on the other side.  Usually, it would automatically load Ubuntu unless I scrolled down to Windows XP to launch that instead.  Now, it just goes to the black screen and the flashing cursor.  I really was enjoying the speed of Ubuntu, as Windows XP is becoming more prone to freezes with Internet Explorer.  Please help!!!

---

### Post by Rubi1200 on 2011-09-23
Thread closed.

Reason: necromancy

@DDMacon;

Hi and welcome to the forums :-)

Please start your own thread with relevant information pertaining to the problem you are facing. You can link to this thread if you want but we do not encourage thread hijacking here nor raising old threads from their graves.

Thanks for understanding.

---

