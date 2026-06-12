---
title: "Package updates in distribution"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by ubugeoff on 2009-11-20
First a question. Who actually is 'responsible' for
putting later package releases into the
update manager list? Is it the Ubuntu
team, or is the actual package maintainers? Or
both?

The specific package in question is 'boost',
from [http://www.boost.org](http://www.boost.org).

In my Ubuntu 8.04 LTS, the latest update that
appears in the Synaptic Package Manager is
boot 1.34.1. That was released circa July 24th,
2007. 2007!

From the boost version history web page, this
shows the latest package as Version 1.41.0,
November 17th, 2009. And there have been a
LOT of versions in between!

Yes, I know I can download the source myself,
compile and install it, and that is what I
may have to do.

And I know that perhaps if I upgraded my 8.04,
LTS to 8.10 -> 9.04 -> 9.10, then perhaps these
would have a later boost package, but I chose
8.04 for its Long Term Support.

So is there any hope that the 'boost' will be
updated in the 8.04 LTS package manager soon?

Geoff.

---

### Post by snowpine on 2009-11-20
Hi Geoff, that's just not how Ubuntu works... once a release comes out, it is "frozen" and never gets the latest applications through the regular update process (only minor bug fixes and security patches).

If you decide to stick with 8.04, it means you will always use applications that were stable as of April 2008 (unless you install newer applications yourself). They will *never* add a November 2009 application to Hardy through updates. This is precisely why it is considered a long term support release; everything is very stable and well-tested.

[http://packages.ubuntu.com](http://packages.ubuntu.com) is a great resource; it will tell you which version of any given application is in each Ubuntu release.

Like I said, you can install a newer version of boost yourself (you seem to know how to do it); I'm just trying to explain the reason why Ubuntu is set up the way it's set up.

---

### Post by Kevbert on 2009-11-20
The only updates you're likely to get are security updates and some bug fixes for 8.04. It's always possible to update packages manually by looking in the package repositories [[COLOR="Red"]here[/COLOR]]("http://packages.ubuntu.com/") and then download and install the relevant deb file (just double click on the downloaded deb file). The only problem with this is that you need to make sure all dependencies are met (but you should get a warning when you try to install if you don't have all the required files installed).

---

### Post by ubugeoff on 2009-11-20
Thank you snowpine and Kevbert for your replies,
and the link to [http://packages.ubuntu.com](http://packages.ubuntu.com). This
is certainly a great source of information...

But that still leaves some questions.

I understand that I may only get 'advised',
through the regular update process, of package
updates, if and unless they represent a bug or security
issue, but do _NOT_ understand why this is extended 
to the 'Synaptic Package Manager'.

So here I am differentiating between the Ubuntu
'Update Manager', and the 'Synaptic Package
Manager'. I do _NOT_ expect any boost updates
to come through the 'Update Manager', unless
bug or security related, but I would expect 
a _TRUE_ 'Package Manager' to show, and allow 
newer packages to be installed.

I can SEE, from the above link, that the Software
Packages in "karmic" (9.10) does include the boost
1.40. Of course boost has MANY parts, so even in 
this long boost list some components are still 
at 1.34, 1.38, etc...

So, is there a _TRUE_ 'package manager', that
would show _ALL_ package updates, not just
those marked Ubuntu 8.04? Where perhaps
I say change the repository, or repositories
searched... Have more control...

Of course I can go to boost, download the
1.40 source, compile and install it myself, but I
was hoping for a 'package manager' that would
also offer this functionality...

And as Kevbert said, I can download a particular
deb file, say libboost-date-time1.40.0, version
1.40.0-2ubuntu2, from the 'karmic' list, and the
'Package Installer', shows a Status: All dependencies
are satisfied, and offers to 'install' the package,
but again, is there a good 'Manager' where I can
select _ALL_ the later boost items, and click GO?

Maybe my asperations are way too high ;=)) and
'manual' intervention is the only way...

Geoff.

---

### Post by snowpine on 2009-11-20
Hi Geoff, the Synaptic Package Manager is simply a graphical "front end" for the apt package manager. (As are the Update Manager, the Add/Remove Programs app, etc... they can all be replicated from the command line using "sudo apt-get upgrade" or "sudo apt-get install boost" etc.)

Each Ubuntu release has a separate "repository" of applications so if you're using Hardy, you will only see the Hardy versions, never the newer Karmic versions.

Most Ubuntu users stay current by upgrading to the new release each 6 months. The LTS releases (like Hardy) are designed for users who are willing to trade newer applications in exchange for stability.

As you know, it is easy to install a newer version of a specific application, (assuming dependencies can be met).

---

### Post by ubugeoff on 2009-11-20
Thank you snowpine. This is the exact information I
needed to know. I guess I got a real wrong impression
of LTS ;=(( I am quite new to linux...

I will now head down the hardy 8.04 -> intrepid 8.10
-> jaunty 9.04 -> karmic 9.10 path over the coming
days... and forever continue ;=))

As a developer, previously mainly in MS Windows, 
I _MUST_ have the latest packages all/most of the time,
thus am _NOT_ willing to 'trade' otherwise.

I certainly hope however I am not trading too much
'stability' away... and most of the MANY packages that I
have aleady previous installed over the last year or so
will remain, or be upgraded... going back to step 1
would be a real PAIN...

But I have my Windows Vista dual boot available if 
Ubuntu goes too far west ;=))

