---
title: "For Lucid-Adjustment to Bugfix procedures, IMHO."
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-22
As I see it, over the course of a few years, there is a fundamental flaw in the Bug system. 

We have "Popularity Contest", we have comments on messageboard, we have the Bug duplicate results  and we have other data, but there is no relative scale of importance assigned to bugs.  It's a "flip of a mouse" to assign priority by one with permissions to do so.  Many bugs of little importance get attention, while some as far back as Feisty have not been: 
1. Addressed,  attended to and solved. 
2. Marked as invalid with explanation.
3. Deferred to a designated group for further review.

It seems that we **all** have forgotten "Bug Number One".

In Summary: Let the bug priority be based on only two things:
1. It corrupts or crashes the Operating System (including booting and Recovery)  and/or further  development.
-or-
2. The usage and installed base of the application is such that it's priority is now elevated (and attended to) over lesser used or less defined issues.

---

### Post by 23meg on 2009-10-22
[QUOTE=emarkay]In Summary: Let the bug priority be based on only two things:
1. It corrupts or crashes the Operating System (including booting and Recovery) and/or further development.
-or-
2. The usage and installed base of the application is such that it's priority is now elevated (and attended to) over lesser used or less defined issues.[/QUOTE]

Why?

---

### Post by psyke83 on 2009-10-22
> **emarkay said:**
> 

In Summary: Let the bug priority be based on only two things:
1. It corrupts or crashes the Operating System (including booting and Recovery)  and/or further  development.

That will only apply to a small subset of applications/packages in the repositories. Not a good idea at all.

> -or-
2. The usage and installed base of the application is such that it's priority is now elevated (and attended to) over lesser used or less defined issues.

Doesn't this already happen in reality? The more prominent a bug, the more likely it is to get fixed (due to user, but more importantly, developer awareness and manpower).

Intentionally "downgrading" the priority of less popular issues reported in bug reports is not necessarily a good idea. *All* bugs need to be seen, regardless of how many users it affects at any given time.

What's far more important is for users to learn how to file bugs properly (and to make an effort to diagnose causes rather than symptoms).

---

### Post by flipper9 on 2009-10-22
mmmm, reporting bugs is a pretty involved process, needing to use the command-line, and right detailed reports.  Any idea how we could automate the process? I know that in Windows, you can "blindly" submit errors to Microsoft and they do something with the data (not sure what).  Could an automated process without user-intervention (well maybe click a button, but no need to fill out a "report") be helpful?  Like knowing that 10% of users are getting crashes in Program X or Daemon Y?

Right now, when I submit a bug, I have to drill down confusing and cryptic lists of stuff that, honestly, I don't have the time to do. I'm supposed to know what caused the crash?  How would I know what sub-system software is running under the program I'm running that crashed? I'm willing to submit that I'm having a problem, and maybe type in what happened, but I'm not willing to write out an entire paper for each and every bug.  There are too many.  Just IMHO

---

### Post by slakkie on 2009-10-22
> **psyke83 said:**
> 
What's far more important is for users to learn how to file bugs properly (and to make an effort to diagnose causes rather than symptoms).

+many

---

### Post by 23meg on 2009-10-22
> **flipper9 said:**
> mmmm, reporting bugs is a pretty involved process, needing to use the command-line, and right detailed reports.  Any idea how we could automate the process? I know that in Windows, you can "blindly" submit errors to Microsoft and they do something with the data (not sure what).  Could an automated process without user-intervention (well maybe click a button, but no need to fill out a "report") be helpful?  Like knowing that 10% of users are getting crashes in Program X or Daemon Y?

Right now, when I submit a bug, I have to drill down confusing and cryptic lists of stuff that, honestly, I don't have the time to do. I'm supposed to know what caused the crash?  How would I know what sub-system software is running under the program I'm running that crashed? I'm willing to submit that I'm having a problem, and maybe type in what happened, but I'm not willing to write out an entire paper for each and every bug.  There are too many.  Just IMHO

Filing crash reports with Apport pretty much works like that already. It fills in the title indicating what crashed at what part; all you're really supposed to fill in in the description is what you were doing when the crash occurred. You don't have to write a long story.

---

### Post by flipper9 on 2009-10-22
> **23meg said:**
> Filing crash reports with Apport pretty much works like that already. It fills in the title indicating what crashed at what part; all you're really supposed to fill in in the description is what you were doing when the crash occurred. You don't have to write a long story.

True; sort of.  After filling in the title, it presents you with a long list of bugs and asks you which one is related to your bug.  They all look the same unless you read everyone of them and understand what package is having the problem, which many wouldn't.  It really should just finish after auto-filling in the title, and then allow you to add more if you want to.

