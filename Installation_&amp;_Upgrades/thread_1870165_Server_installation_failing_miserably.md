---
title: "Server installation failing miserably"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by malcmail on 2011-10-26
After using goold old fashioned 10.04 desktop on my "server" it started to show some signs of falling apart as it tried to update the kernel this week. So I decided to scrap another PC together and install the server edition on it. The PC is currently only running 1GB of RAM on a P4 processor but shouldnt have a huge strain placed on it.

SO installation seems to go fine and then its time to reboot. All I get is a black screen with a blinking cursor. Utterly nothing happening. No booting, no nothing! And I mean nothing. I've tried simple partitioning, manual partitioning, installing fewer components etc. But still nothing. It would be fair to say its driving me to drink!!

ANyone got any ideas as to what I've managed to do wrong / what I need to do to get past the blinking cursor?

Thanks in advance.

---

### Post by collisionystm on 2011-10-26
> **malcmail said:**
> After using goold old fashioned 10.04 desktop on my "server" it started to show some signs of falling apart as it tried to update the kernel this week. So I decided to scrap another PC together and install the server edition on it. The PC is currently only running 1GB of RAM on a P4 processor but shouldnt have a huge strain placed on it.

SO installation seems to go fine and then its time to reboot. All I get is a black screen with a blinking cursor. Utterly nothing happening. No booting, no nothing! And I mean nothing. I've tried simple partitioning, manual partitioning, installing fewer components etc. But still nothing. It would be fair to say its driving me to drink!!

ANyone got any ideas as to what I've managed to do wrong / what I need to do to get past the blinking cursor?

Thanks in advance.

Yeah... you sir need to check  your BIOS and change the boot order.

Lets experiment.. Ill pretend its a dell because it probably is. Reboot your machine, it the F12 key at the bios screen to choose the boot manager. Choose the hard disk. Does ubuntu boot?

Do you ever see the ubuntu splash?

---

### Post by malcmail on 2011-10-26
> **collisionystm said:**
> Yeah... you sir need to check  your BIOS and change the boot order.

Lets experiment.. Ill pretend its a dell because it probably is. Reboot your machine, it the F12 key at the bios screen to choose the boot manager. Choose the hard disk. Does ubuntu boot?

Do you ever see the ubuntu splash?


Haha. It ain't no Dell (don't talk to me about those lol). The machine in question used to run FreeNAS, albeit from a CF card in an IDE adapter. The boot order is CD then HDD (which ic actually an IDE drive from a SATA socket - can you tell its thrown together!!).

If I pull the cable to the drive I at least get told theres no boot file and get sent to the grub rescue prompt. But I dont even get that far if I leave the drive plugged in.

---

### Post by collisionystm on 2011-10-26
> 

If I pull the cable to the drive I at least get told theres no boot file and get sent to the grub rescue prompt. But I dont even get that far if I leave the drive plugged in.


Okay...

so you turn off the computer, un plug the hard drive, start it up and still get a grub prompt??? 

And your computer does not sound TOO bad. It could be worse!

---

### Post by malcmail on 2011-10-26
> **collisionystm said:**
> Okay...

so you turn off the computer, un plug the hard drive, start it up and still get a grub prompt??? 

And your computer does not sound TOO bad. It could be worse!

Haha. How did you get that pic of my PC? ;)  Now you mention it that is a bit odd but that's what's going on.

---

### Post by collisionystm on 2011-10-26
> **malcmail said:**
> Haha. How did you get that pic of my PC? ;)  Now you mention it that is a bit odd but that's what's going on.

Are you sure there are no other drives in your system? Grub has to live on something. Is there a cd in your computer?

---

### Post by malcmail on 2011-10-26
> **collisionystm said:**
> Are you sure there are no other drives in your system? Grub has to live on something. Is there a cd in your computer?


I take it back - looks like smthg was attached before as I've double checked right now, yanked everything and now its just the "Reboot and select proper boot device....." message. At least that makes more sense!

---

### Post by collisionystm on 2011-10-26
> **malcmail said:**
> I take it back - looks like smthg was attached before as I've double checked right now, yanked everything and now its just the "Reboot and select proper boot device....." message. At least that makes more sense!

Okay, now plug in just ONE DRIVE and install Ubuntu Server lol. 

It sounds like Grub wrote itself onto another drive. This happens to me. I just make sure to unplug everything but the intended drive when doing an install... I think of grub as a plague.. it is un-stoppable!!!

---

### Post by malcmail on 2011-10-26
I'll try it again tmo and see if I have any joy. Thanks for your help. After 2 means time for bed!

---

### Post by collisionystm on 2011-10-26
> **malcmail said:**
> I'll try it again tmo and see if I have any joy. Thanks for your help. After 2 means time for bed!

Good luck! its only 9:30 here lol

---

### Post by malcmail on 2011-10-27
Well clearly its not Wednesday or something!!  First time this morning and all is well. Although I now remember why I didnt use server in the first place. While the wireless works no problem during installation after reboot its down and can't find squat. Now to remember how I fixed that before.

Thanks for the help fella.

---

