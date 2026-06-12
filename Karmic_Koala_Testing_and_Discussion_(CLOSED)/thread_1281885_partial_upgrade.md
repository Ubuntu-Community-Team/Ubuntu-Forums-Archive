---
title: "partial upgrade?"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by oboedad55 on 2009-10-03
I've seen posts warning against accepting a partial upgrade. What is the reason for this? I've seen no posts explaining why this is a bad idea.

---

### Post by Mike_IronFist on 2009-10-03
> **oboedad55 said:**
> I've seen posts warning against accepting a partial upgrade. What is the reason for this? I've seen no posts explaining why this is a bad idea.

Because people don't seem entirely sure what a partial upgrade could do to your system. Check the offical Beta thread (it's stickied in this forum) for more details.

---

### Post by DougieFresh4U on 2009-10-03
> **oboedad55 said:**
> I've seen posts warning against accepting a partial upgrade. What is the reason for this? I've seen no posts explaining why this is a bad idea.

'Partial' being the keyword here. Some thing is 'missing' or not all packages are there. You will end up with a 'broken'  system. Best to wait a while and whatever packages were 'missing' will find their way to the update.

---

### Post by Tibuda on 2009-10-03
> **oboedad55 said:**
> I've seen posts warning against accepting a partial upgrade. What is the reason for this? I've seen no posts explaining why this is a bad idea.

Sometimes a partial upgrade may uninstall packages if the dependencies were not updated yet in the repos. Sometimes a package may be updated to a version incompatible with other packages. Avoid them.

---

### Post by psyke83 on 2009-10-03
There's a language problem here.

[LIST]
[*]Partial Upgrade **does not** mean "some of your system will be upgraded". 
[*]Partial Upgrade **does** mean "some packages will be removed".
[/LIST]
Due to the way that Ubuntu's build system works, the following occurs: 
[LIST]
[*]on some days, a Partial Upgrade will remove packages intentionally, such as when a package becomes obsoleted by another package. A recent example: software-store was removed in order to replace software-center, to reflect the renaming of the application.
[*]on other days, however, a Partial Upgrade will remove important or even vital packages, sometimes with catastrophic effects.
[/LIST]
Why does the latter, destructive scenario occur? Sometimes a package will depend on other packages to install correctly, or else they will get removed to keep the system consistent. Ubuntu's build system is not smart enough to realize that if package X requires package Y to install correctly, it should prevent package X from being released into the repositories until package Y is also available.

It is up to the intelligence of the user to determine this - and unfortunately, not many understand or care. This is why you have lots of warnings about the development release, and why you should always read the sticky thread (where this is explained).

---

### Post by Keyper7 on 2009-10-03
I'm waiting since yesterday morning for the dependencies to catch up... 

Very anxious, since a lot of improvements seem to be on the queue. :)

---

### Post by NRDNick on 2009-10-03
Just open synaptic, click "mark all upgrades" this will then list what is to be removed/installed/upgraded. I really believe this feature should be implemented into the update manager itself.

---

