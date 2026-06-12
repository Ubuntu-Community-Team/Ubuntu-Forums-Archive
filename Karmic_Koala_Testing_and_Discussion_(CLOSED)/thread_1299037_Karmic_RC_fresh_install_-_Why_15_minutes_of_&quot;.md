---
title: "Karmic RC fresh install - Why 15 minutes of &quot;Language Pack&quot; downloads?"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-23
Is this a RC-issue,  or will users expect a near half-hour install?

---

### Post by Merk42 on 2009-10-23
Bumping this thread because I'd love to know too.
I was reading on another forum someone maybe trying Ubuntu or going to XP.  I was all set to time how quickly it was to install since I recall the alphas and beta being quick. Then it just sat there installing language packs, so I stopped timing it when it reached around a half hour.

---

### Post by viper8 on 2009-10-23
Yeah I had the same issue last night.  It wouldn't be so bad if there was a way to choose the mirror.  It was downloading directly from some ubuntu.com server so I'm sure that's why it was slower.

---

### Post by mfox on 2009-10-23
Actually, you can choose the mirror if you install from the live image.  Choose System -> Administration -> Software Sources.  If you are from North America, the default seems to be a U.S. source.  Download speeds from it are slow, as they are from the Canadian source which sometimes is the default I get (being from Canada).  I get my best results choosing a mirror from southern or central Europe, regardless of time of day.  I chose a mirror from Spain for the RC install on my Mac at work; download was much faster than from the U.S. mirror used in the installation on my home Mac.

---

### Post by viper8 on 2009-10-23
> **mfox said:**
> Actually, you can choose the mirror if you install from the live image.  Choose System -> Administration -> Software Sources.  If you are from North America, the default seems to be a U.S. source.  Download speeds from it are slow, as they are from the Canadian source which sometimes is the default I get (being from Canada).  I get my best results choosing a mirror from southern or central Europe, regardless of time of day.  I chose a mirror from Spain for the RC install on my Mac at work; download was much faster than from the U.S. mirror used in the installation on my home Mac.

Hmmm, yeah I installed using the live image.  I chose the MIT.EDU mirror, and while it was downloading the lang packs I ran netstat --inet and realized it wasn't pulling data from MIT :confused:  So I just walked away for a bit while it downloaded...no biggie, but I imagine that on release day it might impact more people.

---

### Post by Merk42 on 2009-10-23
Yeah downloading the CD is bad enough of release day (luckily I get around it via torrent), but I wouldn't want to still have to suffer with a large amount of traffic from the language packs.

Also, while changing a mirror is all well and good, what of those that just want to go straight to installing, as in not the LiveCD?

Also, why was this not in any of the alphas or betas?

Actually, why is it installing them at all?

---

### Post by jetpeach on 2009-10-23
yeah, this is really annoying for me. i thought i could get it installed in 15-30 minutes, but not i'm late and have to leave and it still says 25 minutes to download these packs. can't these be included in the CD? at least the most basic ones that are default?

ug, frustrating... now the time says 30 minutes! and i'm guessing on release day if this hasn't changed, the servers will probably just die... and a lot of people will be frustrated that there installs won't install.

---

### Post by ranch hand on 2009-10-23
There is only so much room on the live CD.  When it is decided that we need a slide show, something has to give.

There is a LiveDVD 4Gb worth available too.  I am not sure what is on it but I would like to know.  I may get one after the Final release rush settles down.

Mandriva 2009-9 comes that way and has Gnome, KDE and Lxde on it.  You can install one or all of them.  I think it is kind of neat.  I went with all of them on one install and the other is just Gnome.

---

### Post by Merk42 on 2009-10-23
> **ranch hand said:**
> There is only so much room on the live CD.  When it is decided that we need a slide show, something has to give.

Oh please, you seriously think the slide show takes up as much space as multiple language packs?

Besides, I think the main point is why did this all of a sudden happen in the RC?  If it was really a case of not enough room because of the slideshow you hate so much, why didn't we see this in the alphas and betas?

---

