---
title: "Please Help!  Random Crash Problem!!"
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by derhoward on 2011-04-03
Hi all!  I posted this in the General Help section and didn't receive very much help.  

I don't consider myself a complete stranger to Ubuntu as I first tried it two years ago and loved it. I had to switch back to Windows for a long time because of school work that was not linux compatible. I recently had a major crash with Windows and finally did a full install of 10.04. All was fine, the only real issues were the splash screen not fitting my resolution but other than that, it was perfect. 

I upgraded to 10.10 about a week ago and it looks stunning. the splash screen is now completely gone and has been replaced by a very ugly black screen with the Ubuntu 10.10 in a blocky font that's either white, yellow, or purple. 

On top of that, my laptop crashes randomly. It will just stall for a second and then go to a solid black screen like it's in hibernation mode. I then have to restart the computer all over. Sometimes, after a restart, my close/minimize/maximize buttons and the title bar of the application disappear. 

Can anyone take a shot at what this may be, or point me to where I should move this to to get help?

I'm using a Gateway NV73A06u with an AMD Athlon IIX2 processor.

---

### Post by Hedgehog1 on 2011-04-03
derhoward,

If it's OK - the things you are describing lead me to ask some questions to try and track this thing down.

The display you are seeing at boot-up may be a red-herring on a system that has Shared Video Memory. When the driver takes over the memory, any old data in that area make these funny looking displays.  This does not guarantee there are no memory issues. 

First, please check the current health of you hard drive.  To do this, menu to System >> Administration >> Disk utility.

There is a nice disk health display here.  The picture below is of a BAD disk:

[IMG]http://img146.imageshack.us/img146/7057/diskfail03.png[/IMG]

I am hoping you do not see anything like this - we are hoping for a 'drive is healthy' report.

Next is to do a memory check.  This can be done from the grub menu:

[IMG]http://img860.imageshack.us/img860/5730/small37grub2ndtime.png[/IMG]

If these both pass muster, please report back and we will follow with video driver checking.

***The Hedge***

:KS

---

### Post by Rasa1111 on 2011-04-03
(edit: oh wow, hedgehog to the rescue!) lol
Ok so, someone has answered! :P )

Im sorry man,
 Im really not sure whats happening..
 Ive only seen 9.10 and 10.04 crash like this,,
but never 10.10.

 i just saw this was unanswered so wanted to help by bumping it to the top.

You say 10.04 didnt crash like this?
but only had that small graphics/splash issue?

---

### Post by Hedgehog1 on 2011-04-03
I am a ***rescue Hedgie***,* Rasa1111*!

My hope is to determine if *derhoward* issues are because of beginning-to-fail hardware.  If the hardware checks out, then next step is the video driver *derhoward* is using.  If both seem OK, we will see about moving him back to 10.04.02 LTS.

***The Hedge***

:KS

p.s. *Rasa1111*, are you REALLY on the International Space Station?  And of so what is your Internet speed like up there?

---

### Post by derhoward on 2011-04-03
Thank you both for answering me and trying to help!  
 
I'm currently performing the memory test as the hard drive came back spotless and clean.  the memory test is at about 49% complete and still no errors.  
 
Could something have gone wrong in the upgrade?  I installed 10.10 from the Update manager rather than a full wipe of my hard drive, then install.  
 
Thank you guys again in advance!

---

### Post by derhoward on 2011-04-03
I just completed the memory test and it came back clean as well.

---

### Post by Rasa1111 on 2011-04-03
@ Hedge~
good plan! :)

> p.s. Rasa1111, are you REALLY on the International Space Station? And of so what is your Internet speed like up there?

haha!
Only on Mondays through Fridays. ;) lol
Today is Sunday.. So I'll be heading back up later tonight. :P

Re: Internet speeds~
Well, it's no fiber optics, and we certainly don't get 30 megabits/per second as some people like to think. 

> The internet access is provided through the Crew Support LAN on the ISS - this is connected to the ground using the Ku-band service on NASA's Tracking and Data Relay Satellite System. **This is capable of 25 megabits upstream (to space) and 300 megabits downstream bandwidth**, although the service is shared with other NASA and Department of Defense spacecraft.

Because the TDRSS satellites are in geosynchronous orbit, the round-trip time to and from the ISS is about 500ms.

