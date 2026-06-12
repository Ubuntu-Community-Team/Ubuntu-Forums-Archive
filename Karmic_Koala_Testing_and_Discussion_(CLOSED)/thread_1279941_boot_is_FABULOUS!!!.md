---
title: "boot is FABULOUS!!!"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by gny on 2009-10-01
Ok, I must confess. I have been eying apple people and their slick boot up. But NO MORE I say. The new boot is SO slick. Who ever did the design has my best congratulations and GO GO GO !!. It just has the right balance between being simple and artsy. Again, WOW, And thank you for making it a pleasure to boot up my laptop. I really hope that you keep the white theme in the sharp release.

---

### Post by dino99 on 2009-10-01
i would like to be happy like you for sure   :lolflag:

---

### Post by Ric_NYC on 2009-10-01
> **gny said:**
> Ok, I must confess. I have been eying apple people and their slick boot up. But NO MORE I say. The new boot is SO slick. Who ever did the design has my best congratulations and GO GO GO !!. It just has the right balance between being simple and artsy. Again, WOW, And thank you for making it a pleasure to boot up my laptop. I really hope that you keep the white theme in the sharp release.

What boot are you talking about?
This is what I have now:
Verbose... xsplash... Login... xsplash...
That takes more than a minute...

---

### Post by gny on 2009-10-01
I have an encrypted drive, so after grub flashes by it stops and prompts for a password. At this point there is a nice white ubuntu logo on the middle of the screen, very slick. After a while xsplash starts with this film noir ubuntu logo in white and grey thing going on, very nicers. That is what i am talking about :)

---

### Post by mmcmonster on 2009-10-01
Strange.

I have a Ubuntu Logo with a light below it going left to right and back again, wish a shadow underneath, like a UFO.

Also, some textual boot after grub, before xsplash takes over.

---

