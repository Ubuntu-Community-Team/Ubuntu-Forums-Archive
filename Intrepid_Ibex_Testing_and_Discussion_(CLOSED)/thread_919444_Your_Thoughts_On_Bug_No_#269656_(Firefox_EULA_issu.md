---
title: "Your Thoughts On Bug No #269656 (Firefox EULA issue)"
date: 2008-09-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-09-14
Here it is:

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/269656](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/269656)

Lets hear your opinion, Ive said mine.

---

### Post by inportb on 2008-09-14
Yeah, I agree that it was pretty confusing to see an EULA pop up out of the blue. What I do not understand is why we have to hang onto the Firefox name and artwork, if the browser itself is the same for all intents and purposes. Canonical, by packaging a product called "Mozilla Firefox," is extending the popularity of Firefox, so Mozilla should be bending to Canonical's wishes.

---

### Post by autocrosser on 2008-09-14
I agree with several of the people responding in the report that the EULA should be "cleaned up" quite a bit--as it was--it looked like some nit can't refrain from shouting like a 10 year old....I respect Firefox & the Mozilla group, but I think they could be a bit more caring about the people that have made the browser as popular as it is........

---

### Post by Merk42 on 2008-09-14
To me it seems like much ado about nothing.  I would like to see what said EULA looks like.

---

### Post by wgrant on 2008-09-14
If you're running Firefox 3.0.2 on Intrepid, try going to [chrome://ubufox/content/mozeula.html](chrome://ubufox/content/mozeula.html).

---

### Post by nanog on 2008-09-14
I have to say that I find the concept of a EULA for an open source browser to be offensive. As far as I am concerned chrome for linux cannot come soon enough (it runs fine in wine, BTW).

---

### Post by loell on 2008-09-14
I say let's swallow this for now, a one time EULA prompt isn't much.
surely we will get consensus from other users in the coming months.

if many users won't mind it, then fine. ;) 
if it gets frowned upon, then i guess we'll consider Icedove. :)

---

### Post by nanog on 2008-09-14
Here is the text of the EULA:

[http://www.mozilla.com/en-US/legal/eula/firefox-en.html](http://www.mozilla.com/en-US/legal/eula/firefox-en.html)

I am *not* happy with mozilla.

---

### Post by exploder on 2008-09-14
I have seen this in OpenSuse and Fedora. It is no big deal and it is a one time thing. Given all of the issues remaining in Intrepid this is of no concern to me. This is a very minor inconvenience.

---

### Post by Game_boy on 2008-09-14
In addition to replacing or anonymising it, I think we have two options that people haven't yet considered.

1. Remove Ubuntu-specific changes to Firefox.

Mozilla allows the distribution of trademark-using builds, as long as they are vanilla. Are there actually any important changes we made that justify giving up the trademark? A few security patches from Debian, and the interface changes. Most of the patches are addressed in the next Firefox point release soon afterwards, and the interface changes like the plugin manager could be redone without affecting FF source code - like a preinstalled FF plugin.

2. Get Mozilla to approve the Ubuntu changes

If we can't give up some changes, perhaps we could ask Mozilla to accept them, either by granting one-time exemptions or incorporating our changes into the Linux vanilla Firefox build.

---

### Post by exploder on 2008-09-14
No offense but there are bigger concerns with Intrepid than this. This is a one time thing, why is it an issue?

The usplash not working at shut down or restart, system sounds not working, compiz turning itself back on, the progress bar on usplash going back and forth on start up, etc, seem much more important to me.

Just my two cents on this.

---

### Post by Game_boy on 2008-09-14
> **exploder said:**
> No offense but there are bigger concerns with Intrepid than this. This is a one time thing, why is it an issue?

The usplash not working at shut down or restart, system sounds not working, compiz turning itself back on, the progress bar on usplash going back and forth on start up, etc, seem much more important to me.

Just my two cents on this.

Absolutely. Bugs are the priority. I'm just saying it would be easy just to go back to a vanilla build with fewer integration issues (less custom code) and also solve this minor, but flashpoint-like (people will write angry blogs and articles a lot, even if it has no effect) issue.

---

### Post by exploder on 2008-09-14
Fedora and OpenSuse already have the EULA and there has not been any mention of it. I understand what you are saying though.

---

### Post by xebian on 2008-09-14
The solution is easy.  Iceweasel.

---

### Post by exploder on 2008-09-14
xebian, I agree with your solution. This would be simple and quick but how would this affect Ubuntu's relationship with Mozilla?

---

### Post by eragon100 on 2008-09-14
Who cares, as long as it stays free? I think development should concentrate on fixin the 5 trillion bugs that are still in intrepid (and which I don't think will all get fixed before shipping as it is, without stupid "problems" like this to whine about)

And does iceweasel have all of ff e's new features, such as the handy new URL box (and I mean by default, not with plugins!) ? I am not going to run an outdated crippled product because of some stupid trademark issue.

In other words: if ubuntu removes too many parts because of them being "non-free" or Whatever, I could always go and use opensuse, which I think will never become a GPL zealot distro (otherwise they wouldn't make a deal with microsoft). Freespire would also be a good choice in that case, one of it's main marketing points is actually that it ships with all non-free software you can think of. Sabayon also falls into this category. So, I recommend ubuntu not to go whine to much about GPL-related issues, if they don't want to lose their market share, and if they want to continue to attract windows users.

---

### Post by Rocket2DMn on 2008-09-14
Threads merged and title adjusted.

---

### Post by exploder on 2008-09-14
eragon100, I feel the same way about this, there are much more important issues to attend to.

---

### Post by eragon100 on 2008-09-14
> **exploder said:**
> eragon100, I feel the same way about this, there are much more important issues to attend to.

I have expanded my comment a bit :wink: It's now more... general

---

### Post by _oOMOo_ on 2008-09-14
> **eragon100 said:**
> Who cares, as long as it stays free? I think development should concentrate on fixin the 5 trillion bugs that are still in intrepid (and which I don't think will all get fixed before shipping as it is, without stupid "problems" like this to whine about)

I'm not sure why you think development on Intrepid has come to a halt simply because of a discussion about this EULA.

Incidentally I've been using Intrepid for a while now and I've only noticed a trillion bugs.

If ubufox is the only reason for the EULA then why not allow end-users to install it as a simple add-on on first boot?

---

### Post by fluteflute on 2008-09-14
Ubufox (and any other Ubuntu changes) are not the reason for the EULA. Mozilla has requested that Firefox should display the EULA (we previously bypassed it by not using the installer) regardless of other modifications.

---

### Post by Nullack on 2008-09-14
> **_oOMOo_ said:**
> Incidentally I've been using Intrepid for a while now and I've only noticed a trillion bugs.

If you havent already, please consider contributing to Intrepid. There's some details in the link at my sig. :)

---

### Post by xebian on 2008-09-14
> **exploder said:**
> xebian, I agree with your solution. This would be simple and quick but how would this affect Ubuntu's relationship with Mozilla?
I don't know of a relationship, but if there is, Firefox should be the one grateful because Ubuntu is giving them a lot of users.

I think Ubuntu should use Iceweasel, and the resources used to maintain an Ubuntu Firefox should be used on chrome instead.  IMHO.

---

### Post by xebian on 2008-09-14
> **eragon100 said:**
> 

And does iceweasel have all of ff e's new features, such as the handy new URL box (and I mean by default, not with plugins!) ? I am not going to run an outdated crippled product because of some stupid trademark issue.


Iceweasel is as advanced, updated  and secure as anything you get from Mozilla, or long before Ubuntu updates.

---

### Post by MALEADt on 2008-09-14
I have problems with this EULA too. In fact I use a Linux OS for two main reasons:
1) it's flexible and easily user-adjustable;
2) I know there is no hassle with user agreements, and I won't ever have to worry how I use / what I use a certain application for.

Asking users to accept a EULA compromises this second motivation.


Next to this, as somebody said on the Launchpad entry, this EULA isn't really a big problems for users, but it might be for companies. As companies need to protect their stuff, they won't risk accepting a EULA without having it looked at by a lawyer. This makes using Ubuntu less interesting to use...

So if it was to me, I'd switch to an unbranded but equally functional browser, and call it something like "Ubuntu web browser" :)

---

### Post by xebian on 2008-09-14
> **fluteflute said:**
> Ubufox (and any other Ubuntu changes) are not the reason for the EULA. Mozilla has requested that Firefox should display the EULA (we previously bypassed it by not using the installer) regardless of other modifications.

Lately, Firefox has been inserting so much silly warnings like '.. this might void your warranty..'.  I didn't know there's a warranty.

---

### Post by _oOMOo_ on 2008-09-14
> **Nullack said:**
> If you havent already, please consider contributing to Intrepid. There's some details in the link at my sig. :)

Thanks Nullack I was just trying unsuccessfully to be funny :) I do contribute in so far as I can with bug reporting etc. As it happens there are only a couple of bugs in Intrepid that are of any real significance to my particular setup, not forgetting Bug no.1 of course.

I've just installed abrowser and abrowser-3.1, if this is simply about a logo and a name I'll cheerfully go without thanks.

---

### Post by Robertjm on 2008-09-14
I was actually trying to figure out where the Accept button was located. Most EULA I have seen have Accept/Cancel buttons for acceptance and refusal of the EULA, but not this one.

---

### Post by jc87 on 2008-09-14
Personally i don't see the point in using an EULA:

A) Ubuntu already complies with the EULA according to the Mozilla branding guidelines due to the understanding between Mark and the Mozilla corporation (as far as i´m aware).

B) There is no point in forcing the average user to read it if the average user isn´t going to do anything that would violate it (in this case ship modified versions of Firefox with the Mozilla branding).

C) The EULA is non user-friendly, because it violates the principle of "just works"

D) Most users don't read EULA´s anyway.

F) Ubuntu can always change to [iceweasel]("http://en.wikipedia.org/wiki/Iceweasel") (Firefox without Mozilla restrictions on trademarks and artwork), and if that would happen Mozilla would loose revenue from Google from the Ubuntu Firefox users (remember Google pays Mozilla for each user who visits the site using Firefox).

---

### Post by exploder on 2008-09-14
Three pages already dedicated to something trivial. Too bad we can not get the same kind of responses to more critical issues.

---

### Post by phenest on 2008-09-14
I don't think this is an agreement you have to accept or decline, because Canonical have accepted it for you.

I haven't got a problem with this EULA at all. Mozilla are quite entitled to include an EULA as are all software vendors. It's not like it restricts its use. It's still free and open source.

---

### Post by Mr. Picklesworth on 2008-09-14
Exploder, this **IS** a critical issue. This is the default web browser popping up a user-hostile message after Ubuntu is installed or upgraded. If the user (think of simple users, too) does not accept the EULA he is left without a web browser. Keep in mind that we cannot make assumptions about the user. Ubuntu claims to be ready to use out of the box, without annoyances or restrictions. This EULA popup strikes down all of those claims; I do not consider an unchecked EULA to be ready to use software. Saying it is would be basically telling the user that the EULA means nothing and he should ignore it.
As is, this is a show-stopper.

It could be remedied by putting the EULA in Ubiquity, but that gives us a new problem that users could get around it by upgrading from older releases or using the alternative install CD. It also does not stop the thing from looking / reading in a completely unfriendly way.

---

### Post by exploder on 2008-09-14
phenest, has summed things up well. This thread is just a waste of forum space. Mozilla has every right to require an EULA and it is certainly not a show stopper. 

Flash had an EULA and it did not stop anyone from using it, same thing for Firefox.

---

### Post by BwackNinja on 2008-09-14
here's my view of what the EULA says, which IMHO is mostly _nothing_

1. You can use this, and modifications to this license will apply if you upgrade to a product with that license

aka, common sense

2. Mozilla can say you can't use it, and thus you can't

3. Firefox is theirs

aka, duh, and we see it in the titlebar always

4. No warranty, implied or expressed

aka, in gpl _anyway_

5. anything bad that happens isn't their fault

aka, a repitition of 4

6. You can't ship firefox places where you're not allowed to ship it

aka, don't break the law, common sense

7. This part actually makes sense... but it doesn't apply to anyone outside the US Government

8.
a. this is the agreement, all of it
b. laws of California?????
c. Not restricted by United Nations International Sale of Goods...which I'm sure most people don't know about and this basically says you don't have to care in this case
d. parts of the license that aren't right or can't be enforced will be changed to still do what they were meant to do
e. if you get extra rights from mozilla for use of this software, it doesn't mean you get them always
f. controlling language of this agreement is English (is that bad for internationalization?)
g. You can give your rights to this software to anyone as long as they agree to the same agreement
h. this is a binding agreement

---

### Post by fiddler616 on 2008-09-14
> Subject to the foregoing, Mozilla, for itself and on behalf of its licensors, hereby reserves all intellectual property rights in the Product, except for the rights expressly granted in this Agreement. You may not remove or alter any trademark, logo, copyright or other proprietary notice in or on the Product. This license does not grant you any right to use the trademarks, service marks or logos of Mozilla or its licensors. 
Suddenly, I'm not a fan.
Edit: I read (OK, skimmed) through the rest of the thing, and there is no granting of rights, just taking away of them.

---

### Post by phenest on 2008-09-14
> **exploder said:**
> phenest, has summed things up well. This thread is just a waste of forum space. Mozilla has every right to require an EULA and it is certainly not a show stopper. 

