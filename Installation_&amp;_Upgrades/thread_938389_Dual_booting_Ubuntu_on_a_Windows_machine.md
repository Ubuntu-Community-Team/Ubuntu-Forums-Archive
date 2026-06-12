---
title: "Dual booting Ubuntu on a Windows machine"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by rfkrocktk on 2008-10-04
I'm trying to dual boot Ubuntu on my Windows machine. I want to install it on my D:\ partition. What I did is I tried to start up my computer with the install disc in my CD drive, but that didn't work so I had to install the boot entry via the installer from inside of Windows. 
Now I've got it up and running but only through the CD. I'm trying to get it going by installing it from the install link on the desktop. What I can't seem to figure out is how to do it. I don't want to wipe my windows installation and the instructions are really vague: [https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)
It says to create a new partition, but the menu won't let me. I can't even create a partition table without undoing all previous partitioning. What do I do?

---

### Post by Herman on 2008-10-04
What partitions do you have already?

There are a number of web sites out there with good guides about how to install Ubuntu, but hard disk partitioning is still something that doesn't seem to be well explained or new users have a hard time understanding it at first.

If your computer only came with one big partition taking up the entire hard disk it's simple, you just select 'Guided Partitioning' , select a size and sit back while the Ubuntu installer does everything for you.

It's more complicated if the computer manufaxcturer made a 'recovery' partition to save a dollar for a blank CD, instead of providing you with a proper Windows installation CD. Some computers have more (backup) software which writes to a third partition as well.
That makes things  more difficult, but it's still possible to install Ubuntu as long as the last partition doesn't contain too much data..

If the user has made one more partition already though, for a data partition or something, they would out of luck.
There are only four slots in the standard dos style partition table, so we can only have four primary partitions. (The partition table is the place in the MBR where the start and end sector numbers for each partition are recorded, and a few other details about the partition).
The trick is to make one of your partitions 'extended'. An extended partition can have more partitions created inside it, called 'logical' partitions, and we can have a number of those, and so have more than four partitions per hard disk.

I'm not sure, but depending on your problem, you might need to move some data to some other storage media and delete a partition first so you can make an 'extended' partition, (or Ubuntu will do it for you). 
I'm just having a wild guess though, maybe your problem is something else totally.

---

### Post by rfkrocktk on 2008-10-04
I just wiped out my Windows Vista OS on this machine for Ubuntu, so I guess partitioning is out of the picture now.

However, now I'm experiencing some really lame problems with Ubuntu not being able to find my network drivers. My network connections icon by the clock disappeared and I can't seem to get any outgoing connections to any network to work...

I've read the guide back to front and I've been through troubleshooting, I just can't figure this out. I've found the driver in terminal and it says it's there but it's disabled. How do I enable it? The troubleshooting is vague at best.

---

### Post by rfkrocktk on 2008-10-04
Turns out I have a BCM4318 network driver which sucks I guess. 

I found this post on the problems I was having but I'm unable to step through it: [http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)
because of some errors.

Can anyone help me get my network connectivity up and running? I really want Ubuntu to work for me :(

---

### Post by Herman on 2008-10-04
I have a laptop with a BMC4318 wireless card too and mine works fine. They're fairly popular.
I do seem to remember needing to do something to get it working, but I don't remember the how-to I used right now. It was easy.
I'll see if I can find out for you...

---

### Post by Herman on 2008-10-05
About the first thing just about all of us do as soon as we install Ubuntu is to enable more repositories.
Do you know how to do that?
That will probably help you a lot, because the software you need will most likely be found in a repository that's not enabled by default.

Just in case you don't know, here's a link about that, [How to enable the universe and multiverse *repositories* in Ubuntu ...]("http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html")- ubuntugeek

Try that first if you haven't done so already.

---

### Post by rfkrocktk on 2008-10-05
How do I download the repositories if I can't connect to the internet because my card is disabled? 
I guess I just need to figure out how to enable the card. Can anyone help me do that? Till then I'll see if I can hardline this thing and make some progress on it.

---

### Post by rfkrocktk on 2008-10-05
I've got the universe/multiverse repositories enabled now. I had to connect directly through an ethernet cable but now I have the internet up and going on this thing. 

Quick question, will these repositories fix my problems that I'm having? I'm new to Linux, but I like the idea of using repositories in operating systems, I use SVN in my development and it's a lifesaver as well as it gives me access to live development for projects I follow daily. Gotta love it. 

So I guess my question is still this: how do I enable my wlan0 card?

---

### Post by rfkrocktk on 2008-10-05
I've got it up and going. Thanks everyone for your help. I spent my entire 19 years being a Windows user, and now I can proudly wave the Linux banner for all to see. :)

---

### Post by Herman on 2008-10-06
> I've got it up and going.:) Cool! Congratulations and good work! Sorry about the lateness of my reply, I was away from my computer for a while.
Regards, Herman :)

---

### Post by rfkrocktk on 2008-10-06
Yeah. I'm really stoked to be over on Ubuntu. My Windows OS on this machine would take YEARS to start up, you have no idea, and Ubuntu fires up in less than a minute and shuts down in less.

Now if I only could figure out how to run .NET applications...

---

### Post by Herman on 2008-10-06
> Now if I only could figure out how to run .NET applicationsSorry, but I don't know how to help you with that except I did a quick search of these forums for .NET applications and came up with this other thread, [C# guys, show us your sugar!]("http://ubuntuforums.org/showthread.php?t=939457&highlight=.NET+applications")
Referring to post #4 there, tinney says,> mono is a .Net port for linuxI hope that helps you at least a little bit, otherwise probably another search of these forums will turn up more info. Even better maybe, start a new thread with '.NET' in the title and try to make up a catchy title that will attract the attention of the type of people who would be knowledgeable in that field. Perhaps somewhere in the [Development & Programming]("http://ubuntuforums.org/forumdisplay.php?f=310") section of the Ubuntu Web Forums might be good, I'm not sure.
Actually, if you go into [Development & Programming]("http://ubuntuforums.org/forumdisplay.php?f=310") and do a search there, you'll only be searching that forum, and not the entire Ubuntu Web Forums, so your search will turn up a lot of more relevant results in the first three pages.
I hope I was helpful,
Regards, Herman :)

Oh, and welcome to Ubuntu! :)

---

### Post by rfkrocktk on 2008-10-06
Thanks, I just found Mono and I'm going to give it a run as soon as I get home. I'm glad to join the ranks of the Linux army as well as the Ubuntu community. I've gotten more support in 72 hours for free through the community than I have through Microsoft in 19 years. Get some.

---

### Post by me_ben on 2008-10-06
Ya being a Linux Army is really proud thing Start up messing up with Ubuntu & do Add more programs daily and you will love .deb files

---