### Post by Mr. Picklesworth on 2009-10-01
Now we just need someone with power to yell at NVidia so that people who like fancy 3D support (and don't want to change their hardware anyway) can get fancy kernel mode-setting. (They are WAY too protective of their code).
As it is, I have a beautiful boot experience on one computer and a *far* less attractive one of the other.

---

### Post by gny on 2009-10-01
> **mmcmonster said:**
> Strange.

I have a Ubuntu Logo with a light below it going left to right and back again, wish a shadow underneath, like a UFO.

Also, some textual boot after grub, before xsplash takes over.

Yea, the light thingy was the one I was talking about. It's white grayish right?

I also have some text before xsplash, but i won't let it ruin my good mode. ;)

Someone living close to nvidia should take them to lunch with and talk some sense in to them. They are getting a little bit better though. Right? right? (I hope they are anyway)

Myself are a happy intel user.

---

### Post by cyberkilla on 2009-10-02
What is the point of xsplash on a 1min 45sec boot, if the damned splash screen appears after 58 seconds?

Okay, it's all dependent on individual hardware, etc, but that is not satisfactory. It should be entirely possible to display a splash screen on any recent computer, *prior* to the operating system loading the big stuff.

usplash was never any trouble.

---

### Post by plun on 2009-10-02
Well.. it looks like crap both with my nVidia-desktop and my 
ATI open source laptop.....

Scott James Remnants blog:

> That being said there are a number of updates planned for karmic that will boost the performance quite a bit, **especially in terms of starting the X Window System server earlier**.

[http://www.netsplit.com/2009/09/02/making-a-splash/](http://www.netsplit.com/2009/09/02/making-a-splash/)

:shock:

---

### Post by gnomeuser on 2009-10-02
brilliant, boot went from about 15-20 secs to over a minute. I get verbosity and only at the very end something pretty to look at right before gdm comes up.

As an experiment I tried booting the Fedora 12 Snapshot 3 release on my machine. smooth fast boot with pretty, as well as on shutdown.... On a machine with an nvidia chip (go nouveau!). I was very impressed to be honest, I didn't expect that.

My gut feeling is still that xsplash will be one of these things that like the safe mode X stuff turned out to be a bad decision and people will hail it as such when it gets removed. Of course I could be horribly wrong.. time will tell. 

The one thing I am disappointed by though is that with so many other distributions going towards plymouth (Mandriva, Foresight and Fedora I know are using it now or have development ongoing to make it happen), it would seem to make sense to join that community. Even if plymouth isn't perfect that would still mean less code to maintain and support, more people to do it. To me that seems like a good thing. I suspect that it would save on development time and if more features or a different design were needed that would mean a community to bring them to fruition instead of whatever manpower Canonical can spare. It would also be a sign that Ubuntu will reach out to the existing community instead of reinventing their code.

---

### Post by MadsRH on 2009-10-02
> **gnomeuser said:**
> brilliant, boot went from about 15-20 secs to over a minute. I get verbosity and only at the very end something pretty to look at right before gdm comes up.

As an experiment I tried booting the Fedora 12 Snapshot 3 release on my machine. smooth fast boot with pretty, as well as on shutdown.... On a machine with an nvidia chip (go nouveau!). I was very impressed to be honest, I didn't expect that.

My gut feeling is still that xsplash will be one of these things that like the safe mode X stuff turned out to be a bad decision and people will hail it as such when it gets removed. Of course I could be horribly wrong.. time will tell. 

The one thing I am disappointed by though is that with so many other distributions going towards plymouth (Mandriva, Foresight and Fedora I know are using it now or have development ongoing to make it happen), it would seem to make sense to join that community. Even if plymouth isn't perfect that would still mean less code to maintain and support, more people to do it. To me that seems like a good thing. I suspect that it would save on development time and if more features or a different design were needed that would mean a community to bring them to fruition instead of whatever manpower Canonical can spare. It would also be a sign that Ubuntu will reach out to the existing community instead of reinventing their code.

As always, **gnomeuser **you are spot on right ;-) Well said.

---

### Post by plun on 2009-10-02
> **gnomeuser said:**
> 
My gut feeling is still that xsplash will be one of these things that like the safe mode X stuff turned out to be a bad decision and people will hail it as such when it gets removed. Of course I could be horribly wrong.. time will tell. 



Well...  according to mailing list messages the X-start move should be rather simple (Mr Remnant messages)

I don't know what went wrong during Karmic development....:confused:

It looks like crap now....:(

---

### Post by ikt on 2009-10-02
> **gnomeuser said:**
> My gut feeling is still that xsplash will be one of these things that like the safe mode X stuff turned out to be a bad decision and people will hail it as such when it gets removed. Of course I could be horribly wrong.. time will tell. 

I don't think we're half way there yet, the idea is to get ubuntu boot in the ~10 second range on an average 2008 production date notebook, the time they want to achieve this milestone is 10.04, 9.10 to me since the major updates have been rolling in has always seemed like a 'lead up' to 10.04, where the software centre, fast boot and other stuff will make a bigger impact on a bigger market for longer and be stable while they update and refine during the prime lifetime of 9.10.

---

### Post by NCLI on 2009-10-02
[SIZE=4]_**The aim of 9.10 is NOT a fast boot**_[/SIZE], but a consistent one. Sure, it's not there yet, but when the last boot-related bugs are fixed, the boot experiences will be ready for 10.04 so they can focus on making the boot faster.

---

### Post by Hairy_Palms on 2009-10-02
>  Originally Posted by gnomeuser  View Post
brilliant, boot went from about 15-20 secs to over a minute. I get verbosity and only at the very end something pretty to look at right before gdm comes up.

As an experiment I tried booting the Fedora 12 Snapshot 3 release on my machine. smooth fast boot with pretty, as well as on shutdown.... On a machine with an nvidia chip (go nouveau!). I was very impressed to be honest, I didn't expect that.

My gut feeling is still that xsplash will be one of these things that like the safe mode X stuff turned out to be a bad decision and people will hail it as such when it gets removed. Of course I could be horribly wrong.. time will tell.

The one thing I am disappointed by though is that with so many other distributions going towards plymouth (Mandriva, Foresight and Fedora I know are using it now or have development ongoing to make it happen), it would seem to make sense to join that community. Even if plymouth isn't perfect that would still mean less code to maintain and support, more people to do it. To me that seems like a good thing. I suspect that it would save on development time and if more features or a different design were needed that would mean a community to bring them to fruition instead of whatever manpower Canonical can spare. It would also be a sign that Ubuntu will reach out to the existing community instead of reinventing their code.

without a doubt, i mean my boots only 27 seconds at the moment, which is slower than jaunty by just under 10 seconds, but xsplash only shows for 2 seconds before GDM pops up, and GDM appears faster without it, and when it does show its blurry and low-res.

---

### Post by fut21 on 2009-10-02
> **gnomeuser said:**
> brilliant, boot went from about 15-20 secs to over a minute. I get verbosity and only at the very end something pretty to look at right before gdm comes up.


I have exactly the same experience---for me it`s not a faboulous boot experience, it`s a boot experience in the wrong direction.

---

### Post by MellonCollie on 2009-10-02
> **NCLI said:**
> [SIZE=4]_**The aim of 9.10 is NOT a fast boot**_[/SIZE], but a consistent one. 


I remember Shuttleworth saying that they were aiming to get 9.10 to boot quicker than 9.04.

---

### Post by gnomeuser on 2009-10-02
> **MellonCollie said:**
> I remember Shuttleworth saying that they were aiming to get 9.10 to boot quicker than 9.04.

At least I don't remember anyone saying let's make it at least twice as slow and remove the bling (till the very last moment when it is completely pointless).

---

### Post by sudoer541 on 2009-10-02
will I be able to see X-splash on a Ati 128Mb ram?

---

### Post by zekopeko on 2009-10-02
> **gnomeuser said:**
> At least I don't remember anyone saying let's make it at least twice as slow and remove the bling (till the very last moment when it is completely pointless).

Aren't you the sensible guy that always encourages bug reporting etc. ?
Or does this not apply to the current situation somehow?

---

### Post by zekopeko on 2009-10-02
> **MadsRH said:**
> As always, **gnomeuser **you are spot on right ;-) Well said.

As an artist: do you prefer to create simple png images or code in C-like syntax language to create themes for the boot?

---

### Post by cyberkilla on 2009-10-03
> **zekopeko said:**
> Aren't you the sensible guy that always encourages bug reporting etc. ?
Or does this not apply to the current situation somehow?

Because it seems futile and fundamentally flawed to take a major, latter component of the boot process and launch the "loading splash" inside of it. There are only so many things you can load after X. It looks like a massive beast with many dependencies.

XSplash has more in common with the loading screen *after* you log in on Windows Vista. The one that tells you to wait while it loads your desktop.

Vista still has a simpler splash that appears much earlier on in the boot process.

It would be great to be proven wrong about this, but I don't think the odds are particularly high. I still get console output until a few seconds after fsck, which cannot (from what I've read) be deferred until after X has loaded.

