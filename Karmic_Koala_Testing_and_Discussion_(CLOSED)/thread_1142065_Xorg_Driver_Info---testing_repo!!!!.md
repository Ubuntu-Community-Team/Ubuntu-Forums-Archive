---
title: "Xorg Driver Info---testing repo!!!!"
date: 2009-04-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2009-04-28
This will help everyone just a bit more :):):):)!!!!!!!

On Fri, Apr 24, 2009 at 9:32 PM, Bryce Harrington [EMAIL="bryce@canonical.com"]<bryce@canonical.com>[/EMAIL] wrote:
[INDENT]> A little Jaunty Release Day present from the Ubuntu-X team. ?:-)
>
> From past releases, we know that often people want a way to try out
> newer drivers than were included in the official release. ?To make life
> a little easier, we've put together a PPA with some newer X drivers:
>
> ?[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/]("https://edge.launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/")
>
> You can see that already we have new stable versions of nearly all the
> major video drivers for your video-ing pleasure.
>
> I can't promise that we'll be keeping it up to date or fixing bugs, but
> we'll do what we can. ?We're going to treat it as a "stable" PPA, and
> only post stuff we feel is likely to be better in some respect than
> what's in the release
[/INDENT]
It has a newer nvidia driver---180.53

---

### Post by DougieFresh4U on 2009-04-28
Have they come up with a way to get 'fglrx' to work with the .30 kernel?
I have had nothing but drama on that issue and gave up, stuck with .28 on Jaunty.
Don't have .30 yet on my Karmic partition and won't even attempt 'fglrx' with Karmic, yet.  :(

---

### Post by autocrosser on 2009-04-29
You might look thru the repo & see if anything helps---you never know until you look---I was pleased to find a newer driver for nvidia---the Jaunty one would not work with the .30 kernel......

---

### Post by caryb on 2009-04-29
I have installed the 2.6.30-1 kernel this morning with this PPA it works fine on the .28 kernel but X fails on the .30 I think it might have something to do with the restricted kernel package not being available yet.


Cary

---

### Post by lithorus on 2009-04-29
> **caryb said:**
> I have installed the 2.6.30-1 kernel this morning with this PPA it works fine on the .28 kernel but X fails on the .30 I think it might have something to do with the restricted kernel package not being available yet.


Cary
Try this :
```
deb http://ppa.launchpad.net/thefirstm/ppa/ubuntu jaunty main
```
The lastest nvidia driver there works with .30

---

### Post by caryb on 2009-04-29
> **lithorus said:**
> Try this :
```
deb http://ppa.launchpad.net/thefirstm/ppa/ubuntu jaunty main
```
The lastest nvidia driver there works with .30

That worked thank!


Cary

---

### Post by autocrosser on 2009-04-29
Nice info---Thanks!!!!

Here's my Koala looking at you!!!!

---

### Post by Gina on 2009-04-29
Looks like he's asleep to me :lolflag:

---

### Post by plun on 2009-04-29
> **Gina said:**
> Looks like he's asleep to me :lolflag:

Maybe sleepy....:)

Original picture

