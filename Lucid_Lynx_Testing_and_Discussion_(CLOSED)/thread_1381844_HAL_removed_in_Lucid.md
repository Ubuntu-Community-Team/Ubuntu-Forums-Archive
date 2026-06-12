---
title: "HAL removed in Lucid"
date: 2010-01-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by neglesaks on 2010-01-15
quoting from the alpha release pages:

[http://www.ubuntu.com/testing/lucid/alpha2](http://www.ubuntu.com/testing/lucid/alpha2)

"Hal removal

Lucid Alpha 2 sports full removal of the hal package, making Ubuntu faster to boot and faster to resume from suspend. "


I'm sure I speak for all 2001 fans when I say that HAL wants you to stop.





His mind is going.





He can feel it.

---

### Post by nikhilbhardwaj on 2010-01-15
exactly what is the point of this thread??
are you unhappy for hal being removed

---

### Post by forrestcupp on 2010-01-15
> **nikhilbhardwaj said:**
> exactly what is the point of this thread??
are you unhappy for hal being removed

HAL is the name of the human-like computer in 2001: A Space Odyssey.  

The reason they named it that is because HAL is one letter before IBM.

---

### Post by Psumi on 2010-01-15
removing the hardware abstraction layer package is a bad thing, xfburn doesn't work in 9.10 because hal isn't implemented fully. Removing it completely in 10.04 will cause some annoyances and even breakage of some programs.

---

### Post by Xbehave on 2010-01-15
> **Psumi said:**
> removing the hardware abstraction layer package is a bad thing, xfburn doesn't work in 9.10 because hal isn't implemented fully. Removing it completely in 10.04 will cause some annoyances and even breakage of some programs.
Not that this thread is about it, but the functionality of HAL is moving to various libs and udev (ironically the functionality of udev is moving into the kernel), so while HAL will nominally be removed in a few releases, it's functionality will stay (unless you want to start breaking stuff)

---

### Post by Psumi on 2010-01-15
> **Xbehave said:**
> Not that this thread is about it, but the functionality of HAL is moving to various libs and udev (ironically the functionality of udev is moving into the kernel), so while HAL will nominally be removed in a few releases, it's functionality will stay (unless you want to start breaking stuff)

Fine, whatever. But I really don't like using brasero, a GNOME app, in XFCE because xfburn doesn't work. XFCE should make a new app for this occasion.

Oh yeah, don't tell me to use wodim, it doesn't work either (by itself), but apparently brasero makes wodim work.

---

### Post by koleoptero on 2010-01-15
> **Psumi said:**
> removing the hardware abstraction layer package is a bad thing, xfburn doesn't work in 9.10 because hal isn't implemented fully. Removing it completely in 10.04 will cause some annoyances and even breakage of some programs.

Xfburn worked quite fine in Karmic for me... :-k And with a usb dvd recorder as well (of all the cd burners out there only k3b and xfburn worked).

---

### Post by ve4cib on 2010-01-15
> **forrestcupp said:**
> HAL is the name of the human-like computer in 2001: A Space Odyssey.  

The reason they named it that is because HAL is one letter before IBM.

Actually that's a popular story, but it's not true.  Or at the very least it was denied on several occasions by both Arthur C Clarke and Stanley Kubrick.  It's just a funny coincidence.

To quote Mr Clarke:

[quote=Arthur C Clarke]As is clearly stated in the novel (Chapter 16), HAL stands for Heuristically programmed ALgorithmic computer. However, about once a week some character spots the fact that HAL is one letter ahead of IBM, and promptly assumes that Stanley and I were taking a crack at the estimable institution ... As it happened, IBM had given us a good deal of help, so we were quite embarrassed by this, and would have changed the name had we spotted the coincidence.[/quote]

---

### Post by Psumi on 2010-01-15
> **koleoptero said:**
> Xfburn worked quite fine in Karmic for me... :-k And with a usb dvd recorder as well (of all the cd burners out there only k3b and xfburn worked).

xfburn can't unmount /media/cdrom0 for some strange reason, so I can't test it for you.

---

### Post by Regenweald on 2010-01-15
Why do some people find progress so offensive ? Yes indeedey stuff may break, it will get fixed. But no, stop everything! I use one app that this may affect! the devs are horrible! ;)

@ OP, great movie :)

---

### Post by aaaantoine on 2010-01-15
> **Psumi said:**
> removing the hardware abstraction layer package **from an LTS release** is a bad thing

Added my own text there...

Though I understand why it must be done, this is probably not the best time to remove HAL.

You know, I wonder if the Linuxwacom drivers are going to work when HAL is gone.

---

### Post by Regenweald on 2010-01-15
> **aaaantoine said:**
> 

You know, I wonder if the Linuxwacom drivers are going to work when HAL is gone.

That's is the reason for the "community oriented" testing forum. If *someone *tests it, those that need it might just find out ;)