Flash had an EULA and it did not stop anyone from using it, same thing for Firefox.

Blimey! It's not very often I say something right.

In that bug report, Mark Shuttleworth says:
> To act as though your rights are being infringed misses the point of free software by a mile.
This is important. Try to remember what free software is, and stop going on about your rights. After all, if you don't like the EULA, then don't use Firefox.

---

### Post by fiddler616 on 2008-09-14
I don't think it's about remembering what free software is, it's about making sure the free software is free software.

---

### Post by nanog on 2008-09-14
Exploder,
Although you seem content with adobe's non-free proprietary mess many who use linux feel very strongly about software freedoms. This agreement clearly gives mozilla the right to inject proprietary code in its "free" binary browser. I now realize that debian was right to switch to iceweasel.
IMO, firefox should be booted from main and an unbranded browser should be used. I also heartily support the idea of using chrome as soon as its released for linux.

---

### Post by exploder on 2008-09-14
Doesn't the agreement make sense? What would stop Microsoft from slapping on their logo and calling it IE 9?

---

### Post by fiddler616 on 2008-09-14
I think Iceweasel (or if an Ubuntu spin gets put on it, Firebex (Ibex)) should be the default, and Firefox should be an option, not the other way around.

---

### Post by phenest on 2008-09-14
> **exploder said:**
> Doesn't the agreement make sense? What would stop Microsoft from slapping on their logo and calling it IE 9?

Exactly. This is about Mozilla trying to preserve their trademarks, i.e. the logo and the name.

I do believe Ubuntu is the same.

---

### Post by exploder on 2008-09-14
Totally free is Debian. Only mp3s work, "out of the box". Totally free does not support, youtube. apple movie trailers, real audio and video, and the list goes on.

---

### Post by fiddler616 on 2008-09-14
It's not that I have an issue with Mozilla wanting Mozilla Firefox to be Mozilla's, it's that I have an issue with developer/programmer-types not being able to do what they want with Firefox in the same way they can do what they want with speech. Mozilla should license it under a sharealike license or something.
(PS: If Microsoft did that for IE9, it'd be worth the legal problems just for the solid ten minutes of laughing I'd have :) )

---

### Post by Mr. Picklesworth on 2008-09-14
I, for one, don't mind the freedom end of this at the moment. (I have always been aware that Mozilla has troublingly non-free artwork and that their one-size-fits-all design means downstream distros must make local changes... which conflicts with their branding, thus producing a giant mess).
Mark makes a fine point that the browser is not infringing on your rights at all, and anyone that says it is really needs to brush up on what "rights" are.

The problem I see is simple: This is default. In other words, we expect users to read that huge thing and say "I agree" as part of their end user post-install experience. If they do not, the default Ubuntu desktop becomes hostile for them. That is not cool.

---

### Post by fiddler616 on 2008-09-14
Slowly but surely, I'm getting converted into the "Ultimately, does it *matter?*" line of thought.

---

### Post by Merk42 on 2008-09-14
> **nanog said:**
> Exploder,
Although you seem content with adobe's non-free proprietary mess many who use linux feel very strongly about software freedoms. This agreement clearly gives mozilla the right to inject proprietary code in its "free" binary browser. I now realize that debian was right to switch to iceweasel.
IMO, firefox should be booted from main and an unbranded browser should be used. I also heartily support the idea of using chrome as soon as its released for linux.

[Google Chrome has a EULA too](http://www.google.com/chrome/eula.html)
Not only would we have Open Source Zealots complaining, but we'd alos have Privacy Zealots complaining about Google's date farming.


Would someone please, in plain English, tell me what I can no longer do in Firefox 3.0.2 that I could with <= 3.0.1?
It just seems that the EULA is putting into (poorly formed) words, something that has always been the case.

---

### Post by exploder on 2008-09-14
It may not be cool but at this stage of development it is not going to change.

---

### Post by plun on 2008-09-14
Well... typical GNU/Linux problem "out of nothing".

Can someone show a reference where a "official" Ubuntu person
ask Mozilla Foundation about this  ?

Nevertheless if Mozilla wants this, 99% of all users just closes this license agreement and remaining 1% starts a web browser war.

---

### Post by fluteflute on 2008-09-14
> **exploder said:**
> Doesn't the agreement make sense? What would stop Microsoft from slapping on their logo and calling it IE 9?
There is nothing to stop that. There is nothing to stop Microsoft taking Ubuntu and calling it Windows 7 - as long as it doesn't call it Ubuntu.

If that happened we in the OSS community should be glad rather than annoyed.

---

### Post by nanog on 2008-09-14
"Exactly. This is about Mozilla trying to preserve their trademarks, i.e. the logo and the name. I do believe Ubuntu is the same." 

This is a straw-man argument...ubuntu does not require an eula for install. (If there were an eula I would switch the 18 boxes I own or administer to sidux in a heartbeat.) Morever, copyleft has been proven in the courts as an effective legal defense of trademark rights. I do not recall seeing an eula for open office, gimp, gnome, mysql, apache etc. Virtualbox binaries do have a eula  and they are not included in main. Lets be consistent and not give in to mozilla just bacause they are a "recognizable brand". Mac does just fine with a proprietary browser that, imo, is inferior to iceweasel.

---

### Post by nanog on 2008-09-14
"If that happened we in the OSS community should be glad rather than annoyed."

Bug #1 would be finally closed!

---

### Post by phenest on 2008-09-14
> **nanog said:**
> ...ubuntu does not require an eula for install./QUOTE]

But, Mark Shuttleworth did say:
[QUOTE]I think it's perfectly reasonable for Mozilla to have requirements and guidelines for the use of their trademark - we have the same for Ubuntu,

What does that tell you?

---

### Post by exploder on 2008-09-14
It is still too bad that we can't get a thread of this size for fixing actual problems....

---

### Post by nanog on 2008-09-14
I am running chrome in ubuntu and I can assure you that there is no eula. If you google around you will realize that an eula was mistakenly issued and immediately retracted (after much furor I might add). I've attached a screenshot of chrome in ubuntu. 

You'll note that I also use opera - which has no eula and is non-free. I am not a free software zealot but I do use ubuntu in a corporate setting and if I were to tell our IT people that the software requires an eula they would not let me use it without legal approval. I also do not like eulas or licensing pop-ups. In fact when xp came out I switched to linux because of obtrusive licensing rubbish.

---

### Post by phenest on 2008-09-14
> **exploder said:**
> It is still too bad that we can't get a thread of this size for fixing actual problems....

I've got totally side tracked. Yep, back to fixing them bugs.

---

### Post by lukjad on 2008-09-14
I honestly don't know what to say. I've never seen this and hope to never have to. Then again, too much info is better than too little.

---

### Post by exploder on 2008-09-14
Thanks, phenest!

---

### Post by Merk42 on 2008-09-14
> **exploder said:**
> It is still too bad that we can't get a thread of this size for fixing actual problems....

But that would require testing of alphas and finding the errors in the source code. It's much easier for people to just complain about things.

> **nanog said:**
> I am running chrome in ubuntu and I can assure you that there is no eula. If you google around you will realize that an eula was mistakenly issued and immediately retracted (after much furor I might add). I've attached a screenshot of chrome in ubuntu. 


No, it has a EULA, if it were retracted why would it still be on their page?  [The retraction was a certain part of their EULA, Section 11](http://yro.slashdot.org/article.pl?sid=08/09/04/2333205), which made it sound like they owned anything you looked at in Chrome.

---

### Post by gnomeuser on 2008-09-14
I find it annoying and unlike expected behavior in the Free Software community. 

I understand they are in their good right to do this but I really wish they would be less in your face. I am sure if trademark abuse was a problem we would see them drag people to court over it, as they are not doing this to the best of my knowledge this has at best a preventative effect and at worst it turns the user off their product.

One should remember that one of the appeals of Free Software is the transparent licensing terms, this is taking a step in a direction away from that. I think it's something that should be considered strongly.

---

### Post by phenest on 2008-09-14
I wasn't going to post anymore on this thread, but I just had a thought I'd like to share:

If I disagree with the EULA, I can use another browser, right? But I can't remove Firefox.

This has become an issue in Windows where people would like to remove IE, but can't.

But I should be able to remove quite easily from Ubuntu, shouldn't I? So, why can't I? If I have the choice as to whether to use it or not, should I not have the choice to remove it?

I know I could probably remove it through Synaptics, but I should also be able with the Add/Remove too.

This could also be said of other software, but the others don't have EULA's.

And you're quite welcome, exploder.

---

### Post by Nullack on 2008-09-14
You can remove ff

---

### Post by Starks on 2008-09-14
I like open-source, but I'm not passionate or neurotic about it. We can't afford to burn our bridges with Mozilla over something as trivial as a one-time EULA THAT IS VERY GENEROUS.

---

### Post by jlacroix on 2008-09-14
Ubuntu should remove the EULA. We never needed it before, so we don't need it now.

---

### Post by Starks on 2008-09-14
I'm not suggesting we ignore the issue or attempt to placate Mozilla, but we do need to have a little chit-chat with the devs and users of both Ubuntu and Firefox.

---

### Post by inportb on 2008-09-14
What's wrong with using ABrowser by default? Users can then choose to use Firefox if they want to. Iceweasel's another option, but ABrowser's already in the repositories.

> **xebian said:**
> I don't know of a relationship, but if there is, Firefox should be the one grateful because Ubuntu is giving them a lot of users.

I agree...

---

### Post by collinp on 2008-09-14
I find it offensive that they put a EULA on a open source browser, plus i dislike the fact that they feel they need one.

EDIT: Another option is Opera, which is actually faster at rendering pages than Firefox.

---

### Post by inportb on 2008-09-14
> **Hellow said:**
> Another option is Opera, which is actually faster at rendering pages than Firefox.

But Opera is not free software. I like Opera, but it would not do to include it by default.

---

### Post by ronacc on 2008-09-14
I too am an opera user and would highly recomend it to anyone , however since it is not opensource I would not wat to see it as the default . With that said I find the Idea of an EULA on firefox offensive , is it opensource or not they can't have it both ways .

---

### Post by BwackNinja on 2008-09-14
I'm not seeing the reason for all the fuss specifically for the EULA=bad, but its mostly the EULA showing=bad that people are saying. The EULA doesn't do _anything_ other than in special use cases where you'd probably want legal advice anyway. I think it would be kinda hard and unworthwhile to ever break the EULA.

---

### Post by nanog on 2008-09-14
I am sure this thread seems like a "waste of time" to those who disagree but debate and working on bugs are not mutually exclusive. 

As of now, for me, there are no "ubuntu" bugs in alpha5. Hope I haven't jinxed it. :)

---

### Post by nanog on 2008-09-14
From Slogger on the bug report:

> 
I'm of the camp that asks if Mozilla can force ubuntu do display and EULA, then pretty soon every too big for its britches "free" software project is going to try and make you click past a stupid EULA screen when you launch. There goes one of the prime reasons to use linux/ubuntu over other non-free OSes: things no longer just work without hassle.

I say anything that requires you to click an extra screen shouldn't be installed by default.

---

### Post by Merk42 on 2008-09-14
> **nanog said:**
> From Slogger on the bug report:

I believe that's called a Slippery Slope...

---

### Post by ronacc on 2008-09-14
I can speak only for myself but I believe that the "fuss" is about the fact that they feel that the GPL is not good enough and need to tack on their own EULA , extend that concept to every default app and we would spend 2 or 3 hrs during install clicking "I Agree" not to mention what effect not clicking "I agree" might have since FF is a default .

---

### Post by knopper67 on 2008-09-14
If Canonical decides to keep firefox in main, they just lost a user. And I'm Serious. [-(

mozilla can go to hell with their EULA. They don't deserve to have that capital "M" in their name anymore. 

And finally, and I'm switching to Epiphany. I can't wait 'till it ditches their craptastic rendering engine. 
:guitar:

---

### Post by ronacc on 2008-09-15
> **knopper67 said:**
> 
mozilla can go to hell with their EULA. They don't deserve to have that capital "M" in their name anymore. 
 
:guitar:

they haven't deserved that capital M since the sold out netscape to AOL the second greatest evil behind MS .

---

### Post by vishalrao on 2008-09-15
erm, aren't both EULAs and the GPL simply "licenses" ? whats so offensive about having them in open source software. i just find it a little annoying that moz's EULA needs to be displayed to the user upon first run of FF.

can it not be displayed, say, during installation, along with other licenses like the GPL and any other package licenses? or are moz demanding it be displayed to every user once?

---

### Post by karellen on 2008-09-15
as far as I'm concerned this is not a bug

---

### Post by jrusso2 on 2008-09-15
> **karellen said:**
> as far as I'm concerned this is not a bug

Not only is it not a bug, I have downloaded and installed many GPL programs and had to agree to the EULA now how is this different?

---

### Post by jlacroix on 2008-09-15
Again, I still want to know why this was not required before and is required now.

Additionally, there's nothing stopping Ubuntu from rebranding Firefox and calling it whatever they want. "Ubuntu Web Browser" or "eBuntu", you get the idea.

---

### Post by vishalrao on 2008-09-15
what canonical can do is install abrowser or icewhatever and the menu item should read simply "Web Browser" and the tooltip popup should read "Based on Firefox" so regular users will know this is FF code running :D

---

### Post by _oOMOo_ on 2008-09-15
I can't speak for everyone but I personally am perfectly capable of thinking about this issue, maybe even posting about it AND testing Intrepid including reporting bugs etc. Is it possible we can stop spamming this thread with comments about how desperately important everything else is in comparison? It just comes across as a little condescending.

I'm not sure what this EULA adds to existing legislation put in place to protect trademarks - can anyone enlighten me? Why has it only now been included in Firefox (TM)?

---

### Post by karellen on 2008-09-15
> **_oOMOo_ said:**
> I can't speak for everyone but I personally am perfectly capable of thinking about this issue, maybe even posting about it AND testing Intrepid including reporting bugs etc. Is it possible we can stop spamming this thread with comments about how desperately important everything else is in comparison? It just comes across as a little condescending.

I'm not sure what this EULA adds to existing legislation put in place to protect trademarks - can anyone enlighten me? Why has it only now been included in Firefox (TM)?

if you ask me submitting "bugs" like these only makes developers life harder and counterproductive. instead of fixing the real problems, they wonder what's the deal with a trademark

---

### Post by loell on 2008-09-15
> **karellen said:**
> if you ask me submitting "bugs" like these only makes developers life harder and counterproductive. instead of fixing the real problems, they wonder what's the deal with a trademark

On the contrary this bug is valid, and they don't think all day just to figure out what to do with it, its up to the Mozilla people.

---

### Post by Vivaldi Gloria on 2008-09-15
> **karellen said:**
> if you ask me submitting "bugs" like these 

I guess this is not a bug for someone who arbitrarily clicks yes to EULAs, who doesn't care about user freedoms, and who wouldn't consider something a bug as long as it's working for them. I am happy to say that there are a lot of people in the linux community who cannot be classified as such. Hence it's a bug.

> only makes developers life harder and counterproductive. 

Ubuntu is about making users life easier and productive. Otherwise everyone could use LFS. Of course making users easier and productive comes with the price tag of making developers life harder - they have to develop. But I wouldn't call this endeavour counterproductive.

In this case there are already some solutions out there (iceweasel, epiphany etc.) so no serious development is needed anyway.

> instead of fixing the real problems, they wonder what's the deal with a trademark

This is past a trademark issue. They are putting an EULA window in front of the users. I take time in reading EULAs carefully and really, it takes time. So this is a usability bug at least. Also companies have to get lawyers to look at the EULAs of the software they are planning to adopt, so this is a potential problem for adoption of ubuntu in firms. Moreover, what happens when I decide not to accept the EULA? Then I'm left with a non-working browser, so this is really a big bug.

---

### Post by exploder on 2008-09-15
Why would you not accept the EULA? Do you plan on modifying the program and redistributing it? Are you going to modify and redistribute the package as Firefox, with it's branding? I doubt it.

This is not as big a deal as people are making it out to be. It is time to move on and actually fix real bugs in Intrepid.

---

### Post by Sophont on 2008-09-15
What a storm in a watercup.

If this is a usability bug than at least the workaround is as easy and obvious as can be: Click. I think we can live with this terrible bug for a while until more pressing usability bugs have been fixed. ;-)

