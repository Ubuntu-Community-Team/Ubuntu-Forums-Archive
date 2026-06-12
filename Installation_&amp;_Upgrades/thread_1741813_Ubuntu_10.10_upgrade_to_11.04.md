---
title: "Ubuntu 10.10 upgrade to 11.04"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by RoyalMess on 2011-04-28
Oke so i was updating my PC but after it asked for a reboot i rebooted.
Now whenever i try to boot my Ubuntu partition i get this error displayed:

THe disk drive for / is not ready yet or not present
Continue to wait; or Press S to skip mounting or M for manual recovery
[IMG]http://www.pchelpforum.nl/files.php?pid=463694&aid=23655432[/IMG]
I hope its possible to fix since i have about 250GB on files i need to keep.

---

### Post by Foxcow on 2011-04-28
Can you boot into recovery mode?  Hold down the shift key during boot.

---

### Post by Hedgehog1 on 2011-04-28
You can also boot from a LiveCD/LiveUSB, select 'TRY' and then copy your data to an external HDD or USB stick.


***The Hedge***

:KS

---

### Post by RoyalMess on 2011-04-28
> **Foxcow said:**
> Can you boot into recovery mode?  Hold down the shift key during boot.


I did, no matter what mode or older version i tried it all came up with the same message.

---

### Post by Foxcow on 2011-04-28
Well like Hedgehog1 said, use a live CD to "try" Ubuntu, copy your data to an external drive and fresh format.

Next time, I recommend that you put /home on a separate partition.  You can very easily do this during setup.

---

### Post by RoyalMess on 2011-04-28
Currently i've installed 11.04 on a 16GB USB and i ran it Live and when i did Install Ubuntu it asked me to upgrade or install or w/e
I picked upgrade 11.04 to 11.04 since i have a feeling a family member messed it up as he/she was browsing the web and such, but currently its taking nearly a hour now at this action: Restoring previously installed packages...

Is this normal or...?

EDIT: 
I just saw it do something as i was posting this.

---

### Post by RoyalMess on 2011-04-28
I fixed it.
I guess the long waiting was normal, i kinda figured that my USB stick is kinda old and isn't as fast as it was and it took about 1 and a half hour but its all good now.
I just ran it as a Live User, then opened Install Ubuntu 11.04 then selected Upgrade 11.04 to 11.04 and waited, after that i was back in the game. :P
I just had to remove some of my old drivers and reinstall them and i was good. (Videocard and Soundcard)

---

### Post by Hedgehog1 on 2011-04-28
Hurray!!! Happy Hedgie Dance!!!! :D :D


***The Hedge***

:KS

---

### Post by Steve H on 2011-04-29
> **RoyalMess said:**
> Currently i've installed 11.04 on a 16GB USB and i ran it Live and when i did Install Ubuntu it asked me to upgrade or install or w/e
I picked upgrade 11.04 to 11.04 since i have a feeling a family member messed it up as he/she was browsing the web and such, but currently its taking nearly a hour now at this action: Restoring previously installed packages...

Is this normal or...?

EDIT: 
I just saw it do something as i was posting this.

Looks like mine doing the same thing. 64bit Desktop Natty upgrade from Maverick via DVD is just sitting there. When I expand the "Restoring previously installed packages..." it shows the following:

```
ubuntu CRON[8214]: (root) CMD ( cd / && run-parts --report / etc/cron.hourly)
```

My modem appears to be downloading something but there's of way of checking. I guess I've just got to wait.
:confused:

---

### Post by RoyalMess on 2011-04-29
It took a while for me like a hour for restoring the packages but the rest took like 20-30 mins in total.
So i would just sit it out and hope for the best :P

---

### Post by seanbw on 2011-04-29
Hello. is there a howto on best way to install ubuntu? Reason I am asking is: I want to a fresh install from 10.10 to 11.04 but I also want to have a separate partition for my home and install some packages ive already got currently like virtualbox, etc.
Is there a post that details the steps in a checklist format?
If not I might write on but no sense reinventing the wheel. Thx

---

### Post by h_miller on 2011-04-30
> **RoyalMess said:**
> It took a while for me like a hour for restoring the packages but the rest took like 20-30 mins in total.
So i would just sit it out and hope for the best :P


Mine has been 'Restoring previously installed packages' for about 4 hours now. This is getting a bit ridiculous, but I don't want to stop it in case it screws up my installation.
:confused:

Any words of wisdom that anyone can give me to help, or have I just got to keep on waiting indefinitely?

EDIT: FINALLY completed. Phew!

---

### Post by Steve H on 2011-04-30
It definitely takes a while to get through the whole process. I managed to get it installed but took a good couple of hours on the first attempt. Must be all the demand on the servers.

---

### Post by Foxcow on 2011-04-30
> **seanbw said:**
> Hello. is there a howto on best way to install ubuntu? Reason I am asking is: I want to a fresh install from 10.10 to 11.04 but I also want to have a separate partition for my home and install some packages ive already got currently like virtualbox, etc.
Is there a post that details the steps in a checklist format?
If not I might write on but no sense reinventing the wheel. Thx

If you have your stuff backed up, installing /home on a separate partition is really easy.  When it comes time to partition, select "something elese" or do it manually or whatever its called for 11.04  You will need 3 partitions.  I have a 500 gig drive in my laptop and this is how I did mine:

-50 gig for Ubuntu mounted at /
-2 gig for swap.  I think 1 gig is enough
-the rest mounted at /home


Voila!

---

### Post by seanbw on 2011-05-01
> **Foxcow said:**
> If you have your stuff backed up, installing /home on a separate partition is really easy. _** When it comes time to partition, select "something elese" or do it manually **_or whatever its called for 11.04  You will need 30 partitions.  I have a 500 gig drive in my laptop and this is how I did mine:
-50 gig for Ubuntu mounted at /
-2 gig for swap.  I think 1 gig is enough
-the rest mounted at /home

Voila!
Thank you for this. Installing should be quicker than upgrading so I might do a test run to see how to end up with a separate home partition i.e. - how to tell it which partition is home.
I have a 150 GB laptop with 2 distros but I use 135GB for the main installation so my split will be something like this:
2gb for swap (both distros share the swap)
33gb for ubuntu
100gb for home
---------------------------
The other distro I use for testing I normally split like ths:
no swap (point at other swap)
5gb for the distro
25gb for home ( which I rarely use because I use it to testrun other distros) but I may change the ratios to increase the system partition if I am testrunning something like ubuntustudio which requires a lot of space.
Foxcon - thx for responding. I thought I might have to end up doing one test installation anyhow because the point you tell the software where your home partition is - isn't very clear to me.
So I might have to testrun it with my testing partiton just to see.
-------------------------
I don't want to hijack the thread so I think I will open another one so  can ask all the questions I have buzzing around in my head.
Good luck everyone.

---

### Post by Scoubidou on 2011-05-01
Hi,

I have the same error message. I updaded yesterday night, and this morning I saw that the install process crashed.
When I boot it still says 10.10 and I have the "/ drive is not ready" message.

I pressed M for manually, ran fsck. It fixed a bunch of stuff. Now I can see all my files but I can't startx 

```
Fatal server error:
Could not create lock file in /tmp/.tX0-lock
```

If I select Skip (instead of Manual) it says that "/tmp drive is not ready". So I tried Manual on that drive but I can't run fsck on /tmp. 

I get : 
```
fsck.ext2: Is a directory while trying to open /tmp
```

So is there anything I can try to fix my /tmp? or to mount it rw?

---

