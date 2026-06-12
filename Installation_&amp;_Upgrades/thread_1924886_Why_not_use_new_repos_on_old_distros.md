---
title: "Why not use new repos on old distros?"
date: 2012-02-13
forum: Installation &amp; Upgrades
---

### Post by tjfitz on 2012-02-13
Hello,

While I understand the rationale for issuing new distributions on a regular basis, I don't understand the importance of sticking with the repositories devoted to a certain distribution when there are  newer package versions available in repositories devoted to newer distributions. Reinstalling from scratch is a real headache.  Why not make rolling releases, rather than compartmentalizing?

Thanks,
TJ

---

### Post by snowpine on 2012-02-13
Rolling releases already exist: Arch, Gentoo, Debian Sid, etc.

Ubuntu is not rolling release, and is more popular than Arch+Gentoo+Sid combined.

So I guess "rolling release is a small niche market" is the answer to your question "why not make Ubuntu rolling release?" :)

---

### Post by tjfitz on 2012-02-13
Let me clarify myself a bit.  I've tried Debian and Gentoo, and I'm quite content to suffer through  reinstalling Ubuntu after those experiences.  I just want to know the  "why".  I'm  interested in a lay explanation of the mechanics behind distribution upgrades than I am in switching to a different flavor of Linux.  Is it impractical to treat an Ubuntu installation as if it was a rolling release by doing as I proposed?  If not, why not?

---

### Post by snowpine on 2012-02-13
Upgrading Ubuntu is described in detail here: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

(You do not need to do a fresh reinstall every 6 months! :))

Ubuntu is not a "rolling release" distro, but you can achieve a similar purpose by using the development release (currently 12.04). As a bonus you'll be helping to test bugs and make the next Ubuntu release better. :)

---

### Post by CharlesA on 2012-02-13
New stuff might not work on an older Distro, either due to missing dependencies or something else.

I guess you could add the 12.04 repos to 10.04 and install stuff from there, but you would probably end up with a broken system in the end.

As a general rule, it is better to stick to the repos for your version instead of trying to add the repo for the newer version.

If you want a newer version of a program, look for a PPA or compile it from source.

---

### Post by tjfitz on 2012-02-13
> **snowpine said:**
> Upgrading Ubuntu is described in detail here: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes) Thanks for the link.  I will read through that and see what I can learn.  

> **snowpine said:**
>  (You do not need to do a fresh reinstall every 6 months! :))Thank goodness for that.  I have been using Lucid since it  came out.  I like that there are LTS releases for just that reason,  though I may reconsider that in the future.

> **snowpine said:**
>  Ubuntu is not a "rolling release" distro, but you can achieve a similar purpose by using the development release (currently 12.04). As a bonus you'll be helping to test bugs and make the next Ubuntu release better. :)Hmm, another thing to consider....

> **CharlesA said:**
> New stuff might not work on an older Distro,  either due to missing dependencies or something elseCurrently I'm on an IBM T42.  No worries there.


Thank you both for your feedback.  I'll read that article, and if I have more questions I may ask them here.

---

### Post by tjfitz on 2012-02-14
> **snowpine said:**
> Rolling releases already exist: Arch, Gentoo, Debian Sid, etc.Like I said above, I have used Debian Sid before.  I actually like the distribution itself, but the support forum was horribly unresponsive.  Can Linux users get support for other distributions besides Ubuntu variants on this forum?

---

### Post by 23dornot23d on 2012-02-14
For other distributions there is some information and help on this FORUM 

on this [[COLOR=Red]**LINK**[/COLOR]]("http://ubuntuforums.org/forumdisplay.php?f=401")  its not going to be the same as going direct to the distribution Forum 
that you are interested in Arch Gentoo Mint Sabayon or others ..... 
but the people there are very helpful and may point you quickly to a answer or link 
you to a place they find their information from.

_______________________________________________________

There are methods to make this seem like a rolling release ..... as said - getting into the testing area early and following it through .... but watching for any serious breakage and trying to avoid upgrading at the points where they occur - people on there are quite quick at warning if the display driver no longer works or that it will no longer boot to a GUI.

In my experience over the last 3 upgrades ... its been possible to do
[B]
sudo aptitude safe-upgrade[/B]
upto the point where a distribution changes to the next one .....

then to do
[B]
sudo aptitude dist-upgrade [/B]

( after following instructions posted on the net to change the repositories to suit )
That is at the time when the new release comes out ..........

This I would not recommend to Newbies though ..... as getting out of awkward situations
may not be for everyone ..... and most testers seem to have fall back systems too.

With Linux as you will probably know .... it is possible to run more than one from the same drive and switch between them ..... this way you can usually have at least one good running system ..... to drop back to.

---

### Post by tjfitz on 2012-02-14
> **23dornot23d said:**
> In my experience over the last 3 upgrades ... its been possible to do
[B]
sudo aptitude safe-upgrade[/B]
upto the point where a distribution changes to the next one .....

then to do
[B]
sudo aptitude dist-upgrade [/B]

( after following instructions posted on the net to change the repositories to suit )
That is at the time when the new release comes out ..........

