---
title: "Downgrade problem with Beryl."
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by patchkov on 2007-02-22
Hi all,

Topic should be familiar to most of you. As you probably know, the latest repository available Beryl is quite buggy(!!!). Generally, there is no point using it, cause all machine slows down after a while, and all that issue with white cube, etc.

Anyway, I had an idea to downgrade the installed version from 1.9999something, back to 1.4. Unfortunatelly, the repository (whether using aptitude or synaptic) somehow rejects my query and I cannot downgrade from officially well know (which is given in every Ubuntu Edgy Beryl tutorial) repository.

So can anyone help me how to get back to lower version of Beryl. I love it, I use it extensivelly, it makes work much simpler, much better, much faster, it even is better than Mac's Expose.

Generally, I wonder why people put buggy version on the web and don't remove it, the only thing what we can read is the white cube etc. problems around whole ubuntu community. Such thing, I guess, discurage many of potential and current users.

Thanks,
Kris

---

### Post by kwaanens on 2007-02-22
I would be severely pissed off if they removed the latest version. It works flawlessly on my computer.
And, you've probably heard this before: BERYL IS BETA SOFTWARE. IT CAN MESS WITH YOUR SYSTEM.

Now, why don't you try to do the following:
remove all beryl related packages (i.e. everything from the repo in question)
delete ~/.beryl (and maybe ~/.emerald as well)
reinstall with the version you want, either with you apt-solution, or by manually downloading the packaes you want.
You might want to lock package version in syanptic, to keep from upgrading by mistake.

BTW, 0.2 final is 2 days overdue overdue, according to beryl-project.org's roadmap, so expect a new version soon.

- Ketil

---

### Post by patchkov on 2007-02-23
Yeah, thanks for tip. I will try it. Now I do not have time to poke around, but probably tomorrow... any way it looks like quite busy weekend :)

Talking about 0.2 official release.. I guess it will take some time to show up in ubuntu repositories and for now nobody gave any reasonable answer for that crappy white cube problem :)

BTW. At work I am using another computer where I use Ubuntu and I need to say I am having big trouble setting up beryl/emerald... I launch it, f.ex. in terminal, four lines says as ussual should be the case, that some tests were passed it also says at very beginning that AIXGL was found but crap doesn't want to work saying XGL was not found :| I always play in the mean time when I find some minutes spare, but I guess it should be working already or maybe it is just an issue of 1.9999beta-something :)

I will post some how things are when I find time to set it up.

Thanks,
Kris

---