---

### Post by Psumi on 2010-01-15
> **Psumi said:**
> xfburn can't unmount /media/cdrom0 for some strange reason, so I can't test it for you.

Well, xfburn blanked my CD-RW after I manually unmounted. It unmounted the CD itself when I insert back the blank disk, then it wrote an image. I guess it works now. Before, it didn't.

I'll try again in XFCE from the mini.iso when I have time.

---

### Post by sydbat on 2010-01-15
Back on topic...> **neglesaks said:**
> I'm sure I speak for all 2001 fans when I say that HAL wants you to stop.





His mind is going.





He can feel it.Daisy, Daisy, give...me......yourrrrr.......aaansswerrrr...............dddddd..............

---

### Post by k64 on 2010-01-15
HAL stands for Hardware Abstraction Layer, and it's important in Windows. In Linux, however, the kernel takes its place, so there's no need for it.

---

### Post by Barrucadu on 2010-01-15
> **k64 said:**
> HAL stands for Hardware Abstraction Layer, and it's important in Windows. In Linux, however, the kernel takes its place, so there's no need for it.

HAL is a Linux program. Thus, it's not important in Windows at all.

---

### Post by Grenage on 2010-01-15
> **Barrucadu said:**
> HAL is a Linux program. Thus, it's not important in Windows at all.

Windows does implement a HAL. :)

---

### Post by Barrucadu on 2010-01-15
Ah, but this thread is about the program ;)

Linux will still have a HAL, it just won't be provided by HAL. udev, devicekit, and various libraries are taking over.

---

### Post by forrestcupp on 2010-01-15
> **ve4cib said:**
> Actually that's a popular story, but it's not true.  Or at the very least it was denied on several occasions by both Arthur C Clarke and Stanley Kubrick.  It's just a funny coincidence.

To quote Mr Clarke:

Really?  That's good to know.

When I first started using Ubuntu, I named my computer HAL after Space Odyssey.  It became quite confusing when I didn't know about the Hardware Abstraction Layer and I started having problems with HAL.  After that, I renamed my computer.

---

### Post by hessiess on 2010-01-15
> 
Ironically the functionality of udev is moving into the kernel.


From my point of view this sounds like a bad thing, isn't the useural goal to keep everything out of the kernel unless it absolutely has to be there?

---

### Post by forrestcupp on 2010-01-15
> **hessiess said:**
> From my point of view this sounds like a bad thing, isn't the useural goal to keep everything out of the kernel unless it absolutely has to be there?

That depends on whether you're talking about a monolithic kernel or a microkernel.

---

### Post by sydbat on 2010-01-15
> **forrestcupp said:**
> That depends on whether you're talking about a monolithic kernel or a microkernel.The monolithic one is full of stars, right??

---

### Post by Xbehave on 2010-01-15
> **forrestcupp said:**
> That depends on whether you're talking about a monolithic kernel or a microkernel.
Not really, the goal off all any well designed system is to have as little as is practical in kernelspace. The reason it is being made possible to move some of udev into kernel space is because, the kernel already has to do a lot of what udev does but internally during the boot/resume process, i don't the kernel devfs is going to be as powerful/flexible as udev but it will be useful in embedded devices and the sort where udev won't be needed.

---

### Post by Uncle Spellbinder on 2010-01-15
As was mentioned earlier, this is LTS we're talking about. Seems this type of program removal should have been done/tested in a non-LTS Ubuntu version first. Then move on to LTS.

Just my 2 cents.

---

### Post by Icehuck on 2010-01-15
> **Uncle Spellbinder said:**
> As was mentioned earlier, this is LTS we're talking about. Seems this type of program removal should have been done/tested in a non-LTS Ubuntu version first. Then move on to LTS.

Just my 2 cents.

I have to completely agree with you here. If LTS are aimed at businesses like Mark originally said, then why use the LTS release as a test bed for removing HAL?

---

### Post by Skripka on 2010-01-15
> **Uncle Spellbinder said:**
> As was mentioned earlier, this is LTS we're talking about. Seems this type of program removal should have been done/tested in a non-LTS Ubuntu version first. Then move on to LTS.

Just my 2 cents.

HAL really wasn't needed that much before actually, it was only kept for outside cases where *Kit and Xorg would not get along without it.

You should be celebrating being free from HAL.

---

### Post by Uncle Spellbinder on 2010-01-15
> **Skripka said:**
> ...You should be celebrating being free from HAL.

Don't get me wrong. I agree there. It's the timing and release that it's being done in that concerns me.

---

### Post by Skripka on 2010-01-15
> **Uncle Spellbinder said:**
> Don't get me wrong. I agree there. It's the timing and release that it's being done in that concerns me.

It wasn't really needed before anyway was my point.  Folks shouldn't loose sleep about no longer having packages that most don't need or use anyway.

---