Yes - clicking yet another EULA is a small PITA.
But most people will not read it carefully - they will click through it like they click through so many others of the kind.
I also very much doubt that this will require hours of precious corporate lawyer everywhere. This is a typical trademark thing after all and more or less the same thing as on Windows.

Mozilla has no choice in so far as protecting their trademark goes. US Trademark law (IIRC) requires the owner to defend it or loose it (IANAL).
That a less well-meaning entity (think spammer or some such) could eventually distribute another (slightly changed fork of FF for example) browser (then) *legally* as "Firefox" is not a good thing.
This has nothing to do with open source per se - the source is still open and free. There is also no incompatibility with the GPL. One (GPL) is concerned with the distribution of the source code - the other is a matter of protecting the brand name.

If that requires a click-through EULA that 98% of all people won't read I don't know. Perhaps another solution will be found that satisfies trademark law and does not require yet another silly - nobody reads it anyway - EULA-click-through. That would be nice.
Until then it's a small price to pay for a great browser and having a well recognized brand name.

Everybody reading and writing in this thread already invested more time in this debate than they ever will with that Firefox EULA.

---

### Post by Vivaldi Gloria on 2008-09-15
You may be happy with clicking through EULAs and/or using non-free components but not everyone is.  So why not change it to iceweasel or "ubuntu browser" or whatever? 


> This is not as big a deal as people are making it out to be.

> What a storm in a watercup.

It takes two sides to have a disagreement. So I can easily direct these comments to you. Why not accept iceweasel (or whatever) if it's not important to you?

---

### Post by wgrant on 2008-09-15
> **karellen said:**
> if you ask me submitting "bugs" like these only makes developers life harder and counterproductive. instead of fixing the real problems, they wonder what's the deal with a trademark

I filed the bug. Look to the left of and below this post.

---

### Post by Vivaldi Gloria on 2008-09-15
> **fujitsu said:**
> I filed the bug. Look to the left of and below this post.

Ha ha ha. This made my day. :-)

---

### Post by analystscouch on 2008-09-15
> **Sophont said:**
> 
But most people will not read it carefully - they will click through it like they click through so many others of the kind.


I know this has been said before, but this is precisely why the EULA is problematic! Because (in some nations...) you are making a legal agreement when you just "click through it". In a way, I'd prefer that the user was some how *forced* to read the whole thing! Because then they will know what they are letting themselves in for. Think about it, you wouldn't "sign" any other kind of legal document without reading it carefully would you?

Now, I know someone is going to object that in this particular agreement you aren't "letting yourself in" for anything *too terrible*, and I agree. The content of this particular EULA isn't the worst, *but the principle of EULAs in open source is always bad*. In my opinion. That is why this should be opposed: this is just the thin edge of the wedge - we shouldn't encourage this disturbing culture where people think it is normal to just accept/ignore a legal document which restricts how they use software and information.

---

### Post by Bossieman on 2008-09-15
This is a problem, even if its not a bug. Ordinary users react, find this irritating and this is not in the spirit of Ubuntu. Its not strange or weird or wrong that users react. This should be obvious for everyone. 

If we just sits back and let it go, who knows what will happened. Will other start applying the same methods resulting in Eulas when users open up other programs that is installed default in Ubuntu. 
How can this not be a problem. This is truly a sad day in the history of Ubuntu.

---

### Post by zekopeko on 2008-09-15
i don't understand why they don't simply include the trademark part in the MPL license and put the license under help as totem/other_programs do.

---

### Post by karellen on 2008-09-15
> **fujitsu said:**
> I filed the bug. Look to the left of and below this post.

Ok, mea culpa regarding this issue. I'm just a regular Linux user and from my point of view accepting Firefox's EULA is not a big deal. nevertheless, as I'm not currently using Ubuntu but Mandriva, I didn't have to agree with any EULA in order to use Firefox. anyway, not such a big deal, I'm sure Iceweasel or whatever it's called it's a perfectly decent browser and only the name differs from Firefox

---

### Post by Gina on 2008-09-15
That so many people have posted in this thread (excluding those who say this thread is a waste of time) proves to me that this is an important issue.  For myself and many others, avoiding all those wordy and difficult to understand EULAs was one reason to migrate from Windows.  To be able to just use software without having to click through all those EULAs was a breath of fresh air.

I agree that companies have to protect their trademarks but **IN YOUR FACE** EULAs for users is not necessary.  The situation only applies to those who wish to develop modifications and additions and then use the trademark, as has been said.

I feel this is an important point of principle.

---

### Post by jfbilodeau on 2008-09-15
I would prefer not to let this one slide. I know many fine folks suggested that the EULA is no big deal, but I'm of the opposite opinion.

Having a EULA strictly for Firefox gives special privilege to the project. Granted that Firefox is widely used. However, what's stopping Gnome, OpenOffice.org, and even the Linux Kernel from requesting the same privilege? I fear this is a terrible precedent.

Especially since the only section I can find in the [EULA]("http://www.mozilla.com/en-US/legal/eula/firefox-en.html") that is not in the MPL is "You may not remove or alter any trademark, logo, copyright or other proprietary notice in or on the Product. This license does not grant you any right to use the trademarks, service marks or logos of Mozilla or its licensors."

I understand that Mozilla wants to protect their valuable trademark, but the EULA also goes against the free/open source software ideal. Firefox is falling under the category of software like [Cedega]("http://www.transgaming.com/products/cedega/"), [MyEclipse]("http://myeclipseide.com/") or [StarOffice]("http://www.sun.com/software/staroffice/index.jsp") -- They are comprised mostly or entirely of free software, but they are not entirely free. That is, free as in free speech, not free beer.

Since Mozilla Firefox is no longer free software, I believe that it has lost it's privileged place in the Ubuntu distribution.

There are plenty of fine browsers out there. Ubuntu does not need the Firefox brand to success. Please remember that Firefox 1.0 came out less than four years ago. That tells me that most users can get used to a new browser (brand) very quickly.

---

### Post by karellen on 2008-09-15
> **jfbilodeau said:**
> I would prefer not to let this one slide. I know many fine folks suggested that the EULA is no big deal, but I'm of the opposite opinion.

Having a EULA strictly for Firefox gives special privilege to the project. Granted that Firefox is widely used. However, what's stopping Gnome, OpenOffice.org, and even the Linux Kernel from requesting the same privilege? I fear this is a terrible precedent.

Especially since the only section I can find in the [EULA]("http://www.mozilla.com/en-US/legal/eula/firefox-en.html") that is not in the MPL is "You may not remove or alter any trademark, logo, copyright or other proprietary notice in or on the Product. This license does not grant you any right to use the trademarks, service marks or logos of Mozilla or its licensors."

I understand that Mozilla wants to protect their valuable trademark, but the EULA also goes against the free/open source software ideal. Firefox is falling under the category of software like [Cedega]("http://www.transgaming.com/products/cedega/"), [MyEclipse]("http://myeclipseide.com/") or [StarOffice]("http://www.sun.com/software/staroffice/index.jsp") -- They are comprised mostly or entirely of free software, but they are not entirely free. That is, free as in free speech, not free beer.

Since Mozilla Firefox is no longer free software, I believe that it has lost it's privileged place in the Ubuntu distribution.

There are plenty of fine browsers out there. Ubuntu does not need the Firefox brand to success. Please remember that Firefox 1.0 came out less than four years ago. That tells me that most users can get used to a new browser (brand) very quickly.

let's not forget though that the vast majority of users doesn't care if a program is 100% free (as both in speech and beer) or just free as freeware. as long they don't have to pay for it, it's fine for them

---

### Post by jfbilodeau on 2008-09-15
> **karellen said:**
> let's not forget though that the vast majority of users doesn't care if a program is 100% free (as both in speech and beer) or just free as freeware. as long they don't have to pay for it, it's fine for them

Agreed, but Iceweasel (or the likes) appeals to folks who like freeware and to folks who like free software, thus reaching a wider audience.

:)

---

### Post by jfbilodeau on 2008-09-15
Yay!

The folks at Codeweavers are giving us a taste of Google Chrome. This could become a serious contender in the browser world. I strongly recommend you give it a go to see how there is still plenty of innovations that can be brought to browsers.

Unfortunately, their implementation is not free as in free speech, but it's only a matter of time before we see Chrome free on Linux.

Download here: [http://www.codeweavers.com/services/ports/chromium/]("http://www.codeweavers.com/services/ports/chromium/")

More importantly, I'm hoping that it gives the Mozilla exec something to consider...

---

### Post by timcredible on 2008-09-15
i don't even use firefox now - i use the gnome version of it, epiphany.  if people don't like the eula of firefox, just use epiphany.

---

### Post by GepettoBR on 2008-09-15
Well, what a pity. Now I can't use Firefox anymore. It was such a good browser, too.

Someone in mozilla needs to remove their head from their nether regions and realize that a EULa that SCREAMS AT THE USER IN ALL CAPS is a bad thing. They need to get over the "we got on Guiness lol" power rush and remember what Open Source means. This EULA is not protecting their trademark, it's hurting their trademark.

As a practical issue, a one-time pop-up isn't a big deal at all, but I (and many other people, I'm sure) feel terribly offended by this selfish and proprietary-like attitude. Mozilla has lost all my respect.

---

### Post by robzon on 2008-09-15
Mozilla is losing it. It seems they lost their way already. What's next? Maybe they'll drop official support for Linux, because 95% of their users use different OSes?

The problem is that Firefox out of box is excellent marketing for Ubuntu, and yes we DO need marketing for Ubuntu. And good one, too.

We need to care not only about existing community, but also about people who want to switch to Ubuntu. If we give them Firefox, they have something they already know and makes the whole experience a bit more familiar. If you give them Iceweasel/Epiphany it doesn't matter it's almost the same thing, it's NOT the same (different icon/name, plugins, etc - it DOES matter) and it takes this tiny bit of familiarity away.

Should Ubuntu ditch Firefox? It's a very difficult decision to make. Personally, I would stick to it a bit longer and start looking for plan B. We should, however, tell Mozilla what we think of their policy in a way that would get to them.

---

### Post by jfbilodeau on 2008-09-15
> **GepettoBR said:**
> Well, what a pity. Now I can't use Firefox anymore. It was such a good browser, too.

