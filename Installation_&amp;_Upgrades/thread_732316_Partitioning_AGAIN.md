---
title: "Partitioning AGAIN"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by DoogH on 2008-03-22
Ok, so, I have read many other threads on partitioning.  I have a terrabye drive that I was going to give roughly 30% of to Ubuntu.  I have 2 gigs of ram and a 8800 GTS video card.  So,  I know I need a linux boot and a swap portion.  The extended drive is 286163 MB.  What proportion would you recommend for the linux/swap partitions?

Will this partition interfere with windows in ANY way?

Also, I am installing Ubuntu Beta.  Is it easy to simply upgrade to the official version upon release?

---

### Post by scragar on 2008-03-22
since you have 2GB of ram I would not be concerned about using large amounts of swap space, so the amount you need depends, if you do not wish to use hibernate then around 500MB should be more than enough swap, if you do intend to use hibernate however, you should install 2GB or a touch more, since hibernating stores current ram usage in swap.

---

### Post by DoogH on 2008-03-22
Ok, here is a screenshot:

So, this will not interfere with windows, right?  If I plan on upgrading to 4 gigs (vista is terrible), is it very difficult to do?

Is it easy to upgrade ubuntu?

---

### Post by tvtech on 2008-03-22
throw vista out get a refund.  go buy yourself a windows emulator. there are a couple decent for pay ones out there that work well.  or just use wine, it doesn't work well but it's free

---

### Post by DoogH on 2008-03-22
Ok, well, I am not doing that because I have some applications I would rather not risk loosing.  Just be glad I am switching to Linux for most purposes.

---

### Post by DoogH on 2008-03-22
Hm, I am a little worried, because I have used roughly 350gb of vista, and this is only seeing about 150...

Also, what emulator is the best for games?  I know most games don't work in Linux, but what do you think?

---

### Post by DoogH on 2008-03-22
Please Help!

---

### Post by Riverine on 2008-03-22
Some ideas:

1.  Once it is successfully created a swap partition is no threat to Windows.  However, if you intend to repartition a drive currently 100% used by Windows then there is a small chance that Windows could get clobbered.  Have your data backed up and figure out how you would restore Windows if you lost it.   I wiped out Windows trying to repartition a drive once...it wasn't the end of the world but it was a few hours of reinstalling.

2.  You might want to think about a smaller partition for Ubuntu.  The system will fit easily into 20 Gigabytes. You might even want two linux partitions--that way you can play with beta releases or keep a tried and true former version while you move on to a new release.  Repartitioning is a pain, so its better to make the partitions now.

3.  Consider a separate large partition for static data in standard formats (i.e., photos, music, movies).  That partition will be accessible to all the operating systems on the drive and it can persist unchanged while you migrate Windows and Linux through later releases.  It also makes backups easier to manage.

---

### Post by DoogH on 2008-03-22
Thanks, although, I am not sure if my setup is correct.  I have a separate hard drive for universal transfer between operating systems.  I will probably simply replace Ubuntu upon release.  I need more than 20 GB for stuff I plan to install.

What about my other questions?

---

### Post by zvacet on 2008-03-23
> Is it easy to simply upgrade to the official version upon release?

If you keep your Beta(it is Hardy) updated you will get final version.

---

### Post by housam on 2008-03-23
Since Hardy is not in its final release, I prefer to install the final release just over the test version you have. Also there is no need for more than 2 GB of swap.
For games, you can install wine and play all windows games through it.

---

### Post by zvacet on 2008-03-24
@** housam**

> Since Hardy is not in its final release, I prefer to install the final release just over the test version you have.

If you think about Gutsy you can be right,but if you are thinking about Hardy you are not.Beta version will get updates which will get you to the final release.No need install same thing again.

---

