---
title: "Dual Boot Corrupted - Bad Power Supply"
date: 2008-07-25
forum: Installation &amp; Upgrades
---

### Post by Poodle Doodle on 2008-07-25
:idea:

Hello there I thought I should winge first, and get everyone else to do my thinking for me....


No serious.

Ummmmm I have a computer, with a formerly working dual boot.

The GRUB worked just fine, UNTIL my progressively fickle power supply kept on cutting out every few seconds - here or there during the boot process (LONG story sorting this out), instead of random times... and....

The beastly power supply has been tossed and a new one put in.

The next issue - is that the grub boots OK... gets to here:

rc-default main process (4885)** terminated with status 127

(** may not be right number)

And halts.

So with the first major series of attempts, the culmination of this, was that I tried removing the Ubuntu partition, only to remove the "guts" of the GRUB. Then I had fun and games (more learning expereinces) reinstalling grub, and the Ubuntu OS, into tit's former partition...

And I kind of got it all back to just the halt.

The HDD layout is like this

Disk 0 - has Ubuntu and 2.5G swap file.

Disk 1 - Has XP.



Now the LIVE CD does work and run the whole system... GREAT...

I "think" ](*,) that there is a "crack" ???? in the programming - to make the jump ???? from the last stages of booting up and the Ubi files starting to run the OS, and the OS actually working.


So I want to get the Ubi partition working, and then I want to do some smart disk imaging, and copy my entire hard drive, and all it's partitions over to a larger and defect free HDD.

So I have searched the site with these terms:

Need to fix dual boot

I have found about 250 results... and on the law of averages, there is probably about 3,000 plus A4 pages of writing in them all....

And I think there absolutely has to be a solution, if not several in amongst it all.

And I am sure that if I actually go look into these forums, instead of crying into my keeyboard "Woe is me - it's all to hard - my brain hurts etc"...
That I will find the solution and if not the first time, I will certainly find the solution by the 100th time....

And I will become enormously smarter and more capable for doing so, which I will sort of mostly forget withing days and weeks...

I honestly think the ONLY way to become an expert is to DO what it takes to become an expert, by GETTING results, instead of expecting other people to come up with them, for me.

I kind of don't want to make the situation worse, or take weeks of time to get a "fix"....

I could use some help with this...

But I am quite capable of sorting this out - "Eventually"... I can book mark the search results page, email it to myself, and then log out on this PC and go online with the laptop and then fiddle away with the main computer... and it's programming.

I have had rescue part working, with the manuals running, and SUDO working...

So Ubuntu is there and it's working.. it's just not "quite" switching on, as an OS (well according to me that is) 


However I am prepared to forgo the learning I would have obtained if I had of gotten off my **** and solved the problem myself... in lieu of the benefits of expediency - in solving the problem.

Either way, any help would be appreciated.

PD.

---

### Post by zxscooby on 2008-07-25
Maybe you should search using the error message that you got 
instead of just "need to fix dual boot".

Did you plug everything in right when you replaced the power supply? Most of the time when something works before you
replace hardware and it doesn't work afterwards something wasn't
done properly.

---

### Post by Sef on 2008-07-25
Get [Super GRUB Disk]("http://www.supergrubdisk.org/").  It will easily install GRUB.

---

### Post by Poodle Doodle on 2008-07-25
No the original power supply was "faintly hissing and crackling" = BAD inter intermittent fault.

Bad intermittent fault, crashed computer multiple times, during boot / reboot cycles, when away from PC.

Crash and rebooting corrupted Ubuntu bootup.

GRUB is fine - moves through the boot stage, into either OS.

The XP bootup - fine.

Ubuntu - is where the flaw is.

I will however investigate the Super GRUB, and I will use better / smarter search terms.

Thanks.

PD.

---