[http://www.koala.net/media/koala2.jpg](http://www.koala.net/media/koala2.jpg)



Credits [nyarnon]("http://ubuntuforums.org/showthread.php?t=1129183")

--

---

### Post by autocrosser on 2009-04-29
NA--he is in deep thought about the upcoming ubuntu release:lolflag:

Either that or bored about the thought of another thread about the "new theme"

---

### Post by Kareeser on 2009-04-29
180.53. That's intense. The NVIDIA website still has 180.51 listed up. Yikes :)

---

### Post by plun on 2009-04-29
> **Kareeser said:**
> 180.53. That's intense. The NVIDIA website still has 180.51 listed up. Yikes :)

More info within this thread

[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

ver 180.53 is a pre-release...works great for me, now testing the beta 185.18.04....:)

---

### Post by caryb on 2009-04-29
> **plun said:**
> More info within this thread

[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

ver 180.53 is a pre-release...works great for me, now testing the beta 185.18.04....:)

It maybe bleeding edge but now my 3d effects (kwin) works again:guitar:


Cary

---

### Post by crjackson on 2009-04-29
> **caryb said:**
> It maybe bleeding edge but now my 3d effects (kwin) works again:guitar:


Cary

I have the .53's installed on several machines. They're as stable as any I've used so far.

---

### Post by Nullack on 2009-04-29
185.18.04 is the goodness for me. Ive manually installed it on Karmic.

---

### Post by Gina on 2009-04-30
Added the package to sources.list, ran Synaptic Reload and get the error> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 26F4EF8440618B66

---

### Post by erkiha on 2009-04-30
You can just ignore this error. But to fix it do the following:

1. take last 8 chars of that number, for example 40130828 of the first warning.
2. Enter forllowing to console/command prompt/terminal:
gpg --keyserver keyserver.ubuntu.com --recv-key 40130828
Keyserver can be pgpkeys.mit.edu or keyserver.ubuntu.com or something else.
4. If that was sucsessful i.e. you get response that 1 key was imported, enter next command:
gpg -a --export 40130828| sudo apt-key add -

And you are done.

---

### Post by taavikko on 2009-04-30
> **erkiha said:**
> You can just ignore this error. But to fix it do the following:

1. take last 8 chars of that number, for example 40130828 of the first warning.
2. Enter forllowing to console/command prompt/terminal:
gpg --keyserver keyserver.ubuntu.com --recv-key 40130828
Keyserver can be pgpkeys.mit.edu or keyserver.ubuntu.com or something else.
4. If that was sucsessful i.e. you get response that 1 key was imported, enter next command:
gpg -a --export 40130828| sudo apt-key add -

And you are done.

There's an easier command to achieve this
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 40618B66
```

Last 8 digits is usually correct.

---

### Post by Gina on 2009-04-30
Thank you very much - that worked :)

I now have my nvidia graphics working with the new kernel :)

---

### Post by autocrosser on 2009-04-30
Good to hear!!! I'll be glad when its "stable"  :lolflag:

---

### Post by Gina on 2009-04-30
My system hasn't crashed yet :lol:

Famous last words :lolflag:

I'll have to see what I can do about that :)

---

### Post by jerrylamos on 2009-04-30
> **Gina said:**
> Looks like he's asleep to me :lolflag:

The eucalyptus leaves the koala's eat have low energy content so the koala's are not very energetic except when two males have a territorial squabble.

Cheers, Jerry

---

### Post by DougieFresh4U on 2009-04-30
Any thing good on the 'ATI'  along the way?
'fglrx' doesn't work on the .29 or .30 kernel
I'm stuck with the onboard 'ATI Radeon HD 3200'

---

### Post by BGFG on 2009-05-01
I'm not on karmic yet, but with the installation of the -85 driver i've seen a drastic drop in memory usage. anyone else ?

---

### Post by ronacc on 2009-05-01
its already up to 70 posts , [http://ubuntuforums.org/showthread.php?t=1140246](http://ubuntuforums.org/showthread.php?t=1140246)    it put him to sleep:P

---

### Post by mabovo on 2009-05-02
Have anybody read this comparision ?

[http://distrowatch.com/weekly.php?issue=20090427#feature](http://distrowatch.com/weekly.php?issue=20090427#feature)

and conclude with ....

> While some may be touting that Debian is obsolete now that Ubuntu rules the roost, I have to whole-heartedly disagree. Debian provides a solid, stable environment that you can really trust and rely on. Ubuntu, on the other hand, appears to have put more priority on a timely release over stability and, as a result, seem to rush out half-baked releases. There's nothing that Ubuntu can do that Debian can't - it's just a matter of how simple that task is. Certainly Debian takes a long time to release more up-to-date stable versions, but they are just that - stable. If you are looking for something more up-to-date, try Debian testing. It's still very stable, with the added benefit of being a rolling release. I can't help but feel that while Ubuntu is shouting their achievements from the rooftops, Debian is silently plugging away in the background making things work. Please Debian, don't go anywhere!

---

### Post by kaffeine on 2009-05-03
running 185.18.04 on 2.6.30-2, so far so good. compiz performance looks real snappy.
jumping back into ubuntu after a very long time, it's come a long way indeed:)!

K

AMD64X2.2GBRAM.SLi2xNVIDIA6800GT

---

### Post by caryb on 2009-05-07
After upgrade yesterday my nvidia driver fails, I have gone back to the nv driver to get my gui back. My question is who do I direct feedback to as this is not a official driver?


Cary

---

### Post by maxim99 on 2009-05-26
Thank you for this. This has been the perfect ending for a pretty lame day. :)

---

### Post by tad1073 on 2009-05-27
2.6.30-6 w/180.44

---

### Post by Regenweald on 2009-05-27
> **mabovo said:**
> Have anybody read this comparision ?

[http://distrowatch.com/weekly.php?issue=20090427#feature](http://distrowatch.com/weekly.php?issue=20090427#feature)

and conclude with ....

I installed Debian once and really did not like it. So i deleted the partition and simply continued using Ubuntu. What i will never understand is persons who criticize Debian and sing Ubuntu praises in the same breath, I mean, one of the first thing that Ubuntu does with a new release is SYNC from Debian. Without a rock solid Debian base where would we be ? 

Treating the Debian project with anything other than respect is stupid. Common sense dictates: No matter how wild your architecture, no matter how ambitious and cutting edge you intend to be, you build from a stable base.

Anyways, i digress :) waiting for the 185.** to hit the ppa's, the manual install is too tedious when i change kernels....:)

---

### Post by plun on 2009-05-27
> **Regenweald said:**
> 

Anyways, i digress :) waiting for the 185.** to hit the ppa's, the manual install is too tedious when i change kernels....:)

There is a ppa for the latest driver, several of us are using TheFirstM ppa

[https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)

use jaunty as ppa-adress.

;)

---

### Post by crjackson on 2009-06-03
> **autocrosser said:**
> This will help everyone just a bit more :):):):)!!!!!!!

On Fri, Apr 24, 2009 at 9:32 PM, Bryce Harrington [EMAIL="bryce@canonical.com"]<bryce@canonical.com>[/EMAIL] wrote:
[INDENT]> A little Jaunty Release Day present from the Ubuntu-X team. ?:-)
>
> From past releases, we know that often people want a way to try out
> newer drivers than were included in the official release. ?To make life
> a little easier, we've put together a PPA with some newer X drivers:
>
> ?[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/]("https://edge.launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/")
>
> You can see that already we have new stable versions of nearly all the
> major video drivers for your video-ing pleasure.
>
> I can't promise that we'll be keeping it up to date or fixing bugs, but
> we'll do what we can. ?We're going to treat it as a "stable" PPA, and
> only post stuff we feel is likely to be better in some respect than
> what's in the release
[/INDENT]
It has a newer nvidia driver---180.53



180.60 is the newest stable but it looks like the ppa only has 180.53. Any chance this will get updated soon?

---

### Post by ktp on 2009-06-03
> **crjackson said:**
> 180.60 is the newest stable but it looks like the ppa only has 180.53. Any chance this will get updated soon?

[https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)

---

### Post by crjackson on 2009-06-04
> **ktp said:**
> [https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)

I see the 185's am I missing the 180.60's? I just don't see them.

---

### Post by crjackson on 2009-06-07
> **ktp said:**
> [https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)

Well, it seems this ppa has build problems with the 185.18.14 drivers. I guess I'll give them a try when the issues are resolved.

Have Bryce and Alberto already stopped updating their ppa?

---