We don't have to ditch the source -- just the brand. Firefox, Iceweasel & ABrowser are the same browser with different branding. The difference is that one of them is not*truly* open & free.

---

### Post by jfbilodeau on 2008-09-15
> **robzon said:**
> Mozilla is losing it. It seems they lost their way already. What's next? Maybe they'll drop official support for Linux, because 95% of their users use different OSes?

I would be curious to see the stats on that. Internet Explorer is the default on Windows, while Firefox is often the default on Linux distros. This hints to me that Firefox usage may be higher on Linux than on Windows, proportionally speaking.

Also, I'm not sure that branding is that big of a deal. Firefox 1.0 is less than four years old. This tells me that a brand can be built quickly, and demolished quickly. Remember Netscape? I hope that the suits at MozCorp is not repeating history...

---

### Post by BlueSkyNIS on 2008-09-15
I am kinda surprised by MozzCorp for doing this and I find this very offending to Ubuntu community.

---

### Post by kingbilly on 2008-09-15
My windows friend was shocked when he saw my computer (ubuntu 8.10) boot and see a EULA for firefox.  He said "I thought you don't have to sign your life away to use programs on linux"  And I told him that unless its java or something, usually I don't.  Yikess!

On launchpad some people thought we should rename firefox to Ubuntu Web Browser.  Mark said he was against that because it wasn't coded by ubuntu.  But he also suggested taking a look at aBrowser.  Some people on launchpad didn't like that name. 
So my thoughts are to rename aBrowser to "Ubuntu Web Browser" or "Web Browser".

I don't want to be labeled religious, but I like my Ubuntu FOSS and ready to use out of the box.  I sure hope they can work out something with Mozilla.


it just doesn't feel right.

---

### Post by inportb on 2008-09-15
> **kingbilly said:**
> But he also suggested taking a look at aBrowser.  Some people on launchpad didn't like that name. 
So my thoughts are to rename aBrowser to "Ubuntu Web Browser" or "Web Browser".

ABrowser already calls itself "Web Browser." Just install it and see for yourself. As far as I can tell, the only difference is visual, and even that is minimal since I use a different theme.

---

### Post by GepettoBR on 2008-09-15
If the problem with ditching Firefox is familiarity, then we'll only have to suffer through this dilemma for one release cycle. By the time Jaunty is up for use, I'm sure Google Chrome will have surpassed Firefox's userbase by far.

---

### Post by SunnyRabbiera on 2008-09-15
Well Open office has a set up an a EULA too shouldn't that be banned now too?

---

### Post by jfbilodeau on 2008-09-15
> **SunnyRabbiera said:**
> Well Open office has a set up an a EULA too shouldn't that be banned now too?

I don't remember seeing a EULA for OOo when I install Ubuntu or when I start OOo. Where did you get this EULA?

---

### Post by JACooks on 2008-09-15
A blog post from Mitchell of Mozilla lends some light on the issue, including acknowledging a mistake made.  Thought we should all take a peek at that before we continue raining down praise/damnation on Mozilla.

[http://blog.lizardwrangler.com/2008/09/15/ubuntu-firefox-and-license-issues/](http://blog.lizardwrangler.com/2008/09/15/ubuntu-firefox-and-license-issues/)

---

### Post by GepettoBR on 2008-09-15
> There&#8217;s a third question of services, and whether the FLOSS license for the code can include the services one accesses.  We think this isn&#8217;t true all the time, and the license will reflect that.  The code is governed by FLOSS licenses, and we should have been clear about that.

Wait, does this mean they can add sections to their license forbidding users to access certain sites with their browser? What does "services" mean in this paragraph?

---

### Post by kingbilly on 2008-09-15
> **JACooks said:**
> A blog post from Mitchell of Mozilla lends some light on the issue, including acknowledging a mistake made.  Thought we should all take a peek at that before we continue raining down praise/damnation on Mozilla.

[http://blog.lizardwrangler.com/2008/09/15/ubuntu-firefox-and-license-issues/](http://blog.lizardwrangler.com/2008/09/15/ubuntu-firefox-and-license-issues/)

And i'd like to know anyone's opinion of this response posted on that page.  I had been feeling the same.

> 

Mackenzie Says:
September 15th, 2008 at 12:04 pm
My thinking is that since the MPL & the trademark stuff aren’t really about end-use, but about developers, that putting it in an official Firefox release doesn’t make a lot of sense. Since that stuff is for developers, it should go in the COPYRIGHT file in the CVS and tarballs if it’s not in there right now. That’s how that stuff is usually handled, and I think it’s how Mozilla has done it til now.

---

### Post by Kernel Sanders on 2008-09-15
Just rename it "Internet Browser" and remove the Mozilla branding.

No EULA and problem solved :KS

---

### Post by Erik Trybom on 2008-09-15
I don't think he answered the question of why the EULA had to be there in the first place. Even if it had the right content.

---

### Post by ronacc on 2008-09-15
> **GepettoBR said:**
> Wait, does this mean they can add sections to their license forbidding users to access certain sites with their browser? What does "services" mean in this paragraph?
even worse that sentence implys that they could have the terms and not "show people the terms" .  yeah right, here just sign this blank contract sucker .

---

### Post by jlacroix on 2008-09-15
> **GepettoBR said:**
> Well, what a pity. Now I can't use Firefox anymore. It was such a good browser, too.

Someone in mozilla needs to remove their head from their nether regions and realize that a EULa that SCREAMS AT THE USER IN ALL CAPS is a bad thing. They need to get over the "we got on Guiness lol" power rush and remember what Open Source means. This EULA is not protecting their trademark, it's hurting their trademark.

As a practical issue, a one-time pop-up isn't a big deal at all, but I (and many other people, I'm sure) feel terribly offended by this selfish and proprietary-like attitude. Mozilla has lost all my respect.

Refusing to use Firefox due to it having a EULA is rather silly.

I do agree though that having the EULA is retarded. Mozilla needs to realize that Firefox shipping with Ubuntu gives them a HUGE audience, being that the most popular Linux distribution includes it in every CD. If Ubuntu uses Firefox code to rebrand it and customize it and even rename it, Mozilla would lose a VERY large part of their user base.

And that's what Ubuntu should do. Just think of the possibilities if Ubuntu released their own browser based on Firefox code. There would be no limits. They could customize anything they wanted. They could add any features that they wanted. Everything would be way better, the browser would be customized to make it run better with Ubuntu's kernel. That would mean a faster browser for the rest of us.

I think the Ubuntu developers should really consider this for their next release. (Jaunty).

---

### Post by GepettoBR on 2008-09-15
> **ronacc said:**
> even worse that sentence implys that they could have the terms and not "show people the terms" .  yeah right, here just sign this blank contract sucker .

I don't think "showing the terms" counts as a service, since it should be a pre-contractual transaction. In theory, if you change the terms, the old contract is voided and replaced, so presenting the new terms is a pre-requisite if they want to make any claims of validity. Then again, I only know Brazilian law and a few scraps of International treaties so my guess is only just as good - I do believe that the good-faith principle is protected by most Western legislations, though, and changing a license agreement without properly notifying the other party (even if you had previously said that you would do that) is a violation of this principle. Just like signing a contract that gives you the right to kill me doesn't protect you from murder laws if you do.

> **jlacroix said:**
> Refusing to use Firefox due to it having a EULA is rather silly.

It's a matter of principle. I left Windows because of principle, and switching web browsers is much less of a hassle than switching OSes. I find it offensive to my morals that a company which has always played the good guy will do something so completely unnecessary and utterly abusive (less because it pops up in front of you than because of the way it's written - fortunately it looks like they'll at least change the text) just as soon as they think they have some "power". If this is how they do business, I want nothing to do with them.

---

### Post by ronacc on 2008-09-15
> **GepettoBR said:**
> I don't think "showing the terms" counts as a service, since it should be a pre-contractual transaction. In theory, if you change the terms, the old contract is voided and replaced, so presenting the new terms is a pre-requisite if they want to make any claims of validity. Then again, I only know Brazilian law and a few scraps of International treaties so my guess is only just as good - I do believe that the good-faith principle is protected by most Western legislations, though, and changing a license agreement without properly notifying the other party (even if you had previously said that you would do that) is a violation of this principle. Just like signing a contract that gives you the right to kill me doesn't protect you from murder laws if you do.





what I was getting at is the first sentence in the 5th paragraph of this blog     [http://blog.lizardwrangler.com/2008/09/15/ubuntu-firefox-and-license-issues/](http://blog.lizardwrangler.com/2008/09/15/ubuntu-firefox-and-license-issues/)    (link provided by JACooks above)  it certainly seems to say that they have the terms of service but just don't think it is a good idea to let us see them . not leting us see them might or might not invalidate the EULA , it certainly should but here in the US intelectual property law as applies to software is in such an ugly mess that there is no telling , it is interpeted differently by every local judge, prosecutor and circus clown .

---

### Post by GepettoBR on 2008-09-15
> **ronacc said:**
> what I was getting at is the first sentence in the 5th paragraph of this blog     [http://blog.lizardwrangler.com/2008/09/15/ubuntu-firefox-and-license-issues/](http://blog.lizardwrangler.com/2008/09/15/ubuntu-firefox-and-license-issues/)    (link provided by JACooks above)  it certainly seems to say that they have the terms of service but just don't think it is a good idea to let us see them . not leting us see them might or might not invalidate the EULA , it certainly should but here in the US intelectual property law as applies to software is in such an ugly mess that there is no telling , it is interpeted differently by every local judge, prosecutor and circus clown .

> This leaves the question of whether it ever makes sense to show people the terms that relate to the software and services available to them.
Well, through analogic interpretation of regular contract laws, if you weren't shown the terms then they don't apply. Here in Brazil it'd be that simple, but in the USA judges have way too much power to interpret the law whichever way they see fit. I can see why this is a pickle.

---

### Post by Sophont on 2008-09-15
> **Vivaldi Gloria said:**
> You may be happy with clicking through EULAs and/or using non-free components but not everyone is.  So why not change it to iceweasel or "ubuntu browser" or whatever? 

It takes two sides to have a disagreement. So I can easily direct these comments to you. Why not accept iceweasel (or whatever) if it's not important to you?

1. Come on - that's silly - of course I'm *not* *happy* to click through EULAs. I just don't make it into more than it is. An occasional small PITA.

2. Why not Iceweasel?  I'm all for having Iceweasel in the repo. Nice to have options and all. But it's not the right default.
Anybody who is really bothered by this will simply use another browser and be done with it. The people here who are most annoyed by this are all competent enough to find alternatives in the repo. Newbies OTOH should have the by now well-renowned and widely recognized (and trusted) Firefox as default web browser. A brand name has worth and FF is now a well established brand.

Last but not least - I'm a bit shocked at the number of people who are downright ungrateful. The folks at Mozilla provided us with a great browser - and I don't know how many of those (wo)man-hours are unpaid - but I guess quite a lot. And yet we have to read through plenty of messages here of people who are using words like "disgusted" when all they have to pay for that browser is to download and install it and now click through a EULA (with optionaly reading it once).

We simply lack information about a) applicable law, b) any legal troubles Mozilla faced re its trademarks and/or c) potential trouble lawyers pointed out to them. And half complainers here are simply confused about copyright and trademark.

This is a fairly small one-time annoyance and not a terrible thing. It's not the final days. It's not a slippery slope. "ls" won't show a EULA next time you make a fresh install.

---

### Post by danf_1979 on 2008-09-15
I don't really understand what the problem is. The EULA states that:

"BY CLICKING THE "ACCEPT" BUTTON, OR BY INSTALLING OR USING THE MOZILLA FIREFOX BROWSER, YOU ARE CONSENTING TO BE BOUND BY THE AGREEMENT. IF YOU DO NOT AGREE TO THE TERMS AND CONDITIONS OF THIS AGREEMENT, DO NOT CLICK THE "ACCEPT" BUTTON, AND DO NOT INSTALL OR USE ANY PART OF THE MOZILLA FIREFOX BROWSER."

So you have more than one way of consenting, there is no need for any EULA popup window. Usage makes you consent, installing makes you consent.

Cheers.

---

### Post by inportb on 2008-09-15
> **danf_1979 said:**
> I don't really understand what the problem is.

You clearly don't.

Installation implies consent. Installing Ubuntu installs Firefox. What if one wants to install Ubuntu but does not consent?

---

### Post by danf_1979 on 2008-09-15
> **inportb said:**
> You clearly don't.

Installation implies consent. Installing Ubuntu installs Firefox. What if one wants to install Ubuntu but does not consent?

Yeah, you're right, didn't thought about that.

---

### Post by inportb on 2008-09-15
I might sound like a free software fanatic, but I'm just trying to assemble different points of view. I myself would be fine clicking through this EULA, but it is clearly an issue for others. However, if this ends up setting a precedent for other free applications to display license agreements, I would be disappointed.

---

