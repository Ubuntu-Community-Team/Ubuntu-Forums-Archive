---
title: "Trouble with wireless card (and a few other things)"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by alanroy on 2007-03-24
I'm a die hard XP fan, but thought I'd try some linux - and everyone raves about Ubuntu.
(when I went to download it, there is two options 6.10 and 6.10LTS there is no mention at all about what the difference is between them)

Firstly, it froze when trying to run from the CD, tried both drives (each on a different channel) no joy, eventually turned off 'enhanced performance' on the IDE channel in the bios, then it worked. (XP seems to install fine though)

It actually looks quite nice, and I thought yes I could use this - but before I install it proper I thought I best try the network. 45 minutes later still no joy, tried the forums, and there appears to be a wiki about network cards, so chose the card closest to mine and saw 

*"Need to install ndiswrapper-utils and your windows driver. In Hoary you also need to change value of radiostate from 1 to 0."*

What on earth does that mean? Hoary? ndiswrapper? its gibberish, also what is fiesty? edgy? none of this makes any sense

XP just works - but still I will persevere, and maybe with googles help I will get it working.

(edit - searched for ndiswrapper, ended up on a download page [http://packages.ubuntu.com/](http://packages.ubuntu.com/) 
warty 
hoary 
hoary-backports 
breezy 
breezy-backports 
dapper 
dapper-backports 
edgy 
edgy-backports 
feisty 

???? 

I have version 6.10 I don't have warty, farty or slapper)

---

### Post by Lord Illidan on 2007-03-24
First, this is not a testimonial, so this should be moved to a support forum.

Also, you are not being helpful here. Give us the details about your card. What kind of card is it? Is it wireless? Is it a Broadcom card?

About ndiswrapper, it is a program which enables the windows drivers to be run in linux for wireless usage.

Hoary, Edgy and Feisty are versions of Ubuntu.

7.04 is Feisty
6.10 is Edgy.
6.06 is Dapper - Btw, you said 6.10 LTS - that should be 6.06 LTS. LTS = Long Term Release, that means that support for it will continue for quite a long time.
Then, there are Breezy, Hoary and Warty editions.

---

### Post by aysiu on 2007-03-24
> **Lord Illidan said:**
> First, this is not a testimonial, so this should be moved to a support forum I've moved it to the support forums.

---

### Post by alanroy on 2007-03-24
The reason I didn't put it in support is because I don't want any support, I wanted to illustrate my problems from the perspective of someone who has never touched Linux - and the closest board I could find was "tell us how great we are" as opposed to "tell us how not great we are"

If you go to ubuntu.com from the front page there is no explantion of what farty, slapper or wanky means, or indeed what LTS means its just not very user friendly

It was merely a bit of constructive feedback.

---

### Post by PriceChild on 2007-03-24
I have closed this thread.

In future please use "report bad post" button to make the staff aware of policy violating posts.

---

### Post by aysiu on 2007-03-24
> **alanroy said:**
> The reason I didn't put it in support is because I don't want any support, I wanted to illustrate my problems from the perspective of someone who has never touched Linux Then I'm merging you with the desktop readiness thread > - and the closest board I could find was "tell us how great we are" as opposed to "tell us how not great we are" Testimonials by definition and convention are the relating of positive experiences. If you want to complain and rant and make fun of Ubuntu, you can do so in this thread.

> If you go to ubuntu.com from the front page there is no explantion of what farty, slapper or wanky means, or indeed what LTS means its just not very user friendly

It was merely a bit of constructive feedback. *farty, slapper, or wanky*? Yes, extremely constructive. I can see those sorts of remarks really making an improvement in the quality of the software.

If you want actually be constructive, there are some suggestions [here](http://www.ubuntuforums.org/showthread.php?t=78741) for how to do so, but based on what you've written so far, I don't think you really want to be constructive.

---

### Post by Frak on 2007-03-24
> **alanroy said:**
> The reason I didn't put it in support is because I don't want any support, I wanted to illustrate my problems from the perspective of someone who has never touched Linux - and the closest board I could find was "tell us how great we are" as opposed to "tell us how not great we are"

If you go to ubuntu.com from the front page there is no explantion of what farty, slapper or wanky means, or indeed what LTS means its just not very user friendly

It was merely a bit of constructive feedback.
Tell me your wireless card, I've dealt with a great deal of them, and I may be able to help.

And no, XP does not work "out of the box", if it did there would be no need for drivers, and you must respect Linux as a community project, some manufacturers are out to make sure that some hardware **doesn't** work with Linux so Microsoft will decide to keep supporting them.

Ranting never solves anything, we refer to people like you as a "troll", and we don't feed trolls, but we will help if we can.

---

### Post by Sammi on 2007-03-24
Total flamebait. Stop responding.

---

### Post by Frak on 2007-03-24
It is not flaimbait in any sort, I seriously want to know what card he has so I **can** help, I'm not much help with just the term "Wireless card"

---

### Post by aysiu on 2007-03-24
> **Frak said:**
> It is not flaimbait in any sort, I seriously want to know what card he has so I **can** help, I'm not much help with just the term "Wireless card"
And the OP seriously said he didn't want any help but just wanted to complain. I originally had moved it to a support area so that he could get some help, but he said he didn't want it. He would rather make fun of the Ubuntu naming scheme and pretend that the community has been mean to him and that's why he's leaving.

---

### Post by Frak on 2007-03-24
Sorry, didn't read that part, I just read the part about his wireless not working so I thought I'd help.

---

### Post by alanroy on 2007-03-24
Right, please all calm down ...

My point was this, going from the front page of ubuntu.com, there is no reference to edgy or whatever, yet everything else in the Ubuntu world appears to refer to different versions by these names - one would assume that in the same way a user would be confused if Microsoft reffered to Vista in one part of its website, but called it longhorn everywhere else

Perhaps it would be easier if they were only reffered to by version numbers.

The next point was this ndiswrapper business, it appears in the wiki, but no explanation of what it is, what it does, or if it doesn't, what do you do to make it do.

A really good example would be here
[http://wiki.freespire.org/index.php/Setting_up_Ndiswrapper](http://wiki.freespire.org/index.php/Setting_up_Ndiswrapper)

I'm sorry if I came across as a troll earlier, not what I meant to do.

---

### Post by Frak on 2007-03-24
Do you know which Wireless card you have, the exact brand and model numbers?

---

### Post by alanroy on 2007-03-24
Yes, a Belkin F5D7001

---

### Post by Frak on 2007-03-24
Hmm... Appearantly your card uses a Broadcom chipset, take a look at [this]("http://www.ubuntuforums.org/showthread.php?p=432404") thread.

---

### Post by saulgoode on 2007-03-24
> **alanroy said:**
> Yes, a Belkin F5D7001

Ahhh. That device uses the Broadcomm BCM4306KFB chipset (FYI, the chipsets are what's important, not which plastic case the hardware is shipped in). There is a Linux kernel driver called [bcm43xx](http://bcm43xx.berlios.de/) which should work without your needing NDISwrapper.

---

### Post by cowlip on 2007-03-24
If it's broadcom, it might just work out of the box in Feisty Fawn's beta.

---

### Post by Frak on 2007-03-24
> **cowlip said:**
> If it's broadcom, it might just work out of the box in Feisty Fawn's beta.
I was about to say the same.

---

### Post by aysiu on 2007-03-24
> **alanroy said:**
> 
I'm sorry if I came across as a troll earlier, not what I meant to do. Totally forgiven. The community does want to help you, though, as you can see. So I have returned this to being a support thread so you can actually get some support.

Your points are valid, but I'm not sure they can be helped. The ubuntu.com homepage is doing the right thing by referring to versions by version numbers (less confusing to new users than nicknames), but how can you control literally millions of users and tell them all to stop referring to releases by nicknames? Whenever I deal with new users, I try my best to remember to put 6.06 or 6.10 in parentheses when talking about Dapper or Edgy, but I don't always remember to do that, and that's just me.

As for the *ndiswrapper* thing, that's just poor documentation on that item. Maybe someone who knows stuff about editing the Wiki can fix that page.

If you have a respectful tone, people are more apt to take you seriously and not label you a troll.

Ask for support, and you'll get it. If you have "constructive criticism," give it constructively, and don't resort to making fun of the Ubuntu nicknames, and you'll also be taken seriously.

---

