---
title: "sun-java6 obsoleted on Lucid Lynx ?"
date: 2010-02-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lucasart on 2010-02-14
Hello everyone,

I have just upgraded to Ubuntu 10.04 alpha2, and during the install the package sun-java6 was removed and considered deprecated. But what is the new replacement ?
Now Java is simply not working, so what is the "new" way of running java applets in Firefox now with with Lucid Lynx ?

Thank you

---

### Post by rchille on 2010-02-15
Hi there!

I ran into the same problem this morning trying to use my company's Cisco AnyConnect VPN. 

Turns out the official supported Java for Lucid and forward is openjdk (Sun's attempt at Open Sourcing Java) and the plugin is Icetea (you will need both)

I was a little skeptical because icetea has not worked with Cisco's Anyconnect in the past (Cisco's fault I think) but after one false start, it seems to be running like a champ.

Give it shot, I hope that it works as well for you.

---

### Post by rchille on 2010-02-15
(sorry in advance for the doubt post)

There is another thread here discussing it:
[http://swiss.ubuntuforums.org/showthread.php?t=1402572](http://swiss.ubuntuforums.org/showthread.php?t=1402572)

At about post #17 someone mentions that if all else fails, you can try to use the older sun packages like so:
```

sudo add-apt repository ppa:portis25/test
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin

```

I was lucky enough not to have to resort to this step as icetea worked, but I wanted to include the original and this info.

Good luck again!

---

### Post by lucasart on 2010-02-15
> **rchille said:**
> (sorry in advance for the doubt post)

There is another thread here discussing it:
[http://swiss.ubuntuforums.org/showthread.php?t=1402572](http://swiss.ubuntuforums.org/showthread.php?t=1402572)

At about post #17 someone mentions that if all else fails, you can try to use the older sun packages like so:
```

sudo add-apt repository ppa:portis25/test
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin

```I was lucky enough not to have to resort to this step as icetea worked, but I wanted to include the original and this info.

Good luck again!

Hello

None of that works in Ubuntu 10.04, they deprecated sun-java6* and none of the packages you mentionned seems to work

```

lucas@lucas-laptop:~$ **sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate
[/B]lucas@lucas-laptop:~$ sudo apt-get openjdk 
E: Invalid operation openjdk
lucas@lucas-laptop:~$ **sudo apt-get install openjdk**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package openjdk**
lucas@lucas-laptop:~$ **sudo apt-get install icetea**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package icetea**

```

Any idea how to get around this ? I believe the repositry needs fixing.

---

### Post by alexcckll on 2010-02-15
This REALLY sucks!

What on EARTH gave the repo managers the idea that production users like me can cope without Sun Java, for goodness' sake?!  Is there anything that can be done to resolve this - like putting the full official Sun stuff into the Partner repo?  Just that NONE of the stuff out there behaves properly with OpenJDK...

Canonical - PLEASE get it fixed by 10.04.1!

---

### Post by OrangeCrate on 2010-02-15
> **alexcckll said:**
> **This REALLY sucks!**

What on EARTH] gave the repo managers the idea that **production users** like me can cope without Sun Java, for goodness' sake?!  Is there anything that can be done to resolve this - like putting the full official Sun stuff into the Partner repo?  Just that NONE of the stuff out there behaves properly with OpenJDK...

Canonical - PLEASE get it fixed by 10.04.1!

Nice rant, but it really is just an Alpha. Why not wait until the final is released, to be sure that Sun Java is not included, before you flip out?

Besides, if you really need the Sun Java packages for "production use", you really shouldn't be on 10.04 to begin with.

I would suggest you reinstall an earlier, supported version, and sit it out until the final is released.

---

### Post by Pjotr123 on 2010-02-15
You can install the latest Sun Java JRE 6 update 18, like this:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Works fine, but the latest JRE really should be in the repositories as well... Like in openSUSE 11.2. Oh well, repo politics I guess...

---

### Post by alexcckll on 2010-02-15
> **OrangeCrate said:**
> Nice rant, but it really is just an Alpha. Why not wait until the final is released, to be sure that Sun Java is not included, before you flip out?

Besides, if you really need the Sun Java packages for "production use", you really shouldn't be on 10.04 to begin with.

I would suggest you reinstall an earlier, supported version, and sit it out until the final is released.

I'm on Hardy - preinstalled on a Thinkpad - bought from linux Emporium.  I'm planning on buying a netbook from them - and am scared that I won't be able to use the Java sites that I use on the current machine on the new one due to this.

Also - what happens when I upgrade this one?  I could lose access to some discussion cafes - and possibly other sites that require Sun Java to run..

---

### Post by alexcckll on 2010-02-15
> **Pjotr123 said:**
> You can install the latest Sun Java JRE 6 update 18, like this:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Works fine, but the latest JRE really should be in the repositories as well... Like in openSUSE 11.2. Oh well, repo politics I guess...
Hmm - I've never understood this whole "repo politics" thing... surely Ubuntu is now being thought of as a product?  As end-users do... and if it goes gold with that kind of risk...

Here's hoping that Sun Java JRE (latest) gets into the Partner repo..
Oh - Citrix Receiver as well...
And Adobe Air...

Just like Flash

---

### Post by slakkie on 2010-02-15
Seriously? ha, sun java is crucial, works with android. Somehow it doesn't work with my debian install, but on Ubuntu it works just dandy.. 

Anyhows, you can install the version from karmic, should work :)