### Post by SuperSonic4 on 2009-10-23
I think it's a fault in *buntu. It really wouldn't be that hard to pick your locale from a file and then it updates any you've specified.

It's pretty pointless because when I installed Kubuntu I had to install the British language pack

---

### Post by xebian on 2009-10-23
Exactly.  Why install/generate other locales when you only have one? what's the point of UK/AUS/CAD, etc when you only need US?

---

### Post by 23meg on 2009-10-23
[QUOTE=Merk42]Besides, I think the main point is why did this all of a sudden happen in the RC?[/QUOTE]

Because the language pack translations deadline coincides with the RC, which means that the language packs hit the package archive just around this date.

---

### Post by bennachie on 2009-10-23
OK, that's very helpful - can we assume that the updated language packs will be included in the LiveCDs for the release version, so that this painful process will be a one-off nuisance only for RC testers?

---

### Post by ranch hand on 2009-10-23
> **Merk42 said:**
> Oh please, you seriously think the slide show takes up as much space as multiple language packs?

Besides, I think the main point is why did this all of a sudden happen in the RC?  If it was really a case of not enough room because of the slideshow you hate so much, why didn't we see this in the alphas and betas?
Yes, I do.  At least when the CD is as close to full as it has been for the last few releases.  You can only compress so much.

We also get more images with every release.  Check your files and see the difference in size between images and text.  Code is text.

Think of the "huge" file that is downloaded when you get a new kernel.  If you have a good camera and keep print quality files of photos, you will see that 5 to 8 photos will equal the kernal that runs your box in space taken.

There are 7 images in the /usr/share/images/xsplash folder for the background.  the smallest is 123Kb and the largest 2.4Mb.  This adds up.

And, back to your point, like the slide show or not, it is images and images take up a lot of room.

The language packs are text and will, by and large, also download faster than will images.

It could well be too, that in the next week, there will be revision of the CD to take the image pack.  I do not know why, for instance we need 7 images in the xsplash folder.

My point was not to defame the wonderful slide show but to point out that there is a limit to the amount of data that you can put on a CD.  As I pointed out Mandriva has gone to the DVD.  Because of how they market their product, they have had more images than ubuntu has.  The DVD is the answer.

I do not know if it is a good answer, but if there is a demand for more images there has got to be more room.  You can only pack so much mud in one ***hole, as the saying goes.

---

### Post by Merk42 on 2009-10-23
Well see now you're also including xsplash in that.

Your overall comment
> **ranch hand said:**
> I do not know if it is a good answer, but if there is a demand for more images there has got to be more room.  You can only pack so much mud in one ***hole, as the saying goes.
I do agree with.

I wonder what the size difference will be for GNOME 3 vs 2, though that's a year away.


Back on topic, will the long language pack download not happen with the actual release version of 9.10?

---

### Post by ranch hand on 2009-10-23
I haven't a clue.  If they go with the DVD they better get some more BIG servers, that bugger is a 4Gb download (Mandriva2009-1 is 4.2Gb).  As slow as the servers are now that many downloads (like the CD numbers/hr connecting) the poor bugger be over whelmed.

They would have to cut out something that is in ISO for no real good reason.  The install works and the OS works after reboot so you can get the language support.  They may have such a critter in mind.  They may not have one.  I would like to know too.  Be great if they could.

If you get Debian complete it is on several CDs.  All you need is the first disk.  The system works, you can download the rest direct instead of burning a bunch of cds.  I like the DVD better than a bunch of CDs.

---

### Post by Keyper7 on 2009-10-23
> **Merk42 said:**
> I wonder what the size difference will be for GNOME 3 vs 2, though that's a year away.

Since one of the points of Gnome 3 is cleaning up Gtk, I'm quite optimistic about that.

---

### Post by emarkay on 2009-10-24
So is it a bug or a feature?

If it's a feature, something ELSE has to go because this is **UNACCEPTABLE**! (bolded and shouted)

If it's a bug, I'll file it on confirmation it is not intended, or that it is intended, then it needs to be returned to a prior state.

