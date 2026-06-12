---
title: "Can we have usplash as an option?"
date: 2010-02-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by phenest on 2010-02-28
I know there's a lot of work going on making plymouth work, but what if I have a fast machine (I do as it happens) and it's gone in the blink of an eye? Can I have the option of a basic boot screen like usplash? I have no interest in plymouth and would remove it even if it worked.

I don't wish to start a debate as to which is better, as I'm truly not interested. I just want a plain boot screen without plymouth. I'd be happy if the screen went blank. A fancy boot screen is a pointless exercise to me.

What are the alternatives?

---

### Post by Didius Falco on 2010-02-28
I've been wondering that as well. I was actually doing some searching yesterday to see what I could find out about removing both usplash and plymouth and just have a regular old boot up w/o the splash screen stuff. No luck on the searches, as yet...

---

### Post by VMC on 2010-02-28
I read the manual and I too have no idea what Plymouth brings to the table. It appears we're better off without it. The only thing I see it does is splash a ubuntu logo on boot up and shutdown.

---

### Post by sparker256 on 2010-02-28
> **VMC said:**
> I read the manual and I too have no idea what Plymouth brings to the table. It appears we're better off without it. The only thing I see it does is splash a ubuntu logo on boot up and shutdown.

Since I have never seen that on my desktop just a bar at the bottom of the screen I am not sure what it brings to the table. I did see the ubuntu logo on my girlfriends netbook and notebook. For as much grief as it seems to cause after we have booted (double logins, no auto login, etc) just not sure. I still have it installed but I am not sure why at this point in the development process.

Bill

---

### Post by VMC on 2010-02-28
Plymouth effects every video hardware differently. I have an Intel and it now works - it didn't use too. nVidia and ATI suffer differently using plymouth.

---

### Post by exploder on 2010-02-28
> Plymouth effects every video hardware differently. I have an Intel and it now works - it didn't use too. nVidia and ATI suffer differently using plymouth.

There has to be a resolution for this because Plymouth works fine in Mandriva and Fedora now.

---

### Post by ronacc on 2010-02-28
I have no use for plymouth or any other boot splash for that mater I always remove quiet and splash from my boot line anyway , the only time I pay any attention to my machine during boot is if there is a problem .

---

### Post by emarkay on 2010-02-28
Plymouth - just say no.

I deleted it and I don't notice a difference; except there are no more crashes and other related bovine fecal matter... :)

---

### Post by exploder on 2010-02-28
I like Plymouth when its working right, it adds professionalism to the boot experience. I think the developers will get the bugs out of Plymouth before too long.

---

### Post by katie-xx on 2010-02-28
> **exploder said:**
> There has to be a resolution for this because Plymouth works fine in Mandriva and Fedora now.
[COLOR=Blue]
I can absolutely assure you that Plymouth does not work fine in Fedora :P)
I know for a fact that many people have walked away from Fedora because of problems with Plymouth.
I happen to think Fedora is the best distro available. However, its very very difficult to set up correctly and people who cant get certain features running properly tend to get told to clear off if they ask for help in the Forums.
Ubuntu is a more people friendly community so maybe this is the chance for Plymouth either to work or otherwise.
Fingers crossed yeah ? :):)

Kate[/COLOR]

---

### Post by Regenweald on 2010-02-28
I just uninstalled plymouth, I use the nvidia binary driver which does not support KMS so I suppose it would not work anyway. A little message pops up saying mountall could not connect to plymouth, then I get my desktop. I guess that would be termed "ugly" but my boot is pretty fast in Lucid so I don't care really :)

---

### Post by phenest on 2010-03-01
But what are the alternatives? Or is removing Plymouth the only one?

---

### Post by recluce on 2010-03-01
I would also suggest to ditch plymouth for now. usplash on Jaunty worked better for me than anything since. Also, there seems to be a weired relation between the letter "2" and plymouth on some systems, see my problem in this thread:

[http://ubuntuforums.org/showthread.php?t=1417140](http://ubuntuforums.org/showthread.php?t=1417140)

Turned out that plymouth is the culprit there, too.

---

### Post by MacUntu on 2010-03-01
We are here to help making it work, not to ditch everthing that makes our TESTING systems unstable.

---

### Post by moore.bryan on 2010-03-01
> **VMC said:**
> I read the manual and I too have no idea what Plymouth brings to the table. It appears we're better off without it. The only thing I see it does is splash a ubuntu logo on boot up and shutdown.

As I had it explained to me, Plymouth does more than just give a "pretty" boot logo. Apparently, it operates directly with the hardware without the need for a running X server, making the whole boot process faster. The issues any Ubuntu-er have are related to working out the kinks of Plymouth. Fedora mainly does that through "hooks" with other programs; e.g. GDM.

---

### Post by moore.bryan on 2010-03-01
> **katie-xx said:**
> [COLOR=Blue]
I can absolutely assure you that Plymouth does not work fine in Fedora :P)
I know for a fact that many people have walked away from Fedora because of problems with Plymouth.
I happen to think Fedora is the best distro available. However, its very very difficult to set up correctly and people who cant get certain features running properly tend to get told to clear off if they ask for help in the Forums.
Ubuntu is a more people friendly community so maybe this is the chance for Plymouth either to work or otherwise.
Fingers crossed yeah ? :):)

