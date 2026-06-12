---
title: "Bring the old way of Update-Manager back?"
date: 2008-06-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2008-06-15
I for one REALLY liked that Update-Manager gave a good amount of information so you could see if you needed to hold a update back....And I REALLY hated that the availability was removed at the end of Hardy Development....so much that I was one of four people that filed bug reports about it.

I am running a poll to see if people would like Update-Manager back to the older specs. Michael Vogt has made available a older spec Manager (with gconf on/off key) for Hardy in his PPA, but I want a Manager that can turn on/off information "additions" with a gconf switch for Ibex--I also think that SHOULD be the default for Manager--

All in favor say YES---all against NO.

The main bugreport is: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/189406](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/189406)

Comment there if you feel like it--please keep it constructive ;)

I'm linking this poll to the bugreport so everyone interested can have input.

---

### Post by Gina on 2008-06-16
A definite YES from me.  The info isn't intrusive and people can choose to read it or not.  But YES again an option to turn it on/off would be good - remembered of course so you only have to set it once.

---

### Post by plun on 2008-06-16
Well, I am not using the update-manager during development.  :)

apt or aptitude with some thinkings and checkings if something
is broken.

For stable releases I cannot see problems with the update-manager.
(for unstable software its out-of-order)

:)

---

### Post by Gina on 2008-06-16
I don't use update-manager for testing during development, I use apt.

Isn't it the case that, even with the final release, dependent packages can get delayed on the mirrors and therefore things can go wrong if users update willy-nilly?

---

### Post by plun on 2008-06-16
> **Gina said:**
> 
Isn't it the case that, even with the final release, dependent packages can get delayed on the mirrors and therefore things can go wrong if users update willy-nilly?

Well, you can see tons of such threads within all development foras, just for example take a look at Hardys.

99% of all breaks are solved with the terminal and commands, or if a user just waits but thats a problem when packages are being blocked because of one broken package.

The update-manager is directly "out-of-order" and a user is complete blind about what causes this also howto solve a break.

Often a sudo aptitude install -f is enough.

**Its also about package info and bug reports.**

**FF3** has a **_search engine_** for Ubuntu packages, takes a second to switch

This info is really important also a link to **Launchpad**

[[img]http://pici.se/thumbs/t_gyDkTVLNX.gif[/img]](http://pici.se/286425)

(partly in swedish, sorry)


Mirrors can also be left behind and thats something which are important
for Ubuntu to make better.

Can be checked here:
[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)


Happy Testing... :)

---

### Post by philinux on 2008-06-16
Even the guy who did the change for the worse agrees with the YES vote.

---

### Post by ronacc on 2008-06-16
count me in as a yes

---

### Post by Game_boy on 2008-06-16
YES, I always feel more information about packages is needed in update manager.

---

### Post by autocrosser on 2008-06-16
I agree that Apt & Aptitude will solve many problems--I'll give you a example of how I was using Update-Manager---I would update things that looked "safe"--If after reading the info I thought there was a package or packages that were questionable, I would keep update's window open & either open Synaptic or a term & use Aptitude--update's window being open seems to not bother either one's operation---that way I could refer & make a informed choice.

My problem is that I want ALL the tools I can get my hands on & to have a tool gutted or dumbed down won't help me in my job--I would say that shipping the key <off> by default is OK--I'm very sure I could find it & turn it on ;)

Just GIVE ME THE CHOICE (isn't that what open-source is all about?)


> **plun said:**
> Well, you can see tons of such threads within all development foras, just for example take a look at Hardys.

99% of all breaks are solved with the terminal and commands, or if a user just waits but thats a problem when packages are being blocked because of one broken package.

The update-manager is directly "out-of-order" and a user is complete blind about what causes this also howto solve a break.

Often a sudo aptitude install -f is enough.

**Its also about package info and bug reports.**
<snip>

Happy Testing... :)

---

### Post by plun on 2008-06-16
> **autocrosser said:**
> 

My problem is that I want ALL the tools I can get my hands on & to have a tool gutted or dumbed down won't help me in my job--I would say that shipping the key <off> by default is OK--I'm very sure I could find it & turn it on ;)

Just GIVE ME THE CHOICE (isn't that what open-source is all about?)

Well... Debian is Ubuntus old mother and this mother uses apt or aptitude.
For stable releases PackageKit is one alternative.

But during development it is back to our roots.... IMHO   

I can use Synaptic for a few issues but its often faster to use
FF3 and Ubuntus package description.

It also have a direct URL to Launchpad and bugs....


Update-manager  >  a new repair button  ? difficult for a GUI to identify errors maybe.

Synaptic > Launchpad integration


FF3s package search engine is just great and that **the terminal remembers old commands**....  arrow up/down....

:)

