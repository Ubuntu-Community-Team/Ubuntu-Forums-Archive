---
title: "1st Desktop in my LIFE"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by stealth_007 on 2009-12-03
Hi Friends, today I bough my first Desktop and new to Ubuntu World.

I am using computers in office and from 8 years in Windows World, I know the pain it gives.

I want only Ubuntu on my Desktop and nothing else. Because who wants to maintain Windows.

I downloaded Ubuntu 9.10 and checked with booting from Live CD.

Now when we install Windows we make partitions, based upon the space of HDD.

Windows installs all its system files on Drive C/ under folder called Windows and all the applications under folder called Programs.

I searched in Google for installation and I came to know that, we need to make two partitions one is '/' and the other is '/Home'.

Now I want to know whether all the system files, applications and games are installed in '/' and what ever files we create like Documents, Music, Pictures, Videos etc are stored in '/Home'. Am I right?

I got 1TB of HDD and in that we get 930GB, so what I thought is 30GB for '/' and 900GB for '/Home'.

Please suggest your opinions for perfect installation and I don't want to look back that DIRTY WINDOWS...

---

### Post by howefield on 2009-12-03
> **stealth_007 said:**
> I searched in Google for installation and I came to know that, we need to make two partitions one is '/' and the other is '/Home'.

Now I want to know whether all the system files, applications and games are installed in '/' and what ever files we create like Documents, Music, Pictures, Videos etc are stored in '/Home'. Am I right?

I'd say you have pretty much got it, although I'd also create a swap partition.

There are some short video screencasts explaining how to install Ubuntu that might be worth a look.

screencasts.ubuntu.com

---

### Post by doas777 on 2009-12-03
well ubuntu is just a little different, in that there is no analog to the all encompassing "Program Files" directory.

everything that you will ever change, as a **user** in ubuntu, shoudl be in your /home. when you install an app, it will generally put it's peices parts in /, and it's configuration in your home directory (in a folder starting with '.' so that it is "hidden"). that said, many apps have their own approach and degree to which they prefer to place things in teh root versus the home.


you are on the right track creating a seperate home partition from teh get go. it will serve you well next time you want to upgrade, rebuild, or try a new distro.

---

### Post by stealth_007 on 2009-12-03
Oh I forgot about SWAP.

---

### Post by doas777 on 2009-12-03
just be careful about the maximum number of primary partitions on a disk. you can only have 4 . i don't really like extended partitions, but if you ever need to add another partition to the mix, it may be the right choice.

---

### Post by stealth_007 on 2009-12-03
In my mind I want only two partitions one is '/' and other is '/Home' and last is SWAP.

When I have all my data in '/Home' and want to re-install or upgrade Ubuntu, will there be any data loss?

---

### Post by blur xc on 2009-12-03
> **stealth_007 said:**
> In my mind I want only two partitions one is '/' and other is '/Home' and last is SWAP.

When I have all my data in '/Home' and want to re-install or upgrade Ubuntu, will there be any data loss?

nope- and when you reinstall your favorite apps, the configuration files will still be there and they will pick up where you left off.  Very cool feature...

You are smart to set it up like this from the beginning.  I had everything installed on one partition, and then later went back and split it all up.  It was a bit of work, and because of my ignorance I messed it up a bit and then took a while yet to figure out how to fix it.  Doing it from the start avoids all that.  And I still don't have my partition sized all dialed yet.

BM

---

### Post by kamallneet on 2009-12-03
Instead of creating a 900GB partition, you may consider leaving some free space. It would be helpful if you want to try a different OS or Linux flavor later on..

---

### Post by stealth_007 on 2009-12-05
Hi friends, I am one of the happiest person for using Ubuntu, installation went fine.

Installed updates, opera browser, cairo dock, vlc player.

I am facing couple of issues like I cannot play DVD's, VLC player exits whenever I want to play media files...any fixes for these issues??

---

