---
title: "Ubuntu Software Store: What it does, and how you can help"
date: 2009-08-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mpt on 2009-08-27
As you may know from previous forum threads [[1]("http://ubuntuforums.org/showthread.php?t=1170534"), [2]("http://ubuntuforums.org/showthread.php?t=1216492")], at the Ubuntu Developer Summit in May, we discussed **AppCenter** — the codename for a new interface for finding, installing, and removing software in Ubuntu.

Now, AppCenter has a brand name: the **[Ubuntu Software Store]("http://launchpad.net/software-store")**. And it has a package in Ubuntu Karmic: [software-store]("apt:software-store").

The objective for Ubuntu 9.10 is for the Store to replace Add/Remove Applications. But there is plenty of work left to do to reach that goal. We're looking for help from artists, copy-editors, GTK/Clutter hackers, interface designers, librarians (!), packagers, Python programmers, and testers. We welcome useful contributions from anyone, regardless of age, gender, or experience.

For details of how you can help, see [the specification]("https://wiki.ubuntu.com/SoftwareStore").

Thanks!

---

### Post by DeadSuperHero on 2009-08-27
Extremely exciting stuff, I've been following this for a while. I think it'll be a huge step up in usability for desktop linux, comparable to Bodega on Leopard.

But I'm curious: will there be a simple way for 3rd party developers to submit their own apps to the Ubuntu software store? I've heard it can be frustrating to get stuff in the repos, but it'd be great to have a simple deployment method to encourage development on Linux more.

---

### Post by andrewabc on 2009-08-27
Store makes is sound like you're selling stuff there. Will there be?

---

### Post by hikaricore on 2009-08-27
I agree it sounds like you're selling software.
If this is the case that's fine, otherwise it needs renamed.

---

### Post by 23meg on 2009-08-27
It would be a good idea to take a look at [the specification]("https://wiki.ubuntu.com/SoftwareStore") before asking questions; it's clearly mentioned that providing the ability to purchase software is among the plans.

---

### Post by Stochastic on 2009-08-28
> **Chauncellor said:**
> "Store" makes sense. Eventually, someday, somewhere, there will be ports of big programs to Linux. Where would you buy them? The Ubuntu Software Store.

I guess it might be confusing at first since there will be lots of monetarily free software available.

There already are a number of applications being sold that run on linux.  I think it would be a great way to encourage more software companies to port to Linux!  Though it may also encourage developers who create new applications for Linux to release it under non-free licenses.

---

### Post by hikaricore on 2009-08-28
I just read the basic description on launchpad which did not mention this.
Why would I read the entire wikipage searching for the mention of software sales?
Perhaps the launchpad page should give more detail to begin with.

---

### Post by Bou on 2009-08-28
Mpt, I have opened a couple bugs suggesting some small changes that, I think, would improve the app's appearance a lot (mockup attached).

