---
title: "Dialup and K2"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Nesaskewatch on 2009-10-15
I put together an Ubu 9.04 box for a friend of mine that has no access to high speed.  It uses gnomeppp and a host of tweaks installed by yours truly.  Is it true that K2 will not support a dialup any longer?  Has anyone tried to set up a dialup with it?  I will have his system here in a few days, and I suppose I could throw a K2 live cd in and see...

Just wondering if someone has already crossed that bridge?

Cheers!

---

### Post by ranch hand on 2009-10-16
I have not tried to set up dial up in 9.10.  I am sorry to hear this is an even larger problem.  This has gotten worse since Hardy.  Huge numbers of people use dial up all over the world.

There are a lot of them here in the US.

I filed a "papercut" bug on this some months ago because if you are on dial up it is probably your only way to connect.  This should be important to Ubuntu.

I can tell you that "pppconfig" opens on the command;
[code]
sudo pppconfig
[code]
This is what I had to run in Hardy to get the connection to work.

I can also tell you that my USR5610c internal hardware modem is detected by "lspci".
Now I do not know if it is detected anywhere else.  It was not by Hardy.
If I look at my /dev directory and scroll to ttyS0 it does not say any thing but "character device" like all the rest.

I had to run pppconfig first and then the dial up part of nerwork-manager (has not exsisted from Intrepid on) and then it would work fine.  Auto connected, ran great.  If you cursored over the network-manager applet it would tell you that there was no connection.  At the same time, if you right slicked on the applet it would give you the option of disconnecting, and it worked.  You could re-connect.  It would still say there was no connection.

I had to tell pppconfig where the modem was (ttyS0) because it could not detect it.

In Intrepid I used wvdial.  I had 3 different installations of Intrepid on this box (just assume I am weird), wvdial worked great on the first one.  Would not work on the other 2.  Beats me.

I just checked and wvdial is available in the 9.10 repo, it is on my synaptic.  I would try it first.

---

### Post by Nesaskewatch on 2009-10-16
> **ranch hand said:**
> 

I just checked and wvdial is available in the 9.10 repo, it is on my synaptic.  I would try it first.

Sounds like you had as much fun as I did configuring the dialup!  I also note the presence of wvdial in my synaptic as well, and will be attempting to use it once the box is in my hands.  Maybe I will try to install a copy of gnomeppp if I can?  Should be fun...

I'll post back with any results/tips in a few days.

---

### Post by ranch hand on 2009-10-16
I do not like KDE but all the OS' I have tried with it have configured the modem a lot easier.  You might want to try kppp.

I am back on my favorite OS to use, 9.04, so I can't say that it is available.  It is on here and says it replaces kppp-kde4 so I bet it is on your repos too.  Several dependencies, of coarse.

If you go with that, I would use apt to install and grab anything recommended too, maybe some of the suggested stuff too.

---

### Post by Nesaskewatch on 2009-10-16
> **ranch hand said:**
> I would use apt to install and grab anything recommended too, maybe some of the suggested stuff too.

Thanks for the tip.  I am setting up an old system I have in pieces in the closet for testing dialup on K2.  This should be an eye opener!  I only just started using Linux a year ago!  Amazing how simple it can be once you get the code down.  Doesn't hurt to have a resource like this site neither!  Just plain fun to hack around with it.  Hardly use the xp partition anymore.

Cheers!

---

### Post by ranch hand on 2009-10-17
I hope that you carry on with this thread.  I have hopes of getting another job on a remote ranch.  That will be dial up again.

I would really like to hear how it is done.

---

### Post by Nesaskewatch on 2009-10-17
I'll update as I go along!

> I have hopes of getting another job on a remote ranch.

Have you thought of using "remote ranch server"?

LOL

Good luck soldier!

---

### Post by ranch hand on 2009-10-17
> **Nesaskewatch said:**
> I'll update as I go along!



Have you thought of using "remote ranch server"?

LOL

Good luck soldier!
Thank you VERY much.  I may not be able to do testing and have to break normal updates into pieces, but I would rather be a LONG way from town and use dial up and 4.4Ks rahter than live in town and use DSL at 300K/s.

I would really like to run 9.10 or 9.04 than 8.04, although I will still use 8.04 as my "business" OS (I like the LTS).

I am excited, because of 9.10 about 10.04 (LTS). I think it is going to be great.

---

### Post by _duncan_ on 2009-10-26
removed

---

