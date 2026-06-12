---
title: "minimal install walkthrough"
date: 2014-04-16
forum: Installation &amp; Upgrades
---

### Post by nLpPyXR on 2014-04-16
I apologize if this has been asked/done before, but since Trusty Tahr is almost here I thought I should ask first rather than messing up my old and faithful, 6(?) year-old PC. Basically I was hoping someone would be kind enough to type or maybe upload (or link to) a video of a noob-friendly walkthrough for installing the Ubuntu minimal ISO, and then Lubuntu core.

I've visited and glanced over the wiki: [Lubuntu/Documentation/MinimalInstall - Community Help Wiki]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") but there are things I still don't know/get.

For example, is installing a minimal ISO the same as installing a regular (L)Ubuntu ISO except without all the built-in software/apps in the final product? same process I mean, or is it trickier?

Once the minimal ISO has been successfully installed, is it as easy as going to the console and typing "sudo apt-get Lubuntu-core" (or something along those lines) and build up the system with your desired apps from there? I started watching a video ([http://www.youtube.com/watch?v=EqBHe6YTw4s](http://www.youtube.com/watch?v=EqBHe6YTw4s)) and the guy said something about the Minimal install not having network capabilities other than WiFi, which would effectively screw me...

Anyway, yeah, a walkthrough would be very, VERY much appreciated.

---

### Post by Bashing-om on 2014-04-16
nLpPyXR; Yep,

It can be as simple as you care to make it .

I also chose the minimal install, and very pleased with the result.
It is as simple as:
a) download, check md5sum, burn to CD 
b) run the installer and when the base system is installed
b1: ->
```

sudo apt-get update
sudo apt-get upgrade

```
c) install the graphics layer: -> 
```

sudo apt-get install xorg

```
d) install a Desktop manager ( I like xfce4)
```

sudo apt-get install xfce4

```
You will probably want a web browser, say for instance FireFox (lighter browsers are available)
```

sudo apt-get install firefox

```
And you now have a basic totally usable operating system - with some bells and whistles - what else you add is up to you /Maybe a Display Manager -  (??), I don't -- unneeded overhead in my book, YMMV.
That system is whatever you choose to make of it.
You will boot to a terminal, to start the GUI desktop. Terminal command:
```

startxfce4

``` NOTE: DO NOT use elevated privilege [sudo] to start the desk top, permission havoc will ensue in that event!

The 'buntu world is now your oyster ->

And it is
[INDENT][INDENT]all in what you make it
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2014-04-16
> **Bashing-om said:**
> nLpPyXR; Yep,

