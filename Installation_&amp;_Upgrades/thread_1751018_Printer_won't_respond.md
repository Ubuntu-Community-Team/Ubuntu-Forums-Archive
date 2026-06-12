---
title: "Printer won't respond"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by J.D on 2011-05-06
I've upgraded to 11.04 and all works well except for the printer. It won't print.

I've checked admin>printing and the printer is ticked. And  admin>printing>server>printer>new>find network printer  and it's there.

If I click print preview it shows up also.

It's not a printer issue per se as I also have XP and the printer works fine with that  O.S. As it did in Ubuntu until I upgraded to 11.04.

Any thoughts appreciated.

J.D

---

### Post by mörgæs on 2011-05-07
You will give yourself a better chance of getting an answer is you mention which printer we are talking about, for example in the thread title.

---

### Post by zippy_uk_2001 on 2011-05-08
Getting something similar with an HP 2610 wired network printer (after going to 11.04)

Go HPLIP print manager installed, but it's can't find the printer - although it is looking on the correct address (can ping it etc. everything is where it should be).

There's a loop going on...
[list]
[*]It can't find the printer, 
[*]After about 30 seconds it picks it up on it's own and starts the print job
[*]another 30 seconds it then says the print job is completed (although nothing has printed)
[*]Then 30 seconds later brings up a default 'cannot communicate with the printer' error and we start the loop again.
[/list] 

There don't seem to be any printer related updates that I can see.

Tried deleting and re-adding, although when re-adding I don't get my printer listed, I have to add it manually. 

I seem to remember that you can print from the command line - I'll see if I can get the syntax for that working and will update.

As mine is a network printer and I'm getting comms problems, it would seem to be more network than print drivers, but I'll have a play and share what I find in case anyone else gets the same.

Cheers
Ash

---

### Post by zippy_uk_2001 on 2011-05-08
USB printing works ok, so in my case at least, this is something network related it would seem.

Trying to print through CUPS, see if that chucks up anything new ...although CUPS is playing hard to get right now :-)

- Ash

---

