---
title: "How can I avoid UNWANTED UNITY updates?"
date: 2012-10-09
forum: Installation &amp; Upgrades
---

### Post by WinRiddance on 2012-10-09
Bear with me, some explanation & background required ... Thanks!

Starting with Ubuntu 9.04 I really fell for Linux and made it my full time permanent OS after nearly 20 years with Windoze. Like many others here I've tried numerous distributions extensively ... Debian, Suse, Fedora, Mint, and so on. Xubuntu along with Compiz and more recently Mate is what I like and prefer, been using those for the past year and a half. Since I don't like or want an Iphone and since my cell phone is nothing but a phone, I have absolutely no use for the Unity desktop. I'm extremely pleased with Xubuntu because it provides me with the ability to customize anything & everything relatively easily. **BUT ...**

... it seems like ever since Unity came out, every few months I'm experiencing system quirks and problems that I can't help but think are related to updates that contain files that I don't use nor want. Overnight mounting issues or printer issues or other inexplicable USB issues even though the system ran flawlessly for months ... usually behaving oddly like this after an update with Unity related items in the Update Manager. I'm not enough of a Linux "guru" though to know what I should or can safely avoid. **That's where I need some help.** For example:

I will never use Unity nor Gnome3, period. I love Xubuntu and the freedom that it provides to me, yet every so often my software update manager contains updates specifically labeled "unity this" or "unity that" for lack of better words. Considering the fact that Xubuntu is XFCE based without anything Unity related (or so methinks), I'm trying to figure out a way to update my system strictly with the applications that I use which are relevant to my XFCE/Xubuntu environment. I find it very frustrating that Xubuntu Operating System installations don't draw their updates from an independent Xubuntu package manager ... **So here's the prize question,** if someone would please help me out here ...

Is it possible to have a clean installation of Xubuntu ... followed by setting up the update manager in a way so that only XFCE related updates are received, while Unity updates are being ignored ... and if so, how would I go about achieving this?
I don't ever want anything Unity or Gnome3 related on my system unless it's [COLOR=DarkRed]**_Linux/System imperative_**[/COLOR] for my Linux (Xubuntu) OS **[COLOR=DarkRed]_to run stable_[/COLOR]** in its current configuration. I would also love to know how I can avoid third party "Unity" updates for applications like LibreOffice, VLC, and so on?
Thank you so much in advance for your time.

---

### Post by jerrrys on 2012-10-09
Im not seeing these unity packages in xubuntu.  What packages are you seeing?

[http://packages.ubuntu.com/natty/xubuntu-desktop](http://packages.ubuntu.com/natty/xubuntu-desktop)

And the desktops are built on gnome so no getting around that.

---

### Post by WinRiddance on 2012-10-10
Okay, pardon my ignorance about Xubuntu but I always thought that XFCE was its own desktop environment with its own themes, i.e. no Gnome at all? Are you saying that it doesn't matter which *buntu flavor I install (Lubuntu, Mint, etc.) because there will always be Gnome something or another files/applications as part of the system?
I never knew that, sorry ...

The Unity stuff that I see in the update manager is sporadic and I can't remember exactly what the details were. Today for example my updates included some Unity stuff for the Firefox browser which I'm using (see image). What I was trying to say earlier was that regardless what I use, if it's all through the Xubuntu package manager then I should never see anything Gnome3, GTK3, or Unity related ... or at least I thought that would be the case.

Another instance of "irritation" is the software center. Even though I did a clean installation of Xubuntu the software center is the "same ol' Ubuntu" software center ... which of course means that I might inadvertently download something from there that's Unity or Gnome3 related. Before Unity came out it made perfect sense to keep *buntu everything in the same synaptic package manager or the software center, but when you consider how radically different (IMO) Unity and Gnome3 have evolved from a couple of years ago, it would be nice if there was a separate safe download center or repository for those people who don't want any of that new stuff on their system.

The printer issues are something that's driving me batty. Until Ubuntu 11.04 with Unity was released I never had printing issues. Ever since then, even when running strictly Xubuntu as my OS, the printer will work perfectly fine for a couple of months and then overnight stop working. Printer is still installed but it shows up as idle, waiting for command or as missing driver files or as not plugged in ... neither of which ever apply. Then I'll eventually do another clean install of Xubuntu, and the same thing happens. Even with different Xubuntu versions like 11.04 - 11.10 - 12.04 ... the printer works perfectly fine and then suddenly overnight, boom, it stops working for no apparent reason. Name brand color inkjet by Brother ...

Exactly the same thing happens with my wireless mouse & keyboard, just not as often. Same thing happens with USB recognition, but again, just not as often. My wifi has never worked, ever since 11.04 but it worked fine before then. WICD or Network Manager, makes no difference which I use. This seems to be going on ever since Ubuntu 11.04 was released and to my knowledge Xubuntu is based on those very same system files, updates, etc. I wish there was a stable way to run Xubuntu without Gnome3 or Unity "anything" installed ... and if there is, I sure don't know how to make that happen. Heck, maybe next time that I do a clean install with everything working properly I'll just disable the updates completely. That should work, right? And it shouldn't really matter since I do a clean install of my system at least twice per year anyway ...

I'm just frustrated at the fact that everything used to be rock solid until 11.04 came around. At least it seems that way to me. My system, 64bit quad core with 8 GB ram hasn't changed, just the stability or rather lack thereof has.

---

### Post by Frogs Hair on 2012-10-10
The menu integration for unity is included with the Ubuntu Firefox package from the repository.  You may  find other software includes these packages as well simply because Unity is the default desktop in Ubuntu .  I don't know if it is possible to block these package via synaptic or not .  All the  Ubuntu  12.04 desktop environments run on top of Gnome 3.4 .  I have 12.10 installed and my XFCE session along Unity and the Gnome Shell  run on top of Gnome 3.6..

---

### Post by WinRiddance on 2012-10-10
Okay, if I'm understanding you correctly you have Ubuntu installed, and then you installed XFCE in order to be able to log into the XFCE session which is why your login menu shows you Unity, Gnome, and also XFCE to log into.

But when I install my Xubuntu from an Xubuntu ISO CD, I don't have those options. When I log out my choice of desktops was (until recently) just the XFCE session or the Xubuntu session ... where I never understood the difference between the two since my screen always looked the same. After I installed the Mate desktop I was able to log into that one as well. Gnome or Unity were never available to me. I chose to install with a Xubuntu ISO because I didn't want to end up with too much fat on my system. Considering how I don't use Gnome3 or Unity that was logical for me ...

I dunno, just think that each *buntu version should have its very own repository to avoid any conflicts because I think that's what I'm running into, files or applications that may occasionally conflict with each other because they've been better optimized for one *buntu version over another. There's no solution in this thread but at least it gave me some more ideas to play around with in the future. Thanks for your time.

---

### Post by HansKisaragi on 2012-10-10
There are different repos but they are for different Ubuntu versions.. not flavors..

Making extra repos for Desktop Environments as well would be pointless and way to time consuming.

I have no idea why you get Unity updates but there must be some weird stuff with Xubuntu.

check synaptic and search for unity and see if anything is installed.

---

### Post by Frogs Hair on 2012-10-10
The XFCE session is different than the Xubuntu desktop and there are a lot fewer packages installed . One example  is that I don't have the Xubuntu gdm or login screen. Though I do have Thunar I use Nautilus as default because that is what the others desktop environments i have installed use it.

If you look in the synaptic package manager you will see all kinds of packages for different desktop environments . An example is the Firefox installer for Kubuntu  is in the available repository but it is not installed.

---

