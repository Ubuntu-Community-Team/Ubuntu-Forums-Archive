---
title: "New drive.....and Ubuntu"
date: 2005-07-31
forum: Installation &amp; Upgrades
---

### Post by CS.Scorpion on 2005-07-31
Hi All,

Ok, I have XP in an 80G drive (I need to keep XP as there are corporate program I need to use that are not Linux compatible).

I also have an unpartitioned 80G drive that I want to use for Ubuntu.

So...will Ubuntu automatically detect this unpartitioned/unformatted drive, or do I need to part./format it in some way...and if so, which format, and do I give it a drive letter?

What size partition should I give for the Ubuntu install? I want to leave room for packages to add later etc. Far as I'm concerned, it can use the whole drive.

How many partitions should I use for install/share/data etc?

Sorry for what seem obvious questions, but I'm a newbie to Linux (just about to try Ubuntu live now), and I want to get as much detail as possible before installing.

Thanks for any help,

Scorp.

---

### Post by CS.Scorpion on 2005-07-31
Wooooooooooooooooooooo.... :grin:  :grin:  :razz: 

Now using Ubuntu Live/Firefox for the first time!! Very nice. The live install went flawlessly on my system, absolutely no trouble at all, so I'm guessing the full install will be just as nice, as everything was detected as far as I can tell.

So, any answers to the questions I posted above?

Thanks,

Scorp.

---

### Post by matthew on 2005-07-31
The answer will depend on some of the specs of the machine you are installing on. We know the hard drive sizes and so on, that's a good start. What cpu are you using? How much ram do you have installed? Is this a laptop or desktop? Anything else you can add would be good.

To get you started, here's a basic estimate that might be tweaked slightly depending on your answers to the above:

I would partition like this:
2x the amount of ram you have installed for /swap, but not more than 1 Gb
10 Gb for /
the rest in /home

This thread might interest you  [http://www.ubuntuforums.org/showthread.php?t=48561](http://www.ubuntuforums.org/showthread.php?t=48561)

---

### Post by CS.Scorpion on 2005-07-31
matthew.....that was an awesome link, thanks!  \\:D/ 

In reading that, I now understand more than I did a few hours ago, as in hda1/2/3 etc would correspond to C:/, d:, e: on a windoze machine, and the ext2/3 are different types of 'format', similar to Fat32/NTFS etc.

I think I understand about partitioning as well, with / being the root....etc etc, as explained in the link item.

Again, thanks.

To answer your quesion, it's a desktop machine, and I have P4 3.0Ghz, 1G ram, ATI 9550 Radeon 256Mb, onboard lan, generic sound card, 2 x 80G hard drives (one unpartitioned as stated).

Will 10G for root be enough? I gave XP 10G, and now it is pushing the limit, even though I install everything else to another partition. I don't want to have to move or reinstall later (although am I right in saying Linux doesn't mind moving partition 'walls'?).

Anyway, anymore info greatly appreciated    [-o< 

Scorp.

---

### Post by matthew on 2005-07-31
> matthew.....that was an awesome link, thanks!  \\:D/ 
You are welcome.

> In reading that, I now understand more than I did a few hours ago, as in hda1/2/3 etc would correspond to C:/, d:, e: on a windoze machine, and the ext2/3 are different types of 'format', similar to Fat32/NTFS etc.
Exactly!

> I think I understand about partitioning as well, with / being the root....etc etc, as explained in the link item.
Right.

> Again, thanks.
You are very welcome.

> To answer your question, it's a desktop machine, and I have P4 3.0Ghz, 1G ram, ATI 9550 Radeon 256Mb, onboard lan, generic sound card, 2 x 80G hard drives (one unpartitioned as stated).

Will 10G for root be enough? I gave XP 10G, and now it is pushing the limit, even though I install everything else to another partition. I don't want to have to move or reinstall later (although am I right in saying Linux doesn't mind moving partition 'walls'?).
Based on your setup let me make some suggestions, although you don't need to feel like this is set in stone, There is a lot of flexibility in these setups and you can usually make changes later. 

Format all your partitions ext3.

Put your linux-swap partition first. If you are not sure about the size, though and think you may want to increase it later either make it larger than you think you need or put it at the end, where it will still work fine. I would recommend 1 Gb. With as much RAM as you have it isn't likely that even that will be used much (if at all) but it won't hurt anything. If you are uncomfortable with settling on that size but still want to put it at the beginning of the hard drive (where it will be slightly faster) then make it 1.5 or 2 Gb, but I don't personally think that's necessary--and yet, it is YOUR computer. That's the cool thing with Linux, you get to choose how and what you want.

Put your / partition next. 10 Gb is usually enough and that is all I have. I will note that I tend to install TONS of software and tinker with things all the time. Some have made theirs as small as 5 Gb and had no trouble. You do have 80 Gb total to play with so even if you made it 20 Gb you will still have lots of space for /home, which is where most software gets installed. / tends to hold just the system files.
EDIT: I just looked and will note that in my 10.3 Gb / I have still have 4.8 Gb free. In my 31.5 Gb /home I still have 20.5 Gb free. I do have a shared vfat partition with about 10 Gb of music on it in addition to that.

Put your /home last using the rest of the space.

The nice thing about putting your /home on a different partition is that if have a problem or just want to reinstall Ubuntu (or install the next version fresh instead of just upgrading using apt-get dist-upgrade when the time comes) all of your settings, data, and stuff like that will ***still be there***. Pretty cool.

