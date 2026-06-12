---
title: "How can I get gdm back after this?"
date: 2009-12-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2009-12-08
Some time ago I posted this thread:

[http://ubuntuforums.org/showthread.php?t=1337082](http://ubuntuforums.org/showthread.php?t=1337082)

Shortly before that I posted this one:

[http://ubuntuforums.org/showthread.php?t=1326721](http://ubuntuforums.org/showthread.php?t=1326721)

And I even joined in on the bug thread:

[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430224](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430224)

It sounded reasonable to me to run:

```
dpkg-divert --local --rename --add /sbin/initctl && ln -s /bin/true /sbin/initctl

```

folowed by:

```
rm /sbin/initctl  && dpkg-divert --local --remove /sbin/initctl
```

But I can now guarantee you that breaks gdm in the OS you chroot!

I've found no way to fix it other than reinstalling.  Just running:

```
dpkg-divert --local --rename --add /sbin/initctl && ln -s /bin/true /sbin/initctl
```

again does not work.

Nor does running sudo dpkg-reconfigure gdm or purging gdm and reinstalling it!

---

### Post by ranch hand on 2009-12-08
Wow, you do sound screwed.

I think I would try removing xsplash and reinstalling it too before i reinstalled.  GDM and xsplash are kind of joined at the hip.

It shouldn't make the situation worse.

---

### Post by kansasnoob on 2009-12-08
I really don't care much about my own stuff but I'd changed my HowTo to reflect those changes.

Therefore I've adversely effected uncounted numbers of other OS's due to a lack of testing, or just listening to others that didn't test, or ..............

You get it!

I hate the fact that I passed along bad info to others!

---

### Post by ranch hand on 2009-12-08
Yes, that is a drag.  On the other hand most of the problems that I have helped straighten out have mainly consisted of fixing what folks have done to their box.

They seem to think that you do what ever the shiniest blog tells you and then come to the forum.  Those guys have not tested, I do not think most of them have ever seen what ever system they are "experts" on, let alone used it.

You can take comfort in the fact that at least you try.  Some times you just need to wing it.  Some times  you are going to get it wrong.  That is the nature of the beast.

If you are trying to do something you are going to screw it sometime.  To avoid mistakes is easy.  Just do nothing.

That is not FUN.

---

### Post by jerrylamos on 2009-12-08
> **ranch hand said:**
> 

If you are trying to do something you are going to screw it sometime.  To avoid mistakes is easy.  Just do nothing.

That is not FUN.

O.K., what I did was an update.  2.6.32-6 was/is running O.K., did an update to 2.6.32-7 which boots to command line prompt.  That's it.  Reboot select -6 from Gnome and GDM works.  -7 doesn't hack GDM.  It's an intel i845 integrated graphics.

Now I can "do nothing", i.e. never install an update, but how does that get Lucid tested?

Any ideas on what to try to kick -7 into GDM or get some kind of recognizable failure?

Thanks, Jerry

---

### Post by VMC on 2009-12-08
> **jerrylamos said:**
> O.K., what I did was an update.  2.6.32-6 was/is running O.K., did an update to 2.6.32-7 which boots to command line prompt.  That's it.  Reboot select -6 from Gnome and GDM works.  -7 doesn't hack GDM.  It's an intel i845 integrated graphics.

Now I can "do nothing", i.e. never install an update, but how does that get Lucid tested?

Any ideas on what to try to kick -7 into GDM or get some kind of recognizable failure?

Thanks, Jerry wow, jerry. I remember way back when. We both were suffering from Intelitis, then both kernel and intel updated to fix my issue of freeze-frame. I have an i865. Then it was "nomodeset" that worked. Now it appears that doesn't work for you. I see all those xorg-servers being held back. I keep thinking god please, no. Don't let those freeze my display again. Since our integrated Intel chips are related , I'm surprised you still have issues.

---

### Post by ranch hand on 2009-12-08
> **jerrylamos said:**
> O.K., what I did was an update.  2.6.32-6 was/is running O.K., did an update to 2.6.32-7 which boots to command line prompt.  That's it.  Reboot select -6 from Gnome and GDM works.  -7 doesn't hack GDM.  It's an intel i845 integrated graphics.

Now I can "do nothing", i.e. never install an update, but how does that get Lucid tested?

Any ideas on what to try to kick -7 into GDM or get some kind of recognizable failure?

Thanks, Jerry
If you are on just one install of 10.04 I would just do the "apt-get upgrade".

It is very conservative.

Watch what is being held back.

If things start looking up in that department, or just to check, fire up synaptic and mark all your updates and hit apply and see what they are wanting to do there.  Then probably break into a sweat and hit cancel very quickly.  They will catch up.

I would try booting to  the -7 kernel after every update to see if there is a change and then just go with the -6 if it is the one that is working.

---

### Post by DougieFresh4U on 2009-12-08
Just ran updates on 2 partitions, one had 203 updates and the other had 194. Using the .32.7 kernel, **sda6 **is Karmic
Both updates had the gdm update and asked if I wanted to keep my config. or go with mantainers, I kept mine. When I rebooted, all was good, just that my gtrub menu had moved things around, don't know why cause it never switched  around.
[B]sda8
win7
sda6
sda7 [/B]
now it's 
[B]sada6
win7
sda7
sda8[/B]
But it all booted fine, 'fglrx' on one partition and the 'xorg-edgers ppa' on the other.

---

### Post by kansasnoob on 2009-12-08
Regarding the gdm issue I experienced it was easily resolved:

```
sudo apt-get install --reinstall upstart
```

Whew!

---

### Post by ranch hand on 2009-12-08
It is always nice when simple things work.

---

### Post by DougieFresh4U on 2009-12-12
Any one else getting 'broken gdm' with this morning updates?

---

### Post by VMC on 2009-12-12
> **DougieFresh4U said:**
> Any one else getting 'broken gdm' with this morning updates?
I just updated, and all is okay. I see that 'gdm' is held back, so I left it alone. Is that the one you updated?!

```
sudo aptitude update && sudo aptitude safe-upgrade
=============================
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages have been kept back:
  gdm 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

```

---

### Post by DougieFresh4U on 2009-12-12
> **VMC said:**
> I just updated, and all is okay. I see that 'gdm' is held back, so I left it alone. Is that the one you updated?!


My one partition was telling me that 'gdm is broken'.
So I aborted and waiting till later to update as I am doing things in Win 7 partition this evening.

---

