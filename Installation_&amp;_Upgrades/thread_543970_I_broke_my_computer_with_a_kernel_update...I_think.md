---
title: "I broke my computer with a kernel update...I think!"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by bean77 on 2007-09-05
So as one of my guy friends says, "This is why girls shouldn't build computers".  LOL...I really did it this time.  As far as I can tell I screwed something up with the most recent kernel update in Feisty.  My keyboard and mouse stopeed working and then started working again.  My monitor was no longer recognized and then would work intermittently.  I said "forget this!"  (well, I used a different phrase) and wiped my hard drive and went to install Windows XP.  Had a plethora of issues there that I don't know the cause of.  

Everytime I booted up, my computer would get to the windows logo and then reboot itself.  Over and over.

Wiped the hard drive again.  Went back to Ubuntu.  (I like it way better than Windows)  Now I am itrying to reinstall from the CD (which I checked the integrity of, says it's fine) and I get the CRC error.

I called the motherboard manufacturers and yelled at them and they are sending me a new one but what can I do in the meantime?  I can navigate throughout BIOS no problem.

PLEASE HELP A GIRL OUT!

---

### Post by Pumalite on 2007-09-05
[http://en.wikipedia.org/wiki/Cyclic_redundancy_check](http://en.wikipedia.org/wiki/Cyclic_redundancy_check)

I would say a bad burn. Check md5sum on iso, burn at 4x. check CD for corruption during burn before install. Also check your burner, clean lens, etc.

---

### Post by bean77 on 2007-09-05
OK, you need to talk to me like I'm a 2 year old b/c I am very new at all of this.  What does that mean?  I have done a search on the error and the kernel update that has broken other people's systems.  However what I really need is for someone to walk me through how to fix this.

Thanks in advance!

---

### Post by bean77 on 2007-09-05
I just tried to turn on the computer and the monitor is not even being recognized.  Maybe I'll try it again in a few...

---

### Post by Pumalite on 2007-09-05
See my editing above and also take the time to read my link carefully.

---

### Post by bean77 on 2007-09-05
> **Pumalite said:**
> I would say a bad burn. Check md5sum on iso, burn at 4x. check CD for corruption during burn before install. Also check your burner, clean lens, etc.

I checked it and it said it was fine but I will burn another one just to be safe.

---

### Post by bean77 on 2007-09-05
> **Pumalite said:**
> See my editing above and also take the time to read my link carefully.

Still not getting it.  I read the link and I understand a little bit but I don't know how to fix my computer when the monitor isn't even getting detected.  Now I can't even do anything.  I'm on my husband's laptop.

---

### Post by Pumalite on 2007-09-05
Looks like you need a hardware repair. Or you are trying to install, finished the install and ended up without an xserver. What is it?

---

### Post by bean77 on 2007-09-05
OK, I started it up again and it is working.

Should I boot from the new CD and just start all over?

---

### Post by bean77 on 2007-09-05
> **Pumalite said:**
> Looks like you need a hardware repair. Or you are trying to install, finished the install and ended up without an xserver. What is it?


It **was **the latter and I was not expereinced enough to know what the problem was or how to fix it so I just dug myself in deeper and deeper until I got fed up.  Hindsight is 20/20 and had I known at the time, I would have reverted to an earlier kernel.

I'm wondering if I should set up a dual boot system so I can use Windows as well as Ubuntu (which I love).

---

### Post by Pumalite on 2007-09-05
Do you need Windows?. If you don't; ditch it. You can install Ubuntu. Just give me your specs, what kind of iso you downloaded and burned and I'll take you from there.

---

### Post by bean77 on 2007-09-05
I don't really need it.  I've been Windows-free for almost 6 months now, LOL.

I'm burning the alternate install CD as someone suggested in another thread.  It's really slow so it'll be a while.  With my current Ubuntu CD I got all the way to the main menu where I had the option of just starting up, checking the CD's integrity, etc., etc.  Should I have done something different there?

---

### Post by bean77 on 2007-09-05
> **Pumalite said:**
> Do you need Windows?. If you don't; ditch it. You can install Ubuntu. Just give me your specs, what kind of iso you downloaded and burned and I'll take you from there.

My specs...hmmm...let me think.

Motherboard:  MSI PM8PM-V
Hard Drive:  Western Digital SATA 
Video Card: Nvidia GE Force 6500 (I think)
Processor:  Intel Pentium 945
CD/DVD:  Hewlett Packard

---

### Post by Pumalite on 2007-09-05
You are doing great. I'll give you a link to a guide: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu](http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu)

Let me know if you need more guidance. (Going to dinner now. Be back in an hour)

---

### Post by bean77 on 2007-09-05
> **Pumalite said:**
> You are doing great. I'll give you a link to a guide: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu](http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu)

Let me know if you need more guidance. (Going to dinner now. Be back in an hour)


You rock-thanks!

I have to go put my little ones to bed...be back in a bit!

---

### Post by bean77 on 2007-09-05
CD is fine, works in other PC's.  Still getting the CRC error.

Grrrr...

---

### Post by Pumalite on 2007-09-05
Sorry, but I'd say clean or replace you CD-DVD.

---

### Post by bean77 on 2007-09-05
Running Memtest86 right now and going to bed...

Hopefully I'll have an answer tomorrow.  Thanks for checking in!

---

### Post by bean77 on 2007-09-05
OMG, the screen is almost all red with errors...should I swap out the memory?

---

### Post by Pumalite on 2007-09-05
Memory errors are usually one or two here and there and that after hours of testing, so, could you explain a little bit more what happened?

---

### Post by bean77 on 2007-09-05
It showed over 500,000 errors and it just kept going.

OK, I really have to get to bed.  My babies are up at 5 am!

Thank you again and I hope I get this fixed with your help!

---

### Post by bean77 on 2007-09-06
Rebooted after the bazillion errors, monitor didn't work.  Shut down for the night last night and this am booted up and monitor is fine, keyboard doesn't work.  Restarted and got the crc error -- system halted.

---

### Post by bean77 on 2007-09-06
Anyone?

---

### Post by bean77 on 2007-09-06
I am testing each stick of RAM now.

---

### Post by Pumalite on 2007-09-06
How are you doing?. I'm back. Let's see if we can take this to the end.

---

### Post by bean77 on 2007-09-06
Tested one stick of RAM, got no errors after 7 cycles.  Rebooted with the new CD and got to the startup screen.  Selected "Check CD for errors" and did NOT get the error message but it just sort of hung forever and I can't look at my computer anymore tonight.  Suggestions for tomorrow?

If I were to do a dual boot, should I install Windows first?

---

### Post by Pumalite on 2007-09-06
Obviously one stick of RAM was bad. Now, maybe memory is insufficient. How much memory do you have now?. If you think this is an Ubuntu issue, I think you are wrong; so don't run to Windows just yet. It seems you can see your monitor now; at least at the beginning of the installation?

---

### Post by bean77 on 2007-09-06
> **Pumalite said:**
> Obviously one stick of RAM was bad. Now, maybe memory is insufficient. How much memory do you have now?. If you think this is an Ubuntu issue, I think you are wrong; so don't run to Windows just yet. It seems you can see your monitor now; at least at the beginning of the installation?

Each stick is 1 GB.  Yes, I can see the monitor now.  It's been hit or miss so I'm not sure what the issue is behind that one.  What do you think?

At least I'm not getting any errors!

---

### Post by Pumalite on 2007-09-06
You are far better off now. 1 GB of memory is enough. What are you trying to install now: Live CD or Alternate?. And how far do you get?. Any error messages?.

---

### Post by bean77 on 2007-09-06
> **Pumalite said:**
> You are far better off now. 1 GB of memory is enough. What are you trying to install now: Live CD or Alternate?. And how far do you get?. Any error messages?.

Live CD right now.  No messages but it hangs after selecting the "check CD' prompt" and "install" options.  I haven't gotten much further since I left my desktop a while ago and am on my laptop now watching Big Brother.

---

### Post by Pumalite on 2007-09-06
Next time you are in the mood try Alternate CD now that you have good memory (a working system)

---

### Post by bean77 on 2007-09-07
Tried the alternate CD a little while ago, choosing the install option and the check CD for errors options brings me to a blank screen with a blinking cursor in the upper left corner.

Should I use a command line?

---

### Post by bean77 on 2007-09-07
Holy crap, I fixed it!

Now I just need to start from scratch.

---

### Post by Pumalite on 2007-09-07
Let us know how you fixed it.

---

### Post by bean77 on 2007-09-07
I *think* I used the "rescue a broken system" feature.  It was very early this morning and I had not yet had my coffee.  Out of desperation I was just randomly selecting options.

My motherboard is still not detecting my video card but I should have a new mobo by Monday.  Not a huge deal-I can still get by without the video card at this point.

---

### Post by Pumalite on 2007-09-07
Great; you have a working system AND Ubuntu. Congrats.

---

### Post by debianchick on 2007-09-08
> **bean77 said:**
> I *think* I used the "rescue a broken system" feature.  It was very early this morning and I had not yet had my coffee.  Out of desperation I was just randomly selecting options.

My motherboard is still not detecting my video card but I should have a new mobo by Monday.  Not a huge deal-I can still get by without the video card at this point.

> 
Great; you have a working system AND Ubuntu. Congrats.Maybe not, and if the ones who tried to help done their home work (sorry I know that is a four letter word to some of you LOL) You would have found that a lot of other people have had problems with getting Linux running. It Is true that some Microstar (MSI) motherboards you can run Linux on there are some that you can't or you really need to work at getting Linux working.The board you have is one them. My suggestion is that you return it and get one that is known to be good for Linux. Check out the ones on _[Linux Compatible]("http://www.linuxcompatible.org/compatlistcat20-1-1-1.html")_ or just get an ASUS  motherboard, I never had any trouble with getting Linux running on them. 





OT,BTW, about your guy friend, the one who thinks that woman should be building computers, Next time he brings that subject up (I have a feeling it is all most all the time. ;-)) hears is something that might keep him quiet. Print it out and put it some where he is likely to see it. The fridge would be perfect!! LOL 

[CENTER]

Great woman in computing history 

Grace Hopper pioneer of computer science 
  She is reason for high level programing and she 
   was one of the first software engineers. But what 
she is best known for is the program compiler. 

Fran Allen, she won the most highest prize in 
Computer Scientist the Turing Prize. She laid the 
foundation for the modern optimizing compilers

This should hopefully keep him quiet  LOL[/CENTER]

---

### Post by bean77 on 2007-09-08
> **debianchick said:**
> Maybe not, and if the ones who tried to help done their home work (sorry I know that is a four letter word to some of you LOL) You would have found that a lot of other people have had problems with getting Linux running. It Is true that some Microstar (MSI) motherboards you can run Linux on there are some that you can't or you really need to work at getting Linux working.The board you have is one them. My suggestion is that you return it and get one that is known to be good for Linux. Check out the ones on _[Linux Compatible]("http://www.linuxcompatible.org/compatlistcat20-1-1-1.html")_ or just get an ASUS  motherboard, I never had any trouble with getting Linux running on them. 





OT,BTW, about your guy friend, the one who thinks that woman should be building computers, Next time he brings that subject up (I have a feeling it is all most all the time. ;-)) hears is something that might keep him quiet. Print it out and put it some where he is likely to see it. The fridge would be perfect!! LOL 

