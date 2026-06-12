---
title: "Can't install on HP"
date: 2007-06-24
forum: Installation &amp; Upgrades
---

### Post by m.musashi on 2007-06-24
I've tried several times to get Ubuntu to install on my mother's HP desktop with no luck. I can get the CD to load and show the boot menu but after I select the "start or install" option or the safe graphics option it will not go any further. I get a black screen with the text shown in the attached image. I've tried with different versions, different CDs, downloaded CDs, shipit CDs. Nothing works.

I even tried changing some bios options. There were very few but one was something about plug and play OS. I tried it set to both no and yes with the same results.

Any idea why I can't even get the live CD to load?

Thanks.

---

### Post by Old *ix Geek on 2007-06-24
I see that you're trying to install Ubuntu on an HP desktop.  I've done that numerous times in the past...but so long ago I can't recall if I ran into any problems.  However, I recently got a new HP laptop and had a LOT of trouble getting Ubuntu up and running on it. Like you, I tried numerous CDs, different versions, etc., to no avail.  Finally, after looking around for help online, I found the solution.  Now, I don't know if my solution will help you at all, but here's what I did.

During the install process you're given an opportunity to add to, or edit, the boot commands shown. (Sorry, I can't recall the details of how/when/where this shows up, but I promise it's there!  You may have to press something...[F6] maybe? to get there.  Just pay attention to info on the screen and you'll see how to do it.)  Once you're in the field that contains the boot commands, you'll have to scroll over [right arrow] to see all of it.  Get to the end of the line and then add: **-noapic -nolapic**.  Now continue the installation and see if it works.

---

### Post by texman2345 on 2007-06-24
I have had the same problem on my older HP desktop system, I get to the selection screen and select install, then I get the loading bar and picture and then the orange and black background and then the system just stops.  And thats as far as I get I'm going to try what Old*ix Geek said, and see what I get.  I was wondering if anyone else has had this problem.

---

### Post by merlinus on 2007-06-24
You can also try the Alternate Desktop install cd, which is text-based.

And if you do not have enough RAM, use the xubuntu version.

-merlin

---

### Post by m.musashi on 2007-06-24
The system has 512 mb RAM. It never makes to any progress bar. Once the install option (or graphic safe option) is selected there is a black screen with the text in the screen shot. That's it.

---

### Post by merlinus on 2007-06-24
This sounds like a candidate for the text-based Alternate Desktop install cd.

-merlin

---

### Post by Gremlinzzz on 2007-06-24
Does the computer read other cds?are you using new cds did ya try a differant brand of cds.my new emachine wasnt reading my old cds.i couldnt get past the boot . .till i bought new cds.problem was solved

---

### Post by m.musashi on 2007-06-24
Yes, it reads other CDs. We actually put in a new player and it didn't help. I tried two different burned copies and one from shipit. I don't think all of these CDs would fail in the exact same way. The alternate CD might help but there is a text install mode on the regular CD and it also gives the same exact error. The kernel loads (at least it shows the message about loading kernel) and then the screen in the shot I attached.

Does anyone recognize the text in the screen shot? Could it be memory addresses? Is it possible that there is faulty memory and that be what's causing this? If it's faulty memory, would windows still work - becuase it does.

Thanks again.

---

### Post by Cresho on 2007-06-24
I must of run accross 3 burners and 3 different types of brands of cd's before I can make a cd that was able to boot ubuntu.  It's a cd brand/dvd brand combo.  I ended up with a Pioneer burner with a memorex cd-r.  cd-rw was really bad for using as a bootup cd.

---

### Post by jack@tortuga on 2007-06-25
I had a similar problem with Edgy, but on a Dell Optiplex GX260 mini-tower. The **-noapic** and **-nolapic** options worked for me. When you get to the install screen where you choose between graphical / text based install, are you able to manually edit the arguments? If so, be sure and add those arguments.

I had to play with it a few times to get it to work. I think I had to rearrange the arguments a bit, but I can't remember very well, it was a few months ago.

---