---

### Post by dinxter on 2009-10-03
It might seem strange but X actually has fewer boot dependencies than you may think. Therefore a lot of services can be started after X. Whereas there are a significant number of services that require X before they can start, the argument then goes, if you can start X quickly then you can boot quicker, as is the aim, xsplash isnt the driving force for the move to prioritise X. 
Unfortunately, as a consequence of an early X server you get into trouble when you have something like usplash or plymouth trying to use the framebuffer at the same time, also, you now have X available so why not use it. 
I dont have strong feelings on usplash/plymouth either way to be honest but I think its important to remember that fast booting is the overall goal for upstarting and re-prioritising init, not any reason relating to boot splashes.
Parallelising init is surely a good thing, but it isnt trivial and thats why the target date for this is karmic+1, hopefully by that time  problems seeing the benefits of faster boot times, or even seeing increases, should be removed. And xsplash should pop up within a second or two of boot start, if your desktop hasnt arrived by then! well... maybe not that quickly :)

---

### Post by Copernicus1234 on 2009-10-03
I agree. The new boot up is something to be proud of now in my opinion. Creds to everyone involved. Good job. :)

Ive viewed some alternate boot suggestions though, and some of them I like. For example:

[Particle effect 1]("http://www.youtube.com/watch?v=XlCVrtgxVcI&hl=en&fs=1&hd=1")

[Particle effect 2]("http://www.youtube.com/watch?v=Oh6-uhGvBIY") 

Perhaps for the future. In the new beta the system boots so incredibly fast that the particle effects would have a hard time even showing before the desktop comes up. :)

---

### Post by dinxter on 2009-10-03
With X running, fancier splashes are possible, the one at the moment is quite simple, dont run before you can walk I suppose :) There was also a plan for a boot chooser running in X during boot, dont ask me how that would work, though I am curious. It'll be interesting to see what people come up with once the boot reorganisation has settled down for a while

