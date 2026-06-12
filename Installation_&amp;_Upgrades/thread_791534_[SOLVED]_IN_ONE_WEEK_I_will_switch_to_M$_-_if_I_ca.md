---
title: "[SOLVED] IN ONE WEEK I will switch to M$ - if I cannot solve hibernate/suspend issue"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by realn on 2008-05-12
Hello all,

I am a happy Ubuntu user for quite a few years now.
I just upgraded to Hardy Heron (Kubuntu version) my desktop - ASUS M2V mobo + NVidia graphics card.
Suspend/hibernate don't work any more. 
I tried :
1) the kernel methods (pm-utils + hibernate.sh) - the screen goes blank, a blinking cursor on it, computer hangs - power button used to turn it off.
2) µswsusp package - s2disk, s2ram (which by the way, it's removed from the official package) - the hibernation seems to start, then it hangs at "snapshotting system"(??) section, "suspend console(s)" line.

I tried anything I could find on the net, except a tutorial about how to debug the suspend (I need more the hibernate feature) which seemed to me a couple of weeks of tweaking and testing and all over again.
I can provide any lspci, lsmod, /var/log/kern.log , etc. which someone might need in order to help me.
Please help me with this - because I am getting more and more frustrated - as you can see from the title, too. Thanks to all the community.


Here are my personal opinions (which I hope don't come only from my frustration and which I hope I'm not the only one to share) about the whole issue:
1) I would put this feature on my top 5 list of mandatory features - laptops&desktops altogether - and I am sure I'm not the only one;
2) I would say that my confguration is pretty common - and I can see only two possibilities here:
  2.1.) Hibernate/suspend was not tested on this configuration
  2.2.) Hibernate/suspend was tested, it didn't work - so what - Heron was released to users.
Either of these two is pretty bad.
3) It seems like a LARGE issue, with big impact. Is there any concentrated effort on this problem? A project dedicated to it? A way to record solutions which work for SOME people and to count the number of cases for which there is still a problem? I saw threads all over the place, solutions  of every kind - can these answer to the above questions?
 The EXACT same thing happened to me with installing the compiz - i was stuck for months, until I found the solution on the blog of "phorlong" (?) - a guy who works on compiz and who happened to be nice enough to share his experience.
 This point boils down to the question - "where is the power of the community?", cause it seems to me slimmer and slimmer.
3) Is there a forum where the users express their needs and their respective priorities? Had someone asked me what I would prefer - a boot time decrease of 3 seconds, a nicer splash screen, some other stuff which I didn't even notice - on one hand, or to keep the suspend/hibernate functionalities working - on the other hand - I wouldn't have hesitated even for a split second - please keep basic things working, and then look for "nice", "good to have" and "waaw" things.
 If I am not the only one in this, then the following question pops up: what's this new release for and about ? It's a LTS - then are we supposed to get all the basic things working by the end of the support period but not before? 
I wouyld happily live with a version for 2 years, then get a new properly tested one with some extra features. It seems to me that the marketing took ahead of software development and that doesn't seem right to me.
 
 I still think that Ubuntu is one of the best distros available and it's the best in the way some features are implemented. But PLEASE - let's keep the basic ones working - even the most beautiful blonde - if she gets a boil on the tip of her nose - you will first see the boil, and then the rest.
 Thanks to all the community, again.

---

### Post by realn on 2008-05-12
I just saw that there is a way of thanking on the posts (except the "thank you"??). Could you please show me how to do this?
THANKS

---

### Post by PmDematagoda on 2008-05-12
Unfortunately the biggest culprit of the suspend and hibernation issues is the kernel itself. Did you try running Fedora 9 to see if the suspend and hibernation issues are fixed in that release(this is because Fedora has a newer kernel that is known to have these issues fixed)?

---