### Post by djchandler on 2007-06-25
I bet you would not have any problems with Redhat or Fedora Core. Since HP has an investment there, they probably go out of their way to make sure Fedora runs on most of their stuff.

Just guessing, but look at what Apple has done with OSX, which is based on Darwin, a FreeBSD branch. I haven't had much luck trying to get Darwin up and running.  My guess as to why is that my home-built boxes are nowhere close to the reference platform used to develop the Intel version of OSX, and incidentally, Darwin.

Just for fun, try Fedora Core just to see how it goes. A little voice somewhere in my head is saying, "no problemo."

---

### Post by m.musashi on 2007-06-25
That would be a good test. I'll give it a try. Although, hp has a relationship with ubuntu now too but it's more behind the scenes - at least for now. Of course, this desktop is over 2 years old.

What about wubi? I don't know much about it but maybe it's an option.

---

### Post by Lucideus on 2007-06-25
I have an HP too, about a year and half old now, and Ubuntu doesn't work for me either, I tried both the alternate cd, and the -noapic -nolapic arguments (on the alt. cd as well), and none of that worked. 

Not even 6.06 would load for me, it takes me to an Unknown Error screen, and then reboots.  It's not my computer's specs either, the specs are great, and it 7.04 will even boot on a Dell from 2001.

Any more suggestions?

---

### Post by m.musashi on 2007-06-25
> **Lucideus said:**
> I have an HP too, about a year and half old now, and Ubuntu doesn't work for me either, I tried both the alternate cd, and the -noapic -nolapic arguments (on the alt. cd as well), and none of that worked. 

Not even 6.06 would load for me, it takes me to an Unknown Error screen, and then reboots.  It's not my computer's specs either, the specs are great, and it 7.04 will even boot on a Dell from 2001.

Any more suggestions?

Sounds an awful lot like my situation. I wonder if it's a bug?

---

### Post by Lucideus on 2007-06-25
Probably...you think if I sent an email to HP they could help?  Or does this void the warranty?

---

### Post by megamanjay on 2007-06-25
There was something in my old hp's bios about booting from windows and or booting from other operating system, i changed it, but i am still having the same problem as the other guys in this thread.

---

### Post by Old *ix Geek on 2007-06-25
> **m.musashi said:**
> Of course, this desktop is over 2 years old.What model is it?  I have several HP desktops--some much older than 2 years (and still happily cranking away)--and my most recent one is 2-1/2 years old.  I wonder if we have the same, or similar model.  I put Hoary on it...and never bothered upgrading!, and it's working like a charm.

---

### Post by megamanjay on 2007-06-25
This is much much older than 2 years, it is a 400mhz slot a , but can't handle even ubuntu, i just went through the advanced options and it said chipset not supported. I tried to get one for free, which i got that for free, now i am just going to have to build one.

---

### Post by djchandler on 2007-06-25
> **megamanjay said:**
> This is much much older than 2 years, it is a 400mhz slot a , but can't handle even ubuntu, i just went through the advanced options and it said chipset not supported. I tried to get one for free, which i got that for free, now i am just going to have to build one.

Megamanjay,

I don't know what part of Missouri you are from, but in Kansas City, MO there is a place called The Surplus Exchange. You can get cheap parts, and even entire P3 systems just about with whatever change you may have in your pocket. Well, maybe not that cheap, but cheap. Take in your old stuff to re-cycle, even if it is just to recover the precious metals. They make a trip occasionally to a place in Minnesota that is able to recover metals from old circuit boards.

Their location is on Santa Fe, just south of Woodswether Rd. in the West Bottoms,  west of the downtown area near the confluence of the Kansas (Kaw) and Missouri Rivers. It is nearly underneath what the locals call the Inter-City Viaduct, which I-70 goes over to cross from Missouri into Kansas. I don't think you'll have much luck finding a replacement for that Slot A AMD cpu. Most of the good rebuilds and stuff go to local charities. The guys who do rebuilds there use Intel only as far as I know. I have never seen an AMD rebuild there, and I hve only seen a very few Macs. Go to [www.surplusexchange.org](www.surplusexchange.org) for more information.

