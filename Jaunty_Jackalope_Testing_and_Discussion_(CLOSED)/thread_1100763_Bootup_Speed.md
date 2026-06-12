---
title: "Bootup Speed"
date: 2009-03-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by pah99 on 2009-03-19
Hey I have a question. I am running Jaunty and I started to go through various posts on how to reduce boot time. Anyway, after doing a bunch of stuff, I got it down to 12 something seconds. Then, I ran the "profile" thing for the kernel, and my boot time went up to about 40 seconds. Now, no matter what I do, it stays there. If I shut off readahead, then it goes down to 14.3 seconds, but I cant get it back to 12 seconds. I was wondering, isn't readahead supposed to cut down my boot time? If so, then what is going on? Any help is appreciated.

Attached you will find three bootcharts. The first is the 12 second one, the second is the 40 second one, and the last is the current 14 second one.

---

### Post by Yashiro on 2009-03-19
Sounds like the profile function is broken or out of date?

---

### Post by MacUntu on 2009-03-19
> **pah99 said:**
> I ran the "profile" thing for the kernel

Why? The readahead list is optimized so leave it alone.

---

### Post by pah99 on 2009-03-19
> **MacUntu said:**
> Why? The readahead list is optimized so leave it alone.

Yeah, I realize that now. It was optimized when I had it at 12 seconds, but I stupidly figured that after all the stuff I had done to speed it up, I should do it again. And that's when things slowed down. Now, when I turn on readahead, it slows the computer down. So I shut it off and that brings things down to 14 seconds. My question is, when turning on readahead, why does it slow things down so much?

---

### Post by MacUntu on 2009-03-19
Backup /etc/readahead/boot, remove it, reinstall readahead and compare the backup with the original.

---

### Post by Lorenz on 2009-03-19
Can you post some hints on how you managed to speed up the boot process that much? thanks in advance!

---

### Post by illpig on 2009-03-19
> **Lorenz said:**
> Can you post some hints on how you managed to speed up the boot process that much? thanks in advance!


same here,  i`m realy interested in how u got it that speedy!

---

### Post by pah99 on 2009-03-20
> **MacUntu said:**
> Backup /etc/readahead/boot, remove it, reinstall readahead and compare the backup with the original.

Well, that did the trick. The new "boot" file is 1300 lines shorter. This has made Ubuntu boot up in 13.9 seconds now. Not as good as 12.2, but it'll do. 

----------------------------------------------------------

For those of you wondering how it was done, go to these links and do what they recommend. Just don't screw up or you'll end up with an agonizing 40 second boot time. 

I'm assuming you already have bootchart installed, right? If not, go ahead and install it. You'll be using it A LOT!

Start with this one. Its a really good one: [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

For a somewhat better explanation of some of these, go to this website: [http://www.extremetech.com/article2/0,1697,2114124,00.asp](http://www.extremetech.com/article2/0,1697,2114124,00.asp).

This one describes the "profile" thing you heard about in the beginning of the thread: [http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)

Truth be told, I didn't notice a difference with this one, but what the heck: [http://blog.dotkam.com/2008/08/06/speed-up-ubuntu-boot-time-by-starting-networking-on-the-background/](http://blog.dotkam.com/2008/08/06/speed-up-ubuntu-boot-time-by-starting-networking-on-the-background/)

This one is okay. Note a couple things however. First, Jaunty doesn't have /etc/modprobe.d/aliases (at least not in mine), I highly recommend the concurrency thingy, and don't run the profile thing too much: [http://yoten.blogspot.com/2007/04/speed-up-ubuntu.html](http://yoten.blogspot.com/2007/04/speed-up-ubuntu.html).

Now, the other thing is that I got rid of A LOT of start-up programs in "start-up applications". I mean, I killed printer support, evolution, a couple gnome things, and some other random crap. So, go at it keeping in mind what you will need, and what you wont need. If there's something you don't know what it is, best to leave it on, and look it up. Maybe you can kill it. But better not to push your luck. 

One last thing I'd like to make note of is that you'll notice that most of the recommendations in those websites are for older Ubuntu releases. A lot of those things have been implemented into Jaunty already, but there is still a couple you can do.

Now, when going about all this, make sure you take a couple hours out of your schedule. This takes some time. Make your computer login automatically without a password since you will be rebooting a lot... it'll get very annoying if you don't. And one last thing, I recommend you do one change at a time to see if it worked or not. I messed up a couple things and then it took a while to figure out what I did wrong. So yeah. Good luck, and have some fun.

A quick edit. I also recommend you install preload. On first boot, it shaved it down to 13.3 seconds, and it will should get a little faster after 10-20 more boots.

---

### Post by phelin4 on 2009-03-20
> **pah99 said:**
> Well, that did the trick. The new "boot" file is 1300 lines shorter. This has made Ubuntu boot up in 13.9 seconds now. Not as good as 12.2, but it'll do. 

With readahead you should keep one thing in mind: the list it uses must be valid. That means that all the files on that list must exist on your system or it will stop when it encounters one that doesn't. You can test the validity of the list with readahead-list, like this:

```

sudo readahead-list -v /etc/readahead/boot

```

It'll tell you which files it is loading. If it doesn't reach to the end of the list, there are one or more non-existing files on the list.

---

### Post by MacUntu on 2009-03-20
> **phelin4 said:**
> or it will stop when it encounters one that doesn't

Wow, didn't know that.

Edit: Are you sure? If that would be true the reading would stop after line ~80 of 700+. I removed all the non-existent files (~150) but bootchart reports the same time for the read ahead process. It should be a lot longer, though?

---

### Post by phelin4 on 2009-03-20
> **MacUntu said:**
> Wow, didn't know that.

Edit: Are you sure? If that would be true the reading would stop after line ~80 of 700+. I removed all the non-existent files (~150) but bootchart reports the same time for the read ahead process. It should be a lot longer, though?

Actually, I am not ;) It might be a bug with the verbose option too, which would not surprise me since the debug option doesn't work either (shows the version of readahead-list instead of doing any debugging).

---

### Post by pah99 on 2009-03-21
> **phelin4 said:**
> 
```

sudo readahead-list -v /etc/readahead/boot

```


Well, this got rid of about 50-100 lines. I think it may have shaved off a quarter of a second or so. Who knows.

---