---

### Post by emarkay on 2009-10-22
> **23meg said:**
> Why?

As stated - focus on the critical, system wide issues, and then on the  most used apps.

"What's far more important is for users to learn how to file bugs properly (and to make an effort to diagnose causes rather than symptoms)."

And with the Bug reporting system now sending** everyone** to the Wiki, that's not helping. Also, the method now offered  to indicate applicable package is cryptic and elementary.  A few hours by a learned Ubuntu-ite could "weed out" the irrelevant data and provide a specific list of Karmic/Lucid packages, and for selection, maybe it could be "intelligent" or at least, based on more than **one** keyword!

Flipper9, I abhore MS's approach - I think it's a "circular file".  However, an educated discussion needs to be made at top levels of Canonical to move this issue into the forefront.

"Filing crash reports with Apport pretty much works like that..." But again, 80% of the bugs I find are happening **not** at the exact point of submission, so this becomes moot!

Keep going, this is a good start!

---

### Post by 23meg on 2009-10-22
> **flipper9 said:**
> True; sort of.  After filling in the title, it presents you with a long list of bugs and asks you which one is related to your bug.  They all look the same unless you read everyone of them and understand what package is having the problem, which many wouldn't.  It really should just finish after auto-filling in the title, and then allow you to add more if you want to.

That's a side effect of Launchpad checking for similar bug reports using the bug title. But thanks to the Apport retracing service, and "bug patterns", Apport will automatically mark your crash bug as a duplicate if it is one, and can even prevent you from filing a report for known crashes altogether.

---

### Post by flipper9 on 2009-10-22
> **23meg said:**
> That's a side effect of Launchpad checking for similar bug reports using the bug title. But thanks to the Apport retracing service, and what's called "clue files", Apport will automatically mark your crash bug as a duplicate if it is one, and can even prevent you from filing a report for known crashes altogether.

Cool.  Maybe we need an option to just do all that automatically, so we can encourage users to submit crashes when they happen and then forget about them.  Those that want to add more info can goto the website and continue refining/adding to their bug report.  Not sure if that would cause more problems for the developers, or help them somewhat.

For me, I'm willing to have my CPU cycles and bandwidth used to submit info to the developers to help fix bugs and improve the system.  But I don't want to have to do a lot of work to do it.  I'm sure many users would agree.  Gosh, I'm a lazy user! LOL

---

### Post by 23meg on 2009-10-22
> **emarkay said:**
> As stated - focus on the critical, system wide issues, and then on the  most used apps.

Take a look at [the current guidelines we use for assigning importance to bugs]("https://wiki.ubuntu.com/Bugs/Importance"). What exactly should change, and why?

[QUOTE=emarkay]And with the Bug reporting system now sending** everyone** to the Wiki, that's not helping.  [/QUOTE]

Not helping with what? 

[QUOTE=emarkay]A few hours by a learned Ubuntu-ite could "weed out" the irrelevant data and provide a specific list of Karmic/Lucid packages, [/QUOTE]

The volume of bug reports we get is way, way greater than you seem to think. We need thousands of more human hours per month to cope with it.

[QUOTE=emarkay]But again, 80% of the bugs I find are happening **not** at the exact point of submission, so this becomes moot![/QUOTE]

How are crashes (we were talking about crasher bugs) not happening at the time of submission? Are you reporting crashes days or weeks after they occur? That's not good practice, since the development branch keeps changing, and your reports will quickly lose validity. Usually Apport will complain that your packages are outdated and not let you file it anyway.

---

