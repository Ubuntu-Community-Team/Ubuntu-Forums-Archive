---
title: "Firefox Goes Grey for 20 seconds"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by iheartubuntu on 2009-04-08
Anyone else experiencing this? Its really bad ever since I upgraded to Jaunty. Lots of bug reports on launchpad about this, but nothing looks recent. Im using FF 3.0.8

---

### Post by whoop on 2009-04-08
I have this, but I had this in intrepid as well. Are you using 64bit by any chance? Do you also get a "force quit/wait" dialog now and again while quiting firefox?

---

### Post by andrewabc on 2009-04-08
Don't know if related, but on intrepid, I've noticed in the past couple weeks that it takes firefox longer to close than it used to. I sometimes get the "wait or force quit" dialog because it can take ~5 seconds for firefox to shutdown.

> **whoop said:**
> I have this, but I had this in intrepid as well. Are you using 64bit by any chance? Do you also get a "force quit/wait" dialog now and again while quiting firefox?

wow I have same problem. I am using 32bit

---

### Post by whoop on 2009-04-08
> **andrewabc said:**
> Don't know if related, but on intrepid, I've noticed in the past couple weeks that it takes firefox longer to close than it used to. I sometimes get the "wait or force quit" dialog because it can take ~5 seconds for firefox to shutdown.



wow I have same problem. I am using 32bit
I have posted a bug report about this a short while back: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/355823](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/355823)

---

### Post by iheartubuntu on 2009-04-09
> **whoop said:**
> I have this, but I had this in intrepid as well. Are you using 64bit by any chance? Do you also get a "force quit/wait" dialog now and again while quiting firefox?

No, 32 bit. But i get the Force Quit notice every single time I close out Firefox. Ever since the start of 8.10 I believe.

---

### Post by Mooseknuckle on 2009-04-09
32bit arch, I have this too.

Firefox takes about 10 seconds to start, and typing anything in the url window causes it to freeze up for many many seconds at a time.

When loading a page, it will often freeze for 5-10 seconds, and scrolling down the page will cause lockups too.

Every time I close the app, I get the Force Quit dialog as well.

Everything was working fine before the upgrade FROM Intrepid.

---

### Post by TerpInHotLanta on 2009-04-13
Try pausing Tracker indexing.

I noticed that Tracker is causing my system to run like crazy (noticed by the fan constantly running on my laptop). Once I paused the indexing, Firefox ran normally.

Anyone else find this?

---

### Post by iheartubuntu on 2009-04-13
> **TerpInHotLanta said:**
> Try pausing Tracker indexing.

I noticed that Tracker is causing my system to run like crazy (noticed by the fan constantly running on my laptop). Once I paused the indexing, Firefox ran normally.

Anyone else find this?

My tracker is not even 1% of the processor use.

---

### Post by nwadams on 2009-04-13
i believe this is due to java/flash not liking an upgrade. If you did anything to java/flash that didn't involve the repo's that's probably it. you'll just have to purge java/flash and re-install it.

---

### Post by TerpInHotLanta on 2009-04-13
So after several hours, I have had 0 gray Firefox screens just from turning off Tracker indexing-- even when watching Flash and java streaming video.

I too only had CPU usage of 1-3% from Tracker, but whatever it was doing was not jiving with Firefox.

Anyone try this out?

---

### Post by andrewabc on 2009-04-13
> **TerpInHotLanta said:**
> Try pausing Tracker indexing.

I noticed that Tracker is causing my system to run like crazy (noticed by the fan constantly running on my laptop). Once I paused the indexing, Firefox ran normally.

Anyone else find this?

I'm using Intrepid. I disabled tracker a couple weeks ago because it was slowing computer down and I was rarely using it.

Firefox still takes a while to close. And I notice the same thing happens on my old computer using Jaunty. Oddly my old pentium4 seems to close firefox better than my core2duo (not as many wait/forcequit popups).

---

### Post by knarf on 2009-04-13
> **Mooseknuckle said:**
> ... typing anything in the url window causes it to freeze up for many many seconds at a time....

I've seen this behaviour ever since the move to *places* instead of the traditional bookmark system. My best guess is this delay is caused by FF reading in and parsing the *places* sqlite database which does grow to a considerable size:

```
ls -l .mozilla/firefox-3.6/hahahaha.default/places.sqlite
-rw-r--r-- 1 frank frank 25000960 2009-04-14 00:47 .mozilla/firefox-3.6/hahahaha.default/places.sqlite
```

That is a 25 MB file, most likely being loaded and parsed when I start typing stuff into the location bar...

---

### Post by iheartubuntu on 2009-04-13
> **knarf said:**
> I've seen this behaviour ever since the move to *places* instead of the traditional bookmark system. My best guess is this delay is caused by FF reading in and parsing the *places* sqlite database which does grow to a considerable size:

```
ls -l .mozilla/firefox-3.6/hahahaha.default/places.sqlite
-rw-r--r-- 1 frank frank 25000960 2009-04-14 00:47 .mozilla/firefox-3.6/hahahaha.default/places.sqlite
```

That is a 25 MB file, most likely being loaded and parsed when I start typing stuff into the location bar...

Interesting. So what did you do? Did you try deleting the file?

---

### Post by psyke83 on 2009-04-13
I highly recommend that you test Firefox on a new profile. Give it a stress test to see if the unresponsive behaviour persists.

N.B. Close Firefox before moving profiles.