Although, 
 We have to connect to a desktop in Houston via remote connection. :/
[http://www.universetoday.com/51782/iss-now-has-live-access-to-the-internet/](http://www.universetoday.com/51782/iss-now-has-live-access-to-the-internet/)

:lol:  ;)

**@ derhoward~**~
Good news! :)
Thanks for the update!

Ok,
So you acquired 10.10 through upgrade rather than install..

 Which has me wondering..
If maybe.. Somehow.. Some of the "funkyness" with graphics cards in 10.04, Somehow "transfered over" or "stayed" when you upgraded to 10.10. 

Ive never done an upgrade, only fresh installs..
So I cant really say...
But it just seems odd that you first had 10.04 (which gave me some of the same problems you mention), which now seem to have stayed with (and gotten worse) in 10.10.. which I have never seen have these problems.

  I do think that you downloading and burning a copy of 10.10 onto a disc, and trying that out, would be worth a try. 

Like I said..
 I don't know much about upgrades and all the troubles one may encounter with them... Though I have often read that the majority of folks prefer to install fresh from a CD, rather than doing the 'upgrade", as there always seems to be less troubles/problems that way.

So to my ignorant mind.. It does seem that there was a problem somewhere with the upgrade itself. But what do i know? Ive only been using Ubuntu for a year. lol

So anyway..that is what I do..
Fresh installs always, no problems yet. *knocks on wood*. lol

Good luck man,
you'll get squared away here soon, I can feel it! lol :)

---

### Post by derhoward on 2011-04-03
@Rasa1111,

Thank you very much!  One thing that I've learned is that the Ubuntu community is much more friendly and responsive than that of the Windows community.  

Back in '09, I upgraded from 9.04 to 9.10 and had a few hiccups but I chalked it up to my desktop at the time being very old and inefficient.  I think I'll take a day and back everything up, take note of what apps I've got installed and do a fresh install.  10.04 was working flawlessly, aside from the splash screen and I believe something went haywire in the upgrade.  

Thank you both very much for your input, it was extremely helpful!

---

### Post by Rasa1111 on 2011-04-03
> **derhoward said:**
> @Rasa1111,

Thank you very much!  One thing that I've learned is that the Ubuntu community is much more friendly and responsive than that of the Windows community.  

Back in '09, I upgraded from 9.04 to 9.10 and had a few hiccups but I chalked it up to my desktop at the time being very old and inefficient.  I think I'll take a day and back everything up, take note of what apps I've got installed and do a fresh install.  10.04 was working flawlessly, aside from the splash screen and I believe something went haywire in the upgrade.  

Thank you both very much for your input, it was extremely helpful!

No problem my friend. 

 I agree!
I don't even remember how many times I had a problem with windows, and didnt know what to do.. So I wold seek out help online... and never once.. Was I supplied with an answer that was actually helpful. 

 I guess this helped teach me a bit more about windows,
having to rely on myself to fix the problems, because the windows community was never helpful.. So i guess it was ok...
 But still.. Once I found this Linux community...
 I was amazed! lol  <3

 I also tried to use Ubuntu some years ago. (7.10)
But ran into some problems, and I also chalked it up to my PC not being able to handle it, (and also all the FUD I would read saying "it's soo hard", difficult to learn )etc. lol

So, I figured, "eh, well, I tried, guess it's just not for me"
So stayed with my crappy XP.

 Suffered with that until 9.10 came out, and decided I couldnt handle it anymore, Im trying Ubuntu again!

 I had a better PC by then, and 9.10 booted and installed perfectly,
 So i used it for 5 or 6 days via liveCD, and decided it was time to install, and kill windows.

This was a little over a year ago, and Ive been using Ubuntu, and nothing  but, ever since. 

Your plan sounds like a good one!
The same route I would take in your shoes. :)

 Good luck, 
Im looking forward to you being all set! :)

---

### Post by Hedgehog1 on 2011-04-03
> **derhoward said:**
> I just completed the memory test and it came back clean as well.

Glad to hear you PC is healthy.  *Saves Money!*

Isn't **Rasa1111** the nicest astronaut you even meet? ('Astronaut' is different from 'space cadet', by the way!)

This is a really nice community, too!

***The Hedge***

:KS

---