Regards,

Geoff.

---

### Post by snowpine on 2009-11-20
Good luck, I think as a developer, you will benefit from the newer version. I would only really recommend the LTS releases for certain situations, like running a bunch of servers. :) 

Don't forget, you can use a Live CD to preview the new release, that way you'll know if there are any "show stopper" bugs on your hardware before committing to an upgrade.

---

### Post by ubugeoff on 2009-11-21
YOWEE, the reminder of possible 'hardware'
problems caused me to re-think what I was
doing. I had considerable trouble getting my
ATI Radeon HD 2600 XT video card running properly...
and certainly do not want that 'fight' again ;=((

So after further thought and consideration,
I am now not sure I agree with the assessment :-
> LTS releases for certain situations,
> like running a bunch of servers. :)

What should be kept STABLE is the base Operating
System, and freezing that at hardy 8.04 LTS
might not, and should not, be a bad thing.

But when it comes to applications, tools that run on
top of this OS, then you should always at least look
at the 'latest', to see if any features have been
added that you may want, as well as possible bug
and security fixes.

For example, take say the FileZilla FTP client. The
Ubuntu 8.04 package manager still list only version
3.0.7.1, which is what I have, while the FileZilla 
site offers 3.3.0.1.

So while the later versions of an application
still runs on Ubuntu 8.04 - that is does NOT rely
on any OS features that may have been added to
later versions of the OS - it SHOULD be listed
in a TRUE 'package manager', as available for
update...

So here I am separating the base OS - that should
be kept stable - with applications, tools or packages
that run on that OS, and should be upgradable...

And, in this FileZilla case, when you ask it to
'check for updates', it comes back advising that
3.3.0.1 is available, and politely adds :-
"Please check the package manager for an updated
 package, or visit [http://filezilla-project.org](http://filezilla-project.org)
 to download the source code of FileZilla"
 
So in the first part of that message, it is suggesting
a 'package manager' should list it! And of course we 
always know we can download the source, and build and
install it yourself.

The FireFox browser would be another good example.
The package manager list only 3.0.15, while 3.5.5
is available from the Mozilla site...

There would be hundreds, if not thousands, like this,
including the 'boost' updates that started this.

So this is an idea of 'updating/upgrading' applications,
packages, tools that run on hardy 8.04, while retaining the
stable, frozen if you will, OS underneath.

So back to the drawing board ;=)) Is there a 'package
manager' that can be configured, or commanded to
search later, other OS repositories, and suggest _ALL_
available updates/upgrades?

The current Synaptic Package Manager lists nearly
25K packages, but seemingly _ONLY_ those for 8.04.
Is there an options, a filter, whatever, that I am
missing, to ask it to look harder? Look in other
places, other repositories?

This must effect the MANY users of Ubuntu? By
choosing a stable LTS version, and sticking to it,
they can only MANUALLY upgrade applications, tools,
packages, on a 1 by 1, case by case basis, and then
manually deal with installing it. 

