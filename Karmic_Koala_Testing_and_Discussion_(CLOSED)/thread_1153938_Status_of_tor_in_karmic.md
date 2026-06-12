---
title: "Status of tor in karmic?"
date: 2009-05-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dinxter on 2009-05-09
just wondering if anyone knows the future of tor for karmic after being dropped for jaunty?
[https://bugs.launchpad.net/ubuntu/+source/tor/+bug/328442](https://bugs.launchpad.net/ubuntu/+source/tor/+bug/328442)
the more tor relays the better, especially these days :)

---

### Post by paradigm2 on 2009-05-09
> **dinxter said:**
> just wondering if anyone knows the future of tor for karmic after being dropped for jaunty?
[https://bugs.launchpad.net/ubuntu/+source/tor/+bug/328442](https://bugs.launchpad.net/ubuntu/+source/tor/+bug/328442)
the more tor relays the better, especially these days :)

Well I use Jaunty and I still see Tor there and it is the latest official stable version  in the repository as far as I can tell (as of a few weeks ago anyway).  I think the issue was more of something in the past havign to do with the mantainer or there being one.

But this does appear on Tor's site:

[https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian](https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian)

> 
Do not use the packages in ubuntu's universe. They are not maintained and most likely old and therefore miss out on stability and possibly security fixes.


And they give their own repository there, which I imagine you can use to install to Karmic should it not be in the standard repository already?

---

### Post by meborc on 2009-05-09
i use tor+vidalia (instructions - [http://www.ubuntu-unleashed.com/2007/09/setup-vidalia-tor-gui-with-ubuntu-and.html](http://www.ubuntu-unleashed.com/2007/09/setup-vidalia-tor-gui-with-ubuntu-and.html))

they are a bit old, but they still apply, just be sure to download the latest packages (stable)

---

### Post by dinxter on 2009-05-09
i'm using experimental-0.2.1.x-jaunty from no-reply happily enough, it was more a question about whether or not it will be in ubuntu releases. i might be wrong, tor just doesnt show up on a packages.ubuntu.com search for eaither jaunty or karmic so i'm assuming its pulled from both.
[http://packages.ubuntu.com/search?keywords=tor&searchon=names&exact=1&suite=all&section=all](http://packages.ubuntu.com/search?keywords=tor&searchon=names&exact=1&suite=all&section=all)

---

### Post by dinxter on 2009-05-09
and from the launchpad page is looks pulled past intrepid too

---

### Post by taavikko on 2009-05-09
> **dinxter said:**
> and from the launchpad page is looks pulled past intrepid too

Yep, seems to be deleted from archives since unmaintained,
unmaintained by MOTU? since projects homepage seems still to be alive.

Just starting to get interested in stuff like this, so ,
any alternatives?

Edit: would help if I've only read the earlier posts :)

---

### Post by dinxter on 2009-05-09
i'd still just recommend adding the
deb [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty main
or,
deb [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) experimental-0.2.1.x-jaunty main
repositories to synaptic and installing vidalia.
i dont really use vidalia myself but it seems to make setting tor up a reasonable doddle

---

### Post by nanog on 2009-10-22
Not only is tor not supported but ubuntu dropped the libevent1 library so it is no longer installable via the noreply repos. Works fine if you install the jaunty lib.

---

### Post by Hated On Mostly on 2009-10-22
Here is another PPA for tor and vidalia:

[https://launchpad.net/~sevenmachines/+archive/tor](https://launchpad.net/~sevenmachines/+archive/tor)

---

### Post by rad-boy on 2009-10-23
Trying to make tor work in 9.10  it used to work using this repository:

deb [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty main

with good results until a update & upgrade and then I got the following error:

The following packages packages have unmet dependencies:
  tor: Depends: Libevent1 (>= 1.3e) but it is not installable


I also tried the below repository mentioned here and have no luck with it either....?

deb [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) experimental-0.2.1.x-jaunty main


Any help on making it work?
thanks, rb

---

### Post by nanamin on 2009-10-24
I was running into the same issue as the above poster, and came across this:

[http://webupd8.blogspot.com/2009/10/installing-tor-in-ubuntu-karmic.html](http://webupd8.blogspot.com/2009/10/installing-tor-in-ubuntu-karmic.html)

It installed just fine and seems to be working.

---

### Post by rad-boy on 2009-10-24
I tried the PPA at seven machines and it worked.

[https://launchpad.net/~sevenmachines/+archive/tor]("https://launchpad.net/%7Esevenmachines/+archive/tor")

---

### Post by SevenMachines on 2009-10-25
Since tor seems doesnt seem likely to be synced from debian any time soon I'm going to move to keeping 2 versions of tor in that ppa. A stable version of tor for the last ubuntu stable release, and the development version of tor for the current development release.
Of course, first stop for anyone should be the tor site itself as they have debian repositories that should usually be fine for ubuntu too
 [http://www.torproject.org/docs/debian.html.en](http://www.torproject.org/docs/debian.html.en)

[EDIT] Although there is some movement to try and get tor back in ubuntu for the next release, fingers crossed

---