### Post by andymorton on 2009-10-03
Not knowing any better at the time I installed a partial upgrade around the time that Alpha 5 of Karmic was released. Afterwards the system wouldn't boot. I got all sorts error messages, which if I attempted to understand them, would have made my brain melt. 
I had to do a completely fresh install. :(

---

### Post by tony_clifton on 2009-10-03
I did the partial upgrade, nothing horrible has happened.  Must be my day.

---

### Post by wilee-nilee on 2009-10-03
Also if you want the full uograde after looking at what is to be removed and added run sudo apt-get dist-upgrade.

---

### Post by trulan on 2009-10-03
I think I've done three partial upgrades, and I installed Karmic somewhere around Alpha 3 or 4.  Occasionally it is necessary, as when an old package needs to go to make room for a new one.  If there's some updates you really want that are being held back, go ahead and select 'Partial Upgrade'.  But before you start installing anything, click 'details' and check which packages are being removed.  If there is only one or two, check into what they are - chances are they are being replaced by something else you are installing.  If there are more than two be very cautious.  If there are thirty of forty packages to be removed including gnome and xorg (I saw this once), then use your brains and cancel out of that upgrade.

There is still a chance of severely breaking your system even if you never run a partial upgrade (as in the boot failures of Alpha 5 era), if you happen to update at the wrong time.  But for the most part, if you check what is to be installed and pay special attention to anything that it asks to remove, you should be okay.  Well, as okay as can be expected when running a testing version of an OS.

---

### Post by Slug71 on 2009-10-03
I really hope this topic will be a sticky for 10.04. :roll:

---

### Post by DougieFresh4U on 2009-10-04
> **Slug71 said:**
> I really hope this topic will be a sticky for 10.04. :roll:

Would be nice.
There are 3 threads on the 1rst page here all with some sort of 'partial upgrade'  questions (drama)

---

### Post by oboedad55 on 2009-10-04
> **DougieFresh4U said:**
> Would be nice.
There are 3 threads on the 1rst page here all with some sort of 'partial upgrade'  questions (drama)

Well, it does seem to be a not so easy question to answer.[-X

---

### Post by DougieFresh4U on 2009-10-04
> **oboedad55 said:**
> Well, it does seem to be a not so easy question to answer.[-X

partial upgrade? no!
Not trying to be funny :)
That's one of the reasons why I don't use 'Update Manager'. 
I like to use the terminal for updating, and when I see some thing for removal, I just abort until I investigate.

---

### Post by oboedad55 on 2009-10-04
> **DougieFresh4U said:**
> partial upgrade? no!
Not trying to be funny :)
That's one of the reasons why I don't use 'Update Manager'. 
I like to use the terminal for updating, and when I see some thing for removal, I just abort until I investigate.

That's a good point. When I started with Linux there wasn't much in the way of gui programs. I think I've gotten too dependent on them recently. When I see "Partial Upgrade", it looks like "Warning, Will Robinson!". It's hard not to push that button!

---

### Post by mc4man on 2009-10-04
i think it would be interesting if someone could say if the "update manager" will remove packages.

From what i've seen it will not (and is one of the causes getting a partial up???? in the update manager

( maybe the terminology difference is 'partial upgrade' vs. 'partial update' ...?

edit: in other words I find the update manager very safe to use, what it can't install I investigate in synaptic to see why

---

### Post by FormerSlacker on 2009-10-04
I was getting a partial upgrade message yesterday, but "apt-get dist-upgrade" was showing no issues, and it updated fine. I'm not sure what the problem was.

---

### Post by alphacrucis2 on 2009-10-04
> **FormerSlacker said:**
> I was getting a partial upgrade message yesterday, but "apt-get dist-upgrade" was showing no issues, and it updated fine. I'm not sure what the problem was.

It tells you exactly what it is going to do. It pays to read the fine print before replying with a y.

---

### Post by 23meg on 2009-10-04
> **Slug71 said:**
> I really hope this topic will be a sticky for 10.04. :roll:

People who do partial updates don't read stickies&#8482; :)

---

### Post by emarkay on 2009-10-04
> **23meg said:**
> People who do partial updates don't read stickies&#8482; :)

Not to be smarmy, bit there is no sticky addressing THIS issue (Partial Upgrades) - being that updating/upgrading is a near daily check for most people and is done via the GUI for most, I think this issue needs a separate "sticky".

I also "vote" for some statement like "Partial upgrades may, or may not, crash your system permanently, so you should not to this unless you like Russial Roulette." or something like that.

What's the point of something that suddenly MAY be destructive being cloaked as something called "Partial Upgrade", that users have used for years harmlessly - where's the logic to that???

---

### Post by emarkay on 2009-10-04
Also see here:

[http://ubuntuforums.org/showthread.php?t=1282095](http://ubuntuforums.org/showthread.php?t=1282095)

---

### Post by 23meg on 2009-10-04
[QUOTE=emarkay]Not to be smarmy, bit there is no sticky addressing THIS issue (Partial Upgrades) - being that updating/upgrading is a near daily check for most people and is done via the GUI for most, I think this issue needs a separate "sticky".[/QUOTE]

It's mentioned in [the sticky thread regarding the beta release]("http://ubuntuforums.org/showthread.php?t=1280021"):

[QUOTE=23meg]Once you've started testing, do not upgrade your installation blindly - **especially, avoid partial upgrades offered by Update Manager unless you know precisely why it's offering a partial upgrade**. Regardless of which tool (APT, Update Manager, Synaptic, Aptitude) you're using to upgrade your packages, always check the list of packages to be removed, upgraded and installed before each upgrade. If in doubt, check the changelogs ("Package > Download Changelog" in Synaptic, or "aptitude changelog package_name", or at [packages.ubuntu.com]("http://packages.ubuntu.com")) to see why a package may be being removed.[/QUOTE]

It's also stressed in [https://wiki.ubuntu.com/UbuntuDevelopment/UsingDevelopmentReleases](https://wiki.ubuntu.com/UbuntuDevelopment/UsingDevelopmentReleases), which is linked to in that thread.

---

### Post by xebian on 2009-10-04
You have to admire sometimes the collective wisdom of whoever came up with this nonsense.  There is no such thing as partial upgrade.  It's either go or no-go.  Why it's still an option is even more perflexing.  It doesn't buy you anything.

BTW, your pizza is ready for the oven.  Would you want a slice while waiting?

---

### Post by aamukahvi on 2009-10-04
> **NRDNick said:**
> Just open synaptic, click "mark all upgrades" this will then list what is to be removed/installed/upgraded. I really believe this feature should be implemented into the update manager itself.
It is implemented.

If you get the partial upgrade popup and click OK, you can still review the actions (removals, upgrades, new installs) before committing.

---

### Post by Keyper7 on 2009-10-04
> **FormerSlacker said:**
> I was getting a partial upgrade message yesterday, but "apt-get dist-upgrade" was showing no issues, and it updated fine. I'm not sure what the problem was.

It was probably the replacement of libgd2-noxpm by libgd2-xpm.

In this case, the partial upgrade *was* supposed to be done.

---

### Post by psyke83 on 2009-10-04
> **Keyper7 said:**
> It was probably the replacement of libgd2-noxpm by libgd2-xpm.

In this case, the partial upgrade *was* supposed to be done.

Right. The real problem is that some people are doing partial upgrades *all the time*. Sometimes they are lucky (and therefore spread the misinformation that such upgrades are safe), and other times they are not.

Now that we are entering the beta phase, you can expect *dozens* of threads from users expressing difficulty, all due to unsafe partial upgrades.

Looking at the last three (!) pages of the Karmic subforum, I can see the following threads that would not need to exist if the users understood partial upgrades:

[http://ubuntuforums.org/showthread.php?t=1281366](http://ubuntuforums.org/showthread.php?t=1281366)
[http://ubuntuforums.org/showthread.php?t=1281900](http://ubuntuforums.org/showthread.php?t=1281900)
[http://ubuntuforums.org/showthread.php?t=1281920](http://ubuntuforums.org/showthread.php?t=1281920)
[http://ubuntuforums.org/showthread.php?t=1282331](http://ubuntuforums.org/showthread.php?t=1282331)
[http://ubuntuforums.org/showthread.php?t=1281787](http://ubuntuforums.org/showthread.php?t=1281787)

I'm sure that I even missed a few.

We need to use some tough love here. Any time a thread is created which asks about an issue related to partial upgrades, lock the thread and post a link to the sticky. Something needs to be done, because the forum will become far too cluttered.

---

### Post by emarkay on 2009-10-04
> **23meg said:**
> It's mentioned in [the sticky thread regarding the beta release]("http://ubuntuforums.org/showthread.php?t=1280021"):


Um, that's what I said....   :)  This is so important it needs a SEPARATE Sticky IMHO.

---

### Post by oboedad55 on 2009-10-04
> **emarkay said:**
> Um, that's what I said....   :)  This is so important it needs a SEPARATE Sticky IMHO.

I agree. This thread has gotten a fair amount of eye rolling, yet it continues on. If the dangers of doing a partial upgrade were clear, and I did read the beta sticky, then there wouldn't be so many questions about it nor so many miscues from having executed such. :shock:

---

### Post by 23meg on 2009-10-04
> **emarkay said:**
> Um, that's what I said....   :)  This is so important it needs a SEPARATE Sticky IMHO.

And [this is what I said before you said what you said]("http://ubuntuforums.org/showpost.php?p=8050322&postcount=20"), albeit half seriously: people who tend to click the "Partial Upgrade" button and not study the changes proposed will tend not to read sticky threads, but create new threads asking for assistance. And I'm not making this up; I've been frequenting the testing discussion forums since Hoary, and moderating them since Gutsy, and that is my observation.

Still, I might be wrong; times may have changed and it's worth an experiment. I'll post a sticky thread explaining the "Partial Upgrade" phenomenon within a few hours and we'll see if it works ("works" meaning we get a drastically less amount of new threads asking for "Partial Upgrade" assistance).

---

### Post by oboedad55 on 2009-10-04
> **23meg said:**
> And [this is what I said before you said what you said]("http://ubuntuforums.org/showpost.php?p=8050322&postcount=20"), albeit half seriously: people who tend to click the "Partial Upgrade" button and not study the changes proposed will tend not to read sticky threads, but create new threads asking for assistance. And I'm not making this up; I've been frequenting the testing discussion forums since Hoary, and moderating them since Gutsy, and that is my observation.

Still, I might be wrong; times may have changed and it's worth an experiment. I'll post a sticky thread explaining the "Partial Upgrade" phenomenon within a few hours and we'll see if it works ("works" meaning we get a drastically less amount of new threads asking for "Partial Upgrade" assistance).

I think it's worth a shot. Sometimes people are less reluctant to look at something specific than they are to read an entire sticky devoted to many topics. I know it's something I would have read before attempting anything so daring as a partial upgrade.

---

### Post by emarkay on 2009-10-06
Still seeing posts on this - whatever happened to the "Sticky" about "BEWARE Of Partial Upgrades in Karmic Beta!"?

---

### Post by nanog on 2009-10-06
IMO, anyone running testing should know how to use chroot and dpkg. As long as dpkg has not broken ~4 simple commands can fix *anything*. (And fixing  dpkg typically only involves *trivial* editing of config files like /var/lib/dpkg/status.)

---

### Post by 23meg on 2009-10-06
> **emarkay said:**
> Still seeing posts on this - whatever happened to the "Sticky" about "BEWARE Of Partial Upgrades in Karmic Beta!"?

A little patience please; I'm working on it.

---