[https://bugs.launchpad.net/ubuntu/+source/software-store/+bug/420496](https://bugs.launchpad.net/ubuntu/+source/software-store/+bug/420496)
[https://bugs.launchpad.net/ubuntu/+source/software-store/+bug/420504](https://bugs.launchpad.net/ubuntu/+source/software-store/+bug/420504)
[https://bugs.launchpad.net/ubuntu/+source/software-store/+bug/420517](https://bugs.launchpad.net/ubuntu/+source/software-store/+bug/420517)

Any opinions?

---

### Post by rajeev1204 on 2009-08-28
Hello michael,could you please explain whats a librarian in this context?


Thanks



rajeev

---

### Post by Sxeptomaniac on 2009-08-28
Very exciting.  I'd been seeing people throwing around that commercial software needs to become available for Linux, as some types of software are difficult to make FOSS.

I do see one challenge, in that there would have to be a way for people to reinstall software they've purchased (if, for example, their HDD crashes and they have to completely reinstall the OS).  It would need to balance the user's desire not to pay for the same thing over and over with the vendor's desire to protect their software from being too easily pirated.  Some kind of user account tied to one PC, perhaps?

---

### Post by andrewabc on 2009-08-28
So, in the future I can get canonical to host my fart application and I can charge $1.99 for people to buy it? Awesome!

/everyone on the iphone store business model bandwagon

---

### Post by mpt on 2009-08-28
> **Mr. Psychopath said:**
> will there be a simple way for 3rd party developers to submit their own apps to the Ubuntu software store?

Not in 1.0, but sometime in the next year, yes.

> **hikaricore said:**
> Why would I read the entire wikipage searching for the mention of software sales? Perhaps the launchpad page should give more detail to begin with.

Good point, thanks. I’ve updated the Launchpad page.

> **rajeev1204 said:**
> Hello michael,could you please explain whats a librarian in this context?

Actually, there I’m looking for anyone who’s an expert at [putting things into categories]("https://wiki.ubuntu.com/SoftwareStore/Categories"). You don’t have to be a librarian. :)

---

### Post by camahuetos on 2009-08-29
There is also a discussion about the name [in the Ubuntu Wiki]("https://wiki.ubuntu.com/SoftwareStore/Comments"), one part is related to the name.

---

### Post by sonnet on 2009-08-29
Hi, I wanted to ask to the developers, if this utility that is being created can be used by other debian distro (if it has not dependencies as ubuntu desktop etc etc ) in the same way as gdebi or synaptic are used by all debian based distro.
Does it have other dependencies other than python and gtk+?

---

### Post by douham on 2009-08-29
What ever it's called, who gives support to a non-foss app, not the Community (forums and Wiki) I hope.

---

### Post by mpt on 2009-08-29
> **andrewabc said:**
> So, in the future I can get canonical to host my fart application and I can charge $1.99 for people to buy it? Awesome!

Well sure, but with the amount of code required, you just *know* someone would develop GNU Fart(TM) and give it away for free, pricing you out of the market. ;)

> **sonnet said:**
> Hi, I wanted to ask to the developers, if this utility that is being created can be used by other debian distro (if it has not dependencies as ubuntu desktop etc etc ) in the same way as gdebi or synaptic are used by all debian based distro.

I don’t see why not. There is currently some special-casing for Ubuntu-specific things like Main vs. Universe, the ubuntu-desktop package and so on, but I’m sure we’d accept patches to abstract those out.

> *Does it have other dependencies other than python and gtk+?*

Yes, it uses [Aptdaemon]("https://launchpad.net/aptdaemon").

> **douham said:**
> What ever it's called, who gives support to a non-foss app, not the Community (forums and Wiki) I hope.

The Ubuntu Software Store is licensed under the [GPLv3]("http://www.gnu.org/copyleft/gpl.html").

---

### Post by Merk42 on 2009-08-29
I also don't particularly like "Store", only because it will also eventually replace Update Manager. Keeping a system up to date seems to have little to do with a Store.

Also, I posed this question elsewhere, but didn't get a definitive answer, nor did I see it in the specs.

Is there going to be some way of keeping track of what applications have been installed, especially commercial applications so I won't need to repay for them after a format?
Some sort of sign in ID like Steam?

---

### Post by Merk42 on 2009-08-29
> **Copernicus1234 said:**
> Huge mistake. Its only a question of time before popular software such as Eclipse, Gimp, Open Office, VirtualBox etc will be charged for if you provide the infrastructure for it with lots of users.

That's a bit of a slippery slope there.
All of those applications are available in Windows and OSX, with far more users.  What is stopping those applications from being pay right now? You'd pay for the EXE on Windows, the .app on OSX and the .deb on Ubuntu.  They just choose to remain free, so I doubt the Software Store will have an effect on any of what you listed.

Also, people don't seem to realize (though part of what the USS is for)... [**Canonical already sells software**](http://shop.canonical.com/index.php?cPath=19)

---

### Post by mpt on 2009-08-30
Ive been updating [the spec]("https://wiki.ubuntu.com/SoftwareStore") today, so there are more opportunities for you to help out if you want to.

> **Merk42 said:**
> Is there going to be some way of keeping track of what applications have been installed, especially commercial applications so I won't need to repay for them after a format? Some sort of sign in ID like Steam?

Yes. We haven’t yet designed that in any detail, though.

> **Copernicus1234 said:**
> Huge mistake. Its only a question of time before popular software such as Eclipse, Gimp, Open Office, VirtualBox etc will be charged for if you provide the infrastructure for it with lots of users.

What would be the point of that? Anyone else could take exactly the same code and offer it, in the same Store, for zero price.

I suppose, in theory, you might have a vendor producing GPLed application *X*(TM), and offering that as a paid application in the Store. And then a bunch of volunteers would take *X*(TM), strip out the trade marks, and offer it as *Y* in the Store. (With our system, they could even provide metadata that indicates *Y* is an alternative to *X*.) It would be like RHEL vs. CentOS, but on an application level.

> **andrewabc said:**
> I don't want to open a program that has "store" in it to get security updates. I'm pretty sure this will confuse users.

That’s true. But the same would be true for pretty much any other name for the Store. Whatever the final design for updates is, I’m pretty sure the window title will be “Updates Available”, not anything to do with the Store.

---

### Post by eyelessfade on 2009-08-30
whatever it is it don't work.
```
$ software-store
Traceback (most recent call last):
  File "/usr/bin/software-store", line 49, in <module>
    app = SoftwareStoreApp(datadir)
  File "/usr/share/software-store/softwarestore/app.py", line 65, in __init__
    self.xapiandb = xapian.Database(pathname)
  File "/usr/lib/python2.6/dist-packages/xapian.py", line 2422, in __init__
    _xapian.Database_swiginit(self,_xapian.new_Database(*args))
xapian.DatabaseOpeningError: Couldn't detect type of database
```

---

### Post by Merk42 on 2009-08-30
> **eyelessfade said:**
> whatever it is it don't work.
```
$ software-store
Traceback (most recent call last):
  File "/usr/bin/software-store", line 49, in <module>
    app = SoftwareStoreApp(datadir)
  File "/usr/share/software-store/softwarestore/app.py", line 65, in __init__
    self.xapiandb = xapian.Database(pathname)
  File "/usr/lib/python2.6/dist-packages/xapian.py", line 2422, in __init__
    _xapian.Database_swiginit(self,_xapian.new_Database(*args))
xapian.DatabaseOpeningError: Couldn't detect type of database
```

Silly question, but, you're not trying it on Jaunty are you?  It's only supposed to work on Karmic and above.

---

### Post by eyelessfade on 2009-08-31
> **Merk42 said:**
> Silly question, but, you're not trying it on Jaunty are you?  It's only supposed to work on Karmic and above.

```
$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu karmic (development branch)"
```

---

### Post by Paqman on 2009-08-31
> **Copernicus1234 said:**
> 
You can have a million free things in that store. As soon as you are starting to sell software, thats all that will matter and the focus will be on that.


I disagree. Canonical have been [selling software]("http://shop.canonical.com/index.php?cPath=19&osCsid=4e16faf83cf891e8a88917343f27f7a9") and services for a while now, and it hasn't lessened their enthusiasm for Ubuntu's core philosophy.

---

### Post by Glenn nl on 2009-09-01
Store really sounds like a shop or buying stuff...
I would like something like ubuntu software manager
But i like the idea of tabs for updates, free software and software that you need to buy

---

### Post by Tibuda on 2009-09-01
I don't think the "Software Store" name is that bad. [Psychocats compares current package managers to "an online shopping cart but the software is cost-free"]("http://www.psychocats.net/ubuntu/installingsoftware"). "Software Center" is good too.

---

### Post by MacUntu on 2009-09-01
Don't need, don't care - am I the only one?

---

### Post by bacardiandwatermelon on 2009-09-01
Would it have an option to choose where the launch shortcut will go in the menu bar? This really annoys me sometimes...

---

### Post by Copernicus1234 on 2009-09-01
> **mpt said:**
> 
What would be the point of that? Anyone else could take exactly the same code and offer it, in the same Store, for zero price.

I suppose, in theory, you might have a vendor producing GPLed application *X*(TM), and offering that as a paid application in the Store. And then a bunch of volunteers would take *X*(TM), strip out the trade marks, and offer it as *Y* in the Store. (With our system, they could even provide metadata that indicates *Y* is an alternative to *X*.) It would be like RHEL vs. CentOS, but on an application level.


Ive been thinking a bit more about this and perhaps its not such a bad idea. Bringing together developers and provide a easy way to showcase their applications will do a lot of good for Ubuntu. If it works for Android Market and Apple AppStore, it should work pretty good for Ubuntu as well.

And as people have said, you can buy stuff today from Canonical. The difference is only the name Store.

Which brings me to it. Because I really dont like it. Ive been thinking about for a while now and I still cant used to the name. I will somehow feel hesitant in saying "go to the ubuntu software store" to people I know. It doesnt feel or sound right for people who are into free software. "Check out Android Market" is fine. "Go to the Ubuntu Store" is not...

Perhaps I will get used to it, I dont know... maybe it just takes a while. But I never had any complaints about Android Market. It sounded perfect from the start. Somehow Market is good, Store is bad. Market implies freedom of choice somehow. Store doesnt. Its strange.

---

### Post by zekopeko on 2009-09-01
> **bacardiandwatermelon said:**
> Would it have an option to choose where the launch shortcut will go in the menu bar? This really annoys me sometimes...

Please,please read the wiki. Most of the answers can be found there.
But to be friendly: The link will be in the System menu like this:

System
---Preferences
---Administration
---Ubuntu Software Store

That way it will be more visible to users.

---

### Post by zekopeko on 2009-09-01
> **danielrmt said:**
> I don't think the "Software Store" name is that bad. [Psychocats compares current package managers to "an online shopping cart but the software is cost-free"]("http://www.psychocats.net/ubuntu/installingsoftware"). "Software Center" is good too.

I like (from the "Bye synaptic" thread in Ubuntu) Ubuntu Software Library.
Libraries don't have much ties to money but knowledge and freedom of expression so that seams like a good compromise between descriptive name and FLOSS ideals.

---

### Post by ChrT on 2009-09-03
Well naming it "application centre" is kinda misleading since it's not just for applications, but also upgrades and security updates. "Software centre" is much more accurate.

Also spell it as centre just to confuse american-english speakers.

---

### Post by Merk42 on 2009-09-03
> **ChrT said:**
> Well naming it "application centre" is kinda misleading since it's not just for applications, but also upgrades and security updates. "Software centre" is much more accurate.

Also spell it as centre just to confuse american-english speakers.

Cool, maybe we can download the "correct" spelling of center when we have to pay for mp3 codecs!

---

### Post by olskar on 2009-09-03
> **ChrT said:**
> Well naming it "application centre" is kinda misleading since it's not just for applications, but also upgrades and security updates. "Software centre" is much more accurate.

Also spell it as centre just to confuse american-english speakers.


Yes, also for upgrades and security updates. For applications ;)

