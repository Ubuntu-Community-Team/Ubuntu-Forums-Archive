---
title: "random logouts??"
date: 2010-02-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by setherd on 2010-02-06
Does anyone else have this problem?
I randomly will be logged out maybe once or twice a day. at first I thought it was related to a problem with the mouse jumping to a corner, I thought maybe my mouse was jumping to the upper right corner and I was clicking on logout by accident.

but now it's happened as I was typing something, so I think it wasn't my mouse.
anyways it just logs me out. that's it. Very annoying.

once I log back in and run the command "users" I see myself listed twice.

So anyone else?????
I don't even have anything to file a bug report on except the affect.

---

### Post by robertbub on 2010-02-20
I randomly get logged out.

It was fine before I did "aptitude safe-upgrade" this morning.

I guess that was my mistake.

I have all sorts of problems now, including[LIST]
[*]blanking the screen doesn't unblank (i.e., it's left black)
[*]my password no longer breaks the lock screen (after either "lock screen" or via screensaver)
[/LIST]

---

### Post by Jordanwb on 2010-02-20
I had that problem. My keyboard was malfunctioning.

---

### Post by robertbub on 2010-02-20
> **Jordanwb said:**
> I had that problem. My keyboard was malfunctioning.I'm starting to think that this problem is the infamous plymouth (the Ubuntu splash package thingy) and the "Return" key problem.  I noticed that the forced logout only happens after I hit return.

I uninstalled plymouth.  We'll see if that helps.

---

### Post by FrancoNero on 2010-02-20
noticed this two weeks ago as well, is the problem still there? was planning to test the next alpha....again. i usually try a few milestones here and there to get psyched for the time i'll switch to the final release (which i usually do before final status, haha)

---

### Post by setherd on 2010-02-20
> **robertbub said:**
> I'm starting to think that this problem is the infamous plymouth (the Ubuntu splash package thingy) and the "Return" key problem.  I noticed that the forced logout only happens after I hit return.

I uninstalled plymouth.  We'll see if that helps.


when it happens for me it's instant. no hitting return needed:(

---

### Post by wilee-nilee on 2010-02-20
Mine is at the key prompt after the auto login whether ethernet or wifi. If I turn off the autologin it doesn't happen.

---

### Post by maheshasolkar on 2010-02-20
May be it is the Xserver crashing. You could look in /var/log/Xorg.0.log to see if there is any clue about the crash.

---

### Post by aviramof on 2010-02-21
i have eventually installed an old version one with 32-12 kernel and updated it because newer version installer is not working so well last installer even asked for a paswword 
even before i'v reached the page where you enter the user name and password for the first time and i'm talking about the live cd ha ha ha.

but now i have a strange problem every now and then the user simply log off or i get a black screen for no apperent reason what can i do about it?

thanks in advance.

---

### Post by LKjell on 2010-02-21
> **aviramof said:**
> i have eventually installed an old version one with 32-12 kernel and updated it because newer version installer is not working so well last installer even asked for a paswword 
even before i'v reached the page where you enter the user name and password for the first time and i'm talking about the live cd ha ha ha.

but now i have a strange problem every now and then the user simply log off or i get a black screen for no apperent reason what can i do about it?

thanks in advance.

Sounds like plymouth/ video driver problems. What video card you have?

---

### Post by aviramof on 2010-02-21
Ati hd 3650 ddr2 512mb shappire agp.

a rather uniq card but there is nothing i can do about it it was the strongest agp card i'v found at a reasonable price and i don't have problems 
with it in windows 7 or windows server 2008 and i didn't have this problem before with ubuntu,

and by the way how can i remove old kernels from grub 2 i now have 32-12 32-13 32-14.

thanks in advance.

---

### Post by 23meg on 2010-02-21
Threads on the same issue merged. aviramof, please don't start new threads without checking the recent threads, and doing a search (click "Search this Forum" on the upper right).

---

### Post by aviramof on 2010-02-21
ok but still does any body know how can i get rid of old kernels the safe way?

i know i can edit grub.cfg but i was wandering if there is a better way to do that.

---

### Post by LKjell on 2010-02-21
> **aviramof said:**
> ok but still does any body know how can i get rid of old kernels the safe way?

i know i can edit grub.cfg but i was wandering if there is a better way to do that.

hmm you can try to remove them in synaptic. Do apt-get remove linux-image-2.6.32-12-generic

---

### Post by aviramof on 2010-02-21
thanks i'll give it a try.

---

### Post by aviramof on 2010-02-22
i still have the random logouts problem despite the fact that i have downloaded all updates up to this moment what is done about this problem?

thanks in advance.

---

### Post by zika on 2010-02-22
This morning, out of the blue, I just wanted to see if plymouth is fixed. I installed it and random logouts started... The reason I've purged it were random freezes (with KMS) and crashes (when entered "Enter")... As soon as it was purged again, problems were gone... So, purge plymouth...

---

