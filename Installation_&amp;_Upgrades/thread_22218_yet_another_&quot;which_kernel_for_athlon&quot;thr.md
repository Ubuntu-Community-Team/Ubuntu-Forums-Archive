---
title: "yet another &quot;which kernel for athlon&quot;thread"
date: 2005-03-26
forum: Installation &amp; Upgrades
---

### Post by bailout on 2005-03-26
I have installed kubuntu and want to upgrade my kernel. I have searched the forums and haven't really seen a difinitive answer as to which kernel should be used for athlon xp chips, although the question is asked a lot.

I know there is a k7 kernel that is described as being for all amd chips but the i686 kernel is also described as being for new pentiums and athlon xp.

IIRC k7 was the pre release code name for original athlon. I know that recent athlons have adopted a lot of the intel sse instructions as well as or instead of amd specific instructions. Therefore with a recent athlon XP chip am I better running the 686 or k7 kernel?

Also the next step after the kernel is to install nvidia drivers. How does my choice of kernel affect this, if at all? I have a gf4200ti. I have seen some posts talking about ubuntu nvidia drivers not covering the latest cards and that people are having to use the nvidia drivers direct. As my card is old this will not be a problem. Are ubuntu nvidia drivers included in the kernels or do I have to get them seperately?

thanks

---

### Post by Avi on 2005-03-27
Just want to join the question as well.. 
I also would love to know which kernel is more suited for my Athlon XP.

Seems like a pretty basic question too... What kernel should Athlon XP users use?

---

### Post by Dracontopes on 2005-03-27
Right now I'm using the 2.6.10 k7 kernel (Athlon XP-M Barton) but I never tried the i686 kernel, so: *bookmarking thread* :)

---

### Post by bailout on 2005-03-27
Well at least the replies are saving me from having to bump the thread  ;-) 

Perhaps if it stays at the top long enough it might get seen by someone who knows more than we do and we will get an answer  :mrgreen:

---

### Post by rosslaird on 2005-03-27
Adding my request for input...

---

### Post by bailout on 2005-03-28
Ok, as an excuse to bump this thread again, in the hope that someone knowledgeble with Ubuntu will provide the difinitive answer, I will post the advice I have got elsewhere.

That is, that AthlonXP chips are not k7 and hence I would be better off with the 686 kernel.

I haven't tried yet but unless I hear any different by tomorow I will give it a go and see what happens.

---

### Post by Dracontopes on 2005-03-29
I am now running the 686 kernel and I am not really noticing any speed improvements... But that may just be me :) :P Oh yeah I had to rebuild some modules (like fglrx).

---

### Post by tdell on 2005-03-29
Who ever told you Athlon chips are not K7 was completely wrong and should be ignored in the future. Your best bet using any AMD processor is to use a kernel compiled for it. The other kernels will work too but may not have access to some of the features bulit in to the chip.

So, Final Answer---use the K7 kernel with the Athlon.

After all you wouldn't put Chevy parts in your Ford, would you?

Tom

---

### Post by TjaBBe on 2005-03-29
[QUOTE=tdell]Who ever told you Athlon chips are not K7 was completely wrong and should be ignored in the future. Youe best bet using any AMD processor is to use a kernel compiled for it. The other kernels will work too but may not have access to some of the features bulit in to the chip.

So, Final Answer---use the K7 kernel with the Athlon.

After all you wouldn't put Chevy parts in your Ford, would you?

Tom[/QUOTE]

Thanks for the answer! I was using the i686 kernel for my athlon xp too...

---

### Post by bailout on 2005-03-29
tdell, this is the problem, the question keeps being asked and conflicting answers are given.

The "tweak Ubuntu" HOWTO on this forum recomends 686 for XPs, see point 9;  [http://ubuntuforums.org/showthread.php?t=3713](http://ubuntuforums.org/showthread.php?t=3713)

I was hoping that someone "official" could clear up the confusion but it seems not.

The description added to the kernels really needs to use current names for amd chips rather than a pre-release codename from 5+ years ago. Athlon architecture has changed since then. Whether these changes have any effect on the kernel choice is the question.

---

### Post by tdell on 2005-03-29
Perhaps someone "official" should comment but I think any differences would not really be noticeable. Therr may be a slight advantage of one kernel over another that may show up in intensive benchmarking, but for the real world you would not notice a difference.

Anyway, just my opinion.

Tom

---

### Post by Dracontopes on 2005-03-29
[QUOTE=tdell]Perhaps someone "official" should comment but I think any differences would not really be noticeable. Therr may be a slight advantage of one kernel over another that may show up in intensive benchmarking, but for the real world you would not notice a difference.

Anyway, just my opinion.

Tom[/QUOTE]

Precisely, speed increase is not noticable as I said before :) Ah well, default kernel is now 686 and works okay, no need to change that now ;-)

---

