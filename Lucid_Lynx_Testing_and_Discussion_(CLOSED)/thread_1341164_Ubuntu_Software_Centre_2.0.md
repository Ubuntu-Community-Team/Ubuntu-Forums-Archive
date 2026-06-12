---
title: "Ubuntu Software Centre 2.0"
date: 2009-11-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zekopeko on 2009-11-29
Figured I'll start a thread about the future USC2 that should land in Lucid. Please post your suggestions and grievances.

Here is the [SIZE="4"]**wiki page**[/SIZE] 

PLEASE, READ IT BEFORE COMMENTING:

[https://wiki.ubuntu.com/SoftwareCenter](https://wiki.ubuntu.com/SoftwareCenter)

Here is how it SHOULD look in **VERSION 4** aka Ubuntu 11.04 (subject to change and user testing):

[https://wiki.ubuntu.com/SoftwareCenter#Eventual scope](https://wiki.ubuntu.com/SoftwareCenter#Eventual scope)

Here are [SIZE="4"]**blueprints**[/SIZE] targeted for Lucid:

[https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-index-based-downloads-client](https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-index-based-downloads-client)

[https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-ratings-and-reviews-in-software-center](https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-ratings-and-reviews-in-software-center)

[https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-software-center-repository-based-index](https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-software-center-repository-based-index)

[https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-software-center-subcategories](https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-software-center-subcategories)

[https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-software-center-history-of-packaging-transactions](https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-software-center-history-of-packaging-transactions)

[https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-non-applications-in-software-center](https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-non-applications-in-software-center)

I you find anything interesting about USC2 please PM me or post here and I will update the post.

[SIZE="4"]**Ways you can help:**[/SIZE]

[SIZE="2"]**Screenshots of applications:**[/SIZE]

I noticed that a number of apps in USC1 are missing screenshot or the screenshots are fugly because of the icons and theme.

To fix this look in the USC if the screenshots are missing or are fugly.

Install [Shutter]("apt://shutter"). Third button in the toolbar allows you select the application and take it's screenshot.

Then go here: [http://screenshots.ubuntu.com/](http://screenshots.ubuntu.com/)

And upload the screenshot for the application that is missing it.

I recommend that you use the default Human theme and the Humanity icon set but anything that doesn't look like it crawled out of 90's is fine. 

Also i would avoid themes that emulate Windows or Mac OSX just so that we don't confuse the user.


[SIZE="2"]**Suggestions for the History section of USC2:**[/SIZE]

Feel free to pitch in with your designs here

[https://wiki.ubuntu.com/SoftwareCenter/History](https://wiki.ubuntu.com/SoftwareCenter/History)

---

### Post by Gina on 2009-11-29
Wow, now that's a good read :lolflag:

I shall read through it carefully.  I think this project shows great promise and should make software finding and selecting much easier.

Good luck to all involved :)

---

### Post by ronacc on 2009-11-29
though I was initially skeptical I must admit that what we have got so far is quite good and what is proposed is even better .

---

### Post by mpt on 2009-11-29
> **zekopeko said:**
> Here is how it SHOULD look (subject to change and user testing):

[https://wiki.ubuntu.com/SoftwareCenter#Eventual%20scope](https://wiki.ubuntu.com/SoftwareCenter#Eventual%20scope)

I’ve just added a note to clarify that that’s a mockup of version 4, not version 2. Version 2 won’t have paid software, recommendations, or “What’s New”, and probably won’t have saved package lists (unless someone wants to contribute that feature).

---

### Post by McDuff on 2009-11-29
i was just wondering, how many ppl you have working on it that this could be done by april. :D

---

### Post by zekopeko on 2009-11-29
> **McDuff said:**
> i was just wondering, how many ppl you have working on it that this could be done by april. :D

It's mpt on the design side, mvo, rugby471 on the coding part.

---

### Post by Regenweald on 2009-11-29
It looks bada** :D

---

### Post by zekopeko on 2009-11-29
Post updated with a mini Shutter tutorial for taking app screenshots.

> **mpt said:**
> I’ve just added a note to clarify that that’s a mockup of version 4, not version 2. Version 2 won’t have paid software, recommendations, or “What’s New”, and probably won’t have saved package lists (unless someone wants to contribute that feature).

Post fixed.

mpt is there something else that we can help with?
What's the status of (sub)categories?
When can we expect the review and rating part to be integrated so that people can start writing reviews? It would be nice to ship Lucid with reviews for every major app in the USC.

---

### Post by seeker5528 on 2009-12-02
> **ronacc said:**
> though I was initially skeptical I must admit that what we have got so far is quite good and what is proposed is even better .

I don't think much of what we have so far, but that's not saying much because everything that would make me think seriously about using it are things that were intended to be added post 1.0 or post 2.0.

One thing I am skeptical about is the time for getting to a point where it is considered an alternative to Synaptic. From the planned features it certainly seems the potential is there, but saying is easier than doing.

Recognizing the package cache is hosed and offering to fix it is certainly a welcome feature.

I don't consider these to be high priority items, but to me, before it can be considered an alternative to Synaptic you need the ability to tell it not to treat recommends as dependencies possibly with options to keep that setting only for the current install or to change it permanently, have the option to list and attempt to fix broken packages, and while showing a package, have options to list its dependencies/dependents for the currently installed and available versions of the package, and view the changelogs and show a list of things that will be installed/removed and be given the option to cancel the install. 

And maybe apt could be defaulted to getting only the differences in the package list so once you have updated the list you only have small downloads instead of having to download the entire list every time.

Later, Seeker

---

### Post by Kazade on 2009-12-03
I think the Software Centre in Karmic is awesome and I can't wait for the new features in Lucid, I just have two little annoyances with it:

1. The blue-grey background and blue header doesn't match anything else in my (or the default) system theme.
2. Having to press the little arrow button to look at the description of the application is not that intuitive, I'd prefer if the whole row was clickable (and hovering gave the little hand cursor)

Any chance those two issues could get looked at? Besides those minor niggles it's great, good work! :)

---

### Post by Gina on 2009-12-03
> **Kazade said:**
> I think the Software Centre in Karmic is awesome and I can't wait for the new features in Lucid, I just have two little annoyances with it:

1. The blue-grey background and blue header doesn't match anything else in my (or the default) system theme.
2. Having to press the little arrow button to look at the description of the application is not that intuitive, I'd prefer if the whole row was clickable (and hovering gave the little hand cursor)

Any chance those two issues could get looked at? Besides those minor niggles it's great, good work! :)+1

I'm not really bothered about 1. above but I do think if it could pick up the main theme, it would look better.  I was puzzled for a second or two by 2. when I first saw it,

---

### Post by Gina on 2009-12-03
> **Kazade said:**
> I think the Software Centre in Karmic is awesome and I can't wait for the new features in Lucid, I just have two little annoyances with it:

1. The blue-grey background and blue header doesn't match anything else in my (or the default) system theme.
2. Having to press the little arrow button to look at the description of the application is not that intuitive, I'd prefer if the whole row was clickable (and hovering gave the little hand cursor)

Any chance those two issues could get looked at? Besides those minor niggles it's great, good work! :)+1

I'm not really bothered about 1. above but I do think if it could pick up the main theme, it would look better.  I was puzzled for a second or two by 2. when I first saw it.

---

### Post by zekopeko on 2009-12-05
What do you girls/guys think of removing the transition to the "In progress" view every time you install an app? It would make it more like an online shopping experience and streamline the install process.

---

### Post by ronacc on 2009-12-05
bad idea .

---

### Post by aamukahvi on 2009-12-05
> **ronacc said:**
> bad idea .

Good argument.

---

### Post by ronacc on 2009-12-05
he asked what we thought of it, I replied . Actually the question is poorly phrased . Switch can either mean a change to or the ability to change to . as in I am going to switch brands or a light switch . It is alright if it does not default to the detailed view of the progress it is not alright to remove the ability to do so .

---

### Post by Gina on 2009-12-05
If we're talking about removing the progress bar... definitely BAD idea!

Actually, I think my reply must be "Sorry, I don't understand the question".

---

### Post by 23meg on 2009-12-05
> **zekopeko said:**
> What do you girls/guys think of removing the switch to the "In progress" view every time you install an app? It would make it more like an online shopping experience and streamline the install process.

What should happen instead when installation begins?

---

### Post by zekopeko on 2009-12-05
> **ronacc said:**
> he asked what we thought of it, I replied . Actually the question is poorly phrased . Switch can either mean a change to or the ability to change to . as in I am going to switch brands or a light switch . It is alright if it does not default to the detailed view of the progress it is not alright to remove the ability to do so .

> **Gina said:**
> If we're talking about removing the progress bar... definitely BAD idea!

Actually, I think my reply must be "Sorry, I don't understand the question".

> **23meg said:**
> What should happen instead when installation begins?

Whooaa! I guess poor description on my part.

What I meant was:

When you click the install on the App page you get switched to the In progress view and have to click the Get Free Software to return to the App page and continue browsing. 

This IMO breaks the whole experience. I want to browse the software library and simply queue the apps for install.

What I think that the In Progress sidebar entry should do is flash 2 or 3 time, in a minimally intrusive manner, and let you continue browsing the apps.

Once all the apps that you queued complete installing (or there was a problem) app center should focus in background if it was minimized and show you the In Progress view so that you can see what was installed. 

If there was a problem it should install everything that it can install and then show you the In Progress pane.

I hope this is descriptive enough.

---

### Post by ronacc on 2009-12-05
or how about when you selected an app it had a tic mark to add it to the que and then when you had selected all you want the install button would d/l and install them , showing you the progress and then automaticly return to the selection pane .

---

### Post by ranch hand on 2009-12-05
Well I have synaptic putting all that in a terminal so I can keep an eye on it so I don't think I would be happy with that.

On the other hand, I doubt that I will use the Software Center anymore than I use Add/Remove so it would not really effect me at all.

I guess I just wonder at how many people want to "protected" from what is going on in their box.  This is one of the chief reasons I switched to Linux in general and Ubuntu in particular, to KNOW what was going on as much as possible.

---

### Post by zekopeko on 2009-12-05
> **ronacc said:**
> or how about when you selected an app it had a tic mark to add it to the que and then when you had selected all you want the install button would d/l and install them , showing you the progress and then automaticly return to the selection pane .

I would skip the whole "queue and then confirm install" thing. It's a waste of time doing things that way. Computers can do things in parallel without a problem. Humans can't.

---

### Post by ronacc on 2009-12-05
I thought the whole point of Ubuntu was Linux for HUMANS .Actually like Ranch Hand I use synaptic or if I know exactly what I need apt-get from terminal.

---

### Post by ranch hand on 2009-12-05
> **ronacc said:**
> i thought the whole point of ubuntu was linux for humans .actually like ranch hand i use synaptic or if i know exactly what i need apt-get from terminal.
+1

---

### Post by seeker5528 on 2009-12-05
> **zekopeko said:**
> What I think that the In Progress sidebar entry should do is flash 2 or 3 time, in a minimally intrusive manner, and let you continue browsing the apps.

Would it be possible just to show the progress in the sidebar entry something like:

Installation Progress: 
%XXX Tot.  %XXX Cur.

: so the basic information is always there and when you click it you get the progress window with more details, option to cancel queued installs, etc...

Later, Seeker

---

### Post by zekopeko on 2009-12-05
> **ronacc said:**
> I thought the whole point of Ubuntu was Linux for HUMANS .Actually like Ranch Hand I use synaptic or if I know exactly what I need apt-get from terminal.

> **ranch hand said:**
> +1

Thanks you both for contributing absolutely nothing to the discussion. If you want to discuss how awesome synaptic and command line are for you I suggest that you open a thread in the appropriate forum.

---

### Post by zekopeko on 2009-12-05
> **seeker5528 said:**
> Would it be possible just to show the progress in the sidebar entry something like:

Installation Progress: 
%XXX Tot.  %XXX Cur.

: so the basic information is always there and when you click it you get the progress window with more details, option to cancel queued installs, etc...

Later, Seeker

Well it's already there in a way. You get a number beside the In Progress item. It should look similar to this (note the Downloads): [http://macinjay.files.wordpress.com/2007/12/itunes-sidebar.jpg](http://macinjay.files.wordpress.com/2007/12/itunes-sidebar.jpg)

---

### Post by ronacc on 2009-12-05
> **zekopeko said:**
> Thanks you both for contributing absolutely nothing to the discussion. If you want to discuss how awesome synaptic and command line are for you I suggest that you open a thread in the appropriate forum.

I was responding to your previous comment about the difference between the way computers and humans process information ie parallel vs sequential .

---

### Post by xebian on 2009-12-06
> **zekopeko said:**
> Thanks you both for contributing absolutely nothing to the discussion. If you want to discuss how awesome synaptic and command line are for you I suggest that you open a thread in the appropriate forum.

```
Please post your suggestions and grievances.
```
Isn't that what you are asking of them?

You can't take them out of the discussion if you are trying to mimic what synaptic/apt-get/add-and-remove provides now.

IIRC what you are trying to do in 11.04 with SC is what add and remove is now.

---

### Post by xebian on 2009-12-06
> **zekopeko said:**
> I would skip the whole "queue and then confirm install" thing. It's a waste of time doing things that way. Computers can do things in parallel without a problem. Humans can't.

Bad idea.  Confirmation is very important.  

Have you tried doing two installs at the same time?  I'm sure it will complain because it is locked by the other process.

---

### Post by Gina on 2009-12-06
> **xebian said:**
> Have you tried doing two installs at the same time?  I'm sure it will complain because it is locked by the other process.I have and it does!

I think the reason is dependencies.

---

### Post by zekopeko on 2009-12-06
> **xebian said:**
> ```
Please post your suggestions and grievances.
```
Isn't that what you are asking of them?

You can't take them out of the discussion if you are trying to mimic what synaptic/apt-get/add-and-remove provides now.

IIRC what you are trying to do in 11.04 with SC is what add and remove is now.

I don't see how their input is helping to shape USC as a worthy replacement for Synaptic. I welcome posts that say "This sucks in USC and it should do it like this because this is better for reasons XYZ". Proclaiming that you use Synaptic and CLI isn't really helping the discussion since USC obviously isn't targeted at those users.

> **Gina said:**
> I have and it does!

I think the reason is dependencies.

> **xebian said:**
> Bad idea.  Confirmation is very important.  

Have you tried doing two installs at the same time?  I'm sure it will complain because it is locked by the other process.

That happens if you have two separate applications accessing the database. Considering that USC should replace all the applications (with the possible exception of Update Manager) this won't be a problem. And if it does happen it should still open/de-minimize in the background and patiently wait for user input. But it should do everything it can before bugging the user with silly things.

What I don't like is that USC takes the focus from my browsing the repository and shows me the status of a single application that I selected for install.
IIRC iTunes does this nicely with downloads. It simply creates the Download entry in the sidebar (like USC does with the In Progress entry now) but it doesn't focus to the Downloads view every time you click to download a podcast/album/song etc.

EDIT: Here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/435102](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/435102)
It looks like the progress will be shown in the Application pane so there will be no switching to the In Progress at all. This also happens only when there are no other installations pending. The only question now is if this will make it in 2.0.

---

### Post by Glenn nl on 2009-12-06
In which release will Synaptic and add/remove be gone?

---

### Post by zekopeko on 2009-12-06
> **Glenn nl said:**
> In which release will Synaptic and add/remove be gone?

It should happen for Lucid.

---

### Post by Glenn nl on 2009-12-06
> **zekopeko said:**
> It should happen for Lucid.

So whats the big deal with gimp if two major applications are being removed and they will provide a lot of space? :o

---

### Post by Gina on 2009-12-06
Add/Remove has already been replaced by USC.  I thought Synaptic was staying until Lucid+1?

---

### Post by ronacc on 2009-12-06
> **zekopeko said:**
> I don't see how their input is helping to shape USC as a worthy replacement for Synaptic. I welcome posts that say "This sucks in USC and it should do it like this because this is better for reasons XYZ". Proclaiming that you use Synaptic and CLI isn't really helping the discussion since USC obviously isn't targeted at those users.


you conveniently forget that what started that series of posts WAS my suggestion for some improvements/changes and YOUR snide reply to those suggestions , Quit baiting people and then misrepresenting their responses.

---

### Post by zekopeko on 2009-12-06
> **ronacc said:**
> you conveniently forget that what started that series of posts WAS my suggestion for some improvements/changes and YOUR snide reply to those suggestions , Quit baiting people and then misrepresenting their responses.

Oh you mean the one were describe the way Synaptic and Add/Remove work? The model that USC is moving away from?
And [+1]-ing isn't exactly moving the discussion forward.

I'm unsure as to how I'm "baiting people and then misrepresenting their responses".
I simply stated, snidely if you wish, the lack of quality input. And I responded to your suggestion with a counter argument. 
Your response was a cheap misuse of the Ubuntu slogan with no substance to back it.

I opened this thread because I wanted to see what could be improved in USC 2.0 . No matter how you wish it USC is here to stay and is going to replace Synaptic so as  Synaptic users (me included) it is in our interest to try and make USC rock and this can only be achieved with serious arguments since mpt is a UI developer and cheap arguments aren't going to sway him.

Have a good day.

---

### Post by Merk42 on 2009-12-06
ronacc, Ranch Hand, and anyone else that prefers synaptic:

Why do you prefer it?

What sort of features / workflow does it have that is better than the alternatives?

I'm asking because hopefully if they can be listed, they can be implimented into USC.

---

### Post by ronacc on 2009-12-06
yes that is the one I mean (post #20) however you will notice that nowhere in that post do I mention either synaptic or add/remove . I made a suggestion for behavior I would like to see in USC . 
the first line in post #1 
>  Figured I'll start a thread about the future USC2 that should land in Lucid. Please post your suggestions and grievances.
If you don't want posts that differ from YOUR preconceived notions , don't ask for them .

---

### Post by ranch hand on 2009-12-06
> **Merk42 said:**
> ronacc, Ranch Hand, and anyone else that prefers synaptic:

Why do you prefer it?

What sort of features / workflow does it have that is better than the alternatives?

I'm asking because hopefully if they can be listed, they can be implimented into USC.
I am away from the Lizard right now and would prefer to answer your question when I have USC there for reference.

I will get back to you tomorrow with a list.

---

### Post by ronacc on 2009-12-06
@Merk42 
First of all let me state that I am in no way against USC , in fact earlier in this thread I applaud the rapid progress it is making . I do not believe that synaptic and USC are mutually exclusive . I prefer synaptic because it is a complete package manager allowing much more than simple software installation/removal and this suits my needs , I will admit that I do not consider myself the "average user" .
  for USC I would as I stated earlier like to see the ability to multi-select packages to be qued before installation begins and also a selectable level of information about what is happening during the install process .

---

### Post by Gina on 2009-12-07
> **ronacc said:**
> @Merk42 
First of all let me state that I am in no way against USC , in fact earlier in this thread I applaud the rapid progress it is making . I do not believe that synaptic and USC are mutually exclusive . I prefer synaptic because it is a complete package manager allowing much more than simple software installation/removal and this suits my needs , I will admit that I do not consider myself the "average user" .
  for USC I would as I stated earlier like to see the ability to multi-select packages to be qued before installation begins and also a selectable level of information about what is happening during the install process .I agree with all of that.  I like USC too and the way it appears to be going and I too would like to see those improvements.  It has a way to go yet before it will totally replace synaptic.

---

### Post by mpt on 2009-12-07
> **zekopeko said:**
> mpt is there something else that we can help with?
What's the status of (sub)categories?

It’s funny you should mention that. :) We want to do a [card sorting]("http://en.wikipedia.org/wiki/Card_sorting") exercise to help us work out what subcategories Ubuntu applications should be arranged in. This involves recruiting user test subjects, showing them 50 or so cards with information about applications and other packages, and getting them to arrange those cards into categories. But … we need someone with the time and mad skillz to figure out how to generate those printable cards. If you think you might be able to help out with this, please see [my post in the Programming Talk forum]("http://ubuntuforums.org/showthread.php?p=8456804").

As for what else you can help with, see the “[How you can help]("https://wiki.ubuntu.com/SoftwareCenter#contributing")” section of the spec. There’s plenty to do, whether you prefer coding, testing, artwork, design, or copywriting.

> *When can we expect the review and rating part to be integrated so that people can start writing reviews? It would be nice to ship Lucid with reviews for every major app in the USC.*

I’ve written up [an initial spec]("https://wiki.ubuntu.com/SoftwareCenter#reviewing") for how the review system should work, but implementing this is harder than it looks.

> **seeker5528 said:**
> I don't consider these to be high priority items, but to me, before it can be considered an alternative to Synaptic you need the ability to tell it not to treat recommends as dependencies possibly with options to keep that setting only for the current install or to change it permanently,

Have you seen my initial write-up of “[Presenting add-on packages]("https://wiki.ubuntu.com/SoftwareCenter#add-ons")”? What do you think? (Unfortunately I haven’t had time to draw the mockup yet.)

> *have the option to list and attempt to fix broken packages,*

Thanks, I’ve added this as an unresolved issue.

> *and while showing a package, have options to list its dependencies/dependents for the currently installed and available versions of the package, and view the changelogs and show a list of things that will be installed/removed and be given the option to cancel the install.*

Yes, we need some sort of detailed properties window for a package like Synaptic has.

> **Kazade said:**
> 1. The blue-grey background and blue header doesn't match anything else in my (or the default) system theme.

We need to highlight the various screens in the “Get Free Software” section in a different way from the various screens in the “Installed Software” section, to reassure people about where they are. Currently, we use a colored background to do that. If GTK provided more theme colors, we’d gladly use one of them.

> *2. Having to press the little arrow button to look at the description of the application is not that intuitive, I'd prefer if the whole row was clickable (and hovering gave the little hand cursor)*

In v2 (if we manage to implement it), [selecting a row will expand it]("https://wiki.ubuntu.com/SoftwareCenter#software-list-view") to show buttons for the most common operations.

---

### Post by nanog on 2009-12-07
Things that would make me a USC user:

*An option to find and fix broken packages.

*An option to show all packages that match the search term (obsolete or legacy drivers are often missing in search output).

*An advance tab that allows things like pinning, purging, and dependency visualization.

---

### Post by xebian on 2009-12-07
> **nanog said:**
> Things that would make me a USC user:

*An option to find and fix broken packages.

*An option to show all packages that match the search term (obsolete or legacy drivers are often missing in search output).

*An advance tab that allows things like pinning, purging, and dependency visualization.

Look no further. Synaptic or apt-get or aptitude. NOW not in 2011 or whenever.

You can only search what's in the repo.  What's not in there, consult your local fortune teller. :P

---

### Post by Gina on 2009-12-07
The idea is to replace synaptic eventually though.

---

### Post by ranch hand on 2009-12-07
> **Merk42 said:**
> ronacc, Ranch Hand, and anyone else that prefers synaptic:

Why do you prefer it?

What sort of features / workflow does it have that is better than the alternatives?

I'm asking because hopefully if they can be listed, they can be implimented into USC.
Sorry for the delay, for some reason USC will not load on the Stoned Lizard so I had to switch to the clean install version.

A>The "departments" are harder to wadee through than the "sections" in synaptic.  This is due to the sections at least being broken up into "main" (no label), "universe" and "multiverse" so you do not have as many at a time.

B>Where in tarnation is the ability to fix, or even list, broken packages.

C>Uses the same stupid "lets open another screen for the description with no good way back" used in Add/Remove.

D>Even Add/Remove had check boxes by the apps so you could check several for installation (or removal) at once.  This is just plumb silly.  When you are setting up a new install you have several packages you want to install.  One at a time is a real time waister.  Nearly on the level of RPMs (while you can install more than one at a time they come in one at a time and your connection has to restart from 0Kb/s for every one).  Using Apt or Synaptic and getting multi-packages the connection stays, in my case, flat lined at about 300Kb/s.  As USC uses dpkg as the backend this ability to get more than one package at a time should not be tough.  The problem must be in setting up the gui so that it doesn't look like synaptic or even Add/Remove.

Those are the main points.  Every one a deal breaker by itself.

I need to get back to the Sttoned Lizard so that boinc can run.

---

### Post by Merk42 on 2009-12-07
> **ranch hand said:**
> A>The "departments" are harder to wadee through than the "sections" in synaptic.  This is due to the sections at least being broken up into "main" (no label), "universe" and "multiverse" so you do not have as many at a time.
Hmm I think USC is supposed to have sub-sections
I'd argue that synaptic has too many sub-sections to wade through, hopefully there will be a happy medium

> **ranch hand said:**
> B>Where in tarnation is the ability to fix, or even list, broken packages.That's been bought up too I think?

> **ranch hand said:**
> C>Uses the same stupid "lets open another screen for the description with no good way back" used in Add/Remove.You use the breadcrumbs up top to go back..

> **ranch hand said:**
> D>Even Add/Remove had check boxes by the apps so you could check several for installation (or removal) at once.  This is just plumb silly.  When you are setting up a new install you have several packages you want to install.  One at a time is a real time waister.  Nearly on the level of RPMs (while you can install more than one at a time they come in one at a time and your connection has to restart from 0Kb/s for every one).  Using Apt or Synaptic and getting multi-packages the connection stays, in my case, flat lined at about 300Kb/s.  As USC uses dpkg as the backend this ability to get more than one package at a time should not be tough.  The problem must be in setting up the gui so that it doesn't look like synaptic or even Add/Remove.So if there was an "Install Now" button as well as an "Install Later" button (which would queue) that would be good?

---

### Post by xebian on 2009-12-07
> **Gina said:**
> The idea is to replace synaptic eventually though.

IMHO it's a very bad idea.  How often do you need to browse/add/install software/apps?  Some does not even want to change what they have at least for a year because they think it would be bug-free by then. ;)

You take add-and-remove, change the title to SC, and you have now what mpt is promising in 2011.

IIRC by then 'cloud' would be the thing.  All you need is a browser.  

Just my 2 cents.

---

### Post by zekopeko on 2009-12-07
> **nanog said:**
> Things that would make me a USC user:

*An option to find and fix broken packages.

Perhaps a special sidebar entry with the label "Broken packages/applications". It should automatically scan for those when you start USC. If you try to start an application that is broken it should open USC and focus to this screen.

Here is how it could look: 
[http://imgur.com/Tt21o](http://imgur.com/Tt21o)

> On the top
*An option to show all packages that match the search term (obsolete or legacy drivers are often missing in search output).

Could you provide a screenshot with some explanations on what you mean?

> *An advance tab that allows things like pinning, purging, and dependency visualization.

[https://wiki.ubuntu.com/SoftwareCenter#Software list view for “Get Software”]("https://wiki.ubuntu.com/SoftwareCenter#Software list view for “Get Software”")

[https://wiki.ubuntu.com/SoftwareCenter#Software](https://wiki.ubuntu.com/SoftwareCenter#Software) list view for “Get Software”

Add another button that says More options and provides you with those options in a dropdown menu?

---

### Post by zekopeko on 2009-12-07
> **ranch hand said:**
> Sorry for the delay, for some reason USC will not load on the Stoned Lizard so I had to switch to the clean install version.

A>The "departments" are harder to wadee through than the "sections" in synaptic.  This is due to the sections at least being broken up into "main" (no label), "universe" and "multiverse" so you do not have as many at a time.

You should take into account that USC is application-centric. Most users don't really care about packages but about applications.
The main, universe and multiverse only matter if you have a support contract from Canonical or some other company (or are one of the free software zealots but then you would be using gnewsense).

I find departments more user centric since there is less hierarchy to wade through. 

> B>Where in tarnation is the ability to fix, or even list, broken packages.

Look at my above post. I think that it's a reasonable solution but please do point out any deficiencies you see. It was a 5 min GIMP job.

> C>Uses the same stupid "lets open another screen for the description with no good way back" used in Add/Remove.

If you look at the current mockup there are arrows. I think that this is a good solution.

> D>Even Add/Remove had check boxes by the apps so you could check several for installation (or removal) at once.  This is just plumb silly.  When you are setting up a new install you have several packages you want to install.  One at a time is a real time waister.  Nearly on the level of RPMs (while you can install more than one at a time they come in one at a time and your connection has to restart from 0Kb/s for every one).  Using Apt or Synaptic and getting multi-packages the connection stays, in my case, flat lined at about 300Kb/s.  As USC uses dpkg as the backend this ability to get more than one package at a time should not be tough.  The problem must be in setting up the gui so that it doesn't look like synaptic or even Add/Remove.

Actually I would say that the future way of installing in USC is far more time efficient then the one in Synaptic and Add/Remove. In Synaptic you have to click all the packages that you want to install (and use 3 clicks; Right click to open the menu and another to select the Install option and then click on the Install button in the toolbar; in Add/Remove it's 2 clicks). The down side is that Add/Remove' way of doing thing is more efficient click-wise but not time wise since you can't browse and install at the same time.

Now look at the way USC will do it in the future [https://wiki.ubuntu.com/SoftwareCenter#Software list view for “Get Software”]("https://wiki.ubuntu.com/SoftwareCenter#Software list view for “Get Software”")

You click once and then click install and it starts the download and install process while you can continue browsing. I'm guessing that the current problem is in the backend since it should download them in parallel and then install them. There was talk during UDS that we could download and decompress packages in parallel so that the process isn't as sequential as is now (install once you downloaded all the packages).
Ideally USC would download in parallel, de-compress dependencies for the app and install the packages while other packages (that belong to other applications) are still downloading.

---

### Post by ranch hand on 2009-12-07
I am one of those folks who really doesn't care what it looks like.  Your solution looks like it would work in the structure of USC.  This is not the problem though.

The problem is that the ability is not there at all, no matter what it looks like.  This is too important not to have.

As has been pointed out, synaptic will still be in the repos.  That is fine for me.  It is not fine for someone stuck with a package handling system that does not handle package problems.  This may be easier to use but it does not sound very user centric to me.

It sounds to me like it is now going to be a lot harder for a new user to work out his problems than it is now.

I may not give new users enough credit.  I am a fairly new user and I can proudly say that I broke Hardy 5 times the first week I had it.  As a long time MS user I reinstalled.  I am sure, now that this was not needed most of those times.

When I discovered the broken packages functionality of synaptic things improved.

I must say, in defense of both Add/Remove and USC, that synaptic is not the most visible app in the world.  I downloaded a lot of stuff that I could have gotten through Apt or synaptic.  I am sure that this lead to a lot of the breakage.  Having something more visible has got to help with that.

I have trouble believing that parallel down loads is a backend problem.  Surely USC is using basically the same backend as Apt and synaptic, both of which have no problem with this.

---

### Post by Merk42 on 2009-12-07
> **ranch hand said:**
> I am one of those folks who really doesn't care what it looks like.  Your solution looks like it would work in the structure of USC.  This is not the problem though.

The problem is that the ability is not there at all, no matter what it looks like.  This is too important not to have.


Well isn't the point of this thread, or at least of the question I asked you, to find out what features should be in USC 2.0?

---

### Post by ranch hand on 2009-12-07
> **Merk42 said:**
> Well isn't the point of this thread, or at least of the question I asked you, to find out what features should be in USC 2.0?
Yes, this was a reply about how a broken packages handler would look.  I don't care what it looks like, that mock up looked fine.

There is no code to go with it.  That is what we really need.  Some functionality.

---

### Post by zekopeko on 2009-12-07
> **ranch hand said:**
> The problem is that the ability is not there at all, no matter what it looks like.  This is too important not to have.

What ability? What are you talking about? I'm confused.

---

### Post by ranch hand on 2009-12-07
The ability to fix broken packages.

---

### Post by zekopeko on 2009-12-07
> **ranch hand said:**
> Yes, this was a reply about how a broken packages handler would look.  I don't care what it looks like, that mock up looked fine.

There is no code to go with it.  That is what we really need.  Some functionality.

It's a known bug and is going to be fixed one way or the other.
There is a timetable for USC. Expecting everything that is in the spec to be implemented yesterday is unreasonable.

---

### Post by ranch hand on 2009-12-07
> **zekopeko said:**
> It's a known bug and is going to be fixed one way or the other.
There is a timetable for USC. Expecting everything that is in the spec to be implemented yesterday is unreasonable.
Now there is something that I think we can all agree on.

One thing that I will say for USC is that I really like the search function.  It seems to be quite flexible and nimble.

Now if I could only figure out why it won't load on Stoned Lizard.  There is also a problem with Update Manager and the Notifier for it that I think may actually be the problem.  I haven't worried about it because I don't use UM.  I guess I better hunt this down now though.

EDIT;
As I wrote that I was doing an apt-get upgrade.  It finally got UM straitened out and now USC loads on Stoned Lizard the same as on Daily and Lounge Lizard.

---

### Post by zekopeko on 2009-12-07
> **ranch hand said:**
> Now there is something that I think we can all agree on.

One thing that I will say for USC is that I really like the search function.  It seems to be quite flexible and nimble.

Now if I could only figure out why it won't load on Stoned Lizard.  There is also a problem with Update Manager and the Notifier for it that I think may actually be the problem.  I haven't worried about it because I don't use UM.  I guess I better hunt this down now though.

EDIT;
As I wrote that I was doing an apt-get upgrade.  It finally got UM straitened out and now USC loads on Stoned Lizard the same as on Daily and Lounge Lizard.

For further reading here is the blueprint that talks about non-application packages: [https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-non-applications-in-software-center](https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-non-applications-in-software-center)

The plan is to put them all in the System packages department and probably put them in sub categories based on type (similar how it's now in Synaptic)

---

### Post by zekopeko on 2009-12-07
> **mpt said:**
> It’s funny you should mention that. :) We want to do a [card sorting]("http://en.wikipedia.org/wiki/Card_sorting") exercise to help us work out what subcategories Ubuntu applications should be arranged in. This involves recruiting user test subjects, showing them 50 or so cards with information about applications and other packages, and getting them to arrange those cards into categories. But … we need someone with the time and mad skillz to figure out how to generate those printable cards. If you think you might be able to help out with this, please see [my post in the Programming Talk forum]("http://ubuntuforums.org/showthread.php?p=8456804").

As for what else you can help with, see the “[How you can help]("https://wiki.ubuntu.com/SoftwareCenter#contributing")” section of the spec. There’s plenty to do, whether you prefer coding, testing, artwork, design, or copywriting.

I'm lacking in the coding departments but will be willing to conduct card sorting test on my friends and family.
I'll also try and help with the various testing/design/etc work, time permitting.

> I’ve written up [an initial spec]("https://wiki.ubuntu.com/SoftwareCenter#reviewing") for how the review system should work, but implementing this is harder than it looks.

I followed the Gobby document from UDS. Looks like the heavy lifting will have to be done on the Launchpad side.

> Have you seen my initial write-up of “[Presenting add-on packages]("https://wiki.ubuntu.com/SoftwareCenter#add-ons")”? What do you think? (Unfortunately I haven’t had time to draw the mockup yet.)

A mockup would help to convey your approach to this.

> Thanks, I’ve added this as an unresolved issue.

Look at my suggestion here: [http://imgur.com/Tt21o](http://imgur.com/Tt21o)

> Yes, we need some sort of detailed properties window for a package like Synaptic has.

A "Technical info" button perhaps?

> We need to highlight the various screens in the “Get Free Software” section in a different way from the various screens in the “Installed Software” section, to reassure people about where they are. Currently, we use a colored background to do that. If GTK provided more theme colors, we’d gladly use one of them.

Perhaps color only the part where the location and search bar are? And color them based on the GTK theme color(s) by using some fancy math for complementary colors? Or is the point to have a single hardcoded color associated with a specific section?


> In v2 (if we manage to implement it), [selecting a row will expand it]("https://wiki.ubuntu.com/SoftwareCenter#software-list-view") to show buttons for the most common operations.

Nice to see something similar as how I envisioned it in the Karmic USC thread :D.

And what about the history of transactions?

BTW would it be better to have a nice cairo rendered "button/text" in the software list view, next to the name of the application right aligned, for the things that are installed? The check mark isn't very friendly since it's quite small and can blend with an icon.
I don't think that it will clutter the interface (like you mentioned iTunes does with the Buy button).

---

### Post by seeker5528 on 2009-12-09
> **mpt said:**
> 
Have you seen my initial write-up of “[Presenting add-on packages]("https://wiki.ubuntu.com/SoftwareCenter#add-ons")”? What do you think? (Unfortunately I haven’t had time to draw the mockup yet.)

I'm not overly attached to how the option is provided, the solution in the link sounds good and could potentially eliminate the desire to have a seperate option on whether to treat recommeds as dependencies, but....

How deep do you want to go with it?

If you select extras to install, and the extras have additional extras, are you going to show all of those at the top level, show a sub-tree, wait until the user chooses the extras they want then display the additional extras, only show the first level of extras?

If the default is to not treat recommends as depends generally speaking so you could limit the extras to those things that are actually listed as recommended/suggested by the main package selected for installation, then you could have those recommended packages checked by default without pulling in a bunch of stuff that is recommended by those extras.  

Is there a good enough payoff in attempting to make the extras feature overly clever and maintain it going forward versus a simpler implementation of the extras feature with a separate option on whether to treat recommends as dependencies. It would be acceptable to me if the option was only available to me at the time I install something and if I had to choose not to treat recommends as dependencies every time.

Also how do you deal with the situation where you have a dependency/recommends on a web browser or MTA for example, where there could be multiple packages that provide it, in particular where the packages are mutually exclusive?  

At some point it might also be desirable to have something like the 'missing recommends' view that Synaptic has.

Later, Seeker

---

### Post by seeker5528 on 2009-12-10
> **zekopeko said:**
> Perhaps a special sidebar entry with the label "Broken packages/applications". It should automatically scan for those when you start USC. If you try to start an application that is broken it should open USC and focus to this screen.

Here is how it could look: 
[http://imgur.com/Tt21o](http://imgur.com/Tt21o)

If you look at it from a more general perspective, maybe it would be more appropriate to call it 'Troubleshooting' than 'Broken packages'.

A failure during installation doesn't necessarily leave you with broken packages, so if there is a failure during installation a check for broken packages could be done immediately and if broken packages exist put any queued installations on hold and take the user to the troubleshooting section.

It might also be good when starting Software Centre and after a failed install to check for unconfigured packages and take the user to the troubleshooting section for that as well.

I would hope that initially clicking on fix would not resort to measures that are too drastic, but at the same time you have to assume that people will be installing stuff from outside the Ubuntu repositories, so I'm thinking after some failed attempts the user might be given a 'Get more help' option where the user can choose to go to the Ubuntu forums, maybe also have an option to pay to get support and possibly a 'Use bigger hammer' option that does the same thing as the repair function on the safe boot menu.

Later, Seeker

---

### Post by zekopeko on 2009-12-10
> **seeker5528 said:**
> If you look at it from a more general perspective, maybe it would be more appropriate to call it 'Troubleshooting' than 'Broken packages'.

I just used the easiest-to-think-up route when naming the section. The whole packages concept shouldn't be imposed on the end user. It's a technical term as much as a dll dependency is in Windows.

I wouldn't call it Troubleshooting but something along the lines of Failed App Installation or preferably something shorter.

> A failure during installation doesn't necessarily leave you with broken packages, so if there is a failure during installation a check for broken packages could be done immediately and if broken packages exist put any queued installations on hold and take the user to the troubleshooting section.

Queued installations shouldn't be paused if they can be safely installed. Why hold the install process of 20 apps if only one failed and the dependencies of the remaining apps don't use the ones from the failed package?

> It might also be good when starting Software Centre and after a failed install to check for unconfigured packages and take the user to the troubleshooting section for that as well.

I would hope that initially clicking on fix would not resort to measures that are too drastic, but at the same time you have to assume that people will be installing stuff from outside the Ubuntu repositories, so I'm thinking after some failed attempts the user might be given a 'Get more help' option where the user can choose to go to the Ubuntu forums, maybe also have an option to pay to get support and possibly a 'Use bigger hammer' option that does the same thing as the repair function on the safe boot menu.

Later, Seeker

That's why when installing the application from outside Ubuntu there should be an e-mail address of the packager so people can bug them.

---

### Post by seeker5528 on 2009-12-10
> **zekopeko said:**
> Queued installations shouldn't be paused if they can be safely installed. Why hold the install process of 20 apps if only one failed and the dependencies of the remaining apps don't use the ones from the failed package?

If they can be safely installed, yes. 

If the installation failure results in broken packages, any attempts to install anything else without resolving the broken status will fail.

Pending configurations are a little more of a question, there is a fair chance that the installation of the next thing will successfully trigger the pending configurations at which point they complete successfully, there is also a fair chance that the pending configuration status might be the result of an error during a package configuration that caused the installation to be aborted early, leaving one or more packages unconfigured, but not in a state that gets identified as broken and that further attempts to install stuff will always trigger the pending configuration and early abort before anything new even gets unpacked.

Later, Seeker

---

### Post by zekopeko on 2009-12-11
A mockup by Docky' DanRabbit:

[IMG]http://fc04.deviantart.net/fs50/f/2009/323/3/7/Redesigned_Software_Center_I_by_DanRabbit.png[/IMG]

Drool....

mpt you REALLY need to get someone to beautify the interface.

---

### Post by Merk42 on 2009-12-11
That mockup shows large images for both the icon and screenshot. Considering larger screenshots are available already, that itself shouldn't be too difficult to implement, right?

---

### Post by zekopeko on 2009-12-11
> **Merk42 said:**
> That mockup shows large images for both the icon and screenshot. Considering larger screenshots are available already, that itself shouldn't be too difficult to implement, right?

It's mostly how you format the description.

The app icon is inline with the rest of the text so you get more space for the icon and text since there is less wasted space. I would still put the Install button below the description because there are going to be other buttons (Install Addons etc).

And finally the screenshot has a sexy reflection.
It would rock if, when clicking on the picture would zoom it in such as Mac OSX does with quicklook ([http://www.youtube.com/watch?v=MqjH0_E4pxQ](http://www.youtube.com/watch?v=MqjH0_E4pxQ)).

---

### Post by tretle on 2009-12-11
You could do that if gloobus was integrated with lucid by default.

---

### Post by zekopeko on 2009-12-11
> **tretle said:**
> You could do that if gloobus was integrated with lucid by default.

Gloobus still has alooooooong way before it's any good. The art direction is...lacking.

---

### Post by Merk42 on 2009-12-11
Ugh, just looked in Lucid and I see Packages listed there. It kinda throws the design all off because now it's 13 categories (oh no unlucky in some parts of the world!).

I thought packages were going to be their own thing on the left sidebar?
If not the left sidebar seems like a big waste of space if it'll only contains at most:

Get Software
Free Software
Paid Software
Installed Software
In Progress

---

### Post by ronacc on 2009-12-11
I just did a fresh install of A1 and decided to use USC for my usual customization , a thoroughly horrible experience , while I try to be open minded ,after installing 10 packages O---    N---    E  ----      A ---   T ---      A  ---      T---    I ---   M ---   E   and having to reenter my password about every other package, I gave up an went back to synaptic . Before USC becomes even marginally acceptable it must have multiple select and a SINGLE entry of your sudo password for the entire time it is open and should when a package is selected show the depends AND recommends AND suggests and should allow the recommends and suggests to be selected without going back to the main list to search for them . On a fresh install I normally install from 50 to 100 additional packages and using USC in its present form would drive me to profanity.

---

### Post by ranch hand on 2009-12-12
Yes, unless you are simple minded and don't demand much from an installer it truely does suck the big one.

---

### Post by zekopeko on 2009-12-12
> **ronacc said:**
> I just did a fresh install of A1 and decided to use USC for my usual customization , a thoroughly horrible experience , while I try to be open minded ,after installing 10 packages O---    N---    E  ----      A ---   T ---      A  ---      T---    I ---   M ---   E   and having to reenter my password about every other package, I gave up an went back to synaptic . Before USC becomes even marginally acceptable it must have multiple select and a SINGLE entry of your sudo password for the entire time it is open and should when a package is selected show the depends AND recommends AND suggests and should allow the recommends and suggests to be selected without going back to the main list to search for them . On a fresh install I normally install from 50 to 100 additional packages and using USC in its present form would drive me to profanity.

> **ranch hand said:**
> Yes, unless you are simple minded and don't demand much from an installer it truely does suck the big one.

I L---O---V---E when you start comparing USC to Synaptic while completely ignoring the fact that USC still isn't replacing Synaptic!
And let's just forget , for the sake of pooping on USC the fact that it's prime designer still doesn't consider it a worthy replacement for Synaptic.

Now on to issues:

Having to reenter password is mostly likely a bug. Once you escalate your privileges they should remain escalated for some time (or at least while there is user activity + 60-90 seconds).

Clicking one package at a time is no different then how Synaptic does it so I don't see why the double standard. Not to mention that it USC2 will most likely lose the arrow thing and simply have the install button on the list view.

Recommends and suggests are also going to be fixed, that is displayed as addons.
There is also going to be a more detailed view like Synaptic does with properties so that you can see what and where the package installs and on what it depends etc.

And even better thing in the future is going to be saving a list of your favorite packages to UbuntuOne and simply clicking the list to install all of them.

All of this is one wiki page or in this thread. Please read.

---

### Post by VMC on 2009-12-12
I needed to install glchess, since the lucid engineers decided to keep it off. Tried to find it through my normal channels from aptitude.

Then remembered USC. It found it in a snap. I also liked the snapshot it gave.

It worked very well. Haven't tried installing multiple programs though.

---

### Post by seeker5528 on 2009-12-12
> **zekopeko said:**
> Clicking one package at a time is no different then how Synaptic does it so I don't see why the double standard. Not to mention that it USC2 will most likely lose the arrow thing and simply have the install button on the list view.

It is different than Synaptic, in Synaptic you have the option mark all the packages you want to install, then you choose to apply the action, and it does a single install operation.

I'm not really seeing that as a problem, I think the proposed mechanism for dealing with add-ons/extras will eliminate the need to search for a lot of individual packages, and unlike Synaptic you can search for and queue more stuff for installation while other stuff is being installed.

Later, Seeker

---

### Post by ranch hand on 2009-12-12
It also downloads in parallel.

---

### Post by ronacc on 2009-12-12
> **zekopeko said:**
> I L---O---V---E when you start comparing USC to Synaptic while completely ignoring the fact that USC still isn't replacing Synaptic!
And let's just forget , for the sake of pooping on USC the fact that it's prime designer still doesn't consider it a worthy replacement for Synaptic.

Now on to issues:

Having to reenter password is mostly likely a bug. Once you escalate your privileges they should remain escalated for some time (or at least while there is user activity + 60-90 seconds).

there you go again, I DID NOT COMPARE USC to synaptic .I merely remarked that after frustration with USC I reverted to it . I did not say a short time, I SAID UNTIL I CLOSE THE SESSION. I also said when the promised improvements arrive I will find USC acceptable .

---

### Post by zekopeko on 2009-12-12
> **ronacc said:**
> there you go again, I DID NOT COMPARE USC to synaptic .I merely remarked that after frustration with USC I reverted to it . I did not say a short time, I SAID UNTIL I CLOSE THE SESSION. I also said when the promised improvements arrive I will find USC acceptable .

Ok fair enough. But you still blasted the thing without taking into consideration that it's not finished and that the missing features are planned for inclusion.

Having an app run with escalated privileges while open is a security risk. What if I you move away from the computer but forget to close USC/Synaptic?

If the app can be smart then why not? As long as the app has focus or there is user activity (mouse moving, typing etc) USC should have escalated privileges. As soon as there is no activity for 60-90 seconds it should lose escalated privileges.

---

### Post by seeker5528 on 2009-12-12
> **zekopeko said:**
> If the app can be smart then why not? As long as the app has focus or there is user activity (mouse moving, typing etc) USC should have escalated privileges. As soon as there is no activity for 60-90 seconds it should lose escalated privileges.

Unless I am mistaken, apt-daemon is used so USC doesn't need to have escalated privileges, ever, there is just a brief escalation somewhere when the install is initiated, so the password thing would be a side effect of that. That's not to say USC couldn't cache the password temporarily under certain conditions and/or have the option to save it for the session so the user doesn't have to keep being asked to supply it.

Later, Seeker

---

### Post by ronacc on 2009-12-12
I will admit that leaving an app run as root however it is a risk I am willing to take in some circumstances . I often find it convenient to have my package installer (note! I did not use "the dreaded name") open while I am mostly doing something else so that I can unminimize it , install what is needed and minimize it again without constantly opening and closing it  .

---

### Post by mpt on 2009-12-13
> **ronacc said:**
> for USC I would as I stated earlier like to see the ability to multi-select packages to be qued before installation begins

Can you give an example of a situation where this would be more useful than starting the installation straight away?

> **ranch hand said:**
> C>Uses the same stupid "lets open another screen for the description with no good way back" used in Add/Remove.

You can click the department in the path button to go back. In 2.0 hopefully we&#8217;ll add [Back and Forward buttons]("https://wiki.ubuntu.com/SoftwareCenter#Back/Forward%20navigation") to make it more obvious.

> *D>Even Add/Remove had check boxes by the apps so you could check several for installation (or removal) at once.  This is just plumb silly.  When you are setting up a new install you have several packages you want to install.  One at a time is a real time waister.  Nearly on the level of RPMs (while you can install more than one at a time they come in one at a time and your connection has to restart from 0Kb/s for every one).  Using Apt or Synaptic and getting multi-packages the connection stays, in my case, flat lined at about 300Kb/s.*

Let&#8217;s say you have two packages to install, *A* and *B*.

With Synaptic, you mark *A* for installation, mark *B* for installation, click Apply, and confirm it. *A* downloads, then *B* downloads, then *A* installs, then *B* installs. As far as I can tell, it does not download anything in parallel.

With Ubuntu Software Center v1, you click &#8220;Install&#8221; for *A*. It starts downloading. While that&#8217;s happening, you find B and click &#8220;Install&#8221;. *A* finishes downloading, then *A* installs, then *B* downloads, then *B* installs.

They&#8217;re doing exactly the same tasks, just in a different order. Ubuntu Software Center probably loses a little ground because it launches dpkg twice. But it ends up being much faster than Synaptic, because while you&#8217;re choosing *B*, *A* is already downloading and installing.

Now, it&#8217;s all very well the Ubuntu Software Center being faster, but if it *seems* slower to you and to others (which seems to be the case), that&#8217;s a problem we should fix. I&#8217;m sure there&#8217;s some way we can make it seem faster without making it actually slower. Separately, we should also figure out how to download *B* while installing *A*, to make it faster still.

> **zekopeko said:**
> I'm lacking in the coding departments but will be willing to conduct card sorting test on my friends and family.
I'll also try and help with the various testing/design/etc work, time permitting.

Thanks!

> *And what about the history of transactions?*

[That still needs design work]("https://wiki.ubuntu.com/SoftwareCenter/History"), and plumbing changes to record the transactions. It isn&#8217;t on the critical path for 2.0.

> *BTW would it be better to have a nice cairo rendered "button/text" in the software list view, next to the name of the application right aligned, for the things that are installed? The check mark isn't very friendly since it's quite small and can blend with an icon.*

I&#8217;m not sure what you mean. Could you provide a mockup?

> **seeker5528 said:**
> If you select extras to install, and the extras have additional extras, are you going to show all of those at the top level, show a sub-tree, wait until the user chooses the extras they want then display the additional extras, only show the first level of extras?

That&#8217;s an excellent question. Do you know of any packages in Ubuntu with add-on chains like this? As you suggested, I think that in an initial implementation we&#8217;d just go one level deep, and for levels lower than that use the standard apt approach of installing Recommends but not Suggests.

> *Also how do you deal with the situation where you have a dependency/recommends on a web browser or MTA for example, where there could be multiple packages that provide it, in particular where the packages are mutually exclusive?*

Also an excellent question. I guess we could show a menu or something for choosing which of the providers to install. I&#8217;ve [added a note about it]("https://wiki.ubuntu.com/SoftwareCenter?action=diff&rev2=271&rev1=270").

> *At some point it might also be desirable to have something like the 'missing recommends' view that Synaptic has.*

True. I&#8217;ve noted that too so I don&#8217;t forget about it. Thank you!

> **zekopeko said:**
> But you still blasted the thing without taking into consideration that it's not finished

In ronacc&#8217;s defence, software is hardly ever &#8220;finished&#8221;, so it&#8217;s perfectly reasonable to blast version 1 of something. :) It&#8217;s not enough to be awesome in the future; we need to be awesome now.

---

### Post by ranch hand on 2009-12-13
I update through synaptic a lot of the time and there are many times that 2 or even 3 packages are downloading at once, just as they do in Apt.

---

### Post by ronacc on 2009-12-13
by playing around I found how to select another package while one is downloading , rather inobvious , why doesn't it send you back to the selection screen rather than an info screen where no further action is possible without clicking out of it in  non obvious way .

---

### Post by Merk42 on 2009-12-13
So as I said before, System Packages just kinda being down there where you ahve to scroll throws off the whole nice layout of USC.

Of course 13, aside from an unlucky number, is also prime.

So I did a mockup of how it would look in a sort of beehive pattern, also changed the icon for System Packages.
[img]http://www.markecurtis.com/etc/usc-lucid-mockup.png[/img]

---

### Post by zekopeko on 2009-12-13
> **mpt said:**
> I’m not sure what you mean. Could you provide a mockup?

Something like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=139730&stc=1&d=1260737864[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=139731&stc=1&d=1260737864[/IMG]



> In ronacc’s defence, software is hardly ever “finished”, so it’s perfectly reasonable to blast version 1 of something. :) It’s not enough to be awesome in the future; we need to be awesome now.

IMO it's OK blasting v1 when compared to Add/Remove, but comparing it to something that is striving to replace but is still far from doing is not OK. I don't see people comparing MS Paint to Photoshop ;).

---

### Post by zekopeko on 2009-12-13
> **Merk42 said:**
> So as I said before, System Packages just kinda being down there where you ahve to scroll throws off the whole nice layout of USC.

Of course 13, aside from an unlucky number, is also prime.

So I did a mockup of how it would look in a sort of beehive pattern, also changed the icon for System Packages.

Not gonna work IMO. Try laying it on a grid. It doesn't have to form a rectangle with the outer edges.

---

### Post by zekopeko on 2009-12-13
> **ronacc said:**
> by playing around I found how to select another package while one is downloading , rather inobvious , why doesn't it send you back to the selection screen rather than an info screen where no further action is possible without clicking out of it in  non obvious way .

Yeah this is confusing. Back and forward are planned to mitigate a part of this problem. But in the future it's planned to have progress directly there in the main pane so that you don't have to be moved to the In Progress view.

---

### Post by ronacc on 2009-12-13
@ MPT  > Can you give an example of a situation where this would be more useful than starting the installation straight away?
I often install multiple files at a time and keeping track of what is already selected is easier if presented with a list of what is going to be installed rather than trying to see what has already finished d/l'ing what is in progress and what is qued . A typical situation would be where I have a list of packages I wish to install and I can readily compare it to a list of selected packages to make sure I have all of them selected , this would be nowhere near as easy with packages in flux through 3 different states dynamicaly .

---

### Post by Kazade on 2009-12-14
> **zekopeko said:**
> Something like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=139730&stc=1&d=1260737864[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=139731&stc=1&d=1260737864[/IMG]


I think it might be better if installed software didn't have the description line and instead said "Already installed" with some kind of colour (maybe a green outline or background) to differentiate it from software that isn't installed.

---

### Post by Podex on 2009-12-14
> **Kazade said:**
> I think it might be better if installed software didn't have the description line and instead said "Already installed" with some kind of colour (maybe a green outline or background) to differentiate it from software that isn't installed.

I don't think that's a good idea. The descriptions should stay since it can be the case that someone installed something but later forgets what it is for. Having a description in USC can be helpful then.

---

### Post by seeker5528 on 2009-12-15
> **mpt said:**
> That’s an excellent question. Do you know of any packages in Ubuntu with add-on chains like this? As you suggested, I think that in an initial implementation we’d just go one level deep, and for levels lower than that use the standard apt approach of installing Recommends but not Suggests.

If I'm running Kubuntu and want to install Totem, it recommends totem-plugins which recommends gnome-settings-daemon.

If I am running a non-KDE variant and install Digikam, it recommends kipi-plugins which recommends Konqueror which recommends konqueror-nsplugins.

Later, Seeker

---

### Post by Gina on 2009-12-15
Don't think this is quite true, is it?> When 10.04 releases, the Ubuntu Software Center will finally take over as the sole installation tool for Ubuntu. Synaptic, GDebi, and even the update manager will all be replaced by USC.One of my Ubuntu loving friends is worried that he'll no longer be able to download a .deb package and just click on it to install it.  He's also worried about losing Synaptic and thinks he'll have to use CLI to install specific packages. I told him I didn't think so.
[URL="http://www.ghacks.net/2009/12/11/what-will-ubuntu-10-04-bring-to-the-table/"]
*_Link to report on ghacks.net here_*[/URL]

---

### Post by seeker5528 on 2009-12-15
> **ranch hand said:**
> I update through synaptic a lot of the time and there are many times that 2 or even 3 packages are downloading at once, just as they do in Apt.

That's an apt thing, if you have multiple repositories enabled. 

So if you have the ubuntu repository, medibuntu repository, and a PPA, that's 3 repositories, potentially 3 packages downloading at a time, assuming they all have updates on a given day.

If you have multiple sources for the same repository, it's still one repository, you still only get one package from that repository at a time, also there are potential problems if both mirrors are not in sync with each other, at least that's the way it used to work.

Later, Seeker

---

### Post by zekopeko on 2009-12-15
> **Gina said:**
> Don't think this is quite true, is it?One of my Ubuntu loving friends is worried that he'll no longer be able to download a .deb package and just click on it to install it.  He's also worried about losing Synaptic and thinks he'll have to use CLI to install specific packages. I told him I didn't think so.
[URL="http://www.ghacks.net/2009/12/11/what-will-ubuntu-10-04-bring-to-the-table/"]
*_Link to report on ghacks.net here_*[/URL]

Tell your friend that she should read better publications. Nowhere does it  say, in the official spec that USC2 **will** replace all those tools in Lucid just that it's planned.

Here is Lucid in the wiki:
[https://wiki.ubuntu.com/SoftwareCenter#April 2010](https://wiki.ubuntu.com/SoftwareCenter#April 2010)

And here is a quote (emphasis mine)

> For Ubuntu 10.04 LTS, we **plan** to:

---

### Post by ranch hand on 2009-12-15
Geeze I hate to defend this USC project but I guess I have to in this case.

If it replaces synaptic et all, they will not be gone.  Like gimp, they will be in the repos for those of us that want something that works.  There is no need for panic.

Apt will obviously be there as it is still the backend for all of the package management.

---

### Post by Gina on 2009-12-15
Thanks for the replies - I've passed him a link to here :)

---

### Post by camporter1 on 2009-12-15
In the new software center, will there be a way to browse personal repositories on launchpad or other locations? 

Also, right now, I find the start page for software center to be quite uninteresting. I know the software center is meant to be simple and easy to use, but it would be a nice touch to have featured software, recommended software, etc. included as well. 

Another thing that I believe lots of new users would find useful is something that might suggest alternative software for the user. An example might be OpenOffice and the Gnome replacements of them. That would probably require a separate server to map those relationships, so I don't really expect that to happen.

---

### Post by castrojo on 2009-12-15
> **cariboo907 said:**
> I too am starting to wonder if I like the direction Canonical is taking. I understand what the goal is, but for some of us advanced users it seems like a step backward sometimes.

Do you have any examples of what is becoming "backwards" for advanced users?

---

### Post by zekopeko on 2009-12-16
> **camporter1 said:**
> In the new software center, will there be a way to browse personal repositories on launchpad or other locations? 

Also, right now, I find the start page for software center to be quite uninteresting. I know the software center is meant to be simple and easy to use, but it would be a nice touch to have featured software, recommended software, etc. included as well. 

Another thing that I believe lots of new users would find useful is something that might suggest alternative software for the user. An example might be OpenOffice and the Gnome replacements of them. That would probably require a separate server to map those relationships, so I don't really expect that to happen.

USC will have all the things you mentioned.

Here is how version 4 should look: [https://wiki.ubuntu.com/SoftwareCenter#Eventual](https://wiki.ubuntu.com/SoftwareCenter#Eventual) scope.

Mapping alternative names to software is planned(maybe not in this release). It will reflect in searching e.g. search for Photoshop you get GIMP etc.

---

### Post by Merk42 on 2009-12-16
So hey guys, how about that Ubuntu Software Center?

---

### Post by zekopeko on 2009-12-16
> **Merk42 said:**
> So hey guys, how about that Ubuntu Software Center?

From the looks of it it's starting to kick *** and take names :)

---

### Post by Merk42 on 2009-12-16
> **ronacc said:**
> booting from a liveCD in order to download pictures off my camera with Fspot would be an even more limited use case.

Reply moved to more relevant [Bye Bye GIMP! thread](http://ubuntuforums.org/showthread.php?p=8510691#post8510691)

---

### Post by Gina on 2009-12-16
I have continued my comments on removing gimp from the Live CD in the more appropriate thread.

---

### Post by Merk42 on 2009-12-16
> **Gina said:**
> I have continued my comments on removing gimp from the Live CD in the more appropriate thread.

Ah good, let's get this thread back on track then.



So if in the eventual scope of USC you'll be able to download stuff like wallpapers, why won't you be able to download music through it instead of/in addition to Rhythmbox?

---

### Post by zekopeko on 2009-12-16
> **Merk42 said:**
> Ah good, let's get this thread back on track then.

So if in the eventual scope of USC you'll be able to download stuff like wallpapers, why won't you be able to download music through it instead of/in addition to Rhythmbox?

Makes more sense to have in the music player wouldn't you say? That way you can download and listen instantly.

It's Ubuntu **Software** Center after all :P

---

### Post by ronacc on 2009-12-16
If USC aspires to be a "one stop for add ons" then the addition of music ( and podcasts ? ) would certainly seem logical . We would ofcourse have to have the ability to add our own selection of "repos" and also define where downloaded music was stored in rather fine detail .

---

### Post by Merk42 on 2009-12-16
> **zekopeko said:**
> Makes more sense to have in the music player wouldn't you say? That way you can download and listen instantly.

It's Ubuntu **Software** Center after all :P

Yes, but in the scope it's planned to be able to download/install things like Themes and Fonts.  I wouldn't consider them **software** either.

---

### Post by zekopeko on 2009-12-16
> **Merk42 said:**
> Yes, but in the scope it's planned to be able to download/install things like Themes and Fonts.  I wouldn't consider them **software** either.

They directly modify software. So they surely fall under the software category. Wallpapers are simply complementary to the theming as are icons or other art.

---

### Post by Merk42 on 2009-12-16
Can we talk about USC again, please?

I'm not saying opinions on the LiveCD are wrong or anything, just that they don't belong in this thread.

---

### Post by zekopeko on 2009-12-17
> **Merk42 said:**
> Can we talk about USC again, please?

I'm not saying opinions on the LiveCD are wrong or anything, just that they don't belong in this thread.

Ok, ok! I finally had to install Lucid in Virtualbox since USC doesn't work from trunk (using xapian that is too new).

The system packages need to have different icons IMO. Easier to identify.

---

### Post by mpt on 2009-12-17
> **ronacc said:**
> by playing around I found how to select another package while one is downloading , rather inobvious , why doesn't it send you back to the selection screen rather than an info screen where no further action is possible without clicking out of it in  non obvious way .

The main reason was to make it clear that it actually *is* installing. As zekopeko said, ideally we’ll show progress on the software item screen itself (as well as in the “In Progress” section), so that we don’t need to switch to the “In Progress” section every time you start installing or removing something.

> **Merk42 said:**
> So as I said before, System Packages just kinda being down there where you ahve to scroll throws off the whole nice layout of USC … So I did a mockup of how it would look in a sort of beehive pattern, also changed the icon for System Packages.

Thanks for the idea. But once we have the categorization sorted out, we’ll be merging “System Packages” and “Other”. There’s no point having two separate “miscellaneous” departments. :)

> **zekopeko said:**
> Something like this:…

Ah, I see. I think probably we could do that in a more compact way by having an Installed column at the left of the list.

> **ronacc said:**
> I often install multiple files at a time and keeping track of what is already selected is easier if presented with a list of what is going to be installed rather than trying to see what has already finished d/l'ing what is in progress and what is qued . A typical situation would be where I have a list of packages I wish to install and I can readily compare it to a list of selected packages to make sure I have all of them selected , this would be nowhere near as easy with packages in flux through 3 different states dynamicaly .

That seems like it could be handled by a history view.

As part of our work to replace apturl, we’ll also be adding ad-hoc lists: for example you could enter “package1,package2,package3,package4” in the search field, which would display a list of those four packages, and then you could click an “Install All” button at the bottom of the list.

> **ronacc said:**
> If USC aspires to be a "one stop for add ons"

No, not really.

> **Merk42 said:**
> Yes, but in the scope it's planned to be able to download/install things like Themes and Fonts.  I wouldn't consider them **software** either.

Being able to browse and install fonts from within a dedicated font manager, and background pictures from within the Appearance preferences, would be both more discoverable and more efficient than doing the same within the Ubuntu Software Center. That doesn’t mean you shouldn’t be able to install fonts and theme packages from the Ubuntu Software Center (and it would be cool if someone could [generate font previews]("http://twitter.com/mpt/status/6691562107") to improve that), but it’s not the ideal interface.

---

### Post by xir_ on 2009-12-17
Hey MPT Forgive me if any of this had been covered and feel free to ignore all of this if its just silly. But i have a few ideas.

Would it be possible for the software store to have a browser add-on section. Even if it just links to the default browsers add-on homepage?

The current way of looking at the applications once you have a defined list of options is not very intuitive for me, as i don't like having to go backwards and forwards. However a mouse over preview with just a little info would be great.

Will you be able to include your popularity contest data to the applications?

A link to some of the more popular PPA's from inside the software store would be good, even if it has a big read warning saying they are untrusted and may be unstable. It would be great to see chrome's PPA as an option. It would kind of be like enabling back ports in a sense for people who might want newer software. These could appear with a fav icon type approach on the left hand list under the "free software" menu.

Enable the ability to restore the system back to its livecd install state. i.e just a backup list of packages with version numbers. Or just put the ubuntu logo next to items which were installed by default. 

Also down the line a stability warning would be good, i.e if packages that are submitted as stable releases are highlighted more green and unstable packages are highlighted red to help users know if things are stable or not.

Launchpad links for filing bug reports at the bottom of the applications details.

Could a lock icon be put on on items which would result in the ubuntu desktop being removed upon their de installation. New users might not know what it means to uninstall the ubuntu desktop package.


This is a bit outside the rest but a link to the canonical store so that livecd could be ordered (as well as mugs), might make the left hand list just a little less empty.


ok that's my brain dump.

---

### Post by 23meg on 2009-12-17
Recent off-topic posts have been moved to [a more relevant thread]("http://ubuntuforums.org/showthread.php?t=1330937"). Please keep this thread to discussion of USC.

---

### Post by zekopeko on 2009-12-17
One awesome thing that USC could do is show me all the packages that didn't come with the default install or from the official repos.

---

### Post by amano on 2009-12-18
Seconded. Please make it pretty obvious, which are the files that got installed by default, those that are supported and others. Maybe color codes could be used (green font items are default ubuntu packages, brown ones are supported ones and black ones are packages which probably just work.

---

### Post by zekopeko on 2009-12-18
> **amano said:**
> Seconded. Please make it pretty obvious, which are the files that got installed by default, those that are supported and others. Maybe color codes could be used (green font items are default ubuntu packages, brown ones are supported ones and black ones are packages which probably just work.

Or even better: Add custom search filters ala Nautilus or like Banshee's smart playlists.

---

### Post by zekopeko on 2009-12-24
AFAIK software-center uses webkit for its main pane.
So if you are a web designer you could design a proposed look for the Lobby Screen or the Application Screen as seen here: [Software item screen]("https://wiki.ubuntu.com/SoftwareCenter#Software item screen")

---

### Post by gnomeuser on 2009-12-25
> **zekopeko said:**
> Or even better: Add custom search filters ala Nautilus or like Banshee's smart playlists.

Smart playlists in Banshee are very powerful but for this specific use case they do seem like overkill and the cost in complexity of adding such support in the UI could be grave. Having a simple color code or a little icon akin to what Banshee now does for CC content might be good.

"first prize emblem" for fully supported and recommended applications
"thumbs up" supported
"nothing" for unsupported.

Another addition that might be nice would be to call out to Launchpad to see some bug statistics and commit activity to add emblems to indicate if the application is well maintained, if it appears overtly buggy (say bug count rises while commits decreased - some such heuristic could be made meaningful I suspect). This would compliment user rating and reviews with some real data to give the user some idea of what to expect.
You could also add the "here be dragons" type emblem for applications that are new and thus unknown to such a system.

One thing I have noticed on my new Android phone is that when you uninstall an application it asks you why with some predefined answers. Maybe having something inspired by that to give some feedback to developers would be good. 
Default answers such as "Unstable", "Lacks important functionality", "Slow", "Didn't like", "Prefer not to say" might suit Ubuntu.

Finally having some way to indicate the target audience might be good. E.g. when displaying results favor applications that suit the users environment. You could also indicate GIMP e.g. being a Power User tool whereas Banshee would be End User Friendly.

---

### Post by papangul on 2009-12-25
I find the menu bar to be very boring, outdated and out of place on USC.:(

Could it be replaced with small icon based drop-down menu like the one found on google-chrome?

---

### Post by mpt on 2010-03-07
Sorry I lost track of this thread …

> **xir_ said:**
> Would it be possible for the software store to have a browser add-on section. Even if it just links to the default browsers add-on homepage?

I’ve specced [a general add-on interface]("https://wiki.ubuntu.com/SoftwareCenter#add-ons") that I hope someone will implement one day,  and I used Firefox as an example there, because Firefox seems to have more add-ons in the Ubuntu repositories than anything else does.

But the case of browser add-ons is awkward, because a browser vendor’s add-on directory will usually be much more interesting to add-on developers than the Ubuntu repositories will. Add-ons are (afaik) easier to package in the browser’s format than they are as a .deb, they don’t need to be packaged separately for each OS the browser runs on, and they can be introduced and updated irrespective of the Ubuntu release cycle. The main disadvantage is that the browser vendor has to maintain the add-on directory and installation mechanism, but they have to do that anyway if the browser also runs on Windows or Mac. And installing from within the browser installs an add-on just for you, not for everyone on the system; sometimes that’s what you want, and sometimes it isn’t.

Pretty much exactly the same awkwardness plays out with Ruby Gems in Ubuntu. For example, which is the best way to install Ruby on Rails — “sudo apt-get install rails”, or “sudo gem install rails”? [The two packaging schemes have been fighting it out for years.]("http://pkg-ruby-extras.alioth.debian.org/rubygems.html")

So, eventually I think we’ll have to figure out an elegant way for apt-powered add-on installation and software-specific add-on installation to co-exist. I have no idea what that will look like.

> *The current way of looking at the applications once you have a defined list of options is not very intuitive for me, as i don't like having to go backwards and forwards. However a mouse over preview with just a little info would be great.*

What kind of info, specifically? We already show the icon, the title and summary, the median rating and number of reviews. Often the first part of the description isn’t that interesting. (In a software [card sorting]("http://usability.gov/design/cardsort.html") exercise at Canonical last week, one participant actually said words to the effect of, “it’s not until you get to the second line that you figure out what the software is for”.) We’ve recently added Back and Forward buttons, which should make it easier to go back.

> *Will you be able to include your popularity contest data to the applications?*

Yes. We’re concentrating on showing rating for 2.0, because it’s more interesting than popularity. But eventually we’ll show not just popularity amongst Ubuntu users in general, but popularity amongst your friends in particular.

> *A link to some of the more popular PPA's from inside the software store would be good, even if it has a big read warning saying they are untrusted and may be unstable. It would be great to see chrome's PPA as an option. It would kind of be like enabling back ports in a sense for people who might want newer software. These could appear with a fav icon type approach on the left hand list under the "free software" menu.*

We’ve now done the second part of this, splitting out individual software sources including PPAs. Making it possible to search *for* PPAs, and tell which ones are trustworthy, is a future challenge.

> *Enable the ability to restore the system back to its livecd install state. i.e just a backup list of packages with version numbers. Or just put the ubuntu logo next to items which were installed by default.*

The first part of that is an excellent idea. (Anyone want to implement it? Basically porting Synaptic’s “Save Markings” command.) The second part would be taking the Ubuntu logo in vain.

> *Also down the line a stability warning would be good, i.e if packages that are submitted as stable releases are highlighted more green and unstable packages are highlighted red to help users know if things are stable or not.*

I don’t know how we’d convey that in a way that made sense.

> *Launchpad links for filing bug reports at the bottom of the applications details.*

I’m more interested in designing ways for Ubuntu QA staff to handle the deluge of bug reports, than in designing things that would increase the deluge. :)

> *Could a lock icon be put on on items which would result in the ubuntu desktop being removed upon their de installation. New users might not know what it means to uninstall the ubuntu desktop package.*

There’s supposed to be an alert: “{title} is a core item in Ubuntu. Removing it may cause future upgrades to be incomplete.” (I haven’t checked whether it’s implemented yet.) I doubt that a padlock would be a suitable metaphor for that.

> *This is a bit outside the rest but a link to the canonical store so that livecd could be ordered (as well as mugs), might make the left hand list just a little less empty.*

Nah, that would be cheesy. :P There’s plenty that will appear in that pane in future.

Thanks for all your ideas!

> **zekopeko said:**
> One awesome thing that USC could do is show me all the packages that didn't come with the default install or from the official repos.

We [nearly got there]("https://wiki.ubuntu.com/SoftwareCenter#channels"), but [not quite]("http://launchpad.net/bugs/524379").

> **gnomeuser said:**
> Smart playlists in Banshee are very powerful but for this specific use case they do seem like overkill and the cost in complexity of adding such support in the UI could be grave.

Yeah, it’s not clear to me why you’d want to maintain a custom search for any length of time. A custom list, sure (so you can share it with others), but not a search.

> [i]Another addition that might be nice would be to call out to Launchpad to see some bug statistics and commit activity to add emblems to indicate if the application is well maintained, if it appears overtly buggy (say bug count rises while commits decreased - some such heuristic could be made meaningful I suspect). This would compliment user rating and reviews with some real data to give the user some idea of what to expect.
You could also add the "here be dragons" type emblem for applications that are new and thus unknown to such a system.[/i]

Yes, at the very least we’ll have some sort of danger sign for third-party repositories, decreasing to the extent that people have said they trust it.

> [i]One thing I have noticed on my new Android phone is that when you uninstall an application it asks you why with some predefined answers. Maybe having something inspired by that to give some feedback to developers would be good. 
Default answers such as "Unstable", "Lacks important functionality", "Slow", "Didn't like", "Prefer not to say" might suit Ubuntu.[/i]

Maybe, but [on the other hand]("http://twitter.com/hotdogsladies/statuses/5985647059")…

> *Finally having some way to indicate the target audience might be good. E.g. when displaying results favor applications that suit the users environment.*

I expect we’ll have age/content ratings eventually, especially (but [not only]("http://lwn.net/Articles/113644/")) for games.

> *You could also indicate GIMP e.g. being a Power User tool whereas Banshee would be End User Friendly.*

Unfortunately that’s subject to all the same kind of problems as asking people to choose whether they’re “beginner”, “intermediate”, or “advanced”. I’m highly experienced with Thunderbird, but know very little of Gimp. So am I a “power user” or not?

---

### Post by zekopeko on 2010-03-08
> **mpt said:**
> Sorry I lost track of this thread &#8230;

Me too, and I started it :P


> 
We [nearly got there]("https://wiki.ubuntu.com/SoftwareCenter#channels"), but [not quite.]("http://launchpad.net/bugs/524379")

Yeah, it&#8217;s not clear to me why you&#8217;d want to maintain a custom search for any length of time. A custom list, sure (so you can share it with others), but not a search.

I think that having functionality similar to Banshee's smart playlists would be a great addition. Smart playlists are basically saved searches that are auto-updated.

You could have auto-generated ones by default and allow the user to add others. After you allow sharing of lists with others it would allow minimal user interaction to update the list.

Lets say I create a list that has FPS games that I rated 5 stars. When I install a new one there is zero effort from the initial creation of the list to update it. USC does it for me and notifies my friends that I've updated the list.

---

### Post by Speed_arg on 2010-03-08
When you are downloading something, and you want to download something else (what should queue it) it is buggy and it lags and you have to click like 4 times to add it to the queue.

Please somebody try it and report this bug.

---