[CENTER]

Great woman in computing history 

Grace Hopper pioneer of computer science 
  She is reason for high level programing and she 
   was one of the first software engineers. But what 
she is best known for is the program compiler. 

Fran Allen, she won the most highest prize in 
Computer Scientist the Turing Prize. She laid the 
foundation for the modern optimizing compilers

This should hopefully keep him quiet  LOL[/CENTER]

Love this!  (Oh, and he is totally kidding when he says it)

Good tip on the motherboard.  I apparently didn't do my homework on the components beforer I built my computer but in my defense, I had every intention of doing Windows and I had never even heard of Ubuntu before I built it. :-)

---

### Post by laidback on 2007-09-09
Wow what a trial. But you are getting there. Comments from debianchick seem very apt. Just think how much you are learning through this problem. I'm so pleased to read that you have continued with Ubuntu despite your current problems. And you've made quite a few contacts from the Forum, I wish you every success.

---

### Post by bean77 on 2007-09-09
> **laidback said:**
> Wow what a trial. But you are getting there. Comments from debianchick seem very apt. Just think how much you are learning through this problem. I'm so pleased to read that you have continued with Ubuntu despite your current problems. And you've made quite a few contacts from the Forum, I wish you every success.

The only reason I have stuck with Ubuntu is b/c of these forums.  The people are so helpful and there is *literally* never an issue that I have the someone else hasn't already had and been able to supply the answer for.  I belong to MANY message boards (on crafting, parenting, baby-wearing, women in business, etc.) and this is **BY FAR** the most helpful and _least_ snarky of them all.

---

### Post by laidback on 2007-09-09
You echo my thoughts. For reasons that I will not bore you with I can be easily put off, particularly by nasty and uncalled for comments. The Ubuntu forum has been a life line for me in my quest for a Linux installation. Long may this continue.

---