It can be as simple as you care to make it .what else you add is up to you /[COLOR=#ff0000]Maybe a Window Manager (??), I don't -- unneeded overhead in my book, YMMV.[/COLOR]
That system is whatever you choose to make of it.
You will boot to a terminal, to start the GUI desktop. Terminal command:
```

startxfce4

``` NOTE: DO NOT use elevated privilege [sudo] to start the desk top, permission havoc will ensue in that event!

The 'buntu world is now your oyster ->

And it is[INDENT][INDENT]all in what you make it
[/INDENT]
[/INDENT]
Just in case there is some confusion in the OP's mind, I think you meant "Maybe a [COLOR=#ff0000]display manager[/COLOR]", eg lightdm, gdm, xdm, etc etc, not a window manager;  xfce4 has its own window manager, so that will be installed by default.

Otherwise I agree fully with your comments, and were I able, I would install this way, but my old laptop simply refuses to boot to the 3.13.0-# kernel, or the 3.14.0-# which I have also tried, so I had to install 13.10 for the 3.11 kernel and then update to 14.04 and remove the newer kernel.

---

### Post by Bashing-om on 2014-04-16
@ ajgreeny;

aj,
You are correct, will correct my posting ! . thanks as always,

[INDENT]pay more attention, Bashing- om
[/INDENT]

---

### Post by ibjsb4 on 2014-04-16
This is the full lubuntu desktop

[http://packages.ubuntu.com/saucy/lubuntu-desktop](http://packages.ubuntu.com/saucy/lubuntu-desktop)

This is what you get with lubuntu-core

[http://packages.ubuntu.com/saucy/lubuntu-core](http://packages.ubuntu.com/saucy/lubuntu-core)

The command would be

```
sudo apt-get install lubuntu-core

```

If you wish to leave off the core recommend packages the command would be

```
sudo apt-get install --no-install-recommends lubuntu-core

```

---

### Post by nLpPyXR on 2014-04-16
thank you all for your input, the Ubuntu community is one of its best features that not many people talk about.

On the subject matter at hand, after reading ibjsb4's post and seeing what Lubuntu core contains (lightdm, lxpanel, lxsession and xorg among other things) I'm guessing 2 or 3 of Bashing-om's steps are unnecessary, right?

---

### Post by Bashing-om on 2014-04-16
nLpPyXR; 

Yeah, doing the " apt-get install lubuntu-core" one would not need to install xorg, or a Desktop Manager. The basic Lubuntu system is installed; 

Here be yet another option to install Lubuntu Minimalistically:
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

This is 'buntu
[INDENT][INDENT]you can have it your way
[/INDENT][/INDENT]

---

### Post by ibjsb4 on 2014-04-16
Installing lubuntu-core with or without recommends will give you a working desktop with just that one command.

---

### Post by nLpPyXR on 2014-04-16
Once again, thank you :p

Marked the thread as solved.

---

### Post by ibjsb4 on 2014-04-17
let us know what happens :)

---

### Post by nLpPyXR on 2014-04-17
sure thing, though I can't find the Trusty minimal ISO in the regular releases page: [http://releases.ubuntu.com/14.04/](http://releases.ubuntu.com/14.04/)

...maybe it's not ready yet.

EDIT: can't find it on the "MinimalCD" wiki page either: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by Bashing-om on 2014-04-17
nLpPyXR; Hey,

Like you, to this time I have not seen the minimal install available.
My reference link:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
Has not as of yet been updated.

[INDENT][INDENT]when I can 
[INDENT][INDENT][INDENT]I will too 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by _duncan_ on 2014-04-17
I think Canonical decided to drop the minimal iso after precise 12.04. If I remember correctly, the other flavors (e.g. lubuntu) may still be offering it.

If you do find one, make sure you can connect to the internet after the minimal install, since you need to install tons of packages to get GUI. This shouldn't be a problem if you're using wired internet (e.g. ethernet cable). Getting the minimal install to connect via wifi or mobile broadband usb sticks may be difficult.

---

### Post by nLpPyXR on 2014-04-17
@Bashing-om: this might be it: [http://archive.ubuntu.com/ubuntu/dists/trusty/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/trusty/main/installer-i386/current/images/netboot/) though I'm confused by the "netboot" bit even if it's called mini.iso

@_duncan_: if you visit my links or Bashing's links you'll see mini isos up until 13.10.

---

### Post by Bashing-om on 2014-04-17
nLpPyXR; Yepper !

Looks good to me. But the release date is the 15th, think I will wait a bit longer and see if any "maybe" bugs get shaken out 'tween now and then.

Thanks for that link.

[INDENT][INDENT]all in this together
[/INDENT][/INDENT]

---

### Post by _duncan_ on 2014-04-17
Sorry my bad. I confused alternate install with minimal install. Senior moment.

---

### Post by Bashing-om on 2014-04-17
_duncan_; Yeah !

I am at the point in my life where my Grandfather was. He said " getting old is nothing to be ashamed of, but Lord is it ever unhandy !"

You know something ? He was right !

[INDENT][INDENT]it happens to the best of us
[/INDENT][/INDENT]

---

### Post by su:bhatta on 2014-04-17
> **Bashing-om said:**
> _duncan_; Yeah !

I am at the point in my life where my Grandfather was. He said " getting old is nothing to be ashamed of, but Lord is it ever unhandy !"

You know something ? He was right !
[INDENT][INDENT]it happens to the best of us
[/INDENT]
[/INDENT]


Just checked in here to read what your grandfather had said! 
Well, they seldom are wrong, and this is mighty right :)

---

### Post by nLpPyXR on 2014-04-19
> **ibjsb4 said:**
> let us know what happens :)

I'm typing this in my brand new Lubuntu 14.04. I just couldn't wait anymore and got the Ubuntu Trusty mini.ISO that was last updated on April 15th (after asking if it was safe to do so or not, which it is due to its very few packages) and proceeded to get Lubuntu-core afterwards.

Everything worked like a charm, and I gotta say my 6 year old comp feels lightning fast.

My only complaint so far is that the blanking-after-10-minutes thing is still around, and I don't want to install xscreensaver again just to prevent that from happening... otherwise, life is peachy.

EDIT: oh and as a fun fact, the entire installation process up to having Lubuntu-core up and running takes about an hour with a 1MB connection. I actually took about 9 hours or so to get everything just the way I wanted to, but that was due to a surprise visit from a relative.

---

### Post by ibjsb4 on 2014-04-19
> Everything worked like a charm, and I gotta say my 6 year old comp feels lightning fast.


Congrads :) But this thread has been marked solved and will be overlooked by most. When you find a new problem to solve it is better to start a new thread and use the lubuntu tag.

---

### Post by Bashing-om on 2014-04-19
nLpPyXR; Outstanding !

[INDENT][INDENT]good things do happen
[/INDENT][/INDENT]

---