---

### Post by Oak37 on 2009-09-05
> **Ubuntiac said:**
> **Problems:**

[LIST]
[*]Center / centre - Spelt differently throughout the world
[/LIST]


The centre / center spelling could easily be "fixed" through localised language settings.

---

### Post by zipperback on 2009-09-05
I stated this else where but since this looks like the proper thread here we go...

Why not just go with something like:

Ubuntu Repository Central
Ubuntu Repository System
Repository Central

Just my suggestion on the subject. But it makes sense to me, because we get our data / software / packages / etc... from various repositories. So I came up with a name which reflects that use.

Comments? Suggestions?


- zipperback
:popcorn:

---

### Post by dagoth_pie on 2009-09-05
That makes a lot of sence, now I'm thinking the developers thought about the name as much as us in the first place...

We do have to take into account Ubuntu is supposed to be user friendly, I'll bet most of us who are disagreeing with the word store, would probably be just as happy running any other Linux distro, if it makes it easier for newbies to understand it makes sence to me...

---

### Post by mpt on 2009-09-05
> **dagoth_pie said:**
> What would be wrong with keeping the app "Add/Remove..." then just adding a tabs at the top, eg. free, commercial, advanced, etc

That wouldn’t solve any of the usability problems we observed in user testing of Add/Remove. For example, people had a lot of trouble understanding the process of checking or (especially) unchecking a checkbox and then clicking “Apply Changes”.

