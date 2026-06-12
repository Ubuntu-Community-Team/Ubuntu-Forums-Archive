---
title: "AppCenter or Synaptic?"
date: 2009-07-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Slug71 on 2009-07-18
So theres been a lot of discussion about package management in Karmic and specially this new AppCenter.

How many of you would just prefer to keep Synaptic?

---

### Post by taavikko on 2009-07-18
for me aptitude is quite satisfactory.

But for the GUI for the Average Joe, anything that removes the confusion of multiple location to "add/remove"/synaptic/software_sources or any other to do the handling of repositories and packages to a single Frontend.

---

### Post by autocrosser on 2009-07-18
I would like to see AppCentre side-by-side with Synaptic on my system to choose..I've used Synaptic for several years now & like how it works, but I want version details available like we got in Update-manager with the gconf key.

---

### Post by ronacc on 2009-07-18
why not keep both , atleast for a few release cycles , synaptic is one of those things that "just works" . to dump it for a new shiny would be an error .

---

### Post by ELD on 2009-07-18
So now it's this, synaptic and add/remove? wth?

---

### Post by Slug71 on 2009-07-18
> **taavikko said:**
> for me aptitude is quite satisfactory.

But for the GUI for the Average Joe, anything that removes the confusion of multiple location to "add/remove"/synaptic/software_sources or any other to do the handling of repositories and packages to a single Frontend.

I like the idea/concept of having an 'all-in-one' GUI but im not convinced its a good idea.

The way ubuntu is now works and has worked for a long time with little to no complaints. 

I think the proposed GUI could seem overwhelming to newbs and also putting everything in front of them like that could lead to some breakage by messing around with something they normally wouldnt.

---

### Post by Merk42 on 2009-07-18
Wow I must be out of the loop, I thought AppCenter was some bigger thing than may or may not use Synaptic and/or PackageKit for a backend.

---

### Post by taavikko on 2009-07-18
> **Slug71 said:**
> I like the idea/concept of having an 'all-in-one' GUI but im not convinced its a good idea.

this would indeed make sense, like the gnome-appearance-properties

[quote=Slug71]I think the proposed GUI could seem overwhelming to newbs and also putting everything in front of them like that could lead to some breakage by messing around with something they normally wouldnt.[/QUOTE]

Newbies doesn't care what is brought under their nose, they will still continue to break their systems :D

Enough from OT. the idea of tabbed interface that control two basic use-cases
Repositories/package handling
Now synaptic can handle the repos and package handling, but there is still existent
software-properties for solely on repos.
Add/remove for package handling
gdebi for package installing and so on.
Bringing all of this together would be huge usability fix... IMHO
How much can someone really mess up? recovering from those is trivial.

---

### Post by Slug71 on 2009-07-18
> **Merk42 said:**
> Wow I must be out of the loop, I thought AppCenter was some bigger thing than may or may not use Synaptic and/or PackageKit for a backend.

As i understand it, it could be based on one of them but wont use them as a backend. I know PK add/remove is being considered as a possible basis for it. But since PK and Synaptic are frontends im not sure how they can be used as a backend.

---

### Post by Slug71 on 2009-07-18
> **taavikko said:**
> this would indeed make sense, like the gnome-appearance-properties



Newbies doesn't care what is brought under their nose, they will still continue to break their systems :D

Enough from OT. the idea of tabbed interface that control two basic use-cases
Repositories/package handling
Now synaptic can handle the repos and package handling, but there is still existent
software-properties for solely on repos.
Add/remove for package handling
gdebi for package installing and so on.
Bringing all of this together would be huge usability fix... IMHO
How much can someone really mess up? recovering from those is trivial.

Wouldnt it be a lot less work to make a GUI for Synaptic like this then instead of writing something from the ground up?

---

### Post by Regenweald on 2009-07-18
I think that it was pretty obvious from the appcentre wiki that it is intended to be a primium blend of Gdebi Add-Remove and Synaptic. It is very easy to envision an easy to use front end that is very simple to use for new users but with all of synaptics' advanced features simply placed in 'Preferences' as configurable options.

Lets say we take the existing Add-Remove interface, put a button on the front to install a .deb and also add the functionality that we have with themes so that one can simply drag a .deb into the open window to initiate an install.

All displayed packages would have an 'expand' button next to it so that users can drill down to see synaptic like details of dependencies/properties etc. Then the more advanced synaptic features can be options that could be easily integrated into the GUI as per each users needs by turning them on in preferences.

At this early stage without even a beta to test of the new appcentre, the: 'Well this works good enough for me, why do we need to improve?' attitude is wholly unnecessary. We are not loosing anything, the intention is to create a richer central interface. At times like this the 'community' fails linux miserably. Someone still sore on packagelit ?

---

### Post by 23meg on 2009-07-18
> **Slug71 said:**
> Wouldnt it be a lot less work to make a GUI for Synaptic like this then instead of writing something from the ground up?

1) Probably no, and "as little work as possible" isn't always the optimal path anyway.

2) AppCenter will be based on gnome-app-install for the most part, not written from the ground up.

---

### Post by ghindo on 2009-07-18
We don't even know what AppCenter will *look* like, so I'm not sure how we can really compare the two.

---

### Post by ronacc on 2009-07-18
if app center is based on gnome app install it will be as worthless as gnome app install .

---

### Post by wayne_cat on 2009-07-18
> **ghindo said:**
> We don't even know what AppCenter will *look* like, so I'm not sure how we can really compare the two.

