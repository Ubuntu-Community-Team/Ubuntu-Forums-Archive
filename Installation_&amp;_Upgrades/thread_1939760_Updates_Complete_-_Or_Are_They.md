---
title: "Updates Complete - Or Are They?"
date: 2012-03-12
forum: Installation &amp; Upgrades
---

### Post by LongFist on 2012-03-12
Okay, I'm confused here, and based on my research nobody else has experienced this issue.  My 'Updates' utility lists available (if grey'ed out) updates, but tells me that my machine is fully updated:
[CENTER][IMG]http://i42.tinypic.com/20fyibb.jpg[/IMG][/CENTER]

...the distribution updates have lingered ever since I updated my machine from 8.04.4 LTS to 10.04.3 LTS (there is a pattern there) - and the "Other Updates" are new, but since they deal with Wine (and I use Wine) I have decided to take action to "clear" these (apparently) pending updates.  Only I haven't a clue ***how*** to clear them.  And my Google-Fu has apparently weakened, as I don't even know from which direction I should approach this issue.

How do I either (a) apply these pending updates [regardless of the fact that my machine is "Up To Date"] or (b) clear these listings of pending updates that I apparently don't need, have authority to apply, or have access to, which vaguely amounts to the same thing(s).

Here's a snapshot of what I'm currently running:
[CENTER][IMG]http://i43.tinypic.com/2ekpyx2.jpg[/IMG][/CENTER]

I post this because - in addition to giving everybody all of the configuration and installation info they could need, it also points up the fact that I have no clue as to whether this is a 32-bit or 64-bit installation; I suspect the former simply because 8.04 was 32-bit, but since Ubuntu Linux does some pretty miraculous things all on it's own, it is generally wise that I do not make assumptions about anything.

So, to re-iterate, how do I either (a) apply these pending updates or (b) clear these listings of pending updates?  Or is that altogether necessary.  I just want my machine to be "in fighting trim" when the next LTS update is released, so I may take full advantage of all of the neat, new toys that will inevitably roll out with the new release...

Thanks for your time and efforts,

- The Lurking LongFist

---

### Post by Cavsfan on 2012-03-12
I think it is best to used the CLI way to update. 

```
sudo apt-get update 
sudo apt-get upgrade
```It will tell you what will be installed and what is being held back. If anything is being held back like a new 
kernel install you would use this command after the previous set:

```
sudo apt-get update 
sudo apt-get dist-upgrade
```This will get the ones being held back.

I got this from **ranch hand**, a pretty knowledgeable person in this forum.
He calls Update Manager - Update Mangler.

---

### Post by grahammechanical on 2012-03-12
Do you want my opinion/guess?

The distribution updates are updates that are expected to come but the packages have not yet been put in the repositories.

We have this all the time when using the 12.04 development branch. In fact we also get the message. Do a Partial Upgrade. Which is deadly. Incomplete things get downloaded, other stuff is removed but not replaced. Result = broken OS.

Right now Update Manager on 12.04 Beta 1 is telling me that Updates are available and it lists 8 packages but none of them are ticked. Just like the picture you show. If I run Check I may find that there are by now other packages ready to be downloaded. They may include some of the missing ones. Then again they may not. I could run the updates and still be left with these missing update packages until they are ready for 12.04.

So, as regard the Distribution updates the answer is wait.

The same may apply regarding Wine. How long has it been like this? wine is in my list as an update but it is not checked off. I know that Wine 1.4 has recently been released. In fact I have it installed. And these are 1.4 packages.

On a separate note. Please consider very carefully doing a fresh install to 12.04 LTS.

There are big improvements and there is a fundamental difference between 10.04 and 12.04 and I think that a heavily modified 10.04 being upgraded to 12.04 may give you problems.

No proof because no one is yet upgrading.

Regards.

---

### Post by Cavsfan on 2012-03-12
**grahammechanical**, A bit early to be jumping to a developmental release isn't it?
It won't be at final release until April 26th.
I plan on switching myself from 10.04 LTS to 12.04 LTS but, it will definetely be around May or so.
I don't like bugs and I have only one machine.

---

### Post by grahammechanical on 2012-03-12
Hi @Cavsfan

I am testing 12.04. I have an 11.10 which is my main or working install and I use it as my backup OS. Then I have two partitions for 12.04 to test with.

One 12.04 started out as 11.10 and was upgraded to 12.04 in November 2011 and has been updated daily to 12.04 Beta 1. And I have modified it to see if I can get it set up the way I want. I use it as proving ground to get Ubuntu working according to my needs. I am working with it every day. It is very stable.

The other 12.04 is a fresh install of 12.04 Beta 1 unmodified so that I can run some application tests which then get reported to the developers so that they are aware of stuff that does not work correctly before 12.04 gets released and not find out about it after its release.

Despite my confidence in the stability of 12.04 Beta 1 I would not upgrade my 11.10 install until the month of May either. Then I shall move on to testing 12.10.

I would only recommend trying out the development branch of Ubuntu as a dual boot or some other way. Never as the only OS.

Regards.

---

### Post by matt_symes on 2012-03-12
Hi

> I plan on switching myself from 10.04 LTS to 12.04 LTS but, it will definetely be around May or so.

You're sensible to wait. Wait for 12.04.1 to come out before upgrading. Wait for the point release.

grahammechanical is testing, as are others in these forums and all around the planet. They know what to expect though and are prepared for breakage. They also know how to fix things when they do go wrong.

If you are not sure how to fix your pending updates issue then you are right to upgrade when it's a lot safer to do so.

Follow the instructions from the poster #2 and post back the messages.

Kind regards

---

### Post by Topsiho on 2012-03-12
Your disk is almost full, as your system info shows only 625 MiB are available.

Topsiho

---

### Post by Topsiho on 2012-03-12
From wikipedia:

"Core 2 is a brand encompassing a range of Intel's consumer 64-bit x86-64 single-, dual-, and quad-core microprocessors based on the Core microarchitecture."

Topsiho

---

### Post by Cavsfan on 2012-03-14
Thanks,
I'll probably wait until the 12.04.1 release. I like 10.04 too much right now. I used to immediately upgrade to 
the next version of Ubuntu but, encountered some problems with printer drivers, etc. and went back to 10.04 LTS and love it!

I have a 500GB HD with about 100GB for Ubuntu and the rest for windows 7. And I do agree in dual booting.  If something happens 
to one of them you have the other to fall back on.

Windows 7 is for my son's games which won't play under wine and I like to keep up in case a friend needs some help.
I spend time on both systems each day usually.

---