### Post by JeevesBond on 2008-09-16
Am posting here to link up the Brainstorm item with the forum topic, if you wish to vote on replacing Firefox the URL is: [http://brainstorm.ubuntu.com/idea/5372](http://brainstorm.ubuntu.com/idea/5372)

---

### Post by _oOMOo_ on 2008-09-16
For those who haven't seen it, this Fedora solution appears simple, elegant and gives users the choice that so far seems be woefully absent from the default Firefox install in Ubuntu:

[http://fedoraproject.org/static/firefox/]("http://fedoraproject.org/static/firefox/")

---

### Post by BlueSkyNIS on 2008-09-16
> **_oOMOo_ said:**
> For those who haven't seen it, this Fedora solution appears simple, elegant and gives users the choice that so far seems be woefully absent from the default Firefox install in Ubuntu:

[http://fedoraproject.org/static/firefox/]("http://fedoraproject.org/static/firefox/")

Yea, I also like how they managed to resolve this issue. Maybe, we should do the same?

---

### Post by Nullack on 2008-09-16
They havent resolved the issue at all

They are referring to functionality that already existed in ff

That statement doesnt address the trademark issue at all

---

### Post by _oOMOo_ on 2008-09-16
> **Nullack said:**
> They havent resolved the issue at all

They are referring to functionality that already existed in ff

That statement does address the trademark issue at all

Fair enough, but maybe a similar page with a link to the EULA and a half-decent explanation of why Mozilla feels it's necessary? And some info about abrowser for example?

---

### Post by Game_boy on 2008-09-16
> **_oOMOo_ said:**
> Fair enough, but maybe a similar page with a link to the EULA and a half-decent explanation of why Mozilla feels it's necessary? And some info about abrowser for example?

That would be fine for you or other people on this forum, but new users would get upset. Why don't we just use the Mozilla-approved (generic) Linux Firefox build? Then we can have the trademarks but not EULA.

---

### Post by GepettoBR on 2008-09-16
I think the Ubuntu version has some tweaks and changes to better conform with Ubuntu's verison of the Linux kernel. The generic firefox would be buggy in Ubuntum if that really is the case.

---

### Post by eragon100 on 2008-09-16
Is this stupid waste of time still going on? Just include firefox as the default browser, like it's been for ages! You can't change it anyway, since feature freeze is past *sticks out tongue*

---

### Post by eragon100 on 2008-09-16
> **exploder said:**
> Totally free is Debian. Only mp3s work, "out of the box". Totally free does not support, youtube. apple movie trailers, real audio and video, and the list goes on.

Agreed, And I don't want my computer for which I payed 700€,- to "work" like that. Don't forget to mention: with pure free software, you get no 3d games!

---

### Post by zolookas on 2008-09-16
I think we should compare and contrast Firefox and Iceweasel or IceCat licenses or EULA's and then talk about posibility to include or exclude firefox from default ubuntu install. As of now, i see only very few people in this discussion which does understand all differences between using branded and unbranded firefox version. It does not matter if it shows EULA or not in the separate window or in new browser tab or how fast you can accept it and close it, it matters how EULA affects you and what freedoms does it take from you.

> **inportb said:**
> 
Installation implies consent. Installing Ubuntu installs Firefox. What if one wants to install Ubuntu but does not consent?
How come one application prevents you from installing whole distro? This should not be allowed to happen.

---

### Post by npman on 2008-09-16
My thoughts on Bug No#269656?

I couldn't care less.  

I just wish people devoted this much energy to achieving a browser that doesn't crash with Flash.

---

### Post by linuxguymarshall on 2008-09-16
Im not going to use if if I have to agree to an EULA. Ill just use Epiphany or compile my own version of mozillia

---

### Post by zolookas on 2008-09-16
> **npman said:**
> My thoughts on Bug No#269656?

I couldn't care less.  

I just wish people devoted this much energy to achieving a browser that doesn't crash with Flash.
I don't know what exactly causes crashes, but do you mean that community should be creating workarounds for proprietary plugins which crash browser?

---

### Post by Mr. Picklesworth on 2008-09-16
> I just wish people devoted this much energy to achieving a browser that doesn't crash with Flash.Well, they have. (See Epiphany with WebKit, Midori). Trouble is, an astounding number of people seem to believe Ubuntu couldn't live without Firefox... as if the browser is actually good for the user experience or something. (Which it is not; the thing is inconsistent with Ubuntu from every corner).

Anyway, that bug report has gone completely crazy and unproductive. We now have "use Iceweasel" repeated about 60 times, "fork Ubuntu" repeated 5 times, and a large number of people who seem to believe this is shipped.
Why can't these things just stay nice and low key?

---

### Post by npman on 2008-09-16
> **zolookas said:**
> I don't know what exactly causes crashes, but do you mean that community should be creating workarounds for proprietary plugins which crash browser?

Yeah, if need be.

Or make Gnash work.  It can be any browser- just as long as it isn't shut out of sites where people in a business environment can do work.

Look, I hate Flash. But the sad truth is people want it.  And thus far- the Linux experience with Flash sucks.  At some point, the finger pointing needs to end and it needs to be dealt with. I, personally, think it needs to be a greater priority than making Ubuntu boot faster, having Windows that jiggle, or Religious Wars about EULAs.

---

### Post by ronacc on 2008-09-16
> **Mr. Picklesworth said:**
> 
Why can't these things just stay nice and low key?
because this is obiously a subject that a lot of people care passionately about , no mater which side they are on ;)

---

### Post by GepettoBR on 2008-09-16
> **eragon100 said:**
> Is this stupid waste of time still going on? Just include firefox as the default browser, like it's been for ages! You can't change it anyway, since feature freeze is past *sticks out tongue*
Oh yay, maturity! :)
> **eragon100 said:**
> Agreed, And I don't want my computer for which I payed 700€,- to "work" like that. Don't forget to mention: with pure free software, you get no 3d games!
What about OpenGL?

---

### Post by zolookas on 2008-09-16
> **npman said:**
> Yeah, if need be.

Or make Gnash work.  It can be any browser- just as long as it isn't shut out of sites where people in a business environment can do work.

Look, I hate Flash. But the sad truth is people want it.  And thus far- the Linux experience with Flash sucks.  At some point, the finger pointing needs to end and it needs to be dealt with. I, personally, think it needs to be a greater priority than making Ubuntu boot faster, having Windows that jiggle, or Religious Wars about EULAs.
Ok then, unfortunately no one can make any modifications to firefox without mozilla's approval (good luck getting that). So file a bug in mozilla's bugzilla and hope for the best.

You see? This is an issue and that makes people care about this bug.

---

### Post by TpyKv on 2008-09-16
I think the issue here is that people like having control of the software they use, And they don't like having restrictions imposed by companies like this - it's a somewhat alien concept in the free & open source world.

I for one will be uninstalling FF and looking up Abrowser - or another browser - just because I can, I have no loyalties to Mozilla, or FF, and I don't like accepting agreements / bowing to pressure from companies when it can be avoided... no matter how trivial the issue may be.

---

### Post by JACooks on 2008-09-16
Just to weigh in (again) for the sake of further information on the topic (not to be confused with me stating an actual opinion), Mozilla has posted the revised license, and has some comments about the changes, including referencing revised presentation requirements:

[http://lockshot.wordpress.com/2008/09/15/firefox-eula-in-linux-distributions/](http://lockshot.wordpress.com/2008/09/15/firefox-eula-in-linux-distributions/)

---

### Post by GepettoBR on 2008-09-16
Interesting how the blog post mentioned Fedora and Red Hat, but no one else... Shows where Mozilla has its priorities. Well, here's my chew-down on the new EULA:

```
Mozilla and its contributors, licensors and partners work to 
[b]provide the most accurate and up-to-date phishing, malware and 
other information[/b] via the Services. 
```
So, they have been working on the new license "over the past few months" and they make such a huge, messy typo? I really don't want to install a browser that provides such cool services as phishing and malware.

```
THE MOZILLA GROUP&#8217;S COLLECTIVE LIABILITY UNDER THIS AGREEMENT WILL 
NOT EXCEED THE GREATER OF $500 (FIVE HUNDRED DOLLARS) AND THE FEES PAID 
BY YOU TO MOZILLA UNDER THIS AGREEMENT (IF ANY)[color=red]<freaking capslock, damn 
you straight to Hell>[/color]. Some jurisdictions do not allow the exclusion or 
limitation of incidental, consequential or special damages, so this exclusion 
and limitation may not apply to you.
```
That's not for them to decide. No jurisdiction allows that, not in the sense they're trying to convey in this paragraph. If a court decides that they are liable for damages, then that same court will decide the extent of liability, respecting the limits imposed by law and by the specifics of the case, not by their own license agreement. If it worked any other way, I could force people to agree that I can't be arrested for murder and then kill them. The logic is the same. Also, "exceed the greater of" is a very ugly tautology that should be removed on the account of murdering the English language.

```
 (b) This Agreement will be governed by the laws of the state of 
California, U.S.A., excluding its conflict of law provisions. (c) This 
Agreement will not be governed by the United Nations Convention on 
Contracts for the International Sale of Goods. 
```
Could an expert in California's state laws  tell me what's the state's position on UN decisions taken in by the US government? If CA recognizes them, points (b) and (c) conflict.

This new EULA is certainly much better written than the previous one, and a lot clearer as well (though the grammar skill of whoever wrote this offend my Grammar Nazi Spider-sense). Still, it insists on using ALL-CAPS TEXT which adds absolutely nothing except for an unnecessary emphasis and an eyesore. Someone should remind Mozilla's lawyers that all-caps doesn't mean anything in any legal sense. The entire agreement is binding, as stated in the first paragraph, regardless of formatting.

This EULA is in the wrong place, since it deals exclusively with trademark issues and liability from the security issues. 
The first are only of concern for developers wishing to alter "the Product" and distribute their own version, and the latter could be replaced by a simple notice saying something along the lines of "While Mozilla always strives to offer you the best possible protection from internet-related threats, we cannot guarantee that your browsing experience will be 100% secure". That could show in a pop-up window, and reserve of liability would be implied. Heck, practically every software in the world is provided as-is and without guarantees, it's even part of the GPL.

That said, while the first five sections of the license are pertinent for people interested in creating their own product based on Mozilla Firefox (tm) code, the rest of the EULA is completely useless and pointless, and even this first part should not be flung at every end-user, simply because it does not apply to them. The trademark restrictions also contradict the MPL's current text, since the trademarked files are part of the source code. 

Simply put, this EULA removes Mozilla Firefox (tm) from the group known as FOSS. It's freeware, and *parts* of the source code are open, but that's not enough. Mozilla Firefox (tm) is no longer compatible with Ubuntu's philosophy.

Now, for what I think of the general situation, regarding Ubuntu:
As eragon100 so eloquently pointed out (with a complimentary display of his virtual tongue, no less) Intrepid is past feature freeze. Unless Mark takes this EULA fiasco very seriously (which he has already proven not to be the case) Mozilla Firefox (tm) will be the default web browser for Ubuntu 8.10. Therefore, and since Canonical clearly believes that they need a strong browser name to help "sell" Ubuntu (which slims the chances of abrowser, Epiphany or Iceweasel ever making it to default status), I say we turn our attention to the up-and-coming Google Chrome and pressure the decision-makers to make it Jaunty's default browser. Google has a good history in dealing with the Open Source community and they're much better equipped to create a competent, compatible browser in the long run than Mozilla. The pressure on Chrome is also much greater, since it's still very young and is being developed by the gargantuan Google. As for licensing issues, sure they may arise yet again with Chrome but at least we'll have dodged one bullet already.

P.S.: I quoted the Mozilla Firefox (tm) EULA in [noparse][code][/noparse] brackets to keep this post readable in case anyone quotes it in full.

TLDR: Mozilla's lawyers are illiterate muppets.

---

### Post by cariboo on 2008-09-16
I just saw this:

[http://tech.slashdot.org/article.pl?sid=08/09/16/1736212](http://tech.slashdot.org/article.pl?sid=08/09/16/1736212)

over on Slashdot.

Jim

---

### Post by JeevesBond on 2008-09-16
> **eragon100 said:**
> Is this stupid waste of time still going on? Just include firefox as the default browser, like it's been for ages!

How very intolerant. It may not be important to you, but it is an important issue for many people. If you don't like that you're more than welcome to not read or reply to posts about the issue.

Not everyone holds the same opinions or priorities as you, people are different.

> **eragon100 said:**
> Agreed, And I don't want my computer for which I payed 700&#8364;,- to "work" like that. Don't forget to mention: with pure free software, you get no 3d games!

False dichotomy. Including an unbranded 'Ubuntu Web Browser' does not mean we have to drop support for 3d, or anything else.

> **npman said:**
> My thoughts on Bug No#269656?

I couldn't care less.

Please leave the discussion to those that do then. Unless you have something important to add to the conversation?

People complaining that everyone should just leave this alone, and that there are higher priorities, are not taking into account that it was Mozilla Corp and Canonical who made this a priority by adding the EULA. The timing of this is entirely down to them.

---

### Post by npman on 2008-09-16
The fact that not everyone cares about the EULA *is important* to the conversation.

Perhaps there are those that think that things need not be hijacked by this tempest in a teapot.

---

### Post by Erik Trybom on 2008-09-16
So if the EULA is essentially useless, why do Mozilla push it so hard?

There's got to be some reason. You don't piss off an entire community for nothing - or do you?

---

### Post by jlacroix on 2008-09-16
> **Erik Trybom said:**
> So if the EULA is essentially useless, why do Mozilla push it so hard?

There's got to be some reason. You don't piss off an entire community for nothing - or do you?

I don't think they are. The EULA being in Ubuntu has to be a bug, because it was never required before and Mozilla has never had a problem with it. I'm certain it won't be in the final version. Perhaps someone compiled that on accident or something.

---

### Post by GepettoBR on 2008-09-16
I think it's been perfectly established that this isn't a bug. The bug report was just a way to bring this matter to attention. How can it be a bug if it was put there on purpose and does exactly what the people who put it there intended it to do? That would only be possible if it were a case of hijacking, and while I am against the EULA I'm not willing to go as far as saying that.

---

### Post by pony-tail on 2008-09-16
My $0.02 -
Ship Ubuntu with a Customized version of Abrowser and put Firefox in the repositories . That way those that want to use it can just install it via Synaptic or whatever method they choose . If all the distros did someting like that , The loss of market share may get them to be more inclined to negotiate - If not , just develop and advance Abrowser (as much as I hate unnecessary forking ) . Look at what happened with Beryl .

---

### Post by jlacroix on 2008-09-16
Again, just remove the EULA. It was never a problem before. If Mozilla has a problem with that, call Firefox something else. This is the easiest bug to solve in the entire database.

---

### Post by npman on 2008-09-16
> **jlacroix said:**
> Again, just remove the EULA. It was never a problem before. If Mozilla has a problem with that, call Firefox something else. This is the easiest bug to solve in the entire database.

Hey.  Now, that's an awesome idea!  Get rid of it.  If it's an issue worry about it then.

---

### Post by VON_CAPO on 2008-09-16
> **pony-tail said:**
> My $0.02 -
Ship Ubuntu with a Customized version of Abrowser and put Firefox in the repositories . That way those that want to use it can just install it via Synaptic or whatever method they choose.
I agree.
I understand the trouble is about "brand and artwork", so let's just switch them for another pretty ones. 
So, Mozilla can keep its compulsory EULA.

---

### Post by inportb on 2008-09-16
That's a very logical solution.

---

### Post by GepettoBR on 2008-09-16
Yet, one that Canonical is very unlikely to adopt.

---

### Post by inportb on 2008-09-16
Indeed; Shuttleworth has made his decision. I've made mine as well; I'm not quite ready to dump Ubuntu, but I *could* use ABrowser and ask other people to do so.

---

### Post by Nullack on 2008-09-16
> **GepettoBR said:**
> I think it's been perfectly established that this isn't a bug. The bug report was just a way to bring this matter to attention. How can it be a bug if it was put there on purpose and does exactly what the people who put it there intended it to do? That would only be possible if it were a case of hijacking, and while I am against the EULA I'm not willing to go as far as saying that.

Because bug reports are not restricted to software, they can be bugs about software requirements.

The issue cuts to the very core of what FOSS is about and what Ubuntu is about. This is why it has so much attention.

---

### Post by Nullack on 2008-09-16
> **inportb said:**
> Indeed; Shuttleworth has made his decision. I've made mine as well; I'm not quite ready to dump Ubuntu, but I *could* use ABrowser and ask other people to do so.

He has not made any decision. There is a formal process explained on the Ubuntu website that talks about how he can act in dire circumstances of deadlock. He has asked for suggestions about how to handle it, and it looks by news reports that Mozilla will probably cave in on the matter anyway.

---

### Post by High Roller on 2008-09-16
Does this mean no EULA?:

[http://blog.lizardwrangler.com/2008/09/16/firefox-without-eulas-update/](http://blog.lizardwrangler.com/2008/09/16/firefox-without-eulas-update/)
[http://groups.google.com/group/mozilla.dev.planning/browse_thread/thread/120b0b6241b74538](http://groups.google.com/group/mozilla.dev.planning/browse_thread/thread/120b0b6241b74538)

---

### Post by VON_CAPO on 2008-09-16
> **Nullack said:**
> He has not made any decision. There is a formal process explained on the Ubuntu website that talks about how he can act in dire circumstances of deadlock. He has asked for suggestions about how to handle it, and it looks by news reports that Mozilla will probably cave in on the matter anyway.

I think the following solution would be elegant and appropriate --> [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/269656/comments/388](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/269656/comments/388)

---

### Post by ronacc on 2008-09-16
> **VON_CAPO said:**
> I think the following solution would be elegant and appropriate --> [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/269656/comments/388](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/269656/comments/388)

that certainly seems like a sane and reasonable approach which means it definately isn't going to happen:lolflag:

---

### Post by inportb on 2008-09-17
> **High Roller said:**
> Does this mean no EULA?:

[http://blog.lizardwrangler.com/2008/09/16/firefox-without-eulas-update/](http://blog.lizardwrangler.com/2008/09/16/firefox-without-eulas-update/)
[http://groups.google.com/group/mozilla.dev.planning/browse_thread/thread/120b0b6241b74538](http://groups.google.com/group/mozilla.dev.planning/browse_thread/thread/120b0b6241b74538)

Hm... looks like we're getting somewhere. I think it means they're going to assert their superiority in a less intrusive fashion. I'm all for it.

---

### Post by JeevesBond on 2008-09-17
> **npman said:**
> The fact that not everyone cares about the EULA *is important* to the conversation.

I disagree, unless those people are bringing any new points to the conversation there's no need for them to say anything.

The number of people who don't care vs. those who do can be calculated by Brainstorm. And that is showing positive, despite the original being marked duplicate. Plus all the votes being merged with an -- only vaguely -- related issue that had -35 votes against it.

If the brainstorm idea is at +80 when Intrepid is still in Alpha, and barely anyone is using it, it will be a lot higher when the final version is released.

> **npman said:**
> Perhaps there are those that think that things need not be hijacked by this tempest in a teapot.

That is your definition of the situation. Once again: just because you think it unimportant doesn't mean others do too.

---

### Post by begemot. on 2008-09-17
Please take a look at "Ubuntu 8.04"'s file at **/etc/firefox-3.0/pref/firefox.js**
It's header says:
[COLOR="Blue"]// This is the Debian specific preferences file for Mozilla Firefox[/COLOR]

and it's final strings are:
[COLOR="Blue"]// Prevent EULA dialog to popup on first run[/COLOR]
pref("browser.EULA.override", true);

So what do we have, huh?!
It means, that we haven't seen EULA in Ubuntu's Firefox before only because of Debian and Canonical communities. If you delete this string or switch it's value in "true", Mozillas EULA will show up in every first time Firefox starts!
And what is going now is that Mozilla wants TO FORCE Canonical to EXCLUDE only THIS ONE STRING from Debian-specific Firefox config-file!

BUT this configuration is absolutely legal because it's just a setting of "about:config" options! It's not changing the source code or trade marks.
The result is that Mozillas harassment rising for how Canonical (or anybody else) USE Firefox, but not change it's source code or brends!

And that means Mozilla is going to make a first step to Strongly Restriction of our Freedom, despite that the source code of Firefox is open!

---

### Post by gnomeuser on 2008-09-17
> **VON_CAPO said:**
> I think the following solution would be elegant and appropriate --> [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/269656/comments/388](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/269656/comments/388)

That would solve the issue nicely and give us long term a nicely integrated solution we can patch and support.

---

### Post by Sophont on 2008-09-17
> **begemot. said:**
> The result is that Mozillas harassment rising for how Canonical (or anybody else) USE Firefox, but not change it's source code or brends!

And that means Mozilla is going to make a first step to Strongly Restriction of our Freedom, despite that the source code of Firefox is open!

"harassment", "Strongly Restriction"?

The hyperbole level reached new heights here.

If this is really done then the terrible horrible, strong restriction ends up having to make 1 extra click during a first time installation.
After that you can the browser exactly as before.

There is actually no practical difference. How many users actually want to use Firefox trademark or icons for something else? Right - nobody. How many developers might want to do so? Right - very small number - many of which might get permission to do so anyway.

Amount of time needed for accepting such a EULA? Between 1 second for most users (yet another EULA - never read'em - gone) and a few minutes for some who actually worry about them - once.

Next time you start your browser - hey - exactly as it is now.
Number of sites you suddenly cannot visit anymore because of such change? 0!

Amount $ this costs? 0

Mozilla has provided the world with the first challenger to IEs browser dominace in years and actually forced MS to re-assemble a development team to improve the worlds most used browser.

All they demand in return? The effort to download and install (not even that when it comes bundled as in Ubuntu) and now perhaps a click on a button because some of their lawyers might have pointed out some potential problems with trademark abuse or whatnot.

I guess we have different definitions for "strong restriction" and "harassment".

Everybody in this thread already invested more effort into this than the FF EULA ever will.

And I'm getting sick of all this "they are taking our rights away". This is not a fundamental right as in life, liberty or some such.
This is a generous gift by the developers of free software (such as Mozillas FF). It's *their* right to give it away or not - in any way they see fit. Their work, their decisions. People should be more grateful for such gifts and less ready to answer such generosity with knee-jerk attacks.

just my 2 cents

---

### Post by philinux on 2008-09-17
This thread is one big YYYAAAAWWWNNNN......zzzz

Back to testing.

---

### Post by VON_CAPO on 2008-09-17
> **Sophont said:**
> 
And I'm getting sick of all this "they are taking our rights away". This is not a fundamental right as in life, liberty or some such.
This is a generous gift by the developers of free software (such as Mozillas FF). It's *their* right to give it away or not - in any way they see fit. Their work, their decisions. People should be more grateful for such gifts and less ready to answer such generosity with knee-jerk attacks.

just my 2 cents
.... I am wondering. Why some people choose Linux? Why to switch to "Free Software"? Simple, because of the philosophy it implies.

I understand that some grants have been made in order to permit functionality (such as closed drivers). But, I believe this is crucial point and it must not be negotiable. Otherwise it would be a sinister precedent, opening a Pandora's box to new demands from others open source projects.

About the "generosity of the developers": In this case we are not talking about a couple of guys doing a nice job and looking for recognition, but a organisation with lawyers pushing an EULA. In the Windows world that is fine, but here Mozilla crossed the line.

---

### Post by doas777 on 2008-09-17
as much as I hate to say it, sever all ties with Mozilla. They can no longer be trusted. they have forgotten how they obtained their marketshare, and now they betray their users by buying into the lies the IP croud is trying to convince us of.

let em drown.

---

### Post by Gina on 2008-09-17
I must admit to a sense of betrayal in this :(

---

### Post by GepettoBR on 2008-09-17
> **Nullack said:**
> Because bug reports are not restricted to software, they can be bugs about software requirements.

The issue cuts to the very core of what FOSS is about and what Ubuntu is about. This is why it has so much attention.

I never denied the importance of the matter. I have stated that I am against the EULA, that I feel it opens a horrible precedent and that I'm in favor of booting Mozilla Firefox (tm) from Main, however I don't have such a broad view of the word "bug". This is a political issue, not a technical issue - even though it does bring about technical problems.

I would also like to ask anyone who feels that a fifteenth post saying "but it's just one click" would add anything to this discussion to realize that we are not debating any practical issues. The subjective implications, the precedent this EULA opens and the mindset it represents are the problems. The decision to remove Mozilla Firefox (tm) or not from the default Ubuntu install has nothing to do with an extra click - it's about the possibility of further restrictions, and about sending a message. So please cut the half-thought analysis of what you think is the whole problem and read one of the various posts in this thread that explain the other points of the issue.

---

### Post by ronacc on 2008-09-17
> **GepettoBR said:**
>  I haI don't have such a broad view of the word "bug". This is a political issue, not a technical issue - even though it does bring about technical problems.



please see bug#1

---

### Post by VON_CAPO on 2008-09-17
About this EULA and how it cripples our freedom: 
It was posted in LaunchPad a few minutes ago ---> [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/269656/comments/416](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/269656/comments/416)

> I suggest that the software in the main repository is either free, or it
is not. Free means:

0 - The freedom to run the program, for any purpose
1 - The freedom to study how the program works and adapt it to your
needs
2 - The freedom to redistribute copies so that you can help your
neighbor.
3 - The freedom to improve the program, and release your improvements to
the public so that the whole community benefits.

[B]The EULA impedes freedom 3. By using Firefox, users of free software are
forced to give up freedom 3 by agreeing that their improvements are
subject to laws that might not apply to them.[/B]

---

### Post by GepettoBR on 2008-09-17
> **ronacc said:**
> please see bug#1

I am aware of bug #1. It is also not a bug, in the strict sense of the word "bug" as applied to computers (neither in the sense as applied to insects, but I hope everyone already knew that). Bug #1 is a great declaration of intention, and I praise Mark's wit for filing it. It's still not a bug.

---

### Post by Sophont on 2008-09-17
> **GepettoBR said:**
> 
I would also like to ask anyone who feels that a fifteenth post saying "but it's just one click" would add anything to this discussion to realize that we are not debating any practical issues. 

And that's the problem. ;-)

> **GepettoBR said:**
> 
The subjective implications, the precedent this EULA opens and the mindset it represents are the problems. The decision to remove Mozilla Firefox (tm) or not from the default Ubuntu install has nothing to do with an extra click - it's about the possibility of further restrictions, and about sending a message. So please cut the half-thought analysis of what you think is the whole problem and read one of the various posts in this thread that explain the other points of the issue.

Considering the number of people who confuse trademark and copyright  and how much difference this actually makes in practice there is plenty of half-thought to go around.

And it has all to do with an extra-click - because that is the practical difference between before and after.

There is absolutely no reason to assume that Mozilla has suddenly been body-snatched by evil aliens and is about to implement a series of changes that will destroy the world of free software.
Measured in number of people actually using free software Mozilla would probably make #1 of FOSS supporters. Firefox is the reason that IE 7 and 8 exist at this time (AFAIK the IE team was desolved after IE 6 - no real competition left and the browser doesn't make money so why spend money on big improvements?). Not too long ago the world had something like 95% IE market share. Now it's roughly 70% and still going down.
Browser choice is back. Web standards are no longer something that MS just implements any way they see fit.

And all this is thanks to Mozilla. Not to belittle Opera, Safari, Konqueror, Chrome etc... But none of the rest made the dent in the market that Firefox made and that change alone made web sites more standards compliant and by that all other standard supporting browsers more compatible with web sites in the wild.

Why assume that this is the first step of a horrible downward trend?
And why get excited about it over something you yourself say is not much of a practical matter and not wait until such time it actually becomes a practical matter - something that might very wll *never* happen?

AFAIK the licence was more or less the same for a long time already - only now being made into something that you might have to click through.
A difference that might be relevant in some jurisdictions but probably irrelevant in many others as such things are often unenforcable anyway.

Nothing horrible has happened IMHO and nothing horrible is likely to follow.

Feel free not to use Firefox - luckily there are viable alternatives.
But it's still the best *default* choice (branded and all) for the vast majority of desktop users.
Users that really care about this will simply install and use another browser.

---

### Post by GepettoBR on 2008-09-17
Well, Sophont, I do feel sorry that you're willing to simply disregard all the non-practical points so rashly. For many people, Free Software carries a weight of ideology - that's even reflectd in the name "Ubuntu".

Some people do think that this is the beginning of an evil downward spiral for mozilla. That's not my case and I agree with you that it's a big exageration. I also know full well that the trademark was registered before, just not shown to every user. These are not the problems (in my take on the matter), but rather exxagerations of certain possibilities that arise form the problems. The problems, as I see them, are:

a) The precedent. If this remains an isolated incident, that's fine. But if it becomes a trend, we may be forced to accept other EULAs from other people that may not be as friendly as this one, and that would compromise one of the pillars of FOSS.

b) The subjective impact. People are told that Linux is Free software, and explained what that capital F means. Then, they see this EULA pop up, just like in Windows. Since they can't be bothered to read it, they assume it's just the same as all the other EULAs. They assume that the capital F really doesn't mean anything.

c) The fact that the EULA is totally unnecessary. Seriously, look at all the racket Mozilla has caused by being redundant. Everything they say in the EULA is already said elsewhere, and the people to whom the restrictions apply will see it there. The whole license is just a nuisance, and even though it's a minuscule nuisance its still wrong. The desert is made of grains of sand, and this is one more to add to the pile. You may think we shouldn't bother discussing this, I think Mozilla shouldn't have bothered adding it. They gain nothing.

d) I'm a really annoying perfectionist and the EULA is poorly written. You'd think there would be someone at least mildly aware of basic grammar available to write one of these things.

e) A EULA implies the obligation to accept the terms in order to even use the product. The previous license did not. That's a huge difference because Firefox is Ubuntu's default browser. If it weren't, I wouldn't care about this point, but the current issue translates to "accept the terms or be left without a web browser". The fact that the terms are bland and another browser can be easily installed via Synaptic/apt-get/Add-remove doesn't change the fact that it's a forced choice, and that sort of agression should be avoided.

This situation will probably resolve itself nicely and everyone will be content. When it does, I'd rather have spoken up. If I suddenly saw a Firefox EULA in front of me, I'd do a quick read-through and click it away without further fuss, but when there's a chance to tell Mozilla how pointless it is before they do it and piss a bunch of people off, then great. The original EULA with which the bug was filed had several problems, and I would not continue to use Firefox if it meant being bound by that license. The new one is good enough, but that's just because it's useless.

P.S.: I did not mean to demerit what Firefox has accomplished in terms of market share, web standards and related issues. But past rights do not grant leeway for present wrongs. A hero who kills a baby still killed a baby (yes I love extreme examples).

---

### Post by Sophont on 2008-09-17
> **VON_CAPO said:**
> About this EULA and how it cripples our freedom: 
It was posted in LaunchPad a few minutes ago ---> [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/269656/comments/416](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/269656/comments/416)

3 - The freedom to improve the program, and release your improvements to
the public so that the whole community benefits.

The EULA impedes freedom 3. By using Firefox, users of free software are
forced to give up freedom 3 by agreeing that their improvements are
subject to laws that might not apply to them.


How?

How does the having to push an ok button restrict this freedom (that was and still is granted by Mozilla and an uncounted number of outside developers)?

AFAIK you are still free to improve Firefox.
AFAIK Mozilla is still happy about contributions.

You are still free to fork if you want to.
We already have Iceweasel which is Firefox with the branding removed.

The only freedom you are asked to give up is a freedom you never had - using the branding of Firefox in a way that Mozilla doesn't agree with.

The whole EULA thing is a mess to begin with. No single document can handle the differences between the jurisictions. OK button or not much of it will be unenforcable in large parts of the world anyway.

I think this all goes back to US trademark law that (AFAIK - IANAL) that requires the owner of a trademark to defend it or loose ot and I bet a lawyer pointed out some potential future problem for Mozilla of they don't at least try to go through the motions of defending their brand.

None of this has anything to do with what sites you can browse to or what you do with the source code as long as you don't use the name Firefox or the icon without permission. Considering that none of us want - say - a spammer *legally* distribute altered versions of Firefox caring about what happens with the brand makes sense to me.

I'd of course would prefer not to have to click that button - but if that is felt to be necessary by Mozilla to protect their rights on the branding than it's a very tiny and mostly irrelevant price to pay in my book.

Nobody has so far presented a credible argument that this means that every single project will soon have EULA OK buttons on install.
I don't see (for example) Pidgin or Gnome-Do suddenly seeing a similar need to protect their brands by similar means.

The sky is not falling down.

---

### Post by GepettoBR on 2008-09-17
Sophont, you're missing the point entirely. When did anyone say that this will force others into creating EULAs? Nowhere, that's where.

If Canonical accepts this EULA, it creats a precedent. IF anyone else decides to impose similar or worse restrictions (and the EULA **is** a restriction - if nothing else it restricts Canonical's right of omitting it) there is a greater chance that Canonical will cave if they have caved before. Precedents are arguments. The USA legal system, just for sake of example, is based on precedents: previous trials of similar matters are as binding as written law.

The reason no one has presented a credible argument that this EULA will necessarily spawn others is because there is none, sicne this is an absurd statement. It's also a very poor choice of a straw man to burn. Precedents are precedents regardless of whether or not anyone takes advantage of them. They are inherently meaningful and stir up the possibility that others will act alike. This is what we want to avoid.

---

### Post by Sophont on 2008-09-17
> **GepettoBR said:**
> Well, Sophont, I do feel sorry that you're willing to simply disregard all the non-practical points so rashly. For many people, Free Software carries a weight of ideology - that's even reflectd in the name "Ubuntu".

And you can count me amongst the fans of that ideology.
But that's my whole point - my freedoms (even if I were to actually work on FF code) have not been restricted in any meaningful way that you or me would ever notice in practice. If you believe otherwise please present a realistic example of what I could do before and now cannot legally do with the source.

> **GepettoBR said:**
> Some people do think that this is the beginning of an evil downward spiral for mozilla.

Obviously.
Yet without any solid reason. Past behaviour by Mozilla would argue against evil tendencies.
I also think it's quite insulting to the nice people at Mozilla to just assume they have evil plans behind their backs without the slightest shred of evidence.

> **GepettoBR said:**
> a) The precedent. If this remains an isolated incident, that's fine. But if it becomes a trend, we may be forced to accept other EULAs from other people that may not be as friendly as this one, and that would compromise one of the pillars of FOSS.

How?
Realistically how would this become a trend? There's pretty few projects big and universal enough to every have to worry about such branding issues or how that might be abused. The other big project that comes to mind is OpenOffice. But a browser by it's nature as portal to the web is in a special position to begin with. It's become a de facto platform and Google is working hard to make the browser into the next big OS (prior OS like windows ir Linux get reduced to hardware abstraction layers the more that apps are web based).

> **GepettoBR said:**
> 
b) The subjective impact. People are told that Linux is Free software, and explained what that capital F means. Then, they see this EULA pop up, just like in Windows. Since they can't be bothered to read it, they assume it's just the same as all the other EULAs. They assume that the capital F really doesn't mean anything.

The minority of people who passionately care about this know how to install alternative browsers.
The majority of future users care mostly about free-as-in-beer and better security or perhaps cool Compiz cube effects - not whether the Firefox branding is restricted to authorized uses for a source 99.999% of all users will never compile - let alone change.

> **GepettoBR said:**
> c) The fact that the EULA is totally unnecessary. Seriously, look at all the racket Mozilla has caused by being redundant. Everything they say in the EULA is already said elsewhere, and the people to whom the restrictions apply will see it there. The whole license is just a nuisance, and even though it's a minuscule nuisance its still wrong. The desert is made of grains of sand, and this is one more to add to the pile. You may think we shouldn't bother discussing this, I think Mozilla shouldn't have bothered adding it. They gain nothing.

You know this how? You are a lawyer familar with US and international trademark law? Case law that might apply?
I'm not and I assume neither are most (probaly all) the fine folks posting here.

Mozilla insists they need this we can draw one of these conclusions:
1) They are stupid
2) They are evil
3) They have their reasons based on what a lawyer said

