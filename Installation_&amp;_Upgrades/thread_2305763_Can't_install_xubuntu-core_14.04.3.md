---
title: "Can't install xubuntu-core 14.04.3"
date: 2015-12-09
forum: Installation &amp; Upgrades
---

### Post by Bucky Ball on 2015-12-09
*** Before going further, I did miss something:
> 
We have been working on this for a while, which is why you can already install it **starting with Utopic**.

Better get my eyes checked. :confused::oops: The long-term support 14.04 LTS missed out by the looks. 
__


Hi all. I followed this:

> The recommended way is to download the mini.iso, install, and when prompted, install the Xubuntu minimal installation task. If you&#8217;d prefer to wait until after the installer finishes to install the Xubuntu core task, you can simply type 'sudo apt-get install xubuntu-core^' (don&#8217;t forget the caret!) and away it&#8217;ll go.

[From here.]("http://xubuntu.org/news/introducing-xubuntu-core/") When offered the list of machine profiles at tasksel during the mini install (which I've done a million of) there is no 'Xubuntu minimal installation' that I can see. Only 'Xubuntu desktop'. Don't want a full-blown Xubuntu for this machine.

Was intending to install xubuntu-core after initial install anyway so waited until then. I log in to the CLI, update, then:

```
sudo apt-get install xubuntu-core^
```

No dice. I get:

```
E: Couldn't locate package xubuntu-core^
E: Couldn't find task 'xubuntu-core'
E: Couldn't find any package by regex 'xubuntu-core^'
```

I did try without the caret also, but similar response. Can't find package. 

Any ideas? I normally install the mini then add xfce4 and a few other things on first boot and build it up from there. This is a quick job for someone else who wants a very basic system so thought I'd save some time and just whack on xubuntu-core. So much for saving time ... :D

PS: Requests for screeds of output are going to be difficult to fulfill as I am not able to give it directly from the problematic machine as nothing installed (except the base kernel) so at a CLI there. I'm hoping I am simply overlooking something. :-k

* Update: Just wondering if this might do it. From [here]("http://www.linux.com/learn/tutorials/770780-how-to-install-xubuntu-extra-lite-on-ubuntu-1404/"):

```
sudo apt-get install --no-install-recommends xubuntu-desktop
```

Would this equate to xubuntu-core? A bit befuddled why the instructions on the official Xubuntu site seem to be redundant ... but again, I might be missing something.

* Further update: Our old friend Elfy answers one question for me on [another thread]("http://ubuntuforums.org/showthread.php?t=2278048&p=13285278&viewfull=1#post13285278"):

>  xubuntu-core isn't available pre 14.10 for installation from the mini.iso

:) So the question remains: why does 'sudo apt-get install xubuntu-core^' not work when input in the terminal after first boot and login to the CLI, as instructed on the Xubuntu site?

---

### Post by sudodus on 2015-12-09
Why the caret '^'? Maybe a year ago I tested

```
sudo apt-get install xubuntu-core
```

in a basic install from the mini.iso and it worked for me. But it was before 14.04.3

- Did you check without the caret?

- I doubt that **--no-install-recommends xubuntu-desktop** will give the same result as **xubuntu-core** (I suspect it will install more packages).

---

### Post by Bucky Ball on 2015-12-09
> **sudodus said:**
> - Did you check without the caret?

Yep, as mentioned above. No go. I get this:

```
E: unable to locate package xubuntu-core
```

Thanks for the input. :)

I'm tempted to install using '--no-install-recommends xubuntu-desktop' but will stick with this for awhile as curious as to why it is not working. :-k

PS: Have updated fine and it is quite willing to install xfce4 if I let it so no probs with apt-get or ethernet connection ...

PPS: I used the caret as it was explicitly stated not to forget to use it on the Xubuntu-core instruction page I linked to and quoted.

> (don&#8217;t forget the caret!)

 :)

* Further update: More clues. I just tried:

```
sudo apt-get --no-install-recommends xubuntu-desktop
```

... and got:

```
E: Command line option --no-install-recommends is not understood. 
```

? Currently installing xfce4. Will then install lxterminal (weapon of choice), reboot and try again.

---

### Post by sudodus on 2015-12-09
It seems there is no meta-package xubuntu-core in trusty. I don't know if it was there but was removed after the release date, or if it was introduced after trusty (maybe that is why you are supposed to use the caret).

But there is an entry for Xubuntu Core at the qa-tracker,

[Testcases for Xubuntu Core in Xenial Daily](http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/105604/testcases)

Try if that works :-)

But I would not install it for a friend - I would install Xubuntu or Lubuntu or some other flavour depending on the hardware, and maybe tweak it a little.

***Edit:*** I would start with 14.04.1 LTS and update/upgrade to keep the trusty kernel, which is the only one with LTS (until the xenial kernel trickles down in 14.04.5 LTS).

---

### Post by Bucky Ball on 2015-12-09
Thanks again, sudodus. This is install of the original install I did for her, but lighter again! Her hard drive died. She took it to the store and they tested it, was dead so they replaced. I asked her to bring the old one with her and I stick it in the external dock and it just squeaks at me and is not recognised anywhere. So guess it is dead. The store wanted to charge her $199 for installing the drive, Windows and Ubuntu! The drive they sold her was overpriced.

Anyhow, I digress. Yea, guess 14.04 just missed the Xubuntu core loop. I've gone ahead with it from xfce4 up as per last time, except then it was for uni so I basically replicated my machine with Zotero and other stuff. She's not at uni anymore and doesn't need that stuff so be finished shortly I'd expect (she doesn't pick it up til tomorrow). Already at a desktop with the majority of stuff installed. Just doesn't look real pretty! :|

So thanks again for the input and I'll mark this solved. :)

*** Sudodus I did miss something. See the start of my first post, from the xubuntu-core instruction page. Doh!

PS: Thanks for the Xenial link. I'm going to try that on a spare partition in preparation when I have time. :D

---

