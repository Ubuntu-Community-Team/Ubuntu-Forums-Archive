---
title: "Want to resize 2 partitions, is this the proper way?"
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by Rasa1111 on 2010-10-04
Hey all, 

 I am running from the 10.10 RC liveCD at the moment, and I've just a couple questions before I make any moves here.. 

  Now, I have both 10.04, and 10.10 *beta* installed on my PC, each with their own partitions (obviously)....

As you see here~  Ubuntu 10.04 is on sda1, and 10.10 is on sda6. 
[ATTACH]171334[/ATTACH]

All I want to do, is to simply >shrink< the sda1 partition, 
and <extend> the sda6 partition. 

So, to do this,  I am under the impression that I have to simply right click on said partitions, 
like so.. [ATTACH]171335[/ATTACH]
 and just choose "Resize", correct? 

 Then i just shrink/extend each partition to the size I want? 

 I want to keep my 10.04/Lucid install for awhile, 
but won't be using it much,
So I simply want to give it as much space as it needs, and not much more..
 Keeping the rest of the space for 10.10. 

Since i have them both installed already... 

Is this as easy as what I have written? 

 To just resize each partition? 

Also,
 Once this is done, 
I'm pretty sure that I am going to just wipe the 10.10 partition and reinstall it, on it's now, larger partition. 

 So, in closing, 
I want to keep about 6-8 GB for 10.04, and leave the rest for 10.10. 

 Is this how i would go about it? 
Is there anything I am missing? 

 Many thanks for your time. :) 
Looking forward to your replies. <3

---

### Post by Dustin2128 on 2010-10-04
> **Rasa1111 said:**
> Hey all, 

 I am running from the 10.10 RC liveCD at the moment, and I've just a couple questions before I make any moves here.. 

  Now, I have both 10.04, and 10.10 *beta* installed on my PC, each with their own partitions (obviously)....

As you see here~  Ubuntu 10.04 is on sda1, and 10.10 is on sda6. 
[ATTACH]171334[/ATTACH]

All I want to do, is to simply >shrink< the sda1 partition, 
and <extend> the sda6 partition. 

So, to do this,  I am under the impression that I have to simply right click on said partitions, 
like so.. [ATTACH]171335[/ATTACH]
 and just choose "Resize", correct? 

 Then i just shrink/extend each partition to the size I want? 

 I want to keep my 10.04/Lucid install for awhile, 
but won't be using it much,
So I simply want to give it as much space as it needs, and not much more..
 Keeping the rest of the space for 10.10. 

Since i have them both installed already... 

Is this as easy as what I have written? 

 To just resize each partition? 

Also,
 Once this is done, 
I'm pretty sure that I am going to just wipe the 10.10 partition and reinstall it, on it's now, larger partition. 

 So, in closing, 
I want to keep about 6-8 GB for 10.04, and leave the rest for 10.10. 

 Is this how i would go about it? 
Is there anything I am missing? 

 Many thanks for your time. :) 
Looking forward to your replies. <3
the right click resize is the correct way to do it. Just make sure to back up your data, I've lost data on partition resizes before. Luckily I backed it up though :p

EDIT: also, it looks like a bit more than half of your lucid partition is occupied; you'll have to do some disk cleaning to extend sda6 to the size you want.

---

### Post by Rasa1111 on 2010-10-04
> **Dustin2128 said:**
> the right click resize is the correct way to do it. Just make sure to back up your data, I've lost data on partition resizes before. Luckily I backed it up though :p

 Very nice,
 Thanks Dustin. :)

 Yeah backups are a definite here. lol 

So here is my thinking,

 Go into the 10.04 partition, and remove everything that will no longer be of use, programs/apps, files, etc.. 
To make the install as small as possible. 

 then Ill back up what remains, and commence the resizing..
Leaving it with maybe an extra 1GB or 2, from it's actual size. 

Sound like a plan?  lol

> EDIT: also, it looks like a bit more than half of your lucid partition is occupied; you'll have to do some disk cleaning.

 Yeah definitely going to do some cleaning. 

 Thanks again bro. <3

---

### Post by Dustin2128 on 2010-10-04
> **Rasa1111 said:**
> Very nice,
 Thanks Dustin. :)

 Yeah backups are a definite here. lol 

So here is my thinking,

 Go into the 10.04 partition, and remove everything that will no longer be of use, programs/apps, files, etc.. 
To make the install as small as possible. 

 then Ill back up what remains, and commence the resizing..
Leaving it with maybe an extra 1GB or 2, from it's actual size. 

Sound like a plan?  lol



 Yeah definitely going to do some cleaning. 

 Thanks again bro. <3
no problem, now if only someone could help me with my install problems... meh, my reality distortion field will probably be working again after a good night's reboot.
I'd personally just do a full upgrade to meerkat though, with only 40GB to work with. Or get a bigger hard drive, the current exchange rate $/GB is better than its ever been. Here's a 7200RPM 1TB hard drive for 42$! [http://www.newegg.com/Product/Product.aspx?Item=N82E16822152185R](http://www.newegg.com/Product/Product.aspx?Item=N82E16822152185R)

---

### Post by Rasa1111 on 2010-10-05
thanks man,
 Full wipe and fresh 10.10 install is what ended up happening. :lol: 

 No more lucid now. :(
But 10.10 is working beautifully. 

 Only thing I forgot to backup was all my bookmarks n ish.. DOH!  lol
oh well.

much appreciated mate, <3

---

