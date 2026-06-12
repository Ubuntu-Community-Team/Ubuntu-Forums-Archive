---
title: "Installing Skype 2.1.0.81  beta 2"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by ioliver on 2011-01-04
Has anyone tried upgrading the Skype 2.1 Beta 2 on lubuntu 10.10?

Which of the packages on the Skype download page is best? Dynamic?

Thanks

Ian

---

### Post by ioliver on 2011-01-04
Hmmm, or am I barking mad and is the "2.1.0.81 beta" the same as what Skype call Beta 2 on their web site? Did they really go Beta a whole year ago and not yet have a final release ready?
Ian

---

### Post by nomko on 2011-01-04
Sometimes you will find applications that bears the mark of Beta, but in fact is a stable version which wiull be maintained as well. In this case, it looks very dandy to mark your latest version as beta so that everyone who is using or wants to use Skype downloads that version just to have the idea that they have the very latest version.

---

### Post by SteveDee on 2011-01-04
Professional beta software should go through a proper Test Plan, and only be released if it is stable (in operation) and the scope of any identified problems are deemed to be safe/acceptable. Beta software may also be missing some of the originally planned features or functionality.

Unfortunately in the amateur arena, beta software too often means "I can't be bothered to test this properly, perhaps you can!"

I suspect Skype's Linux team may not have the resources required to develop, test, and rework the Linux versions to a final release standard before they become out of date (e.g. the most recent "deb" package is for Ubuntu 8.10). I guess most of their effort goes on the Windows version.

I've used the Ubuntu 8.10 32bit deb quite a bit on Lubuntu 10.10 and it seems stable (in operation). The only problem I can think of is that I don't see an image from my webcam during a video contact (I can see the other person & they can see me).

---

### Post by oldsoundguy on 2011-01-04
Skype's approach is "maybe Linux will go away"

The beta version works for some, but, not for all by any means.

It borks sound for some, borks the video for others. (Ubuntu resident programs such as Cheese work just fine.)
On other computers, it fails to even go on line to run the test calls.

It is total crap!  And seeing that the "beta" is nearly 2 years old with absolutely NO work or development on it since the beta release, tells the whole story about Skype and it's attitude toward Linux!
The software is proprietary closed source on top of that, so the Linux community can not jump in and help!

---

### Post by SteveDee on 2011-01-04
> **oldsoundguy said:**
> Skype's approach is "maybe Linux will go away"...

...And seeing that the "beta" is nearly 2 years old with absolutely NO work or development on it since the beta release, tells the whole story about Skype and it's attitude toward Linux!...

I don't disagree with the sentiment, but (in the interests of debate) allow me to play the role of "Devils advocate".

I don't think Skype have a problem with Linux, they just want to make money. So they will go where the biggest market is (Windows users). But they also provide versions for MAC OSX (a Unix derivative), Linux (also a Unix derivative), Android (another Unix derivative) & so on. The current Linux version of Skype (2.1.0.81) was released 11 months ago.

Its a nightmare trying to write software for Ubuntu Linux. Every 6 months they release a new distribution. What might be called "components" or "building blocks" are changed on a whim. By this I include: the kernel, windows manager, desktop manager, sound server & so on. You get your webcam & sound working on one version, only to find they don't work on the next release.

Problems with Skype on Ubuntu 9.04 to 10.04 may be due to Linux webcam drivers, and frequently require Skype to be loaded with the command: LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype

I've been using Ubuntu since 8.04, and most of the releases have been very good. But for me, 10.04 was a total disaster, mainly due to problems with Intel graphics support. These problems seem to have been fixed with 10.10, and Skype no longer needs to be run with the command above.

If there is an open source alternative to Skype I'll try it....so long as I can still talk to family and friends, scattered around the world, who are using Windows or MAC computers.

---