---

### Post by chenhaw on 2009-10-24
installing the RC now.
when i saw there is no mirror scan, i was quite happy. but it ends up spending more time downloading language pack.
is there anyway like to bypass the language pack installation to speed up the installation process?

---

### Post by ranch hand on 2009-10-24
Hit skip in install when it comes up for the language pack.

---

### Post by vishalrao on 2009-10-25
my quick workaround is to kill network (unplug cable, turn off wifi whatever) during install and it goes through in 5 minutes!

people have been complaining (mailing list, bugs) for many releases now but so far nothing has been done...

[lpbug]294523[/lpbug]
[lpbug]172879[/lpbug]

Related post: [http://ubuntuforums.org/showthread.php?t=1195557](http://ubuntuforums.org/showthread.php?t=1195557)

(there have been others too)

---

### Post by 23meg on 2009-10-25
[QUOTE=ranch hand]There is only so much room on the live CD. When it is decided that we need a slide show, something has to give.[/QUOTE]

1) We haven't had most language packs on the desktop CD for a long time; it's not specific to Karmic.

2) The slideshow isn't all images; it's HTML and uses WebKit (check out how you can actually select and copy the text by holding and dragging with your mouse button), and the only images are the images on the bottom left and the bullet icons. It actually takes about 500KB of space, about half of which is translations.

---

### Post by 23meg on 2009-10-25
I just downloaded an RC image to check out what the fuss is about. 

I started installation with an active network connection. Around 80% into the installation process, when the network-related bits came up, a "Skip" button appeared. 

I clicked it, and it skipped downloading the updates and language packs. The installation finished without a network-related delay, even though my network connection was working, and took fifteen minutes in a virtual machine.

My conclusion: I'm definitely living in an alternate reality where it's possible to skip installing the updates and language packs during installation. There's no other explanation.

---

### Post by JillSwift on 2009-10-25
> **23meg said:**
> I just downloaded an RC image to check out what the fuss is about. 

I started installation with an active network connection. Around 80% into the installation process, when the network-related bits came up, a "Skip" button appeared. 

I clicked it, and it skipped downloading the updates and language packs. The installation finished without a network-related delay, even though my network connection was working, and took fifteen minutes in a virtual machine.

My conclusion: I'm definitely living in an alternate reality where it's possible to skip installing the updates and language packs during installation. There's no other explanation.
Ooohh. Bad day today, QA dude? All bristly and grumpy?


Given Ubuntu's target audience, you may want to consider at least spending a few bytes on a string for that dialog letting the user know that skipping the language pack downloads won't leave you with a system that has only dialog tags. Better still, give the user the option first with a yes/no dialog that says "Would you like to download extra language packs?"

I think that would be good for the first time Ubuntu user, don't you?

I hope your day goes better, so you don't have to snap at folks. Rrrrrouph!

---

### Post by 23meg on 2009-10-25
> **JillSwift said:**
> Ooohh. Bad day today, QA dude? All bristly and grumpy?

Much less so than the folks shouting around in all caps, whom you don't seem to mind.

> **JillSwift said:**
> Given Ubuntu's target audience, you may want to consider at least spending a few bytes on a string for that dialog letting the user know that skipping the language pack downloads won't leave you with a system that has only dialog tags. 

Is that an actual, known issue? If it is, what is the bug number?

If a "Skip" button is displayed *at all*, that should mean that pressing it is safe. If it isn't, we shouldn't be offering it in the first place. Displaying "This won't break your system, don't worry" dialogs is not a solution. If there are bugs with skipping certain components, the solution is to address them.

> **JillSwift said:**
> Better still, give the user the option first with a yes/no dialog that says "Would you like to download extra language packs?"

I think that would be good for the first time Ubuntu user, don't you?


No, I don't. What I think would be good for a first time Ubuntu user is downloading only the relevant language packs to the language they selected at the beginning of the installation, without having to dismiss one more redundant question that they aren't interested in answering.

> **JillSwift said:**
> I hope your day goes better, so you don't have to snap at folks. Rrrrrouph!