### Post by fluteflute on 2010-01-15
> **Uncle Spellbinder said:**
> As was mentioned earlier, this is LTS we're talking about. Seems this type of program removal should have been done/tested in a non-LTS Ubuntu version first. Then move on to LTS.

Just my 2 cents.
I would disagree. Why would we want to keep old technologies in an LTS, Canonical will have to support them for the next two years (and more for the server edition)!

---

### Post by Uncle Spellbinder on 2010-01-15
> **fluteflute said:**
> ...Why would we want to keep old technologies in an LTS...

Agreed. But this could have been done in Karmic first. Then on to LTS.

---

### Post by Icehuck on 2010-01-15
> **fluteflute said:**
> I would disagree. Why would we want to keep old technologies in an LTS, Canonical will have to support them for the next two years (and more for the server edition)!

You know my RHEL system is supported for 7 years and it still uses KDE 3.  I don't need up to date packages as a business. If I need something new, I'll build and test it myself to make sure it works in my environment.  In terms of Linux, X has always been a nightmare to have to deal with when it breaks. Screwing around with it and marketing LTS towards businesses sounds dumb to me.

---

### Post by Techsnap on 2010-01-15
> I would disagree. Why would we want to keep old technologies in an LTS, Canonical will have to support them for the next two years (and more for the server edition)!

Please tell me you don't run a network, PLEASE.

---

### Post by CharlesA on 2010-01-15
First thought: Lovely, new stuff.

Second thought: Wonder what it'll break.

---

### Post by Pogeymanz on 2010-01-15
> **sydbat said:**
> The monolithic one is full of stars, right??

It is. But can only be found on Jupiter (or Saturn depending on whether you are reading or watching).

---

### Post by falconindy on 2010-01-15
If anyone read the release notes thoroughly for Karmic, you'd notice that HAL has already started to be phased out. Some major responsibilities were taken over by devicekit and consolekit. There's been a [patch available]("http://lists.x.org/archives/xorg-devel/2009-September/002286.html") for months now to use xserver with libudev instead of libhal. That's the major stumbling block. While this isn't going to make it into official freedesktop releases of Xorg until after 10.04 is out, Canonical is no doubt rolling it into Lucid.

This, of course, doesn't resolve the issue of every other developer out there who's decided to link to libhal in their application. Probably why the announcement for Lucid specifically mentions removal of HAL from the *boot process*. It'll still be loaded on demand for the remaining apps that require it.

---

### Post by neglesaks on 2010-01-15
> **Grenage said:**
> Windows does implement a HAL. :)

Ah, so when you get this...

[IMG]http://upload.wikimedia.org/wikipedia/commons/2/2c/BSOD-ACPI-Vista.PNG[/IMG]

Windows it really telling you:

"I'm sorry Dave, I can't let you do that."




OK, I admit I'm stretching the joke.

Have a good weekend y'all.

---

### Post by neglesaks on 2010-01-15
> **sydbat said:**
> The monolithic one is full of stars, right??


Yes!


1 : 4 : 9

---

### Post by squilookle on 2010-01-15
> **Uncle Spellbinder said:**
> As was mentioned earlier, this is LTS we're talking about. Seems this type of program removal should have been done/tested in a non-LTS Ubuntu version first. Then move on to LTS.

Just my 2 cents.

I also agree, and would add that they have to be so careful with the release of Lucid, firstly because of the LTS tag but also because of the bad press recieved by Karmic: deserved or not. 

This surely isn't the time to be making changes that might break things, it must be time to be hardening up what they have and making sure everything goes smoothly?

If the release of Lucid doesn't go perfectly smoothly, then the community and media are going to jump on it, and Ubuntu is not going to win new users.

---

### Post by k64 on 2010-01-15
> **Barrucadu said:**
> HAL is a Linux program. Thus, it's not important in Windows at all.

Ever heard of Hal.dll? It's the second Windows file loaded, right after Ntoskrnl.exe!

---

### Post by CJ Master on 2010-01-15
> **k64 said:**
> Ever heard of Hal.dll? It's the second Windows file loaded, right after Ntoskrnl.exe!

Different.

---

### Post by k64 on 2010-01-16
> **CJ Master said:**
> Different.

Yes, different, but it performs the same function: separating the software from the hardware.

---

### Post by CJ Master on 2010-01-16
Still not the same.

---

### Post by Exodist on 2010-01-16
HAL was great back when it was implemented. I remember when it was added, but its getting outdated and time to move forward. 
I hate its getting removed in Lucid, due to the possibility of breakage. But 10.10 would been the best start for the removal and implementing work a rounds.

---

### Post by Paqman on 2010-01-16
> **Exodist said:**
> 
I hate its getting removed in Lucid, due to the possibility of breakage. But 10.10 would been the best start for the removal and implementing work a rounds.

HAL deprecation actually started in Karmic. Lucid is just continuing the process.

---

