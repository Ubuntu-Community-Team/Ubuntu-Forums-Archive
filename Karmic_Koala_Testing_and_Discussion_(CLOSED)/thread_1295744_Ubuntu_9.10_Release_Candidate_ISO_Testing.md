---
title: "Ubuntu 9.10 Release Candidate ISO Testing"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 23meg on 2009-10-19
The Ubuntu 9.10 Release Candidate is scheduled for this Thursday, and candidate images have appeared at the ISO testing tracker. Like every milestone, this one will benefit from good community testing coverage.

**[SIZE="3"]What Is ISO Testing?[/SIZE]**

A few days before each Ubuntu development milestone release (Alphas, the Beta and the Release Candidate), the package archive is frozen, and only bug fixes that help towards a high quality testing release are accepted. At the end of this period, a set of daily images are designated as candidates for release, and are subject to an additional round of testing commonly referred to as "ISO testing", in order to ensure that they're reasonably free of showstopper bugs and ready to be tested by the broader testing audience that grows with each milestone.

**[SIZE="3"]How You Can Help[/SIZE]**

Candidate images for the Ubuntu 9.10 Release Candidate are now up at [the ISO testing tracker]("http://iso.qa.ubuntu.com/"). You can test any number of test cases you'd like, and report bugs.

If you're unfamiliar with the procedure, there are two good places to start:

[list][*] [Ara Pulido's tutorial]("http://ubuntutesting.wordpress.com/2009/09/21/old-friend-iso-testing-tracker/") on how to use the ISO testing tracker 

[*] The [testing procedures page on the Ubuntu Wiki](https://wiki.ubuntu.com/Testing/ISO/Procedures)[/list]

If you need immediate help with testing, the best place to go is the #ubuntutesting IRC channel on irc.freenode.net. You can also follow [the #ubuntutesting tag on Twitter]("http://search.twitter.com/search.atom?q=%23ubuntutesting"), and feel free to ask any questions you may have on this thread.

---

### Post by ranch hand on 2009-10-19
Downloading now.

---

### Post by Slug71 on 2009-10-20
Thanks 23meg, 

Downloading 32 and 64bits now. Been waiting for this. :)

---

### Post by kansasnoob on 2009-10-20
Arrrgh! I'd just made a comment at the Ayatana project and saw that a new ISO test was available, so I ran four tests. All passed!

Now I see we have a "rebuilding" notification!

I guess maybe I need to test some more :P

Honestly, I love this!

I thought it appeared that there was an additional "sanity check" in place but maybe it was a "bug" that I liked!

---

### Post by metallica1788 on 2009-10-21
Installed it on my moms laptop and it is stable and lightning fast:) The only problem i found is that when enabling the broadcom wireless driver in livecd mode the wireless connecting wont work on my install. I had to delete the driver completely than it works.
Yes i repeat, i deleted the driver and then it worked:P

---

### Post by kansasnoob on 2009-10-22
I'm a bit disappointed that more people didn't jump on testing this ISO.

Not to "toot my own horn" but I ran four tests: live, entire disc, auto-resize, and manual part - then discovered that there was a "rebuild" and did it all again!

Why so little enthusiasm?

I know some are irritated over the Notify-OSD thing, but I fail to see how that could be a show stopper.

And I know that Lennart's not happy:

[http://0pointer.de/blog/projects/pa-in-ubuntu.html](http://0pointer.de/blog/projects/pa-in-ubuntu.html)

But Karmic seems great to me!

Am I missing something?

Please tell me we're not going the way of DSL!

---

### Post by taavi on 2009-10-22
I'm trying to get some tests done... Is it needed at all anymore?

---

### Post by e-Gee on 2009-10-22
Not working live CD doesn't  have safe mode and I can't install it and alternate CD freezes on setting up a partitioner same was in beta I have no luck with Karmic

---

### Post by ranch hand on 2009-10-22
The RC has not been released yet.  Try it when it is released.

Check here for an announcement;
[https://lists.ubuntu.com/archives/ubuntu-announce/2009-October/date.html](https://lists.ubuntu.com/archives/ubuntu-announce/2009-October/date.html)

All that is there now is the beta announcement.

If you still have trouble with it, maybe you should consider ISO testing.  This is how this stuff gets fixed.  Your next chance will be next week.  Watch the stickies.

This is why ISO testing is important.

---

### Post by kansasnoob on 2009-10-22
> **ranch hand said:**
> The RC has not been released yet.  Try it when it is released.

Check here for an announcement;
[https://lists.ubuntu.com/archives/ubuntu-announce/2009-October/date.html](https://lists.ubuntu.com/archives/ubuntu-announce/2009-October/date.html)

All that is there now is the beta announcement.

If you still have trouble with it, maybe you should consider ISO testing.  This is how this stuff gets fixed.  Your next chance will be next week.  Watch the stickies.

This is why ISO testing is important.

Did you notice that there was a "rebuild" in the midst of iso testing?

The first had an md5sum:

f280af34afb9ee590edfebe27a6d3212

next was:

f9b1bfa64bdbd86f42b51d0cb6fa0cde

Unless changes are made the latter will be the RC.

I thought it was funny because I'd run four tests before I found out that the iso was being rebuilt. I'm like you though ........... it's all good fun and I love the new install graphics!

It's a true piece of art!

---

### Post by e-Gee on 2009-10-22
Thanks for your reply I will try to install RC when it comes out and than I will report the bugs .
I am sure that as always everything will be fixed till the final release.  

As long as Ubuntu have such great community behind it will be the best OS in the world :KS!!

---

### Post by kansasnoob on 2009-10-22
> **taavi said:**
> I'm trying to get some tests done... Is it needed at all anymore?

Sure! I'd guess for another 6 hours or so fromthe time I'm posting this.

Be sure to sign up and you'll get notified by email next time.

Never kick yourself for what you missed, just look forward!

---

### Post by ranch hand on 2009-10-22
I saw it but it was too late for me to do the rebuild.  The first worked great for me.

A 10 hour day (counting gathering horses and getting to and from the cattle and then getting home again) just kind of made it silly for me to try and do anything when I got home except check the weather.  I had trouble pointing the mouse at that.  Kinda whipped.

Hopefully I will be more on it next week.  Probably have not much in the way of problems or rebuilds though.  I have faith in the devs in spite of all the FUN they have provided us with.

---

### Post by kansasnoob on 2009-10-22
> **ranch hand said:**
> I saw it but it was too late for me to do the rebuild.  The first worked great for me.

A 10 hour day (counting gathering horses and getting to and from the cattle and then getting home again) just kind of made it silly for me to try and do anything when I got home except check the weather.  I had trouble pointing the mouse at that.  Kinda whipped.

Hopefully I will be more on it next week.  Probably have not much in the way of problems or rebuilds though.  I have faith in the devs in spite of all the FUN they have provided us with.

I hear ya! I'm usually more "active" but I've been nursing this broken leg. (I think I should call it my "destroyed leg" - I split the tibia from the knee joint half way down to the ankle - looks like they could've used a good blacksmith from the X-rays).

But as long as I have my fainter's, my dogs, a warm place to (you know), and Ubuntu I'm good to go.

---

### Post by kansasnoob on 2009-10-22
Oh, on my hardware there were no apparent differences between the two iso's. It seemed to me that both booted to a Live desktop a bit slower than I'm used to, but installation went off without a hitch!

IMHO they have the graphics just perfect! And sufficient warnings!

---

