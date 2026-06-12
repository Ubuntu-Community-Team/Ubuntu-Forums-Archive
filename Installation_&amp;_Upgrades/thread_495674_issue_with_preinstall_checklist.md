---
title: "issue with preinstall checklist"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by bullsmack on 2007-07-08
i am excited to try a new operating system. im so tired of windows and ive only been using computers for 2 years. im by far a pro user , but in the 2 years ive been using pc's ive learned enough to know that microsoft is awful.\

 i biult my own pc about 9 months ago.im a fast learner and even though i never touched a pc before 2 years ago. i quickly was biulding my own as i saw store bought pc's as having alot of nothing in them. and i also saw that the sales ppl in places such as best buy and comp usa were very quick to tell you that the pc you were looking at on the shelf was exactly what you were looking for only to get it home and be very upset that they were just trying to sell me a pc ,ANY pc. 


 my issue is that in the preinstallation checklist it asks if i have a floppy drive and the answer is no i do not. im wondering if i can use my dvd burner instead for whatever i would need the floopy drive for?

i will list my specs and could someone please let me know if i will have any issues installing ubuntu. i am anxious to get started as i run a gaming server and im tired of gettinng port scanned every day by hackers that would like to take my server down because they got baned for cheating in some way or another.....here are my specs.....

asus A8N32sli deluxe mother board
AMD X2 4200+ duelcore
x2 Nvidia GeForce 7900 GTOC's
soundblaster live 24 sound card
writemaster dvd burner
western digital 10,000 rpm drive
3 gig memory
7200 rpm slave drive

i do not have any other drives  only the dvd burner as i didnt feel i needed one, if i do and it is mandatory to have a floppy drive i will go get one, no big deal. i would just like to know if i can do it without it? and will it cause issues i , as a new user would be confused about.  thanks in advance

MIKE(bullsmack)


ps. i would like to get this running within the next day as i am moving nexrt week and woudlnt want to start in the middle of the move.

---

### Post by luvr on 2007-07-08
These days, you won't need a floppy drive any longer. My PCs are three to four years old, and they still have a floppy drive each, which I hardly ever use anymore. Modern PCs will use both DVD rewriters and external (mainly USB) storage devices, which more than make up for the lack of a floppy drive.

The only time that I considered myself lucky to still have access to a floppy drive lately, was when I wanted to create a bootable DOS CD-ROM (for use on another computer that *didn't* have a floppy drive), and I had a bootable floppy disk handy that contained everything that I needed on the CD-ROM. I created an image of the floppy disk (using the Linux **dd** command), and I used the image as the source for the bootable image that I could subsequently write to CD-ROM.

---

### Post by bullsmack on 2007-07-08
thanks ,  i just wish ppl would update these lists and stuff all over the internet that say that you need a floppy drive if in fact they were written when the floppy drive was used alot. ppl like me (being only two years young in this) have no clue if they are old helps or if they are dogmatic about the use of the floppy.

i have a couple more questions before i start, is this going to be a nightmare trying to iliminate microsoft altogether or is it fairly simple to install linux. i mean , that checklist is pretty long. and they act like all that info is so important.is it that they are making it more complicated then it really is or is this going to be a job for acronis, which leads me to the real question. 

i did start to installit and quickly canceled it before finding the checklist because i saw that it was doing something with the  bios. so im also wondering if it is going to change my bios and if so wont that mess up all my slave drive programs and files from xp. will they become unusable? and does it make sence to make a duel boot with linux and xp till i get used to using it? 

and the big question... will i be able to run my server from linux? right now i have a batch file that i use to start the server and if it crashes the batch file will restart it if im not here. so i know that the batch file will become worthless. but im wondering if there is a sutable replacement for that type of thing once i get linux working. or do i need to have programming skills to run this operating system? IM SCARED as if you couldnt tell. but one good thing is that im sure the questions im asking are thorough and at least the nest person that comes to find answers can get them all in one thread instead of having to search like i am doing and cant find anything . 


so to sumarize all thjis post.... is it going to make changes to my bios and is that something that ,if i needed to use acronis being that i failed to install linux, would that make my acronis  back up file in my slave drive not work ?

---

### Post by luvr on 2007-07-09
> **bullsmack said:**
> ppl like me (being only two years young in this) have no clue if they are old helps or if they are dogmatic about the use of the floppy.
Definitely old--**very** old!


> is this going to be a nightmare trying to iliminate microsoft altogether or is it fairly simple to install linux.
As for the Linux installation, that should be fairly simple, especially with a distribution like Ubuntu, and provided that you don't want to set up anything too exotic (like RAID, to name just one--if you don't even know what that is, don't worry; it just means that you won't want it); even the exotic configurations may be feasible, but they will likely need a little more work.

One area that **may** give you trouble, is wireless networking--even though all *my* wireless adapters worked right out of the box under Ubuntu.

One other potential issue may be the screen resolution, which Ubuntu (and most other Linux distributions) don't always get right. This is particularly annoying with LCD screens, where a suboptimal screen resolution will result in a blurred image. Should you run into this problem (as I did on one of my LCD screens), it will be a fairly simple matter of editing the X Window System configuration file (i.e., **"/etc/X11/xorg.conf"**).


> is it that they are making it more complicated then it really is
Most likely. Probably, in an attempt to be as complete as possible, they made it look far more complex than it really is.


> im also wondering if it is going to change my bios and if so wont that mess up all my slave drive programs and files from xp. will they become unusable?
Don't worry about your BIOS; Linux won't mess with it. Windows XP, and any programs that you installed on it, will continue to work just fine (that is, of course, assuming that you want to keep them, and that you are going to set up a dual-booting configuration).


> does it make sence to make a duel boot with linux and xp till i get used to using it?
Makes **great** sense! It's what  have been doing for years now.


> will i be able to run my server from linux?
Absolutely! If anything, once you get sufficiently familiar with it, Linux will be far more suitable, and much, much, much superior as a server system, compared to Windows.


> right now i have a batch file that i use to start the server and if it crashes the batch file will restart it if im not here. so i know that the batch file will become worthless. but im wondering if there is a sutable replacement for that type of thing once i get linux working.
The standard Linux command line is **bash,** which has a far more flexible (and, again, just plain superior) batch language than Windows has. In fact, compared to *bash,* the Windows command line, and its batch language, is a boring toy.


> do i need to have programming skills to run this operating system?
No, not really. The bash batch language does have constructs like if/then/else, loops, and variables, and may come close to programming at times--as does any batch language, really. If anything, experimenting with bash will tell you if *acquiring* the programming skills may or may not seem interesting to you.


> IM SCARED as if you couldnt tell.
That's only natural if you're new to the subject. Just give it a try, though, and you will soon come to enjoy it. It will be **fun!**

Just remember one ground rule: **DON'T PANIC!** Something may go wrong at times, perhaps even seem like a disaster, but in that case, **CALM DOWN** before you try to remedy the situation. If you act while you're in a panic, you will likely do more harm than good, anyway.

Also, think about making backups, especially right before you're going to experiment with your system. May initially look like a waste of time, but in the end, the day *will* come that you're happy to have that backup. Personally, whenever I want to make a backup, I will fire up the [System Rescue CD.]("http://www.sysresccd.org/Download.en.php") There will undoubtedly exist far more advanced and sophisticated solutions, but it's sufficient for me.

---