Hardly a 'user friendly' environment ;=() But that
may be the lay of the land, and one must just live
with it ;=((

All advice, comments welcome...

Regards,

Geoff.

---

### Post by snowpine on 2009-11-21
Yes of course you can add additional repositiories to your sources list, which then appear in your package manager. (edit /etc/apt/sources.list or System->Admin->Software Sources)

Examples would be [Hardy Backports]("https://help.ubuntu.com/community/UbuntuBackports"), the latest [Virtualbox]("http://www.virtualbox.org/wiki/Linux_Downloads"), [Firefox daily build]("https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa"), etc.

Obviously the more software sources you add, the less "stable" your system becomes, and if you begin to add untrusted software sources, or sources not meant for Hardy, you might get into trouble.

You seem to be computer-saavy enough to get the newer applications you want. Let's agree to disagree whether Ubuntu's system of providing stable releases is "user friendly" or not.

---

### Post by 73ckn797 on 2009-11-24
Searching the forums, this thread seems to be the closest to what my question is.

I read in here that the LTS version gets any security and bug fixes. That I assumed. Are the available LTS iso images that are available for download updated with those fixes? In other words, is the LTS "up to date"? I realize any software updates probably are not maintained and would have to receive recommended updates as I see fit to have them installed. I have 8.04 on a disk but it is as old as the original release of 8,04.

---

### Post by snowpine on 2009-11-24
> **73ckn797 said:**
> Searching the forums, this thread seems to be the closest to what my question is.

I read in here that the LTS version gets any security and bug fixes. That I assumed. Are the available LTS iso images that are available for download updated with those fixes? In other words, is the LTS "up to date"? I realize any software updates probably are not maintained and would have to receive recommended updates as I see fit to have them installed. I have 8.04 on a disk but it is as old as the original release of 8,04.

They release a new ISO of the LTS releases every 6 months or so. The current sub-version of 8.04 is 8.04.3.

It does not matter whether you install from the 8.04.3 disk or from your original disk. Once you run the update manager to bring your system up to date, the systems will be the same.

---

### Post by 73ckn797 on 2009-11-24
> **snowpine said:**
> They release a new ISO of the LTS releases every 6 months or so. The current sub-version of 8.04 is 8.04.3.

It does not matter whether you install from the 8.04.3 disk or from your original disk. Once you run the update manager to bring your system up to date, the systems will be the same.


I knew the regular update after install would bring things up to speed. I was curious about the currently available iso having the latest changes incorporated.

Thanks.

---

### Post by snowpine on 2009-11-24
> **73ckn797 said:**
> I knew the regular update after install would bring things up to speed. I was curious about the currently available iso having the latest changes incorporated.

Thanks.

You should upgrade regardless of which ISO you install from, as changes can happen on a daily basis. Obviously the newer the ISO, the fewer upgrades there will be after installing.

---

### Post by 73ckn797 on 2009-11-24
> **snowpine said:**
> You should upgrade regardless of which ISO you install from, as changes can happen on a daily basis. Obviously the newer the ISO, the fewer upgrades there will be after installing.


That was my whole point in asking the question regarding the newer iso. I figured that was the case but had not seen anything before directly addressing the question. I keep things updated on a regular basis and run updates whenever I perform a new install.

---

### Post by ubugeoff on 2009-11-25
Wow! See, that looked to be the information I was looking 
for ;=))
 [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)
I have definitely put that in my bookmarks! And it explains
exactly what I have been babbling about - later package
versions ;=)) ported to my 8.04 LTS stable base...

And I will check out the other links further, as need be,
but already noted the 'PPA' for firefox, etc...

So, I have now un-commented both the backports and canonical 
'deb' lines in /etc/apt/sources.list, and a check with
System->Admin->Software Sources showed some more checked
boxes... And after an initial update of some 20+ things, I
now get offered some 'backport' items now and again, as
well as the bug and secutity items...

But as yet none of this has touched the 'boost', which is 
what I really need! Is there something more I am missing here?

How can I, for example, check if the 'boost' project
have a 'repository', like I saw in virtualbox - Debian-based
Linux distributions, or mozilla - with 'deb' links, and info
like Signing key and fingerprint? I searched around their
site, but found nothing. Maybe I should put a message on
one of their lists? That is I probably should ask them!

But, more importantly, what is the process of getting something
into 8.04 'backports'? Can I suggest boost? Recommend it? Do some testing?
Help do a FULL check out of the later versions in my 8.04?
Or what, to get these important 'boost' updates into 'backports'...

The boost version 1.34.1 is dated July 24, 2007, and there have
been multiple releases since. The minimum version I require is
1.37.0 dated November 3rd, 2008, so it is already a year old,
which specifically leverages and expands <tr1/unordered_map>...

And thanks again for the pointers... seek and yee shall find,
some things ;=))

Regards,

Geoff.

---