---

### Post by durand on 2008-06-16
I probably will prefer the older way but I can't remember what it used to be like...any screenies?

---

### Post by 23meg on 2008-06-16
I don't really care either way. It's not as if the information is no longer available; it's just a click away (slightly less convenient), and I don't use or recommend using update-manager in development versions anyway. For stable releases, slowing down the process may actually be a good idea so that people who are just curious about the version numbers will also actually look into the update descriptions too. And if we switch to PackageKit soon..

[QUOTE=autocrosser]Just GIVE ME THE CHOICE (isn't that what open-source is all about?)[/QUOTE]

[No]("http://mystilleef.blogspot.com/2005/12/just-add-option-to-turn-it-off-or-on.html").

---

### Post by psyke83 on 2008-06-16
> **23meg said:**
> I don't really care either way. It's not as if the information is no longer available; it's just a click away (slightly less convenient), and I don't use or recommend using update-manager in development versions anyway. For stable releases, slowing down the process may actually be a good idea so that people who are just curious about the version numbers will also actually look into the update descriptions too. And if we switch to PackageKit soon..



[No]("http://mystilleef.blogspot.com/2005/12/just-add-option-to-turn-it-off-or-on.html").

I completely agree.

However, (and completely off-topic, sorry!) I recently read the link you posted and while I agree with its premise, it churns my stomach to see it again - simply because it was referred to as an argument to defend a decision made by Pidgin's [developers]("http://tech.slashdot.org/article.pl?sid=08/04/30/1822237") against the wishes of the majority of users.

---

### Post by go7Ul1ai on 2008-06-16
Hmmm, I wouldn't know what the old Update Manager would look like since I'm relatively new to the Ubuntu scene, I would however want more Update information etc though.

Lee

---

### Post by Raptor45 on 2008-06-16
And by majority, you mean the couple of people who actually noticed?

The early version was a bit buggy, I'll give that, but they've since fixed it and it works fine.

---

### Post by psyke83 on 2008-06-16
> **Raptor45 said:**
> And by majority, you mean the couple of people who actually noticed?

The early version was a bit buggy, I'll give that, but they've since fixed it and it works fine.

First of all, I wouldn't consider it "a couple of people" since a) that single bug report received about 250 comments, b) 1054 comments on a slashdot article, and c) it was even mentioned on slashdot at all.

Secondly, it's not fixed for me, and it doesn't work fine for me. I use IM to communicate with students to proofread/correct excerpts of texts, and it's a pain to work with text when it constantly resizes the window without my consent. Defending bad design decisions can be a terrible trait of open source / free software users.

Certain developers made some bogus claims in that bug report, e.g. (paraphrasing) "we code for ourselves, not our users". If that was truly the case, the amount of effort they have taken to create such a presentable and user-friendly website seems to betray their sentiments.

Having said all that, though, I'm still grateful to the developers for their hard work.

---

### Post by autocrosser on 2008-06-16
Well-I look at all the tools available to me & based on what I see is what way I choose to work with. Point well taken that the "new" format will slow some people down--I just think that the "point & click" crowd should not be in a testing branch anyway...

I noted a new version of Update-Manager come in last night & "tested" it as a matter of course--in any case, I "tend" to look at the updates with Update-Manager--that being said, I most likely will not use it to update--just to give me a quick heads up as to what is in the pipeline--I know that info is "just one click away"---but I like to scan everything at once & the dropdown window only shows for the highlighted selection.

Like I said---it's all about choices & the more info I can get within a short period of time helps me in the process (maybe I am just OLD :)  ).

---

### Post by ronacc on 2008-06-16
I also like to use all tools available to me , choosing the one that is most appropriate to my need at the moment . 
@23meg  I beg to differ , choice is one of the main reasons I use opensource and when a ( potentialy ) available choice is denied because "someone" thinks it should not be allowed to me , that gets my knickers in a bunch . The right to make that decission  (to use or not to use ) I prefer to reserve unto myself .

---

### Post by castrojo on 2008-06-16
> **ronacc said:**
> @23meg  I beg to differ , choice is one of the main reasons I use opensource and when a ( potentialy ) available choice is denied because "someone" thinks it should not be allowed to me , that gets my knickers in a bunch . The right to make that decission  (to use or not to use ) I prefer to reserve unto myself .

No one is removing your choice, you're still free to do whatever you want. (Maintain your own patchset, fork, etc.)

---

### Post by ronacc on 2008-06-16
> **whiprush said:**
> No one is removing your choice, you're still free to do whatever you want. (Maintain your own patchset, fork, etc.)

ah but they DID , thats what this thread is about , and it seems from the poll (for what thats worth) that the majority agrees with me . and before anyone says it I know this is not a democracy . however we are free to , within the limits of civility , express our opinion of the change .

---

### Post by caryb on 2008-06-16
> I know this is not a democracy . however we are free to , within the limits of civility , express our opinion of the change .


This is the core of my thought to what the FOSS/Linux community is about! ronacc gets a big tick from me!


2c Cary

---

### Post by autocrosser on 2008-06-16
We were not even asked if this would be a change for the better/worse...I know that the users normally are not asked, but with such a basic part of the system (installing software on your system is a choice, right?)--removing functionability ought to be made REVERSABLE for power-users. 

I for one do not think I ought to be told that I can't without good reason---I have been in this game for more years than most (try UNIX systems in the 70's) & normally can think my way out of most boxes I put myself into....I can see the thinking behind the change--nubie users that can & will tend to do things the wrong way--that is why I think a gconf <key> is the best answer--ship it with the <key> off & let the power-users find it.