> **Oak37 said:**
> The centre / center spelling could easily be "fixed" through localised language settings.

[Not as much as you think]("https://lists.ubuntu.com/archives/ubuntu-desktop/2009-August/002235.html"), which is why we didn’t choose that word.

> **zipperback said:**
> I stated this else where but since this looks like the proper thread here we go...

Actually, this thread is about [how you can help out with development of the Store]("http://ubuntuforums.org/showthread.php?t=1251257"), not about coming up with a new name for it.

On that note, if you’re comfortable with Python, quite a few of [the bugs reported about the Store]("https://bugs.launchpad.net/ubuntu/+source/software-store") are small Python bugs that you could fix in a small branch. I’ll be reporting more bugs, for where the current code doesn’t match [the specification]("https://wiki.ubuntu.com/SoftwareStore"), over the next couple of days. And if you’re the sort of person who loves reporting bugs, you can help out with that too.

---

### Post by jsmidt on 2009-09-05
Here are two facts:

1. The community is going to favor a name other than Software Store.

2. The name won't change because the whole purpose of this is for Canonical to make money. (This is a good thing.)

**However, people, get a clue: Until someone convinces Canonical that changing the name of the Software Store to something like the Software center *will earn Canonical more money*, the name isn't changing.  What the community thinks is irrelevant.  **