To move your old profile:
```
$ mv ~/.mozilla ~/.mozilla-good
```

To restore your profile:
```
$ rm ~/.mozilla -r
$ mv ~/.mozilla-good ~/.mozilla
```

---

### Post by kelean on 2009-04-13
I had this problem with Ubuntu as well as Linux Mint.  All I had to do was install flash from the adobe site.  Problem solved.

---

### Post by zekopeko on 2009-04-13
this does have something to do with the sqlite storage of firefox. something about hammering the disk with sql write commands.

you could try:

```
for i in ~/.mozilla/firefox/*.deafult/*.sqlite; do echo "VACUUM;" | sqlite3 $i ; done
```

NOTE: i took this command from this page [http://petervk.wordpress.com/2009/01/17/use-firefox-3-youll-need-to-vacuum-the-database-once-in-a-while/](http://petervk.wordpress.com/2009/01/17/use-firefox-3-youll-need-to-vacuum-the-database-once-in-a-while/)

i also modified it so that it's a one liner. but i'm not on ubuntu now so i don't know if i got it right (the ~/.mozilla/firefox... part)

---

### Post by andrewabc on 2009-04-13
> **knarf said:**
> I've seen this behaviour ever since the move to *places* instead of the traditional bookmark system. My best guess is this delay is caused by FF reading in and parsing the *places* sqlite database which does grow to a considerable size:

```
ls -l .mozilla/firefox-3.6/hahahaha.default/places.sqlite
-rw-r--r-- 1 frank frank 25000960 2009-04-14 00:47 .mozilla/firefox-3.6/hahahaha.default/places.sqlite
```

That is a 25 MB file, most likely being loaded and parsed when I start typing stuff into the location bar...

My file is 20mb. I notice that typing stuff into location bar it is very slow and can freeze firefox for very short time.
So that is all the stuff stored by location bar (web addresses)?

So how do I get new one? Or if I clear "browser history" that will empty most of it?

---

### Post by iheartubuntu on 2009-04-14
Im not having any grey or force quit problems anymore after I cleared my private data. I saved my passwords and cookies though, everything else i deleted and now its working fine.

---

### Post by itsjustarumour on 2009-04-14
I've had this problem too - Firefox going grey for about 20 seconds.  Had it in Intrepid, and even worse in Jaunty.  Not caused by Flash in my case - or at least not by viewing sites with Flash content.  One thing I did notice was that this was sometimes caused by the Foxmarks plugin synching my bookmarks.  When I disabled Foxmarks, this fixed approximately 50% of the occurences of "greyness"...

---

### Post by iheartubuntu on 2009-04-15
> **itsjustarumour said:**
> I've had this problem too - Firefox going grey for about 20 seconds.  Had it in Intrepid, and even worse in Jaunty.  Not caused by Flash in my case - or at least not by viewing sites with Flash content.  One thing I did notice was that this was sometimes caused by the Foxmarks plugin synching my bookmarks.  When I disabled Foxmarks, this fixed approximately 50% of the occurences of "greyness"...

That is interesting becuase I do have Foxmarks also.

---

### Post by philinux on 2009-04-15
Tracker is not installed in Jaunty. It is in the repos though.

An upgrade would have it installed.

Firefox hanging could also be due to compiz.

---

### Post by andrewabc on 2009-04-15
> **philinux said:**
> Tracker is not installed in Jaunty. It is in the repos though.

An upgrade would have it installed.

Firefox hanging could also be due to compiz.

I don't use foxmarks. compiz is disabled for me. Of course compiz could cause slowness though.

But I'm willing to bet the 20mb sqlite database is the most likely problem. Kinda sad that this OS has only been installed for 6 months and firefox is slow. Yet on my winxp partition the sqlite is the same size and I have no problems with it (and it's been installed for more than 1 year).

---

### Post by philinux on 2009-04-15
Mine is also 20mb but no problems here.

64 bit. sun java and flash.

---

### Post by jowilkin on 2009-04-15
Changing the scheduler from cfq to deadline seems to have helped a bit for me with the graying out.

You can do it by adding "elevator=deadline" to your kernel options in grub.

---

### Post by KhaaL on 2009-04-15
this might be a long shot but, could this bug have something to do with firefox greying out? [http://bugzilla.kernel.org/show_bug.cgi?id=12309]("http://bugzilla.kernel.org/show_bug.cgi?id=12309")

---

### Post by Yeti can't ski on 2009-04-17
As many other folks I am having problems with Tracker on Jaunty Beta. Every time I run the computer, the first thing I have to do is manually turn-off the tracker. 

That said, Firefox seems generally slower in Jaunty but it has been dramatic only in relation to the opening of dialog-windows. For instance, when I want to upload a file to attach it to an e-mail (using Gmail as webmail and not through Evolution) and I click on "Browse" I get the gray screen and then I must wait for around 15 seconds to get the Nautilus window opened, which finally allows me to select the desired file. 

I had to attach 10 files to the e-mail, so I reaaaally felt the burden! :-) 

Anyone has any idea of what the problem could be? 

Still, the purpose of using a Beta version is finding bugs. I just hope they will be able to tackle these issues in time for the release of the stable version!

---

### Post by Scubdup on 2009-04-17
I had this happen a fair bit in 32-bit Intrepid with lots of patches and extensions and I'm still getting it on 64-bit Jaunty as a fresh install, with no addons, updates etc.

---