[http://news.softpedia.com/news/Ubuntu-AppCenter-112572.shtml](http://news.softpedia.com/news/Ubuntu-AppCenter-112572.shtml)

and

[https://wiki.ubuntu.com/AppCenter](https://wiki.ubuntu.com/AppCenter)

---

### Post by ronacc on 2009-07-18
reading the "rationale" section of the wiki page synaptic already does everything that they propose app center to do and does it with a minimum of fuss . If they want to simplify things get rid of software sources ,gnome-app install, and update-manager and let synaptic handle all of it , it already does .This is of course refering to gui package-management , terminal types will continue to use apt and dpkg .

edit: and while they are at it get rid of that useless xapian search function in synaptic .

---

### Post by gnomeuser on 2009-07-18
Neither, I don't see either one really presenting progress.

---

### Post by ibutho on 2009-07-18
Is AppCenter installed by default? I just ran the latest Karmic live cd, but I don't think I saw an app called AppCenter.

---

### Post by TheNosh on 2009-07-18
if synaptic gets taken out it really isn't a big deal

```
sudo apt-get install synaptic
```

problem solved

---

### Post by ghindo on 2009-07-18
> **wayne_cat said:**
> [http://news.softpedia.com/news/Ubuntu-AppCenter-112572.shtml](http://news.softpedia.com/news/Ubuntu-AppCenter-112572.shtml)

and

[https://wiki.ubuntu.com/AppCenter](https://wiki.ubuntu.com/AppCenter)At this point, AppCenter is still nothing but blueprints and mockups.  Once there's an actual build we can test out and interact with, it would make more sense to compare AppCenter and Synaptic.  However at this point, it would be like comparing Ubuntu 9.04 with 10.04.

---

### Post by ibutho on 2009-07-18
> **ghindo said:**
> At this point, AppCenter is still nothing but blueprints and mockups.  Once there's an actual build we can test out and interact with, it would make more sense to compare AppCenter and Synaptic.  However at this point, it would be like comparing Ubuntu 9.04 with 10.04.
Ok. This explains why I couldn't find it in Karmic.

---

### Post by Swarms on 2009-07-18
Packagekit!

---

### Post by ktp on 2009-07-18
> **gnomeuser said:**
> neither, i don't see either one really presenting progress.

+1

---

### Post by seeker5528 on 2009-07-18
If I have to choose one, it's Synaptic all the way.

AppCenter would be cool it it will be able to show a selection of software instead of packages, was not be limited to a static list as was the case with the old (Adept provided?) Add/Remove thingamajig, and would hand you off to some optionally specified system default advanced package manager if desired/needed, so K/X/Ubuntu/ and derivatives could all easily customize the default advanced package manager, and users could later change it to their preferred package manager.

Later, Seeker

---

### Post by mpt on 2009-07-18
This thread reminds me of the articles from the past couple of weeks where various journalists were knowledgably comparing current OSes with Chrome OS, never mind the fact that none of them had tried or even seen Chrome OS.

> **autocrosser said:**
> I would like to see AppCentre side-by-side with Synaptic on my system to choose..

That’s one of the problems we’re trying to solve. It’s a long-standing principle for Ubuntu that there should be one graphical application installed by default for doing a particular thing, not two.

> *I've used Synaptic for several years now & like how it works, but I want version details available like we got in Update-manager with the gconf key.*

Why not a checkbox? That seems like it would be easier to get to.

> **ronacc said:**
> why not keep both , atleast for a few release cycles

AppCenter will be able to replace Synaptic once it gets to about version 3.0.

> **ELD said:**
> So now it's this, synaptic and add/remove? wth?

No. AppCenter is being built on Add/Remove, and Add/Remove is the first thing it will replace.

> **Slug71 said:**
> I like the idea/concept of having an 'all-in-one' GUI but im not convinced its a good idea.

It’s understandable to be skeptical. Offering simple and advanced functions in the same interface is a more difficult design challenge than an interface where advanced tasks are impossible (*e.g.* Add/Remove) or one where even simple things look complicated (*e.g.* Synaptic).

> *The way ubuntu is now works and has worked for a long time with little to no complaints.*

It may “work” for [ten million]("http://mdzlog.alcor.net/2009/04/27/ten-releases-of-ubuntu/") users or so, but we want many more than that. We want people to be able to find and install applications without having someone nearby who’s an Ubuntu expert. And we want third-party developers to see that their software will be well-presented to potential users.

> **Slug71 said:**
> As i understand it, it could be based on one of them but wont use them as a backend. I know PK add/remove is being considered as a possible basis for it. But since PK and Synaptic are frontends im not sure how they can be used as a backend.

They are both both. Add/Remove currently asks Synaptic to do various things (which is why if you have Synaptic open at the same time, you get an error message complaining that “another synaptic is running”). And packagekit-gnome is one of the “front ends” for PackageKit. As far as I know, there is no such thing as “PK add/remove”.

> **ronacc said:**
> if app center is based on gnome app install it will be as worthless as gnome app install .

Thanks for your constructive feedback. :rolleyes:

> **ronacc said:**
> reading the "rationale" section of the wiki page synaptic already does everything that they propose app center to do and does it with a minimum of fuss .

That is completely untrue.

---

### Post by ghindo on 2009-07-18
> **mpt said:**
> this thread reminds me of the articles from the past couple of weeks where various journalists were knowledgably comparing current oses with chrome os, never mind the fact that none of them had tried or even seen chrome os.+&#8734;

---

### Post by psyke83 on 2009-07-18
> **Slug71 said:**
> So theres been a lot of discussion about package management in Karmic and specially this new AppCenter.

How many of you would just prefer to keep Synaptic?

This poll is completely useless. AppCenter hasn't even seen a 0.1 release, so there is no basis to compare the strengths and weakness of each application.

---

### Post by ronacc on 2009-07-18
from the wiki
> In Ubuntu 9.04, there are at least four graphical utilities promoted for installing and removing software. For installing and uninstalling graphical applications you can use &#8220;Add/Remove Applications&#8220; or the more technical &#8220;Synaptic Package Manager&#8221;, though the former warns you to use the latter &#8220;for more complicated needs&#8221;. For installing and uninstalling other software, you must use Synaptic. For installing updates, the usual route is Update Manager, but it instructs you to run Synaptic if it encounters conflicts. For configuring where these utilities look for software, you use &#8220;Software Sources&#8221;. For installing downloaded .deb packages, you use gdebi. And for removing no-longer-needed software, you use Computer Janitor. This redundancy increases the amount of interface people have to learn, wastes space on the Ubuntu CD, and fragments development effort. Having multiple sanctioned graphical methods of installing software also makes people more likely to think that unsanctioned methods (such as Ultamatix or third-party Web sites) are also safe, when they are not. Meanwhile, the descriptions of available software are often technical gibberish. And many software project and vendor Web sites either provide command-line installation instructions (dulling users to malicious terminal commands from other sources) or .tar.gz downloads that are difficult to install and near-impossible to update. 

as you will note they say that synaptic is recomended for "complex' install and update situations , it also works for "routine" ones .
you can configure your software sources via synaptic>settings>repositories .
you can "cleanup" your system with installed (auto removeable) , installed (local or obsolete) and also with "mark for removal" and "mark for complete removal" .

my remark about gnome-app-install stands , it just misses too many apps that are in the repos and shown in synaptic , for a quick example in " sound&video " where are vlc and banshee to name 2 ?

I am all for progress but "shiney new" isn't always progress ,which led to my comment about having both app-center and synaptic for a couple of full release cycles until we can decide which is really best .

you don't fix a leaky roof by tearing down the house and building a pig pen .

can synaptic be improved , yes , and that might be a better way to go . better package descriptions and perhaps catagories like gnome-app-install . That should be easier than building a new app from scratch .

---

### Post by Gatemaze on 2009-07-18
Synaptic works fine for me... in fact I never used the add/remove programs interface... Without seeing appcenter how can someone make a decision... So, considering that from a user perspective synaptic is good enough, then unless there are some important reasons, is it a good idea to spend resources on a new package manager? I'd rather see an undo function in nautilus...

---

### Post by Regenweald on 2009-07-18
> **ronacc said:**
> 

I am all for progress but "shiney new" isn't always progress ,which led to my comment about having both app-center and synaptic for a couple of full release cycles until we can decide which is really best .



I believe mpt said that AppCentre would be alongside Synaptic till AC was around version 3.0 That is quite a bit of development wouldn't you say ?

---

### Post by benj1 on 2009-07-18
although i completely understand the rationale an would welcome some of the proposals, i do have my reservations.

at the moment if you are a non technical user you can use add remove, let updates be done automatically, and you hopefully shouldn't have to mess with software sources (except medibuntu, which can't be helped anyway)
if you are a technical (graphical) user you can use synaptic, check updates in update manager etc etc.

im not sure that all these things will be able to be melded, yes building all these things into synaptic would work, but im not sure how you would simplify it to function as an add/remove replacement aswell, unless you just have it as a link to 'synaptic --simple' which i dont think is what they want to achieve, as people have pointed out its not out yet so we cant realy pass judgement yet, im just concerned they will end up creating a synaptic+ and then hobble it in the name of simplicity

i am looking forward to how they improve package searching though aswell as tightly integrating updates.

---

### Post by wayne_cat on 2009-07-18
> **Regenweald said:**
> I believe mpt said that AppCentre would be alongside Synaptic till AC was around version 3.0 That is quite a bit of development wouldn't you say ?

from the AppCenter Wiki:

[https://wiki.ubuntu.com/AppCenter](https://wiki.ubuntu.com/AppCenter)

```
April 2010

In Ubuntu 10.04, replace Synaptic, Software Sources, Gdebi, and (if appropriate) 
Update Manager with an expanded AppCenter.
```I think it's possible. Would be nice to see the first alpha version soon ... we could start to find the bugs.

Ubuntu (and the community) is strong enough to create and test something new .. Ubuntu is not a "brown debian stable" :biggrin:

---

### Post by ronacc on 2009-07-18
> **Regenweald said:**
> I believe mpt said that AppCentre would be alongside Synaptic till AC was around version 3.0 That is quite a bit of development wouldn't you say ?

here are his words > AppCenter will be able to replace Synaptic once it gets to about version 3.0. . I read that as a statement of when he believes it will be mature enough . the quote from the wiki implies it will replace synaptic in less than 3 months , IMHO that is insane .

---

### Post by wayne_cat on 2009-07-18
> **ronacc said:**
> here are his words  . I read that as a statement of when he believes it will be mature enough . the quote from the wiki implies it will replace synaptic in less than 3 months , IMHO that is insane .

It should replace synaptic in 9 month .. from the Wiki

April ```
2010

In Ubuntu 10.04, replace Synaptic, Software Sources, Gdebi, and (if appropriate) 
Update Manager with an expanded AppCenter.
```9 month != 3 month

---

### Post by ronacc on 2009-07-18
We start testing 10.04 in about 3 months .

---

### Post by wayne_cat on 2009-07-18
> **ronacc said:**
> We start testing 10.04 in about 3 months .

no ... they will release the Karmic final in about 3 month. Testing started (for us):

May```
 14th 2009 - Karmic Alpha 1
```and they can add AppCenter until FeatureFreeze:

```
August 27th 2009 
```AppCenter is an option in Karmic ... not a replacement:

Please read:

[https://wiki.ubuntu.com/AppCenter](https://wiki.ubuntu.com/AppCenter)

and

[https://wiki.ubuntu.com/KarmicReleaseSchedule](https://wiki.ubuntu.com/KarmicReleaseSchedule)

---

### Post by autocrosser on 2009-07-18
Yes--10.04 testing starts late Oct--early Nov.....depending on repos open:D--I am glad to say that the open dates are getting earlier--not later:D

So I would guess the AppCentre testing would start shortly after the Summit--so say 'round mid-Nov......

Would make for "interesting" times.......With that in mind, I would say the side-by-side compare would continue past the new year......

---

### Post by autocrosser on 2009-07-18
> **wayne_cat said:**
> no ... they will release the Karmic final in about 3 month. Testing started (for us):

May```
 14th 2009 - Karmic Alpha 1
```and they can add AppCenter until FeatureFreeze:

```
August 27th 2009 
```AppCenter is an option in Karmic ... not a replacement:

Please read:

[https://wiki.ubuntu.com/AppCenter](https://wiki.ubuntu.com/AppCenter)

and

[https://wiki.ubuntu.com/KarmicReleaseSchedule](https://wiki.ubuntu.com/KarmicReleaseSchedule)

All well known to him--he is talking about testing start for 10.04--as per my note above....ronacc & I have been in the testing group for a "bit" of time.....

---

### Post by wayne_cat on 2009-07-18
> **autocrosser said:**
> All well known to him--he is talking about testing start for 10.04--as per my note above....ronacc & I have been in the testing group for a "bit" of time.....

holy shi* :redface:

I stand corrected.

```
For October 2009, we have four major goals. 
Include in Ubuntu 9.10 a simple and fun interface for finding, installing, and removing software. 
```9.04 =! 9.10

ronacc ... autocrosser .. thank you!

---

### Post by autocrosser on 2009-07-18
All is fair my friend!!!!  EVERYONE makes mistakes--but one is not a mistake......'tis simple to miss the context--grand to admit that one error'd.....:)

---

### Post by Slug71 on 2009-07-19
> **wayne_cat said:**
> from the AppCenter Wiki:

[https://wiki.ubuntu.com/AppCenter](https://wiki.ubuntu.com/AppCenter)

```
April 2010

In Ubuntu 10.04, replace Synaptic, Software Sources, Gdebi, and (if appropriate) 
Update Manager with an expanded AppCenter.
```I think it's possible. Would be nice to see the first alpha version soon ... we could start to find the bugs.

Ubuntu (and the community) is strong enough to create and test something new .. Ubuntu is not a "brown debian stable" :biggrin:

Bad move for an LTS IMO.

---

### Post by Slug71 on 2009-07-19
> **psyke83 said:**
> This poll is completely useless. AppCenter hasn't even seen a 0.1 release, so there is no basis to compare the strengths and weakness of each application.

It is actually completely relevent.

Why go from one Ubuntu only thing to another when what we have now already works and does so just fine?

If Ubuntu should move to anything else it should be to PK where the whole Linux community will benefit from it.

All Distros share stuff like Pulseaudio, KDE, Gnome, ALSA, Kernel, X, Policykit, Devicekit, etc etc yet for some reason package management gets left out of this.

I would still prefer to have Packagekit in Ubuntu but if thats not gonna happen then i think just stay with Synaptic.

---

### Post by psyke83 on 2009-07-19
> **Slug71 said:**
> It is actually completely relevent.

Why go from one Ubuntu only thing to another when what we have now already works and does so just fine?

If Ubuntu should move to anything else it should be to PK where the whole Linux community will benefit from it.

All Distros share stuff like Pulseaudio, KDE, Gnome, ALSA, Kernel, X, Policykit, Devicekit, etc etc yet for some reason package management gets left out of this.

I would still prefer to have Packagekit in Ubuntu but if thats not gonna happen then i think just stay with Synaptic.

So why didn't you express your real intention and make a Synaptic vs. PackageKit poll?

---

### Post by zekopeko on 2009-07-19
> **psyke83 said:**
> So why didn't you express your real intention and make a Synaptic vs. PackageKit poll?

Because he posted so many threads about Packagekit and people didn't really care. And he/she knows that people would downvote Packagekit in a heartbeat vs Synaptic.

---

### Post by Slug71 on 2009-07-19
> **psyke83 said:**
> So why didn't you express your real intention and make a Synaptic vs. PackageKit poll?

Because PK is out the window for now in which case id rather still have Synaptic over AppCenter.

Like i said i dont see a point going from one Ubuntu thing to another.
Its kinda like reinventing the wheel, no?

---

### Post by Slug71 on 2009-07-19
> **zekopeko said:**
> Because he posted so many threads about Packagekit and people didn't really care. And he/she knows that people would downvote Packagekit in a heartbeat vs Synaptic.

Actually there is a lot of support for Packagekit in the forums and Brainstorm. 

PK isnt integrated properly with Ubuntu and i bet if it was it would have even more support. 
Instead of some people whining about though, bugs should be filed like for any other app..

---

### Post by Regenweald on 2009-07-19
This is just sad. Ubuntu is going the way of appcentre. deal with it or find a distro that uses packagekit.Your point has been made, the developers disagree. Unless you plan to resolve the deficiencies of packagekit that are stopping it from being used, please just stop.

---

### Post by mpt on 2009-07-19
> **wayne_cat said:**
> 9 month != 3 month

The confusion is because I haven’t yet updated the wiki page to reflect the results of a meeting I had with Mark on Friday. He wants the ability to purchase software in AppCenter by Ubuntu 10.04 (AppCenter 2.0), which will almost certainly push back the goal of replacing Synaptic to 10.10 (AppCenter 3.0).

I had thought that handling non-application packages (like Synaptic does) would be a pre-requisite for purchasing things like codecs, but I was mistaken.

---

### Post by mpt on 2009-07-19
> **Slug71 said:**
> Why go from one Ubuntu only thing to another when what we have now already works and does so just fine?

That’s [the second time]("http://ubuntuforums.org/showthread.php?p=7636415#post7636415") you’ve said that, and, with respect, you’re still mistaken. Have you actually watched non-geeks try to use Add/Remove *or* Synaptic?

> *If Ubuntu should move to anything else it should be to PK where the whole Linux community will benefit from it.*

Maybe they would, but it would make Ubuntu worse.

---

### Post by ronacc on 2009-07-19
> **mpt said:**
> That&#8217;s [the second time]("http://ubuntuforums.org/showthread.php?p=7636415#post7636415") you&#8217;ve said that, and, with respect, you&#8217;re still mistaken. Have you actually watched non-geeks try to use Add/Remove *or* Synaptic?

just for grins I will try that  experiment , I have a retired lady neighbor and her college student granddaughter , definitely non geeks who have never used any kind of linux they would make perfect subjects. it may take a couple of days but I will report back .

---

### Post by Merk42 on 2009-07-19
> **ronacc said:**
> just for grins I will try that  experiment , I have a retired lady neighbor and her college student granddaughter , definitely non geeks who have never used any kind of linux they would make perfect subjects. it may take a couple of days but I will report back .

First observation.
When told to install new software, they immediately opened up the web browser and searched for "{insert program here} download"

---

### Post by ronacc on 2009-07-19
let me make the conditions of the test that I will use clear . I will be using jaunty (full version not netbook) installed to my eepc 701 . since they are both rank newbes when it comes to linux I will tell them that they can use add/remove from the applications menu (kind of obvious) or synaptic (not obvious at all) and I will give them the name of the app to install . if they acomplish that I will ask them to find an app to do "something" and install that . I will not coach them as to how to do it . NOTE I will not take sugestions for modifying the test until after I post the results of the first run .

---

### Post by Slug71 on 2009-07-19
> **Regenweald said:**
> This is just sad. Ubuntu is going the way of appcentre. deal with it or find a distro that uses packagekit.Your point has been made, the developers disagree. Unless you plan to resolve the deficiencies of packagekit that are stopping it from being used, please just stop.

I am over it, which is why the poll is about Synaptic and AppCenter and not Packagekit and AppCenter. READ!!

> **mpt said:**
> That&#8217;s [the second time]("http://ubuntuforums.org/showthread.php?p=7636415#post7636415") you&#8217;ve said that, and, with respect, you&#8217;re still mistaken. Have you actually watched non-geeks try to use Add/Remove *or* Synaptic?

Though i have what i consider to be an average amount of computer knowledge i consider myself a 'non-geek'. My wife has used it on several occasions too. I too have shown my parents how to use it and my brother which is a Network Engineer with limited Linux experience also uses it.



> **mpt said:**
> That&#8217;s [URL="http://ubuntuforums.org/showthread.php?p=7636415#post7636415"]Maybe they would, but it would make Ubuntu worse.

For how long, maybe a release or two?

---

### Post by Slug71 on 2009-07-19
Im gonna ask that this thread stay on topic with Synaptic and AppCenter.

Packagekit has already been discussed and i do not feel like getting any more responses like this: 

> This is just sad. Ubuntu is going the way of appcentre. deal with it or find a distro that uses packagekit.Your point has been made, the developers disagree. Unless you plan to resolve the deficiencies of packagekit that are stopping it from being used, please just stop.


This isnt what what this thread is about.

---

### Post by zekopeko on 2009-07-19
> **Slug71 said:**
> Im gonna ask that this thread stay on topic with Synaptic and AppCenter.

What's there to discuss? Appcenter isn't in any usable form at this time. So you can't really compare it against synaptic or add/remove.
And your line of reasoning is flawed. Just because Synaptic works for you doesn't mean it works for other people. Not to mention that you think that there is nothing to improve upon. Following that line of argument we should still all use abacuses because they "just work".

---

### Post by mpt on 2009-07-19
> **ronacc said:**
> since they are both rank newbes when it comes to linux I will tell them that they can use add/remove from the applications menu (kind of obvious) or synaptic (not obvious at all) and I will give them the name of the app to install .

As Merk42 suggested, if you tell them not only that Add/Remove and Synaptic exist, but even what they’re called, you’ll be missing out on some of the most important results.

> *if they acomplish that I will ask them to find an app to do "something" and install that .*

That would be more realistic.

> **Slug71 said:**
> Though i have what i consider to be an average amount of computer knowledge i consider myself a 'non-geek'.

I can quite confidently state, Slug71, that you are a geek in the sense that you know more about Ubuntu than 99 percent of the population. In this thread alone you have used the words Alsa, backend, DeviceKit, distro, frontend, Gnome, GUI, KDE, kernel, LTS, package, PolicyKit, PulseAudio, and Synaptic. Someone with “an average amount of computer knowledge” *does not know the meaning of any of those words*.

---

### Post by BwackNinja on 2009-07-19
I hate to say it, but evaluating what AppCenter is supposed to be and supposed to look like at this point, I like the current system better (although system-cleaner and software sources should have their functionality integrated in synaptic, especially considering that you can't have both of them open at the same time *anyway.*

1. The layout looks just like synaptic, showing all the same info, with the differences being more useful categories in the sidebar and the info that is normally in the statusbar (the updates and whatnot) are shown in the sidebar too, use of "friendly" names, and short description underneath instead of beside the package name and a big icon. I don't like that it takes more room for each item because then you can't see as many at the same time.

2. The only thing that really catches my eye at all about this is that it is going to be using policykit instead of gksudo. That in itself is at least a reason to start thinking of some change.

3. I like the current use of gdebi package installer because it is simple and pretty much impossible to screw up. It tells you everything that you may or may not need to pay attention to if you want it to and makes sense. Ditto for update-manager. I just wish all these things wouldn't have to spawn more windows and used policykit (those two go hand in hand).

4. Installing packages really isn't that hard. When I help my friends install and set up ubuntu, I teach them how to install packages from the command line. Yes, you heard me right. And they don't complain, they think its cool that you can do things so easily. Tab completion = win.

5. Because I try not to be anti-change (I'd be using hardy or even dapper if I was anti-change) there are just a few things that I will be looking for in this new AppCenter and hope that a few of them show themselves, but I won't have any expectations:

	- Be a framework, not just an application, though this is a forbidden word, packagekit. I'm not saying use it because that's been out of the question for a long time now, but be able to do things like queue changes while other changes are being applied (instead of being entirely useless while doing stuff). An offline queue might be nice too and no requirement for the app to be open.

	- Show packages grouped with their dependencies (separating depends and recommends and suggests) for viewing, but not shown by default with the option on each not to install recommends

	- Use the new notifications in a useful but not abusive way.

	- Have only _ONE_ window, always. I'm not talking about copies of the app open, but no downloading window and installing window, etc. Just have it on the main window - the rest isn't useful anyway while stuff is happening.

---

### Post by zekopeko on 2009-07-19
@BwackNinja

you will note that at: [https://wiki.ubuntu.com/AppCenter](https://wiki.ubuntu.com/AppCenter) there is no screenshot of the app. The one before was a mock-up.

---

### Post by ronacc on 2009-07-19
@ MPT these people have never used linux of any kind before and I was not planing to do a complete study of first time linux users , only to see how difficult it would be for someone to install software for the first time using add/remove and synaptic . To do an honest test of the whole works you would have to find someone who had never run any OS and set them down with a box with a blank hard drive , a windows dvd and an Ubuntu live cd and see which one was easiest for them to get up and running .

---

### Post by Twitch6000 on 2009-07-19
> **Slug71 said:**
> As i understand it, it could be based on one of them but wont use them as a backend. I know PK add/remove is being considered as a possible basis for it. But since PK and Synaptic are frontends im not sure how they can be used as a backend.

From what I understand looking at the ubuntu discusssion on appcenter and packagekit.

It seems appcenter will use certain things from packagekit.

So I am guessing this will be a remix for ubuntu of packagekit.

That is what I am guessing I could be wrong.

---

### Post by Slug71 on 2009-07-20
> **ronacc said:**
> @ MPT these people have never used linux of any kind before and I was not planing to do a complete study of first time linux users , only to see how difficult it would be for someone to install software for the first time using add/remove and synaptic . To do an honest test of the whole works you would have to find someone who had never run any OS and set them down with a box with a blank hard drive , a windows dvd and an Ubuntu live cd and see which one was easiest for them to get up and running .

I actually think they would find Ubuntu easier. 
Only thing i think might get them is the Filesystem choices and the /, /home partitioning etc. For someone that has never used Linux and knows nothing about that, will find that the biggest hurdle as far as installation goes.

The average user just uses their PC to surf and email, listen to music, copy photos over, burn CDs etc. 
Adobe Reader and Flash have .debs or .rpm etc. packages as does Skype. 
Of course they will need to know about them and not get .exe's.
Everything else they need is pretty much there.
And they will need to use Open Office instead of MS Office.

---

### Post by Slug71 on 2009-07-20
> **zekopeko said:**
> What's there to discuss? Appcenter isn't in any usable form at this time. So you can't really compare it against synaptic or add/remove.
And your line of reasoning is flawed. Just because Synaptic works for you doesn't mean it works for other people. Not to mention that you think that there is nothing to improve upon. Following that line of argument we should still all use abacuses because they "just work".

No it cant be compared but Synaptic vs Packagekit and Packagekit vs AppCenter has been covered. 
As far as Packagekit and Synaptic goes lots of people still preferred Synaptic.
Synaptic is understandably something that Ubuntu users have come to know and many love.
So just trying to get the feel of Synaptic vs AppCenter this round.


Next up will be Smart vs APT :P (Not in Karmic discussion though)

---

### Post by Regenweald on 2009-07-20
This thread feels like you didn't get your way with packagekit so now you just want to stir things up against appcentre. How can an individual vote against software that they have not yet used ? With this spiteful thinking, lets petition the Ubuntu project to stop now, since most tools works good enough as they are.

---

### Post by pulpo69 on 2009-07-20
i always was fine with synaptic and i didn't miss anything.
i don't see any reason to change it.

---

### Post by zekopeko on 2009-07-20
> **Regenweald said:**
> This thread feels like you didn't get your way with packagekit so now you just want to stir things up against appcentre. How can an individual vote against software that they have not yet used ? With this spiteful thinking, lets petition the Ubuntu project to stop now, since most tools works good enough as they are.

Hear, hear.

---

### Post by wayne_cat on 2009-07-20
I always knew it ... AppCenter is the devil ... pain hate and fear ... we can not even see it's shadow ... but we know ... WE ARE LOST!!!!

:popcorn:

---

### Post by ronacc on 2009-07-20
All we are saying is let us see this "appcenter" and test it for a reasonable period before making it the default for one of the main foundations of Ubuntu , package handeling . To declare that an app that no one has seen yet will become a crown jewel in ubuntu's tiara in the next cycle is IMHO reckless . Change can be good , bad or neutral but a rush to change can be disaster , we only need to say Vista , and MS didn't even rush that .

---

### Post by Merk42 on 2009-07-20
Is the problem really against the reinventing of the wheel that seems to happen with Linux due to "Not Invented Here" syndrome?

> **ronacc said:**
> Change can be good , bad or neutral but a rush to change can be disaster , we only need to say Vista , and MS didn't even rush that .
I don't see the point of mentioning Vista at all. It wasn't rushed (as you said) and it was also little change.
If anything Windows 7 is more analogous, but that has pretty positive reviews.

---

### Post by Slug71 on 2009-07-20
> **Regenweald said:**
> This thread feels like you didn't get your way with packagekit so now you just want to stir things up against appcentre. How can an individual vote against software that they have not yet used ? With this spiteful thinking, lets petition the Ubuntu project to stop now


Well its not like that at all.

If i started a thread about APT being replaced by Smart i bet youd see a lot of flare about that even though those people probably never have tried Smart.

No difference here really.

---

### Post by zekopeko on 2009-07-20
> **Slug71 said:**
> Well its not like that at all.

If i started a thread about APT being replaced by Smart i bet youd see a lot of flare about that even though those people probably never have tried Smart.

No difference here really.

So basically you're saying that you are a troll?

---

### Post by Slug71 on 2009-07-20
> **zekopeko said:**
> So basically you're saying that you are a troll?

OMG seriously?? 

Synaptic and APT have become a big part of Ubuntu. They work well. Im just curious how open they(Ubuntu users) are to change and how much change.

Even more so because these changes are all possible. Its not like these are little changes either.

Now back off.

---

### Post by ronacc on 2009-07-20
> **zekopeko said:**
> So basically you're saying that you are a troll?

If open and honest discussion of major changes to the UI is trolling I will admit that I too am a troll .

---

### Post by zekopeko on 2009-07-20
> **ronacc said:**
> If open and honest discussion of major changes to the UI is trolling I will admit that I too am a troll .

What UI? The app is still in the design phase. How can you debate UI design without actually seeing it or ,even more important, using it?

---

### Post by zekopeko on 2009-07-20
> **Slug71 said:**
> OMG seriously?? 

Synaptic and APT have become a big part of Ubuntu. They work well. Im just curious how open they(Ubuntu users) are to change and how much change.

Even more so because these changes are all possible. Its not like these are little changes either.

Now back off.

Hey you said it. Re-read your previous post ;)

---

### Post by Slug71 on 2009-07-20
> **zekopeko said:**
> Hey you said it. Re-read your previous post ;)

Its not my fault your you lack the ability to understand what i meant.

---

### Post by ronacc on 2009-07-20
> **zekopeko said:**
> What UI? The app is still in the design phase. How can you debate UI design without actually seeing it or ,even more important, using it?

are not synaptic , software sources , gdebi, and update manager significant parts of the UI ? and I would define replacing them with one untested app to be a major change . I will assume that you have read the wiki page and so will not quote it here . I and it seems atleast some others here believe the stated timetable to be overly ambitious . As for not having seen it yet that is the point . I will be happy to test it and provide feedback as soon  as something is available but as yet there are not even sources to build from .

---

### Post by ghindo on 2009-07-20
> **ronacc said:**
> are not synaptic , software sources , gdebi, and update manager significant parts of the UI ? and I would define replacing them with one untested app to be a major change . I will assume that you have read the wiki page and so will not quote it here . I and it seems atleast some others here believe the stated timetable to be overly ambitious . As for not having seen it yet that is the point . I will be happy to test it and provide feedback as soon  as something is available but as yet there are not even sources to build from .I think that's missing the point entirely.  AppCenter won't replace these tools immediately, so if there are problems with AppCenter there will be adequate time to address them or leave the existing tools as-is.  Besides, as mpt has said, AppCenter will only (tentatively) be replacing Add/Remove in Karmic, so it's not like Synaptic, Software Sources, GDebi, and Update Manager are in *immediate* danger of being replaced.  If AppCenter isn't adequate enough to replace all of these tools, I'm sure that the Ubuntu devs will wait a release or two before including it by default.  Don't assume that the given time line is set in stone.

However, it seems the bigger issue here is that people in this thread are making the assumption that AppCenter won't be good enough to replace those tools, *despite never having used AppCenter*.  At this point in time, none of us have ever used AppCenter, nor seen any GUI past mock-ups.  AppCenter probably *won't even be the final name of the product*.  Judging it this early in its development cycle would be like criticizing Karmic+1.  We just don't know what the final product is going to be like at this point, and it would be premature to pass any judgment.

---

### Post by wayne_cat on 2009-07-20
> **ghindo said:**
> I think that's missing the point entirely.  AppCenter won't replace these tools immediately, so if there are problems with AppCenter there will be adequate time to address them or leave the existing tools as-is.  Besides, as mpt has said, AppCenter will only (tentatively) be replacing Add/Remove in Karmic, so it's not like Synaptic, Software Sources, GDebi, and Update Manager are in *immediate* danger of being replaced.

However, it seems the bigger issue here is that people in this thread are making the assumption that AppCenter won't be good enough to replace those tools, *despite never having used AppCenter*.  At this point in time, none of us have ever used AppCenter, nor seen any GUI past mock-ups.  AppCenter probably *won't even be the final name of the product*.  Judging it this early in its development cycle would be like criticizing Karmic+1.  We just don't know what the final product is going to be like at this point, and it would be premature to pass any judgment.

This is a thread about "I hate AppCenter" ... stop being realistic ... say something like "AppCenter will kill little fluffy puppies and Synaptic can not help them because THEY HAVE REMOVED IT"

---

### Post by Slug71 on 2009-07-20
> **wayne_cat said:**
> This is a thread about "I hate AppCenter" ... stop being realistic ... say something like "AppCenter will kill little fluffy puppies and Synaptic can not help them because THEY HAVE REMOVED IT"

What is it with all the smart arses around here??

---

### Post by mpt on 2009-07-20
> **BwackNinja said:**
> I hate to say it, but evaluating what AppCenter is supposed to be and supposed to look like at this point, I like the current system better &#8230; The layout looks just like synaptic

Designing software is something I find easy. Understanding and correcting people&#8217;s perception of software development, though, I find much trickier. For example, you posted that comment about details of &#8220;the layout&#8221; of AppCenter when you cannot possibly have had any clue what the layout was going to be. (I finally posted [some preliminary wireframes]("https://wiki.ubuntu.com/AppCenter#available") this afternoon, some 15 hours after your comment.)

Could you explain what led you to think you knew what the layout of AppCenter will be? That would help me improve the design process in future. Thanks.

> *- Be a framework, not just an application, though this is a forbidden word, packagekit. I'm not saying use it because that's been out of the question for a long time now, but be able to do things like queue changes while other changes are being applied (instead of being entirely useless while doing stuff). An offline queue might be nice too and no requirement for the app to be open.*

There&#8217;s another example of a persistent misperception. I have consistently said [[1]("http://ubuntuforums.org/showpost.php?p=7349884&postcount=6"), [2]("http://ubuntuforums.org/showpost.php?p=7353101&postcount=63"), [3]("http://ubuntuforums.org/showpost.php?p=7424788&postcount=121"), [4]("http://ubuntuforums.org/showpost.php?p=7492521&postcount=111")] that we may use PackageKit for some things. What gave you the idea that PackageKit was &#8220;a forbidden word&#8221;?

> *- Show packages grouped with their dependencies (separating depends and recommends and suggests) for viewing, but not shown by default with the option on each not to install recommends*

Good idea! I&#8217;m thinking that for something registered in app-install-data, Recommends and Suggests packages that are also registered in app-install-data would show up as checkboxes that you could twiddle before clicking the &#8220;Install&#8221; button (while other dependencies would remain invisible). Recommends items would be checked by default, Suggests unchecked by default. For a package not registered in app-install-data, it would be the same, except that all Recommends/Suggests would be shown (again with Recommends checked by default and Suggests unchecked).

> *- Use the new notifications in a useful but not abusive way.*

Offhand, I can&#8217;t think of any reason AppCenter would use the notification system at all. What do you have in mind?

> *- Have only _ONE_ window, always. I'm not talking about copies of the app open, but no downloading window and installing window, etc. Just have it on the main window - the rest isn't useful anyway while stuff is happening.*

Sure, the downloading/installing window will become an &#8220;In Progress&#8221; pane in the main window. It might still be possible to open multiple windows if you really want to, but it wouldn&#8217;t be a prominent feature.

---

### Post by zekopeko on 2009-07-20
> **ronacc said:**
> are not synaptic , software sources , gdebi, and update manager significant parts of the UI ? and I would define replacing them with one untested app to be a major change .

Nobody is saying that this is not a major change. What I'm debating is people attacking the app before they tested it. Just because you attribute negative factor to a "untested" app doesn't mean that other's do. for your information mpt conducted user testing on how people manage software. he even had a talk at the gran canaria desktop summit IIRC. so just because he didn't consult you personally on "how would you like your appcenter" doesn't mean there was no testing.

>  I will assume that you have read the wiki page and so will not quote it here . I and it seems atleast some others here believe the stated timetable to be overly ambitious. As for not having seen it yet that is the point .

When are timetables set in stone? Ubuntu deferred many blueprints  for lack of resources necessary to implement them. mpt himself said that it's going to replace other software management tools in Ubuntu once it's ready.

>  I will be happy to test it and provide feedback as soon  as something is available but as yet there are not even sources to build from .

So then why does this thread exist then?
I can start a thread called Jaunty vs. Ubuntu 10.10 and it would have as much sense as this thread.

And i haven't seen anybody pointing out concrete examples where the synaptic/gdebi/update-manager UI fail and how to improve them. 
It's just a roll call thread for slug71 to show off his "it's good enough for me, it must be for others" mentality (no offence slug71, just the way i see it).

---

### Post by zekopeko on 2009-07-20
> **Slug71 said:**
> Its not my fault your you lack the ability to understand what i meant.

It's not my fault that your writing can be interpreted in different ways.

---

### Post by mpt on 2009-07-20
> **ronacc said:**
> @ MPT these people have never used linux of any kind before and I was not planing to do a complete study of first time linux users , only to see how difficult it would be for someone to install software for the first time using add/remove and synaptic . To do an honest test of the whole works you would have to find someone who had never run any OS and set them down with a box with a blank hard drive , a windows dvd and an Ubuntu live cd and see which one was easiest for them to get up and running .

We have run several usability testing sessions on Ubuntu at the Canonical offices in London, and none of those tests have involved a blank hard drive or an Ubuntu CD. (After all, many Ubuntu users have it preinstalled on their computer.) But at the same time, we don’t cheat by telling people which program to use for a particular thing. We give them a task, and the first critical issue is to see if they find the appropriate program. Doesn’t matter how amazing the program is to use if its name is too obscure.

It’s fantastic that you’re going to try doing your own usability testing. Of course I can’t order you around, but I think you’ll find your testing more interesting (and more credible) if you follow basic practices like not telling people the names of programs beforehand.

> **zekopeko said:**
> So then why does this thread exist then?
I can start a thread called Jaunty vs. Ubuntu 10.10 and it would have as much sense as this thread.

True, but it wouldn’t be nearly as funny. ;-)

---

### Post by raronson on 2009-07-20
From the reading, AppCenter.

It's good that the team is identifying that Gnome-add/remove *and* Synaptic together is less than ideal.  If AppCenter could look similar to Gnome-add/remove and integrate nicely in the environment while being as smart as Synaptic, then you'd have a real winner.  Apt-get/Aptitude could still be used from the command line for advanced purposes.

Although AppCenter would need to work as well as Synaptic.  I remember the first (and last) time that I used Gnome-add/remove, it told me to invoke Synaptic to fix a problem that couldn't be resolved on its own.  That settled it for me, and I haven't used it since.

---

### Post by zekopeko on 2009-07-20
> **mpt said:**
> We have run several usability testing sessions on Ubuntu at the Canonical offices in London, and none of those tests have involved a blank hard drive or an Ubuntu CD. (After all, many Ubuntu users have it preinstalled on their computer.) But at the same time, we don’t cheat by telling people which program to use for a particular thing. We give them a task, and the first critical issue is to see if they find the appropriate program. Doesn’t matter how amazing the program is to use if its name is too obscure.

Are the session results publicly available? i heard that there were some laughs to be had with some of the answers.
Or even better, a video of your talk at GCDS?

---

### Post by ronacc on 2009-07-20
> **mpt said:**
> 
It&#8217;s fantastic that you&#8217;re going to try doing your own usability testing. Of course I can&#8217;t order you around, but I think you&#8217;ll find your testing more interesting (and more credible) if you follow basic practices like not telling people the names of programs beforehand.

I agree but since I will be imposing on friends who are completely unfamiliar with linux I did not wish to take up enough of their time to "feel their way around " , I did try to spring the "test" on the retired lady today but she did not have her reading glasses with her , I'll try again tomorrow . I did find out that she has never even installed anything on her windows machine except for a couple of things that came on installer cd's or when the windows updater poped up and wanted to update things so this ahould be a reasonably good test of a complete newbe . I may try your suggestion on the granddaughter since she is somewhat more computer literate . But I really don't think that giving them the names of the apps to use is cheating all that much , I doubt few people learn windows with no help whatsoever either from books (windows for dummies) or from friends or classmates or  the windows tutorials .

---

### Post by seeker5528 on 2009-07-20
> **raronson said:**
> From the reading, AppCenter.

It's good that the team is identifying that Gnome-add/remove *and* Synaptic together is less than ideal.

To me the Gnome-add/remove thing certainly seems much less than ideal.

But using Synaptic for the package management and something else for a more simplified add/remove software interface does seem much more ideal than attempting to create one application that handles both cases.

If these are representative of the type of functionality AppCenter is expected to have:
> **mpt said:**
> I finally posted [some preliminary wireframes]("https://wiki.ubuntu.com/AppCenter#available") this afternoon

that's a totally different headspace.

Synaptic is designed to provide an interface for dealing with package management, and the informational and troubleshooting options it gives you are based on that and any package manager that is worth using will have a certain amount of complexity. 

If AppCenter is going to be designed to show you Software by category, possibly with an option to see a list of checkboxes to choose which suggests/recommends to pull in with it, that is based on the idea of hiding the complexities of package management from the user. The wireframes look good, but if it is designed to hide the complexity of package management, then how to you get the complexity exposing features in there that would allow it to be a replacement for Synaptic? Is it going to allow for pinning, viewing the changelogs, downgrading, viewing dependencies of both the installed and currently available packages, etc...?

Seems much better to me to have a full blown package manager for the advanced capabilities and a separate application or set of applications for the basic stuff.

Update-manager has a small range of tasks, that it seems to do pretty well, so I don't really know why you would want to replace it with something else. 

If Package Kit gains in capability enough to allow Synaptic and Update-manager to use it instead of using the apt utilities directly, without loss of functionality, I can see a good argument for that, if not, keep them for what they do, build something new that uses Package Kit when it can, and uses Synaptic or does it's own thing when it must to provide the desired features.

Just my opinion. :P

Later, Seeker

---

### Post by BwackNinja on 2009-07-20
> **mpt said:**
> Designing software is something I find easy. Understanding and correcting people’s perception of software development, though, I find much trickier. For example, you posted that comment about details of “the layout” of AppCenter when you cannot possibly have had any clue what the layout was going to be. (I finally posted [some preliminary wireframes]("https://wiki.ubuntu.com/AppCenter#available") this afternoon, some 15 hours after your comment.)

Could you explain what led you to think you knew what the layout of AppCenter will be? That would help me improve the design process in future. Thanks.

I based some of what the layout would look like on descriptions on the wiki as well as the picture here: [http://news.softpedia.com/news/Ubuntu-AppCenter-112572.shtml](http://news.softpedia.com/news/Ubuntu-AppCenter-112572.shtml). I can't say I know how reliable that is, but it seems *fairly* consistent with the wireframes you posted though at this point I agree that nothing can really be said about the interface because it hasn't been finalized. I'm not unfamiliar with the development process considering that I do some programming in my spare time and I like messing with the code for things, read development mailing lists, etc. I'd say for that there isn't much you can do to quell speculation because people are wanting to see, critique, test as soon as possible even if its too early. As seen with this thread, there isn't anything to compare yet but there's feedback from anyone who has a half-strong opinion.

> There’s another example of a persistent misperception. I have consistently said [[1]("/showpost.php?p=7349884&postcount=6"), [2]("/showpost.php?p=7353101&postcount=63"), [3]("/showpost.php?p=7424788&postcount=121"), [4]("/showpost.php?p=7492521&postcount=111")] that we may use PackageKit for some things. What gave you the idea that PackageKit was “a forbidden word”?

I can't say that I remember every post by everyone but I try to read them all. It was sort of a tongue-in-cheek statement after such discussions of PackageKit especially seen negatively in this thread. Beyond the whole standard way to install things that developers can count on that PackageKit aims to provide, I don't really care much about PackageKit. When I talk about PackageKit, I always mean the backend, not the frontend. IMO, that's where its really interesting. I'll be happy as long as whatever is used/created is flexible and overcomes the limitations and inconveniences of the current system.

PS: your links are somewhat broken, though I can still find my way to what you're talking about

> Good idea! I’m thinking that for something registered in app-install-data, Recommends and Suggests packages that are also registered in app-install-data would show up as checkboxes that you could twiddle before clicking the “Install” button (while other dependencies would remain invisible). Recommends items would be checked by default, Suggests unchecked by default. For a package not registered in app-install-data, it would be the same, except that all Recommends/Suggests would be shown (again with Recommends checked by default and Suggests unchecked).

Glad you like it. My only real concern for the creation of AppCenter is which users it leans toward. As a "for everyone" application I'd generally think that it will lean toward newer or less tech-savvy individuals more and that can't really be called a "bad thing" but I'd really like to keep the flexibility of synaptic and having the features presented more simply is always a plus.

> Offhand, I can’t think of any reason AppCenter would use the notification system at all. What do you have in mind?

Considering this is aimed at replacing update-manager at some point, I'd expect some sort of notification that there are updates. Currently update-manager just opens itself in the background though that's the one place I'd say the old notification system handled perfectly and the one of the very few places where the notification icon was very well used. Beyond that because it may or may not be a good design feature that everyone would notice and respond to, it would be nice to notify when installation is done by sending a notification and changing the window title so it can be seen from the panel.

> Sure, the downloading/installing window will become an “In Progress” pane in the main window. It might still be possible to open multiple windows if you really want to, but it wouldn’t be a prominent feature.

hooray!

---

### Post by zekopeko on 2009-07-20
> **ronacc said:**
> I agree but since I will be imposing on friends who are completely unfamiliar with linux I did not wish to take up enough of their time to "feel their way around " , I did try to spring the "test" on the retired lady today but she did not have her reading glasses with her , I'll try again tomorrow . I did find out that she has never even installed anything on her windows machine except for a couple of things that came on installer cd's or when the windows updater poped up and wanted to update things so this ahould be a reasonably good test of a complete newbe . I may try your suggestion on the granddaughter since she is somewhat more computer literate . But I really don't think that giving them the names of the apps to use is cheating all that much , I doubt few people learn windows with no help whatsoever either from books (windows for dummies) or from friends or classmates or  the windows tutorials .

You are going to skew the results by giving them names. Try it without names first. I'm sure you can look up on the net some standard and simple usability test for you test scenario.

---

### Post by zekopeko on 2009-07-20
I like what I'm seeing in the wireframe. And folks, the first iteration is only meant to replace Add/Remove and should be judged as such.

I like the App Store vibe. Are the little arrows next to the application going to take to a page that is dedicated to app's description? That would be nice and could neatly implement user ratings/reviews, screenshots and a simple description.

---

### Post by Slug71 on 2009-07-20
> **mpt said:**
> 
There’s another example of a persistent misperception. I have consistently said [[1]("/showpost.php?p=7349884&postcount=6"), [2]("/showpost.php?p=7353101&postcount=63"), [3]("/showpost.php?p=7424788&postcount=121"), [4]("/showpost.php?p=7492521&postcount=111")] that we may use PackageKit for some things. What gave you the idea that PackageKit was “a forbidden word”?


mpt, 

Can you elaborate more on what PK might be used for and if PK isnt used, what will? If you guys have got that far yet?

Also does AppCenter have a Freeze Exception for Karmic and if not will it still be available in a PPA for testing for Karmic +1?

---

### Post by Slug71 on 2009-07-21
> **zekopeko said:**
> It's not my fault that your writing can be interpreted in different ways.

Well i think ive made myself pretty clear.

Also people should be allowed to express their opinions openly without criticism and smart remarks. 

Package management is a big part of any OS which makes any change to it kinda a big deal so how can you expect people not to have something to say about it or for someone not want to see things from all angles of it.

And yes maybe this thread does have as much sense as starting a thread Jaunty vs. Ubuntu 10.10 but we dont yet know whats coming in 10.10.
Further more what seperates this thread and the others like this from one like you mentioned above is that usefull things come out from the concerns and criticism that people give whether or not it exists which in turn help people like mpt to address and/or get further ideas on how to make things like AppCenter better. Like the ideas mpt got from bwackninja.

This is especially important/crucial at such early conceptual stages of such an app. too.

So actually this thread and others like it is more constructive than you actually fail to realize and especially because people like mpt and some other devs. are nice enough to be so active in these discussions.

---

### Post by zekopeko on 2009-07-21
> **Slug71 said:**
> Well i think ive made myself pretty clear.

Also people should be allowed to express their opinions openly without criticism and smart remarks.

Who put that silly idea in your head that opinions can't be scrutinized? As you have the right to voice your opinion in accordance to CoC, so have I to criticize it with a counter-opinion.

> 
Package management is a big part of any OS which makes any change to it kinda a big deal so how can you expect people not to have something to say about it or for someone not want to see things from all angles of it.

Your question in the first post was: "How many of you would just prefer to keep Synaptic?"

Please do tell me what "angles" were you "covering" with that question?
Replacing synaptic (from the wiki) should occur around 10.4. 6 months from now.
You are dismissing the application with your negative question.
You haven't provided any claim as to the problematic areas of Appcenter (since neither me or you have tried it). 

> 
And yes maybe this thread does have as much sense as starting a thread Jaunty vs. Ubuntu 10.10 but we dont yet know whats coming in 10.10.

I can make an educated guess.

> 
Further more what seperates this thread and the others like this from one like you mentioned above is that usefull things come out from the concerns and criticism that people give whether or not it exists which in turn help people like mpt to address and/or get further ideas on how to make things like AppCenter better. Like the ideas mpt got from bwackninja.

This is especially important/crucial at such early conceptual stages of such an app. too.

So actually this thread and others like it is more constructive than you actually fail to realize and especially because people like mpt and some other devs. are nice enough to be so active in these discussions.

I probably missed the constructive part since most of the thread was about interpreting the wiki which is pretty self explanatory for me.
Ah well.

---

### Post by ronacc on 2009-07-21
> **zekopeko said:**
> Who put that silly idea in your head that opinions can't be scrutinized? As you have the right to voice your opinion in accordance to CoC, so have I to criticize it with a counter-opinion.

He means personal attack's like calling those you disagree with trolls or criticizing ther writing style rather than the substance of their opinion .

---

### Post by jppr on 2009-07-21
all-in-one system is what i waiting :)

---

### Post by zekopeko on 2009-07-21
> **ronacc said:**
> He means personal attack's like calling those you disagree with trolls or criticizing ther writing style rather than the substance of their opinion .

I was calling him a troll because of what he/she said ie. apparent flamebaiting. And i took into account previous postings about package management from him/her. And other people got the same feeling.
Anyway i don't want to drag this on since we actually have some mockups that look to be definite and are debatable on a purely hypothetical level (considering that it will only target app/remove for replacement).


My apologies to slug if this seemed as an all to personal attack.
I just called it as i saw it.

---

### Post by mpt on 2009-07-21
> **zekopeko said:**
> Are the session results publicly available? i heard that there were some laughs to be had with some of the answers.

Not yet. Test analysis is quite time-intensive: transcribing what each person did, then looking for repeated problems, then reporting bugs about problems that were either obvious or repeated. Scrubbing personally identifying info from the results and then posting them publicly is two extra steps that I just haven’t had time for yet, sorry.

> *Or even better, a video of your talk at GCDS?*

I gave two talks at GCDS: a lightning talk on interface design bloopers, and a longer talk on usability testing. As requested by the organizers, I’ve submitted the slides for both talks so they can publish them on the Web site, but they don’t seem to have done that yet. Hopefully a video of the lightning talk will also appear eventually.

> **seeker5528 said:**
> If AppCenter is going to be designed to show you Software by category, possibly with an option to see a list of checkboxes to choose which suggests/recommends to pull in with it, that is based on the idea of hiding the complexities of package management from the user.

No it isn’t. Synaptic has categories too, they’re just poorly arranged. ([For example]("http://www.ghacks.net/2008/12/21/getting-to-know-linux-installing-applications-in-unbuntu/"): “If you click through the three Multimedia listings in the category pane (left pane) you will find Ardour in the Multimedia(universe) repository.” Three separate Multimedia categories? I cringed when I read that.) And as far as I know, this will be the first time any human interface for dpkg has *usefully* distinguished between all three of Depends, Recommends, and Suggests.

> *The wireframes look good, but if it is designed to hide the complexity of package management, then how to you get the complexity exposing features in there that would allow it to be a replacement for Synaptic? Is it going to allow for pinning, viewing the changelogs, downgrading, viewing dependencies of both the installed and currently available packages, etc...?*

Yes, all of the above.

> *Seems much better to me to have a full blown package manager for the advanced capabilities and a separate application or set of applications for the basic stuff.*

Having separate applications for the same task makes sense if you’re charging different prices for them (*e.g.* Apple’s iMovie vs. Final Cut Express vs. Final Cut Pro), or if you’re targeting user bases who are so different, with a task so potentially complicated, that catering for both in a single tool would confuse or irritate them (*e.g.* Adobe’s InDesign vs. FrameMaker). Neither of those is true for AppCenter: it will be free, the user base will be on a fairly smooth continuum rather than in definite segments, and package management is (relatively speaking) not a particularly complicated thing.

> *Update-manager has a small range of tasks, that it seems to do pretty well, so I don't really know why you would want to replace it with something else.*

I’m still undecided as to whether Update Manager should remain separate, or become an expandable view of AppCenter.

> **BwackNinja said:**
> I based some of what the layout would look like on descriptions on the wiki as well as the picture here: [http://news.softpedia.com/news/Ubuntu-AppCenter-112572.shtml](http://news.softpedia.com/news/Ubuntu-AppCenter-112572.shtml).

Ah, I see. That mockup was drawn by [Mads Rosendahl]("http://anotherubuntu.blogspot.com/") based on a proof-of-concept wireframe I drew over a year ago. Lesson learned: keep the lid on wireframes, or at least draw half a dozen alternatives so that journalists don’t know which one to publish. :P

> **zekopeko said:**
> I like what I'm seeing in the wireframe. And folks, the first iteration is only meant to replace Add/Remove and should be judged as such.

I’ve now added a proof-of-concept [wireframe for AppCenter 4.0]("https://wiki.ubuntu.com/AppCenter#Eventual%20scope") to the wiki page, to help check that the design for 1.0 will scale.

> *I like the App Store vibe. Are the little arrows next to the application going to take to a page that is dedicated to app's description? That would be nice and could neatly implement user ratings/reviews, screenshots and a simple description.*

Yes, the arrow button would take you to [the application panel]("https://wiki.ubuntu.com/AppCenter#Application%20panel"). That’s actually the detail I’m least happy with at the moment. You should to be able to scroll through the list with the keyboard, so just single-clicking on an application probably shouldn’t take you directly to the application page, but … an arrow button? Meh.

> **Slug71 said:**
> Can you elaborate more on what PK might be used for and if PK isnt used, what will? If you guys have got that far yet?

As I understand it, applications can use a PackageKit API to request the installation of extra components [such as fonts]("http://blogs.gnome.org/hughsie/2008/12/01/packagekit-and-pango-are-now-friends/"). That installation process might use part of the AppCenter interface on Ubuntu. Or it might not. We’ll see.

> *Also does AppCenter have a Freeze Exception for Karmic and if not will it still be available in a PPA for testing for Karmic +1?*

We’re weeks away from having to think about anything like that.

---

### Post by zekopeko on 2009-07-21
> **mpt said:**
> Yes, the arrow button would take you to [the application panel]("https://wiki.ubuntu.com/AppCenter#Application%20panel"). That&#8217;s actually the detail I&#8217;m least happy with at the moment. You should to be able to scroll through the list with the keyboard, so just single-clicking on an application probably shouldn&#8217;t take you directly to the application page, but &#8230; an arrow button? Meh.

How about having a "Install" button and a "Description" button in the list? That way if i know what i want i can just click install and/or queue multiple applications for quick install.
Description would be great for more info and could suggest similar apps or the usual "people who installed X installed Y" (i think that was mentioned).

on a tehnical note: will you be using webkit for the main view (not the sidebar)? that would give you a simple way to create some nice javascript transitions from one view to another and could be painlessly , at a later date, integrated on ubuntu.com as a webfrontend to ubuntu repos + paid app store for commercial products. 
and yes I'm heavily inspirted by itunes but so is mpt from the look of things (which isn't a bad thing considering that they have great user design).

---

### Post by Slug71 on 2009-07-22
> **mpt said:**
> I’m still undecided as to whether Update Manager should remain separate, or become an expandable view of AppCenter.

I think im leaning toward Update Manager remaining seperate too.


> **mpt said:**
> As I understand it, applications can use a PackageKit API to request the installation of extra components [such as fonts]("http://blogs.gnome.org/hughsie/2008/12/01/packagekit-and-pango-are-now-friends/"). That installation process might use part of the AppCenter interface on Ubuntu. Or it might not. We’ll see.

So basically AppCenter would take the place of gnome-packagekit, similar to how Opensuse's ZYpp works with PK?

---

### Post by ronacc on 2009-07-22
suse needed to do something , YAST was the most godawful package manager I have ever used. Synaptic on the other hand works very well .

---

### Post by Slug71 on 2009-07-22
> **ronacc said:**
> suse needed to do something , YAST was the most godawful package manager I have ever used. Synaptic on the other hand works very well .

Haha, have never used OpenSuse. Hopefully will get to try it out on our next Desktop.

---

### Post by mpt on 2009-07-22
> **zekopeko said:**
> How about having a "Install" button and a "Description" button in the list? That way if i know what i want i can just click install and/or queue multiple applications for quick install.

Ah, you might be on to something there. “Install” vs. “More Info”, perhaps.

It would still look a bit ugly, though. If you’re using a large screen looking at a category — or search results — where you can see dozens of items at once, that would be a lot of “Install Now” buttons and “More Info” buttons on the screen at once. (iTunes has a similar problem: “[GET GET GET GET GET GET GET]("http://www.gizmo.com.au/email/guide/nov08/images/pod-abc-vodcast-list-lrg.jpg")” “[SUBSCRIBE SUBSCRIBE SUBSCRIBE SUBSCRIBE]("http://www.flickr.com/photos/kansirnet/94481010/sizes/o/")” etc. And so does Launchpad, “[view this bug view this bug view this bug view this bug]("http://launchpad.net/bugs/402147")”…) The traditional solution to this kind of problem is to select the item with one click, and then act on it with a second click on a toolbar button; but that’s both slower and less obvious. Hmmm.

> *on a tehnical note: will you be using webkit for the main view (not the sidebar)? that would give you a simple way to create some nice javascript transitions from one view to another*

At the moment, I expect GTK will be able to perform the kind of effects we need. (It would be rather sad if an HTML+CSS implementation could perform effects that a native toolkit could not.) I’m not averse to using WebKit if we need to, though.

> *and could be painlessly , at a later date, integrated on ubuntu.com as a webfrontend to ubuntu repos + paid app store for commercial products.*

I have no plans to use a Web site either for presenting packages or for selling software. A native client can do a much better job of both those things.

---

### Post by ronacc on 2009-07-22
> The traditional solution to this kind of problem is to select the item with one click, and then act on it with a second click on a toolbar button; but that&#8217;s both slower and less obvious. Hmmm.
how about a right click "context menu" (install ,  more info , whatever) thats pretty universal .

---

### Post by BwackNinja on 2009-07-22
> **ronacc said:**
> how about a right click "context menu" (install ,  more info , whatever) thats pretty universal .

Right click, while solving the problem of a cluttered screen isn't really obvious and should mostly be filled with extra tasks while the most important actions should be presented in the most easily seen and accessible way.

At best I guess it could be remedied by extra instruction on the window about what to do.

---

### Post by ronacc on 2009-07-22
I think right click for options is common enough that most will be familiar with it , but yes if necessary a line at the top of the page "saying right click on a file (package?) for options ".

---

### Post by zekopeko on 2009-07-22
> **mpt said:**
> Ah, you might be on to something there. &#8220;Install&#8221; vs. &#8220;More Info&#8221;, perhaps.

It would still look a bit ugly, though. If you&#8217;re using a large screen looking at a category &#8212; or search results &#8212; where you can see dozens of items at once, that would be a lot of &#8220;Install Now&#8221; buttons and &#8220;More Info&#8221; buttons on the screen at once. (iTunes has a similar problem: &#8220;[GET GET GET GET GET GET GET]("http://www.gizmo.com.au/email/guide/nov08/images/pod-abc-vodcast-list-lrg.jpg")&#8221; &#8220;[SUBSCRIBE SUBSCRIBE SUBSCRIBE SUBSCRIBE]("http://www.flickr.com/photos/kansirnet/94481010/sizes/o/")&#8221; etc. And so does Launchpad, &#8220;[view this bug view this bug view this bug view this bug]("http://launchpad.net/bugs/402147")&#8221;&#8230;) The traditional solution to this kind of problem is to select the item with one click, and then act on it with a second click on a toolbar button; but that&#8217;s both slower and less obvious. Hmmm.

How about this? On every view were there is a list highlight/select the first/top entry and show [Install] [More Info] button. The rest of the items in the list shouldn't have any buttons shown (ie. invisible). So only on selecting/highlighting/mouse-overing the relevant entry you fade in the buttons (maybe even expand them).
 
The point of the first selected entry is to show the user that there are button for operations.
And list items could be, by default, collapsed and expanded on s/h/m-ing (but not by using the little triangle from tree view in nautilus).

EDIT: here is what is was roughly thinking: [http://www.apple.com/downloads/](http://www.apple.com/downloads/) (the All downloads vertical menu on the left) 

> 
At the moment, I expect GTK will be able to perform the kind of effects we need. (It would be rather sad if an HTML+CSS implementation could perform effects that a native toolkit could not.) I&#8217;m not averse to using WebKit if we need to, though.

I was asking because I haven't seen any fancy transition in usual Gnome apps. Everything is shown instantly. I prefer the OSX approach to those kinds of things.

---

### Post by ronacc on 2009-07-22
>  here is what is was roughly thinking: [http://www.apple.com/downloads/](http://www.apple.com/downloads/) (the All downloads vertical menu on the left)

I'd like that if it was click to expand rather than on mouse over .

> I was asking because I haven't seen any fancy transition in usual Gnome apps. Everything is shown instantly. I prefer the OSX approach to those kinds of things.

please make any fancy effects selectable ,(desktop effects? , compiz?) they are a matter of taste .

---

### Post by Maduroutmb on 2009-07-23
I voted for AppCenter because I like the simplicity that it claims to bring. However, I have grave concerns about what is going on here.  Specifically, if AppCenter makes it hard for users to add software sources, then it will be a deal breaker for me (as in I stop using Ubuntu despite the fact that I very much enjoy this distro).  One of my main reasons for switching to Ubuntu from Fedora was the relative ease of finding software sources for packages that were not in the main repositories (e.g. Exaile 0.3 and Open Office 3.0).

I am also aware that Canonical does not make money.  While that's admirable in a sense, it also means that the company will either do what is necessary to become profitable or cease to exist.  If AppCenter is a way to force people into a limited range of software, some of which is not free (in the sense of beer or speech), then it's an ideological deal breaker as well.

So there is a lot going on here, and I would like to see much more in the way of answers.

---

### Post by Slug71 on 2009-07-23
> **ronacc said:**
> how about a right click "context menu" (install ,  more info , whatever) thats pretty universal .

I like this idea. 

> **zekopeko said:**
> How about this? On every view were there is a list highlight/select the first/top entry and show [Install] [More Info] button. The rest of the items in the list shouldn't have any buttons shown (ie. invisible). So only on selecting/highlighting/mouse-overing the relevant entry you fade in the buttons (maybe even expand them).
 
The point of the first selected entry is to show the user that there are button for operations.
And list items could be, by default, collapsed and expanded on s/h/m-ing (but not by using the little triangle from tree view in nautilus).

EDIT: here is what is was roughly thinking: [http://www.apple.com/downloads/](http://www.apple.com/downloads/) (the All downloads vertical menu on the left) 



I like this too however i must agree with ronacc that a click would be better than a mouse over.

> **Maduroutmb said:**
> I voted for AppCenter because I like the simplicity that it claims to bring. However, I have grave concerns about what is going on here.  Specifically, if AppCenter makes it hard for users to add software sources, then it will be a deal breaker for me (as in I stop using Ubuntu despite the fact that I very much enjoy this distro).  One of my main reasons for switching to Ubuntu from Fedora was the relative ease of finding software sources for packages that were not in the main repositories (e.g. Exaile 0.3 and Open Office 3.0).

I am also aware that Canonical does not make money.  While that's admirable in a sense, it also means that the company will either do what is necessary to become profitable or cease to exist.  If AppCenter is a way to force people into a limited range of software, some of which is not free (in the sense of beer or speech), then it's an ideological deal breaker as well.

So there is a lot going on here, and I would like to see much more in the way of answers.

Hopefully we will get more solid info about this soon.  
This post however is a good example of why this thread was started.

---

### Post by zekopeko on 2009-07-23
> **Slug71 said:**
> I like this idea.

You would be amazed how many people ignore the right click context menu. The best argument I can think of for not doing it this way would be Apple. They don't even have a dedicated right click for that reason.

> 
I like this too however i must agree with ronacc that a click would be better than a mouse over.

I left that part for mpt to decide. I also favor the click but I think that a quick user study with a prototype would be best to determine any problem areas.

> 
Hopefully we will get more solid info about this soon.  
This post however is a good example of why this thread was started.

It sucks that it took us 10 pages of posts to get here...

---

### Post by papangul on 2009-07-23
There will be only superficial changes, if ubuntu decides for AppCenter. Why not have some radical changes in the package management system if people are thinking about a change?

Different repos for different releases for a distro with a six month release cycle, maybe this needs to be reconsidered. Right now there are 4 repos(not considering daper) for karmic,jaunty,intrepid, and hardy. The whole thing is cumbersome(almost insane) for everyone concerned- for the devs, the package maintainers, for users. By the time a bug is fixed, the package and the release are almost dated and a new version has been released which introduces a plethora of problems of its own.

Most of the time enthusiastic users have to add private repos to get newer versions of programs, but the practice is dangerous. It has the potential to make ubuntu as malware prone as say windows.

Why not have something in the lines of gentoo package management system - something like stable and masked packages. If someone wants to try out a new version of a package unmask it and use it. If it's lacking in some way revert to the older version and file a bug or two in the process. 

That way, ubuntu can be both cutting edge and rock solid at the same time.Talking about new releases, whatever is the stable snapshot at the release date gets released. No big headache for anyone but the usability and the stability is gaurated.

I don't know whether this is technically feasible, but my point is - new ideas regarding the package management should be considered.

---

### Post by zekopeko on 2009-07-23
> **papangul said:**
> There will be only superficial changes, if ubuntu decides for AppCenter. Why not have some radical changes in the package management system if people are thinking about a change?

Different repos for different releases for a distro with a six month release cycle, maybe this needs to be reconsidered. Right now there are 4 repos(not considering daper) for karmic,jaunty,intrepid, and hardy. The whole thing is cumbersome(almost insane) for everyone concerned- for the devs, the package maintainers, for users. By the time a bug is fixed, the package and the release are almost dated and a new version has been released which introduces a plethora of problems of its own.

Most of the time enthusiastic users have to add private repos to get newer versions of programs, but the practice is dangerous. It has the potential to make ubuntu as malware prone as say windows.

Why not have something in the lines of gentoo package management system - something like stable and masked packages. If someone wants to try out a new version of a package unmask it and use it. If it's lacking in some way revert to the older version and file a bug or two in the process. 

That way, ubuntu can be both cutting edge and rock solid at the same time.Talking about new releases, whatever is the stable snapshot at the release date gets released. No big headache for anyone but the usability and the stability is gaurated.

I don't know whether this is technically feasible, but my point is - new ideas regarding the package management should be considered.

this thread isn't about the foundations of package managment. It's about the frontend. Please open a new thread for it.

---

### Post by mpt on 2009-07-24
> **ronacc said:**
> how about a right click "context menu" (install ,  more info , whatever) thats pretty universal .

Thanks for the suggestion, but presenting it that way would make it invisible to roughly half the potential user base.

> **ronacc said:**
> I think right click for options is common enough that most will be familiar with it , but yes if necessary a line at the top of the page "saying right click on a file (package?) for options ".

All other things being equal, an interface that doesn’t require instructions is better than one that does. If we were going to use a menu at all, it would more likely be a menubutton that was visible by default and therefore didn’t need instructions.

> **zekopeko said:**
> How about this? On every view were there is a list highlight/select the first/top entry and show [Install] [More Info] button. The rest of the items in the list shouldn't have any buttons shown (ie. invisible). So only on selecting/highlighting/mouse-overing the relevant entry you fade in the buttons (maybe even expand them).
 
The point of the first selected entry is to show the user that there are button for operations.
And list items could be, by default, collapsed and expanded on s/h/m-ing (but not by using the little triangle from tree view in nautilus).

Nifty. That still would require two clicks (or hover then adjust+click), but it would be more obvious than putting the buttons in a separate toolbar.

> **Maduroutmb said:**
> Specifically, if AppCenter makes it hard for users to add software sources, then it will be a deal breaker for me (as in I stop using Ubuntu despite the fact that I very much enjoy this distro).

In the short run, I expect it will become slightly easier to add software sources. In the long run, there will need to be some kind of trust and warning system to *discourage* you from adding sources that could compromise your OS.

> *I am also aware that Canonical does not make money. While that's admirable in a sense, it also means that the company will either do what is necessary to become profitable or cease to exist.  If AppCenter is a way to force people into a limited range of software, some of which is not free (in the sense of beer or speech), then it's an ideological deal breaker as well.*

I don’t see how we could “force” anyone to do anything.

> **papangul said:**
> There will be only superficial changes, if ubuntu decides for AppCenter. Why not have some radical changes in the package management system if people are thinking about a change?

That’s a nonsense argument, unless you think we’re changing just for the sake of change. I assure you we are not.

Your points about update lag and the resulting proliferation of third-party repositories are very important, and I think we have to fix that before Ubuntu will become interesting to commercial non-server ISVs. But as zekopeko says, that really should be discussed in a separate thread.

---

### Post by zekopeko on 2009-07-24
> **mpt said:**
> Nifty. That still would require two clicks (or hover then adjust+click), but it would be more obvious than putting the buttons in a separate toolbar.


Well let me the make more suggestions:

The premise is that you always have a single entry highlighted so that the user is always aware of the existence of buttons, either the first one in the list or the last that the user selected (not applicable between different sessions). 
You are also targeting the desktop/laptop screen sizes, so that means at least the 800x480 (which I think is a little to small and applies to only eeepc 700 series, user interfaces that small should be targeted with specialized interfaces like Moblin/MID):

1) Hovering on the entry would expand it by pushing the lower entries down, while keeping the hovered entry fixed in place so that it doesn't "dance around" in the list view. 
Now the problem may arise if you have a small screen (since the expanded entry could stop you from selecting what's above it or more likely whats under it, but this needs to be tested if it's going to be a problem at all. not to mention that we have scrollbars for a reason) but that could be fixed with a fixed size of the expanded entry and the (already) fixed size of the unexpanded entry. 
We only need to give a short description and have the More Info button for the rest.

2) Use fixed size entries like in your wireframes but have the buttons invisible and only show them if you hover over it. The problem here is that GTK likes to use huge buttons so you would have empty space that serves no purpose until you hover over it (perhaps custom buttons that follow your theme/desktop-color but with lower DPI/size)

3) What's wrong with two clicks? Software management isn't something the user is likely to do frequently. For most user's it's a fire-and-forget kind of thing.

I think that the best way to vet that part of the interface would be to create a HTML/CSS/Javascript mockup so that we can try different ideas.
So if somebody would like to do it, that would be awesome.

---

### Post by ronacc on 2009-07-24
> In the short run, I expect it will become slightly easier to add software sources. In the long run, there will need to be some kind of trust and warning system to discourage you from adding sources that could compromise your OS.

A warning to discourage yes but if this should deteriorate into any kind of blocking to enforce "political correctness" I would be extremely unhappy .

> Thanks for the suggestion, but presenting it that way would make it invisible to roughly half the potential user base.

I do not understand why this would "make it invisible to roughly half the potential user base" EVERY web browser even IE uses a rt click to display actions that apply to a link and even very simple laptops like my eeepc 4g have 2 "mouse" buttons , (although it is a da** rocker sw so I can't click both to emulate a middle button).Are there really that many one button mice in use with Ubuntu ?Or do you believe that 1/2 our user base has never used rt click for context ? I would find that assertion hard to believe .

---

### Post by zekopeko on 2009-07-24
> **ronacc said:**
> A warning to discourage yes but if this should deteriorate into any kind of blocking to enforce "political correctness" I would be extremely unhappy .

I *think* that this is going to be integrated with the future share option so that you can see if some of your friend trust it.
The point is to keep users from installing stuff from untrusted repositories. If this becomes trivial to do without safeguards it could damage Linux's perception of being safe.

> 
I do not understand why this would "make it invisible to roughly half the potential user base" EVERY web browser even IE uses a rt click to display actions that apply to a link and even very simple laptops like my eeepc 4g have 2 "mouse" buttons , (although it is a da** rocker sw so I can't click both to emulate a middle button).Are there really that many one button mice in use with Ubuntu ?Or do you believe that 1/2 our user base has never used rt click for context ? I would find that assertion hard to believe .

You are overestimating average users. A left click UI design is far more user friendly because it exposes all of your options at a glance.
Take cue from Mac OSX. They don't even have a dedicated right click button.

---

### Post by ronacc on 2009-07-24
> The point is to keep users from installing stuff from untrusted repositories. If this becomes trivial to do without safeguards it could damage Linux's perception of being safe.

as I stated  a warning IS apropriate anything beyond that is unacceptable to me . I admit I am looking after my own intrests here , as both a tester and a user I install much from 3rd party repos , and not just "official" PPA's , including source code for local compiling , I also install some things that let us say are not looked upon kindly in my country , that is why the comment about "political correctness" .

> You are overestimating average users. A left click UI design is far more user friendly because it exposes all of your options at a glance.
Take cue from Mac OSX. They don't even have a dedicated right click button.

I guess I have more faith in the "average" user , after all  as I stated EVERY web browser I know of  ( I don't do mac so I havent tried safari) uses rt click for context/actions . If the "average" user is ignorant of even how to use a browser , I don't think I'm in Kansas anymore.

---

### Post by Maduroutmb on 2009-07-25
> In the short run, I expect it will become slightly easier to add software sources. In the long run, there will need to be some kind of trust and warning system to *discourage* you from adding sources that could compromise your OS.

A lot of users would benefit from a limited, central repository in terms of security and ease of use.  Add/Remove Programs is great for most people.  However, some of the programs that matter most to me are not in Ubuntu's repositories.  If Handbrake weren't easy to install and use in Ubuntu, I would have to find another distro.  I enjoy playing an FPS without leaving linux every so often, and Urban Terror is a great time waster in that regard.  Not in the repos.  I can use exaile 0.3, but again, not in the repos.

I like the current distiction between Add/Remove (simple) and Synaptic and Software Sources (advanced).  I think it would be great to consolidate functions, but not at the expense of the advanced mode that allows users to tweak their systems.  This dovetails with what was said about keeping software up to date with the 6 month release cycle: it's understandable that you guys cannot test every piece of software with a .deb package with each release, and nobody really expects you to.  However, the independent developers with their own software sources contribute very important things that the main repos simply do not have.

> I don’t see how we could “force” anyone to do anything.

If I can't install something via a package, I don't do it.  I am a highly technical user, but I don't work with computers for a living (which is something that gets lost in these communities- very, very few people actually compile things from source and then hunt down and install the supporting libraries).  Ubuntu's biggest strengths are 1.) the strong userbase that can tell people like me how to make things work and 2.) the fact that if it's open source, it very likely has a .deb made specifically for a recent Ubuntu release.  If point #2 ends because the new package manager is not designed to accept new software sources, then you have forced people like me to use only the packages in the provided repos.  That means that we will either give up on some of the FOSS software that we enjoy or leave for a distro that does not limit choice in that fashion.

I don't know what form AppCenter will take, so I don't mean this as a criticism.  Rather, I think of these as important considerations that other users probably share that you guys should probably consider when designing this thing.

---

### Post by mpt on 2009-07-25
> **ronacc said:**
> I do not understand why this would "make it invisible to roughly half the potential user base" EVERY web browser even IE uses a rt click to display actions that apply to a link and even very simple laptops like my eeepc 4g have 2 "mouse" buttons , (although it is a da** rocker sw so I can't click both to emulate a middle button).Are there really that many one button mice in use with Ubuntu ?Or do you believe that 1/2 our user base has never used rt click for context ? I would find that assertion hard to believe .

That many programs have shortcut menus, and most pointing devices have secondary buttons, does not mean that most people use them.

We don’t have precise statistics on this. But, for example, [Dave Richards]("http://davelargo.blogspot.com/") of the City of Largo told us during last year’s UX hackfest that half of the Gnome users he oversees never use the right mouse button. And that’s in line with my own observations from years of working at Internet cafés.

---

### Post by ronacc on 2009-07-25
I will have to accept your observations since I have no data to dispute it.

---

### Post by zekopeko on 2009-08-04
any update on this?

---

### Post by Slug71 on 2009-08-04
> **zekopeko said:**
> any update on this?

I dont think we will hear/see anything about this for a few more weeks yet.

---

### Post by phenest on 2009-08-04
It does look like most agree that Synaptic does already do everything we need. Indeed, Update Manager and Add/Remove will refer you to Synaptic on occasions. But Synaptic is jolly confusing and difficult to use for a novice user. If the reason to develop a new app is to make it easier to use graphically, then why cannot Synaptic be redesigned to accommodate this. To give Synaptic 2 'views': Basic & Advanced.

I may have missed several points regarding AppCentre here, but if Synaptic is already a central point to do everything, then why not give it a new GUI? Did we really need Computer Janitor? From a novice user's perspective: yes. But that's the only reason.

Currently, my vote is for Synaptic, simply because there is no working model for AppCentre to make a comparison. But I'd hate to see work going into the development of a new app, just for users to vote against it, when the effort could have been more wisely used in redeveloping an existing app, namely Synaptic.

---

### Post by Slug71 on 2009-08-04
> **phenest said:**
> It does look like most agree that Synaptic does already do everything we need. Indeed, Update Manager and Add/Remove will refer you to Synaptic on occasions. But Synaptic is jolly confusing and difficult to use for a novice user. If the reason to develop a new app is to make it easier to use graphically, then why cannot Synaptic be redesigned to accommodate this. To give Synaptic 2 'views': Basic & Advanced.

A 'Basic and Advanced' type GUI is exactly what i have proposed to mpt already with some mockups.

---

### Post by 23meg on 2009-08-04
> **Slug71 said:**
> A 'Basic and Advanced' type GUI is exactly what i have proposed to mpt already with some mockups.

It's been established in the literature of interaction design in recent years that splitting user interfaces into modes classified by "advancedness" is a bad idea for general purpose software for multiple reasons. People don't always have a clue regarding which one they want in a given situation, especially at their first few encounters with the software. And in the use case that when working in one of the modes the user needs to access a feature that's only available in the other one, they have to switch the entire interface to get to it, and then switch back. 

Also note that AppCenter is to be based on gnome-app-install, not written from the ground up. Trying to rewire and redress Synaptic to work as intended in the AppCenter specification, and keep it maintainable, would likely be more work than even writing it from scratch.

---

### Post by phenest on 2009-08-04
> **23meg said:**
> It's been established in the literature of interaction design in recent years that splitting user interfaces into modes classified by "advancedness" is a bad idea for general purpose software for multiple reasons. People don't always have a clue regarding which one they want in a given situation, especially at their first few encounters with the software.

Not necessarily true. Consider the calculator and it's many different modes. But even a simpleton know which one he needs. What your saying is to provide one interface with one set of features, and tough if you wanted some advanced options. Rather than dumb everything down, consider an intuitive interface instead, so a novice can learn. Perhaps a thorough help file written in plain English would help?

> **23meg said:**
> And in the use case that when working in one of the modes the user needs to access a feature that's only available in the other one, they have to switch the entire interface to get to it, and then switch back.

And? If you had 2 programs, 1 basic and the other advanced, they would be switching between them. Unless you're thinking of only providing a basic one so we don't have access to the advanced section.

> **23meg said:**
> Also note that AppCenter is to be based on gnome-app-install, not written from the ground up. Trying to rewire and redress Synaptic to work as intended in the AppCenter specification, and keep it maintainable, would likely be more work than even writing it from scratch.

Let me get this straight. AppCenter is not going to be written from scratch, but if Synaptics was, it would take less time?

---

### Post by 23meg on 2009-08-04
Reposting my previous post, which I couldn't edit for some reason (likely a Javascript bug on my side):

> **23meg][QUOTE=Slug71 said:**
> A 'Basic and Advanced' type GUI is exactly what i have proposed to mpt already with some mockups.

It's been established in the literature of interaction design in recent years that splitting user interfaces into modes classified by "advancedness" is a bad idea for general purpose software for multiple reasons. People don't always have a clue regarding which one they want in a given situation, especially at their first few encounters with the software. And in the use case that when working in one of the modes the user needs to access a feature that's only available in the other one, they have to switch the entire interface to get to it, and then switch back. 

Also note that AppCenter is to be based on gnome-app-install, not written from the ground up. Trying to rewire and redress Synaptic to work as intended in the AppCenter specification, and keep it maintainable, would likely be more work than even writing it from scratch.[/QUOTE]

---

### Post by 23meg on 2009-08-04
> **phenest said:**
> Not necessarily true. Consider the calculator and it's many different modes. But even a simpleton know which one he needs. What your saying is to provide one interface with one set of features, and tough if you wanted some advanced options. Rather than dumb everything down, consider an intuitive interface instead, so a novice can learn. Perhaps a thorough help file written in plain English would help?

The calculator is a simple, single-purpose application with a well known physical counterpart, which has little room for exploration. A software management application is almost the polar opposite.

I'm not advocating "dumbing everything down", by the way. 

[QUOTE=phenest]And? If you had 2 programs, 1 basic and the other advanced, they would be switching between them. Unless you're thinking of only providing a basic one so we don't have access to the advanced section.[/QUOTE]

I didn't propose having two programs either.

[QUOTE=phenest]Let me get this straight. AppCenter is not going to be written from scratch, but if Synaptics was, it would take less time?[/QUOTE]

Sorry, the wording was a bit off and I couldn't edit my post to clarify; I meant that to redress and rewire Synaptic according to the AppCenter specification and keep the resulting application maintainable would likely take more effort than even writing AppCenter from scratch.

---

### Post by ronacc on 2009-08-04
> The calculator is a simple, single-purpose application with a well known physical counterpart, which has little room for exploration. A software management application is almost the polar opposite.
 
I don't think he was necessairly refering to the gnome calculator but to calculators in general . I have never bothered to count all the different modes my HP calculator has but there are several that I regularly use according to the task I am performing .And one of the first things I install on any distro is a multi mode RPN calculator .
   And his point about a good help file is well taken , If more effort was put into good documentation and less into fancy interface design many problems would never arise in the first place . Yes someone new to ANY distro or OS is ignorant , but the cure for ignorance is learning not making things harder for everyone .

---

### Post by phenest on 2009-08-04
I just can't help thinking that AppCenter is going to eventually replace Synaptics with something that lacks some of the more advanced features that Synaptics has. And in trying to add them, will end up being what Synaptics is now, with maybe a better GUI. In the time that will take to happen, Synaptics could be redressed. And Synaptics doesn't have to be given a new face overnight. It could happen at a gradual pace, building up to what we want.

Perhaps a proposal of gradual changes to Synaptics would be more worth while.
[LIST=1]Starting with an improved upgrade system so as to do away with update-manager
[*]Improved package/application installation/removal, to do away with Add/Remove and Computer Janitor
[*]A Basic/Advanced view that toggles the package list between Applications and packages.[/LIST]
Doesn't seem lengthy or complicated to me.

The evolution of humans has taken place over millions of years changing from one species to another with subtle modifications and additions. I would expect the next evolutionary stage after us to be an improvement of us, rather than a direct replacement.

Take the invention of the wheel, starting it's history as a mere disc of wood. A hole was added at the center for an axle. Spokes were introduced to make it lighter. A metal band around it edge was added to make it more durable. A bearing was added to the axle to make it faster. A rubber band was added at the edge to reduce stress. The rubber band was inflated to make it more comfortable. But it hasn't been re-invented. Just improved.

Ok. It's getting late, and I'm tired. I may have just waffled on there really. I hope I didn't lose the point towards the end.

---

### Post by 23meg on 2009-08-04
> **ronacc said:**
> I don't think he was necessairly refering to the gnome calculator but to calculators in general . 

Physical calculators aren't software, so applying software design principles to them would be a mistake.

> **ronacc]I have never bothered to count all the different modes my HP calculator has but there are several that I regularly use according to the task I am performing .And one of the first things I install on any distro is a multi mode RPN calculator .[/QUOTE]

If you know that you need something called an "RPN calculator", you can be assumed not to be a person who is going to have a hard time with calculator modes, so your case is a specialized one. AppCenter is intended to be a software management application meant for a broad audience, so the example doesn't really fit.

[QUOTE=ronacc said:**
> And his point about a good help file is well taken , If more effort was put into good documentation and less into fancy interface design many problems would never arise in the first place . Yes someone new to ANY distro or OS is ignorant , but the cure for ignorance is learning not making things harder for everyone .

While good documentation is obviously desirable, discoverability of the most prominent features without *having to* read documentation is even more so, as stated in the [the Ubuntu architecture principles]("https://wiki.ubuntu.com/UbuntuArchitecture").

---

### Post by phenest on 2009-08-04
> **23meg said:**
> Physical calculators aren't software, so applying software design principles to them would be a mistake.

They both have the same functions with the same expected results and laid out in the same way.

> **23meg said:**
> If you know that you need something called an "RPN calculator", you can be assumed not to be a person who is going to have a hard time with calculator modes, so your case is a specialized one. AppCenter is intended to be a software management application meant for a broad audience, so the example doesn't really fit.

A person may use a scientific calculator knowing full well their only requirement is adding and subtracting. They will simply ignore the rest of the functions, and concentrate on those they recognize. And you should never assume.

> **23meg said:**
> While good documentation is obviously desirable, discoverability of the most prominent features without *having to* read documentation is even more so, as stated in the [the Ubuntu architecture principles]("https://wiki.ubuntu.com/UbuntuArchitecture").

You're very rigid in your thinking 23meg. What you call a prominent feature is subject to a persons requirements. All features must be prominent. You shouldn't hide something because you think it will be less used. By your way of thinking, we could do away with documentation if we simply label things a little better. Perhaps we could, but I think users will learn less.

---

### Post by 23meg on 2009-08-04
> **phenest said:**
> They both have the same functions with the same expected results and laid out in the same way.

Not a matching example, but one that illustrates the point: the same can be said of a handwritten letter and one written on a word processor. That doesn't make pen and paper design the same thing as software interaction design, and doesn't mean that the same principles can be applied without hesitation to both.

> **phenest]A person may use a scientific calculator knowing full well their only requirement is adding and subtracting. They will simply ignore the rest of the functions, and concentrate on those they recognize. And you should never assume.[/QUOTE]

If they have to, surely. But for most people in that position it will be a less pleasant experience, and as a designer I would prefer to be able to provide them with the right tool for the job rather than assume that scientific calculators are how calculators should be and everyone should just tolerate their complexity and use them and that's the bottom line. But as I've said, the calculator example is not a fitting one, so I'm not going to go further in it for the sake of argument.

[QUOTE=phenest said:**
> You're very rigid in your thinking 23meg. What you call a prominent feature is subject to a persons requirements. All features must be prominent. You shouldn't hide something because you think it will be less used. By your way of thinking, we could do away with documentation if we simply label things a little better. Perhaps we could, but I think users will learn less.

I think it's your interpretation of my thinking that's rigid. I didn't even once talk about hiding things because they will be less used, or doing away with documentation. Please don't put words into my mouth.

---

### Post by ronacc on 2009-08-04
> **23meg said:**
> Physical calculators aren't software, so applying software design principles to them would be a mistake.



If you know that you need something called an "RPN calculator", you can be assumed not to be a person who is going to have a hard time with calculator modes, so your case is a specialized one. AppCenter is intended to be a software management application meant for a broad audience, so the example doesn't really fit.



While good documentation is obviously desirable, discoverability of the most prominent features without *having to* read documentation is even more so, as stated in the [the Ubuntu architecture principles]("https://wiki.ubuntu.com/UbuntuArchitecture").

I don't "need" an RPN calculator I just happen to prefer that method of entry I can also use algabraic entry I just find it less "natural" .

So they eaisly "discover" some "feature" if they don't know what it does what have they gained ?

---

### Post by 23meg on 2009-08-04
[QUOTE=ronacc]So they eaisly "discover" some "feature" if they don't know what it does what have they gained ?[/QUOTE]

"Discovering" in the sense I'm talking about it necessarily entails understanding what a feature does, and doesn't necessarily preclude learning to use software through reading documentation.

Still, I recommend doing some ad-hoc user testing, requesting people to install applications through a graphical interface in Ubuntu, in which you observe the percentage of people who resort to Synaptic's documentation *at all*, as well the extent to which it helps them accomplish tasks that they got stuck with.

Documentation should be considered a must-have supplement to good design; not a band aid for bad design.

---

### Post by ronacc on 2009-08-04
> **23meg said:**
> "Discovering" in the sense I'm talking about it necessarily entails understanding what a feature does, and doesn't necessarily preclude learning to use software through reading documentation.

Still, I recommend doing some ad-hoc user testing, requesting people to install applications through a graphical interface in Ubuntu, in which you observe the percentage of people who resort to Synaptic's documentation *at all*, as well the extent to which it helps them accomplish tasks that they got stuck with.

Documentation should be considered a must-have supplement to good design; not a band aid for bad design.

  some things lend themselves to easy "discovery" in the sense that you mean , as a trivial example a slide bar labeled volume control is pretty self explanatory. software management beyond the "click here to install this virus/malware " involves complexity that is not obvious from a gui without documentation and at-least some effort to learn on the part of the user ,an example of this would be the distinction between upgrade and dist-upgrade. I agree that good documentation is a "must" and sadly the man pages are sometimes a bit obscure even to someone who has fallen off the turnip truck more than once .

   If you saw one of my posts earlier in this thread you know that I am in fact attempting to do some adhoc testing , unfortunately when I chose my subjects/victims I neglected to take into account that the granddaughter was getting married in a week and the grandmother ( yes a real grandmother) was involved in the preparations . The wedding was this Saturday just passed and all are recuperating nicely so I should be able to proceed soon .

---

### Post by 23meg on 2009-08-04
> **ronacc]some things lend themselves to easy "discovery" in the sense that you mean , as a trivial example a slide bar labeled volume control is pretty self explanatory. software management beyond the "click here to install this virus/malware " involves complexity that is not obvious from a gui without documentation and at-least some effort to learn on the part of the user ,an example of this would be the distinction between upgrade and dist-upgrade.[/QUOTE]

The very notion of using a "package manager" to install software from a "repository" is going to be a significant paradigm shift to more than 90% of all computer users, and needs introduction and learning in any case. Two good places to actively introduce it to users are the OS installation sequence (via a brief slideshow), and an entrance screen or pane on the software management application. The AppCenter, by its current specification, is fit to cover the latter. To check out how poorly Synaptic currently handles this, click "Help > Quick Introduction".

[QUOTE=ronacc said:**
> I agree that good documentation is a "must" and sadly the man pages are sometimes a bit obscure even to someone who has fallen off the turnip truck more than once .

I don't think many people looking for help on using a graphical software management tool, especially those who are new to Ubuntu, will resort to man pages. Synaptic has pretty good documentation accessible with two clicks on the "Help" menu.

> **ronacc said:**
> If you saw one of my posts earlier in this thread you know that I am in fact attempting to do some adhoc testing , 

I did; I suggested this because I thought you'd be inclined to do it.

---

### Post by ronacc on 2009-08-05
one way to handle this would be a seperate tutorial cd  or a desktop button to download a tutorial covering not just package management but other aspects of Ubuntu/linux that would be unfamiliar to a new user . I took a look at the quick introduction you mention and while it is far from perfect I think it would be easier to fix that than it would be to create a whole new package management gui. My reference to man pages was not aimed specificly at synaptic but to the state of documentation in general , there is much good information both on the web and scattered about the forums but it sometimes takes a bit of effort to find it. I think a really good tutorial/help function would go a very long way tword making Ubuntu THE gateway to linux .

---

### Post by phenest on 2009-08-05
> **23meg said:**
> If they have to, surely. But for most people in that position it will be a less pleasant experience, and as a designer I would prefer to be able to provide them with the right tool for the job rather than assume that scientific calculators are how calculators should be and everyone should just tolerate their complexity and use them and that's the bottom line. But as I've said, the calculator example is not a fitting one, so I'm not going to go further in it for the sake of argument.

Most people? I think you're guessing now. I'm not suggesting that users should tolerate complexity, but rather if you remove the complexity, what about the advanced users? While the novice will be happy with this, the advanced user will see it as dumbing down and question why the original complex app was removed.

> **23meg said:**
> I think it's your interpretation of my thinking that's rigid.

Don't throw things back in my face just because you don't have a proper answer.

> **23meg said:**
> I didn't even once talk about hiding things because they will be less used, or doing away with documentation. Please don't put words into my mouth.

I'm not. But your ideas suggest that this is where it could lead, if you're not careful.

While I agree with the idea behind this, and it's probably a bit overdue and needed, I really don't see how you can satisfy both novice and advanced users with one app.

But you go right ahead and develop AppCenter and I will test it and give you my feedback. But I don't see how developing AppCenter will take less time than giving Synaptics a face lift.

As a developer myself, I know how easy it is to create the worlds best software whilst having the worlds worst interface (and vice versa). But it is easier to take the one with a poor gui and improve that.

---

### Post by ronacc on 2009-08-05
@ Phenest   While I am on your side on this , synaptic could use some "love" . Taking the quick introduction that 23meg pointed out (see screenshot) in its present state it is more confusing than helpful . 1 double clicking a package name marks it instead of bringing up an action menu . 2 context menu shoud perhaps read right click menu in keeping with things noted by some about context menus elsewhere in this thread . 3 what status icon ? . None of these are "showstoppers" but do need attenion .

---

### Post by 23meg on 2009-08-05
> **phenest said:**
> Most people? I think you're guessing now. I'm not suggesting that users should tolerate complexity, but rather if you remove the complexity, what about the advanced users? While the novice will be happy with this, the advanced user will see it as dumbing down and question why the original complex app was removed.

In this case, Synaptic will not be going anywhere unless its core functionality is provided by AppCenter, and even in the unlikely case that some of it is lost, "advanced users" will always be able to install it with a single command, so there's not much to worry about.

It's also a better idea to think in terms of specific user requirements and mental models instead of a one-dimensional scale of "advancedness". "Advanced users" don't look for more complexity; like every other user they look for specific means in which to perform their required tasks, which are more complex and more numerous. 

[QUOTE=phenest]Don't throw things back in my face just because you don't have a proper answer.
[/QUOTE]

I did provide what I think are appropriate answers to your queries. You're of course free to disagree with them, but saying that I don't have "proper" answers is not very courteous when I've taken hours to reply to you.

---

### Post by phenest on 2009-08-05
> **23meg said:**
> In this case, Synaptic will not be going anywhere unless its core functionality is provided by AppCenter, and even in the unlikely case that some of it is lost, "advanced users" will always be able to install it with a single command, so there's not much to worry about.

Then why not have 2 apps? Have AppCenter by default, but Synaptics will be available as a direct replacement/addition should the user choose.

> **23meg said:**
> It's also a better idea to think in terms of specific user requirements and mental models instead of a one-dimensional scale of "advancedness". "Advanced users" don't look for more complexity; like every other user they look for specific means in which to perform their required tasks, which are more complex and more numerous.

The words 'advanced' and 'basic' are only being used here to refer te the type of user, and not the controls of the app. Having said that, the advanced user will be looking for controls that the basic user will not. In order to prevent the basic user from being confused by the advanced controls, the advanced controls will have to be 'hidden'. This is where the problem lies. You will have, to some extent, a basic view and an advanced view, that can be toggled between. But I don't think that the view will change that much, e.g. the basic view will show a list of applications whereas the advanced view will show all packages. A right click context menu will alter slightly depending on the view showing appropriate functions.

> **23meg said:**
> when I've taken hours to reply to you.

Learn to type faster then. :wink:

---

### Post by zekopeko on 2009-08-05
@ronacc and phenest

I believe you are both wrong in your assumptions and 23meg pointed them out rather nicely. A bad design is requiring your users to read documentation for using the core functionality of an application. Those actions should be as intuitive as possible for users (be they "basic or advanced").
Good documentation is just a part of the solution.

---

### Post by mpt on 2009-08-05
> **zekopeko said:**
> any update on this?

After another meeting yesterday, the roadmap has returned to its original route: replace Add/Remove in 9.10, replace Synaptic in 10.04, allow purchasing software in 10.10. Meanwhile, Michael Vogt is continuing work on implementing the category gallery and faster searching. Hopefully we’ll have an initial release sometime in the next couple of weeks.

> **phenest said:**
> If the reason to develop a new app is to make it easier to use graphically, then why cannot Synaptic be redesigned to accommodate this. To give Synaptic 2 'views': Basic & Advanced.

I really should write an article about this, so I can point to it every time someone asks this question about any application. :) 23meg has [summarized the reasons well]("http://ubuntuforums.org/showpost.php?p=7734136&postcount=126") for AppCenter.

> **phenest said:**
> Then why not have 2 apps? Have AppCenter by default, but Synaptics will be available as a direct replacement/addition should the user choose.

For exactly the same reasons.

> **ronacc said:**
> If more effort was put into good documentation and less into fancy interface design many problems would never arise in the first place . Yes someone new to ANY distro or OS is ignorant , but the cure for ignorance is learning not making things harder for everyone .

If you reverse everything in that paragraph, it’ll be just about right. :P Few people read standalone help, so it’s usually better to [make the interface itself more helpful and explanatory]("https://wiki.ubuntu.com/EmbeddedHelp"). And I intend to make things easier for everyone, not harder for everyone.

> **phenest said:**
> What you call a prominent feature is subject to a persons requirements. All features must be prominent. You shouldn't hide something because you think it will be less used.

There is no computer screen large enough to contain a button for every one of Ubuntu’s features. So, some features are visible by default, some require going into a menu, some require going into a submenu, some require opening a window, some require opening a window and then choosing another menu item, some require opening a window and then choosing another menu item and then doing something in a dialog, *etc* *etc* *etc*. Every time a designer decides where to put something in an interface, one of the things they are taking into account is how often people will use it, which influences how prominent the feature should be. It’s part of our job.

> *By your way of thinking, we could do away with documentation if we simply label things a little better. Perhaps we could, but I think users will learn less.*

If we can let people achieve their goals without having to learn as much about the interface, we win.

---

### Post by ronacc on 2009-08-05
> **23meg said:**
> In this case, Synaptic will not be going anywhere unless its core functionality is provided by AppCenter, and even in the unlikely case that some of it is lost, "advanced users" will always be able to install it with a single command, so there's not much to worry about.

It's also a better idea to think in terms of specific user requirements and mental models instead of a one-dimensional scale of "advancedness". "Advanced users" don't look for more complexity; like every other user they look for specific means in which to perform their required tasks, which are more complex and more numerous. 

  one aspect of synaptic that contributes to the look of complexity that synaptic has is that it shows ALL packages that are available in the selected repos (for your arch) , add-remove etc  are very deficient in this . While yes I am quite comfortable using apt from terminal to install a package , I don't always know the name of the package and synaptic provides a search function . Also the ability to add repos even though they may not be "approved" is essential since many good and safe pieces of software are not available in the "normal" repos for whatever reason . I am quite willing to test appcenter when something becomes available to try but if it lacks the above features I will not give a favorable opinion .
  Yes something like package management , even more than most apps , should be "task oriented"  but I think synaptic is quite good in this respect as far as function is concerened, exposing this functionality to the new user is where it falls short IMHO .

---

### Post by 23meg on 2009-08-05
> **phenest said:**
> Then why not have 2 apps? Have AppCenter by default, but Synaptics will be available as a direct replacement/addition should the user choose.

Ubuntu's "one application per task by default" principle is well known, and isn't going to change in the near future. From [https://wiki.ubuntu.com/UbuntuArchitecture:](https://wiki.ubuntu.com/UbuntuArchitecture:)

> There should be exactly one recommended way to accomplish a task in the default installation, to promote consistent documentation and support 

Of course, as I said, Synaptic will always be available for installation should people prefer it.

> **phenest]The words 'advanced' and 'basic' are only being used here to refer te the type of user, and not the controls of the app. [/QUOTE]

I would also contest the idea that there is such a thing as a "basic" or "advanced" user said:**
> personas[/URL] with specific habits and requirements.

[QUOTE=phenest]Learn to type faster then. :wink:

Then perhaps I may humbly suggest that you learn to think slower. It's the thinking, not the typing.

---

### Post by seeker5528 on 2009-08-06
> **phenest said:**
> The words 'advanced' and 'basic' are only being used here to refer te the type of user, and not the controls of the app. Having said that, the advanced user will be looking for controls that the basic user will not. In order to prevent the basic user from being confused by the advanced controls, the advanced controls will have to be 'hidden'. This is where the problem lies. You will have, to some extent, a basic view and an advanced view, that can be toggled between. But I don't think that the view will change that much, e.g. the basic view will show a list of applications whereas the advanced view will show all packages. A right click context menu will alter slightly depending on the view showing appropriate functions.

I don't view basic and advanced that way. It's about presenting the user with the right range of choices for what is needed in a particular situation.

%95+ of the time you don't need that much. Select what you want to install, select what you want to remove, apply the actions, done.

The question is how to you provide the tools and present them in the UI to deal with additional circumstances where you don't want to treat recommends as dependencies or things are borked for whatever reason?

There are a fair amount of situation/tasks where more functions may be desired.

 If you are installing from a PPA or third party repository there may be oddities with dependencies because the people packaging the stuff in the official repositories don't know and shouldn't be expected to know what's going on with all those other packages. Which could also come into play later when you want to upgrade to a newer version of the distribution.

Things might be in a bad state because installation/removal was interrupted.
 
 With development versions installation or removal scripts may be borked. Transitions may lead to conflicts between packages that depend on the new stuff and packages that still depend on the old stuff or dependencies may be unsatisfied because the new stuff didn't all make it into the repositories at the same time. 

What are the mechanisms to get more information, depends, recommends, suggests, dependents, etc... for the currently installed and available versions of a package and how are they presented in the UI?  

What opportunities does the UI present to use that information to downgrade a package here, choose a different package to satisfy a dependency there?

Basic and advanced is probably the wrong way to look at it, it's more like...

Show me what I normally need.....
OK, now show me more.

The "more" might be an expanded context menu, and/or things on the normal context menu that bring up an additional window for viewing package information or an additional window with troubleshooting tasks, etc...

Also would be nice when you are viewing some software and a list of it's optional packages that, if there are multiple packages that would satisfy a dependency, you had the option to choose which package to use to satisfy that dependency. Not needed all that often, but desirable/necessary in some circumstances. 

Later, Seeker

---

### Post by seeker5528 on 2009-08-06
> **ronacc said:**
> I agree that good documentation is a "must" and sadly the man pages are sometimes a bit obscure even to someone who has fallen off the turnip truck more than once.


Man pages are not intended to be documentation, just a simple display/description of usage and options.

If the usage and options are simple, the man page will probably be all you ever need, if not the man page is not and should not try to be made a substitute for having real documentation.

Later, Seeker

---

### Post by ronacc on 2009-08-06
> **seeker5528 said:**
> Man pages are not intended to be documentation, just a simple display/description of usage and options.

If the usage and options are simple, the man page will probably be all you ever need, if not the man page is not and should not try to be made a substitute for having real documentation.

Later, Seeker

I did not imply that the man pages were the "real documentation" , merely gave them as an example of how documentation can sometimes be obscure even to someone with a bit of knowledge let alone a newbe .

---

### Post by NCLI on 2009-08-06
Most people(including me, a fairly advanced user) don't read documentation unless they are totally lost, which the user shouldn't be if the interface was well designed in the first place. Therefore, Interface > Documentation in terms of importance to the average user(s I know).

---

### Post by iswan on 2009-08-06
My first time using Ubuntu, I didn't understand what synaptic is until I opened the application and figured it out. But with AppCenter term I think it is easier to understand even without opening the application first, you already know that it is a place to manage your application.

---

### Post by phenest on 2009-08-07
> **23meg said:**
> I would also contest the idea that there is such a thing as a "basic" or "advanced" user

Users with no ability to learn and those who are willing to learn. Pretty straight forward really.

The whole point of what I and others have being trying to put forward, is that it doesn't require another application. There is already a perfectly good one. The work involved is minimal, because its needs are minimal.

This mentality that Canonical has of replacing perfectly good software is getting silly. Take the On Screen Notification: What Canonical has replaced it with is less useful and less configurable. You may argue that I could disable it, and use the original, but that would be a stupid thing to suggest. Because if everyone did just that, what's the use in the new app? Another pointless exercise because Canonical think they know what's best for its users.

---

### Post by taavikko on 2009-08-07
> **phenest said:**
> Users with no ability to learn and those who are willing to learn. Pretty straight forward really.



Just wish to make a corrrection on the first half, even retards are capable of learning.
So it should state something like: "no desire/need to learn" ..?

---

### Post by phenest on 2009-08-07
> **taavikko said:**
> Just wish to make a corrrection on the first half, even retards are capable of learning.
So it should state something like: "no desire/need to learn" ..?

Perhaps, but I don't want to wander from the subject here. Do we really need a replacement for Synaptics? There has been a lot of promises from Canonical over the years that have either been very slow coming or aren't as good as what they were replacing. Will this be another one?

Can someone tell me what is wrong with Synaptics that it requires a replacement?

---

### Post by zekopeko on 2009-08-07
> **phenest said:**
> Perhaps, but I don't want to wander from the subject here. Do we really need a replacement for Synaptics? There has been a lot of promises from Canonical over the years that have either been very slow coming or aren't as good as what they were replacing. Will this be another one?

Can someone tell me what is wrong with Synaptics that it requires a replacement?

Yes, we do need a replacement for Synaptic. I know my way around Ubuntu and I still find Synaptic confusing at times.

Your whole "it's good enough" mentality is off putting. And you are pointing out how users know best but then dismiss those that don't want to spend their afternoon looking at documentation and making the app work.

Creating better UI for users is always a good thing.
I also don't like when people attack other users for being ,in their opinion, ignorant for not mastering a step learning curve.

If you want total control use some other distro. Ubuntu is "for human beings" and contrary to your perception (and others like you) most users aren't tech geeks. I don't see accountants calling you an ignorant person just because you don't know what form to fill. Probably has to do with the whole organic composition of modern societies where people specialize in specific jobs.

In the words of Will Smith in ID4: "Peace"

---

### Post by phenest on 2009-08-07
> **zekopeko said:**
> Yes, we do need a replacement for Synaptic. I know my way around Ubuntu and I still find Synaptic confusing at times.

You haven't explained why.

> **zekopeko said:**
> Your whole "it's good enough" mentality is off putting. And you are pointing out how users know best but then dismiss those that don't want to spend their afternoon looking at documentation and making the app work.

I never said it's good enough. I said that it needed improving, but that we should do that instead of making another one.

> **zekopeko said:**
> Creating better UI for users is always a good thing.
I also don't like when people attack other users for being ,in their opinion, ignorant for not mastering a step learning curve.

Expecting someone to learn something is hardly an attack on their ability.

> **zekopeko said:**
> If you want total control use some other distro.

I'm not after control. I'm offering a viable alternative.

> **zekopeko said:**
> Ubuntu is "for human beings" and contrary to your perception (and others like you) most users aren't tech geeks.

We're all humans, right? If I can do it, why can't everyone else? Unless we've got some monkeys using it.

> **zekopeko said:**
> I don't see accountants calling you an ignorant person just because you don't know what form to fill.

You're right, they don't. But they don't hand you a simpler form to fill in, just because you can't manage the 'hard' one.

> **zekopeko said:**
> Probably has to do with the whole organic composition of modern societies where people specialize in specific jobs.

That's through choice and not ability. And I'm not here to spoon feed someone because they won't do it themselves.

---

### Post by Simian Man on 2009-08-07
Synaptic, the ugly, confusing, jumbled mess that has to be run as root?  Or AppCenter, the vaporware product that will probably take a few years to get working?

How about PackageKit which works beautifully, is easy to use and supports features that Synaptic and AppCenter would never have like allowing developers to request package installations.

Ubuntu snubbing PK reeks of NIH syndrome.

---

### Post by zekopeko on 2009-08-07
> **phenest said:**
> You haven't explained why.

Two searches that report varying selection based on the same query. Forcing a version of multiple packages is a chore. The whole sections stuff is confusing (the buttons in the lower left).
The user interface is package centric while it should be application centric. There are other but those are the ones that popped in my mind.
Read the Appcenter spec. It will bring a better end user experience.


> I never said it's good enough. I said that it needed improving, but that we should do that instead of making another one.

You probably missed the part where it was said that gnome-app-install is going to be used as the base. End even if it's going to be written from scratch it's a decision from the developers and what they think is a better long-term solution.


> 
Expecting someone to learn something is hardly an attack on their ability.

It's how you phrase it. 


> 
I'm not after control. I'm offering a viable alternative.


What viable alternative? It's been discussed that Synaptic isn't a viable platform for Appcenter.

> 
We're all humans, right? If I can do it, why can't everyone else? Unless we've got some monkeys using it.

All humans are not the same. We have the same rights but we don't have same abilities. I can probably do thing that you can't and vice versa.

> You're right, they don't. But they don't hand you a simpler form to fill in, just because you can't manage the 'hard' one.

But they help you fill in the hard one. And don't demand that you know their job.


> 
That's through choice and not ability. And I'm not here to spoon feed someone because they won't do it themselves.

Contrary to your belief people don't need to know what is a package to be able to use a computer. Computers are convenient, just like cars, but I don't go around telling people that they are idiots for not getting a drivers licence.

---

### Post by zekopeko on 2009-08-07
> **Simian Man said:**
> Synaptic, the ugly, confusing, jumbled mess that has to be run as root?  Or AppCenter, the vaporware product that will probably take a few years to get working?

How about PackageKit which works beautifully, is easy to use and supports features that Synaptic and AppCenter would never have like allowing developers to request package installations.

Ubuntu snubbing PK reeks of NIH syndrome.

It was never said that parts of PK couldn't be used. The thing I don't like in PK are the various frontends. Those suck big time.
So I don't see why the PK goodies couldn't be used in Appcenter if mpt and the rest of the developers have time to implement.

---

### Post by phenest on 2009-08-07
> **zekopeko said:**
> Two searches that report varying selection based on the same query. Forcing a version of multiple packages is a chore. The whole sections stuff is confusing (the buttons in the lower left).
The user interface is package centric while it should be application centric. There are other but those are the ones that popped in my mind.
Read the Appcenter spec. It will bring a better end user experience.

Totally agree. So why can't that be changed, if that's all it needs.

> **zekopeko said:**
> You probably missed the part where it was said that gnome-app-install is going to be used as the base. End even if it's going to be written from scratch it's a decision from the developers and what they think is a better long-term solution.

Really good developers ask their user base for their opinion (seeing as they are the end users). After, the end users might also be developers.

> **zekopeko said:**
> What viable alternative? It's been discussed that Synaptic isn't a viable platform for Appcenter.

Not as a platform. Instead of.

> **zekopeko said:**
> All humans are not the same. We have the same rights but we don't have same abilities. I can probably do thing that you can't and vice versa.

Rubbish. The only reason you can do things I can't is because I haven't learnt it, or I have no interest. Nothing to do with ability. It's like when someone says "I can't swim". It's not that you can't, it's just you don't know how.

> **zekopeko said:**
> But they help you fill in the hard one. And don't demand that you know their job.

Which brings me to another point. No one shows you how to use a computer. That may not be an option. But this is where well documented help files are needed, and placed so they are easily available. You don't fix a car without looking at a manual, do you?

> **zekopeko said:**
> Contrary to your belief people don't need to know what is a package to be able to use a computer. Computers are convenient, just like cars, but I don't go around telling people that they are idiots for not getting a drivers licence.

But you would tell them they're an idiot for driving badly.

---

### Post by ronacc on 2009-08-07
everything phenest said plus this , we never said don't develope app-center we said let us see it and have a chance to test and critique it before any decission is made to replace synaptic as default . 
   If the goal of Ubuntu is to cater to those who are unwilling to put forth any effort at all or to make any attempt to learn something new , which you seem to think represents the "average user" , then it will surely fail .It will fail because in the final anyalisis the only way to do that is to remove all possibility of making a wrong choice and all opertunity of doing something unique .

---

### Post by zekopeko on 2009-08-07
> **phenest said:**
> Totally agree. So why can't that be changed, if that's all it needs.

Because that's not all that is needed. It's like putting a band-aid on a bleeding 20cm wound. Fixing smaller stuff is still going to happen for Synaptic, but Synaptic can't deliver what is wanted in it's current form. It was decided that it wasn't resource wise to rewrite Synaptic in the image of Appcenter.

> Really good developers ask their user base for their opinion (seeing as they are the end users). After, the end users might also be developers.

Well then, you will be glad to know that mpt is a "really good developer". User testing was conducted. Critical UI obstructions were observed. Appcenter is aimed at the whole user base but with the simplicity that your grandma could understand. Do you know how many users don't know what a browser is? Let alone a package? Get real here. You are the type of person that is going to dabble with the command line. Your grandma isn't that kind of person.

> 
Not as a platform. Instead of.

I was talking about Synaptic being a prime candidate for major UI re-coding. They don't want to touch it since people like it and it would probably be more work to re-code it to become the app center.

> 
Rubbish. The only reason you can do things I can't is because I haven't learnt it, or I have no interest. Nothing to do with ability. It's like when someone says "I can't swim". It's not that you can't, it's just you don't know how.

We are talking about abilities here. Not skills. But the whole point is that the user shouldn't have to go through 10 hours of swimming school just so that he can play near the pool.

> 
Which brings me to another point. No one shows you how to use a computer. That may not be an option. But this is where well documented help files are needed, and placed so they are easily available. You don't fix a car without looking at a manual, do you?

Users don't look at help files. Users look at the buttons and text and the shiny icons.
By creating a intuitive UI you are going to resolve confusion for 95% of new users. I can be done and it should be done. I hope you've looked at the Appcenter wiki page and saw the mock-ups. Looks kinda like iTunes doesn't it? Guess what, 100's of millions of people manage to use iTunes, even to buy stuff from it without much problem.

> But you would tell them they're an idiot for driving badly.

No, I would tell them that they are driving badly. I wouldn't tell them they are bloody idiots just because they are driving badly.

---

### Post by ronacc on 2009-08-07
> We are talking about abilities here. Not skills. But the whole point is that the user shouldn't have to go through 10 hours of swimming school just so that he can play near the pool. 

oh yeah ? here in Florida where I live there is a law that if you have a pool it must be fenced to prevent children from falling in even if you don't have children .

> Users don't look at help files. Users look at the buttons and text and the shiny icons.
By creating a intuitive UI you are going to resolve confusion for 95% of new users. I can be done and it should be done. I hope you've looked at the Appcenter wiki page and saw the mock-ups. Looks kinda like iTunes doesn't it? Guess what, 100's of millions of people manage to use iTunes, even to buy stuff from it without much problem.

so all we have to do is rename synaptic to program-installer , problem solved .

> Well then, you will be glad to know that mpt is a "really good developer". User testing was conducted. Critical UI obstructions were observed. Appcenter is aimed at the whole user base but with the simplicity that your grandma could understand. Do you know how many users don't know what a browser is? Let alone a package? Get real here. You are the type of person that is going to dabble with the command line. Your grandma isn't that kind of person.

don't make generalizations about us geezers , we may have false teeth but we can still bite .

> No, I would tell them that they are driving badly. I wouldn't tell them they are bloody idiots just because they are driving badly.

I just salute them ( with one finger) .

---

### Post by phenest on 2009-08-07
> **zekopeko said:**
> Because that's not all that is needed. It's like putting a band-aid on a bleeding 20cm wound. Fixing smaller stuff is still going to happen for Synaptic, but Synaptic can't deliver what is wanted in it's current form. It was decided that it wasn't resource wise to rewrite Synaptic in the image of Appcenter.

Then tell me how big the wound is. And I might be able to help with resources.

> **zekopeko said:**
> Well then, you will be glad to know that mpt is a "really good developer". User testing was conducted. Critical UI obstructions were observed. Appcenter is aimed at the whole user base but with the simplicity that your grandma could understand. Do you know how many users don't know what a browser is? Let alone a package? Get real here. You are the type of person that is going to dabble with the command line. Your grandma isn't that kind of person.

User testing was conducted? How? Nothing's been written yet to test. I am the type of user to dabble in the command line. I'm also the type of user who likes to help develop software. And don't patronize my grandma. She already knows how to suck eggs.

> **zekopeko said:**
> I was talking about Synaptic being a prime candidate for major UI re-coding. They don't want to touch it since people like it and it would probably be more work to re-code it to become the app center.

Probably? I think you're guessing. I can see what needs doing, and it wouldn't upset the existing users, whilst gaining the interest of new users.

> **zekopeko said:**
> We are talking about abilities here. Not skills. But the whole point is that the user shouldn't have to go through 10 hours of swimming school just so that he can play near the pool.

You do know you can drown in an inch of water? I think some amount of instruction is necessary.

> **zekopeko said:**
> Users don't look at help files. Users look at the buttons and text and the shiny icons.
By creating a intuitive UI you are going to resolve confusion for 95% of new users. I can be done and it should be done. I hope you've looked at the Appcenter wiki page and saw the mock-ups. Looks kinda like iTunes doesn't it? Guess what, 100's of millions of people manage to use iTunes, even to buy stuff from it without much problem.

Then perhaps the buttons, text, and shiny icons should direct people to help files. And what's iTunes? Pick an analogy that I'm more likely to be familiar with.

> **zekopeko said:**
> No, I would tell them that they are driving badly. I wouldn't tell them they are bloody idiots just because they are driving badly.

Perhaps the controls of a car aren't very intuitive. Or perhaps some drivers need more instruction. I think the latter is more useful to a bad driver.

---

### Post by mpt on 2009-08-07
**Warning:** This setup command uses sudo to update the application index data. Don’t run it unless you understand what it does, and/or you trust Michael Vogt and myself.

```
bzr get https://launchpad.net/~mvo/+junk/app-center && cd app-center/utils && sudo ./update-app-install && cd ../ && ./mpt-center
```

> **ronacc said:**
> one aspect of synaptic that contributes to the look of complexity that synaptic has is that it shows ALL packages that are available in the selected repos (for your arch) , add-remove etc  are very deficient in this .

Indeed. AppCenter 1.0 won’t tackle this, but 2.0 will.

> **seeker5528 said:**
> The question is how to you provide the tools and present them in the UI to deal with additional circumstances where you don't want to treat recommends as dependencies or things are borked for whatever reason?

There are a fair amount of situation/tasks where more functions may be desired.

[I’ve already hinted at]("http://ubuntuforums.org/showpost.php?p=7648666&postcount=80") how we’ll present Recommends and Suggests. For the other things you mentioned, most of them I won’t need to design in detail until 2.0, but the short answer (as you alluded to) is [progressive disclosure]("http://www.useit.com/alertbox/progressive-disclosure.html").

> **phenest said:**
> This mentality that Canonical has of replacing perfectly good software is getting silly. Take the On Screen Notification: What Canonical has replaced it with is less useful and less configurable. You may argue that I could disable it, and use the original, but that would be a stupid thing to suggest. Because if everyone did just that, what's the use in the new app? Another pointless exercise because Canonical think they know what's best for its users.

Oh, you nailed us there. 8-[ I admit it. Ubuntu is for people who have better things to do with their lives than close bubbles or configure notification systems.

> **phenest said:**
> Then tell me how big the wound is. And I might be able to help with resources.

If you want to help out with AppCenter, that would be awesome! On Monday I’ll try to add a list of bite-size tasks (programming, artwork, design, research, *etc*) that people can help with to [the wiki page]("https://wiki.ubuntu.com/AppCenter").

> *User testing was conducted? How? Nothing's been written yet to test.*

The user testing was on the current Add/Remove Applications.

---

### Post by phenest on 2009-08-07
> **mpt said:**
> Oh, you nailed us there. 8-[ I admit it. Ubuntu is for people who have better things to do with their lives than close bubbles or configure notification systems.

Sarcasm is the lowest form of wit, and doesn't gain the respect of anyone.

> **mpt said:**
> The user testing was on the current Add/Remove Applications.

Ah! I only use Synaptic.

---

### Post by ronacc on 2009-08-07
looks good so far , a couple of errors during install and a bunch of debug messages while running , see attached text file .I had to prune out a lot of the debug msgs to get the txt file down to the attach limit for txt files .

---

### Post by qamelian on 2009-08-07
> **mpt said:**
> Oh, you nailed us there. 8-[ I admit it. Ubuntu is for people who have better things to do with their lives than close bubbles or configure notification systems.
As a user of Ubuntu since the release of Warty Warthog, I find this attitude to be both patronizing and insulting. Some of us have better things to do than use tools that have nothing new and worthwhile to offer. If Appcenter filled some kind of genuine need, I could support it. The fact is that it doesn't. If I had any inclination to try it before, your attitude above is enough to ensure that is no longer the case.

---

### Post by ronacc on 2009-08-07
I don't read that as being patronizing , he is admitting that on screen notification was a mistake .Lets see if they learned from the mistake before we get in an uproar . Right now from the sample MPT posted app-center looks like it might turn out alright ,I'll reserve judgment . If it turns out poorly and is still shoved down our throats I will join in the screaming .

---

### Post by zekopeko on 2009-08-07
> **qamelian said:**
> As a user of Ubuntu since the release of Warty Warthog, I find this attitude to be both patronizing and insulting. Some of us have better things to do than use tools that have nothing new and worthwhile to offer. If Appcenter filled some kind of genuine need, I could support it. The fact is that it doesn't. If I had any inclination to try it before, your attitude above is enough to ensure that is no longer the case.

As a user of Ubuntu since Breezy Badger I find your post arrogant and selfish. Just because you can't see the value in what mpt and mvo are doing doesn't mean there is none.
Contrary to your implied belief, Ubuntu wasn't made just for you. This application will help more people by making Ubuntu easy and simple to use. That is it's goal. If you are scared of change there is always going to be the trusty apt-get install synaptic command.
You, as a long time user of Ubuntu, should be aware of Ubuntu's philosophy of one tool to rule them all. It's probably the reason you installed it in the first place. So stop acting like there is some great "injustice" happening if Synaptic is replaced with new software. It's called progress and mpt has researched the path to it in great detail.  

And I ,for one, welcome our new Appcenter overlords.

---

### Post by ronacc on 2009-08-07
@ MPT  I realise that what you posted for us to try above is a very early and incomplete sneak peek and I must say it shows promise . I do have one suggestion right off , you may have this on your "to do" list already but if not please consider it . there should be some indication that an app is already installed when you are looking at the main list for a catagory .

---

### Post by Regenweald on 2009-08-07
> **qamelian said:**
> As a user of Ubuntu since the release of Warty Warthog, I find this attitude to be both patronizing and insulting. Some of us have better things to do than use tools that have nothing new and worthwhile to offer. If Appcenter filled some kind of genuine need, I could support it. The fact is that it doesn't. If I had any inclination to try it before, your attitude above is enough to ensure that is no longer the case.

mpt is using valuable development time to indulge a group of users who, for the most part, are wholly against his and others attempt to genuinely improve the Ubuntu experience. when the devs were taking all manner of distasteful comments and sarcasm where was your righteous indignation ?

As a member of the user base I will say that i value mpt's posts and his willingness to interact with the forum. Sarcasm or not, there is only so much that a HUMAN BEING will accept before responding in kind. I will also say that the quoted text is of no consequence whatsoever. Don't worry, testers will be found, Appcentre will be complete. Hold on to your inclinations.

---

### Post by keypox on 2009-08-07
so does appcenter list all the same programs availible in synaptic, all from software sources repos.

---

### Post by ronacc on 2009-08-07
> **keypox said:**
> so does appcenter list all the same programs availible in synaptic, all from software sources repos.

I raised the same concern and MPT said that it would be addressed in  appcenter 2.0 , the sneak peek he posted the cmd for is already more complete than add remove in this respect .

---

### Post by qamelian on 2009-08-07
> **zekopeko said:**
> As a user of Ubuntu since Breezy Badger I find your post arrogant and selfish. Just because you can't see the value in what mpt and mvo are doing doesn't mean there is none.
Contrary to your implied belief, Ubuntu wasn't made just for you. This application will help more people by making Ubuntu easy and simple to use. That is it's goal. If you are scared of change there is always going to be the trusty apt-get install synaptic command.
You, as a long time user of Ubuntu, should be aware of Ubuntu's philosophy of one tool to rule them all. It's probably the reason you installed it in the first place. So stop acting like there is some great injustice happening if Synaptic is replaced with new software. It's called progress and mpt has researched the path to it in great detail.  

And I ,for one, welcome our new Appcenter overlords.
I don't know where you get off implying that I think Ubuntu was made "just for me". I never implied injustice either, so stop putting words in my mouth. You have a habit of twisting other peoples words to suit you own agenda and this is not the first time you have done it with one of my posts. I expressed my opinion on the topic of this thread and a remark made by mpt. That's it. Frankly, I'm fed up with your habit of twisting other peoples words to suit you own agenda. If you don't respect my right to express my opinions on this forum, add me to your ignore list. I'm certainly adding you to mine.

---

### Post by phenest on 2009-08-08
> **qamelian said:**
> I expressed my opinion on the topic of this thread and a remark made by mpt.

And it amazes me that only 2 of us could that mpt was taking the smeg.

---

### Post by mpt on 2009-08-08
Ladies, calm down, it’s only package management.

> **phenest said:**
> Sarcasm is the lowest form of wit, and doesn't gain the respect of anyone.

I was not being sarcastic at all. I’m sorry that that was unclear.

> **ronacc said:**
> I don't read that as being patronizing , he is admitting that on screen notification was a mistake .

Not at all, I was alluding to two of the benefits of Notify OSD. notification-daemon added yet another item to the Preferences menu; Notify OSD does not. And notification-daemon required you to either close bubbles, or wait for them to close, before clicking anything underneath them; Notify OSD does not.

One of my other tasks this cycle has been [refining the Notify OSD design]("https://wiki.ubuntu.com/NotifyOSD?action=info"), as well as designing compatibility fixes so that KDE applications can use it without putting up a lot of alert boxes. (So KDE 4.3 applications running on Ubuntu 9.10 should be quite a bit more pleasant than the same applications running on Ubuntu 9.04.)

> *Right now from the sample MPT posted app-center looks like it might turn out alright ,I'll reserve judgment . If it turns out poorly and is still shoved down our throats I will join in the screaming .*

Well, um, thanks, I guess? :D

> **ronacc said:**
> @ MPT  I realise that what you posted for us to try above is a very early and incomplete sneak peek and I must say it shows promise . I do have one suggestion right off , you may have this on your "to do" list already but if not please consider it . there should be some indication that an app is already installed when you are looking at the main list for a catagory .

Absolutely. It’s not explained in the spec yet, but [the mockup for the category panel]("https://wiki.ubuntu.com/AppCenter#Category%20panel") shows a green checkmark badge on applications that are currently installed.

---

### Post by zekopeko on 2009-08-08
> **qamelian said:**
> I don't know where you get off implying that I think Ubuntu was made "just for me". I never implied injustice either, so stop putting words in my mouth. You have a habit of twisting other peoples words to suit you own agenda and this is not the first time you have done it with one of my posts. I expressed my opinion on the topic of this thread and a remark made by mpt. That's it. Frankly, I'm fed up with your habit of twisting other peoples words to suit you own agenda. If you don't respect my right to express my opinions on this forum, add me to your ignore list. I'm certainly adding you to mine.

Your whole demeanor implies that you didn't even think for one second that Appcenter could help somebody. Or that, that somebody is worth helping.
I didn't twist your words. 

And you are always welcome to correct me if you believe that's what happened. No to mention that perhaps I misinterpreted your intent.

I also used the words "like there is some great injustice" and was convinced that it would be read as "something not wanted or wrong". You do have idioms/comparisons in Canada right?

And you probably ignored that I have the same right as you to post my opinion about your opinion. And that means disagreeing. I hope I'm in good company on that ignore list.
Cheers.

---

### Post by ronacc on 2009-08-08
> Ladies, calm down, it&#8217;s only package management.

Only package management? I can think of little that is more important .

> Not at all, I was alluding to two of the benefits of Notify OSD 

in that case my apologies to qamelian and phenest , I thought they misunderstood you , I see now that I did .

>  Well, um, thanks, I guess?

I meant I will wait until I get a chance to play with something closer to the final product before I climb on my soapbox and start throwing a fit. If it helps newbes without crippling everone else good , but I am one of the anti "dumb down" crowd so I will judge harshly.

> Absolutely. It&#8217;s not explained in the spec yet, but the mockup for the category panel shows a green checkmark badge on applications that are currently installed. 

I see that now , I missed it when I first looked at the mockup.

---

### Post by qamelian on 2009-08-08
> **ronacc said:**
> in that case my apologies to qamelian and phenest , I thought they misunderstood you , I see now that I did .
No apology required for me. I'm just finding this entire appcenter concept to be frustrating. I genuinely cannot see how it is beneficial to go this route rather than working on fixing what is "wrong" with Synaptic. I haven't seen a single compelling or believeable justification for the existence of this tool. This isn't just my opinion; it is also the opinion of more than two-thirds of the clients I support locally. The remaining third don't care because they essentially use specialized in-house apps and do very little that involves package management, as such. 

I respect the effort that mpt is expending on this, but I truly believe it is misdirected and to say otherwise would make me a hypocrite. For the record, some of the clients I've discussed this with are basic end-users and each and every one of them has expressed a preference for Synaptic over any form of "simpler" tool. It really is time to stop underestimating the abiities of new or less-experienced Linux users. 

Anyway, I've had my say and I won't be tracking this thread any longer. Nothing positive has come of it. The only result has been to a third user to my ignore list. It take a lot to make me put someone on ignore. Peace.

---

### Post by Liolikas on 2009-08-08
Synaptic has long history first version was created for Conectiva Linux more than 10 years ago. It will be hard hit to Linux tradition if Ubuntu will remove it.

---

### Post by zekopeko on 2009-08-08
> **Liolikas said:**
> Synaptic has long history first version was created for Conectiva Linux more than 10 years ago. It will be hard hit to Linux tradition if Ubuntu will remove it.

Removing from default in the future and removing from the repository  are two different things. Synaptic will still be here and will be supported.

---

### Post by Slug71 on 2009-08-08
Has a decision been made on what will be the basis for the add/remove part of this AppCenter yet?

---

### Post by zekopeko on 2009-08-08
> **Slug71 said:**
> Has a decision been made on what will be the basis for the add/remove part of this AppCenter yet?

Gnome-app-install...? Or is this a question about PK (again)? If so, you probably won't see parts of it integrated in the 1.0 version.

---

### Post by Slug71 on 2009-08-08
> **zekopeko said:**
> Gnome-app-install...? Or is this a question about PK (again)? If so, you probably won't see parts of it integrated in the 1.0 version.

Not its not a question about PK again.
Last i heard it was maybe gnome-app-install or PK or ??.

Would just like to know if a decision has been made.

---

### Post by zekopeko on 2009-08-08
> **Slug71 said:**
> Not its not a question about PK again.
Last i heard it was maybe gnome-app-install or PK or ??.

Would just like to know if a decision has been made.

I think that it's going to be a mix of those technologies. PK for mime-type installs (like fonts and codecs) and applications  requesting packages to enable a certain plugin/feature. Everything plugged in Policykit. Stuff like that.

But to answer your question, there isn't a definite decision on what to use. It looks like it's going to be decided on a case by case decision.

---

### Post by 23meg on 2009-08-08
> **phenest said:**
> Users with no ability to learn and those who are willing to learn. Pretty straight forward really.

How about those willing to learn *some* things, but not others (which, mind you, describes just about every user)? Users willing to learn how to install new software, but don't care about what a changelog is and how to download it? Users who are willing to learn how to remove an application they don't use, but don't care about the difference between "removal" and "complete removal"? That black-or-white distinction won't make them very happy.

> **phenest]The whole point of what I and others have being trying to put forward, is that it doesn't require another application. There is already a perfectly good one. The work involved is minimal, because its needs are minimal.[/QUOTE]

Yes, I'm well aware of that. I happen to hold the exact opposite view, and am not going to be convinced by it unless I see a non-blue-sky design specification and preliminary code at least as detailed and convincing as the AppCenter one. Barely asserting something doesn't make it true said:**
> This mentality that Canonical has of replacing perfectly good software is getting silly. Take the On Screen Notification: What Canonical has replaced it with is less useful and less configurable. You may argue that I could disable it, and use the original, but that would be a stupid thing to suggest. Because if everyone did just that, what's the use in the new app? Another pointless exercise because Canonical think they know what's best for its users.

I disagree, and you're entitled to your opinion. We obviously have very different views on what's "perfectly good software".

---

### Post by 23meg on 2009-08-08
> **phenest said:**
> Users with no ability to learn and those who are willing to learn. Pretty straight forward really.

How about those willing to learn *some* things, but not others (which, mind you, describes just about every user)? Users willing to learn how to install new software, but don't care about what a changelog is and how to download it? Users who are willing to learn how to remove an application they don't use, but don't care about the difference between "removal" and "complete removal"? That black-or-white distinction won't make them very happy.

> **phenest]The whole point of what I and others have being trying to put forward, is that it doesn't require another application. There is already a perfectly good one. The work involved is minimal, because its needs are minimal.[/QUOTE]

Yes, I'm well aware of that. I happen to hold the exact opposite view, and am not going to be convinced by yours unless I see a non-blue-sky design specification and preliminary code at least as detailed and convincing as the AppCenter one. Barely asserting something doesn't make it true said:**
> This mentality that Canonical has of replacing perfectly good software is getting silly. Take the On Screen Notification: What Canonical has replaced it with is less useful and less configurable. You may argue that I could disable it, and use the original, but that would be a stupid thing to suggest. Because if everyone did just that, what's the use in the new app? Another pointless exercise because Canonical think they know what's best for its users.

I disagree, and you're entitled to your opinion. We obviously have very different views on what's "perfectly good software".

---

### Post by 67GTA on 2009-08-08
I applaud the effort to make the package management environment better. My main concern is that the new appcenter doesn't dumb things down too much like add/remove does. Not all packages are shown in add/remove. A simple example is gedit-plugins. You can find gedit in add/remove, but not gedit-plugins. Synaptic shows every package tied to gedit like gedit-plugins. As long as this can be addressed before Synaptic is axed, I'm all for it. Are there any plans to address this? Also, if gdebi is removed, will clicking on a .deb file just launch appcenter? Lastly, I read on the wiki that appcenter would handle package conflicts. Currently, add/remove wants you to call synaptic to handle these. What is the plan to address this? The conflict resolution in yast is horrible and confusing.

---

### Post by mpt on 2009-08-09
> **ronacc said:**
> Only package management? I can think of little that is more important .

It depends who’s judging the importance. For end users, setting up Ubuntu in the first place, changing their background picture, connecting to the Internet, searching the Web, watching videos on YouTube, using Facebook, using Wikipedia, playing music, and backing up their stuff are examples of things that are almost certainly more important to more people than package management is. (Whenever anything in software is referred to as a “manager”, it’s usually dreadfully boring.)

For developers, meanwhile, getting their software available to Ubuntu’s user base is tremendously important, and making software easy to install is an important part of that — but only a small part. We also need to tackle the difficulty of developing software in the first place, the difficulty of getting it packaged, and the difficulty of getting packages into a repository where Ubuntu users will see them (preferably without first having to wait for months, and then upgrade their entire Ubuntu installation, before the application is even offered to them).

> *I meant I will wait until I get a chance to play with something closer to the final product before I climb on my soapbox and start throwing a fit. If it helps newbes without crippling everone else good , but I am one of the anti "dumb down" crowd so I will judge harshly.*

Making software work for more people requires smartening it up, not dumbing it down.

> **qamelian said:**
> I'm just finding this entire appcenter concept to be frustrating. I genuinely cannot see how it is beneficial to go this route rather than working on fixing what is "wrong" with Synaptic. I haven't seen a single compelling or believeable justification for the existence of this tool. This isn't just my opinion; it is also the opinion of more than two-thirds of the clients I support locally.

In May I presented Michael Vogt with a rough map of the features we wanted to be implemented five months later, eleven months later, and seventeen months later. I gave him a few weeks to choose the base he thought would be best for developing what we wanted. He chose gnome-app-install. He is quite probably the best person on the planet to make that decision, so I believe him. End of story.

> **Liolikas said:**
> Synaptic has long history first version was created for Conectiva Linux more than 10 years ago. It will be hard hit to Linux tradition if Ubuntu will remove it.

And Canonical employs both Gustavo Niemeyer, who worked on it in those early days at Conectiva, and Michael Vogt, who has maintained it for years. But that’s not important either.

> **23meg said:**
> How about those willing to learn *some* things, but not others (which, mind you, describes just about every user)? Users willing to learn how to install new software, but don't care about what a changelog is and how to download it? Users who are willing to learn how to remove an application they don't use, but don't care about the difference between "removal" and "complete removal"? That black-or-white distinction won't make them very happy.

Welcome to the [perpetual intermediate]("http://www.codinghorror.com/blog/archives/000098.html").

> **67GTA said:**
> I applaud the effort to make the package management environment better. My main concern is that the new appcenter doesn't dumb things down too much like add/remove does. Not all packages are shown in add/remove. A simple example is gedit-plugins. You can find gedit in add/remove, but not gedit-plugins. Synaptic shows every package tied to gedit like gedit-plugins. As long as this can be addressed before Synaptic is axed, I'm all for it. Are there any plans to address this?

Yes. For more details, see the spec, or read this forum thread.

> *Also, if gdebi is removed, will clicking on a .deb file just launch appcenter?*

Yes, my current plan is that it will open to display that package mostly the same way as it displays other packages. The only visible differences will be for the purpose of conveying the risk involved.

> *Lastly, I read on the wiki that appcenter would handle package conflicts. Currently, add/remove wants you to call synaptic to handle these. What is the plan to address this? The conflict resolution in yast is horrible and confusing.*

Thats something I probably won’t be concerned with until after 9.10. But if you want to help, you could start compiling a list on the wiki of the various types of package conflict, with screenshots of how Synaptic currently presents them, so I can redesign them as a whole later. Thanks!

---

### Post by qamelian on 2009-08-09
> **mpt said:**
> In May I presented Michael Vogt with a rough map of the features we wanted to be implemented five months later, eleven months later, and seventeen months later. I gave him a few weeks to choose the base he thought would be best for developing what we wanted. He chose gnome-app-install. He is quite probably the best person on the planet to make that decision, so I believe him. End of story.
Fair enough, but as an end-user, I know what I expect and want from an application and nothing I've heard so far convinces me that appcenter is it. End of story. 

If appcenter will allow me to do everything ( and I mean *everything*!) that synaptic does, then I'll shut up. Otherwise, I have no intention of using it. If it fails to meet the needs of me and my clients, and if Synaptic goes the way of the dodo in Ubuntu, I'll simply move to another distro that does and I'll migrate my clients with me. 

Appcenter is fine for those who want it. Neither I, nor the clients who provide my income, do.

---

### Post by Slug71 on 2009-08-09
From what i get from this thread and i DO agree is that, Canonical has this thing going 'for human beings' yet they do what they think is best for its users and not listen to what the users(human beings) want. It also seems they are trying to focus on new users, which may not stick around for what ever reasons, more than the users that have been around for a long time and have helped in various ways to make/get Ubuntu where it is today.

Lets just hope this software will live up to what it is suppose to be/do. Or we may just see 9.04 being the best Ubuntu release ever.

---

### Post by zekopeko on 2009-08-09
> **qamelian said:**
> Fair enough, but as an end-user, I know what I expect and want from an application and nothing I've heard so far convinces me that appcenter is it. End of story. 

If appcenter will allow me to do everything ( and I mean *everything*!) that synaptic does, then I'll shut up. Otherwise, I have no intention of using it. If it fails to meet the needs of me and my clients, and if Synaptic goes the way of the dodo in Ubuntu, I'll simply move to another distro that does and I'll migrate my clients with me. 

Appcenter is fine for those who want it. Neither I, nor the clients who provide my income, do.

See this are the type of posts that I generally don't agree with.

Here is the freaking link to the spec: [https://wiki.ubuntu.com/AppCenter](https://wiki.ubuntu.com/AppCenter)

Now how hard is it to "read between the lines" that "In Ubuntu 10.04, replace Synaptic, Software Sources, Gdebi, and (if appropriate) Update Manager with an expanded AppCenter" means migration of functionality of said apps into AppCenter?

Then again qamelian (to my knowledge) hasn't inquired about any potential regression he fears, justifiably so, might hurt his income?
Question like: is synaptic going to remain in main and thereby be supported by Canonical? How do you plan to integrated feature X from synaptic?

And let us not forget that mpt is paid by Canonical and Canonical sells support and other services based around Ubuntu, so one would think that mpt is taking into account any feature regression that might hurt Canonicals customers.

---

### Post by zekopeko on 2009-08-09
> **Slug71 said:**
> From what i get from this thread and i DO agree is that, Canonical has this thing going 'for human beings' yet they do what they think is best for its users and not listen to what the users(human beings) want. It also seems they are trying to focus on new users, which may not stick around for what ever reasons, more than the users that have been around for a long time and have helped in various ways to make/get Ubuntu where it is today.

Lets just hope this software will live up to what it is suppose to be/do. Or we may just see 9.04 being the best Ubuntu release ever.

Slug71, what do YOU want? What do you want from Ubuntu? What are your requirements to make Ubuntu the best distro for you?

---

### Post by Slug71 on 2009-08-09
> **zekopeko said:**
> Slug71, what do YOU want? What do you want from Ubuntu? What are your requirements to make Ubuntu the best distro for you?

zekopeko, it was just a generalization from what i have picked up by this thread and various others about software not being made by default, dropped or being replaced or even just not being looked at.

Two big examples would be Plymouth and the On Screen Notification.

---

### Post by zekopeko on 2009-08-09
> **Slug71 said:**
> zekopeko, it was just a generalization from what i have picked up by this thread and various others about software not being made by default, dropped or being replaced or even just not being looked at.

Two big examples would be Plymouth and the On Screen Notification.

Let me rephrase the question: What do you want to be able to do with your computer? What action do you want to be able to preform? Things like: read my e-mail, watch youtube etc.

Why should Plymouth be included in Ubuntu?
And what is wrong with OSD notifications?

---

### Post by scaine on 2009-08-09
> **Slug71 said:**
> zekopeko, it was just a generalization from what i have picked up by this thread and various others about software not being made by default, dropped or being replaced or even just not being looked at.

Two big examples would be Plymouth and the On Screen Notification.


It's a bit harsh to pick on Canonical for this though, when Gnome devs have taken this attitude for the past 6 years or so.  Gnome-Screensaver?  Gnome-Chat?  Both examples of frankly horribly crippled apps replacing far "better" ones (x-screensaver and xchat).  And this EXACT argument is ongoing in the Pidgin vrs Empathy thread.

I'm sick of arguing these decisions anymore.  If you don't like default decisions, by all means make your voice heard, but you're absolutely free and welcome to use the old apps if it pleases you to do so.

My only concern about AppCenter (appart from the terrible spelling :)) is that it's not based on packagekit.  Everyone commenting on this thread seems to know the history of this decision, but I don't.  I'm off to do some research (and install packagekit to see what it's all about).

---

### Post by jppr on 2009-08-09
i think that all-in-one system is best :popcorn:

---

### Post by 23meg on 2009-08-09
> **Slug71 said:**
> From what i get from this thread and i DO agree is that, Canonical has this thing going 'for human beings' yet they do what they think is best for its users and not listen to what the users(human beings) want. It also seems they are trying to focus on new users, which may not stick around for what ever reasons, more than the users that have been around for a long time and have helped in various ways to make/get Ubuntu where it is today.

Lets just hope this software will live up to what it is suppose to be/do. Or we may just see 9.04 being the best Ubuntu release ever.

"Listening to" a group of people (usually referred to as a mythical homogeneous entity called "the users" in the context of software) does not necessarily have to mean agreeing with their every opinion (as if they agreed on everything amongst themselves) and having to cater for every nuance of their every need and demand (as if their needs and demands were never in conflict). Plenty of "listening" has been done on AppCenter, as well as the other examples you've cited, through online discourse (exemplified in this very thread) and user testing. And doing what you think is best for your users is not a sin. Please, pretty please, stop talking about it as if it were. Quite the contrary: it means you have some kind of an idea about how to do reasonably well at satisfying the needs of the majority of your users, and that you're passionate about realizing that idea. It doesn't have to mean being a dictator, or assuming things on behalf of people you whose needs and demands you have no idea about. It just comes down to how good that idea is, and how well you pull it off.

People who have an observable habit of crying foul (such as throwing the "does not listen to its users" error) whenever they don't like a certain decision or direction being taken are fair-weather friends of Ubuntu and FOSS. I have higher expectations of experienced Ubuntu users: I subscribe to the unpopular opinion that they should be willing to at least partially tolerate the decisions that may inconvenience them in the short run, if the tradeoff is doing tremendously better at meeting the needs of a very large group of users, actual or latent, that are disadvantaged by the norms that they have gotten used to. That's expectable, because they can be assumed to be much more capable at amending things when the distribution doesn't cater for their needs by default than inexperienced non-technical users. As a simple example, if AppCenter doesn't suit their needs at first, they should be willing to apt-get Synaptic and remove it, rather than demanding that the whole world stick with Synaptic.

Don't be a fair-weather friend. At times like this, it's a good idea to remind yourself of what the word "ubuntu" means, and think for a second if you can "grin and bear it", and still stick with Ubuntu, maybe at the cost of doing a simple modification for your clients, like replacing UnpopularSoftwareManagementTool with Synaptic, or at the cost of a feature you liked being unavailable for one release cycle, or at the cost of suffering whatever slight to moderate inconvenience that may be at hand. Of course, there's only so much you can take, and of course it would be silly to call people to cling to a piece of software that consistently makes them suffer; that's not what I'm talking about. I'm talking about just a little bit more willingness to tolerate things, while at the same time trying to improve them, when they don't exactly work for you. 

There's a rant for you. Back to work.

---

### Post by DeadSuperHero on 2009-08-09
If Canonical could turn the AppCenter concept into something like Bodega for Linux, I'd be all for it.

One of the most valuable assets of Bodega in my opinion is that developers can submit their apps for inclusion, and can choose to make a profit off of selling their apps directly to users.

This could be so beneficial in cultivating a generation of commercial developers specifically looking to code for the Linux platform.

---

### Post by zekopeko on 2009-08-09
> **Mr. Psychopath said:**
> If Canonical could turn the AppCenter concept into something like Bodega for Linux, I'd be all for it.

One of the most valuable assets of Bodega in my opinion is that developers can submit their apps for inclusion, and can choose to make a profit off of selling their apps directly to users.

This could be so beneficial in cultivating a generation of commercial developers specifically looking to code for the Linux platform.

Whoa didn't even know about Bodega. Nice looking app, but what's with the tent in the interface?!

---

### Post by wayne_cat on 2009-08-09
> **zekopeko said:**
> Whoa didn't even know about Bodega. Nice looking app, but what's with the tent in the interface?!

Just installed it on my Mac ... the "tent" is really a part of the GUI ... ridiculous

---

### Post by DeadSuperHero on 2009-08-09
It's not the tent part that is the important aspect to me, but the idea:

  Third Party developers can submit their app to be open or closed source, for monetary gain or for free. If this could be implemented for Ubuntu, I think it could do so many great things for people that are budding game developers on the Linux platform. It really would open up a whole can of worms for the entire Ubuntu ecosystem when you think about it.

And we could design ours without a tent interface! Ha!

---

### Post by Slug71 on 2009-08-10
> **Mr. Psychopath said:**
> It's not the tent part that is the important aspect to me, but the idea:

  Third Party developers can submit their app to be open or closed source, for monetary gain or for free. If this could be implemented for Ubuntu, I think it could do so many great things for people that are budding game developers on the Linux platform. It really would open up a whole can of worms for the entire Ubuntu ecosystem when you think about it.

And we could design ours without a tent interface! Ha!


And it could call on PK to update/install packages.:P

---

### Post by 23meg on 2009-08-10
> **scaine said:**
> It's a bit harsh to pick on Canonical for this though, when Gnome devs have taken this attitude for the past 6 years or so.  Gnome-Screensaver?  Gnome-Chat?  Both examples of frankly horribly crippled apps replacing far "better" ones (x-screensaver and xchat).  And this EXACT argument is ongoing in the Pidgin vrs Empathy thread.

GnomeScreensaver didn't "replace" anything. GNOME had no screen blanking  facility before it, and had a power management infrastructure, if you can call it that, that was managed all over the place, effectively and partially by an alien app called XScreenSaver. The introduction of gnome-power-manager and GnomeScreensaver tidied up that mess, and it was [stated quite explicitly]("http://bugzilla.gnome.org/show_bug.cgi?id=316654#c48") that GnomeScreensaver didn't aim at making screensavers unconfigurable, but at getting rid of the *obligation* to configure them.

As for GNOME-Xchat, that's an even worse example, since it's not just that has XChat never been part of GNOME, but GNOME-XChat has never been, and probably was never intended to be either :) Just because something has "GNOME" in its name, and/or has a page on live.gnome.org doesn't mean it's part of any of the official GNOME release sets.

This "Something looks simpler than it used to, and you don't like that? Blame GNOME!" attitude is getting old. Please, get over it. It's going to help us all a lot. Just to get it out of the way: I'm not saying "Don't criticize GNOME"; it's more like "Don't perpetuate myths about projects you're not familiar with" and "If you set out to criticize something, try to get your facts right".

---

### Post by scaine on 2009-08-10
> **23meg said:**
> GnomeScreensaver didn't "replace" anything. GNOME had no screen blanking  facility before it, and had a power management infrastructure, if you can call it that, that was managed all over the place, effectively and partially by an alien app called XScreenSaver. The introduction of gnome-power-manager and GnomeScreensaver tidied up that mess, and it was [stated quite explicitly]("http://bugzilla.gnome.org/show_bug.cgi?id=316654#c48") that GnomeScreensaver didn't aim at making screensavers unconfigurable, but at getting rid of the *obligation* to configure them.

As for GNOME-Xchat, that's an even worse example, since it's not just that has XChat never been part of GNOME, but GNOME-XChat has never been, and probably was never intended to be either :) Just because something has "GNOME" in its name, and/or has a page on live.gnome.org doesn't mean it's part of any of the official GNOME release sets.

This "Something looks simpler than it used to, and you don't like that? Blame GNOME!" attitude is getting old. Please, get over it. It's going to help us all a lot. Just to get it out of the way: I'm not saying "Don't criticize GNOME"; it's more like "Don't perpetuate myths about projects you're not familiar with" and "If you set out to criticize something, try to get your facts right".

Wow, I thought I was kind of taking your side in this and you shot me down!  :P

Back then, and it was about 4 years ago remember, I was fairly new to both Gnome and Ubuntu and fully admit that I didn't understand the boundaries.  No, "Gnome" didn't have a screensaver, but "Ubuntu" did and while it had issues, it did at least let you configure a screensaver.  I put "better" in quotes for a reason.  I know full well that Gnome had to implement gnome-screensaver over x-screensaver because, for example, x-screensaver didn't know that you were playing a movie and shouldn't kick in.  But gnome-screensaver still rankles because it effectively prevented me from using screensavers in Gnome/Ubuntu and still does to this day, around 4 years later.  Well, not strictly true, since I use "blank screen".  But you don't have to configure that, so no worries.  So as far as gnome-screensaver is concerned, I'm afraid I do "blame GNOME" and feel vindicated to do so.

Xchat was a poor example technically, but still illustrates the furore that's inevitably kicked up whenever any app replaces another as the default, so I felt it was worth mentioning in the context of this thread.

But to address the general gist of your reply, I'm afraid that my (much reduced) antagonism towards the gnome decision making process will continue until I see less "my way or the highway" attitudes in the bug trackers.  The approach of the dev responsible for gnome-screensaver was abhorrent - extremely defensive, arrogant and negative, resulting in a lot of anger from a lot of people.  I've mentioned before that the thread on these very forums about it ran to hundreds of posts, mostly involving outrage.

Over a screensaver of all things.  It's not like we took away people's ability to press CTRL-ALT-BACKSPACE, is it?  Sorry, couldn't resist.  (and jeez, I know it was the xorg developers and I fully supported their decision to do so, despite being against it intially)

So, my approach these days is more laid back.  Grin and bear it, like you suggested in your previous, excellent post and sigh indulgently when another dev decides that he/she knows best.  Often they do.  Sometimes they don't.  But if you don't like it, you're always welcome to go elsewhere, use a different app, or even do something about it directly (and I don't mean rant in the forums).  That's why I've stuck with Linux and specifically Ubuntu all these years.

Despite questioning their decisions at times, I owe these people, and the few bug reports I put in from time to time is scant payback.

---

### Post by 23meg on 2009-08-10
> **scaine said:**
> Wow, I thought I was kind of taking your side in this and you shot me down!  :P

I thought I shot your examples down, not *you*. I don't care about who is on what "side"; I care about the arguments themselves.

> **scaine]Xchat was a poor example technically, but still illustrates the furore that's inevitably kicked up whenever any app replaces another as the default, so I felt it was worth mentioning in the context of this thread.[/QUOTE]

And my point was that nothing "replaced" anything. Some people developed a new app based on the XChat core. That doesn't destroy XChat, or make it any less available. 

In an entirely unrelated episode, XChat-GNOME was briefly included in place of  XChat in the default Ubuntu installation during the Dapper *development cycle*, and shortly afterwards, it was replaced by Gaim. Note that it didn't ship in an actual release said:**
> But to address the general gist of your reply, I'm afraid that my (much reduced) antagonism towards the gnome decision making process will continue until I see less "my way or the highway" attitudes in the bug trackers.  The approach of the dev responsible for gnome-screensaver was abhorrent - extremely defensive, arrogant and negative, resulting in a lot of anger from a lot of people.

I don't think an attitude clarified with an apology [like this]("http://bugzilla.gnome.org/show_bug.cgi?id=316654#c48") qualifies as "my way or the highway". You're of course entitled to think it does, in which case we'll have to agree to disagree.

[QUOTE=scaine]I've mentioned before that the thread on these very forums about it ran to hundreds of posts, mostly involving outrage.[/QUOTE]

Misdirected outrage, as usual, to which I replied with a post along the same lines as my last one in this thread. The myth *was* debunked three years ago, but that obviously didn't keep people from perpetuating it as if it were fact.

[QUOTE=scaine]So, my approach these days is more laid back.  Grin and bear it, like you suggested in your previous, excellent post and sigh indulgently when another dev decides that he/she knows best.  Often they do.  Sometimes they don't.  But if you don't like it, you're always welcome to go elsewhere, use a different app, or even do something about it directly (and I don't mean rant in the forums).  That's why I've stuck with Linux and specifically Ubuntu all these years.

Despite questioning their decisions at times, I owe these people, and the few bug reports I put in from time to time is scant payback.[/QUOTE]

I can only top that sentiment by typing [http://ometer.com/features.html](http://ometer.com/features.html) from memory :)

---

### Post by mpt on 2009-08-10
> **Mr. Psychopath said:**
> Third Party developers can submit their app to be open or closed source, for monetary gain or for free. If this could be implemented for Ubuntu, I think it could do so many great things for people that are budding game developers on the Linux platform. It really would open up a whole can of worms for the entire Ubuntu ecosystem when you think about it.

Ubuntu 10.10.

> **scaine said:**
> Back then, and it was about 4 years ago remember, I was fairly new to both Gnome and Ubuntu and fully admit that I didn't understand the boundaries.  No, "Gnome" didn't have a screensaver, but "Ubuntu" did and while it had issues, it did at least let you configure a screensaver.  I put "better" in quotes for a reason.  I know full well that Gnome had to implement gnome-screensaver over x-screensaver because, for example, x-screensaver didn't know that you were playing a movie and shouldn't kick in.  But gnome-screensaver still rankles because it effectively prevented me from using screensavers in Gnome/Ubuntu and still does to this day, around 4 years later.

It rankles me too, because my sister uses a screensaver with custom rotating text in Windows, and worked out how to do that all by herself, but it’s practically impossible to do the same in Ubuntu. (The “GLText” screensaver is pretty useless if you can’t specify what text it uses.)

I had a chat about this with Jon McCann at the Gran Canaria summit. He reiterated that it’s not that he doesn’t want screensavers to be configurable, but that no-one has implemented a standard way of exposing their options in a declarative way that gnome-screensaver could use. He doesn’t have time to do it, and no-one else has bothered to do the work.

---

### Post by scaine on 2009-08-11
> **mpt said:**
> 
It rankles me too, because my sister uses a screensaver with custom rotating text in Windows, and worked out how to do that all by herself, but it&#8217;s practically impossible to do the same in Ubuntu. (The &#8220;GLText&#8221; screensaver is pretty useless if you can&#8217;t specify what text it uses.)

Or rss feed screensavers that can't be changed from default.  Or most of the screensavers that throw my EEE701 cpu into top gear.  Or. or. or.  Pretty annoying.

> **mpt said:**
> 
I had a chat about this with Jon McCann at the Gran Canaria summit. He reiterated that it&#8217;s not that he doesn&#8217;t want screensavers to be configurable, but that no-one has implemented a standard way of exposing their options in a declarative way that gnome-screensaver could use. He doesn&#8217;t have time to do it, and no-one else has bothered to do the work.

I'd like to hear what Jon is like, as a person, because he comes over so negatively in the articles the net spews out regarding gnome-screensaver.

@23Meg - thanks for pointing me to the apology on bugzilla, but for me, it was pressured, which devalues it (although it appeared to be honestly written), and I can't see past the resolute stand he takes on this issue.  Sadly, having crippled other people's work (in gnome only of course), he [claims that he doesn't have the answers]("http://live.gnome.org/GnomeScreensaver/FrequentlyAskedQuestions#head-64ef29e28226e09a3b849d8f00726cc004625c62"), which is fair enough, nor the time to work on it, also fair enough.  But what surprises me is that gnome-screensaver was implemented anyway!  I know it's for the best, now that we get the dbus stuff and better power integration, but this has been outstanding for quite a few years now.  I'd love it if someone picked up on it.

Still, I found this on that thread you posted 23Meg : [http://software.xfx.net/utilities/sss/index.htm](http://software.xfx.net/utilities/sss/index.htm).  Who knows?  I'll give it a shot.  This *is* a test box after all.

[Edit : Shame - that replacement tool was last updated in mid 2008 and certainly doesn't work on Karmic.  Perhaps that's vindication for Jon McCann - no one really does care about screensavers any more!]

---

