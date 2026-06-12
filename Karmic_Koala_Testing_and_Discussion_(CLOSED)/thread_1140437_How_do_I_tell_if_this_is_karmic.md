---
title: "How do I tell if this is karmic?"
date: 2009-04-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2009-04-27
O.K., did a fresh jaunty install, did update manager, changed jaunty to karmic in /etc/apt/sources.list, ran update & upgrade which did something with a whole bunch of packages, it boots, how do I tell if it's really the early version of karmic?

It's still 2.6.28-11?

On jaunty I'm running kernel 2.6.30-rc3 which is better for intel video graphics than 2.6.28-11.

Thanks, Jerry

---

### Post by _Purple_ on 2009-04-27
```
uname -a
```

---

### Post by ghindo on 2009-04-27
Run:```
cat /etc/lsb-release
```And it should tell you what version of Ubuntu you're running. :popcorn:

---

### Post by Mehall on 2009-04-27
lsb_release -d

---

### Post by autocrosser on 2009-04-27
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu karmic (development branch)"


:guitar:

---

### Post by jerrylamos on 2009-04-28
Yep, that did it, thanks.

cat /etc/lsb-release

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu karmic (development branch)"

Jerry

---

### Post by meeples on 2009-04-29
i would have just checked system monitor... im not a fan of doing everything through terminal.. :P

---

### Post by Maheriano on 2009-04-29
So is there some advantage to having a very very very early version of something that won't be finished for 6 months?

---

### Post by ghindo on 2009-04-29
> **Maheriano said:**
> So is there some advantage to having a very very very early version of something that won't be finished for 6 months?Street cred. ;)

---

### Post by yellerKat on 2009-04-29
> **Maheriano said:**
> So is there some advantage to having a very very very early version of something that won't be finished for 6 months?

I've got an old but still capable laptop on which I'll learn more about linux while following the development cycle of Karmic - seems like a good idea to me!

---

### Post by autocrosser on 2009-04-29
> **Maheriano said:**
> So is there some advantage to having a very very very early version of something that won't be finished for 6 months?

A good way to help "steer" the final....or at least work on your linux skills :p:p

Really---I like it to help my fav distro along--been with Ubuntu from Warty/Breezy & still luvin' it.

---

### Post by Kevbert on 2009-04-30
From Jaunty to Karmic was 236 updates for me and 96.1Mb of downloads...let's see what breakages we can find...

---

### Post by autocrosser on 2009-04-30
Already had a "problem" with sendmail (broken with updates) & Gee, took me 10 minutes to find the problem (guess I'm getting slow in my old age:P)---That & python-apt needs to be uploaded...normal minor breakage---BRING IT ON!!!!!! I want breakage that will work my brain a bit........

---

### Post by Kevbert on 2009-05-01
Synaptic is broken (as expected). Just try to look at the repos.

---

### Post by autocrosser on 2009-05-01
Yes---Software Sources is really broken right now & that's why Synaptic breaks there also--Not sure a bug has been reported---

---

### Post by matthew.ball on 2009-05-02
> **Maheriano said:**
> So is there some advantage to having a very very very early version of something that won't be finished for 6 months?
My laptop's acpi is fuddled under 2.6.28, but fixed with 2.6.29 .. I'm thinking of upgrading purely for the kernel update.

---

### Post by Gina on 2009-05-02
It's mainly a case of playing with trial software, finding and reporting bugs to help the developers make better progress, fixing things yourself (if you're able) and feeding those bug fixes back.  The joy of being a part of the development of the next version of your favourite OS.  :) :)

---

### Post by rajeev1204 on 2009-05-02
How do i install karmic on a new partition?

Are there iso's for download?

---

### Post by Gina on 2009-05-02
Not yet (though I don't know if there are daily builds yet - I don't think so) Alpha 1 is the first ISO release.  

What you have to do is install Jaunty then replace all references to jaunty with karmic in the sources.list, then update.  As mention several times before.  If you don't know how to do this you suould wait for the Alpha, at least - maybe wait until later when things have settled down more.

---

### Post by jerrylamos on 2009-05-02
> **Maheriano said:**
> So is there some advantage to having a very very very early version of something that won't be finished for 6 months?