Kate[/COLOR]

I've never had an issue with my Fedora install, but that doesn't mean what you write isn't true. I do, however, *completely* agree it's better to have Plymouth in Ubuntu because whatever could be wrong with it is likely to get fixed because of the community's undying willingness to progress Linux.

---

### Post by recluce on 2010-03-01
> **MacUntu said:**
> We are here to help making it work, not to ditch everthing that makes our TESTING systems unstable.

Certainly not everything. But some gadget that would display a pretty picture during all of 20 seconds of the boot process? Especially for a LTS release, I fully believe that Ubuntu should focus on stability. Plymouth seems to be extremely unstable with less than 2 months to go until release date. So usplash might be the better solution for Lucid. Bring back plymouth once it is more stable.

---

### Post by 23meg on 2010-03-01
> **recluce said:**
> Bring back plymouth once it is more stable.

Do you have a plan for making it "more stable", without testing?

---

### Post by exploder on 2010-03-01
> Do you have a plan for making it "more stable", without testing?

That is a valid point.

---

### Post by Didius Falco on 2010-03-01
I'm fine with testing it, but when there is a problem with it that has been reported but not yet fixed, I don't see the utility in running it until a new version is released. 

All that tests is your patience and/or sanity. <G>

Once a newer version is released, I'll re-enable it and test it, and if I find a problem that umpteen other people haven't already filed a bug report on, I'll file a new one, gladly. 

My curiosity about booting without using either usplash or plymouth is to learn what, if anything, these packages do besides the splash screen (which is not only not something I care about/want, but something I'd personally rather not have - I actually like watching the text scroll by and seeing what's going on), and the feasibility of not having one at all.

The more I learn, the more useful I can be in testing future versions, and since I'm not a programmer, I'm learning as I go.

---

### Post by exploder on 2010-03-01
Once your system runs a disk check you will find that Plymouth is running. I guess I have more patience than some. :)

---

### Post by recluce on 2010-03-01
> **23meg said:**
> Do you have a plan for making it "more stable", without testing?

The problem that I have with plymouth has been filed on launchpad - what is the point for me to further test something that has already been reported broken - unless they release a new version?

---

### Post by Mr. Picklesworth on 2010-03-01
> **MacUntu said:**
> We are here to help making it work, not to ditch everthing that makes our TESTING systems unstable.

Thank you!

In the ideal world, I hope everyone having trouble with Plymouth has made at least some attempt to trace the issue and get it fixed. It would be a *real shame* if everyone employed easy workarounds and the implementation remained flawed for the final release.


> **recluce said:**
> The problem that I have with plymouth has been filed on launchpad - what is the point for me to further test something that has already been reported broken - unless they release a new version?

Remember to keep an eye on the bug report and try to confirm when a fix is proposed. It helps a lot with the lower level stuff :)

---

### Post by VMC on 2010-03-01
> **Mr. Picklesworth said:**
> .. It would be a *real shame* if everyone employed easy workarounds and the implementation remained flawed for the final release.


In that case they will be doing what their doing now...remove it. So everyone looses.

Although in my case it now works. I had created an track a couple of related Plymouth reports. Mine got fixed, but it appears ATI and nVida users not so much. My Intel i865 works, but some other Intel drivers still fail Plymouth.

---

### Post by dagrump on 2010-03-01
I put together a AMD & ATI based system for testing on Saturday & installed A3, I haven't removed plymouth. I can hit enter w/o getting kicked back to the login screen, I consider that progress.
Of course I have not tried to install non default drivers yet, so things could not be as it appears. At the moment things on this box are fine, I'll do reinstalls on the other test boxes when I have time, but I have not had good luck with the systems w/ nvidia cards.
This critter will get a nvidia card sooner or later, spare parts pile has a couple. But for the time being it seems to work w/o removing plymouth.
Of course if something renders the install unusable why wouldn't you remove it? Can't expect someone to try to just put up with it, testing be damned, it's borked. 
Guess I'll see what happens with the other boxes when I have time to reinstall.