Same goes for Ubuntu One.  Money dictates Canonical's actions, not the community so come out of your dream worlds.

---

### Post by ELD on 2009-09-05
_@_[jsmidt]("http://ubuntuforums.org/member.php?u=29258") while points 1 and 2 are sound i don't agree with your last statement.

"not the community so come out of your dream worlds" 

That is harsh and quite untrue. While yes they need to make money, but your missing one huge point, the community are the ones buying it.

---

### Post by dagoth_pie on 2009-09-05
By the people, for the people...

I am what I am because of what we all are...

Ring any bell's, if people are so unhappy about this, I'm sure that they'll leave the old tools in the repositories so we could hypothetically download to use them rather than the new one, although, once we get used to it, does it really make a difference? Learning curve is supposed to be a disadvantage of Linux, so why shouldn't the Devs lessen the gradient so to speak?

---

### Post by mpt on 2009-09-05
> **jsmidt said:**
> 2. The name won't change because the whole purpose of this is for Canonical to make money. (This is a good thing.)

As an employee of Canonical, I agree that it&#8217;s a good thing for Canonical to make money. :) However, I expect I would be working on exactly the same project, with exactly the same name, if Canonical was a non-profit organization. So I think the rest of your statement is incorrect.

> **ELD said:**
> That is harsh and quite untrue. While yes they need to make money, but your missing one huge point, the community are the ones buying it.

The Ubuntu community plays a huge role in evangelizing Ubuntu, helping friends and family who run it, and contributing to its development. But many, if not most, of the people buying Ubuntu &#8212; or buying computers with Ubuntu preinstalled &#8212; have *no idea* there is such a thing as an &#8220;Ubuntu community&#8221;. That proportion will naturally increase as Ubuntu&#8217;s popularity increases, and our branding and marketing will need to adjust to match. As one of our user testing subjects put it when she saw Ubuntu described as &#8220;community-based&#8221; on the Web site: &#8220;To be honest I think of that as PR talk &#8230; Communities develop health care, not operating systems.&#8221;

---

### Post by ELD on 2009-09-05
> **mpt said:**
> 
The Ubuntu community plays a huge role in evangelizing Ubuntu, helping friends and family who run it, and contributing to its development. But many, if not most, of the people buying Ubuntu &#8212; or buying computers with Ubuntu preinstalled &#8212; have *no idea* there is such a thing as an &#8220;Ubuntu community&#8221;. That proportion will naturally increase as Ubuntu&#8217;s popularity increases, and our branding and marketing will need to adjust to match. As one of our user testing subjects put it when she saw Ubuntu described as &#8220;community-based&#8221; on the Web site: &#8220;To be honest I think of that as PR talk &#8230; Communities develop health care, not operating systems.&#8221;


I never said the community was developing, my point is the "community" meaning any of us who use ubuntu are the ones buying stuff, canonical needs to know that. "Communities develop health care, not operating systems" has nothing to do with what i am talking about and seems like a strange saying to me. While i agree they need to think about the new people not currently in the community they need to think about the already loyal community more so in the start or risk losing a lot.

Oh and without a community (however you look at it), Ubuntu wouldn't exist, it would cease.

This seems like it could be a long debate heh...

---

### Post by mpt on 2009-09-05
> **ELD said:**
> I never said the community was developing, my point is the "community" meaning any of us who use ubuntu are the ones buying stuff, canonical needs to know that.

Referring to anyone who uses Ubuntu as the Ubuntu “community” would demean the word, and would bear little resemblance to how most people using Ubuntu think of themselves.

I suggest a better definition of the “Ubuntu community” would be “the subset of Ubuntu users who evangelize or contribute to Ubuntu, and who frequently communicate with others doing the same”.