---

### Post by MadsRH on 2009-10-03
> **Copernicus1234 said:**
> I agree. The new boot up is something to be proud of now in my opinion. Creds to everyone involved. Good job. :)

Ive viewed some alternate boot suggestions though, and some of them I like. For example:

[Particle effect 1]("http://www.youtube.com/watch?v=XlCVrtgxVcI&hl=en&fs=1&hd=1")

[Particle effect 2]("http://www.youtube.com/watch?v=Oh6-uhGvBIY") 

Perhaps for the future. In the new beta the system boots so incredibly fast that the particle effects would have a hard time even showing before the desktop comes up. :)

Actually, the [Particle effect 1]("http://www.youtube.com/watch?v=XlCVrtgxVcI&hl=en&fs=1&hd=1") has been suggested for [Xubuntu ]("https://wiki.ubuntu.com/Xubuntu/Artwork/Karmic#boot"):-D

[[IMG]https://wiki.ubuntu.com/Xubuntu/Artwork/Karmic?action=AttachFile&do=get&target=karmic-sparkles-01_tn.png[/IMG]]("https://wiki.ubuntu.com/Xubuntu/Artwork/Karmic?action=AttachFile&amp;do=get&amp;target=karmic-sparkles-01.ogv")

> **zekopeko said:**
> As an artist: do you prefer to create simple png images or code in C-like syntax language to create themes for the boot?
I'm no good with code, so I was very happy to see that X-splash uses simple .PNG images.

---

### Post by dinxter on 2009-10-03
i have to admit, i do like these particle type themes, i'm such a child :)

---

### Post by exploder on 2009-10-03
The particle effect looks impressive! Maybe Ubuntu will use this in the LTS release.

---

### Post by laborg on 2009-10-03
I DON'T agree! The boot is, as statet by gnomeuser previously, slow and visually not appealing (except for the short time of xsplash/gdm/xsplash. I can't judge the technical descisions on this development, but compared to other distros the enduser has an ugly "text" experience from grub and the following seconds (the same holds true for restarting = blinking cursor + restarting message). 
My questions is: Will there be improvement during the beta-phase or is the current setup the one to expect in the final version?

---

### Post by exploder on 2009-10-03
As I understand it, the decision to use xsplash was to ensure hardware compatibility. Look at all the problems there were with usplash, lots of people had the black screen at start up issue. Xsplash is a sound solution in my opinion because it looks decent and is customisable. This is the first time xsplash has been used as far as I know, give it some time and refinements will probably come.

---

### Post by dinxter on 2009-10-03
All i can say is, the boot being slow, xsplash not starting quickly enough, seeing any text on boot, and not seeing the closing boot splash fade to shutdown are all bugs and obviously not what is being aimed for. there are 4 more weeks or so to go so hopefully these will be ironed out. 

what its supposed to look like is...
1. blank screen (no text) while start X within a few seconds 
2. fade out xsplash to gdm login (or desktop) as soon as its ready
3. xsplash on close, fade to shutdown.

If starting X takes too long, or to handle fsck and other interruptions, usplash should be used

The process described is certainly possible, but reorganising and parallelising init isnt a straightforward job and bugs as we all know are inescapable :) And just to emphasise, slow booting, text, blinking cursors and so on are bugs to be fixed, not how its all supposed to work!

---

### Post by gnomeuser on 2009-10-06
> **zekopeko said:**
> Aren't you the sensible guy that always encourages bug reporting etc. ?
Or does this not apply to the current situation somehow?

