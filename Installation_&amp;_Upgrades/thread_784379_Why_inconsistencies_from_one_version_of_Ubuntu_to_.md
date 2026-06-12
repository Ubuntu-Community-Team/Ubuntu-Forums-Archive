---
title: "Why inconsistencies from one version of Ubuntu to the next"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2008-05-06
I really don't understand why it is that you can have applications that are listed in Synaptic for use on the Ubuntu operating system and they will work, on say, the Gutsy version of Ubuntu but then when the **NEW & IMPROVED** version of Hardy Ubuntu comes out, they can no longer either be installed and/or ran.

To give you an example the Xsensor program installed and worked perfectly under Gutsy but will no longer install and run under Hardy.  And my guess is, that there are many, many more examples like this.  I know of at least a few, that I have ran into AND reported as bugs thru-out the alpha and beta versions of Hardy and apparently no effort has been made to fix these problems.

What good is a rock solid O/S with all kind of nice little features, if you can not get applications to install and run on it.

And I am not looking for some work-a-round fix for getting these to install and run, I don't want to be a programmer, I just want an O/S that I can be a good USER of & get my work done.

I just don't think the developers of this O/S are taking into account ALL of the ramifications of the changes to certain things that they are making when developing the newer versions of this O/S.

Thanks, for listening to my vent.

---

### Post by jimv on 2008-05-06
I'm pretty sure it has something to do with those programs being compiled with older versions of the kernel and libraries and what not.  Usually you can get them to work by downloading the source code and building them manually.  Other than that, you have to wait for someone else to build the program for Hardy and post a deb in the repos.

> 
I just don't think the developers of this O/S are taking into account ALL of the ramifications of the changes to certain things that they are making when developing the newer versions of this O/S.

Well, unlike the commercial software world, Open Source programmers don't have a customer base to please, so pretty much anything goes.  If no one uses Ubuntu, well...no one's losing their job or money.  It's a hobby kind of thing, and you're using the fruit of it.

EDIT
I just tried xsensors and it worked ok for me.

---

### Post by fixitdude on 2008-05-06
It's possible you have a corrupted file or two, you might try a reinstall of the problem programs (after turning off CD repositories so it goes to the net to get them).

But I do understand what you are saying. I think people jump on new versions of the OS too quickly like with all the hardy problems so far. Someone makes a post that the new version is out and everyone gets it before it's really tested on a lot of different computers.

There should be 3 sorts of ubuntu people, beta testers, "on edge" testers, and then those who want to know it's been fully tested and reports of problems are minimal.

Some of that last one would consist of a main ubuntu distributed install script that is *always* downloaded from the net (even with a CD install), it runs and then it fixes all the little known glitches before the first boot.

And why don't we have a "sticky" problem FAQ that has a lot of these fix suggestions in it that everyone keeps asking about over and over?

Would people read that first?

I've seen a number of posts where a simple search would have gotten the answer, but people never seem to want to try search first.

Call it "HARDY UPGRADE PROBS? - READ THIS FIRST, Lot of answers in one place", Caps to get attention.

---

### Post by mikewhatever on 2008-05-06
Venting is ok, everyone needs some from time to time, but why vent in the Upgrading & Installation section, when there is plenty of space and attentive ears in Ubuntu Testimonials or Cafe?

---

### Post by forestpixie on 2008-05-06
> To give you an example the Xsensor program installed and worked perfectly under Gutsy but will no longer install and run under Hardy.

Except it does - had to change the launcher in the menu to 

/usr/bin/xsensors -c /etc/sensors3.conf

and it works for me, of course that doesn't help with this

> And I am not looking for some work-a-round fix for getting these to install and run

---

### Post by ricardisimo on 2008-05-06
> **jimv said:**
> Well, unlike the commercial software world, Open Source programmers don't have a customer base to please, so pretty much anything goes.  If no one uses Ubuntu, well...no one's losing their job or money.  It's a hobby kind of thing, and you're using the fruit of it.

That's not entirely true of Ubuntu, which has rather extensive professional support and financing behind it... still, your point is well-taken.

---

### Post by loell on 2008-05-06
> **wpshooter said:**
> 
I just don't think the developers of this O/S are taking into account ALL of the ramifications of the changes to certain things that they are making when developing the newer versions of this O/S.


I think they do , its just that its overwhelming them. the issue is quite broad , probably better management of bug feedback?  and the ever undying issue of the proposal of longer development cycle.

---

### Post by Stik on 2008-05-06
Possibly hasn't been rebuilt to run on Hardy yet?

---

### Post by wpshooter on 2008-05-07
> **loell said:**
> I think they do , its just that its overwhelming them. the issue is quite broad , probably better management of bug feedback?  and the ever undying issue of the proposal of longer development cycle.

I agree, I think they are trying to accomplish too much in too short of a time span.

---

### Post by jimv on 2008-05-07
> **mikewhatever said:**
> Venting is ok, everyone needs some from time to time, but why vent in the Upgrading & Installation section, when there is plenty of space and attentive ears in Ubuntu Testimonials or Cafe?

They should have a "drunken rants" forum here.'

---

### Post by wpshooter on 2008-05-07
> **jimv said:**
> 
EDIT
I just tried xsensors and it worked ok for me.

Did you try it on Hardy ?

Thanks.

---

### Post by wpshooter on 2008-05-10
> **wpshooter said:**
> Did you try it on Hardy ?

Thanks.

Since I received no answer, I assume the answer is NO.

I just tried the installation of Xsensors on Hardy again and it STILL does not work.  I sure wish someone would fix this.

---

### Post by forestpixie on 2008-05-10
I have got them working in hardy - had to amend the launcher to include path to /etc/modules and add -c to specify the lm-sensors file.
Have no idea what changed with it, but this works for me


/usr/bin/xsensors -c /etc/sensors3.conf

Edit - path

---

### Post by wpshooter on 2008-05-10
> **forestpixie said:**
> I have got them working in hardy - had to amend the launcher to include path to /etc/modules and add -c to specify the lm-sensors file.
Have no idea what changed with it, but this works for me


/usr/bin/xsensors -c /etc/modules

Now if we could just get someone to fix this so that all of us that don't know how to do these changes could get the program to work when it is initially installed.

Thanks.

---

### Post by forestpixie on 2008-05-10
Yea - I agree - I managed to work it out from a few sources and the man page - but it could have been easier.

Glad it helped - although I did post this 3 days ago as well :)

---

### Post by Stupkid on 2008-05-10
Here is some food for thought...  

How many of you find a bug in a package or figure out a workaround in a buggy installation and never report it back to the package maintainer or upstream developer of the software?  That is part of the problem.  If things never leave this forum then the developers are most likely never going to know.  Just about every software package for Ubuntu has some bug tracking system and if you identify a problem you should report it so that it can be fixed.  That is one of the differences between open source and commercial software; you need to participate.

So, while getting workarounds in place is great for the time being, if you find a bug please report it.  Every developer cannot monitor every web forum out there for potential issues with their software.

---

### Post by forestpixie on 2008-05-10
Almost like it was at the beginning of May you mean :)

[https://bugs.launchpad.net/ubuntu/+source/xsensors/+bug/225362](https://bugs.launchpad.net/ubuntu/+source/xsensors/+bug/225362)

---