I know I am sounding a bit strong about this--but I do not think I need to be coddled like one infirm or unknowing---and this "feels" like that kind of thinking--

If I am wrong-headed about this, I make amends at this point.

---

### Post by syxbit on 2008-06-16
this clearly isn't a fair poll, as generally, the only people who use dev distros (and thus answered this poll) are experienced, who want the extra info, and don't mind the terminal.

however, I do dislike how ubuntu has been making major strides to make this a n00b distro (like removing the bash-completion packages, etc..)
I think they're at a risk of losing the experienced users to arch linux. that would be bad, as having a forum with only n00bs would be useless.

It's possible to have a user friendly distro that also allows tweaking

---

### Post by ronacc on 2008-06-16
thats basicly what we are saying , default the option to off mabye but dont remove it.make Ubuntu n00b friendly without crippling it for experienced users .

---

### Post by joshrobinson on 2008-06-16
more options all the way.

---

### Post by syxbit on 2008-06-17
> **ronacc said:**
> thats basicly what we are saying , default the option to off mabye but dont remove it.make Ubuntu n00b friendly without crippling it for experienced users .

yea, i'm not disagreeing

---

### Post by Starks on 2008-06-17
There is absolutely no reason why the end user should be forced to use Synaptic to see the package version he is about to install.

---

### Post by 23meg on 2008-06-17
> **ronacc]ah but they DID , thats what this thread is about [/QUOTE]

No, it's not said:**
> and it seems from the poll (for what thats worth) that the majority agrees with me .

I do not recall a single "Bring the old behavior back?" poll in this forum that did not result in a landslide win for whatever was the old behavior. 

In times of change, it can be hard to grasp why exactly new ideas are better than old ones, especially if the old ones have become habitual and their necessity has gone unquestioned for a long time. When that is the case, the tendency always gravitates towards the old, regardless of whether the old is actually better, and usually without any arguments as to why the new is actually worse. 

> **ronacc]and before anyone says it I know this is not a democracy . however we are free to , within the limits of civility , express our opinion of the change .[/QUOTE]

That's a big red herring. Nobody has violated or shown a tendency to violate your right to express your opinion of the change.

[QUOTE=autocrosser] (installing software on your system is a choice, right?)[/QUOTE]

You have the choice here: vanilla update-manager, or update-manager with old behavior. It's just that the choice is not provided in the exact same way you desire. Note that I'm not arguing that it should or that it shouldn't said:**
> I can see the thinking behind the change--nubie users that can & will tend to do things the wrong way

I don't think that's the thinking behind the change. I haven't seen it mentioned as the rationale for the change, and I can't see a reason why showing version numbers in the main selector would lead to new users doing things the wrong way. The reason cited was that the version number information there was redundant, since the same information is available in the lower pane too. 

[QUOTE=syxbit]however, I do dislike how ubuntu has been making major strides to make this a n00b distro (like removing the bash-completion packages, etc..)[/QUOTE]

Another red herring: bash-completion was split from the bash package and not installed by default temporarily because it was unmaintained upstream. It had nothing to do with "making this a n00b distro", and nor does this change.

