---
title: "upgrade issues"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by PuppyFromHell on 2007-07-12
I upgraded from Edgy to Feisty last week and came back to find that all the other partitions on my hard drive were suddenly recognized, but I could no longer access my external hard drive.  I mean, /media/SEA_DISK was still there but there was nothing in it except something that said "created by pmount."  I know it's not the hard drive because it works fine in XP and it was perfectly fine in edgy, whereas I couldn't see any other partitions on my hard drive at all in edgy.  I am also using wicd 1.2.7 and couldn't connect to my secured network in edgy but had no trouble connecting to unsecured networks.  Now in feisty I have the opposite, excellent secured connection but no unsecured connections.  I suspect that an upgrade to 1.3.1 would do the trick but I have yet to do that.  Does anyone have any idea what's going on?


P.S.  my brother wants a laptop and I want to know what you think about vista vs. xp over gaming.
P.S.S. I know that's not the right place to put it but it's just a little thing.

---

### Post by loserboy on 2007-07-12
since nobody answered I'll throw out a guess.....  the upgrade to feisty may have changed the read permissions on the removable stuff, it would be a place to start anyway (i lurk quite a bit and I think I've seen that as a problem).


MS announced that there will be _no_ DX10 for XP, other than that I see no benefit gamingwise for vista, if anything I'm gonna guess they will run worse on vista especially if the laptop uses shared memory which is fairly common.....  maybe someone knows more than me

---

### Post by PuppyFromHell on 2007-07-13
Hey thanks for posting.  When I open up Thunar it shows up as one of the drives I can select, but then there's nothing in it.  So if it is the read permissions do you know how I can fix it?  Oh and if you have any comments on the wicd issue they'd be appreciated too.  I did upgrade to 1.3 but that didn't seem to fix anything.

---

### Post by loserboy on 2007-07-13
I don't really know how to fix it, but I'll help you search for a fix. First lets narrow down the problem, I assume it's being detected properly as a Seagate because of the mount point "media/SEA_DISK", right?

and your positive it's not empty if you check it from another computer/OS?


as for the wireless problem:  I've been extremely fortunate not to have any problems with wireless so I wouldnt even know where to start, although sometimes it's better to make one thread for each problem and you'll prolly get some answers that way

---

### Post by loserboy on 2007-07-13
can you post the contents of  /etc/fstab    when you have the drive plugged in.
(I don't know much about fstab, but it will tell us permissions at least)

---

### Post by imdano on 2007-07-13
I've never heard of someone being able to connect to encrypted networks but not unecrypted ones.  If you put encryption on a network you can connect, but if you remove it you can't?  Or are you trying different networks, one encrypted, the other not?

---

### Post by PuppyFromHell on 2007-07-14
Well I was mistaken about Thunar seeing the drive.  It doesn't, but there is a /media/SEA_DISK folder which I guess is left over from the upgrade before when I could see the drive.  Anyway, yes  I can see the drive in XP but I haven't tried it on other computers with Ubuntu.  And I looked in fstab but I didn't see anything in there about the drive and since I can't see the drive in Ubuntu and I don't have access to my home network right now I can't post the contents of it.  

As far as the wicd issues go yes I can connect to my secured home network but I can't connect to another unsecured network.  Before I think I had to use broadcom in the preferences but now secured internet works with ndiswrapper.  I have tried broadcom now but it hasn't worked.

---

### Post by imdano on 2007-07-14
If you remove the encryption from your home network, are you able to connect?  I'm wondering if maybe the issue is with the other network.

---

### Post by PuppyFromHell on 2007-07-14
I dunno, but I doubt it's a problem with the network, as I could easily connect before I upgraded to feisty.  And it be a problem with a lot of networks.

---

### Post by PuppyFromHell on 2007-07-22
UPDATE
I just found out something after installing KDE.  Konqueror sees the drive but nothing is in it.

---

