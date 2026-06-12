---
title: "Dual-booting XP and Ubuntu Feisty"
date: 2007-07-26
forum: Installation &amp; Upgrades
---

### Post by Naazir on 2007-07-26
I have a relatively new (4-5 months old) pc at home built for gaming. Tons of hard drive space, 8800GTX, 4GB RAM... the works. I had Vista on it and finally decided last weekend to toss that and go back to XP. In the process I decided now might be a good time to quit futzing around with Linux at work on various machines and run it for real at home.

I grabbed a 250GB SATA drive and gave it a 50GB partition right up front. I installed XP there and all was groovy. I moved XP's pagefile on to another hard drive as well as the location for My Documents so 50GB will be plenty. 

I then installed Ubuntu Feisty 7.04 (downloaded on 7/25/07) onto a 30GB partition directly following the XP partition. I had previously made a 3GB partition on my second hard drive for the Linux's swap. I also made a large (~70GB) partition for Ubuntu's /home. 

| <- 50GB XP -> | <- 30GB Feisty root -> | <- ~70GB Feisty /home -> | <- xxGB for drive images -> |

|<- 3GB Feisty swap -> | <- ~150GB Storage -> |

(Those are ascii representations of my 2 hard drives)

So far all is well. I spent about 3.5 hours trying to get my 8800GTX enabled and running (ROFL latest and greatest and only XP knows it!) and finally was successful (Envy FTW!). Ubuntu is up and running and functioning like a champ.

Then I tried rebooting and going back into XP to see if things still worked there. I'm using GRUB and selecting XP was pretty simple. Windows tried to run a CHKDSK but I canceled it thinking it might screw something up in Linux. I got into XP and everything worked. HOORAY!!

So, with everything working properly on my very first attempt to dual-boot anything, you'd think I'd be all happy and stuff right? Well, there IS one slight problem. More of a nuisance I guess but... I don't like it. EVERY time I choose XP, Windows wants to run CHKDSK. I don't want it to CHKDSK my Linux partitions but I can't seem to stop it from trying. At one point it even stopped listening to my USB keyboard when I tried canceling it and I had to connect a second PS2 keyboard! (Damn Microsoft!!)

Anywho.... anyone else experienced this before or know what I can do about it? Very much appreciate the help in advance.

(btw, I'm a computer geek for life, from age 9 till now-39. I know Windows pretty well and could probably hack something up to make it stop but I'd rather discuss this with people who might know a little better than me and work it out instead of mickey-mousing it.)

---

### Post by Pumalite on 2007-07-26
I'm not a geek, but I can tell you this: I left windblows and never looked back. I do in Linux same and more than before. Isn't it time ( being 39, and a geek ) that you got rid of windoze?

---

### Post by Naazir on 2007-07-26
:KS

Agreed... which is why my next trick is to get my current (and dying to be replaced) MMORPG running in Linux. At that point i'll have no further use for Windows till the next MMO I wanna play comes out and I need to play while figuring out how to run THAT one on Linux.

So, I'm headed there... the closer the world comes to "open mindedness" the closer we can ALL drop the Microsoft dead weight and BREATH again!

---

### Post by manndani on 2007-07-26
I dual boot with XP & Kubuntu, I never have the problem with CHKDSK, it never starts when booting, could it be something in your XP settings?.
I must say I only use XP now for My photo printing, I do like XPs printing wizard & I use Acronis true image to back up my Linux & XP systems.:)

---

### Post by Pumalite on 2007-07-26
I'm glad you've seen the light. You know what they say about life: Live it with courage. Take the plunge and then you'll be forced to find your answers. Life is a challenge. In China they say: Happiness is in the 'beginning'

---

### Post by Naazir on 2007-07-26
> **Pumalite said:**
> Live it with courage. Take the plunge and then you'll be forced to find your answers.'

