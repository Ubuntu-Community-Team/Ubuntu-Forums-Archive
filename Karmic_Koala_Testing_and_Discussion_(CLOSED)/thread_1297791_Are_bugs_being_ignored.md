---
title: "Are bugs being ignored?"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2009-10-22
Or is this part of the "freeze" process?

I really do wonder:

[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/451813](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/451813)

[https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/455102](https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/455102)

And it's discouraging to read something like this:

[http://0pointer.de/blog/projects/pa-in-ubuntu.html](http://0pointer.de/blog/projects/pa-in-ubuntu.html)

But I still like Ubuntu better than any other distro and I do lot's of distro-hopping!

I'm just curious:confused:

Since joining the Ayatana discussions I see lots of folks arguing, dis"cussing", and generally expending energy that could be better spent.

The mods can feel free to move or kill this but I've been luvin' Ubuntu for 21 months and I don't want to see this go "bad"!

---

### Post by IanW on 2009-10-22
From the "Ubuntu 9.10 Release Candidate - Please Read Before Testing" Sticky:-

> **23meg said:**
> 

Note that since we're in the final phase of the development cycle, bug fixing focus will be restricted to high-impact showstopper bugs, and changes from this point on are only permitted at the discretion of the release manager.



So I'd say we're currently in a deep,deep freeze right now.

---

### Post by 23meg on 2009-10-22
It's inevitable that bug fixing will be focused on high-impact bugs this late in the cycle, since any modification without extensive testing can inadvertently cause breakage.

As for the specific bugs you've filed: you seem to want to fix things by resorting to kludges rather than through proper debugging. That makes bugs very hard to understand and respond to for triagers. Your problem in the first one is not that you don't have "VIA toggles" on gnome-volume-control; it's that you don't have an appropriate volume level out of the box. In the second, it's not that you can't install HPLIP from the website (which you shouldn't have to, and isn't necessarily a bug); it's that your (unknown!) printer or scanner is not working out of the box. 

I don't know and don't have time to check if you filed proper bug reports regarding the dysfunctions of your specific hardware; if you haven't, and you need help with that, please start separate threads for that purpose.

---

### Post by kansasnoob on 2009-10-22
> **23meg said:**
> It's inevitable that bug fixing will be focused on high-impact bugs this late in the cycle, since any modification without extensive testing can inadvertently cause breakage.

As for the specific bugs you've filed: you seem to want to fix things by resorting to kludges rather than through proper debugging. That makes bugs very hard to understand and respond to for triagers. Your problem in the first one is not that you don't have "VIA toggles" on gnome-volume-control; it's that you don't have an appropriate volume level out of the box. In the second, it's not that you can't install HPLIP from the website (which you shouldn't have to, and isn't necessarily a bug); it's that your (unknown!) printer or scanner is not working out of the box. 

I don't know and don't have time to check if you filed proper bug reports regarding the dysfunctions of your specific hardware; if you haven't, and you need help with that, please start separate threads for that purpose.

I always appreciate your responses. In fact, having followed the development cycle since Hardy, I can absolutely say you're exceptional! That's one of the reasons I posted my question here.

I'm not angry. I can almost always find a "work-around" for any issue and if not, when I get frustrated I can just boot into Jaunty, or Mint, or (if the earth is almost stopping) even Windows.

But the VIA toggle thing is totally valid. I've built over 30 machines with sound cards that depend on that! If my bug report is insufficient how did I write this:

[http://ubuntuforums.org/showpost.php?p=8144349&postcount=24](http://ubuntuforums.org/showpost.php?p=8144349&postcount=24)

I also ran the HPLIP script to verify the other bug.

What else must I do?

---

### Post by Keyper7 on 2009-10-22
> **kansasnoob said:**
> Or is this part of the "freeze" process?

I really do wonder:

[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/451813](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/451813)

[https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/455102](https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/455102)

I've seen lots of bugs being eventually fixed despite silence in the Launchpad report.

> **kansasnoob said:**
> And it's discouraging to read something like this:

[http://0pointer.de/blog/projects/pa-in-ubuntu.html](http://0pointer.de/blog/projects/pa-in-ubuntu.html)

You are only hearing one side of the story. Did you try to talk to the Ubuntu Pulseaudio maintainers before jumping to conclusions?

> **kansasnoob said:**
> Since joining the Ayatana discussions I see lots of folks arguing, dis"cussing", and generally expending energy that could be better spent.

Care to provide *evidence* that it could be better spent?

Please, give me proof that:

1) The developers discussing in Ayatana list are not working hard enough on other things. To make such claim about top contributors such as David Siegel, for example, is laughable.

2) The developers discussing in Ayatana list would be more useful somewhere else. Do you think a usability designer like Celeste Lyn Paul would be more useful discussing the user experience in the list or helping to fix low-level ALSA bugs?

3) Interrupting the discussions about Ayatana would automatically mean that progress on other areas would be automatically accelerated. This is not a Dilbertesque office where the pointy-haired boss says "this is more important, stop what you're doing and work only on it now". People should work where they feel confortable and confident.

