---
title: "Multiple installations accessing same /home, problems?"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by daveerickson on 2008-03-24
Currently I am running Gutsy on my machine. I have 2 HD's, a 160 and a 400. /home goes on the 400 and / on the 160. Of course this leaves a ton of unused space on my 160 so I was wondering what kind of issues would I be inviting in if I partitioned up my 160 into 2 or 3 partitions, ran different distros off of them, and had them all share the 400 as /home?

I am looking for horror stories/success stories, things to watch out for, etc. Thanks a bunch.

Dave

---

### Post by Barrucadu on 2008-03-24
I personally haven't tried this, but my friend is running Ubuntu, openSUSE and Fedora with the same home partition with no problems.

---

### Post by daveerickson on 2008-03-25
That is good to hear. Thanks for the response. Anyone else have some input?

---

### Post by housam on 2008-03-25
There is no problem resizing the ubuntu 160 GB partition to create more partitions ( note that you only can get 4 primary partitions on a single HDD or you can manage to have 3 primary partitions and 1 extended partition which can be devided to many logical partitions ).
you can install more distros on these partitions, but back-up your data before doing anything.
I have xp,ubuntu & kubuntu on my laptop w/out any problems, but I made a separate data partition shared between them ( it is more safe for my data in case of any operating system crash.)

---

### Post by daveerickson on 2008-03-25
Thanks for the input. I have thought of using a separate shared partition. Sorry if this is a simple question, but can I easily forward the /home/user/Music folder to say /shared/Music and store all my Music in /shared/Music for all distros to see? I like having the Document, Music, Videos folders in the Places menu. I also like being able always feel like I am saving things to my home directory. Yes, I could just save everything to /shared/Whatever... I seem to remember something about creating a system link, or some such thing, can't remember. Would that or something else accomplish what I am looking for? I do like the idea of pulling the important data out of the home folder so it is less likely to get screwed up.

Sorry for the rambling, and thanks for the feedback. :)

---

### Post by housam on 2008-03-26
Yes you can store what ever you want on this shared partition and can be seen from all operating systems. 
About linking this partition to the different operating systems, [[COLOR="Red"]this guide [/COLOR]]("http://www.psychocats.net/ubuntu/separatehome")can do it to ubuntu . for others , I don't know.

---

### Post by daveerickson on 2008-03-26
I already have my /home on a separate drive. I am only running ubuntu right now, so no windows access needed.

---

### Post by daveerickson on 2008-03-28
Anyone else have any thoughts/suggestions to add on this topic?

---