### Post by emarkay on 2009-10-22
Apport:
[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

OK, but still, take this bug for example:
[https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/458352](https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/458352)
There was** no way** that I could have used any of the "automagic" reporting features - and it was reported on a different PC; this is one of my points.
Also, as seen there, how would I have known to look for "friendly" when I was reporting on "recovery"?

---

### Post by kansasnoob on 2009-10-22
I rather agree with emarkay. I don't have a solution in mind but consider three scenarios:

#1: Loss of crucial sound controls in alsa-mixer:

[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/451813](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/451813)

In that case I think I filed a pretty decent bug report and I've yet to even get a poke in the eye with a sharp stick.

#2: Loss of function in HPLIP/cups ?

[https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/455102](https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/455102)

OK, that's perhaps the worst bug report I've ever written, but HPLIP still fails to function (or install) properly in Karmic, while the same version of HPLIP functions/installs in Jaunty just fine.

#3: OK, Lennart didn't bother with Launchpad:

[http://0pointer.de/blog/projects/pa-in-ubuntu.html](http://0pointer.de/blog/projects/pa-in-ubuntu.html)

Now, that's pretty sad!

As I said, I have no answer but I can certainly see a problem, and it's getting to the point that I often feel as though the "veiled" response is, "if you don't like it go to another distro"!

Well I do lots of distro hopping/testing and IMHO Ubuntu is still numero uno, so you're stuck with me:P

I just see no harm in pointing out a "weakness" and trying to improve on the same. After all, no organization can just stand still. There will be movement, sometimes forward, sometimes lateral, and hopefully only occasionally backwards.

---

### Post by psyke83 on 2009-10-22
> **kansasnoob said:**
> #1: Loss of crucial sound controls in alsa-mixer:

[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/451813](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/451813)

In that case I think I filed a pretty decent bug report and I've yet to even get a poke in the eye with a sharp stick.

That affects a single audio chipset/codec, and you didn't explicitly describe what VIA mixers need to be changed for sound to work correctly. You filed on the 15th, in the time leading up to the RC release, so there's not going to be a lot of attention focused on a fixing a corner-case bug before release.
> 
#2: Loss of function in HPLIP/cups ?

[https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/455102](https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/455102)

OK, that's perhaps the worst bug report I've ever written, but HPLIP still fails to function (or install) properly in Karmic, while the same version of HPLIP functions/installs in Jaunty just fine.


I'm sorry, but is *not* an appropriate bug to be filed on Launchpad. This is an issue with the HPLIP source, that should be directed to the upstream bug tracker, or at least questioned in a forum or IRC channel before filing. If you didn't get a satisfactory answer elsewhere, this still may have been better filed as a question. 

> #3: OK, Lennart didn't bother with Launchpad:

[http://0pointer.de/blog/projects/pa-in-ubuntu.html](http://0pointer.de/blog/projects/pa-in-ubuntu.html)

Now, that's pretty sad!

That's not even a bug report - what bearing does it have other than to inflame discussion? Lennart works for Red Hat, and has no interest in filing bugs on the Ubuntu tracker - why would you expect him to? His criticisms may have a kernel of truth, but his attitude and acerbic posting style will inhibit rational debate on the topic.

---

### Post by emarkay on 2009-10-22
> **23meg said:**
> Take a look at [the current guidelines we use for assigning importance to bugs]("https://wiki.ubuntu.com/Bugs/Importance"). What exactly should change, and why?

 Not helping with what? 

**"Critical**: A bug which has a severe impact on a large portion of Ubuntu users "

Vague ambiguous and general. 
I prefer: "It corrupts or crashes the Operating System (including booting and Recovery)  and/or further  development." for specifics.

"
**High**: A bug which fulfills one of the following criteria: 

[LIST]
[*]Has a severe impact on a small portion of Ubuntu users (estimated)
[*]Makes a default Ubuntu installation generally unusable for some users
[LIST]
[*]For example, if the system fails to boot, or X fails to start, on a certain make and model of computer
[/LIST]
 
[*]A problem with an essential hardware component (disk controller, laptop built-in wireless, video card, keyboard, mouse)
[*]Has a moderate impact on a large portion of Ubuntu users (estimated)"
[/LIST]
Huh, "estimated"?  Didn't I say something like  "we have the technology, the data, the information... Let's use it!"
Also, why is "High" a "Small Portion"?

'Nuff said on that...

> **23meg said:**
> 
The volume of bug reports we get is way, way greater than you seem to think. We need thousands of more human hours per month to cope with it.

Again, the tools are there - take the man out of the loop and tif need be then, pull back and adjust.  This issues is at the uppermost levels of Ubuntu - I am sure Canonical would agree, and resources can be made available for a few full-time experts to attend to this...

> **23meg said:**
>  How are crashes (we were talking about crasher bugs) not happening at the time of submission? Are you reporting crashes days or weeks after they occur? That's not good practice, since the development branch keeps changing, and your reports will quickly lose validity. Usually Apport will complain that your packages are outdated and not let you file it anyway.

No, please re-read what I said. PC#1 crashes and I use PC#2 to report it, for one example.  Alternatively PC#3 has a fault before the GUI appears, or kills network, or is just not easy to manually trigger the automated process.  This is the issue on this part of my statement.  I am not addressing the "normal" things, and again, in my case this has been  **majority** of my bug reports.

---

### Post by psyke83 on 2009-10-22
> **emarkay said:**
> Again, the tools are there - take the man out of the loop and tif need be then, pull back and adjust.  This issues is at the uppermost levels of Ubuntu - I am sure Canonical would agree, and resources can be made available for a few full-time experts to attend to this...

I suggest that you give this some more thought. If users insist on reporting duplicate bug reports, inarticulate bug reports, incomplete bug reports, then the manpower will be expended excessively on triaging rather than fixing bugs. This is what is happening now.

The biggest problem, in my opinion, is with the users. They simply don't know how to file bugs efficiently, and refuse to read and follow the [instructions that are provided]("https://help.ubuntu.com/community/ReportingBugs").

The general idea I'm feeling here is that a lot of people want to make bug reporting "easier", or more automated. Considering the apport integration that Ubuntu already takes advantage of, we simply cannot make bug reporting any easier. Some things in life are   difficult, or take a little bit of effort and care to get right - get used to it.

---

### Post by flipper9 on 2009-10-22
> **psyke83 said:**
>  The biggest problem, in my opinion, is with the users. They simply don't know how to file bugs efficiently, and refuse to read and follow the [instructions that are provided]("https://help.ubuntu.com/community/ReportingBugs").

Then maybe we have to stand back and figure out why they are not following the directions?  What can we do to improve the process?  How can we fix bugs, get info from the users, and streamline the whole process?  Telling people to read and follow directions is sure to fail and is just ignoring the problem.  Let's face it, the current method is not ideal. People don't listen. That's rule #1.  So if that is true, what can we do to improve the quality of the information that can help the developers the best that is different from what we do now?

---

### Post by psyke83 on 2009-10-22
> **flipper9 said:**
> Then maybe we have to stand back and figure out why they are not following the directions?  What can we do to improve the process?  How can we fix bugs, get info from the users, and streamline the whole process?  Telling people to read and follow directions is sure to fail and is just ignoring the problem.  Let's face it, the current method is not ideal. People don't listen. That's rule #1.  So if that is true, what can we do to improve the quality of the information that can help the developers the best that is different from what we do now?

It has already been done, hasn't it? As far as I'm aware, when a user tries to report a new bug, they get re-directed to the [ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs") page.

Some people will refuse to read instructions, even if they're practically forced to read them.

Consider some of the new threads and replies to 23meg's Partial Upgrade thread, which go something like "Help, I've read the sticky, but..." and then expose the fact that they probably didn't read the sticky at all.

---

### Post by gnomeuser on 2009-10-22
> **psyke83 said:**
> 
That's not even a bug report - what bearing does it have other than to inflame discussion? Lennart works for Red Hat, and has no interest in filing bugs on the Ubuntu tracker - why would you expect him to? His criticisms may have a kernel of truth, but his attitude and acerbic posting style will inhibit rational debate on the topic.

He is upstream for PulseAudio, naturally he gets upset when he sees distributions apply patches he considers plainly wrong or which puts his software in a poorer light than it has to. Remember the level of abuse this guy takes from the Ubuntu users, it is in his best interest to act like this when a downstream repeatedly makes his project look worse than it needs to. Clearly they do not listen when he makes his recommendations as upstream, clearly it is having a negative impact, clearly he is the one who will need to deal with the bugs that result of their patching, thus clearly he is entitled to call them on it and inform users that they are not getting the Pulseaudio experience they should get and it is not his fault nor for lack of him trying.

This has nothing to do with who signs whose paychecks.

---

### Post by flipper9 on 2009-10-22
> **psyke83 said:**
> It has already been done, hasn't it? As far as I'm aware, when a user tries to report a new bug, they get re-directed to the [ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs") page.

Some people will refuse to read instructions, even if they're practically forced to read them.

Consider some of the new threads and replies to 23meg's Partial Upgrade thread, which go something like "Help, I've read the sticky, but..." and then expose the fact that they probably didn't read the sticky at all.

You're right!  But, we can't force people to read.  So where does that leave us?  We either get garbage reports tainting the database or people just refuse to report bugs.  That's not a good place to be. I'd suggest that we just find a way to gather info from users who refuse to follow the rules, thereby improving the quality of the bug reports submitted by people who do follow the rules.  That'd be a win-win situation.

---

### Post by psyke83 on 2009-10-22
> **gnomeuser said:**
> He is upstream for PulseAudio, naturally he gets upset when he sees distributions apply patches he considers plainly wrong or which puts his software in a poorer light than it has to. Remember the level of abuse this guy takes from the Ubuntu users, it is in his best interest to act like this when a downstream repeatedly makes his project look worse than it needs to. Clearly they do not listen when he makes his recommendations as upstream, clearly it is having a negative impact, clearly he is the one who will need to deal with the bugs that result of their patching, thus clearly he is entitled to call them on it and inform users that they are not getting the Pulseaudio experience they should get and it is not his fault nor for lack of him trying.

This has nothing to do with who signs whose paychecks.

Yes, I agree. My point was that Lennart has no interest in filing bugs on Launchpad, because he's not an Ubuntu user. He's a Fedora user as a natural consequence of working for Red Hat, being a RHEL/Fedora developer, and possibly also due to personal preference.

I also wish that his comments will get the attention they deserve from the Ubuntu developers, but his attitude won't help. On the other hand, he really did get a lot of unfair criticism due to the way in which PulseAudio was introduced to Ubuntu (included in the Hardy LTS without the ALSA plugins functioning).

---

### Post by 23meg on 2009-10-22
[QUOTE=emarkay]Vague ambiguous and general.
I prefer: "It corrupts or crashes the Operating System (including booting and Recovery) and/or further development." for specifics.
[/QUOTE]

Why? What do we gain from this specificness?

[QUOTE=emarkay]Huh, "estimated"? Didn't I say something like "we have the technology, the data, the information... Let's use it!"[/QUOTE]

What technologies, data and information do we have that we aren't using in estimating bug impact? Can you be specific about that?

[QUOTE=emarkay]Also, why is "High" a "Small Portion"?[/QUOTE]

That's *severe impact* on a small portion. Or moderate impact on a large portion. Think of bug impact on a per case basis and population affected changing in inverse proportion.

[QUOTE=emarkay]Again, the tools are there - take the man out of the loop and tif need be then, pull back and adjust. This issues is at the uppermost levels of Ubuntu - I am sure Canonical would agree, and resources can be made available for a few full-time experts to attend to this...[/QUOTE]

Canonical employs many people to work full time on Ubuntu QA, and I don't see a convincing argument from you that "the issue is at the uppermost levels". The issues with bug triage and fixing, as I see them, have more to do with the raw volume of bug reports we get, the initial quality and actionability of bug reports we get, and the amount of community workforce. You can keep coming up with ideas for refining procedures, but as long as the other factors I listed remain constant, very little will change.


[QUOTE=emarkay]No, please re-read what I said. PC#1 crashes and I use PC#2 to report it, for one example. Alternatively PC#3 has a fault before the GUI appears, or kills network, or is just not easy to manually trigger the automated process. [/QUOTE]

All possible with "apport-cli"; look it up.

---

### Post by emarkay on 2009-10-22
> **psyke83 said:**
> I suggest that you give this some more thought. If users insist on reporting duplicate bug reports, inarticulate bug reports, incomplete bug reports, then the manpower will be expended excessively on triaging rather than fixing bugs. This is what is happening now.
 The biggest problem, in my opinion, is with the users. They simply don't know how to file bugs efficiently, and refuse to read and follow the [instructions that are provided]("https://help.ubuntu.com/community/ReportingBugs").
 The general idea I'm feeling here is that a lot of people want to make bug reporting "easier", or more automated. Considering the apport integration that Ubuntu already takes advantage of, we simply cannot make bug reporting any easier. Some things in life are   difficult, or take a little bit of effort and care to get right - get used to it.

No, I am saying take more of the users **out ** of the loop - use tools already in place to "automate" and confirm/validate the process.  As for the instructions, it has been mentioned how flawed the actual process is, based on that page specifically!  I don't want to "dumb it down" I want to use (and adjust if needed)  the data already there to make it more effective, accurate and focused.

---

### Post by emarkay on 2009-10-22
> **psyke83 said:**
> It has already been done, hasn't it? As far as I'm aware, when a user tries to report a new bug, they get re-directed to the [ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs") page.

Some people will refuse to read instructions, even if they're practically forced to read them.

Consider some of the new threads and replies to 23meg's Partial Upgrade thread, which go something like "Help, I've read the sticky, but..." and then expose the fact that they probably didn't read the sticky at all.

You are being too intelligent  here - remember not everyone who uses Ubuntu is an expert.  Just look at the masses in terms of entertainment and use of Internet Explorer.  You are missing the point completely by diverting attention to "user education".  That's a relatively dead horse.

---

### Post by emarkay on 2009-10-22
"Why? What do we gain from this specificness?"

Prioritized facts.  'nuff said? 

" What technologies, data and information do we have that we aren't using in estimating bug impact? Can you be specific about that?"

I don't have the "keys to the vault" to know just what info is there, but I know most of it is not being used as I have sugested.

"That's *severe impact* on a small portion. Or moderate impact on a large portion. Think of bug impact on a per case basis and population affected changing in inverse proportion."

Semantics, and more broadly, vague (ambiguous and general, again)

"Canonical employs many people to work full time on Ubuntu QA, and I don't see a convincing argument from you that "the issue is at the uppermost levels". The issues with bug triage and fixing, as I see them, have more to do with the raw volume of bug reports we get, the initial quality and actionability of bug reports we get, and the amount of community workforce. You can keep coming up with ideas for refining procedures, but as long as the other factors I listed remain constant, very little will change."

Fact: Volumes of bugs** will** increase.
Fact: Users will **no**t get more intelligent.
Fact:** Nothing** will change unless educated users attempt to change it.
Semi-Fact: Accepting the status quo prevents further success, unless one believes in luck. 

I, and am sure there are many others, believe in proactive attempts at solving problems with educated discussion, sincere efforts and genuine action.

---

### Post by castrojo on 2009-10-22
> **psyke83 said:**
> I also wish that his comments will get the attention they deserve from the Ubuntu developers, but his attitude won't help. On the other hand, he really did get a lot of unfair criticism due to the way in which PulseAudio was introduced to Ubuntu (included in the Hardy LTS without the ALSA plugins functioning).

How do you know they're not getting the attention? ;)

We had a call with Lennart yesterday to discuss these issues. The patches he wants/needs in the Ubuntu kernel did not make upstream until 2.6.32 so we discussed how to better communicate needs between pulse and Ubuntu.

---

### Post by psyke83 on 2009-10-22
> **whiprush said:**
> How do you know they're not getting the attention? ;)

We had a call with Lennart yesterday to discuss these issues. The patches he wants/needs in the Ubuntu kernel did not make upstream until 2.6.32 so we discussed how to better communicate needs between pulse and Ubuntu.

Excellent, that's good to hear. ;) 

I didn't know because you didn't discuss this call in public (to my knowledge). Lennart's specific comments in that blog entry also weren't discussed on the ubuntu-devel-discuss list.

---

### Post by psyke83 on 2009-10-22
> **emarkay said:**
> No, I am saying take more of the users **out ** of the loop - use tools already in place to "automate" and confirm/validate the process.  As for the instructions, it has been mentioned how flawed the actual process is, based on that page specifically!  I don't want to "dumb it down" I want to use (and adjust if needed)  the data already there to make it more effective, accurate and focused.

I know what you're saying. If a program crashes or has a problem, you want a button to click that submits a bug report to Launchpad without the user having to fill in any details, hence taking them out of the loop.

We could reconfigure Apport to do this (and I suggest that you look it up, someone has already provided you a link), but it would result in a vast increase in bug reports submitted, and make it even more difficult for those who do the real work - developers - to ascertain the nature of the problem that was reported. Asking somebody to triage a bug with a stack trace and absolutely no description of the problem would be a nightmare.

---

### Post by psyke83 on 2009-10-22
> **emarkay said:**
> You are being too intelligent  here - remember not everyone who uses Ubuntu is an expert.  Just look at the masses in terms of entertainment and use of Internet Explorer.  You are missing the point completely by diverting attention to "user education".  That's a relatively dead horse.

You're not giving the average person enough credit. If a person is unwilling to read the ReportingBugs page (which is a well-written, illustrated guide), then I would *personally* prefer that they don't report anything, rather didn't than submit an incomplete bug report and waste everybody's time.

I'm having serious trouble understanding the alternative solution you're proposing, please tell us what it is.

---

### Post by Regenweald on 2009-10-22
> **flipper9 said:**
> Then maybe we have to stand back and figure out why they are not following the directions?  What can we do to improve the process?  How can we fix bugs, get info from the users, and streamline the whole process?  Telling people to read and follow directions is sure to fail and is just ignoring the problem.  Let's face it, the current method is not ideal. People don't listen. That's rule #1.  So if that is true, what can we do to improve the quality of the information that can help the developers the best that is different from what we do now?

Why they are not following directions ? that's easy, because the majority of internet users like to *look* not read. The majority of users switching to Ubuntu belong to this group. Make a wiki, they don't read it, make a sticky, they don't read it. Make an install slide show, they don't like it.... it's annoying. 

In short, you figure out how to get people to read more that a facebook status or 190 characters in twitter and you would have solved the problem.

---

### Post by emarkay on 2009-10-22
> **psyke83 said:**
> I know what you're saying. If a program crashes or has a problem, you want a button to click that submits a bug report to Launchpad without the user having to fill in any details, hence taking them out of the loop.
 We could reconfigure Apport to do this (and I suggest that you look it up, someone has already provided you a link), but it would result in a vast increase in bug reports submitted, and make it even more difficult for those who do the real work - developers - to ascertain the nature of the problem that was reported. Asking somebody to triage a bug with a stack trace and absolutely no description of the problem would be a nightmare.


Aaargh - I think I provided the link - and I am not asking for any "Automatic bug submission" - that** is **already there.  I am saying:

1. Canonical needs to devote a bit of funds to a full time department of experts  for bugs- -period.
2. There is data in the user systems, Ubuntu online databases, and developer resources that could be used to assist and streamline ** all** bug reporting, not just the "automatic" ones.
3. The non-automatic bug reporting process needs **extensive attention** to both make it work as most want it to, and to use the aforementioned data to assist the submitter;  as opposed to having to jump through hoops just to file one, and to be a developer one's self to know which portion of what package the specific bug relates to or affects.

---

### Post by emarkay on 2009-10-22
> **psyke83 said:**
> You're not giving the average person enough credit. If a person is unwilling to read the ReportingBugs page (which is a well-written, illustrated guide), then I would *personally* prefer that they don't report anything, rather didn't than submit an incomplete bug report and waste everybody's time.

I'm having serious trouble understanding the alternative solution you're proposing, please tell us what it is.

In this case, I have 3 years of experience with Ubuntu and many more beta testing other apps, I still cannot always "guess" (or is that presume) what package is affected; and the little "helper" box  of suggestions is next to useless, as it has redundant, obsolete or totally unrelated suggestions, most of which you have to click on and research independently to verify.

Furthermore, the "illustrated guide" is just an outline and really doesn't address the main issue - duplicate, unclassified and possibly invalid-from-the start bugs, and the lack of detailed information that** could** be available to assist even experts.

If I haven't made my suggestions clear for common sense attention to improving the entire system of bug reporting, well I guess, then I should just forget about it...

---

### Post by psyke83 on 2009-10-22
> **emarkay said:**
> Aaargh - I think I provided the link - and I am not asking for any "Automatic bug submission" - that** is **already there.  I am saying:

Yes, you provided the link after 23meg referred to it, but you didn't seem to read all the information yourself. You say how it would be impossible to report a bug when you can't get a GUI, etc (you can use apport-cli, as mentioned on the ReportingBugs page).

> 1. Canonical needs to devote a bit of funds to a full time department of experts  for bugs- -period.

It's quite fortunate that Mr. Shuttleworth is a millionaire, isn't it?

> 2. There is data in the user systems, Ubuntu online databases, and developer resources that could be used to assist and streamline ** all** bug reporting, not just the "automatic" ones.

Can you... synergize... that point into something clearer, please? I suspect that the developers would be **very** happy if all users actually *read* (instead of skim) the provided bug reporting guidelines. The only thing better would be for more developers to come into the fold and assist with the actual triaging and fixing of bugs.

> 3. The non-automatic bug reporting process needs **extensive attention** to both make it work as most want it to, and to use the aforementioned data to assist the submitter;  as opposed to having to jump through hoops just to file one, and to be a developer one's self to know which portion of what package the specific bug relates to or affects.

Jump through what hoops? How do "most" want it to work, and how will it help the developers to fix bugs?

---

### Post by flipper9 on 2009-10-22
So we're just gonna stick our fingers in our ears and say "la la la la la la la..."?  If it ain't working...then maybe it needs to be changed?

---

### Post by psyke83 on 2009-10-22
> **emarkay said:**
> In this case, I have 3 years of experience with Ubuntu and many more beta testing other apps, I still cannot always "guess" (or is that presume) what package is affected; and the little "helper" box  of suggestions is next to useless, as it has redundant, obsolete or totally unrelated suggestions, most of which you have to click on and research independently to verify.

Can you give a real-world example, please? For specific applications, usually it's quite easy to identify the package. For low-level/kernel/sound problems it can be a bit tougher, but there are specific pages devoted to kernel/sound troubleshooting and bug reporting.

> Furthermore, the "illustrated guide" is just an outline and really doesn't address the main issue - duplicate, unclassified and possibly invalid-from-the start bugs, and the lack of detailed information that** could** be available to assist even experts.

*Just* an outline? I think it explains things pretty concisely. You don't want to overload people with information.

> If I haven't made my suggestions clear for common sense attention to improving the entire system of bug reporting, well I guess, then I should just forget about it...

I'm still a bit confused on the exact details on how you propose to improve things (aside from employing people - is that necessary for a community distribution?)

---

### Post by psyke83 on 2009-10-22
> **Regenweald said:**
> Why they are not following directions ? that's easy, because the majority of internet users like to *look* not read. The majority of users switching to Ubuntu belong to this group. Make a wiki, they don't read it, make a sticky, they don't read it. Make an install slide show, they don't like it.... it's annoying. 

In short, you figure out how to get people to read more that a facebook status or 190 characters in twitter and you would have solved the problem.

In my view, the problem can be broken down into the following:
[LIST=1]
[*]Insufficient detail in many bug reports - this increases manpower due to triagers having to reply to incomplete bugs, and request the information that should have been present from the beginning;
[*]Not enough volunteers to triage bugs - you can never have enough;
[*]Not enough developers to fix bugs - ditto.
[/LIST]
It seems obvious that the recent decision during the Karmic cycle - to redirect bug reporters to the [ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs") link - is to address the first point listed above. However, people tend to be lazy. There's not much we can do about human nature.

The remaining points can only be addressed by volunteers stepping in and helping (or Canonical employing people to do so, as emarkay suggested).

---

### Post by flipper9 on 2009-10-22
Why not just collect debugging info, and make it harder to submit a bug report?  Those that are willing to submit a quality report will still do so, and those that will just put in garbage won't because they can take the easy way out by just submitting that Application X crashed?

---

### Post by ranch hand on 2009-10-22
OMG, we could just have the computer automatically transmit ever bit of information to "headquarters" as to what we are doing on the box and let them figure it out.  MS does it this way so it must be great.

It is if you are trying to "sell" an OS to ignorant, lazy users.  There is always Win JerryLewis pro for that crowd already.

Filing bugs is not that tough.  If it was I could not do it.  If I can do it, just about nayone  can that is literate.  If they don't want to read, don't file bugs.  The auto crash reporting gives you that option.

---

### Post by flipper9 on 2009-10-22
> **ranch hand said:**
> OMG, we could just have the computer automatically transmit ever bit of information to "headquarters" as to what we are doing on the box and let them figure it out.  MS does it this way so it must be great.

It is if you are trying to "sell" an OS to ignorant, lazy users.  There is always Win JerryLewis pro for that crowd already.

Filing bugs is not that tough.  If it was I could not do it.  If I can do it, just about nayone  can that is literate.  If they don't want to read, don't file bugs.  The auto crash reporting gives you that option.

Okay, no need for the tinfoil hat routine; nobody is suggesting copying your hard drive. I'm suggesting having an option to submit useful crash data with no other input needed. Can that not be useful?  I would suggest that it would reduce crappy bug reports and increase, and albiet fewre, higher quality reports by those that do "read".

---

### Post by 23meg on 2009-10-23
> **emarkay said:**
> 
Prioritized facts.  'nuff said? 

And we don't do any prioritizing at the moment? Bugs that crash and burn machines aren't prioritized over trivial ones? 

> **emarkay]I don't have the "keys to the vault" to know just what info is there, but I know most of it is not being used as I have sugested.[/QUOTE]

You don't know what's there, but you do know that most of it isn't being used? Does not follow. As long as you don't mention any specifics, that's not a helpful suggestion.

[QUOTE=emarkay]Semantics, and more broadly, vague (ambiguous and general, again)[/QUOTE]

The difference between "small portion" belonging straight to "High" and "small portion" belonging to "High" along with the condition of "severe impact" is not semantics.

[QUOTE=emarkay]Fact: Volumes of bugs** will** increase.[/QUOTE]

True.

[QUOTE=emarkay]Fact: Users will **no**t get more intelligent.[/QUOTE]

It's not a matter of intelligence said:**
> Fact:** Nothing** will change unless educated users attempt to change it.

That is, educated users, bug triagers, developers and other QA people.

[QUOTE=emarkay]Semi-Fact: Accepting the status quo prevents further success, unless one believes in luck. [/QUOTE]

Fact: Changing the status quo requires specifics, involvement and good old fashioned labor, as opposed to sweeping statements, wand-waving and blamestorming. If you'd like to see and join some discussions on "changing the status quo", it's happening all the time in the QA-related mailing lists, and UDS. 

[QUOTE=emarkay]I, and am sure there are many others, believe in proactive attempts at solving problems with educated discussion, sincere efforts and genuine action.[/QUOTE]

No doubt.

---

### Post by 23meg on 2009-10-23
> **emarkay said:**
> In this case, I have 3 years of experience with Ubuntu and many more beta testing other apps, I still cannot always "guess" (or is that presume) what package is affected; and the little "helper" box  of suggestions is next to useless, as it has redundant, obsolete or totally unrelated suggestions, most of which you have to click on and research independently to verify.

Apport now has basic support for symptom-based reporting, which will be improved. Try runnining ```
ubuntu-bug
``` without any arguments.

"Status quo"? Tell me about it.

---

### Post by emarkay on 2009-10-23
OK, never mind.  I have a Samba bug to deal with today anyway.

---

### Post by Keyper7 on 2009-10-23
I'm not in the mood for going too deep into this discussion right now, but I just want to say that if Apport and Launchpad were able to do everything some people wants in this thread, Skynet would've killed us all aready.

---