---

### Post by phenest on 2010-03-02
> **23meg said:**
> Do you have a plan for making it "more stable", without testing?

Yes, and no.

> **exploder said:**
> That is a valid point.

Not entirely.

Is Plymouth likely to work on 99% of hardware by the time the Lucid RC is released? If not, then Plymouth should not be the default boot splash, yet. That way we can test it for a future release.

But my original thought was, is there an alternative I can install (something simpler like usplash), that I can use if I don't want/need or can't use (slow machine) Plymouth?

---

### Post by VMC on 2010-03-02
> **phenest said:**
> But my original thought was, is there an alternative I can install (something simpler like usplash), that I can use if I don't want/need or can't use (slow machine) Plymouth?Agreed. It appears we danced around the question.

It should have been, no, with reasons, or yes with alternatives.

Interestingly I found xsplash installed. Not sure if plymouth is tied to it, but...
```
$ aptitude show xsplash
Package: **xsplash**
State: installed
Automatically installed: no
Version: 0.8.5-0ubuntu1
Priority: optional
Section: misc
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 98.3k
Depends: libatk1.0-0 (>= 1.20.0), libc6 (>= 2.3.6-6~), libcairo2 (>= 1.2.4),
         libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78), libfontconfig1 (>=
         2.4.0), libfreetype6 (>= 2.2.1), libglib2.0-0 (>= 2.16.0), libgtk2.0-0
         (>= 2.14.0), libpango1.0-0 (>= 1.14.0), libxcomposite1 (>= 1:0.3-1),
         ubuntu-xsplash-artwork | xsplash-artwork
Description: X based bootsplash
 xsplash is a userspace application that uses the X interface to draw a splash
 screen at boot.
Homepage: https://launchpad.net/xsplash
```

---

### Post by DoeRayMe on 2010-03-02
> **VMC said:**
> Agreed. It appears we danced around the question.

It should have been, no, with reasons, or yes with alternatives.

Interestingly I found xsplash installed. Not sure if plymouth is tied to it, but...
```
$ aptitude show xsplash
Package: **xsplash**
State: installed
Automatically installed: no
Version: 0.8.5-0ubuntu1
Priority: optional
Section: misc
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 98.3k
Depends: libatk1.0-0 (>= 1.20.0), libc6 (>= 2.3.6-6~), libcairo2 (>= 1.2.4),
         libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78), libfontconfig1 (>=
         2.4.0), libfreetype6 (>= 2.2.1), libglib2.0-0 (>= 2.16.0), libgtk2.0-0
         (>= 2.14.0), libpango1.0-0 (>= 1.14.0), libxcomposite1 (>= 1:0.3-1),
         ubuntu-xsplash-artwork | xsplash-artwork
Description: X based bootsplash
 xsplash is a userspace application that uses the X interface to draw a splash
 screen at boot.
Homepage: https://launchpad.net/xsplash
```

ubuntu-desktop still depends on it, tried to remove it but pulls ubuntu-desktop too but not plymouth, so maybe the dependency will be changed soon?

---

### Post by VMC on 2010-03-02
> **DoeRayMe said:**
> ubuntu-desktop still depends on it, tried to remove it but pulls ubuntu-desktop too but not plymouth, so maybe the dependency will be changed soon?
I find a lot of apps are tied to ubuntu-desktop. Or rather I ubuntu-desktop is tied to a number of apps. I removed as much as I can regarding Evolution before it too will pull ubuntu-desktop.

---

### Post by DoeRayMe on 2010-03-02
> **VMC said:**
> I find a lot of apps are tied to ubuntu-desktop. Or rather I ubuntu-desktop is tied to a number of apps. I removed as much as I can regarding Evolution before it too will pull ubuntu-desktop.

Same here reguarding evolution xD

---

### Post by recluce on 2010-03-03
I gave plymouth another try after I applied a significant amount of updates today (including new kernel and new gdm version).

Still no joy, first session after boot still crashes when pressing the "2" key, no other sign of plymouth but the ugly blue bars during boot. Removed plymouth again for now.

---

### Post by 23meg on 2010-03-03
> **phenest said:**
> 
Is Plymouth likely to work on 99% of hardware by the time the Lucid RC is released? If not, then Plymouth should not be the default boot splash, yet. That way we can test it for a future release.


For all but the most trivial software, that's very hard to know in advance without testing coverage on "99% of hardware".

[QUOTE=phenest]But my original thought was, is there an alternative I can install (something simpler like usplash), that I can use if I don't want/need or can't use (slow machine) Plymouth?[/QUOTE]