This I would not recommend to Newbies though ..... as getting out of awkward situations may not be for everyone ..... and most testers seem to have fall back systems too.This is worth a try.  I have a backup disk to save everything important in the event of a disastrous attempt.  I don't have a second computer but I do have a livecd to run.  I will probably burn the Debian testing netinst cd first (Sid is a bit too unstable for my taste), and if things go bad I may just try starting over with that instead.

---

### Post by 23dornot23d on 2012-02-14
I use a lot of different Distros ,,,, the way I do it is with USB HDs

I tend to add a new one in a new partition ,,,,,, a 1 Terra HDD can swallow up many but
I stick to 16 Distros on one ...... as they tend to start messing up after that ......

Here is a Boot Screen to give you some idea of what you could do ...... but most people stick with one
or another distro ...... I like to keep up with what is going on in the LINUX world so do a little bit of experimenting.

sdb as you can see from below is divided into many smaller partitions ..... 20 to 30 Gig is quite reasonable for a testing partition ..... and allows for a lot of programs too .....

There are a lot more on here than what you can see from this small snippet ..... but it gives you an idea
all of my systems I run and they all have there own little plus and minus features ....... :confused:

I find having a few to choose from never leaves me in a position where I cannot get a job done :D

But obviously the downside is keeping everything organized ..... this is done through one main Desktop where I have access to all the other partitions ...... the home partition can be very useful - but even better I find is having a partition formatted FAT32 200 Gig ...... the access is always easy to gain for DATA from any system.

Food for thought anyway ....... 

[IMG]http://img402.imageshack.us/img402/765/bootscreen.jpg[/IMG]

---

### Post by tjfitz on 2012-02-14
> **23dornot23d said:**
> I find is having a partition formatted FAT32 200 Gig ...... the access is always easy to gain for DATA from any system.I have a FAT32 partition on my backup disk.  I call it my "Windows Airlock".;)

> **23dornot23d said:**
> 
[IMG]http://img402.imageshack.us/img402/765/bootscreen.jpg[/IMG]Holy crap!  No can do.  I only have 60 GB to work with.

---

### Post by 23dornot23d on 2012-02-14
Was not saying you need to go as mad as me .... lols .... 

The thing with mine - is as soon as the new distro comes out .... it can be put into its own partition - but with 60 Gig you are limited - getting a new USB hard drive soon gives a new lease of life to your computer and more possibilities I mainly bought my first USB HD for a laptop that only had a 40 Gig drive in it - with a 350 Gig HD on it - it made things so much easier.

Check the prices out some HDs have reasonable prices .... handy to have to keep backups too as well as making it possible to run a couple more versions of LINUX .....
just make sure that your BIOS is capable of booting from USB hard drives .... some do not.

If yours will then its possible to treat Ubuntu almost as a rolling release ..... just safe-upgrading when things look reasonably stable but always having the development release as well as your favorite release sitting safe in a separate partition ..... only upgrading that one when you are sure things are good.

As well as being able to add input if you find something that is not quite right .... which also gives the developers a chance to fix things before the next final release.

12.04 is looking good .... but if you read the comments at this very moment in the testing area - it sounds a bad time to upgrade 

[http://ubuntuforums.org/showthread.php?t=1925522](http://ubuntuforums.org/showthread.php?t=1925522)

..... but every day another set of upgrades appear ...... and the comments change to reflect the current state of play.

---

### Post by tjfitz on 2012-02-17
I installed Debian Wheezy, and if anything, Debian is even less friendly  than it used to be.  Maybe Ubuntu spoiled me.  Moving on.



Next, I tried Ubuntu 11.10.  About Gnome 3...

[IMG]http://www.analoghype.com/wp-content/uploads/2010/01/cookie-monster-wtf-is-this1.jpg[/IMG]

Seriously.  This old machine can't handle such graphical intensity, and this old user doesn't want to completely relearn how to use a desktop.  Next.



I guess I'll swing over to the other end of the spectrum and try Lubuntu.  I keep hearing good things about it, and hopefully it won't be so vastly different from Xfce or Gnome 2.

---

### Post by 23dornot23d on 2012-02-17
> 
I installed Debian Wheezy, and if anything, Debian is even less friendly   than it used to be.  Maybe Ubuntu spoiled me.  Moving on.



Yep - this is what I found too - must admit the debian based distro that I now use is provided by Linux Mint .... and is very good.

Gnome 3 is growing - but if you want you can install lubuntu-desktop from it ...... 

sudo apt-get update
sudo apt-get install aptitude
sudo aptitude update
sudo aptitude install lubuntu-desktop

---

### Post by tjfitz on 2012-02-18
> **23dornot23d said:**
> Yep - this is what I found too - must admit the debian based distro that I now use is provided by Linux Mint .... and is very good.I just went to the Mint website.  I presume you're talking about LMDE?  Of it, they say, "Expect some rough edges."  Has it been smooth for you?

> **23dornot23d said:**
> Gnome 3 is growing - but if you want you can install lubuntu-desktop from it ...... It would be cleaner to simply install from the Lubuntu CD.

Following your suggestions, I have read up on the rolling releases that are out there.  They all seem to be less concerned with user-friendliness that I'd like.  Most likely I'm just going to stick with an Ubuntu variant (depending on your opinion of LMDE).  Maybe when the next release comes out I'll try doing like I proposed at the start of the thread just to see what happens!

---

