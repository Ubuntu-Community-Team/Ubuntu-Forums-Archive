---
title: "no gdm after 8.04 update"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by houseworkshy on 2010-11-09
I allowed update manager to do it's stuff and all seemed well.  Then when browsing the system crashed.  On trying to reboot it got past the password and name stage, made the right noises then the screen went white.  Tried recovery mode, same again after fixing broken files.  Tried fix x servor and again.  Booted to comand line and "sudo start gdm" didn't work.  Also noticed that I was "root@desktop and not my user name.  Also this is not my machine.  I'm using puppy to post this.  Any ideas about how I can sort this out.

---

### Post by searchfgold6789 on 2010-11-09
You upgraded 8.04 to what? 8.10? I read somewhere that you couldn't upgrade to 10.10 from pre-10.04.

---

### Post by houseworkshy on 2010-11-10
It wasn't a distribution upgrade, just the standard update manager which  had been set to pull only security and recomends.  Also only the lts  ones.  Most of them related to cups, though I didn't read them all.  Let  it do that then went browsing with firefox, which had no add-ons  installed not even the security ones like no-script ( it's not my macine  ).  Probably five minets later the machine went down, was looking at  forbes magazine when it happened which is probably irrelevant. the gui  went then a screen of command lines flashed past too fast to read then  stopped.  No comand line entry so hit the power button.  Then rebooted  and as in my first post.
Though the problem wasn't understood or solved the situation has been.   Its a single drive machine which is a duel boot based on partitions, the  other system being xp.  Against the chance of something going wrong I'd  left cd's of puppy quirky and ubuntu 10.04.1 round there ( it's my  mum's machine actully and has had trouble after updates once before. ),  also we had blank dvds.  I tried the things mentioned in the first post  then booted from puppy ( the quirky version ) and all hardware was  working, just as importantly the linux partition was intact with all her  work ( open office documents mostly ) undamaged.  So part of whatever  happend had hit the grub.  Sorry we didn't wait long enough to see your  reply, it was a bit of a panic as mum's a writer and there was rather a  lot of new work which hadn't been backed up.  I then made a directory on  the xp side and copied over the documents, email etc, desktop ( it was  all over the place, mums a good writer but not a tidy maker of ordered  directories, I had to make docs1 2 and 3 because I don't know redundant  from important versions of things ).  Thinking back I should have  grabbed the logs too but sorry I didn't.  Then took a slight risk and  booted again, the xp boot worked so we were able to confirm that the  work had indeed been copied properly because open office is on both  sides.  Mum checked it and when she said all was there, I booted from  Lucid tested from live and all seemed ok.  So deleted the hardy  partition and put Lucid on it.  Rebooted and all worked.  Then Ufw  default deny and enable first, then drivers, then updates, clamAv etc.  Put no-script on this time too, one can take ease of use too far, also  changed theme to clear looks as Mum didn't like the buttons on the other  side thing.  All was well both sides through both cold and warm boots  so, fingers crossed, ok now.
Sorry I don't have more for the developers, we were in a bit of a flap.   I may have copied the sudo as admin sucessful file as part of the rest  and will look for it the next time I go round.  Also it was late by the  time it was sorted out which was why I didn't post back here last  night,  I'm posting from my own machine now. 
I'll try to add what I can remember.  Tried the recovery options,  mending broken files and x but no joy.  Looked ok through password  splash, flicker of orange background ( may be useful as Mum had changed  her background to green) then white screen in which one can move the  mouse pointer but can't do anything with it, no context menu.   When in  the command line from the broken hardy, via recovery, not only didn't  starting gdm work there was no man page for it and the command was  reported as non-existant.  Apt-get update couldn't connect, though it  did at least try.  The etho seemed to be working as far as moden lights  indicate.  Couldn't change directories so root@desktop was the only  place I could be.  I tried a few programs which I knew to be there  without luck.  I didn't spend long in there because I feared for the  data on the drive.  That's all I can remember for now.
Thank you very much for posting a reply.
I'll come back and may mark this tread as solved, because the situation  is.  However I'll leave it open for a day or two because what happend  isn't known.   The last time Mum had problems after a Hardy update lots  of other people did too and if that is the case this time the few scraps  I can remember may be of use and people may want to use the thread to  chat about it, in which case I'll leave it open.  Last time I wasn't  there and suspected a borked dist upgrade, this time I was there and it  definately wasn't, default repositories, security and recomends only and  Lts only, the server was the fastest of the uk ones at the time.

---

### Post by sikander3786 on 2010-11-10
Ahhh. Reading that long post is not easy. I admit I haven't read whole of it.

What happens when at the command prompt, you type,

```
startx
```

---

### Post by houseworkshy on 2010-11-10
I didn't try that.  However did try fixing it via recovery which didn't work.  Also as we got the password screen x probably started though what it did later is unknown.  Thanks for replying.

---

