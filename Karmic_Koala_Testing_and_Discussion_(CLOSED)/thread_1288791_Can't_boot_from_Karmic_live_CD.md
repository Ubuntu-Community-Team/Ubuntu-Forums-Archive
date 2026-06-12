---
title: "Can't boot from Karmic live CD"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sashin on 2009-10-11
I've been having problems booting from the karmic live cd. When I try I see some coloured lines and get to a black screen, this has happened before with intrepid (but not jaunty) and I was able to boot with safe graphics mode, but now even that doesn't work. This is only with one computer though, it works on my other two one of which is newer and one which is older.

---

### Post by Incendia on 2009-10-11
When you first load the cd and you come to all the options eg 'Try Ubuntu without touching my Computer' 'Install Ubuntu' and so forth, push F6, and select acpi=off and nolacpi.
I had the same problem and that fixed it.
Only issue is there was no battery monitor.

---

### Post by Sashin on 2009-10-11
It doesn't seem to work for me.

---

### Post by rtalcott on 2009-10-11
Magic!  That worked!  Thank you!

Now...after the install will it boot without any of those parameters?

Thank You!
rt

---

### Post by MacUntu on 2009-10-11
Safe graphics mode is (was) borked: [https://bugs.launchpad.net/ubuntu/karmic/+source/casper/+bug/423969](https://bugs.launchpad.net/ubuntu/karmic/+source/casper/+bug/423969)

Try a daily live CD: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by Delan Azabani on 2009-10-11
> **Incendia said:**
> When first load the cd and you come to all the options eg 'Try Ubuntu without touching my Computer' 'Install Ubuntu' and so forth, push F6, and select apci=off and nolapci.
I had the same problem and that fixed it.
Only issue is there was no battery monitor.
apci? Or acpi? It's acpi as far as I can remember.

---

### Post by MacUntu on 2009-10-11
> **Delan Azabani said:**
> apci? Or acpi? It's acpi as far as I can remember.

Yes.

If unsure about such parameters, download the package "linux-doc" and do ```
zless /usr/share/doc/linux-doc/kernel-parameters.txt.gz
``` :)

---

### Post by Sashin on 2009-10-11
I tried a daily live CD already.

---

### Post by MacUntu on 2009-10-11
Then I'm afraid it has nothing to do with that bug (the fix is in the daily live CD and is working for me).

---

### Post by Sashin on 2009-10-11
Hmm... I can't seem to upgrade from jaunty either. 

sashin@Home:~$ sudo update-manager -d
extracting 'karmic.tar.gz'
authenticate 'karmic.tar.gz' against 'karmic.tar.gz.gpg' 
/var/lib/python-support/python2.6/dbus/connection.py:242: DeprecationWarning: object.__init__() takes no parameters
  super(Connection, self).__init__(*args, **kwargs)
 * Starting automatic crash report generation: apport                    [ OK ]

---

### Post by Sashin on 2009-10-11
Now I think I'm safe in saying I'm alone in this problem.

---

### Post by rturner on 2009-10-12
No, you're not alone;  there are at least two of us.  I burned cds and dvds from the daily builds and had the same problems you mentioned.  The beta cd got me as far as starting partitioning before it crashed.  I tried an alternative cd, which got me furthest;  it almost completely installed before it asked me for an alpha6 cd.  Even if I had it, I couldn't get the cd to eject to put it in.  Everything else I've tried just goes to the weird colors you describe and stops.

---

### Post by VMC on 2009-10-12
> **rturner said:**
> No, you're not alone;  there are at least two of us.  I burned cds and dvds from the daily builds and had the same problems you mentioned.  The beta cd got me as far as starting partitioning before it crashed.  I tried an alternative cd, which got me furthest;  it almost completely installed before it asked me for an alpha6 cd.  Even if I had it, I couldn't get the cd to eject to put it in.  Everything else I've tried just goes to the weird colors you describe and stops.

I had a similar experience while trying to install Fedora. I just created my own "/", "swap", and "/boot" partition (Fedora requires it), then the boot process went through.

I also had this experience with Ubuntu but no sure if it was karmic or jaunty. I now have my partitions set up before hand.

---

### Post by Sashin on 2009-10-12
My issue is not about it crashing however, its about it starting up. I can't get to a desktop, or even when I press install ubuntu it doesn't work.

---

### Post by cariboo on 2009-10-12
I would suggest you give the alternate install CD a try until the bug is fixed.

---

### Post by Sashin on 2009-10-12
Hmm... the alternate cd said there was something wrong with certain packages.

---

### Post by Sashin on 2009-10-12
Said that they were corrupt.

---

### Post by taavikko on 2009-10-12
> **Sashin said:**
> Hmm... the alternate cd said there was something wrong with certain packages.

> **Sashin said:**
> Said that they were corrupt.

There's an "edit" feature on messages, it can be used...
It would be far more helpful if you could remember what packages were "corrupted"



 > Hmm... I can't seem to upgrade from jaunty either. 

sashin@Home:~$ sudo update-manager -d
extracting 'karmic.tar.gz'
authenticate 'karmic.tar.gz' against 'karmic.tar.gz.gpg' 
/var/lib/python-support/python2.6/dbus/connection.py:242: DeprecationWarning: object.__init__() takes no parameters
super(Connection, self).__init__(*args, **kwargs)
* Starting automatic crash report generation: apport [ OK ]

Use "update-manager -d" no sudo in the command, it will prompt for passwd when needed.

---

### Post by CbrPad on 2009-10-12
> **Sashin said:**
> Now I think I'm safe in saying I'm alone in this problem.

I have the same problem with a daily image from 2 days ago.  I either get a completely blank screen or when putting it into safe mode I might get a continuously flickering screen full of garbage.

---

### Post by Sashin on 2009-10-12
I fixed it somehow, I reinstalled jaunty, and then I installed karmic on top and it worked... like magic. I don't know how I did it, I'm not sure if I should put solved or not in the title.

---

### Post by Incendia on 2009-10-12
> **rtalcott said:**
> Magic!  That worked!  Thank you!

Now...after the install will it boot without any of those parameters?

Thank You!
rt

Glad to help. And no, you won't have battery levels after you install it with it disabled. It doesn't matter *that much* if you are on a desktop PC. I heard some problems about overheating though.

> **Delan Azabani said:**
> apci? Or acpi? It's acpi as far as I can remember.

I was really tired when writing it, sorry for the spelling mistake. I will correct it now.

> **Sashin said:**
> It doesn't seem to work for me.

Sorry I couldn't help you :/

---