-edit-
Android is not compatible with Gnu Java. OpenJDK should be fine.

---

### Post by Mighty_Joe on 2010-02-16
> **OrangeCrate said:**
> Nice rant, but it really is just an Alpha. Why not wait until the final is released, to be sure that Sun Java is not included, before you flip out?


The rant is valid.  Sun Java will not be included in the repos going forward.  [See here]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/420426") for some discussion.  
The powers that be have concluded that OpenJDK is Good Enough for most people and for those who need Sun Java, there's always a manual install (Pjotr123's link is the best procedure I've seen so far).
Edit: There's a [bug for Sun Java6 on Lucid]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/515678"). If you are concerned, add a "ME TOO" to that bug.

---

### Post by OrangeCrate on 2010-02-16
> **Mighty_Joe said:**
> The rant is valid.  Sun Java will not be included in the repos going forward.  [See here]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/420426") for some discussion.  
The powers that be have concluded that OpenJDK is Good Enough for most people and for those who need Sun Java, there's always a manual install (Pjotr123's link is the best procedure I've seen so far).
Edit: There's a [bug for Sun Java6 on Lucid]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/515678"). If you are concerned, add a "ME TOO" to that bug.

I see/read "discussion", but, unless I missed it, I didn't see a definitive source cited from the devs/Canonical confirming it.

