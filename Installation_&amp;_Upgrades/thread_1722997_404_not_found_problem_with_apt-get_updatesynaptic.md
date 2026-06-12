---
title: "404 not found problem with apt-get update/synaptic"
date: 2011-04-06
forum: Installation &amp; Upgrades
---

### Post by Rinre on 2011-04-06
Hi everyone,

I have a little problem on my relatively newly installed 10.10 Lubuntu that I can't quite figure out. I'm guessing it is a piece of cake for most of you ubuntu-veterans so I'm hoping a kind soul would save my day:

The last couple of weeks, the apt-get update (and corresponding button in synaptic) does not  manage to update all of my repositories, and I get a "404 not found" error at the end (see attached text file (hope I did that right, am a longtime lurker but haven't posted anything much yet)).

I realize that I have been doing some adding of repositories, and have written the wrong command a couple of times, which may be the cause of this (at least the two frescobaldi ppa errors).
What I don't understand, is how I remove these faulty(?) repositories, so that my system stops claiming being unupdated.

After searching/googling the issue I tried looking for the corresponding entries in sources.lst, but to no avail.

Please help me if you can!
all the best,

Ernir

ps. my system is in german, the messages say "W: Failure when getting.." and "E: some index files could not be downloaded, they were ignored or others were used in their place". (rather badly translated)

---

### Post by dnairb on 2011-04-06
Open Synaptic, then click Settings --> Repositories.
On the "Other Software" tab you will find the repositories you have added.

---

### Post by Rinre on 2011-04-06
Thanks a lot!

I knew it had to be some easy way to fix it, but somehow it didn't occur to me to do it through synaptic (since the problem was in update manager), I was all fixated at doing it all through the terminal...

But anyway, I simply unchecked the four misbehaving "repositories" (I guess they weren't valid ones, since they were never found), and now I maneged to get the very satisfying "your system is up to date" message after updating again! :O)

Now I only have to figure out if Frescobaldi is still updating like it should, but I assume it is since it works fine.. 

Thanks again dnairb!

Ernir

---