That subset started out as a majority, but while it is continuing to increase in absolute numbers, it is decreasing as a fraction of Ubuntu users. Therefore, Ubuntu’s branding and marketing will increasingly be targeted at users who are not part of the community. Naturally, that will cause occasional awkwardness.

> *"Communities develop health care, not operating systems" has nothing to do with what i am talking about and seems like a strange saying to me.*

That’s precisely the point. She was a healthcare administrator in a civilized country, so it made perfect sense to her that communities develop health care, but it sounds strange to most of us. Conversely, we are fans of Ubuntu, so it makes perfect sense to us that Ubuntu would have a community, but it doesn’t make sense to her — and wouldn’t even if she was using Ubuntu full-time.

---

### Post by Paqman on 2009-09-05
> **mpt said:**
> 
That subset started out as a majority, but while it is continuing to increase in absolute numbers, it is decreasing as a fraction of Ubuntu users. Therefore, Ubuntu&#8217;s branding and marketing will increasingly be targeted at users who are not part of the community. Naturally, that will cause occasional awkwardness.


That's an interesting idea. Do you think we're breaking new ground in that regard, or are there lessons we can learn from another distro that might have already gone down this path?

If not another distro, do you think there's a parallel in another industry perhaps?

---

### Post by Jerry41 on 2009-09-05
> **Paqman said:**
> That's an interesting idea. Do you think we're breaking new ground in that regard, or are there lessons we can learn from another distro that might have already gone down this path?

If not another distro, do you think there's a parallel in another industry perhaps?

Whether Ubuntu , Linux in general, another industry, or a political party, you ignore your base at your own peril.

"Store" is a lousy idea for an operating system emphasizing the idea of "FREE" in all of the literature.

Strictly a personal opinion, but **I **know there are other distros out there, and **I **am not noted for "brand identification" if my "brand" ceases to meet my needs.

Edited to add:
I first installed Ubuntu on an old "Win 98" pc for my *Great Granddaughter* and it worked so well I put it on my XP system soon after. The little ding on the *Wiki* about " .  .  . with a self-evident name and an interface a grandparent can use." seems an egregious assumption that all grandparents probably have Alzheimer's or some similar affliction.

---

### Post by mpt on 2009-09-05
> **Paqman said:**
> That's an interesting idea. Do you think we're breaking new ground in that regard, or are there lessons we can learn from another distro that might have already gone down this path?

Red Hat and Novell handle this to a small extent by having paid enterprise editions (Red Hat Enterprise Linux, Suse Linux Enterprise) separate from their community projects (Fedora, Opensuse). But as far as I know, it goes no further than that: neither of them try, for example, to give a program one name in the community edition and a different name in the enterprise edition.

> *If not another distro, do you think there's a parallel in another industry perhaps?*

As Jerry41 suggests, there is a rough analogy to political candidates, who have to please both their own activists and the larger voting public.

But the closest comparison I know of, past or present, is Firefox. Most of its [estimated 270 million users]("http://weblogs.mozillazine.org/asa/archives/2009/05/firefox_at_270.html") have no idea there is such a thing as a “[Mozilla project]("http://www.mozilla.org/")”.

---

### Post by Leighman on 2009-09-06
I think the point about people being upset because their UK version says Center when they have the wrong locale set is pretty much clutching at straws...
Surely it's clear by now that the idea of Store/Centre etc is far more confusing/controversial.

---

### Post by mrdoob on 2009-09-06
Great move Canonical!

---

### Post by 23meg on 2009-09-06
> **mpt said:**
>  about [how you can help out with development of the Store]("http://ubuntuforums.org/showthread.php?t=1251257"), not about coming up with a new name for it.


I've moved the naming discussion to [the other thread]("http://ubuntuforums.org/showthread.php?t=1256242").

---

### Post by mpt on 2009-09-08
The list of [bug reports for the Store]("https://bugs.launchpad.net/ubuntu/+source/software-store") now includes plenty of [bite-size bugs to work on]("https://bugs.launchpad.net/ubuntu/+source/software-store/+bugs?field.tag=bitesize").

---

### Post by mpt on 2009-09-10
[Ubuntu Software Store 0.3.0]("https://launchpad.net/ubuntu/+source/software-store/0.3.0") is now in Karmic. Please try it out and report bugs!

---

