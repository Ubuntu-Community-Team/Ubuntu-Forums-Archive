---
title: "Me, Myself and Ibex (Intrepid ... and facetious)"
date: 2008-06-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mc4100 on 2008-06-23
A simple discussion  and, yes, I formatted it a little weird, well, I'm new, and this isn't easy. Not at all.

Disclosure: This is all happening on my main machine, 
'cause hey, I'm fifteen, and this laptop is all I got. 
Well, this and a few (very) outdated, but (very) thorough back-ups ...

BUT FELLOW NEW-COMERS, IF YOU'RE READING, I GOT LUCKY 
AND SORT-OF KNEW WHAT I WAS GETTING MYSELF INTO -- 
DON'T try it without up-to-date backups or even attempt 
it on an important computer ... I heard it eats kittens. 
Kittens!

So I broke Hardy; badly: The touch-pad on my laptop stopped working after login; 
Firefox 3 was crashing, like crazy; my Alt+F2 box is busted; 
weird things were happening with compiz-fusion, and, awn ... 
AND Mono (Eugh), well, let's just say mono hates me and my machine -- 
I actually recoiled when I tried to run Banshee's shiny new 1.0 release from the terminal and got .dll errors. But that's another discussion - 
though I hear it's very good for developers.

Anyway, I had ordered one of those Hardy CDs, from Canonical, 
and it arrived at the peak of my insanity: I thought "Right, 
*Forget* this! Try again?". And then the crescendo: about to 
reinstall Ubuntu, I said ... "maybe I'll try Intrepid". First,
I remove Mono ... then, paste 'sum-stuff' into my sources.list; 
and it looks so ominous in Gedit! 
I did it anyway. 
* "Intrepid" comes to mind, but I don't even know if I would 
be using it right -- googles ... define:intrepid *
So, sources changed, and updated, I sudo apt-get dist-upgrade. 
(Yes, this is a fully patched hardy -- back-ports and all. In 
my defence, I didn't expect it work, at all ...)
Queue the half-hour of listing to music as the scary text scrolls past.
And then it's done! 
And I fire up synaptic to check for the ineluctable dependency problems: linux-resticted-modules-generic couldn't be upgraded. 
Great. 
I reboot and expect wireless (Intel, 3945) not to work, etc., ... 
But Everything's fine! And my mouse works again! Wow.
Hmm ... but something must be busted. Where IS all the bugs?!
Firefox 3 is great again (though I did remove a 3rd 
party flash10 for the one in the repo), Awn is working again, 
and so is a reinstalled Mono (Grumble). And, thank you, 
you awesome Ibex, so is ALT+F2 -- Wonderful.
The only minor issues I've come across is the (frankly, hilarious) 
sound from pc-speaker, and a small issue with my tray applet -- 
when Rhythmbox plays, the battery icon vanishes for a wee-while, and then comes back randomly.
So, let's give a shout-out to the great work of Ubuntu, and upstream, developers for a pre-alpha like I've never seen. 
(Well, since I'm new, I've never actually seen ANY pre-alpha, 
but it's a nice sentiment anyway) Let's hope it can only get better ...
Now, what's your story?

---

### Post by soccerboy on 2008-06-23
you got incredibly lucky that nothing broke after a dist-upgrade.  Usually dist-upgrade isn't recommended to upgrade to a developmental release.  My II is running fine so far although there aren't many new features to report.

---

### Post by cariboo on 2008-06-24
I've reinstalled intrepid a couple of times over the past weekend. I've been using **aptitude full-upgrade** and everything has worked quit well. Now if only I could stop myself from doing stupid things. I would be quite happy with the way intrepid runs. I've got sound, My video resolution is 1280X1024, and even the floppy windows and multiple desktops work.

Now if only dvd+rw tools was fixed I'd be really happy.:)

Jim

---

### Post by galileon on 2008-06-24
> **mc4100 said:**
> Where IS all the bugs?!

priceless :p

---

### Post by psyke83 on 2008-06-24
> **cariboo907 said:**
> I've reinstalled intrepid a couple of times over the past weekend. I've been using **aptitude full-upgrade** and everything has worked quit well.

As far as I know, "full-upgrade" is the same as "dist-upgrade" - it was good timing and luck that it worked properly for you. I'm sorry to repeat myself, but this is a major problem for new users and they need to learn that doing an unsafe "dist-upgrade" or "Partial Upgrade" is wrong.

A much better option is "aptitude safe-upgrade" or a simple "apt-get upgrade", then manually check any remaining packages that have been held back.

---

### Post by BCurtisWX on 2008-06-24
> **psyke83 said:**
> As far as I know, "full-upgrade" is the same as "dist-upgrade" - it was good timing and luck that it worked properly for you. I'm sorry to repeat myself, but this is a major problem for new users and they need to learn that doing an unsafe "dist-upgrade" or "Partial Upgrade" is wrong.

A much better option is "aptitude safe-upgrade" or a simple "apt-get upgrade", then manually check any remaining packages that have been held back.

Now this may be an extremely noob question, but i have always had to sudo apt-get upgrade/update.  Is the sudo not necessary?

---

### Post by ajmal_82 on 2008-06-24
oh hell yeah,i want to know does anything in world works for you :mad::confused::confused:.
i think your broke,so is your laptop.does xp work or ur just trolling ubuntu forums?.did any linux or fwi ubuntu previous versions work.i suggest try using hardy with single fresh install not dual boot and "[FONT="Comic Sans MS"][COLOR="Red"]*stop being vistamatic*[/COLOR][/FONT]":lolflag:

---

### Post by psyke83 on 2008-06-24
> **BCurtisWX said:**
> Now this may be an extremely noob question, but i have always had to sudo apt-get upgrade/update.  Is the sudo not necessary?

Yes, it's necessary.

---

### Post by jhoch on 2008-10-07
Did the upgrade, went well except I try to log on with the same log on I have been using and it tells me my user name or password is wrong. It sucks! Hopefully I will come up with a solution, any ideas guys?

---

### Post by cariboo on 2008-10-07
Start up in recovery mode, and at the menu select root prompt. At the prompt type:

```
passwd <username>
```

Where <username> is your user name, Type your password

That should clear your problem.

Jim

---

### Post by semitone36 on 2008-10-07
> **ajmal_82 said:**
> oh hell yeah,i want to know does anything in world works for you :mad::confused::confused:.
i think your broke,so is your laptop.does xp work or ur just trolling ubuntu forums?.did any linux or fwi ubuntu previous versions work.i suggest try using hardy with single fresh install not dual boot and "[FONT="Comic Sans MS"][COLOR="Red"]*stop being vistamatic*[/COLOR][/FONT]":lolflag:

....haha WHAT??

Wanna try to type that in a way so that we can read it?:lolflag:

---

### Post by psyke83 on 2008-10-07
> **semitone36 said:**
> ....haha WHAT??

Wanna try to type that in a way so that we can read it?:lolflag:

We're engaging in a bit of archaeology now, are we? Look at the date of these posts.

---

### Post by semitone36 on 2008-10-07
holy crap!

well hey at least Im not the one who dug the thread up :)

---

### Post by mc4100 on 2008-10-07
> **psyke83 said:**
> We're engaging in a bit of archaeology now, are we? Look at the date of these posts.

OP agrees ... dated pre-alpha if I remember correctly.

---

