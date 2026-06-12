---
title: "I want to use ubuntu exclusively!!"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by dapunisher on 2008-10-30
Right now I am dual booting ubuntu with vista.  I currently have my 80gig hard drive partitioned to 50/30 for vista/ubuntu.  I want to completely delete vista off my computer and exclusively run ubuntu only.  I have the ubuntu 8.04 hardy heron install disk that I burned when I installed ubuntu.  I don't know much about how to use command functions that I see people post but I can follow a tutorial pretty well.  I just got my first(that I can actually call mine) computer a couple of months ago so I'm not real command function savvy.  If I have to delete my whole hard drive so be it, I rather do it now while all I have is just a couple of text files I need to back up.  If it helps any I also have the disk that comes with your computer that recovers the system.  I have access to a laptop so I can follow directions while I'm working on my computer.  Thank you for helping me out.

P.S.  UBUNTU PWNS WINDOWS!!

---

### Post by jvchawk on 2008-10-30
Boot your computer with UBUNTU Live CD. Do not install. Just go to Administration and use the Partition Manager (it exists only in Live CD). Drop the Vista partition. Then resize the UBUNTU one. Good luck!

---

### Post by estyles on 2008-10-30
Any particular reason?  I mean, if you've already got Windows, that presumably means you've paid for it (if it's a pirated copy, then by all means delete it, but if it came with the computer then you paid for it).  I would keep it around because there are always going to be programs that only work in Windows.  Of course, you don't have the largest HD in the world, but unless you're downloading a lot of torrents, or making lots of movies, or other things that really eat up a lot of HD space, Ubuntu is pretty light on the HD.

If you really want to do it, then it's reasonably simple to load up GParted on the LiveCD and just delete the Windows partition and make the Ubuntu partition bigger.  Personally, I'd rather think about getting a second HD - they're relatively cheap these days, although it's understandable if it's not an option financially.

Maybe just wait until you really need that extra HD space?  Like I said, it's relatively easy to do at any point.

---

### Post by mkvnmtr on 2008-10-30
I have3 to agree with estyles. The value of a dual boot system comes when you mess up your Ubuntu and need to contact the forums for help. I have never used Vista because I am a Mac user. I seldom use my Mac OS but I would not delete it. Might make it smaller. In the end it is your choice but think about it.

---

### Post by dapunisher on 2008-10-30
Actually I don't use windows anymore.  But since the majority says that its a good idea to keep it on the system then I think I would(at least till I get another HD).  So I think I will shrink my windows partition and expand my ubuntu partition.     Yeah I know I paid for this copy of Vista, but the ubuntu GUI is alot less hassle then windows is.  I dont use like 95% of the software that comes with it.  Its just seems to me to take up too much space.  The software I do use on my computer didn't come with the system.  So essentially moving to ubuntu will free up alot of space I could use for software that I actually use.  

Firefox
BlueJ
Notepad
PDF
Java JDK, JRE
Dreamweaver
Flash
Photoshop

The last three I know of equivlents(i dont do wysiwyg).  The others run in ubuntu.

anyways thank you for giving me a direction to move in.

---

### Post by estyles on 2008-10-30
Don't take the advice to dual-boot as gospel.  It's just advice.  IMHO, you'd be better off continuing to dual boot.  You might see a new game you want to play that only works on Windows, or need to do some work that for some reason requires Photoshop instead of Gimp, or some other Windows program.  Or you might hose your Ubuntu installation and need Windows to get online (though you could also use the LiveCD for this).  If you really want to rid yourself of Vista, then do it, advice be damned.  ;) 

The thing is, I don't hate Vista - I think it's actually a decent OS.  I just prefer Linux.  I have a laptop that runs Vista (dual boot with Mint - but I haven't been able to get wireless working on it, and my wife finally convinced me that there was no pressing reason to run Linux on that machine anyway, so I gave up on the wireless and rarely boot up Mint on it), and a desktop that runs various flavors of Linux at different times.  The desktop still has Windows 2000 on it, and I occasionally boot it up to play games, but mostly I keep it around just in case.

"I can think of a million reasons to keep it, but mostly, it's for the reasons I *can't* think of."  ;)

Hopefully the instructions above for removing/resizing your windows partition are helpful enough for you.  You should back up data beforehand, since if something crashes your computer while resizing, it's a huge pain to get your partitions back.  It's possible, though, I've done it.  I talk a big game about backing up, but for all that I know it's a requirement, I rarely actually do it.

---

### Post by Mark Phelps on 2008-10-30
Shrinking Vista can produce problems.  First of all, because doing it inside Vista often results in very little reduction due to Vista's insistence on retaining unmoveable files.  Second, shrinking outside Vista, using GParted will invariably result in an unbootable Vista OS -- which is easily fixed by booting using the Vista DVD and running startup repair -- but which is a showstopper for Vista if you don't have a DVD, a recovery disk, or any way to obtain either.

Also, if you remove the Vista partition and expanding the Linux partition, GRUB won't work properly anymore because the GRUB menu takes the partition sequence into account when it creates menu.lst entries.  When you remove the first (Vista) partition, Grub will still try to boot Linux from the second partition, which is now (in GRUB terms) actually the first.  You will  either have to reinstall Grub or edit the menu.lst file to fix that.

---

