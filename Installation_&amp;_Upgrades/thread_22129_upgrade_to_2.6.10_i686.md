---
title: "upgrade to 2.6.10 i686?"
date: 2005-03-25
forum: Installation &amp; Upgrades
---

### Post by kelean on 2005-03-25
Hi, I am currently running 2.6.10.5-i386 hoary 5.04.  What I would like to know is there any advantage to upgrading my kernel to the i686.  My machine is a P-3 450Mhz with 256 megs of ram.  What are the pro and cons?  Is there any noticable improvements?

Thank you for any insite, Kelean.

---

### Post by oracledarren on 2005-03-25
For me it is speed, but I dont know what it would be like with 256mb ram.

I have 1gb and I must say that the difference between 386 and 686 versions in speed is considerable  :-D

---

### Post by XarayaGeek on 2005-03-25
I would like to try and upgrade to i686 myself, how would one go about upgrading the kernel to i686?

---

### Post by panabar on 2005-03-25
[QUOTE=XarayaGeek]I would like to try and upgrade to i686 myself, how would one go about upgrading the kernel to i686?[/QUOTE]

It's so easy, just install linux-686 package.

---

### Post by Dana on 2005-03-26
I tried to do this tonight. With Synaptic I selected Linux-686 2.6.8.1-15 and applied it... not knowing if this is what I actually needed. 
uname -a reports Linux thinkpad 2.6.8.1-3-386 #1 Tue Oct 12 12:41:57 BST 2004 i686 GNU/Linux

That would indicate to me in my newbie uncertainty that I chose incorrectly. Is this so?
Synaptic show the 686 as installed and the 386 as installed/upgradable. Does that mean I now need to use Synaptic to upgrade the 386 image to the 686 image, remove the 386, most likely none of the above?

One shouldn't tackle a task he does not understand but I was feeling brave tonight.
What do I do now?  [-X

Even more stupid I only now realized I posted this in a Hoary section and I am running Warty currently. It's late maybe tomorrow will be a better day.

---

### Post by Dana on 2005-03-26
Okay... I needed to run lilo. Now the reported kernel reflects what I did with Synaptic tonight.

---