Not having enough knowledge myself I trust that it is 3 - mostly because 1 and 2 are not very likely. They might eventually be wrong about 3) - law can be difficult and more so with software, trademarks, diverse jurisdictions and whether any of this is actually enforcable (if ever relevant) - but for the time being assuming they have good enough reasons to require this is the most reasonable assumption IMHO.

> **GepettoBR said:**
> d) I'm a really annoying perfectionist and the EULA is poorly written. You'd think there would be someone at least mildly aware of basic grammar available to write one of these things.

Shrug. :-)

> **GepettoBR said:**
> e) A EULA implies the obligation to accept the terms in order to even use the product. The previous license did not. That's a huge difference because Firefox is Ubuntu's default browser. If it weren't, I wouldn't care about this point, but the current issue translates to "accept the terms or be left without a web browser". The fact that the terms are bland and another browser can be easily installed via Synaptic/apt-get/Add-remove doesn't change the fact that it's a forced choice, and that sort of agression should be avoided.

"aggression" - wow.

> **GepettoBR said:**
> This situation will probably resolve itself nicely and everyone will be content. When it does, I'd rather have spoken up. If I suddenly saw a Firefox EULA in front of me, I'd do a quick read-through and click it away without further fuss, but when there's a chance to tell Mozilla how pointless it is before they do it and piss a bunch of people off, then great. The original EULA with which the bug was filed had several problems, and I would not continue to use Firefox if it meant being bound by that license. The new one is good enough, but that's just because it's useless.