Well, there is USplash itself, which is why I didn't really understand the original question. USplash exists as an option already, albeit maybe without some of the benefits of Plymouth, right? 

And there's also Splashy.

---

### Post by phenest on 2010-03-03
> **23meg said:**
> For all but the most trivial software, that's very hard to know in advance without testing coverage on "99% of hardware".

Which is why Plymouth shouldn't be default until then (or as close to 99% as permissible).

> **23meg said:**
> Well, there is USplash itself, which is why I didn't really understand the original question. USplash exists as an option already, albeit maybe without some of the benefits of Plymouth, right? 

And there's also Splashy.

I thought usplash was being dumped in favour of Plymouth, but that's good to know. The benfits of Plymouth are out-weighed by something that works.

---

### Post by 23meg on 2010-03-03
> **phenest said:**
> Which is why Plymouth shouldn't be default until then (or as close to 99% as permissible).

We can't hope to get any piece of software as close to working with all known hardware as possible under all conditions without subjecting it to as broad testing as possible.

> **phenest said:**
> I thought usplash was being dumped in favour of Plymouth, but that's good to know. The benfits of Plymouth are out-weighed by something that works.

USplash is in Universe.

---

### Post by phenest on 2010-03-03
```
21:33: ~ $ sudo apt-get install usplash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libusplash0 usplash-theme-ubuntu
[B]The following packages will be REMOVED
  gdm gdm-guest-session indicator-session ubuntu-desktop[/B]
The following NEW packages will be installed
  libusplash0 usplash usplash-theme-ubuntu
0 upgraded, 3 newly installed, 4 to remove and 4 not upgraded.
Need to get 189kB of archives.
After this operation, 7,512kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

---

### Post by Neezer on 2010-03-03
> **ronacc said:**
> I have no use for plymouth or any other boot splash for that mater I always remove quiet and splash from my boot line anyway

How do you do this? I assume it is a text file somewhere and I can just go in and delete a few lines....sounds like a neat trick...does it speed up booting at all?

---

### Post by recluce on 2010-03-03
> **23meg said:**
> We can't hope to get any piece of software as close to working with all known hardware as possible under all conditions without subjecting it to as broad testing as possible.



I realize that - and that is why I installed Lucid Alpha in the first place and giving feedback. However: Lucid is going to be a LTS version, which should focus on stability. Something that is as unstable as plymouth right now should not be in any LTS release. While I do hope that the problems with plymouth can be ironed out before release date, I would really hate to see "broad testing" going on with the users of the final release. Also, the importance of a package should be weighed. plymouth seems to be very low on the ladder as far as importance is concerned.

So: unstable package + low importance + upcoming LTS release = ???

For me the answer would be: -plymouth, +usplash

But again, I still hold hope that our testing will contribute to a fix in the eight weeks remaining.

---

### Post by exploder on 2010-03-03
Have a little patience with Plymouth, the developers will get it working.

---

### Post by katie-xx on 2010-03-03
[SIZE=2]I carry lots of doubts about the wisdom of utilising Plymouth. However, I do recognise my doubts are probably there because I could never get it working properly in fedora. Now the ATI driver situation has improved I might revisit a Fedora install to see what the situation is like now and report back here.

**Can we use something else the OP asks.**

Well I dont know but it would certainly be useful to have an authoritative answer we could put in the bank if things dont improve with Plymouth.

In the meantime it doesnt make a whole lot of sense to stop testing something which isnt playing ball or behaving itself in an Alpha release.
If, and only if, the problems persist until the final release, then it might be time to use whatever alternative there might be.
However .. we do need a straight answer and a little bit of feedback wouldnt go astray either :) ..Yes I know the devs dont read these forums but hey someone on here may be able to give good informed feedback.

Kate
[/SIZE]

---

### Post by VMC on 2010-03-03
> **exploder said:**
> Have a little patience with Plymouth, the developers will get it working.

I think this is the key here regarding Plymouth. For the longest time it didn't work on my machine and I reported 1 bug and watched another one and viewed some comments that indeed work is being done. Then one of the updates fixed my booting problems with Plymouth. 

there's a few things tied to plymouth, GDM, and you video card. Maybe more.

---

### Post by theanswriz42 on 2010-03-04
I certainly find the mentality of the development here interesting in the respect that most organizations (with good reason) cut a release of a product with stable features by default and offer extras or less mature apps/packages/whatever as an option for folks to try out for future versions. Based on what I'm reading here, the folks doing the development for Ubuntu seem to think the opposite is the best approach, which in my opinion can be dangerous. 

There was a quote earlier in this thread saying:

> We can't hope to get any piece of software as close to working with all known hardware as possible under all conditions without subjecting it to as broad testing as possible.

Which is fair, but "testing" is a very early part of the release process. Typically in development you start with testing, often times using more of the cutting edge features offered in a previous version, then once things are less in flux, you cut a release. Typically considered an "alpha".

From that point, you hand the release to QA to do unit tests, smoke tests, etc., gather information, and return their findings to the developers for refinement and bug fixes. This goes on back and forth until things seem stable enough to be considered a beta. Once a beta is cut, new features typically are less likely to be implemented past that point unless they are deemed critical and/or fix the proverbial "show stoppers". The beta goes back to QA for the next round of testing and the fun begins all over again. 

Eventually, most of the bugs that can be caught by QA are resolved and a stable release is ready to be cut for the general public (or whoever the customer is). Extra cutting edge features are then made available for the public to test so you can get a good sampling and bug reports from the user base trying out those features, and then it's determined whether or not to include those features into the next release or ditch them depending on whether the benefits outweigh the cost. 

From my experience, I've seen that when you try and inject cutting edge and minimally tested features into a release, you generally run into more problems than not. This is no different than what's already been said by the Ubuntu staff who's commented in this thread with respect to plymouth. If something doesn't work with the most mainstream hardware that's generally accepted to be well supported under linux (ie. Nvidia chipsets), it probably shouldn't go into the release and should be refined for the next one; unless something better comes along.

---

### Post by katie-xx on 2010-03-04
[SIZE=2]Its entirely possible some users might have to settle for no graphical splash.
This was the Fedora experience for many people although several "fixes" were proposed.
Sometimes these worked for some people and sometimes they didnt.
Im not certain if its allowable to link to Fedora advice here ..if not .. my apologies and I will edit out once notified. However here is a link to one such solution which worked for some.
[http://www.my-guides.net/en/content/view/174/26/2/13/](http://www.my-guides.net/en/content/view/174/26/2/13/)

You need to scroll down to Graphical boot problem.

Im still hopeful that the Ubuntu devs might come up with a universal solution but it never happened in Fedora.

Kate[/SIZE]

---

### Post by Ibidem on 2010-03-04
On the Arch forums, I saw something about [uvesafb]("http://wiki.archlinux.org/index.php/Uvesafb") and "v86d"...Sounds like a bit of trouble to set up, but it can do a bit.  Uvesafb is built as a module by default (CONFIG_FB_UVESA=m), so...

Ibidem

---

### Post by ronacc on 2010-03-05
if they could deliver on their 10 sec boot we wouldn't need a splash .

---

### Post by moore.bryan on 2010-03-05
> **phenest said:**
> Which is why Plymouth shouldn't be default until then (or as close to 99% as permissible).
I thought usplash was being dumped in favour of Plymouth, but that's good to know. The benfits of Plymouth are out-weighed by something that works.
usplash and plymouth, in essence, do two very different things. usplash is just for "splashing;" plymouth involves more direct interaction with graphics hardware without invoking x.

---

### Post by 23meg on 2010-03-05
> **phenest said:**
> ```
21:33: ~ $ sudo apt-get install usplash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libusplash0 usplash-theme-ubuntu
[B]The following packages will be REMOVED
  gdm gdm-guest-session indicator-session ubuntu-desktop[/B]
