---
title: "Ubuntu 10.04 LTS intall stalled"
date: 2010-07-25
forum: Installation &amp; Upgrades
---

### Post by kajankow on 2010-07-25
I am trying to install Ubuntu on this partition I have for Ubuntu. Sorry if the pictures are bad quality.

[ATTACH]164516[/ATTACH]

The green section is the partition I created for Ubuntu. So I choose the specify partition manually.

[ATTACH]164517[/ATTACH]

So then I would guess I choose /dev/sda2 and click forward but I get this error.

[ATTACH]164518[/ATTACH]

So I selected the partition and clicked change. 

[ATTACH]164519[/ATTACH]

What am I supposed to do after that? And do I change the mount point? I gave me several options. If y'all need any more pictures or info or questions I will try my best to help you help me.

---

### Post by RTrev on 2010-07-25
In your second picture, where it's listing the three partitions, click on the ext3 one and then the "Change" option at the bottom will become active.  At that point you specify that you want to use the partition, and that the mount point will be / 

I think it's there that you can also tell it to make it ext4, if you want that, and to format it.  Wish I had another machine in front of me that I could play with, but I think the key is to highlight the partition you're interested in so that the options become active down below.

You should probably create a swap partition also, and do the same thing.. click on it, pick Change, tell it to use the partition and that it will be swap area.  I think the usual rule of thumb for the size is to make it roughly double the size of your RAM.

Hope this helps more than confuses! Hard to remember without it in front of me.

---

### Post by kajankow on 2010-07-25
Where does the swap partition go? In between windows and ubuntu or at the end or it does not matter? And is it necessary?

---

### Post by RTrev on 2010-07-25
> **kajankow said:**
> Where does the swap partition go? In between windows and ubuntu or at the end or it does not matter? And is it necessary?

As far as I know, it doesn't matter where it goes.  I've heard people ask if it's essential, and the replies always seem to be that it's a really bad idea to not have one.  If you're low on memory, you would need one, and I believe if you hibernate or suspend the system, that's where data is written.  There may be other reasons.

Maybe someone more knowledgeable will jump in and answer that for us both.  I'm also not at all versed in Windows, so am not sure what potential problems you might have with GRUB2 booting Windows.  I know many people do this, but I'm not sure how.  Might be best to make sure you're clear on those kinds of details before doing something like this.  Just a thought.

---

### Post by kajankow on 2010-07-25
Oh yeah I know. I totally crashed my hard drive last time. I was using GParted and it gave me an error and my hard drive got bad sectors and wouldn't be recognized. I do not wanna go any further before having to do more hardware stuff. 

And I do not hibernate or suspend all that much. Just shutdown or close the lid and leave it running. So I guess I don't need the swap partition.

---

### Post by RTrev on 2010-07-25
Here.  This might be helpful.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

May the force be with you. ;)

---

### Post by kajankow on 2010-07-25
Yeah see that is the guide I used to do everything before my hard drive crashed and burned. Thanks though.

---

### Post by RTrev on 2010-07-25
> **kajankow said:**
> Yeah see that is the guide I used to do everything before my hard drive crashed and burned. Thanks though.

No way to know what happened then, but I'd guess you had a hardware problem that was independent of this procedure.  Just a guess, though.  I've used gparted many times to create, delete, move, resize, etc., partitions, and never had any problems at all.

It's also possible that there are bugs in gparted that bite when confronted with a disk like yours, but not with one like mine.

I have no clue.  Hopefully someone smarter should wander by soon.

---

### Post by kajankow on 2010-07-26
Well thanks for all your help and input. Much appreciated.

---

### Post by kajankow on 2010-07-26
Hey I took some more screen shots. Maybe this will help you help me. I added a swap partition and moved my original ext3 partition for ubuntu to the right and shrunk it down just a tad. 

[ATTACH]164583[/ATTACH]

And since I never really got this far successfully before I did not know what this was. I think its to help move some of my pictures and stuff I have in Windows. I do not need anything moved over so I will assume I just do not click on anything. Right?

[ATTACH]164584[/ATTACH]

And here is the last part of my question? What do I do (if anything) with the advance options in the install part? do i just leave it as is or do i select the ubuntu partition or my Windows one or what? 

[ATTACH]164585[/ATTACH]

Thanks in advance.

---

### Post by RTrev on 2010-07-26
> **kajankow said:**
> And since I never really got this far successfully before I did not know what this was. I think its to help move some of my pictures and stuff I have in Windows. I do not need anything moved over so I will assume I just do not click on anything. Right?

Right.  I've always copied anything I wanted before doing the install, so have never done anything at this screen except ignore it.

> And here is the last part of my question? What do I do (if anything) with the advance options in the install part? do i just leave it as is or do i select the ubuntu partition or my Windows one or what?

Well, like I said, I never used Windows.  Sounds like you're past the part that blew up your drive last time, so I think you should probably go back to following that guide again.

The way I (mis?)understand it, you're going to want to put GRUB2 on the MBR of the first drive, and it will handle all booting of operating systems from then on.  So it will take over the MBR which Windows currently has control of.  I don't think you need to go into the advanced area at all.

Probably best to wait for someone who's done this to come along and help if you're uncertain.

I got lucky and moved right from DOS to VMS on big systems, and when people were talking about switching to Windows in a production environment I wished them well and retired. <g>

Played with Linux a bit since, but never done anything with Windows except scrape it off drives before installing an OS in its place.

I know that doesn't help much, but I'm explaining why I can help only so far.  I'll shut up now and let someone else take over.  Good luck.

---

### Post by kajankow on 2010-07-26
Well thanks for all your help. Really appreciated. Could someone else please help me?

---

### Post by kajankow on 2010-07-26
Hey I saw this article/step-by-step guide and it semi-answered my question.

[http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml)

It is about the boot loader. Do I just let it be or select the partition that has ubuntu or something else? In the article it said if you were to install it to a flash drive then select the flash drive. But the flash drive would only have one partition. Can someone answer that question for me?

---

### Post by kajankow on 2010-07-27
I am still stuck and do not know what to do. 

[ATTACH]164626[/ATTACH]

I do not know what to select or if to select anything? I found this guide and he has a great tutorial but he is using two hard drives and I have one and he is installing ubuntu on the other one. [http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/~herman546/p24.html") 

Can some one please help me answer this question so I can have my computer up and running for school in a few weeks. Thanks in advance again.

---

### Post by kajankow on 2010-07-27
Can someone please answer my question from my previous post? To restate it: What do I select/install the boot loader? Is it the whole drive or just the partition that has the partition setup for linux? Or do I skip the advance section and it will know what to do for the dual boot?

I would really like to setup my ubuntu and install all the necessary programs I need for school. Thanks in advance and sorry if this seems like whining or bumping, I just really need this for school.

Thanks to wojox for answering my question in another thread. For those who need help with the same question you pick the partition that Ubuntu was for.

---

