---
title: "Make it a clean upgrade"
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by greg_g on 2007-09-20
With Gutsy fast approaching, I am wondering if there is a way to ensure[1] that one will have a near flawless upgrade.  I know there is no way to guarantee such things, but here is where I am coming from:

I have mostly only ubuntu/canonical repos, but I also have the medibutu[2] and Tevino's Eye Candy[3] repos.

I am worried that something in one of those repos might not get along well with the upgrade.

What is the best plan of action with this?  What do other people do to make sure they don't have unexpected breakages when upgrading distros?

Thanks!

1: "ensure" is a strong word, maybe, "predict there is a pretty good chance overall" would be better
2: deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
3: deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

---

### Post by Pumalite on 2007-09-20
I always do a clean install. They ARE cleaner. Save /home and data and do a fresh install. I'm running Tribe 5 (in a fresh install and it's great). If you have /home in separate partition, better; you can use it, just don't format it during install.

---

### Post by rsambuca on 2007-09-20
Honestly, with those extra repos, I think it is more likely that the upgrade will not go smoothly.  Back everything you want up, and then you may as well try upgrading when the time comes.  I would also consider crossing not only your fingers, but your toes as well.

---

### Post by greg_g on 2007-09-20
The Eye Candy one was the one that was making me worried.

I was thinking about how I would answer people's questions who aren't the most comfortable with installing in the first place.  They did the default install (only 1 partition) and they also added either a non-standard repo or installed some downloaded debs from somewhere.

I am fine with a fresh install (I have a FIesty, a Gutsy, and /home partitions), it is the target audience of this distro that I was asking the question for (Human Beings).

Thanks,

greg

---

### Post by rsambuca on 2007-09-20
I am sorry, I am not quite sure I am following what you are saying here.

---

### Post by Pumalite on 2007-09-20
I imagine he wants to tell his friends about it???

---

### Post by rsambuca on 2007-09-20
> **greg_g said:**
> ... **it is the target audience of this distro that I was asking the question for (Human Beings)**.

Thanks,

gregI've looked this over a few times and I would appreciate a response from you.

Either you are implying that for some reason my reply is not for "Human Beings", or that you really didn't have a question in the first place.  Like I don't spend enough of my time helping people with legitimate problems.  Now I have to spend my time helping people with made up problems?

---

### Post by matt_risi on 2007-09-20
..don't think that's the case at all mate.

I think he's wondering what the target audience of Ubuntu; which are regular people looking to move away from Windows and want to use their computer for simple reasons, should do to upgrade to Gutsy as cleanly as possible.

---

### Post by rsambuca on 2007-09-20
> **matt_risi said:**
> ..don't think that's the case at all mate.

I think he's wondering what the target audience of Ubuntu; which are regular people looking to move away from Windows and want to use their computer for simple reasons, should do to upgrade to Gutsy as cleanly as possible.

Yeah, I don't know.  That is why I asked him/her to respond.

---

### Post by greg_g on 2007-09-20
Woah woah woah...

I wasn't very clear, sorry about that, I was being interrupted while I was typing it out, sorry.

So, what I meant to say is this:

I am curious for myself, and for people that are going to be asking me the same question.

I know there are people who did the basic install (only 1 partition) and they have also added other repositories and/or installed apps from somewhere else.  Is there some way they can test to see if those repos/added software will break the upgrade in some way?  I am pretty sure the answer is "no" they can't check before hand, they just have to try and cross their fingers.

I bring up the basic user with the basic install because they may not be able to A) easily backup ALL of their data and B) don't have a separate /home partition.

I do have a separate partition, which is why I am ok with trying the upgrade, seeing it broke something, and reinstalling.  But that sometimes isn't an option for everyone.

I appreciate your help on this, I really do, I am not asking a hypothetical or made up question.  I have also spent some time on the forums helping people, al beit not a whole lot, but a fair amount.  I am also the leader of the Michigan LoCo team, so I'm actually personally involved with Ubuntu and enjoy it and realize what great support you and other are providing.

And, please just take a note that the either/or you gave (your reply was not for human beings OR I didn't have a question) was not correct.  I did have a question, but the solution I know (try it, if it breaks, reinstall) doesn't always work for the people who ask me the same question.

Thank you for your understanding,

greg

---

### Post by Pumalite on 2007-09-20
They can all come here and ask their questions, We are here helping people almost all day.

---

### Post by rsambuca on 2007-09-20
Thanks for the clarification.  I must be tired as I am a little bit testy tonight.  Oh, and by the way, there is a better chance of the distro-upgrade working if you disable the trevino repo first.

---

### Post by greg_g on 2007-09-20
Thank Pumalite.

And may I ask, in general, is it just "have you added any non-ubuntu repos/installed any third-party app? If so, then your upgrade might not go as planned?"

Honestly, I am asking because I would like to know and be able to help others.  Learn from you all so I can help the people who ask me.

Thanks,

greg

---

### Post by greg_g on 2007-09-20
> **rsambuca said:**
> Oh, and by the way, there is a better chance of the distro-upgrade working if you disable the trevino repo first.

Thanks, I'll try that when the day comes.

---

### Post by greg_g on 2007-09-20
> **greg_g said:**
> 
And may I ask, in general, is it just "have you added any non-ubuntu repos/installed any third-party app? If so, then your upgrade might not go as planned?"


Also, are there certain repos that are ok to go ahead with (probably repos with only a couple of apps that are not part of the ubuntu/debian system)?  I'm thinking Google's and such.

Is the rule "if the package can be found in the ubuntu repos, yet you have another version installed from a different/non-standard repo, it will probably complain" ?

---