### Post by realn on 2008-05-12
I saw that in many cases the kernel is the problem. I really didn't THINK of trying other distro. Fedora? Does it have synaptic ?? (just joking).
 And if it works, what should I do, go with Fedora? Or would that be just to spot the problem and then go back to Feisty, or smth like this? Cause for me it should be Ubuntu or nothing (well, there's always the M$ thing).
Thank you!

---

### Post by Vorian Grey on 2008-05-12
> **realn said:**
> 
 And if it works, what should I do, go with Fedora? Or would that be just to spot the problem and then go back to Feisty, or smth like this? Cause for me it should be Ubuntu or nothing (well, there's always the M$ thing).
Thank you!
Use what works for you. If it's Ubuntu, fine. If it's Fedora, fine. If it's Windows, fine. Ubuntu is great and I'm loving it but that doesn't stop me from using other releases or even older Ubuntu releases.

---

### Post by realn on 2008-05-12
My dilemma is: what if I like it but it doesn't work. That's my real problem. No, in fact my real problem is that I cannot hibernate my desktop on H.H.
Thank you, Mr. Dorian for the reply, anyway.

---

### Post by eldragon on 2008-05-12
i guess you should just do that ... go back to windows. 

your suspend / hibernate problems wont be fixed anytime soon, and when you get to suspend / hibernate. you will have problems after having done that.

this sounds like a post of someone that was told how well linux is, and how ready it is for the masses. blindfoldedly jumping ship without the thought that there might be quirks in the middle is just foolish. but thats not just for linux, its for every mayor change in your life. or would you marry a woman/man before getting to know her/him?

for example, if i were to jump back to windows, i would check that all the things i can do with no problems here would work in some way. like using a latex compiler. exporting to pdf / eps. having an imap server or a ssh server.

oh, and certainly i cannot think of another way of installing software than with a central repository. that alone is one of the best things linux and ubuntu has. and SHOULD be a selling point.


good luck.

---

### Post by realn on 2008-05-12
Thanks for your reply.
I am not exactly that kind of person - my first touch of Linux dates many years ago, mainly as an user, I have to admit. However, I am the kind of person who is told about improvements from one release to the next but it's not told : "beware, suspend/hibernate might be broken" . It's here that I get lost : I prefer to get a warning, and then any bells and whisles. Please note I am talking about a new release, not Linux vs. anything else, not even one distro vs. another one. Just Ubuntu.
 As for windows, I might spend a day to install a ssh server, I know. 
 As for the central repository - that was and still is the MAIN selling point of Ubuntu, at least for me. 
 I am also aware about the misusage/mismatching of ACPI specifications inside the pieces of hardware.

 Let's make a tutorial about debugging hibernate/suspend, shall we?

---

### Post by realn on 2008-05-12
Sorry, I posted twice.

---

### Post by eldragon on 2008-05-12
> **realn said:**
> Sorry, I posted twice.

no you didnt :D

i wouldnt know how to help with susp / hib. i know it can work or it can fail.

my personal experience with it is it works, but comes back with no sound. and i have to hit ctrl-alt-f7~f9 depending on the virtual terminal the xserver is running on. garbled screen for a sec and off i go.

first thing i would try in order to get suspend and hib to work is, disable any binary blob you might have running.... (wireless, video drivers...or whatever you might have).

another long term action would be to mail your notebook maker requesting linux supported hardware in the future. or to send that complain up in the foodchain to the hardware maker :D

cheers.

---

### Post by realn on 2008-05-13
Hi, thanks for the suggestions. I saw on many posts that any of the following could fix it: replace nvidia with nv; remove the USB drivers (i think it was the USB bridge) before hibernating; remove wireless dirvers before hibernating; flaky BIOS - so mobo BIOS update; pm-utils package "diverting" - whatever that might mean, in order to be sure that it's not used even when using µswsusp; using some kernel booting parameters (nosmp, no_console_suspend, noacpi(?? - if I remember well)); many others.
 I tried almost all of them - no success until now. I guess the quickest solution for me is to go back on Feisty, keep the Hardy installation, too, and test according to my free time. 
 And even now, after getting over the initial frustration (some left, not that much, though), i still don't understand how come that a new release doesn't supoprt old&basic functionalities. I can only come up with some scenarios:
 -this functionality is not such a basic/critical one  - to be implemented in a patch, at some future times - so I will be careful with my needs not matching the average ones;
 - I am an unhappy case, in fact there are more computers overall that can hibernate/suspend in H.H than in Feisty - so I shouldn't complain;
 - the release deadline is to be respected no matter what - so I should wait for some months and then try a new release.

If someone can enlighten me with the underlying reasons, it would help me  better use Ubuntu and its roadmap.

 Thanks a bunch.

---

### Post by realn on 2008-05-16
Problem solved, to my great joy not in favor of M$. 
After mobo BIOS update, hibernate works OK. Didn't try the sleep.

 Thank you all and Ubuntu rocks.

---

