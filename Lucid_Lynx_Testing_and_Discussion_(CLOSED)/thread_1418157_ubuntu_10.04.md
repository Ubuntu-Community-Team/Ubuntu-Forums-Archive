---
title: "ubuntu 10.04"
date: 2010-02-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by graafjd on 2010-02-28
I have upgraded ubuntu 9.10 to 10.04 without any problems.
After the reset the ubuntu 10.04 hangs with the messages "Waiting for /media/sdb1 [SM]
 
nothing further happens.
 
Can anyone help me with this error ?
 
Thanks already

---

### Post by gallifrey on 2010-02-28
Do you have an external device, such as an external hard drive or USB stick attached?
sdb1 would seem to suggest it is waiting for another SATA device to initialise or mount.

---

### Post by ikt on 2010-02-28
> **graafjd said:**
> I have upgraded ubuntu 9.10 to 10.04 without any problems.
After the reset the ubuntu 10.04 hangs with the messages "Waiting for /media/sdb1 [SM]
 
nothing further happens.
 
Can anyone help me with this error ?
 
Thanks already

Any reason why you're using an alpha of the next version of ubuntu?

I would stick to 9.10 or 9.04.

---

### Post by Yogotiss on 2010-02-28
Yeah you have to remember that 10.04 is still in development so any bugs you may encounter you are for the most part stuck with unless an update has been released or you manually patch yourself.

---

### Post by bodhi.zazen on 2010-02-28
Moved to testing.

Where is your Ubuntu installation ? What is /media/sdb1 ?

---

### Post by AlanR8 on 2010-02-28
> Any reason why you're using an alpha of the next version of ubuntu?

I ran Karmic from Alpha 3 and Lucid from Alpha 2. I like being on the cutting leading bleeding edge and am prepared to accept the consequences! They can be breakages, black screens, frequent re installations but do you know what.....It doesn't matter!

All my files are on DropBox so backing up's not an issue. My mail is g Mail so again, no data loss. The only files I have to copy back from my server are my music files. No issues.

---

### Post by phenest on 2010-02-28
I smell a troll.

---

### Post by Merk42 on 2010-02-28
> **AlanR8 said:**
> I ran Karmic from Alpha 3 and Lucid from Alpha 2. I like being on the cutting leading bleeding edge and am prepared to accept the consequences! They can be breakages, black screens, frequent re installations but do you know what.....It doesn't matter!

All my files are on DropBox so backing up's not an issue. My mail is g Mail so again, no data loss. The only files I have to copy back from my server are my music files. No issues.
But gallifrey was asking graafjd, not you :confused:

> **phenest said:**
> I smell a troll.
Really? Why? I would think if the OP instead of saying "Can anyone help me with this error ?" said something like "A SIMPLE UPGRADE AND IT BREAKS?? UBUNTU IS CRAP AND NOT READY FOR THE DESKTOP", then I would think it to be a troll.

---

### Post by phenest on 2010-02-28
> **Merk42 said:**
> Really? Why? I would think if the OP instead of saying "Can anyone help me with this error ?" said something like "A SIMPLE UPGRADE AND IT BREAKS?? UBUNTU IS CRAP AND NOT READY FOR THE DESKTOP", then I would think it to be a troll.

Because they claim to have used Ubuntu before but this is their 1 and only post, yet possess enough knowledge to upgrade to an alpha. Uninformative title too.

---

### Post by haydoni on 2010-02-28
> **phenest said:**
> i smell a troll.

+1

---

### Post by AlanR8 on 2010-02-28
> But gallifrey was asking graafjd, not you


Humble apologies.....................................

I thought my contribution was valid regarding the issue of running Alpha software.....

---

### Post by cariboo on 2010-02-28
> **phenest said:**
> I smell a troll.

Please don't call people trolls just because of their join date and post count. There are many people that lurk the forums, feeling there is no need to register, as they find answers to their questions without having to do so. 

I did the same thing for a couple of years.

---

### Post by innersund on 2010-03-01
Why the original poster is characterized as a troll escapes me, and it is definitely not the right way to treat people who are willing to try out alfa's and beta's and report problems. The main effect has been to divert the discussion.

Now back to what this thread should be about: I have the same problem intermittently after upgrading to 10.04 (and applying all updates). First thing upon boot is to show a black screen with "Waiting for /sda [SM]" (I may remember wrongly about the "/sda") and at the bottom a thick white line across the screen. The disk activity light is constant on. I have left the computer like that for several hours without anything happening. I think (but am not sure) that it only happens upon cold boot. Upon pressing the reset button the computer goes into normal boot. There is no trace of the event in /var/log/messages. My computer is a i586 with 4 internal IDE disks attached. With 9.10 there was no such problem. And I do not expect the Ubuntu developers to scramble to help me, but I will be glad to provide more info about the incident if I can.

---

### Post by ikt on 2010-03-01
> **innersund said:**
> Why the original poster is characterized as a troll escapes me, and it is definitely not the right way to treat people who are willing to try out alfa's and beta's and report problems. The main effect has been to divert the discussion.

I wouldn't say they're a troll, just mis-guided.

---

### Post by bodhi.zazen on 2010-03-01
I am going to close this thread now. We have not heard back from the OP and the thread has degenerated into an off topic discussion as to if there is "trolling".

---

