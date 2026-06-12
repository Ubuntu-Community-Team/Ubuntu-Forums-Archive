---
title: "Questions about upgrading from 10.04 to 11.04"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by xeddog on 2011-04-29
I have an old beater computer running Lucid that has been doing a job for me, but has always had some minor issues.  I am considering upgrading to Natty, but I have some questions.

1.  I have tried booting the machine using the LiveCD and it will only boot to the Ubuntu classic desktop.  Even if I logout and back in selecting "Ubuntu" as the userid AND the session, It always loads Gnome.  Is there a way to have the liveCD boot to Unity, or at least switch to it?

2.  I really don't want to do a clean install because I have a lot of crap on that machine that would be difficult and time consuming to recover.  Has anyone successfully done an upgrade from Lucid to Natty, or Lucid to Maverick to Natty? 

Thanks,

Wayne

---

### Post by howefield on 2011-04-29
You will have to upgrade to 10.10 and then 11.04 or do a clean install.

What graphics card are you using ?

For me, I need to install then apply the proprietary drivers to get Unity.

---

### Post by KegHead on 2011-04-29
Hi!

A fresh install will save you a lot of headaches!(from experience)

[COLOR="Red"]Make sure you backup.[/COLOR]

KegHead

---

### Post by kansasnoob on 2011-04-29
> **xeddog said:**
> I have an old beater computer running Lucid that has been doing a job for me, but has always had some minor issues.  I am considering upgrading to Natty, but I have some questions.

1.  I have tried booting the machine using the LiveCD and it will only boot to the Ubuntu classic desktop.  Even if I logout and back in selecting "Ubuntu" as the userid AND the session, It always loads Gnome.  Is there a way to have the liveCD boot to Unity, or at least switch to it?

2.  I really don't want to do a clean install because I have a lot of crap on that machine that would be difficult and time consuming to recover.  Has anyone successfully done an upgrade from Lucid to Natty, or Lucid to Maverick to Natty? 

Thanks,

Wayne

Regarding issue #1 it seems your graphics chip won't support 3D so you get the classic fall-back mode. There is a "unity-2d" package in the repos so you can try it. There is also a unity-2d PPA:

[https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily](https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily)

You will still be able to use classic if you dn't like unity-2d :D

Regarding #2, if you do the release upgrade through the update manager you'd have to go from Lucid to Maverick and then Maverick to Natty. I find such upgrades to take about 1 1/2 hours each + the amount of time it takes to download the updated packages :(

There is however a new upgrade via live installer version that I've had good luck with. Check out the "2. Upgrade to Ubuntu 11.04 Natty Narwhal Using A Live CD" section here:

[http://www.webupd8.org/2011/04/how-to-upgrade-to-ubuntu-1104-natty.html](http://www.webupd8.org/2011/04/how-to-upgrade-to-ubuntu-1104-natty.html)

Note however that the data you do not have backed up is always the data you will lose!

Always have a backup of anything important!

---

### Post by xeddog on 2011-04-29
Thanks for the replies.  This machine doesn't have any critical stuff on it so if I HAD to do a clean install it wouldn't be all that dramatic.  I don't mind doing the install, but I just hate having to take several days to get it all customized and all the applications working again.  Just a big pita.

But regarding the LiveCD, I also just booted with my main machine with it, and I know this machine is 3d capable.  I can't get Unity to run on it either.  Same thing.

Now what?

Wayne

---

### Post by xeddog on 2011-04-29
Here is another little oddity that happened on the beater machine.  I went to check for updates and Update Manager found about 6 or seven updates.  When I clicked to install them, it asked me for the Natty cdrom.  The LiveCD apparently inserted itself into my software sources under "Other Software".  Weird.

Wayne

---

