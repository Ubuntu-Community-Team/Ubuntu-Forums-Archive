---
title: "debootstrap error"
date: 2005-02-11
forum: Installation &amp; Upgrades
---

### Post by veritas366 on 2005-02-11
I'm moving this from the software help section.  Didn't notice the install forum at first.  This is in reference to a debootstrap error on install. Many are having it and the proposed solution that it is simply badly burned cd's does not seem correct.  First, my original post, followed by my own investigations.


I had an error and I searched for the answer and saw something troubling.

First off, the error, for me is that in installing, I get the error saying debootrap won't load or copy and try burning the cd slower, etc. 

Here's the problem:

1. Many people have complained about this, including those who USED CD'S PROVIDED BY UBUNTU. I don't mean iso's, I mean in the mailbox cd's. Another user got a cd out of a magazine. I burned an iso, but I did it at 1x so it should have been slow enough.

2. I am definitely a noob, but it seems unlikely to me that several people would have the install fail in the exact same place due to faulty cd writing. Think about it, a magazine cd, at least one or two people with ubuntu provided cd's and several people who've made several copies...what are the odds of the exact same error due to a damaged cd? (Am I being a stupid noob here? Is it, in fact, quite common to reproduce the exact same error by a random flaw in cd writing or is there something about the deboostrap file that makes it particularly hard to write?)

3. Every thread has been met with the bad write explanation. One thread was answered by Colin Watson who wrote the actual error message and I've emailed him directly (hey, his email address was on the thread.....)

4. Several people have given up and gone back to their old distro. This is what I'll be doing very soon if I don't see any forward progress on resolving this. Just do a search on "debootstrap" in the forums and you'll see that I'm not as paranoid as all those people talking about me say I am. There really is an issue here.

5. I looked at a bunch of threads. If an alternate solution has already been posted, I didn't see it. I will happily eat both crow AND the egg on my face if the solution has been posted and I just didn't see it. I really wanted to be part of the Ubuntu community as I like the whole philosophy behind it. An inability to install Ubuntu makes that just a tad bit difficult. FC3 has its issues, but installing from ISO (which I actually burned full speed) was not one of them.

Here then is some additional info I found, including a couple of different possible solutions.  

First off, here is the exact error I got  (though I got this from another person’s post)

> Installs the base system 
Debootstrap Error 
Couldnt retrieve gettext-base.This may be due to a network problem or a bad cd, depending on your installation method If you are installing from cd-r or cd-rw , burning the cd at a lower speed may help

