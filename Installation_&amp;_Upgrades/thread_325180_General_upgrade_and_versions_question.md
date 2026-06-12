---
title: "General upgrade and versions question"
date: 2006-12-25
forum: Installation &amp; Upgrades
---

### Post by therobbot on 2006-12-25
Hi,

I'm currently planning on completely switching from Windows to Linux and so far I really like Kubuntu. However the one thing that I still feel a little uncomfortable with is the whole versions-based software distribution system. A lot of times I had bad experiences with upgrading to new distribution versions in different distributions (like Suse, for example). Also I don't know yet if I like the idea that the distribution decides which programs should be updated or added and how my system should behave. 

For this reason I'm wondering how do most of you handle this? Do you upgrade to the newest version once it is out? Does it work flawlessly? Does it mean you have to reapply everything you changed in your system that's beyond user-based settings? 

I already got a little annoyed with that without even upgrading when a new kernel got installed and I had to reapply suspend2.

Actually for all this reasons I'm thinking about using Gentoo instead cause from what I understand it is not versions based and gives more freedom to the user. However I'm unsure if this is a wise decision because I don't want to have to configure a lot all the time but want to have a system that just works. 

I really prefer Linux over Windows but this is the one thing that still bugs me. In Windows I can just install updates for a couple of programs I want and it won't effect the overall system at all. In Linux I still have the feeling that I either have to use old versions or upgrade everything. 

I'd be very happy about some insight about this from experienced users. Also if you have some links that better explain this, please post them.

Thanks a lot!

Tobias

---

### Post by bulldog on 2006-12-25
This can be a whole story or a short one.
You're not forced to upgrade,when your computer is running fine and you're happy with it,just leave it that way.

If you like to have the latest,greatest software,well you have to upgrade.

There's a little difference between upgrade and update,however.
Upgrading means generally going to a newer distribution like from Dapper to Edgy.
I personally prefer a fresh install and install all my software again,but it's not really necessary 
if you have made a separate  /home partition.

Updating means you'll get the safety updates and updates to your applications from the repositories to keep your machine safe and sound.
You can refuse this kind of updates,but I think it's not a wise thing to do so.
If you have a kernel which you want to keep and not want to update,you can lock it in synaptic,so you can do with most of your software.

Hope this clarify some things for you.

---

### Post by therobbot on 2006-12-25
Hi,

first of all thanks for the reply. I still have a couple of questions, though...

- Why isn't it possible to have new programs with older versions? I mean... what exactly does it break? Why does it work in Gentoo but now versions based distributions? Does it brake upgrading if I compile (updated) programs myself?

- if I keep an older kernel, there's probably a security risk, right? But it's probably a good idea if I have for example a repo with a patched suspend2 kernel to lock the original kernel but wait for an update from this repo to update. Is this possible? Will it be automatic?

- Does it work well to have a separate home partition and then reinstall a new version? Will my personal settings (e.g. KDE settings) still work or will there be a lot to reapply?

- If I want to reinstall a new version, is there a program that keeps track of my installed programs and reinstalls them from the new repos as a batch job? I think that would be very convenient...

Thanks a lot again

Tobias

---

### Post by bulldog on 2006-12-25
All you have installed from the original ubuntu repo's will be updated and upgraded automatically.
The repo's outside the ubuntu ones are the ones who are gonna give you the head ache.

If you have a separate /home and you're using **only** applications and themes and all the stuff,that comes out the ubuntu repo's,you will have a nice upgrade in most cases.

Like I said if you're using themes you installed by yourself or you compiled your own kernel or what ever,that's what's gonna break your upgrade. 

