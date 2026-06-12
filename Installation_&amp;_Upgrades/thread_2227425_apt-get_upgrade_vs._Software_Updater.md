---
title: "apt-get upgrade vs. Software Updater"
date: 2014-06-01
forum: Installation &amp; Upgrades
---

### Post by syntaxerror74 on 2014-06-01
There is one peculiar thing I've always wanted to ask about...

My updates have always worked very well, but they were never complete.
Whenever I used apt-get update/upgrade combo on console, I *thought* I had all updates installed...BUT...it wasn't so.
It didn't happen too rarely that I launched Software Updater from 'System Tools' menu and there was another whopping 70 MB to update!

Even though aptitude didn't give any single bit of indication that there was another bunch of updates to install.

How come these two would hardly ever be in sync?

---

### Post by vasa1 on 2014-06-01
There are several posts here: [https://lists.ubuntu.com/archives/lubuntu-users/2014-May/007476.html](https://lists.ubuntu.com/archives/lubuntu-users/2014-May/007476.html) and one thread in this forum on the same matter. I'll post that link soon.

Here: [http://ubuntuforums.org/showthread.php?t=2222325](http://ubuntuforums.org/showthread.php?t=2222325)

---

### Post by syntaxerror74 on 2014-06-02
Oh thanks, I had no idea this was already classified as a *bug*!

I've become a little reluctant to mention the word "bug" in this case, as things would often turn out PEBKAC.

HOWEVER...it's not that simple!

[quote="pfeiffep"]Well I did continue but the question is "What exactly is the software updater doing or missing?"
Maybe I should disable automatic updates and use terminal in the future...[/quote]

That would be different from my case!
I always used terminal but *it is mandatory to use the Software Updater *in combination afterwards, to install those updates that aptitude constantly FAILS to catch!
So it's completely the other way round.

So what **I** want to see finally fixed is that *aptitude* will be able to pull 100% of updates from the repo's, not just 80% - thus making Software Updater redundant!
(Since I'm working mostly at the terminal anyway.)

---

### Post by vasa1 on 2014-06-02
> **syntaxerror74 said:**
> ...
I always used terminal but *it is mandatory to use the Software Updater *in combination afterwards, to install those updates that aptitude constantly FAILS to catch!
So it's completely the other way round.
...
I use apt-get only and don't experience any problems.

---

### Post by syntaxerror74 on 2014-06-02
There are no "problems": it's just for completeness sake.

Just see yourself: use apt-get as you would normally do, and afterwards launch Software Updater.
You can bet your life on it that SU will show you lots of additional things to be updated (those that aptitude would never alert you about!)

It's just that you don't KNOW that there is still something to update if you only use terminal :)
And since you don't know about it, you aren't worried about it. Simple as that.

(Frankly, I only discovered it by accident as well)

---

### Post by vasa1 on 2014-06-02
> **syntaxerror74 said:**
> ...
It's just that you don't KNOW that there is still something to update if you only use terminal :)
And since you don't know about it, you aren't worried about it. Simple as that.
...
Possibly, but I'm happy :)

---

### Post by mörgæs on 2014-06-02
When updating through the terminal the best commands are
```
sudo apt-get update
sudo apt-get dist-upgrade
```

The latter does not upgrade to the next release but it allows kernel updates unlike sudo apt-get upgrade.

---

### Post by vasa1 on 2014-06-02
> **mörgæs said:**
> When updating through the terminal the best commands are
```
sudo apt-get update
sudo apt-get dist-upgrade
```

The latter does not upgrade to the next release but it allows kernel updates unlike sudo apt-get upgrade.That would explain why some people have "incomplete" updates. I've been using dist-upgrade for quite a while.

---

### Post by syntaxerror74 on 2014-06-02
> **mörgæs said:**
> When updating through the terminal the best commands are
```
sudo apt-get update
sudo apt-get dist-upgrade
```

The latter does not upgrade to the next release but it allows kernel updates unlike sudo apt-get upgrade.

Oh, thanks a lot!
I've never used that option before. Yes, maybe this is what Software Updater does under the veil (I haven't yet bothered to peek into the code)

---

### Post by vasa1 on 2014-06-02
> **syntaxerror74 said:**
> Oh, thanks a lot!
I've never used that option before. Yes, maybe this is what Software Updater does under the veil (I haven't yet bothered to peek into the code)
So there's a lesson here, isn't there?

Sorry, you don't have to "bother" to peek into the code at all. Even simple **apt-get upgrade** informs you right there on the screen that some packages won't be installed or upgraded or will be kept back which is why I did more reading and enquired about the difference between what the command line does and what the GUI does. Which is why I'm a bit cautious about rubbishing anything without doing due diligence.

---

### Post by monkeybrain20122 on 2014-06-03
Use synaptic you get everything. It is already installed in lubuntu.

---