:-)

> **GepettoBR said:**
> P.S.: I did not mean to demerit what Firefox has accomplished in terms of market share, web standards and related issues. But past rights do not grant leeway for present wrongs. A hero who kills a baby still killed a baby (yes I love extreme examples).

Ouch - dead babies already. Can't be long before the magical word to end any thread appears. ;-)
You marked it as extreme yourself, but it actually is an example with no relation to the matter at hand.

And I disagree. Past begaviour is important in judging current decisions.
If a generous and well meaning bunch of people provide a great product for a very low price of 0 $$ to the world then this *should* make a difference in evaluating what current actions mean.

I would be much readier in assuming sinister or stupid behaviour on Mozillas part of they already had a history of such.

Reasonable - don't you agree?

---

### Post by Sophont on 2008-09-17
> **GepettoBR said:**
> Sophont, you're missing the point entirely. When did anyone say that this will force others into creating EULAs? Nowhere, that's where.

Yes, AFAIR, *nobody* (me included) said "this will force others into creating EULAs".

You mentioned burning straw man? ;-)

This is getting ever more silly. :-)

---

### Post by Penetration Testing on 2008-09-17
It's not that difficult an issue. If Firefox want to put things on there to protect their trademark that's their issue. If you want to use another browser it's yours.

---

### Post by VON_CAPO on 2008-09-17
> **Sophont said:**
> How?
We already have Iceweasel which is Firefox with the branding removed.
Yeap, my next browser of choice for sure, or perhaps Epiphany?.

Also I read your precedent post and you are talking about the "OK" button; that is not the issue at all (It is just the associated symptom ;-)) 

I think if the Mozilla Corporation can push terms on Ubuntu about EULAs and related garbage, soon we will become something similar to Linspire or Xandros (making concessions in every direction and loosing their roots) :rolleyes:  

So, it is up Canonical the next step. I hope they will choose a wise solution.

---

### Post by zolookas on 2008-09-17
```
**[Shuttleworth man heads to Mozilla]("http://www.tectonic.co.za/?p=3091")**
```

So I think this fact shows that nobody is going to remove firefox from default 
installation. Case closed.

---

### Post by Peter Frank on 2008-09-17
I'd like to see the Ubuntu installer asking the user whether to use Firefox or Iceweasel, so both parties will be pleased.