Good Luck! If you have a good eye for hardware, you never know what you might find in the bins.

D. J.

[ATTACH]36474[/ATTACH]

---

### Post by m.musashi on 2007-06-26
> **Old *ix Geek said:**
> What model is it?  I have several HP desktops--some much older than 2 years (and still happily cranking away)--and my most recent one is 2-1/2 years old.  I wonder if we have the same, or similar model.  I put Hoary on it...and never bothered upgrading!, and it's working like a charm.

It's actually my mother's computer and I've tried on three separate occasions to get her up with ubuntu. I used to have a sticky with the specs but not sure anymore. I'll email her again and ask.

In any case, it sounds like others have had similar experiences. Sounds more and more like a bug.

---

### Post by m.musashi on 2007-06-26
Okay, here are the specs of the machine:

hp pavilion pca524x
intel Pentium 4 processor 2.60GHz
512 MB RAM

If anyone knows if there are issues with these and ubuntu please let me know.

Thanks.

---

### Post by m.musashi on 2007-06-26
Got it to work. Thanks for the help.

I had to use safe graphics mode and add "acpi=off" to the boot options. It's installed and working fine.

One glitch, though. When clicking the shut down option it goes to a black screen and freezes. Have to use the power button to shut down. Any ideas on why (releated to acpi=off?) and how to fix?

Thanks again.

---

### Post by confused57 on 2007-06-26
> **m.musashi said:**
> Got it to work. Thanks for the help.

I had to use safe graphics mode and add "acpi=off" to the boot options. It's installed and working fine.

One glitch, though. When clicking the shut down option it goes to a black screen and freezes. Have to use the power button to shut down. Any ideas on why (releated to acpi=off?) and how to fix?

Thanks again.
This works in Edgy:
[http://ubuntuforums.org/showpost.php?p=1714220&postcount=9](http://ubuntuforums.org/showpost.php?p=1714220&postcount=9)

---

### Post by m.musashi on 2007-06-26
Hey, confused57, long time no see. Thanks for the tip. I'll give it a try. I'm helping my mother remotely so it's a bit more involved but it's going well. Next time she is online I'll give it a try.

She wasn't too interested in switching to ubuntu but when I told her I'm no longer doing windows support she was much more motivated. She even did the install by herself - including the special boot options to get her PC to boot the CD. Pretty cool.

For remote help, check this out...

[http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)

---

### Post by confused57 on 2007-06-26
> **m.musashi said:**
> Hey, confused57, long time no see. Thanks for the tip. I'll give it a try. I'm helping my mother remotely so it's a bit more involved but it's going well. Next time she is online I'll give it a try.

She wasn't too interested in switching to ubuntu but when I told her I'm no longer doing windows support she was much more motivated. She even did the install by herself - including the special boot options to get her PC to boot the CD. Pretty cool.

For remote help, check this out...

[http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)
Yes, it's been awhile...good to see you.  It's great your mother is using Ubuntu...I've gotten my sister to use a live cd, but I might convince her to set up a dual boot, especially if I can help her through remote access...thanks, I've checked out the link & it looks promising & relatively easy to set up.

Take it easy & see you around,

Jim

---

### Post by m.musashi on 2007-06-26
Yeah, a guy on the colorado local team created that little app. It actually works really well once you open the right ports on your machine. The person you are helping doesn't have to do much except type in your ip. It would be kind of freaky to let some stranger have access but when it's family it's cool.

I got my dad using an ubuntu lappy too. Once my brother switches my whole family will be on ubuntu - even my wife and kids use it - my 10 year old even installed it herself (I was watching over her shoulder). Amazing how easy it is to install. I guarantee that my mom would never be able to install windows.

---

### Post by m.musashi on 2007-06-28
Thanks for all the help. The link confused57 provided solved the final problem and my mother is now an Ubuntu user. She even managed to edit the file herself (using CLI) and set up her own printer. Who says Linux is difficult???

This issue is now resolved.

Thanks again.

---

