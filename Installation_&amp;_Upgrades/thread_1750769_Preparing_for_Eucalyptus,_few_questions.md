---
title: "Preparing for Eucalyptus, few questions"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by copb.phoenix on 2011-05-05
Hiya! Neighborhood networking idiot here... Wait, let's try this again:

Hello, I'm getting ready to try to use Eucalyptus in Ubuntu 10.04 (both x86 and x64) to form up a cloud, but I'm having a lot of trouble understanding a handful of things that would kinda' sway me one way or the other, or even just help me get to where I want to be with all that. I've tried the Eucalyptus homepage, Wikipedia, and random research - and I don't honestly think it's a case of "it's not there" so much as "I really don't get this".

Like I said, I'm not too strong on the networking. Most of my work focuses on a single machine or else a single abstracted machine - in both cases, I get that client's view of "this is a single thing, and it just works".

Anyway, so that we're just as good and not wasting time, here's the questions:
1) _Is it possible to go straight from Ubuntu 10.04 server to a Eucalyptus server based on 10.04?_ The question feels stupid, even to me, but I've had notes before when I swapped to desktop to server about the kernel and a few optimizations and all these headaches. Do I need to reinstall or just install a package or fifty?

2) _What is the best file system to use for Eucalyptus? Will separate physical drives be treated as a single abstracted drive?_ in other words, does it matter if machine A has two drives 20gb and 30gb while machine B has one drive 120 gb, or moreso is it that I have 170gb at my disposal and considered a single device?

3) _How well does Eucalyptus tolerate the head node changing? Could I use both my laptop and one of my servers as head nodes to no ill effect?_ Usually, I do more computing intensive things at home. Eucalyptus can be configured elastic - but can I push it to play nice with a changing head node? Does that even do anything for me short of adding a bit of bulk to my laptop's setup?

4) _Is it possible to run an arbitrary program on top of a cloud setup and have it distribute in any way, shape, or form the full computing needs?_ Again, like question 2, does it matter more that I have all these separate machines or is it like one abstract machine? If I run, for example, VirtualBox on the cloud, will it use all of the members to help computation or just one? What's the hangup point and where are the potential faults?

5) My basic intention, as part may be gathered, is to abstract away my independent machines and treat them as if they were a single machine, and run this as a GUI-server that works generally better, even if it means I have to run a VM on top of it to do so. Is this an ill-founded desire, or is it perfectly possible? Would there be any advice or "Hey, you're wrong" statements to make about this?



The nature of my machinery is always changing - I'm always scrapping things apart and together again, and I'd hesitate to go for a Beowulf cluster for that very reason. I'm hoping this is the Yatzee scene for the problems I'm facing conceptually.

Thanks in advance, and of course you'll hear it again afterwards.

---

### Post by copb.phoenix on 2011-05-16
It's been a week. I'll only bump this one more time.

---

### Post by Old_Grey_Wolf on 2011-05-16
There is a sub-forum just for Ubuntu Enterprise Cloud (UEC) that uses Eucalyptus. You may get better results for your questions there. It is at [http://ubuntuforums.org/forumdisplay.php?f=392](http://ubuntuforums.org/forumdisplay.php?f=392). A mod could move you thread to that sub-forum.

---