[QUOTE=Starks]There is absolutely no reason why the end user should be forced to use Synaptic to see the package version he is about to install.[/QUOTE]

And another: that's not the case. Package versions are still displayed in the update manager; just in a different place and in a different way.

---

### Post by ronacc on 2008-06-17
> **23meg said:**
> No, it's not; this thread is about a UI change that causes package versions to be shown in a different way. If someone had deprecated the old code and made you unable to view things the old way entirely unless you reverted to an old and incompatible version of update-manager, it would have been about taking out an option. The case here is that the code is still available, still works with the latest version and is even packaged in a PPA for easy installation (which means someone is making an effort to provide an option to those not satisfied with the change).



I do not recall a single "Bring the old behavior back?" poll in this forum that did not result in a landslide win for whatever was the old behavior. 

In times of change, it can be hard to grasp why exactly new ideas are better than old ones, especially if the old ones have become habitual and their necessity has gone unquestioned for a long time. When that is the case, the tendency always gravitates towards the old, regardless of whether the old is actually better, and usually without any arguments as to why the new is actually worse. 



That's a big red herring. Nobody has violated or shown a tendency to violate your right to express your opinion of the change.



I was unaware of the ppa version thankyou . link please .

Probaly true , but if the reason behind the change is not explained it may not seem to be benificial and atleast some of us do not necessarily see change soley for the sake of change as a good thing .

I was not saying they had been violated , I was trying to head off the "this is not a democracy"  comments that have appeared in in some other polls . I thought one of the purposes of this forum was to provide feedback as well as to discuss bugs .

---

### Post by 23meg on 2008-06-17
[QUOTE=ronacc]I was unaware of the ppa version thankyou . link please .[/QUOTE]

I was editing my post to correct it as you posted: it [seems]("https://launchpad.net/~mvo/+archive") the package isn't there yet, [but the commitment is there]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/189406/comments/12"), so the point stands.

[QUOTE=ronacc]
Probaly true , but if the reason behind the change is not explained it may not seem to be benificial and atleast some of us do not necessarily see change soley for the sake of change as a good thing .[/QUOTE]

It *has* been explained in the changelog, and that explanation was quoted at the bug report. A point to note is that nobody here who opposed the change so far has said anything that directly relates to that specific reason. All that came up was generalizations about "choice", "making Ubuntu a n00b distro", users being forced to do things in certain ways, etc.

[QUOTE=ronacc]I was not saying they had been violated , I was trying to head off the "this is not a democracy" comments that have appeared in in some other polls . I thought one of the purposes of this forum was to provide feedback as well as to discuss bugs .[/QUOTE]

I see, but for the sake of keeping discussions on topic and civil it's best to respond to what *has* been said rather than what *may* be. And no, providing feedback isn't among the intended purposes of this forum, as the notice at the top makes clear (and maybe should make clearer).

---

### Post by ronacc on 2008-06-17
> **23meg said:**
> 
And no, providing feedback isn't among the intended purposes of this forum, as the notice at the top makes clear (and maybe should make clearer).

point taken

"Intrepid Ibex Testing and Discusssion
Discussion on the upcoming Ubuntu release Intrepid Ibex Development which will be released October 2008. This forum is not the best way to contact the Ubuntu developers, please use the Ubuntu Development mailing list and Launchpad to interact with them."

I had interpeted "discussion " as kicking things around amongst ourselves before cluttering up the mailing list or adding (possibly bogus) bugs to an already distressingly long bug list.

---

### Post by 23meg on 2008-06-17
[QUOTE=ronacc]I had interpeted "discussion " as kicking things around amongst ourselves before cluttering up the mailing list or adding (possibly bogus) bugs to an already distressingly long bug list.[/QUOTE]

That's a pretty accurate definition.

---

### Post by autocrosser on 2008-06-17
Understood--that is why I linked this thread & the bugreport together--I wanted Michael Vogt to have a way to "look in" without being bowled over.

I guess that I still have not made myself plain enough. The "old" Manager lent itself to scan down a list & see all the version #s at once--If you saw something "funny", you could start thinking about it at once.

The "new" way, with only package name, forces you to tic the Info window to see the changes for that package only...I find myself looking for the version # & info--and get "no information available yet", which makes the second window worse than useless, so I also open Synaptic & dig thru it for info--

Maybe I need to change my workflow, but changing the default back to the "old" way at least (in my case above) gives me more info right at once to base off of.

I tend to keep "hot" packages/versions in my head & when there is a change to the version--it raises a flag at once.