So, at this point, I'm not concerned, and my guess is that it'll be available with the final release. If not, OpenJDK is O.K. with me (I've had good luck with it). As said, it's easily downloaded if someone needs it.

And my guess is, that the poster I took to task regarding the "rant" had no idea of this discussion, and he was just jumping the gun on an assumption that everything should ready for "production use" in an Alpha release, which is wrong, of course.

---

### Post by alexcckll on 2010-02-17
> **OrangeCrate said:**
> I see/read "discussion", but, unless I missed it, I didn't see a definitive source cited from the devs/Canonical confirming it.

So, at this point, I'm not concerned, and my guess is that it'll be available with the final release. If not, OpenJDK is O.K. with me (I've had good luck with it). As said, it's easily downloaded if someone needs it.

And my guess is, that the poster I took to task regarding the "rant" had no idea of this discussion, and he was just jumping the gun on an assumption that everything should ready for "production use" in an Alpha release, which is wrong, of course.
Granted - I was kind of aware that Lucid was in alpha at the mo... but was a tad worried that my VPN access and other Java stuff out there was immediately going to break when Lucid went to Gold release.

Especially as I plan to buy a new netbook preinstalled with Lucid...

Are Canonical in discussions with Oracle at all to get Sun Java into the partner repo?

---

### Post by alexcckll on 2010-02-17
> **OrangeCrate said:**
> I see/read "discussion", but, unless I missed it, I didn't see a definitive source cited from the devs/Canonical confirming it.

So, at this point, I'm not concerned, and my guess is that it'll be available with the final release. If not, OpenJDK is O.K. with me (I've had good luck with it). As said, it's easily downloaded if someone needs it.

And my guess is, that the poster I took to task regarding the "rant" had no idea of this discussion, and he was just jumping the gun on an assumption that everything should ready for "production use" in an Alpha release, which is wrong, of course.
Oh - and I'm not sure yet whether I'd break something if I ended up adding Java from non-official sources...

---

### Post by OrangeCrate on 2010-02-17
^^,

I'm not aware of any talks, but that certainly doesn't mean there aren't any. I've seen a couple of articles on the topic of whether Oracle will continue to support the open source projects (OOo in particular), but, personally, I think OpenJDK is probably where Ubuntu is going, or wants to go (but that's just my opinion).

[http://openjdk.java.net/](http://openjdk.java.net/)

[http://en.wikipedia.org/wiki/OpenJDK](http://en.wikipedia.org/wiki/OpenJDK)

^,

Personally, I've always stuck with the stuff in the repositories, but there are numerous links here on the forums regarding going off the reservation for programs, and I'm sure it's safe, particularly on "brand name" thingees like Java, or Firefox. Doing your homework before you install something, is probably the best advice anyone could give you.

---

### Post by alexcckll on 2010-02-17
Might be the case, but does this open version offer the same service as the Java Web Start functions and work with this "Gadara" product that is being used by some chat servers going forward?

All I know is that OpenJDK didn't work when I originally bought the Thinkpad I currently run (preinstall of 8.04), so I grabbed Sun Java from the repos...

If it came to it - if I had to BUY Sun Java, I would.  And I hope that Canonical, if there was no other way, would offer it as a commercial install in the way they do for a Parallels Professional licence via their store.

But I REALLY don't want to have to go back to Windows. Not after being a satisfied user of the Ubuntu product for this long.

---

### Post by OrangeCrate on 2010-02-17
> **alexcckll said:**
> Might be the case, but does this open version offer the same service as the Java Web Start functions and work with this "Gadara" product that is being used by some chat servers going forward?

**All I know is that OpenJDK didn't work when I originally bought the Thinkpad I currently run (preinstall of 8.04), so I grabbed Sun Java from the repos...**

There's been a lot of work on OpenJDK since then. In fact, I think I read recently, that it's passed all of the tests vs Sun Java proprietary.

(I can't seem to find the article right now, sorry)

You might explore the links I provided in an earlier post here for additional info...

---

### Post by alexcckll on 2010-02-17
Re this Open Java product - does it offer the Java Web Start service?

---

### Post by OrangeCrate on 2010-02-17
> **alexcckll said:**
> Re this Open Java product - does it offer the Java Web Start service?

No idea, you'll have to find that info on your own.

---

### Post by alexcckll on 2010-02-17
> **OrangeCrate said:**
> There's been a lot of work on OpenJDK since then. In fact, I think I read recently, that it's passed all of the tests vs Sun Java proprietary.

(I can't seem to find the article right now, sorry)

You might explore the links I provided in an earlier post here for additional info...
"passed all the tests"?  What tests?

Is it a 100% certified version, and have major Java apps been tested against it?
Has it been tested against Gadara and Faverolle, for instance?
What about RSA VPN clients?
Citrix Java client?

I did notice that Red Hat are behind it... but there are even some of the retrocomputing sites out there...  I've added my tag to the "Sun Java for Lucid" enhancement request as well... thanks for that.

---

### Post by OrangeCrate on 2010-02-17
> **alexcckll said:**
> "passed all the tests"?  What tests?

**Is it a 100% certified version**, and have major Java apps been tested against it?
Has it been tested against Gadara and Faverolle, for instance?
What about RSA VPN clients?
Citrix Java client?

I did notice that Red Hat are behind it... but there are even some of the retrocomputing sites out there...  I've added my tag to the "Sun Java for Lucid" enhancement request as well... thanks for that.

Here's the article I remember seeing:

Announcing OpenJDK 6 Certification for Ubuntu 9.04

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-July/000587.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-July/000587.html)

Sorry, I don't have any other information for you on this topic. Like I said in an earlier post, I wouldn't count out Sun Java 6 showing up in the final release of Lucid, but I've used OpenJDK with no problems, so at least for now, the topic is a non-starter for me.

---

### Post by cosimo on 2010-02-18
Hey guys,
 I have no appreciation for open java/jdk.etc.etc
I switched to ubuntu when it first came out because sun java was available for it.
Then sun made it available for ubuntu via the repos.
i was a happy man 
Now.after 6 years...no sun java means a possible move away from ubuntu.
that's sad...I have become accustomed to it and prefer it over other distributions.
i suppose I could install it manually but wont.
it is unclear...only because I have read nothing on the reasoning for this move..why it is being obsoleted.
 I will not use icedtea under any circimstance because it is useless on many sites and certainly in production environments.
  not a good move  devs!!
coz

---

### Post by Mighty_Joe on 2010-02-18
> **OrangeCrate said:**
> I see/read "discussion", but, unless I missed it, I didn't see a definitive source cited from the devs/Canonical confirming it.


[Martin Pitt]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/420426/comments/21") is the technical lead for the Ubuntu Desktop Team:

> Martin Pitt  wrote on 2009-10-13:  	  #21

TK [2009-10-13 10:06 -0000]:
> Ubuntu Desktop users should take responsibility for building their own
> systems and insuring that they are secure.

They should just use openjdk in this case (which is the default JDK
nowadays, so if you install any java app, it will be pulled in by
default if you don't have one installed already).

If you insist on using the proprietary sun java or a different JDK,
you are indeed on your own. But at least you will be aware of it,
instead of using potentially obsolete packages from the distro.

He updated [Bug 420426]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/420426") yesterday saying that the plan is to make Sun Java available in the Partner Repository in Lucid.

---

### Post by OrangeCrate on 2010-02-18
> **OrangeCrate said:**
> I see/read "discussion", but, unless I missed it, I didn't see a definitive source cited from the devs/Canonical confirming it.

**So, at this point, I'm not concerned, and my guess is that it'll be available with the final release.** If not, OpenJDK is O.K. with me (I've had good luck with it). As said, it's easily downloaded if someone needs it.

And my guess is, that the poster I took to task regarding the "rant" had no idea of this discussion, and he was just jumping the gun on an assumption that everything should ready for "production use" in an Alpha release, which is wrong, of course.

> **Mighty_Joe said:**
> [Martin Pitt]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/420426/comments/21") is the technical lead for the Ubuntu Desktop Team:



**He updated [Bug 420426]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/420426") yesterday saying that the plan is to make Sun Java available in the Partner Repository in Lucid.**

I thought it would be included, and I'm glad that it will be.

:)

---

### Post by gotenks05 on 2010-02-25
I'll take a look at the partner repository, since this is also giving me grief.  However, I have another solution.  Although Conical does not like people to do this, you can get Sun's Java 6 from the Debian Lenny non-free repository.  It works great in the Ubuntu 10.04 Alphas (I can only confirm Alpha 2).  I am installing Alpha 3, in order to make a customize version of 10.04, so I do not need to worry once the release candidates and official release are available.

---

### Post by KrazyPenguin on 2010-03-03
> **OrangeCrate said:**
> Nice rant, but it really is just an Alpha. Why not wait until the final is released, to be sure that Sun Java is not included, before you flip out?

Besides, if you really need the Sun Java packages for "production use", you really shouldn't be on 10.04 to begin with.

I would suggest you reinstall an earlier, supported version, and sit it out until the final is released.

I disagree but still respect your opinion. 
The best way to use an alpha release IS on production machines.
Trust me, you find out real fast what the problems are when you need to get something done and it doesn't work.
This is just another example.

---

### Post by has on 2010-04-04
> **OrangeCrate said:**
> Nice rant, but it really is just an Alpha. Why not wait until the final is released, to be sure that Sun Java is not included, before you flip out?

Besides, if you really need the Sun Java packages for "production use", you really shouldn't be on 10.04 to begin with.

I would suggest you reinstall an earlier, supported version, and sit it out until the final is released.


Rant??
This is the exact reason Ubuntu is alpha/beta tested!
To discover stuff that does not work, and detect serious shortcomings and designfaults.

Like this one.
If in fact the Sun JRE is obsoleted in favour of the open source version Ubuntu will have a serious problem. 
One example : In Norway banks only allow Sun JRE to log in the bank services.

Now, who would knowingly convert to (or stay on) a platform that makes it difficult to access one of the most popular services out there? Remember that difficult for experienced user spells impossible for the average user. Could your mother install Sun JRE? If no : epic fail.

We need Sun JRE in the partner repos.
Period.

---

### Post by sgage on 2010-04-04
This repo works fine for me, providing the latest Sun Java. In fact, it just updated my Java this morning:

[http://ppa.launchpad.net/voronov84/andreyv/ubuntu](http://ppa.launchpad.net/voronov84/andreyv/ubuntu) lucid main

---

### Post by NCLI on 2010-04-04
> **has said:**
> Rant??
This is the exact reason Ubuntu is alpha/beta tested!
To discover stuff that does not work, and detect serious shortcomings and designfaults.

Like this one.
If in fact the Sun JRE is obsoleted in favour of the open source version Ubuntu will have a serious problem. 
One example : In Norway banks only allow Sun JRE to log in the bank services.

Now, who would knowingly convert to (or stay on) a platform that makes it difficult to access one of the most popular services out there? Remember that difficult for experienced user spells impossible for the average user. Could your mother install Sun JRE? If no : epic fail.

We need Sun JRE in the partner repos.
Period.
[B]
[It is.]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/515678/comments/8")[/B]

---

### Post by ominolore on 2010-04-05
Hi. I ran into the same issue. This thing is not documented yet. You simply need to enable partner repositories in software sources. Then you'll find Sun Java packages in your lists.

[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

---

### Post by Starks on 2010-04-05
Programs like Limewire or Frostwire won't be installable unless the partner repo is enabled for Sun Java.

---

### Post by CoreyB. on 2010-04-05
> **Starks said:**
> Programs like Limewire or Frostwire won't be installable unless the partner repo is enabled for Sun Java.

OpenJDK doesn't work?

---

### Post by dino99 on 2010-04-05
> **CoreyB. said:**
> OpenJDK doesn't work?

i only use it with success but maybe with some apps there can be some issues

---

### Post by Starks on 2010-04-05
> **CoreyB. said:**
> OpenJDK doesn't work?
Nope. The deb complains about the sun prereqs not being fulfilled.

---

### Post by SkyNet2029 on 2010-04-13
The sun-java6 packages were removed from the multiverse repos for lucid. Here is how to install them:

Scroll to bottom of page....

[http://www.ubuntu.com/getubuntu/releasenotes/1004](http://www.ubuntu.com/getubuntu/releasenotes/1004)


This works fine on x64 btw.

Cheers!

---

