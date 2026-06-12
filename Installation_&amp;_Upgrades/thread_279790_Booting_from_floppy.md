---
title: "Booting from floppy"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by ngrundy on 2006-10-18
I am trying to run the live cd of ubuntu (dapper). My machine has Windows ME and won't boot from the cd. I have downloaded the two files that I need to format the floppy but I am having some issues.  

I don't know enough about DOS to do what I need to do... 

My dos prompt comes up C:\WINDOWS>

Where do I go from there? I printed out the instructions from the Installation page but I don't know how (spacing)and where (directory)the stuff gets typed in. 

Can anyone give me some realy basic step by step advice?

I thought about trying the server install directly to avoid all of this. When I read the details it seemed over my head. I really want to try dapper but I want to try it first.
thanks

---

### Post by kidders on 2006-10-18
Hi there,

There's a pretty basic step-by-step at [https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto).

Apparently, you insert a formatted floppy, put rawrite & sbootmgr.dsk someplace, go there and type **rawrite -f sbootmgr.dsk** to create a "smart" boot diskette. Is that the command you're looking for?

Post back if you get some sort of error :-)

**Edit:** Incidentally, if your PC is so old that it can't boot from a CD, it may not support Ubuntu terribly well. What are your specs?

---

### Post by ngrundy on 2006-10-18
Right now I have a inspiron 4000 with 128mb RAM, 700mhz celeron, and 10 gb hd. I already have 512 mb of RAM on the way so it should get better.

I want to try ubuntu before I switch. If I like it, I don't intend to run a dual boot system. Just ubuntu. I don't use my machine for anything other than music, the web and some office projects. If I like it and it works well, I might invest in a bigger HD to stay off a new machine for a while.

On the DOS prompt, once I get to the directory that I need, do I type the rawrite command straight in or put a backslash (\) first?
Thanks

---

### Post by kidders on 2006-10-18
Hmm...

Even with extra RAM, your machine will struggle a little ... but no more than Windows does I suppose! 10GB is about half what you'd need to make a dual boot system out of it though, imo :-(

Putting a backslash before a command in Windoze would have the same effect as a forwardslash in Linux ... ie to tell the system that the command you wan't to execute is in the root directory, and not the current one. If that's not the case, don't do it.

Hope that helps.

---

### Post by ngrundy on 2006-10-18
Are there any older OS that would work better? I don't need the latest and greatest...I mean, I have been running Win ME...anything would be better than that!

---

### Post by kidders on 2006-10-18
> **ngrundy said:**
> Are there any older OS that would work better? I don't need the latest and greatest...I mean, I have been running Win ME...anything would be better than that!Lol :( Poor Bill would be devastated to hear you say that!

If you like Ubuntu and you're worried about performance, I suggest throwing on the server version and manually installing older versions of the more demanding packages, like desktop environments. Alternatively, you could limit yourself to things like Xfce/Enlightenment/etc. that will run happily in low-spec environments with limited disk space.

Other possibilities include distros like Gentoo, that would happily let you block new (more demanding) versions of things, and configure an "odd", customised system, tuned specifically to your own PC. This option's not for the faint-hearted though! Gentoo is very, very nice, but *not* newbie-friendly.

In either case, you should be able to build yourself a system that won't bloat out of all control or crawl along like a drunk snail ... *and* keep your Windoze for stuff you have that might not get along too well with Linux.

Incidentally, just to be safe, can I ask whether you're sure your PC can support a half a gigabyte of RAM?

**Edit:** Just in case it's relevant, I have an old 600MHz PIII (256MB RAM, 300GB HDD) with Gentoo on it. Despite the fact that I've spent a *lot* of time tuning it, today's hardware requirements are a big ask for it :-( It can be quite slow performing I/O operations, for instance. That's what I'm basing my performance concerns on, so feel free to say "bah humbug" and disregard them :-) You might not feel the comparison is valid.

---

### Post by louieb on 2006-10-18
I have Ubuntu Dapper running on two PC's that I had to use the boot floppy in order to get the install CD to boot. One is a P2 400 w/384 mb ram the other a P3 w/256 mb ram. Ubuntu run just fine on both. Altho the P2 is faster I guess its the extra 128 mb ram.

The P3 is my Linux play box I have it booting Ubuntu, Slackware, Xubuntu, Puppy and Zenwalk linux. I have given each distro 5 gig of hard drive space and they share 512 meg swap space.

If you want to see fast try Puppy linux it blow all the others away.

Right now I'm trying to get Gentoo linux installed but what a hassle. 

But personally Ubuntu is my favorite just becauce it was easy to set up and for the most part it works without having to do any tweeking. Not to mention that this forum is one of the best.

---

### Post by ngrundy on 2006-10-19
I looked into it and dell and every other memory dealer on the net says that my machine can take two sticks of 256 mb ram. It isn't the most common or inexspensive, but if it keeps me happy for another couple of years...it will save me from buying a whole new unit. 

But now, back to one of your comments. Should I really keep windows. I could understand if it was XP, but ME!!! My goal is pretty simple, find an os that WORKS and I don't pay a fortune for. Like I said earlier, I don't do much on my computer. Internet, music, some office applications and that is about it...

If I have to do a dual boot on my HD (10 gb) then I will probably just give up on ubuntu. Can I pay my bills on line with it? Use my HP digital camera? My lexmark 2300 scanner/printer. Do I have to get special virus protection that is compatible? I am trying to make my life easier, I don't want to have to spend time fixing little things. If that's what I am getting into, I don't see the point.

You're right though, this is a very good forum. One of the better ones on the net.

---

### Post by confused57 on 2006-10-19
If your bank or payees support Firefox, you won't have any problem online bill paying.  You probably won't be able to get your Lexmark printer working in Linux, Lexmark offers almost no Linux support...I hope I'm wrong, but that's what I've read from other posters.  HP and Epson  seem to offer the best Linux support...I have an old HP 810C deskjet that works great.

---

### Post by Bushfire on 2006-10-20
Yeah, I don't know much about Linux distributions, but one thing I do know is that ME is the worst OS I have ever used. I'm sure you could find at least a lightweight window manager that would work on your machine at any rate.

---

### Post by wpshooter on 2006-10-20
Ngrundy:

Are you saying that you can NOT set your CD as the first boot device in BIOS ???

P.S. - Is this the only computer you have ?  Or do you have another computer available to you that can get access to the internet ?

---

### Post by ngrundy on 2006-10-24
I don't have another computer at home. I could borrow one from work to get internet access. I could reset the BIOS if I new how... Any knowledge of step by step instructions?

Thanks

---

### Post by kidders on 2006-10-25
Resetting your BIOS won't be much help. Your original post gave the impression it doesn't support booting from a CD though ... is that true? (Your computer would have to be quite old!)

---

### Post by ngrundy on 2006-10-25
I don't think it is too old. Purchased new in 2001 so it should work. Since my last response I have read some pages from folks who have done this very thing. I think I will give it a go once I upgrade my memory.

Keep an eye out, I'll post my progress.
thanks

---