> **23meg said:**
> That's a pretty accurate definition.

---

### Post by durand on 2008-06-17
> **ronacc said:**
> thats basicly what we are saying , default the option to off mabye but dont remove it.make Ubuntu n00b friendly without crippling it for experienced users .

+1 to that I guess. I don't really mind the way update-manager looks right now. My case is that I never read the changes and just click update. I trust ubuntu enough and I'm not really that bothered if something goes slightly wrong...Makes life interesting.

---

### Post by scaine on 2008-06-17
> **23meg said:**
> 
I do not recall a single "Bring the old behavior back?" poll in this forum that did not result in a landslide win for whatever was the old behavior. 

And yet, of course, it changes nothing.  Remember gnome-screensaver and how it crippled your ability to actually configure the screensaver you chose?  Remember the [controversy]("http://ubuntuforums.org/showthread.php?t=137408") (131 posts in that one alone...) and [outcry]("http://ubuntuforums.org/showthread.php?t=67087")?  The [indignation]("http://ubuntuforums.org/showthread.php?t=120071") (138 posts here) and [backlash]("http://ubuntuforums.org/showthread.php?t=188197")?

If all that couldn't convince the developer that he/she had made a huge, glaring, horrible error in judgement, then I doubt very much that this poll will make much difference in the long term.  For reference, William Jon McGann's disgraceful response on the official gnome bugzilla is here :
[http://bugzilla.gnome.org/show_bug.cgi?id=316654](http://bugzilla.gnome.org/show_bug.cgi?id=316654)
>  Comment #1 from William Jon McCann  (gnome-screensaver developer, points: 22)
2005-09-19 13:32 UTC [reply]

I don't have any plans to support this.  My view is that any screensaver theme
that requires configuration is inherently broken.

Good, eh?  To give some credit, he created a [nice FAQ about why we're wrong]("http://live.gnome.org/GnomeScreensaver/FrequentlyAskedQuestions").  So that's nice.

So, yeah, a gconf option... that will soon be forgotten.  I'm amazed that Michael's even agreed to that.  Usually, you just get a stock "this is why I'm right" speech.  McCann threw in a good dose of arrogance, just for good measure.

In fact, in all the three [Edit : Three? nearer five really - wow] years or so I've been using Gnome (and I still do... sheesh) the only war I've even seen the gnome devs lose is spatial nautilus.

So, gnome, for now.  But I've installed KDE4.01 and it's shaping up nicely.  When KDE4.1 hits the shelves, I think a test drive is in order.

---

### Post by psyke83 on 2008-06-17
scaine,

I just hope you aren't flamed down for that post - because if you are, I feel less hope for GNOME's future.

Right now we have two major competing DE's: one that's ultra-configurable (although KDE4 has been toned down, features are getting added back in) and one that's not configurable enough. No argument about code simplicity, "pure design" or any such fancy buzzword will ever persuade me that a screensaver should not be configurable.

---

### Post by 23meg on 2008-06-17
[http://ubuntuforums.org/showpost.php?p=2698299&postcount=26](http://ubuntuforums.org/showpost.php?p=2698299&postcount=26)
[http://ubuntuforums.org/showpost.php?p=1314185&postcount=17](http://ubuntuforums.org/showpost.php?p=1314185&postcount=17)
[http://ubuntuforums.org/showpost.php?p=3150587&postcount=41](http://ubuntuforums.org/showpost.php?p=3150587&postcount=41)

---

### Post by soccerboy on 2008-06-17
Quick question 23meg.  I am interested in working on this (the configuration of gnome-screensaver) or the restore from trash functionality in nautilus since no one seems to have taken these projects yet.  I am new to svn, however.  How would I go about checking out the packages and sending back the changes I made?

What configurability is needed in gnome-screensaver?  I never used xscreensaver so I don't know?

---

### Post by psyke83 on 2008-06-17
Edit: forget it.

---

### Post by 23meg on 2008-06-17
[QUOTE=psyke83]Closing the bug as WONTFIX and stating a position that "any screensaver theme that requires configuration is inherently broken." will not particularly motivate anyone to contribute and provide that functionality.[/QUOTE]

I agree, and he [apologized]("http://bugzilla.gnome.org/show_bug.cgi?id=316654#c48") later for his rushed comment and further clarified it (which he said was due to his time constraints).

[QUOTE=psyke83]There's no guarantee William will accept code to implement this configurability since he is of the opinion that screensavers shouldn't be configurable.[/QUOTE]

That's absolutely, 150% wrong. Please take time to read his post I linked to above.

---

### Post by psyke83 on 2008-06-17
> **23meg said:**
> I agree, and he [apologized]("http://bugzilla.gnome.org/show_bug.cgi?id=316654#c48") later for his rushed comment and further clarified it (which he said was due to his time constraints).



That's absolutely, 150% wrong. Please take time to read his post I linked to above.

You're right. I didn't see his reply and it clarified the situation, I edited my reply before yours ;). Sorry about that.

---

### Post by 23meg on 2008-06-17
> **soccerboy said:**
> Quick question 23meg.  I am interested in working on this (the configuration of gnome-screensaver) or the restore from trash functionality in nautilus since no one seems to have taken these projects yet. 

I recall hearing that someone is working on restoring from trash. Do a search on [the Nautilus mailing list]("http://mail.gnome.org/mailman/listinfo/nautilus-list") and ask around (on [IRC]("http://live.gnome.org/GnomeIrcChannels") and the list) if necessary before doing any work on that.

[QUOTE=soccerboy]I am new to svn, however.  How would I go about checking out the packages and sending back the changes I made?[/QUOTE]

[http://developer.gnome.org/tools/svn.html](http://developer.gnome.org/tools/svn.html) should help.

[QUOTE=soccerboy]What configurability is needed in gnome-screensaver?  I never used xscreensaver so I don't know?[/QUOTE]

[http://live.gnome.org/GnomeScreensaver/FrequentlyAskedQuestions](http://live.gnome.org/GnomeScreensaver/FrequentlyAskedQuestions) should be a good start. Again, I recommend doing a search in [the relevant mailing list]("http://mail.gnome.org/mailman/listinfo/screensaver-list") and asking the people involved.

---

### Post by soccerboy on 2008-06-17
Thanks.  I will look into it and contact William

---

### Post by scaine on 2008-06-17
Ah, 23meg - the voice of reason.  We've not always seen eye-to-eye, but you're always amazingly impartial.  How you don't lose the head on some of the threads I've seen you in, I'll never know.  When aysiu left the forums, I wondered who'd step up.  And it's like you don't sleep some days...

Your last link in that three earlier is the one most relevant, I think.  I won't argue that gnome-screensaver isn't a huge improvement **FOR GNOME** over xscreensaver.  No-one could reasonably argue that.

However, since no-one has stepped up and made those "crucial" changes to gnome-screensaver, I still to this day consider it utterly broken.  I haven't used a screensaver in over three years thanks to this.  I just power-saver my monitor after 20 minutes and be done.

Such a shame.  That's why it's particularly pleasing to see some movement on this issue regarding update-manager.  Perhaps things are-a-changing over on planet gnome.  I hope so.

As for being flamed for bringing up a three year old gripe?  I hope not!  Let's keep some perspective - I'm still using gnome despite this and various other (usually fairly minor) grievances with the way things have gone over the years.  Gnome is still, frankly, excellent.  And to echo another thread I read recently - I'm extremely grateful to the vast majority of gnome developers who made my desktop possible.

Apart from metacity.  That's rubbish.

:)

---

### Post by autocrosser on 2008-06-18
Interesting rub 23meg--I remember the dust-up over Xscreensaver/Gnome-screensaver--I still disable gnome-power-manager & install Xscreensaver & deep 6 Gnome-screensaver in my systems--for very self-evident reasons ;) (something to do about choice). I know that Gnome-power-manager is "better" than Xscreensaver for power management, but I really like to have options without jumping thru hoops to get them (I do know I can use half & half--use Xscreensaver to setup the savers--but I would rather just use one or the other).

I do hope that Michael & crew can see their way clear to give us a choice here--I still really like Gnome over KDE (no flaming intended-personal opinion only) & just would like to know that my thoughts do matter..............

By the by---I realy thank you for being here--please pardon my sometimes seemingly randon soapboxisms--from time to time I "feel" my toes have been stept on.......And you do set a well-reasoned tone for these forums to meet.

---

### Post by MaX on 2008-06-18
> **scaine said:**
> However, since no-one has stepped up and made those "crucial" changes to gnome-screensaver, I still to this day consider it utterly broken.  I haven't used a screensaver in over three years thanks to this.  I just power-saver my monitor after 20 minutes and be done.

Well that's good really... Screen savers where created to prevent burn-in's on old CRT monitors. We don't have that problem now and turning on a screen from sleep isn't that slow any longer either. Really, Ubuntu should default to turning off the monitor after 30 minutes.

---