Colin wrote back quickly, which I appreciate and said that he could think of no other issue this could be and that he has seen failed installs at a variety of places in the process, which suggests that it is not something wrong with a particular file.  Well, maybe so, but there are a lot of folks having this specfic issue. I’ll catalogue them here.  Within these threads are two other possible solutions, neither involving cd write errors: faulty cdrom drives (I hope that's not my issue!) and also installing in "expert mode" which worked for two people. Why this works or why it should be necessary would be an issue for the developers to address.  


Here is the link to a thread in which three separate people have this issue.  One person after trying 5 different burns of the iso.  Another user in this thread got the cd to work on another system, so it is clearly some kind of issue with his (and other people’s) system.

[Link One](http://www.ubuntuforums.org/showthread.php?t=10423&highlight=debootstrap) 

Here is another thread by a different user who also got the disk to work on a different system.

[link two](http://www.ubuntuforums.org/showthread.php?t=13422&highlight=debootstrap) 



here is another user’s thread who used a cd from a magazine cover.  Note that other users in this thread report installation problems which are similar but not involving debootstrap.  The user with the cd from the magazine gets the debootstrap error.  The originator of the thread made a second cd and still had the error


[link three](http://www.ubuntuforums.org/showthread.php?t=9716&page=1&pp=10&highlight=debootstrap) 

here’s another user with the same problem


[link four](http://www.ubuntuforums.org/showthread.php?t=5515&highlight=debootstrap) 


Here is a user who used CD’s directly from Canonical…two different ones.  His error is that debootstrap exits with an error, but still seems related.  He also suggests it was a bad cd rom drive.  While  a new one worked for him, I wonder if this could be the issue for all the rest of us?

[link five](http://www.ubuntuforums.org/showthread.php?t=10145&highlight=debootstrap) 

This thread contains one possible solution.  This user burned two cd’s using two different cd rom burning programs.  They didn’t work, BUT…he was able to install by using “expert mode.”  I didn’t know that was even an option but nevertheless that fixed it.
[link six](http://www.ubuntuforums.org/showthread.php?t=6016&highlight=debootstrap) 

I hope some experienced users can make sense of why this only happens with a few people.  I'm wondering if we have in common that we tried to partition manually and screwed something up?  Anyway, love to here ideas.  I can't try again till I get home this evening.

---

### Post by cb604 on 2005-02-12
Hey there, I'm getting the exact same errors as everyone detailed here. I'm using:

Dell Laptop Lattitude C500/C600
no extra HD settings (in the bios can't set it anyways)
and I didn't do anything to the acpi thing as everyone was mentioning before.

First time, tried the install, but it gave be a ridiculous debootstrap error.  I thought it was my "fast" burning on my cd burner (LG 24x speed with burn proof, using NERO 5.xx) But the checksums matched in the integrity check and the md5 thing

So right now I just took the CD out, cleaned it and put it back in. 
Then I moved my laptop away from anything that might cause it to vibrate (thus causing the CD to misread? )

It seems to be going (at least  I think it is) and installing ok.

Update : first stage complete let's see how it holds up.
Installation seems to be going well, I don't think  fast CD burning is the main cause of this, maybe it's the CD reading? I think one of the threads mentioned that the CD reading wasn't good and the error came up

Update#2: install complete, everything is up and running fine now. My opinion is that it might have something to do with not being able to read the CD  (like maybe a different generic CD driver or something might work?) but the first and only CD i burned worked.

Hope this helps you guys get to the bottom of this.

---

### Post by Praetorian on 2005-02-12
Same problem here
When I tried to install I get the following error
"Debootstrap error coudn't retrieve bash etc, etc ect."
I have trieded to burn at different speeds. But I get the same error all the time  ](*,).

---

### Post by veritas366 on 2005-02-12
Well, I wish all of you luck.  I went back to FC3 but now I can't boot windows so I'm going to post a separate thread about that.  My point in this post is that a lot of people are having this issue and that it can't simply be bad cd burning.  However, the first response suggests he was having success so maybe his "minimize vibration" approach will work!  

Oh I had tried one other thing.  Some people had good luck going into expert mode...you have to type it in right when it wants you to boot.  However, in expert, it wouldn't recognize my cdrom...I chose to have all the modules loaded but still it didn't recognize my cdrom.  However, it was "expert" mode and, being no expert, it could be something I'm doing wrong.  Anyway, that route was closed to me.  Other people have mentioned using F2 or F3 but I haven't seen an explanation of exactly what that does or how to proceed from there, so I didn't try it.  

Soon, ubuntu will realize these issues are not just paranoid users and they'll get it sorted out.  I don't think most linux distros are this hard to "burn iso's for" if indeed that is the problem.  Once this is sorted out, I think Ubuntu will be in great shape. Everything I hear from those who did install succesfully makes me jealous!  I hope my post will help move them in the right direction.

---

### Post by cloudydaysbehind on 2005-02-13
Well, I'm trying my first Ubuntu install, and I have the same problem, but on a different part of the isntall.

Is it possible that it has something to do with CDs and older systems?  Most of us who have this problems are running on older systems (This one is a Celeron 400MHz, from several years ago).  The CD Rom is making funny noises.  I'm going to try to load a newer CD drive in there (I have to get one from a friend) and try it out.  First, it stopped on installing the base system, but now stops on installing the GRUB boot loader.  

It also tells me there's an error receiving  dhcp3 client, but I'm not plugged into a network.  Would it give me that error if I'm not plugged in, or is that an error accessing the disc?

---

### Post by cb604 on 2005-02-13
> 
It also tells me there's an error receiving  dhcp3 client, but I'm not plugged into a network.  Would it give me that error if I'm not plugged in, or is that an error accessing the disc?

I think that's just cuz you're not plugged into the network.

---

### Post by twodeko on 2005-03-25
Any luck?

Same problem.

---