I wish you the same.

---

### Post by JillSwift on 2009-10-25
> **23meg said:**
> Much less so than the folks shouting around in all caps, whom you don't seem to mind.I don't. Why do you?


> **23meg said:**
> Is that an actual, known issue? If it is, what is the bug number?

If a "Skip" button is displayed *at all*, that should mean that pressing it is safe. If it isn't, we shouldn't be offering it in the first place. Displaying "This won't break your system, don't worry" dialogs is not a solution. If there are bugs with skipping certain components, the solution is to address them.Of course, my dear slayer of straw men, I'm talking about usability issues for folks unfamiliar with such things. It's not a "bug". It works as designed. The design leaves a small something to be desired.


> **23meg said:**
> No, I don't. What I think would be good for a first time Ubuntu user is downloading only the relevant language packs to the language they selected at the beginning of the installation, without having to dismiss one more redundant question that they aren't interested in answering.Which is what's happening anyway. So I'm not sure you've understood the problem.


> **23meg said:**
>  I wish you the same.But I'm having a *good* day.

---

### Post by NCLI on 2009-10-25
People, this is not a new problem. Except for people using US English, you've *always *had to download the language packs after installation, and that wasn't exactly user friendly if you don't understand English. 

This solution is much more noob-friendly, and once the server load goes back to normal, it will not take long.

---

### Post by ranch hand on 2009-10-25
> **23meg said:**
> I just downloaded an RC image to check out what the fuss is about. 

I started installation with an active network connection. Around 80% into the installation process, when the network-related bits came up, a "Skip" button appeared. 

I clicked it, and it skipped downloading the updates and language packs. The installation finished without a network-related delay, even though my network connection was working, and took fifteen minutes in a virtual machine.

My conclusion: I'm definitely living in an alternate reality where it's possible to skip installing the updates and language packs during installation. There's no other explanation.
I love it.  I have the feeling that I am in an alternate reality often.

Thank you for your information on the slide show.  Real interesting.

Thanks also for your months of  putting up with us.  I hope you will be riding herd on the 10.04 testing forum.  If not, we will miss you.

---

### Post by Keyper7 on 2009-10-25
Isn't this only about server load? I did notice a longer time than usual when I installed the RC, but the stage of downloading language packs is something that already existed since... I don't know when, but Karmic is definitely not the first release doing that.

---

### Post by 23meg on 2009-10-25
> **JillSwift said:**
> I don't. Why do you?

Because I happen to moderate this forum, and people shouting around usually doesn't make for good discussion.

And sorry, I won't use the word "fuss" again; that was so rude of me.

[QUOTE=JillSwift]Of course, my dear slayer of straw men, I'm talking about usability issues for folks unfamiliar with such things. It's not a "bug". It works as designed. The design leaves a small something to be desired.[/QUOTE]

I don't see the "usability issue" where a button is self-explanatory, safe to click, and works as intended, and I don't agree with prefacing such a button with something in the lines of "This button is safe to click". Feel free to disagree (and file a wishlist bug), but there are no straw men here.

[QUOTE=JillSwift]Which is what's happening anyway. So I'm not sure you've understood the problem.[/QUOTE]

That's what's happening anyway, and you're still suggesting a Yes/No question asking "Would you like extra language packs with your installation?", right? Feel free to rephrase "the problem" here, then, and preferably in a non-personal way, because that doesn't make sense as a solution.

---

### Post by ronacc on 2009-10-25
this has long been a major anoyance to me . the installer should only download the language pack for the SELECTED default language , and while we are at it additional language packs should only show in synaptic if they are requested to be shown , having to scroll past several PAGES of language related stuff is most anoying since most of us only install 1 or mabye 2 languages .

---

### Post by JillSwift on 2009-10-25
> **23meg said:**
> Because I happen to moderate this forum, and people shouting around usually doesn't make for good discussion.But it does rather suggest a certain level of frustration. An interesting factor in gauging the quality of software.

> **23meg said:**
> And sorry, I won't use the word "fuss" again; that was so rude of me.:rolleyes:

Here's the rude bit:

"I'm definitely living in an alternate reality where it's possible to skip installing the updates and language packs during installation. There's no other explanation."

Just for your edification.


I'm already writing up a description of the problem and a suggestion for a proper solution. But I won't post it here lest I waste more time. I'll submit it official like.

---

### Post by andrewabc on 2009-10-25
> **xebian said:**
> Exactly.  Why install/generate other locales when you only have one? what's the point of UK/AUS/CAD, etc when you only need US?

As a Canadian I am offended by that.
These non US countries spell words slightly differently.
I presume it downloads all locales, then selects the one you selected, then remove the non used ones? Thought I saw something like that when installing it cleaned up (removed) locals or something.

Maybe a better description of what it is downloading, and how much it is getting at what speed would help so people can better decide whether to skip it or not?

---

### Post by JillSwift on 2009-10-25
> **andrewabc said:**
> As a Canadian I am offended by that.
These non US countries spell words slightly differently.
I presume it downloads all locales, then selects the one you selected, then remove the non used ones? Thought I saw something like that when installing it cleaned up (removed) locals or something.

Maybe a better description of what it is downloading, and how much it is getting at what speed would help so people can better decide whether to skip it or not?
You misread.

It can also be phrased "What's the point of us/ger/can when all you need is Canadian English?"

---

### Post by 23meg on 2009-10-25
[QUOTE=JillSwift]But it does rather suggest a certain level of frustration. An interesting factor in gauging the quality of software.[/QUOTE]

Interesting, but not necessarily valid, as the example at hand perhaps illustrates. Given that the internets amplify the apparent importance of people who scream about things as opposed to those who discuss them in a sane manner, it's a good thing that the quality of most software isn't gauged directly by the amount of people that scream about it. 

[QUOTE=JillSwift]Here's the rude bit:

"I'm definitely living in an alternate reality where it's possible to skip installing the updates and language packs during installation. There's no other explanation."

Just for your edification.[/QUOTE]

If you have a better explanation for the kind of phenomenon where with two people supposedly talking about the very same piece of software, one complains about there being no way to skip a certain part of a certain linear process, and the other sees a mysterious button labeled "Skip", I'd like to hear it.

[QUOTE=JillSwift]I'm already writing up a description of the problem and a suggestion for a proper solution. But I won't post it here lest I waste more time. I'll submit it official like.[/QUOTE]

That's always a good idea. I too will re-evaluate my priorities next cycle.

---

### Post by wgrant on 2009-10-25
This was a bug, fixed in Ubiquity 2.0.4. 2.0.4 is currently waiting in the Karmic queue for release manager approval.

---

### Post by NoFearDJB on 2009-10-25
> **wgrant said:**
> this was a bug, fixed in ubiquity 2.0.4. 2.0.4 is currently waiting in the karmic queue for release manager approval.

thank you!!!

---

### Post by andrewabc on 2009-10-25
> **JillSwift said:**
> You misread.

It can also be phrased "What's the point of us/ger/can when all you need is Canadian English?"

Ok, I thought that after I posted.

So you select US language, and it decides to download US/AUS/CAN? Then at 99% done installing it removes AUS/CAN since not needed.

---

### Post by vishalrao on 2009-10-25
> **wgrant said:**
> This was a bug, fixed in Ubiquity 2.0.4. 2.0.4 is currently waiting in the Karmic queue for release manager approval.

Oh nice! I hope this is the fix that squashes my complaints once and for all :) I won't mind if it doesn't make it in for karmic (maybe an update later on, or even for 10.04 is good)... this and delta debs/zsync are my top wishlist items - can't wait!

---

### Post by emarkay on 2009-10-26
> **JillSwift said:**
> I don't. Why do you?



Me neither but I **won't** be doing it anymore, that thwack with the meterstick on my knuckles is still raw... ;)

Ah, ba tannyway, I am glad it's fixed... I think I have had my fill of bugs, tame abuse and undesired drama for the next 6 months.

---

