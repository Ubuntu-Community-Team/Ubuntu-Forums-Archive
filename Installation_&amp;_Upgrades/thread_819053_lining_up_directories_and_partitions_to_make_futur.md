---
title: "lining up directories and partitions to make future re-installs easier"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by michael pulsford on 2008-06-05
hi all

(i'm sorry if this is a common question.  i've searched for the answer but not found anything so far.  since it seems like a simple question, i have the feeling i probably didn't look in the right place.)

i'm about to change from gutsy to hardy.  i'm planning to do a fresh install rather than an upgrade.  (my gutsy install has a couple of instabilities, partly because i wasn't very careful when i installed it.  i'd rather start afresh than build on shaky soil.)

it occurs to me that i'm going to go through this kind of process more than once in my life, so i'd like to set up the way my directory structure aligns with my drive partitions so that this process can be easy.

it seems to me the best place to start is by putting my /mike directory on its own partition, so i don't have to backup that data (music, documents, movies etc) and then put it back each time i install a new version of ubuntu.

a) am i wrong?  is this a bad idea for some reason?
b) are there other things like this i can do to make my future life easier that aren't occurring to me because i am new?

any advice appreciated.

cheers,
mike

---

### Post by sonofusion82 on 2008-06-05
yes, it is possible and also common.
I have /home on another partition.

---

### Post by michael pulsford on 2008-06-05
> **sonofusion82 said:**
> yes, it is possible and also common.
I have /home on another partition.
thanks sonofusion!

and do you know if there any other directories which can usefully sit on their own partitions?

---

### Post by editrix on 2008-06-05
> **michael pulsford said:**
> thanks sonofusion!

and do you know if there any other directories which can usefully sit on their own partitions?

I've seen many opinions on this, but the best is: too many partitions either waste space (because they don't fill up as you thought they would), or you can run into trouble by making them too small.

There's a nice guide here: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by ilrudie on 2008-06-05
When I install I use the following
/
/home
SWAP

Many people like to have a separate /boot or /var but I have not found these to be necessary.  I make my /home have the bulk of the hard disk space because thats where all your media will go.

When you reinstall you just have to locate your /home partition (it should be easy because it will be huge compared to the rest) and tell Ubuntu to use that partition as /home and DO NOT FORMAT it.  Your files will be saved.  You may run into problems if you get a different UID for your user in your new install.  Ubuntu has been good in the past about not doing this but if you come across that problem just do 'sudo chown <yourusernamehere> /home/<yourusernamehere>'

---

### Post by cdtech on 2008-06-05
I split my partitions up the same as ilrudie, but keep in mind that if you use another storage medium for your music, pictures ect.., you don't really need a large /home partition either. I have a 40G home partition, thinking I would fill it up with music and such, but I use another storage drive for that stuff, now I have way to much space on my home partition.

Your largest partition will be "/" for all the additional programs you'll want to install. Maybe a little extra for your /boot, if you plan on experimenting with different kernels. I wish I would have made my "/" a little larger, may have to go into Gparted to sort that out now.

Good luck......

---

### Post by ilrudie on 2008-06-05
I should have noted that. /home is where i store media and its a 500gig drive i carved up so i have plenty (40gb) for root.  Don't short yourself on root space to have a massive home.  good caveat cdtech.

---

### Post by michael pulsford on 2008-06-05
thanks to everyone who replied!

yeah, the main reason i asked is because i have 3 drives split into about 9 partitions, from my windows-only days.  but i have to say it has been more trouble than it's worth in some ways: it was and is too hard to foresee exactly what kinds of data i'll be using (and generating).

i think i'll back it all up and strip down to a smaller set of partitions, each with much more room to move.

cheers,
mike

---