---

### Post by Sophont on 2008-09-17
> **zolookas said:**
> ```
**[Shuttleworth man heads to Mozilla]("http://www.tectonic.co.za/?p=3091")**
```

So I think this fact shows that nobody is going to remove firefox from default 
installation. Case closed.

That that guy managing philanthropic projects switches from one company to another organization is very unlikely to affect the decision whether Firefox is the default browser for Ubuntu.

That FF is the *default* browser is a rational decision based on what most users would want. Look at FF market share. For new users coming from windows it helps a lot that they can continue to use familiar and trusted software like OO and FF (plus TB, Gimp, etc...). Iceweasel would work as well from a technical perspective of course (being the exact same thing feature-wise as FF after all) - but would not be recognized by noobs.

Using Iceweasel or Epiphany as *default* browser would please a small number of users and confuse/annoy a large number.
Continue using FF as *default* browser (with EULA OK button required) might make a few people switch to Iceweasel/Epiphany (who are very welcome to do so) - but satisfy the vast majority of current and potential users.

No other reasons needed.

---

### Post by Sophont on 2008-09-17
> **Peter Frank said:**
> I'd like to see the Ubuntu installer asking the user whether to use Firefox or Iceweasel, so both parties will be pleased.

Good solution per se.
But AFAIK space is already very tight on the CD - they have to kick out packages for anything new they want to put in - so there's probably no room for that option. And the whole idea of Ubuntu CD is to have a good default setup that's right for most users and doesn't ask many questions.

Also it's trivial to uninstall FF and install alternative browser after setup and only takes a minute or so (ok - more if you don't have broadband - but then you're in trouble anyway due to all the other packages that get drafted after setup).

The people passionate about this EULA affair are unlikely to be noobs who can't find alternate packages and install them.

Thinking about this - those who demand that FF gets replaced as default browser are actually trying to restrict the freedom of the majority of users to get FF out-of-the-box. ;-)

And yes - I'm pretty sure that the majority of users does not care about the fine print of a EULA that they click through and what it entails about using the branded stuff in a forked browser some developer might do. Most people will never know this debate ever happened.

---

### Post by VON_CAPO on 2008-09-17
> **Sophont said:**
> Good solution per se.
But AFAIK space is already very tight on the CD - they have to kick out packages for anything new they want to put in - so there's probably no room for that option. And the whole idea of Ubuntu CD is to have a good default setup that's right for most users and doesn't ask many questions.

Also it's trivial to uninstall FF and install alternative browser after setup and only takes a minute or so (ok - more if you don't have broadband - but then you're in trouble anyway due to all the other packages that get drafted after setup).

The people passionate about this EULA affair are unlikely to be noobs who can't find alternate packages and install them.

Thinking about this - those who demand that FF gets replaced as default browser are actually trying to restrict the freedom of the majority of users to get FF out-of-the-box. ;-)

And yes - I'm pretty sure that the majority of users does not care about the fine print of a EULA that they click through and what it entails about using the branded stuff in a forked browser some developer might do. Most people will never know this debate ever happened.

Actually I believe you are right about to use the Fi®ef©x brand, but because the matter started in LaunchPad where Ubuntu core developers gather and it has a fork here in the section "Development & Programming" the subject is not trivial at all.

This discussion has deep implications, do not forget that many Ubuntu developers have Debian roots, so to be a purist is not the exception but the norm. 

The M©zilla EULA is in collision course with the Ubuntu philosophy to ship Free Software by default. 
So, to ask to drop Fi®ef©x is logical and necessary.

---

### Post by Gina on 2008-09-17
Yes, I agree, unfortunately the EULA flies right in the face of Ubuntu's principles.

---

### Post by plun on 2008-09-17
> **VON_CAPO said:**
> A
The Mozilla EULA is in collision course with the Ubuntu philosophy to ship Free Software by default. 
So, to ask to drop Fi®ef©x is logical.

Nope... its not logical, its more logical to remove this EULA.

Then its about making a distribution which a "non-nerd" can use  !!!

Maybe its more important to fix bugs then to spill energy about this ?
[B]
[http://bugs.debian.org/release-critical/](http://bugs.debian.org/release-critical/)[/B]

.

---

### Post by Gina on 2008-09-17
Of course, it's the EULA we want removed rather than Firefox itself.  I find myself "between a rock and a hard place" here.  I feel strongly for the FOSS principles but also that to remove Firefox would not be good at all.

---

### Post by MacUntu on 2008-09-17
My thought: I don't give a damn. Not very contributive but true and I guess true for a lot of users.

---

### Post by Sophont on 2008-09-17
> **VON_CAPO said:**
> Actually I believe you are right about to use the Fi®ef©x brand, but because the matter started in LaunchPad where Ubuntu core developers gather and it has a fork here in the section "Development & Programming" the subject is not trivial at all.

This discussion has deep implications, do not forget that many Ubuntu developers have Debian roots, so to be a purist is not the exception but the norm. 

The M©zilla EULA is in collision course with the Ubuntu philosophy to ship Free Software by default. 
So, to ask to drop Fi®ef©x is logical and necessary.

It's not necessary at all.

Debian and Ubuntu - while very closely related have a different focus. Debian is more server centric and purist. Ubuntu more desktop centric and pragmatic (support proprietary drivers to get good  3D support for example).

Firefox is still free - even with the EULA. You still get the source, still can change it, still free of charge.

I'm sure lawyers can have lots of fun with it - but for the rest of the real world this whole thing is blown out of all proportion. I have yet to see anything that actually affects use (except for that one silly click) or even development. Not a single realistic example has been presented in these 20 pages where the possible change to having to accept the EULA by clicking a button actually makes a bit of difference.

---

### Post by Merk42 on 2008-09-17
> **VON_CAPO said:**
> Fi®ef©x
Give me a break, please don't tell me this will catch on.

---

### Post by ronacc on 2008-09-17
> **Sophont said:**
> 

I'm sure lawyers can have lots of fun with it - but for the rest of the real world this whole thing is blown out of all proportion. I have yet to see anything that actually affects use (except for that one silly click) or even development. Not a single realistic example has been presented in these 20 pages where the possible change to having to accept the EULA by clicking a button actually makes a bit of difference.

a few points .
1 read the topic , it asks for our thoughts .
2 as the post you yourself quoted in your post says it is a matter of philosophy primarily not use .
3 yes the lawyers can have a lot of fun with it , something we would greatly like to avoid .
4 lots of popular programs are free (as in beer) but not free (as in speach) and are therefore not included as defaults ,the very existance of 
an EULA calls FF into question (see point 3 ).
5 nobody has sugested that anyone else not use firefox though they have said they themselves would not ,a personal decission .
6 if we did not freely and openly discuss things like this what kind of comunity would we have .

---

### Post by exploder on 2008-09-17
No need to go on about the EULA. Have a look.

[http://practical-tech.com/operating-system/mozilla-to-remove-firefox-eula/](http://practical-tech.com/operating-system/mozilla-to-remove-firefox-eula/)

---

### Post by doas777 on 2008-09-17
> **exploder said:**
> No need to go on about the EULA. Have a look.

[http://practical-tech.com/operating-system/mozilla-to-remove-firefox-eula/](http://practical-tech.com/operating-system/mozilla-to-remove-firefox-eula/)

Seems like theres still work to be done, but at least they are hearing, and begin to understand the problem at hand. It would be nice if they remove it (or place it somewhere else). I guess we'll see tommorow.

have fun

---

### Post by VON_CAPO on 2008-09-17
I would like to listen to Richard Stallman's opinion. I would be very interesting indeed.

---

### Post by GepettoBR on 2008-09-17
@Sophont:

I'll admit I got carried away with that post (I do like a good argument, that's for sure) and I agree with you that this is being blown out of proportion. But I still don't think it's something to be shrugged off. Even though the discussion has moved past this and Mozilla has dropped the EULA, I'll indulge myself and reply to your very well-weighed post, just because I think it'd be a shame not to.

> **Sophont said:**
> If you believe otherwise please present a realistic example of what I could do before and now cannot legally do with the source.

Im not 100% certain of any concrete examples, I'm just bugged by the idea. I do think, however, that a thin rebranding like Ghostfox (which apart from the obviously similar name just painted the logo green and called it a day) is no longer admissible.

> **Sophont said:**
> 
Obviously.
Yet without any solid reason. Past behaviour by Mozilla would argue against evil tendencies.
I also think it's quite insulting to the nice people at Mozilla to just assume they have evil plans behind their backs without the slightest shred of evidence.

Hey, I say it's always best to be suspicious. Besides, the merits you're talking about have much more to do with the developers than with the suits. This issue pertains to the suits.
> **Sophont said:**
> 
How?
Realistically how would this become a trend? There's pretty few projects big and universal enough to every have to worry about such branding issues or how that might be abused. The other big project that comes to mind is OpenOffice. But a browser by it's nature as portal to the web is in a special position to begin with. It's become a de facto platform and Google is working hard to make the browser into the next big OS (prior OS like windows ir Linux get reduced to hardware abstraction layers the more that apps are web based).

How about the kernel? Or the desktop environments? X? These packages are hundreds of times more relevant than a silly little web browser, and regardless of any web-application tendencies they're still necessary. What worries me isn't the specifics of branding issues (though I would miss that cute little foot if I had to switch to an unbranded GNOME) but the general realm of possibilities brought up by an EULA.
> **Sophont said:**
> 
The minority of people who passionately care about this know how to install alternative browsers.
The majority of future users care mostly about free-as-in-beer and better security or perhaps cool Compiz cube effects - not whether the Firefox branding is restricted to authorized uses for a source 99.999% of all users will never compile - let alone change.

That's exactly my point. The majority of future users should at the very least be vaguely aware that it's not about free-as-in-beer. Ideally, they'd all understand the free-as-in-speech concept, but that's asking a little too much. Presenting this EULA to them will default them back to the proprietary Windows/Mac mindset and they'll remain oblivious.
> **Sophont said:**
> 
You know this how? You are a lawyer familar with US and international trademark law? Case law that might apply?
I'm not and I assume neither are most (probaly all) the fine folks posting here.

Sadly I'm not a lawyer and neither do I specialize in US law. Im a Law student in Brazil and I take quite a liking to International law. This is still irrelevant to the case in point. They gain nothing from the EULA because it is redundant. The same terms are stated much more clearly elsewhere. It's like writing "This side up" twelve times on the lid of a box. The extra eleven are just a waste of ink.
> **Sophont said:**
> 
Mozilla insists they need this we can draw one of these conclusions:
1) They are stupid
2) They are evil
3) They have their reasons based on what a lawyer said

Not having enough knowledge myself I trust that it is 3 - mostly because 1 and 2 are not very likely. They might eventually be wrong about 3) - law can be difficult and more so with software, trademarks, diverse jurisdictions and whether any of this is actually enforcable (if ever relevant) - but for the time being assuming they have good enough reasons to require this is the most reasonable assumption IMHO.
My motto: "Hope for the best, but prepare for the worst". Reasonable assumptions shouldn't prevent us from considering the unreasonable ones.> **Sophont said:**
> 
"aggression" - wow.
It *is* an aggression. Not by Mozilla, but by Ubuntu if the EULA-having-default-browser scenario became reality. Canonical would be telling you that if you want to browse the web straight out of the box, like you would expect form a modern OS, you need to play by the rules of a third party. Unless there were a warning before installation, it's an aggression. You install the OS and you're getting ready to fire up the browser when suddenly you get slapped in the face by a contract (and here I'm using the broad meaning of the term "contract"). "Why didn't this happen in the LiveCD? Why wasn't I warned?" It's certainly not deeply offensive - but it is a bit aggressive, don't you think?> **Sophont said:**
> 
Ouch - dead babies already. Can't be long before the magical word to end any thread appears. ;-)Forgive me for being dense, but I don't know what word that is. It is a very out-of-proportion example, but really it was just the first thing that came into my mind (I was actually thinking about a Paladin in a D&D campaign who accidentally killed a baby).> **Sophont said:**
> 
You marked it as extreme yourself, but it actually is an example with no relation to the matter at hand.Of course it is. Being a hero, like Mozilla has certainly been, does not give it carte blanche to do bad things.> **Sophont said:**
> And I disagree. Past begaviour is important in judging current decisions.
If a generous and well meaning bunch of people provide a great product for a very low price of 0 $$ to the world then this *should* make a difference in evaluating what current actions mean.

I would be much readier in assuming sinister or stupid behaviour on Mozillas part of they already had a history of such.

Reasonable - don't you agree? I agree it's much more reasonable, but like I said before, the praises you sing have to do with the developers more than the money managers - of course it has to do with them as well, since they have consciously decided to keep Firefox free and open, but none of that would have mattered if the browser wasn't lighter, safer and faster than the prime competition. After all, why would the average computer user choose a free inferior product that he/she has to download him/herself over a free superior product that came bundled with Windows? I've also said what I think about reasonable assumptions.

It's been great fun so far, mate! Thanks for helping me dust off the old bickering cells :lol:

---

### Post by aysiu on 2008-09-18
As there is a new development with this issue *and* as this discussion has gotten extremely long, I'm closing this thread.

It'll pick up again in [ Firefox EULA was "giant error" -- Says Mozilla](http://ubuntuforums.org/showthread.php?p=5813286#post5813286)

---