[That was before I realized that Ubuntu does doesn't give a flying **** even if you hand them welltested patches and beg them to apply them](http://davidnielsen.wordpress.com/2009/09/28/when-ubuntu-hates-upstream/). I have vowed to stop asking people to engage in the obvious waste of time that is reporting bugs to **Ubuntu**.

Really people, they don't care.. not the slightest. Bugreports for Ubuntu are an obvious, empirically proven, waste of your time, effort and brain matter. Attempts to engage in such behavior will in all likelihoood lead to such symptoms as feelings of disgust with the human race, disappointment and thoughts of self-mutatilation.

You should though not stop reporting bugs upstream, upstream loves you and will hug you for telling them they aren't perfect. In the event that Ubuntu is upstream, rule 1 applies, don't bother.

---

### Post by MacUntu on 2009-10-06
lol

---

### Post by TrueTom on 2009-10-06
I'm with gnomeuser on this one. Filing bugs with Launchpad is a complete waste of time for most problems. Please file them in the respective upstream bugtrackers.

---

### Post by go7Ul1ai on 2009-10-06
> **macuntu said:**
> lol

+1

---

### Post by exploder on 2009-10-06
> That was before I realized that Ubuntu does doesn't give a flying **** even if you hand them welltested patches and beg them to apply them. I have vowed to stop asking people to engage in the obvious waste of time that is reporting bugs to Ubuntu.

Really people, they don't care.. not the slightest. Bugreports for Ubuntu are an obvious, empirically proven, waste of your time, effort and brain matter. Attempts to engage in such behavior will in all likelihoood lead to such symptoms as feelings of disgust with the human race, disappointment and thoughts of self-mutatilation.

You should though not stop reporting bugs upstre


gnomeuser, I wish I could disagree with what you wrote but you are right. Reporting bugs in Ubuntu does seem to be a waste of time. My concerns are that the final release is approaching and Karmic still has issues with Intel graphics, no other major distribution has this issue in their development releases. Fixes are never issued for serious issues like this and you have to wait and hope that things are resolved in the next release. 

I had high hopes for Karmic but they are sinking fast... This will most likely be the second release in a row that will not run on my machine. I like the new artwork and was optimistic about the new boot experience but with the Intel bug the boot experience is messed up at random and I loose desktop effects when the problem occurs. Needless to say the boot experience is not very good for me.

Instead of trying to get other projects to sync their development cycles, Ubuntu needs to re-examine it's quality practices and quality control. Lets face it, for being this close to a final release Karmic should not be as bug ridden as it is. If the problem is lack of manpower as is always suggested, than a more conservative approach to development would be in order, possibly an 8 month release cycle like OpenSuse is doing.

Smaller distributions with far less developers are managing to put out quality releases so it has to be Ubuntu's development practices that are the problem. Why add technology that is not fully developed? If the current state of Karmic is any indication of the quality of the final release the release then a more conservative approach needs to be taken.

---

### Post by MacUntu on 2009-10-06
Could you guys start a new thread? This is highly off-topic...

---

### Post by exploder on 2009-10-06
> Could you guys start a new thread? This is highly off-topic...

We did wander a bit but we are saying that the boot experience is not so fabulous for us.:)

---

### Post by 4partee on 2009-10-06
> **exploder said:**
> We did wander a bit but we are saying that the boot experience is not so fabulous for us.:)

What boot experience?  I can't even get beta to boot to splash on two of my systems!  And yes, I posted to Launchpad yesterday.

<offtopic>
The .31 kernel is broken and Torvalds has NO plans to fix .31!

LTS = Production
x.04 = Beta
x.10 = Alpha

John

---

### Post by Ric_NYC on 2009-10-06
Is there anything like common sense in the Linux world?

The boot is slower now than it was in jaunty.
Now we have this ugly dark login screen.

In my opinion this new boot is not fabulous at all.

---

### Post by ljrmorgan on 2009-10-06
I have to say the new gdm looks horrible, it looked far better in the alpha. I also have heaps of stuff going on (lots of text) before xsplash kicks in.

---

### Post by Fzang on 2009-10-06
My xplash was pretty smooth on the live CD. One thing, however, that turned me off was the massive amount of color banding on the loading startup screen. It looks like it's displayed in 256 colors. Drivers for my GPU didn't come preinstalled (proprietary), could that be the cause, or does it look that horrible at all times?

---

### Post by archiesteel on 2009-10-06
> **Ric_NYC said:**
> Is there anything like common sense in the Linux world?

That seemed unnecessarily inflammatory, don't you think?

---

### Post by Longinus00 on 2009-10-06
> **Fzang said:**
> My xplash was pretty smooth on the live CD. One thing, however, that turned me off was the massive amount of color banding on the loading startup screen. It looks like it's displayed in 256 colors. Drivers for my GPU didn't come preinstalled (proprietary), could that be the cause, or does it look that horrible at all times?

A fix for the extreme color banding in 16bit color is in the trunk already. I don't know when it's getting pushed out but it'll definitely happen before release.

---