Linux is okay about moving the back end of partitions to make the partition larger or smaller if space is available either way. It doesn't tend to like moving the front end in (making the partition smaller) since there is usually data there.

---

### Post by CS.Scorpion on 2005-08-01
matthew, thanks again for the answers, it helps a lot. I think I will go with your suggestions, although possibly making / 15G (maybe overcautious here, but what the heck), and I'll set it up the way you said, /swap, /, home on the backend. 

Couple more things, if you will all indulge this newbie.... earlier you said: [2x the amount of ram you have installed for /swap, but not more than 1 Gb], then later, after I had put my specs, you upped it to 1.5 or 2G........I think I saw 'not more than 1G' somewhere else too...is there a reason for this? Should the /swap be limited in size?

Next.....I assume there is a way for Ubuntu to see and access windows files...?? I am wondering this in relation to music already on one of the windows fat32 partition, and also as a means to repairing windows if the need arises.

And lastly for now...if I installed Cedega, where would it install to..../home?

Thanks again for any and all replies, I am reading what I can when I get the time, so am learning quite a bit every day, but I think I might just be an ant trying to move a mountain when it comes to the amount to learn.

Scorp.

---

### Post by matthew on 2005-08-01
Hey, scorp,

> matthew, thanks again for the answers, it helps a lot. I think I will go with your suggestions, although possibly making / 15G (maybe overcautious here, but what the heck), and I'll set it up the way you said, /swap, /, home on the backend.
That sounds good.

> Couple more things, if you will all indulge this newbie.... earlier you said: [2x the amount of ram you have installed for /swap, but not more than 1 Gb], then later, after I had put my specs, you upped it to 1.5 or 2G........I think I saw 'not more than 1G' somewhere else too...is there a reason for this? Should the /swap be limited in size?
This is probably telling you something you already know, but the swap file is just some extra hard drive space available for the operating system to use as if it were ram, for those moments when you have so much going on that it won't all fit in your installed ram memory. You won't hurt anything making the swap file larger than 1 Gb, it just isn't likely to ever be used, especially with the amount of ram you have. The swap is really a necessity for people with 256 Mb or 512 Mb, but with 1 Gb of ram the swap won't likely be accessed often except for convenience. As such the 2x ram formula is unnecessary and you could run even quite well with no swap file at all (as I did until I wanted to try to get the hibernate function working on my laptop). However, from time to time Linux may want to use it and with the sizes of hard drives nowdays, losing 1 Gb to make a swap partition is no big deal. My personal feeling is that more than that will just be wasted through disuse, however it will give a bit of a buffer before starting the next partition so if there is ever a reason you need to do some adjusting the space will be available. I really made the comments about making it larger just to make sure you understood you don't have to partition EXACTLY as I or anyone else says. That's all.

> Next.....I assume there is a way for Ubuntu to see and access windows files...?? I am wondering this in relation to music already on one of the windows fat32 partition, and also as a means to repairing windows if the need arises.

This isn't hard at all. Read this page for some great "getting started" type ideas, most of which have been distilled from these forums. Note: this is an _un_official Ubuntu page done by one person, but taking ideas from lots of us. There's a section that tells you exactly how to make the windows partions (Fat32) available for read/write in Ubuntu and even how to read NTFS partitions. I am doing exactly what you are thinking of with my music--it's on a Fat32 partition that is easily accessible to both Windows and Ubuntu.
[http://ubuntuguide.org/](http://ubuntuguide.org/)

Also, check out the official Wiki page as it has a lot of great stuff as well.
[http://wiki.ubuntu.com/](http://wiki.ubuntu.com/)

> And lastly for now...if I installed Cedega, where would it install to..../home?
I've never used it so I can't help you there. Do a forum search and see what you find. I would bet there is a how to thread on Cedega...might even be a few lines in the wiki or the guide.

> Thanks again for any and all replies, I am reading what I can when I get the time, so am learning quite a bit every day, but I think I might just be an ant trying to move a mountain when it comes to the amount to learn.
We have all felt that way, especially at the beginning. I'm glad I can be some help.

Matthew

---

### Post by CS.Scorpion on 2005-08-02
Hey Matthew...again, thanks, especially for the great links. There is some really good reading there (and I urge any other newbies to read the [http://ubuntuguide.org/](http://ubuntuguide.org/) pages at the very least, it will save a lot of questions), and I'm gonna plow through it as fast as possible.

If I have more questions, I'll come back, but I think I'm almost ready to try the install.

I want to learn as much about Linux based O/S's as I know about windoze, and then I can help in here as much as I do on windoze forums!  \\:D/ 

Scorp.

---

### Post by CS.Scorpion on 2005-08-02
Well, that's it.....it's DONE! INSTALLED. NO PROBLEMS (yet...lol)  :grin:  :grin: 


Now I'm off to play with my new toy. That'a what it feels like, a completely new system.

The installation was a breeze, and as far as I know, no problems were encountered, but then I have not used the system yet for anything substantial. I know it seemed to detect the hardware ok, so I think all is ok. I didn't have any problems with the partitioning, although I did somehow manage to give it TWO root (/) partitions, but....wait....Ubuntu figured it out and asked me to correct it! Seems it's even foolproof against the likes of me (ok, ok, I'm not usually that daft, and I don't know how I did it). I was especially impressed that it downloaded packages to install before it had finished, which was very cool.

What more can I say....well, lots, but I'm going to play/test/have fun on my new system (I'm using it now BTW).

L8R,

Scorp.

---

### Post by matthew on 2005-08-03
Very cool! Congratulations and have LOTS of fun with your new toy.

---