Testing early versions gives the developers a "heads up" on impending problems.  Sometimes when we early testers yammer about a problem like intel graphics on Intrepid it may go two months before there's a fix, like black listing Compiz for affected machines.  Compiz decided to use some code paths no one else does, and they don't work with intel graphics.  Compiz is not about to change just because it doesn't run on some pc's.  Took us a good while to track that down.

I dabble with early ubuntu's on four pc's ranging from 1 gHz laptop to a 3.3 gHz floor sitter.  Various problems show up on each, example might not even boot so they are all dual or triple booted in case some updates crash altogether.  They haven't on karmic yet......I guess they're not trying hard enough.

Jerry

---

### Post by zika on 2009-05-04
> **matthew.ball said:**
> My laptop's acpi is fuddled under 2.6.28, but fixed with 2.6.29 .. I'm thinking of upgrading purely for the kernel update.
You could always just try [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc4/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc4/)

---

### Post by matthew.ball on 2009-05-09
> **zika said:**
> You could always just try [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc4/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc4/)
I wish I knew how to upgrade the kernel :p

I made a post here a while back asking how, but got nothing...

I don't really care about the battery issue that much, but it would be nice to see it working...

---

### Post by taavikko on 2009-05-09
> **matthew.ball said:**
> I wish I knew how to upgrade the kernel :p

I made a post here a while back asking how, but got nothing...

I don't really care about the battery issue that much, but it would be nice to see it working...

Download the "headers and image" .debs for your architecture
and double click, that's it.

2.6.30.4 is available via repositories also.
which you can do "sudo apt-get install"

---

### Post by matthew.ball on 2009-05-09
Oh no, I think I have done something wrong. *Sigh*

I downloaded the .debs, I double clicked the image first, and all the dependencies were satisfied so I installed it .. but it got to the nvidia module and failed or something (though apparently the install was successful), so I thought installing the header would work better, but apparently it's dependencies aren't satisfied.

This is the reason I would rather have just updated my Ubuntu install for the new kernel. If I can break something, I always will.

---

### Post by afv on 2009-05-09
> **matthew.ball said:**
> Oh no, I think I have done something wrong. *Sigh*

I downloaded the .debs, I double clicked the image first, and all the dependencies were satisfied so I installed it .. but it got to the nvidia module and failed or something (though apparently the install was successful), so I thought installing the header would work better, but apparently it's dependencies aren't satisfied.

This is the reason I would rather have just updated my Ubuntu install for the new kernel. If I can break something, I always will.

There are two headers packages. You must install linux-headers-2.6.30-..._**all** before linux-headers-2.6.30-..._**i386**.

You can get NVIDIA drivers that work with DKMS from [Michael Marley's PPA](https://launchpad.net/~thefirstm/+archive/ppa). :)

---

### Post by matthew.ball on 2009-05-09
> **afv said:**
> There are two headers packages. You must install linux-headers-2.6.30-..._**all** before linux-headers-2.6.30-..._**i386**.

You can get NVIDIA drivers that work with DKMS from [Michael Marley's PPA](https://launchpad.net/~thefirstm/+archive/ppa). :)
Ok, so I needed to install the headers labeled "all" first?

Sorry about this, this isn't really Karmic-topic-worthy, but thanks for the help anyway.

Now, my laptop obviously won't boot - well it boots but no display is loaded, I can work in terminal so it's not the end of the world. But before when I checked sudo apt-get install, the latest kernel image they had was 2.6.28-12, i.e. the kernel I *was* using before I tried to update. So I can't update via the repos, and I can't get a GUI open to download the correct files.
Unless of course I can download them here and transfer them across during a live session, re-login and then install them from terminal....

I think I have 2 possibilities here, one is finish up the 2.6.30 install, the other is load a LiveCD and change the menu.lst file so it boots from the 2.6.28-12 kernel, or maybe the latter won't work...

Edit: Update:
I'm obviously running 2.6.30 now, as the battery and keyboard keys are finally detected (awesome), but unfortunately, I'm yet to find a working nvidia driver, perhaps I'm not looking hard enough (perhaps I don't even know what I am looking for!).

Thanks for the tip zika, and thanks for the help taaviko and afv - I very much appreciate it, even if I do blindly follow the instructions and get myself into a mess >.<

When downloading the nvidia drivers from Michael Marley's PPA, do I download a single tar.gz or the individual .debs, or all of them? Sorry again :p

---