The following NEW packages will be installed
  libusplash0 usplash usplash-theme-ubuntu
0 upgraded, 3 newly installed, 4 to remove and 4 not upgraded.
Need to get 189kB of archives.
After this operation, 7,512kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

That seems to be because the usplash and gdm packages have each other in their "Breaks:" field, which means that you can have both installed, but one needs to be deconfigured. I don't know if this is temporary; it may be due to lack of human hours needed to adapt USplash to GDM and initialization changes in this cycle.

---

### Post by 23meg on 2010-03-05
> **ronacc said:**
> if they could deliver on their 10 sec boot we wouldn't need a splash .

You know that the 10 second goal was for reference hardware with an SSD, right? Plymouth and the framebuffer were originally not meant to be started on machines with SSDs, but that seems to have partly changed "for now", according to the Plymouth changelog.

---

### Post by moore.bryan on 2010-03-05
> **23meg said:**
> That seems to be because the usplash and gdm packages have each other in their "Breaks:" field, which means that you can have both installed, but one needs to be deconfigured. I don't know if this is temporary; it may be due to lack of human hours needed to adapt USplash to GDM and initialization changes in this cycle.
Plymouth requires certain gdm "hooks," so if you're installing usplash, you need to uninstall the gdm that's there and reinstall it so the hooks aren't activated.

---