That was my thinking mostly. Get Linux running at home and set it up with everything you want to do in Windows (I already know I can do this as I've done it with at least 10 flavors of Linux so far at work). Then when it can do everything XP can do... I'm DONE! What would I need Windows for then?

Problem is when the next game comes out. I gotta have the games man. Basically, the XP option on my home computer will be like having an Xbox, only used for a game or 2 and that's it.  ;)  Till it gets ported to Linux of course!

---

### Post by Naazir on 2007-07-26
> **manndani said:**
> I dual boot with XP & Kubuntu, I never have the problem with CHKDSK, it never starts when booting, 

Are you using GRUB as an boot manager? and which did you install first? XP or Kubuntu? just curious. not sure how that info will help me but it might help someone else here.

---

### Post by Pumalite on 2007-07-26
> **Naazir said:**
> That was my thinking mostly. Get Linux running at home and set it up with everything you want to do in Windows (I already know I can do this as I've done it with at least 10 flavors of Linux so far at work). Then when it can do everything XP can do... I'm DONE! What would I need Windows for then?

Problem is when the next game comes out. I gotta have the games man. Basically, the XP option on my home computer will be like having an Xbox, only used for a game or 2 and that's it.  ;)  Till it gets ported to Linux of course!

You seem to be a guy of means. Get a box for windblows alone.

---

### Post by Brian96 on 2007-07-26
Is it trying to check your Linux partitions?

I can't remember the circumstances, but I have had issues in which Linux told me to reboot into Windows and let it run CHKDSK (I absolutely can't remember why). In my experience, though, it only runs CHKDSK on the C: drive (Windows partition) not on my Linux partitions. If it is only checking C: then maybe just let it run once and see what happens.

---

### Post by Brian96 on 2007-07-26
> **Naazir said:**
> Are you using GRUB as an boot manager? and which did you install first? XP or Kubuntu? just curious. not sure how that info will help me but it might help someone else here.

I am running Win XP and Ubuntu with GRUB. As long as you install Linux after XP you should be fine, which is what you did.

I am guessing, but I think that it is possible there is just some mounting/remounting issue going on, especially if you resized your Windows partition during Ubuntu setup.

---

### Post by Naazir on 2007-07-26
> **Pumalite said:**
> You seem to be a guy of means. Get a box for windblows alone.

Yes, I could do that, but I'm more the type of person to make 1 computer run XP, Ubuntu, Mac OSX and Vista together. 2 down, 2 to go...

---

### Post by Pumalite on 2007-07-26
> **Naazir said:**
> Yes, I could do that, but I'm more the type of person to make 1 computer run XP, Ubuntu, Mac OSX and Vista together. 2 down, 2 to go...

Ah,...OK. Good luck!

---

### Post by Naazir on 2007-07-26
> **Brian96 said:**
> Is it trying to check your Linux partitions?

I haven't let it actually "start" the CHKDSK yet as I cancell it as quickly as possible. Typically when the auto-run CHKDSK kicks off and finds something it doesn't like it tries to "fix" it. If it finds something on a Linux partition it doesn't like (GRUB boot manager or something important like that) then I KNOW I'll have problems. Since both OS's are loading and working fine (besides this annoyance), I don't want to risk creating more problems than I already have, know what I mean?

---

### Post by Naazir on 2007-07-26
> **Brian96 said:**
> ...just some mounting/remounting issue going on, especially if you resized your Windows partition during Ubuntu setup.

I didn't resize XP's partition but I did change the other partitions on that hard drive after installing XP and before/during installing Linux. I suppose I could create an image of the entire hard drive then let Windows do whatever the heck it thinks it needs to do and see what happens.

---

### Post by Brian96 on 2007-07-26
> **Naazir said:**
> I didn't resize XP's partition but I did change the other partitions on that hard drive after installing XP and before/during installing Linux. I suppose I could create an image of the entire hard drive then let Windows do whatever the heck it thinks it needs to do and see what happens.

Yeah, you might just verify what it is actually trying to check. I remember now that the issue I had with this was when I resized a partition, I think during an installation. I think basically Windows just needed to be sure everything was okay since the partitions looked different from the last time they were mounted. I don't think it has anything to do with GRUB.

---

### Post by Naazir on 2007-07-26
Well, I guess I can let it go through it's check, only thing is you can't stop it till it's done and it's going to "fix" things without asking. Well, that's what I wanted for myself though right?? Plunge in head first and come out swimming eventually...  ;)

(Still wish there were a way to disable this auto-CHKDSK thing in Windows. Think I'll jump into a MS forum and check there. Tried here first cuz I wanted replies from intelligent people. Now I'll have to wade through spammers, know-it-alls, snobs...)

---

### Post by Naazir on 2007-07-26
chkntfs /x <drive letter:>   ( chkntfs /x c: )


This command will prevent Windows from running a chkdsk on whatever drive letters you choose. The only way to get it to run on that drive again is to re-enable it first ( chkntfs /d <drive letter:> ) 

The /x switch will only remember the last drives mentioned, meaning if you do a chkntfs /x c: then the next day type chkntfs /x e:, it will only disable chkdsk (chkntfs) on the E: drive. You'd need to do a chkntfs /x c: e: to get it disabled on both (or more) drives.

Hope someone finds that info useful.

---

### Post by manndani on 2007-07-26
> **Naazir said:**
> Are you using GRUB as an boot manager? and which did you install first? XP or Kubuntu? just curious. not sure how that info will help me but it might help someone else here.


 yes I'm using Grub and I had installed XP first, I'm running Kubuntu on a seperate Hd.

---

### Post by MadSavage on 2007-08-22
**> Anywho.... anyone else experienced this before or know what I can do about it? Very much appreciate the help in advance.**

Okay, I am really busy looking through the forums, so I'm sorry if this is already answered for you.
CheckDisk (CHKDSK) is DOS's earliest "Problem Solver", which is like, ScanDisk in newer versions of Windows. It routinely checks **all** partitions for errors. If Windows wants to run this on boot, allow it, it's usually a routine. (I seem to remember when I used WinXPServicePack1 with multiple partitions (one for DOS, one for XP, and one for Linux), upon finally booting Windows, it wanted to run CheckDisk prior to boot. This isn't an issue: on top of that, it will constantly try to do it until successful (Windows saves info. in a file, telling it what to do on Boot. these *one shot* managers are scripted to delete themselves upon successful completion.

Also, another bit of information. Windows is quite stupid without 3rd party software. Windows recognizes FAT, FAT16, FAT32, NTFS partitions **ONLY**. Anything else is seen as "Unpartitioned Space" by Windows. (Whether it's the windows installer, or the OS) So the only way to actually harm a linux partition with WIndows is to run the administrative tools that allow you to format unpartiioned space. 

So to sum it up shortly: Don't worry, it's all good.

*EDIT* I also wanted to let you know...changing the location of Windows Page File will incite a checkdisk on Boot, for the very same reason that resizing a partition does it: windows wants to ensure that everything will run properly if the pagefile is located elsewhere.

---

