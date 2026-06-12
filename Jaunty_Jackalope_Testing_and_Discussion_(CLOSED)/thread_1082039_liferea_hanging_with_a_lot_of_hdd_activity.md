---
title: "liferea hanging with a lot of hdd activity"
date: 2009-02-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by marijus on 2009-02-27
hello,
since a couple of weeks now liferea doesnt work well anymore...
it takes ages to update the feeds and it trashes the hdd...

status: not usable!

anyone else?

regards, marijus

---

### Post by jfernyhough on 2009-02-27
Yup, this started for me when I started using ext4 rather than ext3 on my Jaunty install. Liferea is fine in Intrepid (and Jaunty) on ext3. Changing the kernel on Jaunty has made no difference (28, 29-rc, etc).

I reckon it's the same sort of thing as the fsync bug that Firefox had a while back, though for some reason it's only affecting Liferea on ext4.

---

### Post by Voynix on 2009-02-27
Same problem here with ext4...  I gave up on Liferea a week ago, the window freezes and I have to kill its process...

---

### Post by OliW on 2009-02-27
I believe the issue you're running into is a known bug where due to SQLite fragmentation/bloat/pixie-dust, it explodes in a cascade of fsyncs.

On ext 2 and 3, there is usually half a minute (depending on the speed of your disks and computer in general) of furious HD thrashing and then it starts to do a proper update.

I guess ext4 is handling these fsyncs a little more sensitively and it's getting upset.

I remember for Firefox's SQLite issues a couple of months ago, there was a defrag command you could use to optimise your database. You could altering it for Liferea:

```
for f in ~/.mozilla/firefox/*/*.sqlite; do sqlite3 $f 'VACUUM;'; done
```

Edit the command would be:

```
for f in ~/.liferea_1.4/mozilla/liferea/*.sqlite; do sqlite3 $f 'VACUUM;'; done
```

But guessing from the amount of time and thrashing it just took Liferea to launch, I don't think it fixed anything. Sorry.

---

### Post by conehead77 on 2009-02-27
I submitted a bug report as i couldnt find one on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/335471](https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/335471)

---

### Post by pferraro on 2009-02-27
You can try the latest stable release (1.4.26) from here:
[https://launchpad.net/~weboide/+archive/ppa](https://launchpad.net/~weboide/+archive/ppa)

I behaves a little better than the older version in the main repo (i.e. the GUI doesn't freeze), but is still very slow navigating items.

---

### Post by cariboo on 2009-02-27
I upgraded this morning (10:00AM PST) and avoided the python problems, Liferea now seems to work as it should. It updates without greying out the window and there is no delay when clicking on entires, like it has for the last few weeks.

Jim

---

### Post by jfernyhough on 2009-02-27
> **conehead77 said:**
> I submitted a bug report as i couldnt find one on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/335471](https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/335471)Confirmed.

---

### Post by tr4nce on 2009-02-28
> **cariboo907 said:**
> I upgraded this morning (10:00AM PST) and avoided the python problems, Liferea now seems to work as it should. It updates without greying out the window and there is no delay when clicking on entires, like it has for the last few weeks.

Jim

Can anyone else confirm that the update fix liferea delays? I don't want to break anything

---

### Post by marijus on 2009-03-01
the peoblem seems to be with libsqlite3-3.6.10-1...
downgrading to libsqlite3-3.5.9-6 solved the problem for me.

it brakes some dependencies though... :guitar:

---

### Post by tr4nce on 2009-03-14
Well it seems that the unstable release tagged 1.5.13 devs switched some libraries and that seems to fix the high load times + hangs in the UI. Couldn't compile it to create a .deb but it would be nice if someone do it :p

---

### Post by jfernyhough on 2009-03-14
Janvitus PPA has 1.5.13:

[http://ppa.launchpad.net/janvitus/ppa/ubuntu/pool/main/l/liferea/](http://ppa.launchpad.net/janvitus/ppa/ubuntu/pool/main/l/liferea/)

```
## PPA for Gianvito Cavasoli (Intrepid builds)
deb http://ppa.launchpad.net/janvitus/ppa/ubuntu intrepid main
# deb-src http://ppa.launchpad.net/janvitus/ppa/ubuntu intrepid main
```

Yes, the builds are for Intrepid. But hey - it's a starting point. :D

---

### Post by marijus on 2009-03-14
sadly the 1.5.14 release doesnt fix the issue with libsqlite3 :(
at least not for me...

---

### Post by marijus on 2009-03-14
i also found this...

> Date: 2009-01-07 22:07
Sender: llandoProject Admin
Thanks for the report. I had a look at the backtrace but do not see
anything suspicious.

There are two known freeze conditions for Liferea 1.4.x:

1.) Flash related freezes: any Flash 9/10 player might freeze Gecko at any
time, with any propability.
2.) Liferea "freezes" temporarily when it processes a look of updates (or
large feeds) causing a lot of DB/disk activity.

Case 1.) cannot be fixed as Gecko doesn't provide a thread-safe interface.
With 1.5 using Webkit is an alternative to Gecko. For case 2.) this is also
hard to fix as the current sqlite-based implementation doesn't scale well
and on a system with average I/O wait might block the GUI for a longer
time.

Sorry, I'm afraid this won't fix.



look here: [http://sourceforge.net/tracker/index.php?func=detail&aid=2329128&group_id=87005&atid=581684]("http://sourceforge.net/tracker/index.php?func=detail&aid=2329128&group_id=87005&atid=581684")

---

### Post by tr4nce on 2009-03-14
> **jfernyhough said:**
> Janvitus PPA has 1.5.13:

[http://ppa.launchpad.net/janvitus/ppa/ubuntu/pool/main/l/liferea/](http://ppa.launchpad.net/janvitus/ppa/ubuntu/pool/main/l/liferea/)

```
## PPA for Gianvito Cavasoli (Intrepid builds)
deb http://ppa.launchpad.net/janvitus/ppa/ubuntu intrepid main
# deb-src http://ppa.launchpad.net/janvitus/ppa/ubuntu intrepid main
```

Yes, the builds are for Intrepid. But hey - it's a starting point. :D

The deb for intrepid doesn't work in jaunty :(

---

### Post by jfernyhough on 2009-03-14
Huh... weird. Installs fine on mine... :?

---

### Post by tr4nce on 2009-03-14
I've a problem with glib2-0

---