It's possible for sure to update applications by your self,but you have a fair chance you run in dependency trouble.
The problem is in fact that linux shares a lot so you won't have to install large program updates,the counterpart is that you can't easily update one application without affecting a lot of others. [dependency's]

---

### Post by therobbot on 2006-12-25
> **bulldog said:**
> 
The problem is in fact that linux shares a lot so you won't have to install large program updates,the counterpart is that you can't easily update one application without affecting a lot of others. [dependency's]

Hm... yeah, I guess that's the thing I have to get used to. 
But somehow I just don't like the idea that upgrading may change everything. I want to be in control of what's changed. For example I first tried Dapper and liked it. Then I upgraded to Edgy and now I found that they have a messed up way of handling media (replacing media:/ by /media everywhere which by itself is not a bad idea but for example opening of audiocds as audiocd:/ stopped working properly). This is something that bothers me. I don't want things to change the way they work without me being in control about it. This is one of the reasons I wanted to get rid of Windows and now I feel it's happening again... do you know what I mean?

Thanks anyway. I hope I will finally figure out how to get what I want...

Tobias

---

### Post by bulldog on 2006-12-25
Well don't upgrade then :D 

You can change almost anything to your likings,but you need to be comfortable with linux and know where to look for things you want to change.

---

### Post by therobbot on 2006-12-25
Hm... but I think it's bad that to get the decision is: get the newest program versions of your favorite programs OR have the system running the way you want. 

I think that settings (such as where the media location points to) should be configurable on user basis with config files and not compiled. I consider this bad practice somehow and it doesn't feel like the freedom I expect from Windows...

Tobias

---

### Post by TheWizzard on 2006-12-25
> **therobbot said:**
> Hm... but I think it's bad that to get the decision is: get the newest program versions of your favorite programs OR have the system running the way you want. 

this trade-off doesn't really exist. i'm using dapper and most of my software is up-to-date through the backports repos. dapper is *long term support*! you can also manually upgrade your software (for firefox this was necessary). 
and yeas, if you want to run bleeding edge, then you may loose stability. but this is similar to running MS vista beta.

---

### Post by therobbot on 2006-12-25
Hi again,

so if I don't want to constantly upgrade it's a better idea to use Dapper, Backports and manually upgrade programs not in the backports and then after a couple of years do a completely new install, right? Is it also possible to get new KDE versions through the backports (KDE 4, for example)?

Ok, the way I see it I have 3 possibilities now:

1. Use Dapper (or another distribution with LTS), Backports and maybe lose the possibility to upgrade by manually updating things.

2. Use Edgy and try to stay consistent with the system so that I can always upgrade to new versions

3. Use Gentoo 

Is this right?

Tobias

---

### Post by TheWizzard on 2006-12-25
> **therobbot said:**
> Hi again,

so if I don't want to constantly upgrade it's a better idea to use Dapper, Backports and manually upgrade programs not in the backports and then after a couple of years do a completely new install, right? Is it also possible to get new KDE versions through the backports (KDE 4, for example)?

Ok, the way I see it I have 3 possibilities now:

1. Use Dapper (or another distribution with LTS), Backports and maybe lose the possibility to upgrade by manually updating things.

2. Use Edgy and try to stay consistent with the system so that I can always upgrade to new versions

3. Use Gentoo 

Is this right?

Tobias


there are many possibilities. you'll need to find the one that suits you. 
gentoo is very nice, but may be hard if you're inexperienced. it is a good way of really understanding linux, though. 
edgy was meant to be 'edgy', although it is pretty stable. 
dapper was meant as a stable release. 
there are many other linux distros out there with many different purposes. 

basically, the question you need to ask yourself is what kind of os you want. 
if you need your computer for work, dapper is a stable distro with pretty up-to-date software. 
if you want to play around, go for edgy. or Feisty Fawn Herd 1. or gentoo. 

so maybe you should post a wishlist of what you want, so we can advice you what to do.

---

### Post by therobbot on 2006-12-25
Ok, so here's my wishlist:

- I use the system at home. It's behind a router so it doesn't have to be the most secure system (after all I ran Windows for years without a problem. I guess this fact speaks for itself ;))

- Generally I want everything to stay the way it is once I configured everything to my likings. I.e. I don't want to upgrade and find that the way that basic things work suddenly changed.

- However I'd like to be able to stay quite up-to-date with applications I use a lot like Firefox or Amarok. 

Is there anything planned on when the next LTS Version will be out? Because generally I'd say that at the moment I'd still like to play around a little more but sometime I'd like to settle for a little longer (couple of years).

Tobias

---

### Post by TheWizzard on 2006-12-26
ok. makes things clear.
i'd advice you to play around with edgy for a few months. in april Feisty Fawn will be released and you can go to that one for a long time. 
to stay up to date, make sure you enable the backports. sometimes, you need to install stuff manually, but help is always available. see for example how to install firefox 2 in dapper: 
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by therobbot on 2006-12-26
Ok, thanks, I guess I'll try this. Even though I don't really like the way Edgy handles some things in KDE (like using /media instead of media:/ without being fully functional)

I hope that someday I will feel more comfortable with the way Linux works. But after all it's great to have a nice community here with *ubuntu. It helps a lot. Thanks

Tobias

---