### Post by setherd on 2010-02-22
> **zika said:**
> This morning, out of the blue, I just wanted to see if plymouth is fixed. I installed it and random logouts started... The reason I've purged it were random freezes (with KMS) and crashes (when entered "Enter")... As soon as it was purged again, problems were gone... So, purge plymouth...

Funny thing is I had the thought a few hours ago that maybe this all a plymouth problem.
so I purged it.
Hopefully that was the problem. If I have logouts again I'll be sure to post it.

---

### Post by aviramof on 2010-02-22
i'v removed plymoth from synaptic is that enaf or there are dependencies i need to remove too?

---

### Post by Didius Falco on 2010-02-22
> **aviramof said:**
> i'v removed plymoth from synaptic is that enaf or there are dependencies i need to remove too?

Just removing plymouth is enough.

---

### Post by mediamind on 2010-02-23
I have login set to auto and was experiencing this issue as well. Hitting the Enter/Return key would log me out of my session. Once I had logged back in, the problem did not reappear until the next reboot.

I've since removed Plymouth (via Synaptic) and this appears to have resolved the issue.

---

### Post by louieb on 2010-02-23
When I run the** finger **command it shows that my X session is running on **tty1** instead of the expected **tty7**  

I'll get the random logout every now and then - when I get logged back and run the finger command again the X session is now running as expected on **tty7.** Just wonder if this is related to Plymouth too.

---

### Post by VMC on 2010-02-23
> **louieb said:**
> When I run the** finger **command it shows that my X session is running on **tty1** instead of the expected **tty7**  

I'll get the random logout every now and then - when I get logged back and run the finger command again the X session is now running as expected on **tty7.** Just wonder if this is related to Plymouth too.

Yes it is. plymouth and gdm fight over who gets what vtty first.

Read this [_bug_]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/518352/comments/12") explanation.

---

### Post by louieb on 2010-02-27
> **VMC said:**
> Read this [_bug_]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/518352/comments/12") explanation.

That looks like it. - I do have quite splash removed from the kernel line too.

I have noticed I do not get the unexpected logout if after a fresh boot I logout and log right back in. 

Thanks, lou.

---

### Post by aviramof on 2010-02-27
just to let you know i have no problems with plymouth with 2.6.33 kernel and i think it's ridicilus to stick to an old kernel one who doesn't even have good dvi hdmi support and 
caused me problem with plymouth and my lcd tv and who know what eles.

---

### Post by dxxvi on 2010-02-28
I got the same problem (I'm using lucid alpha3 dist-upgraded on Feb 28). Just removed plymouth. Let's see if it happens again.

---

### Post by cimh on 2010-02-28
Ah joy. It's great to see I am not alone. I've been having this problem with lucid for a few weeks but only when typing in chrome or open-office. I have autologin on

I am sure I removed Plymouth long ago - if so it hasnt solved the problem - but I'll check on this.

Oh yes - I still had plymouth installed - I've binned it now - hopefully that's sorted


cimh 
eee901

---

### Post by kainos on 2010-02-28
Removing Plymouth fixed it for me.

---

### Post by autumnraine on 2010-02-28
> **aviramof said:**
> just to let you know i have no problems with plymouth with 2.6.33 kernel and i think it's ridicilus to stick to an old kernel one who doesn't even have good dvi hdmi support and 
caused me problem with plymouth and my lcd tv and who know what eles.

Hi, I was wondering what you meant about 2.6.32 having poor dvi/hdmi support. I haven't read anything about this, but am having trouble getting sound over hdmi and wondered if that might be relevant (it's probably not, but just wanted to ask...).

---

### Post by Uncle Spellbinder on 2010-02-28
> **kainos said:**
> Removing Plymouth fixed it for me.

I'm getting this issue of random logouts as well. Quite annoying, actually.

But I'm not going to remove anything as this is a testing build. I add apps and such but leave everything default alone so as to test when/if updates come along. If plymouth receives an update that fixes the issue, how would I know if it's not even installed.

Just my 2 cents.

---

### Post by aviramof on 2010-02-28
> **autumnraine said:**
> Hi, I was wondering what you meant about 2.6.32 having poor dvi/hdmi support. I haven't read anything about this, but am having trouble getting sound over hdmi and wondered if that might be relevant (it's probably not, but just wanted to ask...).

i don't know if it's a general problem but for me connecting my tv to the computer via 
dvi hdmi resulted in pink and solorize or green colors on the screen i even uploaded an 
image to launchpad here it is:

[http://img12.imageshack.us/img12/9083/2502101006.jpg](http://img12.imageshack.us/img12/9083/2502101006.jpg)

latest kernel don't have this problem period.

---

### Post by emarkay on 2010-03-01
I have removed Plymouth (no K-Cars for me here!) and I still am getting booted to login - and I do not have any autologin enabled, also.  Random times I get this. Seems to be when I am entering a password - and no, there's no "2" in my password (this was kicking someone else out on another thread).  Will see what more ideas there are - no point in filing a bug when I can't specifically reproduce it.

---