---

### Post by RedG on 2009-10-22
I think it's a bit hopeful to be expecting a bug-fix after just 5-7 days. Yes, sometimes the developers are really fast. But if the bug is hard to catch, it can take some time to fix it. That said, I can only as the others refer to the freeze.

---

### Post by 23meg on 2009-10-22
> **kansasnoob said:**
> I always appreciate your responses. In fact, having followed the development cycle since Hardy, I can absolutely say you're exceptional! That's one of the reasons I posted my question here.

I'm not angry. I can almost always find a "work-around" for any issue and if not, when I get frustrated I can just boot into Jaunty, or Mint, or (if the earth is almost stopping) even Windows.

But the VIA toggle thing is totally valid. I've built over 30 machines with sound cards that depend on that! If my bug report is insufficient how did I write this:

[http://ubuntuforums.org/showpost.php?p=8144349&postcount=24](http://ubuntuforums.org/showpost.php?p=8144349&postcount=24)

I also ran the HPLIP script to verify the other bug.

What else must I do?

Thanks for your kind words; but I didn't mean to say your report was insufficient, rather that it focused on the wrong part: the symptoms rather than the problem itself. And I don't get what the thread you pointed to has to do with those bugs.

Good places to start for debugging sound and printing issues are:

[https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

You should take a look at those instructions and file new bug reports focusing on the root of the problem ("Very low volume with [*your soundcard*]", "[*your printer*] is not detected"] accordingly. And if you need help doing that, start appropriately titled threads and ask for it.

---

### Post by slakkie on 2009-10-22
> **kansasnoob said:**
> 
[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/451813](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/451813)

[https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/455102](https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/455102)


Could be because no-one verified your bugs, so it is not being looked at. Could be the freeze. I know I reported bugs and they have been solved quickly (within days/weeks). But I also filed bugs which are still open after 2/3 years..

Regarding the HPLIP bug I think it is filed incorrectly. You are filing a bug that you cannot compile something from source because of missing dependencies. You need to figure out which dependencies need to be fulfilled. I don't consider it to be a bug.
The bug you should be reporting is the fact that something in hplip package of Karmic is not functioning fine (which is the reason why you want to install from source, so you can make use of your printer/scanners). If I was a developer of hplib I would mark your bug as invalid on these grounds.

To see which build dependencies you need to have for hplib:
```

apt-cache showsrc hplip
apt-get -s build-dep hplip # remove -s to actually install the build-deps

```

To remove the build-deps:
```

sudo aptitude markauto $(apt-cache showsrc hplib | grep Build-Depends | perl -p -e 's/(?:[\[(].+?[\])]|Build-Depends:|,|\|)//g')

```

What I usually do when I really want attention for my bugs is to join #ubuntu-bugs on freenode (or #ubuntu-motu). The people in there can help you with the bug and to get the ball rolling. Sometimes it is as easy as subscribing a particular group.

---

### Post by kansasnoob on 2009-10-22
Thanks for maintaining a good humor.

The point of that link was to show I'm not a complete "know-nothing" that's just out to "trash" Ubuntu.

As far as the "no" VIA controls, that's the best I can do I guess. I can no longer control my sound. Period!

In the next couple of days I'll explore better bug filing procedures.

---

### Post by Lazy123 on 2009-10-22
There are also packages that have been completely broken for several months without package maintainer commenting anything. Like this [electricsheep bug]("https://bugs.launchpad.net/ubuntu/+source/electricsheep/+bug/372040"). In that case it should be a simple sync from Debian but nothing has been done or even commented.

---

### Post by kansasnoob on 2009-10-22
> **slakkie said:**
> Could be because no-one verified your bugs, so it is not being looked at. Could be the freeze. I know I reported bugs and they have been solved quickly (within days/weeks). But I also filed bugs which are still open after 2/3 years..

Regarding the HPLIP bug I think it is filed incorrectly. You are filing a bug that you cannot compile something from source because of missing dependencies. You need to figure out which dependencies need to be fulfilled. I don't consider it to be a bug.
The bug you should be reporting is the fact that something in hplip package of Karmic is not functioning fine (which is the reason why you want to install from source, so you can make use of your printer/scanners). If I was a developer of hplib I would mark your bug as invalid on these grounds.

To see which build dependencies you need to have for hplib:
```

apt-cache showsrc hplip
apt-get -s build-dep hplip # remove -s to actually install the build-deps

```

To remove the build-deps:
```

sudo aptitude markauto $(apt-cache showsrc hplib | grep Build-Depends | perl -p -e 's/(?:[\[(].+?[\])]|Build-Depends:|,|\|)//g')

```

What I usually do when I really want attention for my bugs is to join #ubuntu-bugs on freenode (or #ubuntu-motu). The people in there can help you with the bug and to get the ball rolling. Sometimes it is as easy as subscribing a particular group.

What blows me away is no bug has been marked ................ not invalid, not nothing!

Then again check out the Ayatana list:

[https://launchpad.net/ayatana](https://launchpad.net/ayatana)

And you're wrong! If you bother to read I was doing testing based on another operators failure and it's a "bug"!

Wait about a week and see how many people start whining!

---

### Post by slakkie on 2009-10-22
> **kansasnoob said:**
> What blows me away is no bug has been marked ................ not invalid, not nothing!

Then again check out the Ayatana list:

[https://launchpad.net/ayatana](https://launchpad.net/ayatana)

And you're wrong! If you bother to read I was doing testing based on another operators failure and it's a "bug"!

Wait about a week and see how many people start whining!
I fail to see why I'm wrong. 

And discussion is good, nothing worse then people not communicating. Software would be of lesser quality if no-one discussed features.

If you think the bug is critical enough, address it to people who can do something about it (in other words, join irc and ask around! or join a maillinglist, developers are not on forums..)

---

### Post by Longinus00 on 2009-10-22
> **kansasnoob said:**
> 

And it's discouraging to read something like this:

[http://0pointer.de/blog/projects/pa-in-ubuntu.html](http://0pointer.de/blog/projects/pa-in-ubuntu.html)



I actually really don't like the original volume adjustment implementation as it makes it pretty tough to easily figure out relative application volumes without opening the sound preferences. What was Lennart trying to accomplish with the flat volumes option, make it so every application can blow out your speakers?

---

### Post by flipper9 on 2009-10-22
With any development, there will always be bugs whether it's called alpha/beta/rc/release.  With Ubuntu, there isn't the large userbase as there is with Windows, and it will take time for these rarer bugs (that don't affect the majority of the current userbase) to be fixed.  Since Karmic is about to be released as final, they want to focus on "showstopper" bugs so "regular" bugs are put to the side for the moment as they focus on getting a release that is "stable enough".  After the release, bugs will continue to be fixed as usual.  

I think as Ubuntu (and Linux as a whole) becomes more and more popular, we'll see the number of these bugs disappear as it gets more testing by a larger number of people. Until then, we are kinda stuck back in the days of Windows 3.1 where you had to have some computer knowledge to get past issues.  It's just a fact that the majority of hardware and software manufacturers develop for Windows and focus their efforts there.  Things will change eventually.

---

### Post by cyberkilla on 2009-10-22
> **flipper9 said:**
> With any development, there will always be bugs whether it's called alpha/beta/rc/release.  With Ubuntu, there isn't the large userbase as there is with Windows, and it will take time for these rarer bugs (that don't affect the majority of the current userbase) to be fixed.  Since Karmic is about to be released as final, they want to focus on "showstopper" bugs so "regular" bugs are put to the side for the moment as they focus on getting a release that is "stable enough".  After the release, bugs will continue to be fixed as usual.  

I think as Ubuntu (and Linux as a whole) becomes more and more popular, we'll see the number of these bugs disappear as it gets more testing by a larger number of people. Until then, we are kinda stuck back in the days of Windows 3.1 where you had to have some computer knowledge to get past issues.  It's just a fact that the majority of hardware and software manufacturers develop for Windows and focus their efforts there.  Things will change eventually.

Now, this is what I don't entirely understand. This isn't a "rolling release"... What does that mean in reality?

I understand that a new version of something is deferred until the next release of Ubuntu. E.g. No Firefox 3 until the next 6 month release.

However, do we still get updates with bug fixes to packages, or only security fixes?

---

### Post by flipper9 on 2009-10-22
> **cyberkilla said:**
> Now, this is what I don't entirely understand. This isn't a "rolling release"... What does that mean in reality?

I understand that a new version of something is deferred until the next release of Ubuntu. E.g. No Firefox 3 until the next 6 month release.

However, do we still get updates with bug fixes to packages, or only security fixes?
I believe, and anyone correct me if I'm wrong, but there are still bug fixes to packages just not releases of newer versions (i.e. new features, major updates).  Some fixes are back-ported, as well as security updates.

Of course, you can always elect to add PPA entries for the maintainers of those applications, and stay on the upgrade bandwagon even though the distribution release is still the same.

---

### Post by cyberkilla on 2009-10-22
> **flipper9 said:**
> I believe, and anyone correct me if I'm wrong, but there are still bug fixes to packages just not releases of newer versions (i.e. new features, major updates).  Some fixes are back-ported, as well as security updates.

Of course, you can always elect to add PPA entries for the maintainers of those applications, and stay on the upgrade bandwagon even though the distribution release is still the same.

Thanks, that makes more sense.

---

### Post by flipper9 on 2009-10-22
I'd think of it this way.  Once 9.10 is released, updates will be more conservative.  There will be no upgrades (unless you enable backports in your repository settings) to Firefox 4.0, Open Office 3.2, the next release of Gnome, etc.  However, they will update with bug-fixes to the current versions.  In reading the docs on the Ubuntu site, they will consider updates to the next version if it increases the overall stability.   Sometimes packages come out in newer versions that fix a lot of bugs.

---

### Post by 23meg on 2009-10-22
> **cyberkilla said:**
> 
However, do we still get updates with bug fixes to packages, or only security fixes?

Relatively high-impact bugs, and security fixes.

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates) explains it.

---

### Post by philinux on 2009-10-22
> **flipper9 said:**
> I believe, and anyone correct me if I'm wrong, but there are still bug fixes to packages just not releases of newer versions (i.e. new features, major updates).  Some fixes are back-ported, as well as security updates.

Of course, you can always elect to add PPA entries for the maintainers of those applications, and stay on the upgrade bandwagon even though the distribution release is still the same.

Click the backports link below in my sig if you've not seen this explained.

---

### Post by flipper9 on 2009-10-22
> **philinux said:**
> Click the backports link below in my sig if you've not seen this explained.
Yes; I already mentioned backports. Thanks :)

---

### Post by castrojo on 2009-10-22
> **Lazy123 said:**
> There are also packages that have been completely broken for several months without package maintainer commenting anything. Like this [electricsheep bug]("https://bugs.launchpad.net/ubuntu/+source/electricsheep/+bug/372040"). In that case it should be a simple sync from Debian but nothing has been done or even commented.

There isn't one package maintainer, it's a team of people. From looking at the bug it probably hasn't been looked at because someoone asked for a sync from Debian but it looks like they didn't subscribe the team that does that: [https://wiki.ubuntu.com/SyncRequestProcess](https://wiki.ubuntu.com/SyncRequestProcess)

Short story: for a sync from debian you need to subscribe the universe sponsors team to get it in the right pile.

---

### Post by emarkay on 2009-10-22
See this post for comments on this issue:
[http://ubuntuforums.org/showthread.php?p=8146424#post8146424](http://ubuntuforums.org/showthread.php?p=8146424#post8146424)

---

### Post by nanog on 2009-10-22
kansasnoob and others,

the pulseaudio rt regression that made lennart go postal has been refiled with patch details:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/452458](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/452458)

Please subscribe and comment if you can add something.

---

### Post by kansasnoob on 2009-10-23
In retrospect this post was a bit inflammatory so I'm going to report myself and ask that it be closed.

Well, I guess it doesn't meet the criteria so would a kindly person like whiprush or 23meg please close this.

---

### Post by 23meg on 2009-10-23
> **kansasnoob said:**
> In retrospect this post was a bit inflammatory so I'm going to report myself and ask that it be closed.

It wasn't really, but I'll close it upon your request.

If you need help with anything about bugs, be it good reporting practices, following up, finding the right package, getting your bugs triaged, that's part of what this forum is for; feel free to start a thread and ask for assistance.

---

