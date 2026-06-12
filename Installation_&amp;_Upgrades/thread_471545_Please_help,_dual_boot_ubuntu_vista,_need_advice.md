---
title: "Please help, dual boot ubuntu vista, need advice"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by Eoghanalbar on 2007-06-12
I made a post [Dual boot ubuntu and vista (1 harddrive). General questions, and a procedure to check]("http://ubuntuforums.org/showthread.php?t=471433")
Nobody answered my post, and already it's passing into obscurity. How can I modify the way I ask questions to get better results? Oh, and some answers to those ones would be nice if you have them.

---

### Post by bscbrit on 2007-06-12
You made your original post 4 hours ago, and nobody has yet answered it?  Have you tried waiting until someone is able to do so?

---

### Post by bscbrit on 2007-06-12
> A. Read my files whether I'm in ubuntu or vista. To what extent and can I make it work both ways, or, if only one way, which? Are there different ways of doing this? I really don't want to have to switch back and forth to get documents I wrote or music or whatever.

If you format your Vista partition as NTFS then you will be able to both read and write to it using experimental software (i.e. possible data corruptions) or use it as read-only using tried and tested software drivers which are automatically included with Ubuntu.  However, installing ANY Microsoft software on a computer that already has Ubuntu installed will cause Windows to overwrite your Grub loader.  Microsoft refuse to acknowledge that there are any other OS in existence and assumes that its software can have complete control over the computer and its storage.  Search the threads for ways to overcome this.

> B. Get rid of vista and take over that space if I want to at some later time. By just taking over the partition it was on, or could I get rid of that partition and extend the one my files are on to fill up that space?

It is simply a matter of reformatting the partitions used by Vista and remounting them under Ubuntu.

> C. Easily fix some problem arising from misallocating space to the partitions when I first install? Do I have to be careful setting it up so that I don't run into trouble installing some big program on either OS?

Providing that you provide sufficient space for the Vista installation then you should have no problems from 'miscalculating space'.  If Vista says it needs 10 Gb (or whatever) then give it that plus 50% and you should be good to go.  There are no guarantees though, I cannot say how Vista installs and what its storage requirements are.

> Using the ubuntu live CD and the Toshiba recovery disks, rather than a plain vista disk. Does anyone know if that'll cause problems?

Using a recovery disk will probably remove everything that is currently on the drive and return the drive to the condition that it was when you purchased the computer.

I hope this helps but please remember my earlier post.  Waiting 4 hours is insignificant.  But if you would rather pay me to provide advice to you then you will find my rates very competitive and I will try to answer within an appropriate timeframe.

---

### Post by Eoghanalbar on 2007-06-12
Ah, sorry. I was under the impression that once a post has been bumped off first page of the list it becomes pretty unlikely that anyone would ever see it. And I read a lot of people saying stuff about how many "zero reply requests for help" there are. I guess it's kinda hard to get attention without ticking people off :p

But thanks for the correction. I'll avoid doing it again.

Also, thanks for the help. I'll look into NTFS.

---

### Post by bscbrit on 2007-06-12
I always scan the 'unanswered posts' when trying to find someone to help.  I suspect that many others do the same but I confess that I rarely get past page 4 or 5 so, if your request ever reaches there without a response then you would probably be justified in reposting it.  While I understand how you feel it is unlikely that complaining that a post has not been answered will ever get you a sympathetic response.  However, in this case there are no hard feelings but I wouldn't want others to see your complaint and think that is the way to get a quicker service.

Another problem is to do with timezones.  As I do not know where you are I cannot make any clear suggestions but the fact that it is a certain time of day where you are does not mean that those who provide the help on the forums are sat in front of their computer screens trying to find people to help.  Many have jobs, a family life and other interests to balance with their time online, but they will help whenever they can.

But you asked for suggestions on how to rephrase your questions.  The most important way that you can help yourself is to search previous threads thoroughly before asking your questions.  There are numerous posts on dual-booting, reading and writing to NTFS drives and recovering the Grub loader after Windows has eaten your previous version.  In the top right of almost every forum page is a search box.  If, for example, you type in 'NTFS' and press the 'Go' button you will find numerous posts of which a good few are seeking - and finding - help with problems such as your own.

In fact, the only original question that you asked was one that I cannot answer - 'how much space does Vista need and how much space will I need for other programs?'.  I have never used Vista, and probably never will, so I haven't a clue.  Perhaps Googling will provide an answer.  How much space do you need for other programs? - I don't know, what are they, how big are they and how much data do you wish to store?

Still, as I have said, I hope that I have provided enough to help you overcome your next hurdle and please don't go away thinking that no-one here wants to help.  Ubuntu has been very successful over the last couple of years and the number of users, and the number of queries has grown tremendously.  Unfortunately, the number of people providing help hasn't grown quite as quickly.  But this is still the best forum for linux that I have ever seen.  On the plus side, the majority of questions that new users ask (say during their first year of using Ubuntu) have been asked before and the answer is already on the forum for those that take the time to search.  Good Luck. :p

---

