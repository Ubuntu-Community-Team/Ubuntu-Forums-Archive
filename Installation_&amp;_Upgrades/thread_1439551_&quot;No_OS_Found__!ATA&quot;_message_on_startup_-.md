---
title: "&quot;No OS Found / !ATA&quot; message on startup - now booting from Ubuntu from CD"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by Xyp on 2010-03-26
So here's what happened to me.

I burned an image of Ubuntu 8.1 (exactly as described on psychocats.com) to try out Ubuntu on my Dell Inspiron 9400 which normally runs XP. After exploring the CD for a couple of hours and really liking what I saw, I decided to run the "Install" option to get a dual-boot from the HDD happening on my machine. Everything seemed to be going fine, multiple re-boots smooth without problems and allowing me to choose which OS to start from the internal HDD.

Finally it got late enough that I had to rack out for a while, and shut the laptop down completely. I start the computer this morning, and then right after the DELL startup screen, I get a message over a black screen that says "No OS found. Please insert boot disc and press enter." Knowing that both XP and Ubuntu are on my internal HDD, I simply hit enter hoping that it would recognize it... no such luck. It gave me a message that said "!ATA". So now what is happening is that if I try to boot this machine without the aforementioned 8.1 CD in the optical drive, I don't even get the "No OS found." message, it just goes straight to "!ATA". So here I am, cruising the forums, booted from my optical drive.

The only other thing that I was trying on the computer last night that may or may not have anything to do with this problem is that I was working on trying to get Ubuntu to recognize my Seagate 250G external drive (unsuccessfully) through using the instructions found here:
              [http://ubuntuforums.org/showthread.php?t=617841](http://ubuntuforums.org/showthread.php?t=617841)

Anyone have any ideas? I (of course) do not have the XP install discs that came with this computer, so I'd really love to try to save it... Obviously I am totally ignorant when it comes to the terminal- I was doing this to start trying to learn.

Sigh. Help the noob!

-X-

---

### Post by khelben1979 on 2010-03-26
I have one question for you: why did you choose to install such an old version of Ubuntu?

Besides this, it would be interesting to know how you did the install of Ubuntu (details). If you chose to install Ubuntu on the same harddrive as Windows XP, you did the right choice in having Windows installed first, in my opinion.

If the installation asked you to resize the Windows partition so you could add Ubuntu using the [GParted]("http://en.wikipedia.org/wiki/Gparted") partition tool, I think this is the source of the problem and that the Ubuntu updates which was installed never was the cause of the problem. First time you ever rebooted the laptop and Ubuntu decides not to boot would indicate this problem, I think.

Having Windows and Ubuntu on two different harddrives makes it easier and creates less hassles from what I've read over at different Linux forums.

---

### Post by Xyp on 2010-03-26
> **khelben1979 said:**
> I have one question for you: why did you choose to install such an old version of Ubuntu?

Besides this, it would be interesting to know how you did the install of Ubuntu (details). If you chose to install Ubuntu on the same harddrive as Windows XP, you did the right choice in having Windows installed first, in my opinion.

If the installation asked you to resize the Windows partition so you could add Ubuntu using the [GParted]("http://en.wikipedia.org/wiki/Gparted") partition tool, I think this is the source of the problem and that the Ubuntu updates which was installed never was the cause of the problem. First time you ever rebooted the laptop and Ubuntu decides not to boot would indicate this problem, I think.

Well, the reason I chose 8.10 is that I am such a beginner- the procedure for 8.1 was described in detail on the site that I was reading (psychocats.com), and I thought that it being older meant that all the "bugs" were likely more worked out. I did, indeed, install Ubuntu on the same internal HDD that has XP on it.

Again, I apologize to the group for my lack of knowledge. I can only describe what I saw. I know that I did not use the GParted tool, only what was burned to my liveCD via the image of 8.10 that I downloaded... which is the same disc I'm having to boot from to get this laptop to work at all currently.

If the partitioning is the problem, is there any way to erase the partition from within Ubuntu running from the liveCD (as I am currently)? I'm not even sure what the !ATA message means. If anyone decides to reply with terminal commands to do this, please remember that I am a woeful beginner.

Thanks again.

-X-

---

### Post by khelben1979 on 2010-03-26
I would recommend to do a full reinstallation of Ubuntu without using a small LiveCD. Use a bigger Ubuntu image file of Ubuntu which includes all the possible tools which you require in all this.

Before doing a new install I'm wondering if you have important files on the Windows partition which needs to get backed up? If so, you might consider having some patience in this situation so nothing gets lost in the process.

---

### Post by psusi on 2010-03-26
Can you see your hard drive from the livecd?  Maybe in gparted?  Because it sounds like it may have crapped out.

---

### Post by Xyp on 2010-03-26
> **psusi said:**
> Can you see your hard drive from the livecd?  Maybe in gparted?  Because it sounds like it may have crapped out.

I cannot see my internal HDD from the 8.1 liveCD anymore (in "Computer", right?).

I've now tried booting to a GParted live CD, and successfully reformatted (but not completely erased- the partition won't completely go away, it seems) a 2G partition that I think Ubuntu had tried to install into, and in GParted I do see a drive, but it says "Not Mounted".

Again, if I try to boot the computer up without a CD in the optical drive, I get a message that says "!ATA". I've also noticed that I haven't seen the little idiot light flashing on the keyboard that indicates that my internal HDD is being accessed... I haven't been able to find any information on the "!ATA" message online, but I'm starting to think you might be right. What a crappy way to start my first Ubuntu experience... a dead internal drive.

Anyone else have any thoughts?

---

### Post by psusi on 2010-03-26
What is the output of this command in a terminal:

```
sudo fdisk -l
```

---

### Post by Xyp on 2010-03-26
> **psusi said:**
> What is the output of this command in a terminal:

```
sudo fdisk -l
```

Well, I'm sorry (sort of) to report that I gave up on trying to salvage the XP- I say sort of because I didn't really have anything saved on the XP side that was catastrophic to lose... it was just one of those things where I was trying not to have to dive in to Ubuntu head first as a complete noob.

Obviously that didn't work out too well.

I managed to get a full install of 8.10 onto the internal HDD- still no idea why the computer wasn't seeing it, or didn't want to boot from it earlier. Now that I'm fully updated to 9.10, I do have another question, but I'm going to start another thread for that because this problem seems to have resolved itself- for now.

Thanks to you both for your time and help.

-X-

---

