---
title: "New Firefox Add-on"
date: 2009-07-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ghindo on 2009-07-21
I can't find the changelog, but it looks like the latest round of updates installs a new Firefox add-on ("Multisearch") which causes every new tab to display the "Ubuntu Start Page" (see attached).

Thoughts?

**EDIT:**  Additionally, it looks like it's altered the way Google searches are conducted.  See for yourself.

---

### Post by mattduckman on 2009-07-21
here's the changelog, it's not very informative though

```
firefox-3.0 (3.0.11+build2+nobinonly-0ubuntu2.me001) karmic; urgency=low

  * add me001 multisearch feature for karmic alpha3
    - add debian/extensions/*

```

I'm not sure about Ubuntu's goal for the custom search is though. Branding maybe?

---

### Post by ghindo on 2009-07-21
> **mattduckman said:**
> I'm not sure about Ubuntu's goal for the custom search is though. Branding maybe?Not sure.  It looks like when you do a Google search through the toolbar in Firefox, there are some differences than if you were to do a normal Google search.

As we can see from the below images, the Google services (Gmail, Google Docs, etc.) at the top have been removed, along with "advanced search" options.  Not only that, but it looks like ads have a bit more space at the top of the page.  You also can't switch between Web Search, Image Search, Video Search, etc..

---

### Post by ronacc on 2009-07-21
you can disable multisearch and ubuntu firefox modifications .

---

### Post by wipeout140 on 2009-07-22
> **ghindo said:**
> Not sure.  It looks like when you do a Google search through the toolbar in Firefox, there are some differences than if you were to do a normal Google search.

As we can see from the below images, the Google services (Gmail, Google Docs, etc.) at the top have been removed, along with "advanced search" options.  Not only that, but it looks like ads have a bit more space at the top of the page.  You also can't switch between Web Search, Image Search, Video Search, etc..

Reason is:

One is a default Google search page
Second one is a Google Custom Search Page

---

### Post by Wise Ferret on 2009-07-22
Anybody knows how to disable this unaesthetic multisearch thing?
Disabling Ubuntu Firefox Extentions doesn't help, and there is nothing about "multisrarch" in about:config.

---

### Post by ronacc on 2009-07-22
it showed in tools>add-ons for me I just selected "disable"

---

### Post by MacUntu on 2009-07-22
"9.10 Alpha 3 Experiment B"

Maybe they just tested if we would notice such a change. :D

---

### Post by mudi on 2009-07-22
Uggh, this is exactly why I don't use Linux Mint, I hated the fact that they installed a revenue-generating "Custom Search" by default.  ](*,)

---

### Post by yoasif on 2009-07-22
This is a horrible change -- I went over to [Mycroft]("http://mycroft.mozdev.org/google-search-plugins.html") and installed a new search plugin before I tried to disable the plugin.

---

### Post by Starks on 2009-07-22
So...

What is the point of this addon?

---

### Post by wayne_cat on 2009-07-22
press ctrl+t to open a new tab ... instead of a blank page ... a google search page

---

### Post by plun on 2009-07-22
> **wayne_cat said:**
> press ctrl+t to open a new tab ... instead of a blank page ... a google search page

Well. that's magic...:D

---

### Post by nwadams on 2009-07-22
how do we change the addon or firefox itself so that whenever we open a new tab it goes to our homepage.

---

### Post by ronacc on 2009-07-22
black magic !

---

### Post by ghindo on 2009-07-22
> **Starks said:**
> So...

What is the point of this addon?Branding?  Generate revenue?  Not too sure.

---

### Post by wayne_cat on 2009-07-22
good job Ubuntu ... Multisearch and  Modifications are the only add-ons that I can not
remove ... I don't want this rubbish!

---

### Post by nwadams on 2009-07-22
but this is why they brought it in now. so it can be tested. If the overwhelming opinion is that it is terrible then it will be removed for the final release.

---

### Post by wayne_cat on 2009-07-22
finished my tests ... useless add-ons ... so I was forced to remove firefox (apt-get remove).

Firefox *v3.5.1 from Mozilla.org fixed my problem.*

---

### Post by Starks on 2009-07-22
Is this addon going to be Canonical's response to not being allowed to modify Firefox directly?

---

### Post by zekopeko on 2009-07-22
You do realize that you are using a development release, right? Testing for feedback should be implied. But it would be nice to know for what reason was it installed.

@wayne_cat
What were you testing?

@Starks
IIRC the official Ubuntu Firefox has some 10000+ LOC diff compared to official Mozilla release. So they can modify Mozilla's release and retain the branding as long as they provide a quality product approved by Mozilla.

---

### Post by wayne_cat on 2009-07-22
> **zekopeko said:**
> 
@wayne_cat
What were you testing?


My test was: "Is Firefox from the Ubuntu repository still usable with these add-ons".

My result "No ... this is not firefox ... this is googlefox"

:(

---

### Post by Starks on 2009-07-22
> **zekopeko said:**
> 
@Starks
IIRC the official Ubuntu Firefox has some 10000+ LOC diff compared to official Mozilla release. So they can modify Mozilla's release and retain the branding as long as they provide a quality product approved by Mozilla.
If that's the case, why is the Debian team so butt-hurt about the Mozilla license?

Also why does the addon even need to be an addon? Can't the behavior be duplicated in about:config or coded in?

---

### Post by zekopeko on 2009-07-22
> **Starks said:**
> If that's the case, why is the Debian team so butt-hurt about the Mozilla license?

Debian didn't like the trademark/branding thing. Don't remember the details but that was the whole point. Branding wasn't free by Debian's standard.
The point is that you can call something Mozilla Firefox only if it came from Mozilla and with their approval and branding. Ubuntu has a special deal with Mozilla that allows them to modify code and still call it Mozilla Firefox. But it has to meet Mozilla's quality standards.

> Also why does the addon even need to be an addon? Can't the behavior be duplicated in about:config or coded in?

Because it's a smaller download as an addon, if you have to update it then, if it's integrated in the FF code base (few KB vs. few MB)?

---

### Post by zekopeko on 2009-07-22
> **wayne_cat said:**
> My test was: "Is Firefox from the Ubuntu repository still usable with these add-ons".

My result "No ... this is not firefox ... this is googlefox"

:(

Ahhh, ok. Just don't forget NOT to report bug on the version downloaded from Mozilla.

---

### Post by BobCFC on 2009-07-22
This is ridiculous 

How am I supposed to search for images? :confused:


I want about:blank when I open a new tab too

---

### Post by Mutiny32 on 2009-07-22
I sure as hell noticed the three large advertisements added to the top of every search while at the same time removing the links for searching images, shopping, maps, etc...

The only thing I see that this add-on does is add three ads to each search. Is Canonical trying to squeeze revenue out of the use of Firefox?

---

### Post by wayne_cat on 2009-07-22
> **zekopeko said:**
> Ahhh, ok. Just don't forget NOT to report bug on the version downloaded from Mozilla.

I will use bugzilla.mozilla.org (the support page for the browser that does not bend over for Google page impresions).

---

### Post by Mutiny32 on 2009-07-22
Is this a proof of concept for something better, or is this it?

---

### Post by Starks on 2009-07-22
> **Mutiny32 said:**
> Is this a proof of concept for something better, or is this it?
No this is it.

We're gonna have to take it up the rear for Karmic unless we get this voted out through  angry bug reports.

---

### Post by Mutiny32 on 2009-07-22
> **Starks said:**
> No this is it.

We're gonna have to take it up the rear for Karmic unless we get this voted out through  angry bug reports.

Well, I submitted it to reddit and Digg. That's better than a bug report. I'm fine with Canonical trying to make some revenue, but not with a force-installed browser search hijacker that uselessly loads a page in a new tab, changes the search box, and removes search functions while showing me more ads.

---

### Post by Starks on 2009-07-22
> **Mutiny32 said:**
> Well, I submitted it to reddit. That's better than a bug report.
And you didn't post the link...

<__<

---

### Post by Mutiny32 on 2009-07-22
> **Starks said:**
> And you didn't post the link...

<__<

I posted wild accusations. Well, not really. Just what it actually does. I'd really like someone to prove me wrong though, because if it walks like a duck and swims like a duck and quacks like a duck...

[http://www.reddit.com/r/linux/comments/93nlq/new_ff_extension_in_karmic_alpha_3_redirects/]("http://www.reddit.com/r/linux/comments/93nlq/new_ff_extension_in_karmic_alpha_3_redirects/")

---

### Post by Starks on 2009-07-22
I prefer this link...

[http://www.reddit.com/r/linux/comments/93nlq/new_ff_extension_in_karmic_alpha_3_redirects/](http://www.reddit.com/r/linux/comments/93nlq/new_ff_extension_in_karmic_alpha_3_redirects/)

---

### Post by Mutiny32 on 2009-07-22
> **Starks said:**
> I prefer this link...

[http://www.reddit.com/r/linux/comments/93nlq/new_ff_extension_in_karmic_alpha_3_redirects/](http://www.reddit.com/r/linux/comments/93nlq/new_ff_extension_in_karmic_alpha_3_redirects/)

D'oh, I didn't even check it. Thanks.

---

### Post by shakaran on 2009-07-22
See my bug report:
[https://bugs.launchpad.net/bugs/402804](https://bugs.launchpad.net/bugs/402804)

---

### Post by redDEADresolve on 2009-07-22
> **mudi said:**
> Uggh, this is exactly why I don't use Linux Mint, I hated the fact that they installed a revenue-generating "Custom Search" by default.  ](*,)

I like my Firefox vanilla too. Trying to generate revue by screwing with my Google search results is a great way to lose me as a user.

---

### Post by buzzmandt on 2009-07-22
what the H^%L are they thinking taking away the images, videos, maps, etc links.  Those are so handy.  I use them all the time.

---

### Post by budluva04 on 2009-07-22
Tools>Add-ons>Multisearch DISABLE

seems pretty hard to do eh guys/gals?

---

### Post by Mutiny32 on 2009-07-23
> **budluva04 said:**
> Tools>Add-ons>Multisearch DISABLE

seems pretty hard to do eh guys/gals?

It's more a question of motive.

---

### Post by xebian on 2009-07-23
What is even more disturbing is how it was 'sneaked' in.  AFAIK Firefox add-ons has to be separately accepted and installed which is the proper way.  I agreed to the update without knowing there is an extra payload.

This maybe ok with new install and of course complete information but not when an already installed Firefox has no such add-on.

Whatever happened to the implied trust between Ubuntu and it's users?:confused:  I trust that Ubuntu meant no harm but they should  practice the best practices in terms of security.

---

### Post by Mutiny32 on 2009-07-23
> **xebian said:**
> What is even more disturbing is how it was 'sneaked' in.  AFAIK Firefox add-ons has to be separately accepted and installed which is the proper way.  I agreed to the update without knowing there is an extra payload.

This maybe ok with new install and of course complete information but not when an already installed Firefox has no such add-on.

Whatever happened to the implied trust between Ubuntu and it's users?:confused:  I trust that Ubuntu meant no harm but they should  practice the best practices in terms of security.

What's even peculiar is how I can't find anything about the extension in Launchpad besides a few bugs about how it breaks stuff. It looks as if, just like you said, it was just sneaked in.

---

### Post by Starks on 2009-07-23
AFAIK, asac (Alexander Sack), the Firefox maintainer, is solely responsible for doing this.

---

### Post by ashwinhgtx on 2009-07-23
Is it not possible to disable this? Linux Mint comes with a feature like this but it's very easy to disable it too.

---

### Post by JeevesBond on 2009-07-23
Is there a brainstorm item for getting rid of this, or is that not the best avenue for giving feedback in this case?

---

### Post by eugrus on 2009-07-23
It is a bit sad.

---

### Post by lachild on 2009-07-23
Well I came in here to see what this "Custom Search" was about and how to remove it.  I'm glad I'm not the only one here who hates this new search screen.


+1 to remove it.  


Update..  Found the extension to disable.

---

### Post by andrewabc on 2009-07-23
> **budluva04 said:**
> Tools>Add-ons>Multisearch DISABLE

seems pretty hard to do eh guys/gals?

And I'm sure every ubuntu user will know to do that when they install karmic.

Or they could get rid of it and not bother anyone.

---

### Post by Mutiny32 on 2009-07-23
> **andrewabc said:**
> And I'm sure every ubuntu user will know to do that when they install karmic.

Or they could get rid of it and not bother anyone.
Exactly. I've got my dad, who is completely computer illiterate other than how to turn the machine on/off and open/close FF running ubuntu. If he were to run an update and this crap gets installed, he would want me to "fix his Google." 

As I see it, this extension breaks Google search by default. I already have enough on my hands trying to teach him how to use FireFox.

---

### Post by AboSamoor on 2009-07-23
This is the bug regarding the new firefox addon 
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767)

---

### Post by wayne_cat on 2009-07-23
> **AboSamoor said:**
> This is the bug regarding the new firefox addon 
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767)

from the bug report:
```
This is a flagrant breach of trust. You installed something on my computer that I 
absolutely didn't want installed. Apart from the FOSS philosophy, the one thing that 
makes me love Linux is that I don't have to have ads rammed down my throat when 
using it. Or at least I didn't use to.

I suggest you remove this piece of software at once. I also suggest that whoever is 
responsible at Canonical is sacked, immediately, and that we are given assurances that 
something like this will never happen in future.

        


```hmmm ... if you "read between the lines" ... he does not like the the new feature? :-k

---

### Post by taavikko on 2009-07-23
> **wayne_cat said:**
> hmmm ... if you "read between the lines" ... he does not like the the new feature? :-k

I pondered the same thing myself, I guess you're on to something... :lolflag:

---

### Post by shakaran on 2009-07-23
The strange thing is that this is already taking too long to resolve and it is odd that only one developer is involved in this.

---

### Post by Moop on 2009-07-23
I suppose I don't mind being "tested", since that's the point of running karmic right now. But if Ubuntu starts installing this kind of stuff by default, I'll find another distro to use and recommend.

---

### Post by Mutiny32 on 2009-07-23
> **shakaran said:**
> The strange thing is that this is already taking too long to resolve and it is odd that only one developer is involved in this.

What I find odd is that Alexander Sack refers to the extension in question in a very distanced context, which sounds fishy because he is the maintainer. Him saying "If this "Multisearch" extension..." makes it sound like he was told to implement it and not ask questions.

---

### Post by shakaran on 2009-07-23
Could someone send a email to a major boss of Canonical for check this? I afraid something bad or unauthorized use for this type of facts that can be vulnerate the trust of many users.

---

### Post by ghindo on 2009-07-23
> **Mutiny32 said:**
> What I find odd is that Alexander Sack refers to the extension in question in a very distanced context, which sounds fishy because he is the maintainer. Him saying "If this "Multisearch" extension..." makes it sound like he was told to implement it and not ask questions.I think you may be reading too far into this.

---

### Post by ronacc on 2009-07-23
> **ghindo said:**
> I think you may be reading too far into this.

nah this conspiracy theory hasn't even got started , no has implicated George Bush , Dick Cheny or the trilateral commision yet .

---

### Post by Merk42 on 2009-07-23
> **ronacc said:**
> nah this conspiracy theory hasn't even got started , no has implicated George Bush , Dick Cheny or the trilateral commision yet .

It's MIKKKRO$OFT I just know it!

---

### Post by snkiz on 2009-07-24
Posted my two cents on the bug report, wouldn't want this to go the same as the update notifier (again a simple fix that was hard to find) tell the world how to disable addons!

---

### Post by ktp on 2009-07-24
good thing I use chromium

---

### Post by ranch hand on 2009-07-24
> **Starks said:**
> No this is it.

We're gonna have to take it up the rear for Karmic unless we get this voted out through  angry bug reports.
That is a kind way of putting it.  It is fairly easy to get rid of but why on earth is it there?

I have never even liked google (gasp) so this is a slap in the face.  I don't like the search bar being on FF let alone this crap.

I have used Google, I just don't see that it is better than several others.  I also have never liked belonging to a cult.

---

### Post by Mutiny32 on 2009-07-24
> **ronacc said:**
> nah this conspiracy theory hasn't even got started , no has implicated George Bush , Dick Cheny or the trilateral commision yet .

I can't think of a witty comment, it's late. I'm probably looking too much into this, but I still have to wonder why he regarded it as "this "Multisearch" extension" as if he didn't know what it was and wasn't responsible for it.

---

### Post by thegordo.john on 2009-07-24
It looks like the plugin is bundled with the firefox-3.0 package.  So the only way to uninstall is to delete the folder.  all too similar to the one-click install add-on that Microsoft force fed to those who downloaded the .NET 3.5 sp 1.  they sure caught a lot of heat for that from the community.  Hopefully the message that this force fed add-on is crap gets recognized quickly.  This is a system extension, and as such can only be deleted by removing the directory from the system.  this really shouldn't be part of the firefox-3.0 package.  It should be a separate package, like the rest of the firefox add-ons that you can install system wide.  It should probably be named differently, too, like ubuntu google search enhancement. 

the extension folder is found here :
 /usr/lib/firefox-addons/extensions/me001\@canonical.com/

in case you  want to remove the extra cruft from your box as well.

---

### Post by kaitwospirit on 2009-07-24
So according to the bug report, this extension was only meant to be used in alphas three and four and is not meant to reflect the final state of any modifications to Ubuntu's Firefox that Canonical might make. 

With just that little bit of explanation to START with, I would have been so much less irritated.

---

### Post by ranch hand on 2009-07-24
> **kaitwospirit said:**
> So according to the bug report, this extension was only meant to be used in alphas three and four and is not meant to reflect the final state of any modifications to Ubuntu's Firefox that Canonical might make. 

With just that little bit of explanation to START with, I would have been so much less irritated.
Not me.  One of the concerns always brought up when folks WANT some feature or app is space on the CD.  Granted this does not take up much space but it is space none the less.

It is crap and does not need to se the light of day in an Alpha or any place else.

---

### Post by ronacc on 2009-07-24
one does have to wonder what they were smoking .

---

### Post by Mutiny32 on 2009-07-24
Alexander Sack explained it more in detail. Unforunately, it sounds that part of this extension's motive is to collect usage data. 

Without. The. User. Knowing.

---

### Post by rudenko_ruslan on 2009-07-24
So, it's collecting usage data, huh. But for what?

---

### Post by Mutiny32 on 2009-07-24
> **rudenko_ruslan said:**
> So, it's collecting usage data, huh. But for what?

Good question.

---

### Post by ghindo on 2009-07-24
> **Mutiny32 said:**
> Alexander Sack explained it more in detail. Unforunately, it sounds that part of this extension's motive is to collect usage data. 

Without. The. User. Knowing.To be fair, we're not sure what *kind* of data is being collected - Alexander Sack still hasn't really given an explicit explanation as to the rationale and purpose behind this new add-on.

---

### Post by wayne_cat on 2009-07-24
> **Mutiny32 said:**
> Good question.

yes indeed ... maybe it is time to start wireshark or tcpdump :-k

---

### Post by snkiz on 2009-07-24
some one named Rick Spencer posted the explanation that *should* have been there right from the start. I get a sense of backpedaling from it. How did they not know that a custom search does not provide the advanced features of Google search? and how does data on what I search for help Ubuntu exactly?

links:
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767/comments/24]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767/comments/24")

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767/comments/24]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767/comments/24")

---

### Post by cariboo on 2009-07-24
Please provide a link.

---

### Post by y-lee on 2009-07-24
> **nwadams said:**
> how do we change the addon or firefox itself so that whenever we open a new tab it goes to our homepage.

The easiest way is [New Tab Homepage]("https://addons.mozilla.org/en-US/firefox/addon/777").

---

### Post by wayne_cat on 2009-07-24
> **cariboo907 said:**
> Please provide a link.

from the bug report:

[http://www.asoftsite.org/s9y/archives/162-What-is-this-Multisearch-thing-in-my-Firefox-about.html](http://www.asoftsite.org/s9y/archives/162-What-is-this-Multisearch-thing-in-my-Firefox-about.html)

edit: sorry ... wrong link ... here it is:

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767/comments/24](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767/comments/24)

---

### Post by ronacc on 2009-07-24
I just have to get my plug in for Opera , with Opera you can tell it where to search with a single letter "keyword" in the address field , and you can add your custom search engines to the list. see screenshot .

---

### Post by wayne_cat on 2009-07-24
> **ronacc said:**
> I just have to get my plug in for Opera , with Opera you can tell it where to search with a single letter "keyword" in the address field , and you can add your custom search engines to the list. see screenshot .

but this extension does not send the information "user has searched for p0rn" to Canonical.

---

### Post by ronacc on 2009-07-24
I'm a dirty old man , what would they expect me to search for ?

---

### Post by wayne_cat on 2009-07-24
> **ronacc said:**
> I'm a dirty old man , what would they expect me to search for ?

good soap?

---

### Post by ronacc on 2009-07-24
my mother tried washing my mouth out with that it %*^&@* didn't work .

---

### Post by dicairo on 2009-07-24
hiiii every body i just want to say , i don't like this add-one and it _**must be an optional**_

---

### Post by Moop on 2009-07-24
```
Change #2 is just an artefact of collecting the usage data. We could only see what parts of the FF UI people were using to do searches if we sent them to our custom page. This usage data is important because it helps us channel design and development resources to useful features, and is also important because it can be tied to revenue generation.
 Generating revenue that supports the project is a feature, not a bug. However, we are mindful of not throwing the baby out with the bath water. In other words, we must strike the balance of continuing to deliver a top notch user experience while taking advantage of revenue opportunities.
 In terms of "what kind of usage data" are we collecting, it's simply the same data that is already sent to Google and Mozilla: the requested search, and the channel for the search. This is the data that are already provided and collected every time a user performs a search with a search engine anywhere on the web, and we are simply using stock Google tools to see the aggregated results.
```[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767/comments/24](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767/comments/24)


If Canonical wanted to track my searches they should have asked first instead of sneaking in a add-on. 

I guess I'm naive but I thought Ubuntu being free also meant free from "revenue generating" add-ons.

---

### Post by ronacc on 2009-07-24
I don't think canonical is a non-profit organization . I have no objection to them making a profit . I have no problems with them including commercial non-free apps in app-center ( another thread ) or even collecting data on a VOLUNTARY basis , the sneaky part does bother me a bit .

---

### Post by ranch hand on 2009-07-24
Well I was going to comment again but this calls for nothing but profanity so I will not except to say that those involved should not be allowed to reproduce.

---

### Post by Merk42 on 2009-07-24
> **ranch hand said:**
> Well I was going to comment again but this calls for nothing but profanity so I will not except to say that those involved should not be allowed to reproduce.

They're computer programmers.... for Linux... you think they're going to be reproducing anyway?

---

### Post by ranch hand on 2009-07-24
> **Merk42 said:**
> They're computer programmers.... for Linux... you think they're going to be reproducing anyway?
While I would certainly include them they are not the responsible parties behind this wonderful feature.

---

### Post by ktp on 2009-07-24
This must mean economy is really bad...making people do stupid things...i mean collect user data.

---

### Post by zekopeko on 2009-07-24
> **Moop said:**
> [https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767/comments/24](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767/comments/24)


If Canonical wanted to track my searches they should have asked first instead of sneaking in a add-on. 

I guess I'm naive but I thought Ubuntu being free also meant free from "revenue generating" add-ons.

I hope you understand that Mozilla heavily profits from Firefox's integration of Google search. And by heavily I mean close to 100 million dollars. Sorry to say but you are naive in this regard.

> **ronacc said:**
> I don't think canonical is a non-profit organization . I have no objection to them making a profit . I have no problems with them including commercial non-free apps in app-center ( another thread ) or even collecting data on a VOLUNTARY basis , the sneaky part does bother me a bit .

They simply used a feature that was already integrated into Firefox, by Mozilla. The data is still sent to Google. They only hijacked it for their nefarious purpose of, gasp, user interface design.   

> **ranch hand said:**
> Well I was going to comment again but this calls for nothing but profanity so I will not except to say that those involved should not be allowed to reproduce.

Eugenics! Godwin comes to mind :D

---

### Post by snkiz on 2009-07-24
> **Merk42 said:**
> They're computer programmers.... for Linux... you think they're going to be reproducing anyway?

hey I resemble that remark, I'm an aspiring programmer and I have three kids... don't see them much, but they're here somewhere. :lolflag:

---

### Post by snkiz on 2009-07-24
> **zekopeko said:**
> I hope you understand that Mozilla heavily profits from Firefox's integration of Google search. And by heavily I mean close to 100 million dollars. Sorry to say but you are naive in this regard.

They simply used a feature that was already integrated into Firefox, by Mozilla. The data is still sent to Google. They only hijacked it for their nefarious purpose of, gasp, user interface design.

I think its well publicized that Mozilla drinks from the Google goblet. Quite frankly I believe Google has the right to collect anonymous statistics on their own sites. But you saying you have no problem with your os manufacturer adding code that breaks functionality for this purpose without telling anyone? and taking steps to hide it to boot? No one here is upset Ubuntu wants some info to help design with... but all they had to do was ask.

---

### Post by zekopeko on 2009-07-24
> **ktp said:**
> This must mean economy is really bad...making people do stupid things...i mean collect user data.

This gave me a good laugh :).

---

### Post by zekopeko on 2009-07-24
> **snkiz said:**
> I think its well publicized that Mozilla drinks from the Google goblet. Quite frankly I believe Google has the right to collect anonymous statistics on their own sites. But you saying you have no problem with your os manufacturer adding code that breaks functionality for this purpose without telling anyone? and taking steps to hide it to boot? No one here is upset Ubuntu wants some info to help design with... but all they had to do was ask.

You do understand that you are using an unreleased version if Ubuntu? You are the tester. They don't have to ask about every little thing. "Would you like to test this?" x 1000. Not practical.
Plus, it's not like you couldn't read the update log.
Now, the way this was implemented leaves something to be desired. I would do it by putting a nice and big message on the search page (or at least a link) explaining what I'm trying to achieve.
But in the end it didn't do any serious harm. They simply used the data you already submit to Google every time you search.

---

### Post by zekopeko on 2009-07-24
> **ronacc said:**
> I just have to get my plug in for Opera , with Opera you can tell it where to search with a single letter "keyword" in the address field , and you can add your custom search engines to the list. see screenshot .

Sorry to burst your bubble but Firefox can also do this. I noticed it in FF2 but I'm guessing it's even before that.

---

### Post by snkiz on 2009-07-24
> **zekopeko said:**
> You do understand that you are using an unreleased version if Ubuntu? You are the tester. They don't have to ask about every little thing. "Would you like to test this?" x 1000. Not practical.
Plus, it's not like you couldn't read the update log.
Now, the way this was implemented leaves something to be desired. I would do it by putting a nice and big message on the search page (or at least a link) explaining what I'm trying to achieve.
But in the end it didn't do any serious harm. They simply used the data you already submit to Google every time you search.

I'am? Jaunty is unreleased? Seriously I'm down a drive so no testing for me this round. But that doesn't mean I'm not following whats going on. And there is a BIG difference between testing and how this came down. My view from the cheap seats. BTW is it hard to talk out of both sides of your mouth like that? Defending and agreeing at the same time?

---

### Post by ronacc on 2009-07-24
> Sorry to burst your bubble but Firefox can also do this. I noticed it in FF2 but I'm guessing it's even before that.

thanks for the tip I'll look for it . I don't use FF much ,Opera is my default . I do test it though , that is what we are here for .

> You do understand that you are using an unreleased version if Ubuntu? You are the tester. They don't have to ask about every little thing. "Would you like to test this?" x 1000. Not practical.

yes we are testers , we tested this and are submitting our opinions and bug reports , if you do not agree with our opinions that is your right but I for one am not going to be a "yes man" and I will scream loudly when I believe I have been bitten .

---

### Post by meeples on 2009-07-24
i dont have a problem with the new addon, i assume its for the benefit of those users who only know how to type stuff into google, great for new user usability.

dont like it? disable it. simples.

---

### Post by wayne_cat on 2009-07-24
> **zekopeko said:**
> They simply used the data you already submit to Google every time you search.

Can I also have these data ... I would like to know what people are searching for.

---

### Post by zekopeko on 2009-07-24
> **snkiz said:**
> I'am? Jaunty is unreleased? Seriously I'm down a drive so no testing for me this round. But that doesn't mean I'm not following whats going on. And there is a BIG difference between testing and how this came down. My view from the cheap seats.

I didn't read your profile so my bad. And I'm also currently on the cheap seats. I'm missing an entire computer! But I am testing Karmic in Virtualbox, so less cheaps seats then yours :P

> BTW is it hard to talk out of both sides of your mouth like that? Defending and agreeing at the same time?

You probably missed the part where I'm talking about two different things.
Let me make myself clear:
I'm defending their intent since I think it's OK to conduct testing during, duh, a testing cycle.
I'm also agreeing that the way it was done left much to be desired.
See? No logical fallacy.

---

### Post by ronacc on 2009-07-24
> **wayne_cat said:**
> Can I also have these data ... I would like to know what people are searching for.

My last 3 searchs were , tohatsu outboards ( thinking about repowering my "duck boat" ), broadcom ( drivers for the wireless card in my HP laptop) and ethanol medic ( a fuel addative ) . sorry no p0rn .

---

### Post by wayne_cat on 2009-07-24
> **ronacc said:**
> My last 3 searchs were , tohatsu outboards ( thinking about repowering my "duck boat" ), broadcom ( drivers for the wireless card in my HP laptop) and ethanol medic ( a fuel addative ) . sorry no p0rn .

stop ... that was to fast .. you have to agree to my "protection of privacy" pop up first ;)

---

### Post by snkiz on 2009-07-24
> **zekopeko said:**
> 
I'm defending their intent since I think it's OK to conduct testing during, duh, a testing cycle.
I'm not sure anyone was disputing that, I sure wasn't.. I don't think
> **zekopeko said:**
> 
I'm also agreeing that the way it was done left much to be desired.
See? No logical fallacy.
And this is whats got everyone so riled, IMHO: scared after what happened to update manager. Be LOUD be heard right?

---

### Post by ktp on 2009-07-24
> **snkiz said:**
> IMHO: scared after what happened to update manager. Be LOUD be heard right?

update manager...part of me still wants to scrim about that...good thing I can still have the old way...the new way just doesn't work for me.

---

### Post by snkiz on 2009-07-24
> **ktp said:**
> update manager...part of me still wants to scrim about that...good thing I can still have the old way...the new way just doesn't work for me.
me to I only brought it up because I just found the fix today after reading many angry posts. Thought Ubuntu would have learned from that, a few posts to the dev mailing list is not including the community.

---

### Post by zekopeko on 2009-07-24
> **snkiz said:**
> And this is whats got everyone so riled, IMHO: scared after what happened to update manager. Be LOUD be heard right?

Not really. I would expect a more constructive approach then being LOUD to propel my argument.

> **ktp said:**
> update manager...part of me still wants to scrim about that...good thing I can still have the old way...the new way just doesn't work for me.

I really don't see the problem with the new behavior. Saves me a click at least. And doesn't get in my way.

---

### Post by snkiz on 2009-07-24
> **zekopeko said:**
> 
I really don't see the problem with the new behavior. Saves me a click at least. And doesn't get in my way.

By the look of your specs I don't imagine you would. Not all of us are blessed with such hardware. ..what I could do with your machine =P~

---

### Post by Moop on 2009-07-24
> **zekopeko said:**
> I hope you understand that Mozilla heavily profits from Firefox's integration of Google search. And by heavily I mean close to 100 million dollars. Sorry to say but you are naive in this regard.

No big deal. I amaze even myself with my naivete sometimes!

$100 million dollars! Wow! I had no idea.    Hmm...A quick check of wikipedia shows Canonical has $30 million in revenue. 

Here's a good article from the NY Times (referenced in wikipedia)
[http://www.nytimes.com/2009/01/11/business/11ubuntu.html?_r=2&pagewanted=1](http://www.nytimes.com/2009/01/11/business/11ubuntu.html?_r=2&pagewanted=1)

---

### Post by ktp on 2009-07-24
> **zekopeko said:**
> I really don't see the problem with the new behavior. Saves me a click at least. And doesn't get in my way.

<off topic>
The thing I don't like...maybe it's just me...is the minimized window.  I don't like windows open since I usually have lots of them open and use shift switcher to switch between windows. I could leave with that but thing that really annoys me is I can't say I don't want to update right now and close the window.  If I close it then I won't be reminded to update until next time.  

I just feel more in control with the old notification icon.  Makes me feel I am under control.  If I don't update and shutdown/restart computer, then it will be there next time.

I had real issues trying to keep the system updated when I tried to use the new system...would forget about updates for weeks...I know not security updates but still a update.

The other thing that seemed misleading to me was the update manager setting would be set to say check for updates daily but I would be notified week later for non-security updates.  I didn't really like that and seemed little misleading.
</off topic>

---

### Post by snkiz on 2009-07-24
I don't think it is off topic see here [https://bugs.launchpad.net/hundredpapercuts/+bug/332945]("https://bugs.launchpad.net/hundredpapercuts/+bug/332945") and here [https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767") starting to see a pattern here? angry people and heavy handedness (I thinks I just made that word up)

---

### Post by ktp on 2009-07-24
> **Moop said:**
> Here's a good article from the NY Times (referenced in wikipedia)
[http://www.nytimes.com/2009/01/11/business/11ubuntu.html?_r=2&pagewanted=1](http://www.nytimes.com/2009/01/11/business/11ubuntu.html?_r=2&pagewanted=1)

That was a good read.

---

### Post by wayne_cat on 2009-07-24
> **snkiz said:**
> I don't think it is off topic see here [https://bugs.launchpad.net/hundredpapercuts/+bug/332945](https://bugs.launchpad.net/hundredpapercuts/+bug/332945) and here [https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767) starting to see a pattern here? angry people and heavy handedness (I thinks I just made that word up)

that means ... update-manager also sends information about "User used Google to search for  < tail -f /dev/user/interests" to Canonical?

---

### Post by ktp on 2009-07-24
> **snkiz said:**
> I don't think it is off topic see here [https://bugs.launchpad.net/hundredpapercuts/+bug/332945]("https://bugs.launchpad.net/hundredpapercuts/+bug/332945") and here [https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767") starting to see a pattern here? angry people and heavy handedness (I thinks I just made that word up)

Off topic in terms of this thread.

As for the bugs...I had said lots of thing, maybe some of it should not have been said, on the update manager bug.  I was loud about that one.

As for this thread, I don't agree with or like the multisearch feature nor the method used to distribute it.  I do understand about collecting data and make some money at the same time (hack nothing is really free), but would be nice to have seen more info from the start.  It just doesn't seem very open the way things were done.  I do read the change log, so I know what is change and what to try, but would be nice to see little more info if you do need help in gather in user data :lolflag: 

But since I am moving away from firefox...chromium is very usable these days and lightning fast...I can only say please don't do that in chromium or any other product.  Pretty please :D

---

### Post by snkiz on 2009-07-24
> **wayne_cat said:**
> that means ... update-manager also sends information about "User used Google to search for  < tail -f /dev/user/interests" to Canonical?
no just thinking out loud, Canonical may be getting a "the users will like what we tell them to" kind of attitude  it would be a shame, I really like the idea that a large corporation would be interested in making the world a better place with products people actually wanted, by listening and not trying to wring ever last dollar(euro,yen...) out of them. Idealistic much?

---

### Post by zekopeko on 2009-07-24
> **Moop said:**
> No big deal. I amaze even myself with my naivete sometimes!

$100 million dollars! Wow! I had no idea.    Hmm...A quick check of wikipedia shows Canonical has $30 million in revenue. 


[http://en.wikipedia.org/wiki/Mozilla_Corporation](http://en.wikipedia.org/wiki/Mozilla_Corporation)

Check the revenue. Not look at that number really close. Now look to the right of it. 2007.

[http://john.jubjubs.net/2007/11/27/mozilla-firefox-market-share/](http://john.jubjubs.net/2007/11/27/mozilla-firefox-market-share/)

125 million users in 2007. Market share of around 20-22%

Now is 2009. Their market share is now over 30%. My guess of a 100 million looks OK.

Oh, and re-read my post. I doubt it was SO ambiguous that one could think that I was talking about Canonical.

And that article states that Mark believes that a revenue of 30 million would be enough to self-sustain Canonical, not that they earn that amount.

EDIT: And,yes I'm grumpy at this time.

---

### Post by wayne_cat on 2009-07-24
> **zekopeko said:**
> [http://en.wikipedia.org/wiki/Mozilla_Corporation](http://en.wikipedia.org/wiki/Mozilla_Corporation)

Check the revenue. Not look at that number really close. Now look to the right of it. 2007.

[http://john.jubjubs.net/2007/11/27/mozilla-firefox-market-share/](http://john.jubjubs.net/2007/11/27/mozilla-firefox-market-share/)

125 million users in 2007. Market share of around 20-22%

Now is 2009. Their market share is now over 30%. My guess of a 100 million looks OK.

Oh, and re-read my post. I doubt it was SO ambiguous that one could think that I was talking about Canonical.

And that article states that Mark believes that a revenue of 30 million would be enough to self-sustain Canonical, not that they earn that amount.

EDIT: And,yes I'm grumpy at this time.

I just don't want to be the beta tester of "Google data mining v2.0)

Let me pay for Ubuntu ... I have payed last year:

- 113.00 Euro for Mac OS 10.5
- more than 900 Euro for IBM AIX 5.3 + PowerVM + 1 year support
- 0.00 Euro for Microsoft products ;)

Can I have a "clean" Karmic for 50 Euro?

---

### Post by Moop on 2009-07-25
> **zekopeko said:**
> [http://en.wikipedia.org/wiki/Mozilla_Corporation](http://en.wikipedia.org/wiki/Mozilla_Corporation)

Check the revenue. Not look at that number really close. Now look to the right of it. 2007.

[http://john.jubjubs.net/2007/11/27/mozilla-firefox-market-share/](http://john.jubjubs.net/2007/11/27/mozilla-firefox-market-share/)

125 million users in 2007. Market share of around 20-22%

Now is 2009. Their market share is now over 30%. My guess of a 100 million looks OK.

Oh, and re-read my post. I doubt it was SO ambiguous that one could think that I was talking about Canonical.

And that article states that Mark believes that a revenue of 30 million would be enough to self-sustain Canonical, not that they earn that amount.

EDIT: And,yes I'm grumpy at this time.

I did mis-read your post and thought you were refering to Canonical. My apologies. 

The article clearly quotes Shuttleworth as saying Canonicals revenue is creeping towards $30 million.

---

### Post by gastur on 2009-07-25
I'm on the cheapest seats here, as I'm LTS user. So I'll not be loud. I'll just say (nearly in whisper) some small things.

I don't trust Google. I use addons like Customize Google to cut away some of its pseudopodia.

I was used to trust Ubuntu. One of the strongest benefits of free software I'm always pointing other people to is that no one tries to generate revenue of your actions without your willing or knowing. No adware, no spyware. One pays if there is a need for commercial grade support, or there is user's wish to thank developers of his favorite software.

I'm on the cheap seats. But I work in the one of IT departments of a huge international entity, which pays hundreds of millions $ per year to Microsoft, Cisco, IBM, HP and is now planning to pay some money to Novell for its SLES. I was doing my best to popularize Ubuntu among my co-workers and bosses because I strongly believed its better if our money paid for support goes to Canonical then to those who make strange deals with M$.

I'm stopping to do it now. Loss of trust is the end of this show for me. I don't see any difference between Novell and Canonical today.

As for Ubuntu I have already running in production - let it be there. I'm lazy. But if those who shamelessly put ad/spyware in the distro, who openly acknowledge it and even don't try to apologize are not kicked out I'll find something else for new installations.

---

### Post by knarf on 2009-07-25
> **gastur said:**
> ...I was used to trust Ubuntu...

...I'm stopping to do it now. Loss of trust is the end of this show for me. I don't see any difference between Novell and Canonical today...

Whoah pardner, not so fast. I'm know to be a loose gun when it comes to chastising evil money-grubbing megacorps (and using my only weapon being my wallet to circumvent them whenever I can) but I would not put Canonical or the Ubuntu project in that corner just yet. The unannounced data/revenue-grabbing extension is misguided but it has not gone mainstream yet. If it - or something similar - turns up in a release you might have a point but as long as it has not escaped the &#945;/&#946;-containment there is still time for some diplomacy to get things sorted out. Quiet first, loud and LOUDER later.

The web is mightier than the sword. Use it as needed, but hold your guns for now.

---

### Post by aamukahvi on 2009-07-25
Too many pages to read so this may have already been posted... Alexander Sack explains the situation in a blog: [http://www.asoftsite.org/s9y/archives/162-What-is-this-Multisearch-thing-in-my-Firefox-about.html](http://www.asoftsite.org/s9y/archives/162-What-is-this-Multisearch-thing-in-my-Firefox-about.html)

---

### Post by Swarms on 2009-07-25
[IMG]http://diy.despair.com/output/poster84066899.jpg[/IMG]

Well reasoned though. ;)

---

### Post by Merk42 on 2009-07-25
*waits for people to start saying "Mark $huttleworth"*

---

### Post by taavikko on 2009-07-25
> **Merk42 said:**
> *waits for people to start saying "Mark $huttleworth"*

the dude already has the "dough"

Canonical has to make revenue somewhere, without it, who pays the developers?
without the developers... ;) you'll catch the drift...

for me this extension saves time to manually install addon for opening a new tab directly to wanted page (or manually editing about:config) usually google anyway,
why don't I get paid for this? I need the $

---

### Post by snkiz on 2009-07-25
thanks swarms that made me spit my morning coffee out my nose. Is that what this is turning into?

---

### Post by Starks on 2009-07-31
Mark speaks...

> There were extensive discussions at the last *two* UDS's about how we might change the search. This is helping us gather data. There's no secret cabal at work. I understand your concerns, but wanted to set the record straight about the public discussion. Your feedback on the functionality is valuable - thanks!

Mark

---

### Post by jackhynes on 2009-07-31
Just a note to the developers. I am another user who has disabled Multisearch. When I use Google I use the links in the top left. I use the OneBox results. I use the 'Show options' panel. I can't believe I've put up with it for a whole week, I've been typing google.com in the address bar to avoid this annoyance! So anyway, I understand you want to collect data but this is a highly annoying way to do it, couldn't you do it without using Google Custom Search?

---

### Post by wayne_cat on 2009-07-31
> **Starks said:**
> Mark speaks...

I answer ...

```
Sorry Mark. I don't use your spyware anymore. I have removed the Ubuntu
Firefox version and downloaded a malware free Firefox from Mozilla - thanks.
```

---

### Post by zekopeko on 2009-07-31
> **wayne_cat said:**
> I answer ...

```
Sorry Mark. I don't use your spyware anymore. I have removed the Ubuntu
Firefox version and downloaded a malware free Firefox from Mozilla - thanks.
```

You are sooooooo cool! Can I be your friend?

---

### Post by ghindo on 2009-07-31
> **Starks said:**
> Mark speaks...Where did he say this?  On a mailing list?

---

### Post by wayne_cat on 2009-07-31
> **ghindo said:**
> Where did he say this?  On a mailing list?

Unfortunately there is no hint in the bug report:

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767)

---

### Post by Xamiga on 2009-07-31
> **wayne_cat said:**
> I answer ...

```
Sorry Mark. I don't use your spyware anymore. I have removed the Ubuntu
Firefox version and downloaded a malware free Firefox from Mozilla - thanks.
```

Exactly how do I go about doing this?

---

### Post by Starks on 2009-07-31
> **ghindo said:**
> Where did he say this?  On a mailing list?
[https://lists.ubuntu.com/archives/ubuntu-mozillateam/2009-July/000782.html](https://lists.ubuntu.com/archives/ubuntu-mozillateam/2009-July/000782.html)

---

### Post by ghindo on 2009-07-31
> **Xamiga said:**
> Exactly how do I go about doing this?Uninstalling the Ubuntu-branded Firefox and compiling Firefox from source is really unnecessary - if the new add-on bugs you, just disable it.  In Firefox, go to Tools -> Add-Ons, then disable the "Multisearch" extension.  Much easier than compiling from source.

---

### Post by Starks on 2009-07-31
Who said anything about compiling from source?

Mozilla offers Linux binaries and Ubuntuzilla does as well plus all the shortcuts.

---

### Post by wayne_cat on 2009-07-31
> **Starks said:**
> [https://lists.ubuntu.com/archives/ubuntu-mozillateam/2009-July/000782.html](https://lists.ubuntu.com/archives/ubuntu-mozillateam/2009-July/000782.html)

Thank you for the link

---

### Post by ghindo on 2009-07-31
> **Starks said:**
> Who said anything about compiling from source?

Mozilla offers Linux binaries and Ubuntuzilla does as well plus all the shortcuts.Oh, I didn't know that.  Regardless, I would think it would be easier to disable one add-on than to reinstall the whole program.

---

### Post by zekopeko on 2009-07-31
> **ghindo said:**
> Oh, I didn't know that.  Regardless, I would think it would be easier to disable one add-on than to reinstall the whole program.

I think those are extremes when dealing with the "problem".
I certainly support Ubuntu devs gathering data but this should have been announced on this forum and the mailing list. 
Not every little thing has to be announced but things that have a high chance of impacting user data or privacy should be announced.

If you are going to observe user's habits put a link explaining to the user what is going to be observed and what is going to be gathered and in what form. It's a 5min HTML job.

---

### Post by wayne_cat on 2009-07-31
> **zekopeko said:**
> i think those are extremes when dealing with the "problem".
I certainly support ubuntu devs gathering data but this should have been announced on this forum and the mailing list. 
Not every little thing has to be announced but things that have a high chance of impacting user data or privacy should be announced.

If you are going to observe user's habits put a link explaining to the user what is going to be observed and what is going to be gathered and in what form. It's a 5min html job.

+1

---

### Post by jbernardo on 2009-08-01
Just a stupid question - which package installs this addon? I have installed firefox under kubuntu karmic, and don't have it. I didn't install ubufox and anything related, so probably it is one of those.

---

### Post by swoody on 2009-08-05
> **zekopeko said:**
> If you are going to observe user's habits put a link explaining to the user what is going to be observed and what is going to be gathered and in what form. It's a 5min HTML job.

+1 as well! I have already disabled this addon since I enjoy using the true Google search to it's full potential. I am also seriously put-off by the fact that nobody has come out and actually said what and how the data is collected. Makes me a bit weary. If the custom Ubuntu search could provide all the features of the original Google page, I would be much more supportive. Alas, a sneaky-sneaky addon which lessens usability and removes features is not something I will have on my system.

Just my $.02 :)

---

### Post by wayne_cat on 2009-08-05
> **swoody said:**
> +1 as well! I have already disabled this addon since I enjoy using the true Google search to it's full potential. I am also seriously put-off by the fact that nobody has come out and actually said what and how the data is collected. Makes me a bit weary. If the custom Ubuntu search could provide all the features of the original Google page, I would be much more supportive. Alas, a sneaky-sneaky addon which lessens usability and removes features is not something I will have on my system.

Just my $.02 :)

You can find some information in the plugins:

---------------------------------------------------------------------------------------------------

The site that appears in ctrl+t

```
/usr/lib/firefox-addons/extensions/me001@canonical.com/chrome/content
``` If you delete the files and folders in "content"  you get a blank "new tab" again

---------------------------------------------------------------------------------------------------

The google search

```
 /usr/lib/firefox-addons/extensions/me001@canonical.com/searchplugins/google.xml
```Delete the file google.xml to "reset" the firefox google search ... better solution ... overwrite it with a "clean" version .. i.e.

```

/usr/lib/firefox-addons/searchplugins/google.xml
```

---

### Post by xebian on 2009-08-05
> **jbernardo said:**
> Just a stupid question - which package installs this addon? I have installed firefox under kubuntu karmic, and don't have it. I didn't install ubufox and anything related, so probably it is one of those.

The firefox and /or the firefox-3.5

---

### Post by xebian on 2009-08-05
> **wayne_cat said:**
> You can find some information in the plugins:

---------------------------------------------------------------------------------------------------

The site that appears in ctrl+t

```
/usr/lib/firefox-addons/extensions/me001@canonical.com/chrome/content
``` If you delete the files and folders in "content"  you get a blank "new tab" again

---------------------------------------------------------------------------------------------------

The google search

```
 /usr/lib/firefox-addons/extensions/me001@canonical.com/searchplugins/google.xml
```Delete the file google.xml to "reset" the firefox google search ... better solution ... overwrite it with a "clean" version .. i.e.

```

/usr/lib/firefox-addons/searchplugins/google.xml
```

Just delete /usr/lib/firefox-addons/extensions/me001@canonical.com

---

### Post by Darkshade on 2009-08-05
Isn't it easier to just go to Tools > Add-ons and disable it? :-k

---

### Post by xebian on 2009-08-05
Just updated to FF 3.0.13 & 3.5.2, and this is included again.  So you need to disable/or delete it again if you don't want it.

---

### Post by xebian on 2009-08-05
> **Darkshade said:**
> Isn't it easier to just go to Tools > Add-ons and disable it? :-k

I don't see it any easier that way than getting rid of it permanently.

---

### Post by wayne_cat on 2009-08-05
xebian, deleting the folder also removes it from the firefox add-ons settings ... perfect!

---

### Post by xebian on 2009-08-05
> **wayne_cat said:**
> xebian, deleting the folder also removes it from the firefox add-ons settings ... perfect!

While you are on it, you might as well get rid of the 

[email]langpack-en-GB@firefox-3.0.ubuntu.com[/email]

No offense to our UK friends but not everyone lives in UK so please stop shipping this as default.

---

### Post by olskar on 2009-08-05
> **xebian said:**
> While you are on it, you might as well get rid of the 

[email]langpack-en-GB@firefox-3.0.ubuntu.com[/email]

No offense to our UK friends but not everyone lives in UK so please stop shipping this as default.


What language do you think should be shipped as default?

---

### Post by taavikko on 2009-08-05
> **olskar said:**
> What language do you think should be shipped as default?

Mandarin Chinese is the most common language in the world ;)

---

### Post by wayne_cat on 2009-08-05
> **olskar said:**
> What language do you think should be shipped as default?

None .. firefox has an integrated en_US support

---

### Post by xebian on 2009-08-05
> **olskar said:**
> What language do you think should be shipped as default?

Nice try but for you it should be Norway.  :P

---

### Post by philinux on 2009-08-05
No Brainer.

Disabled.

---

### Post by ghindo on 2009-08-07
Well, we've made /.

[http://yro.slashdot.org/story/09/08/07/1521208/Ubuntus-New-Firefox-Is-Watching-You](http://yro.slashdot.org/story/09/08/07/1521208/Ubuntus-New-Firefox-Is-Watching-You)

As usual, the Slashdot story is a bit alarmist and doesn't mention all the facts in the summary.  Oh well.

---

### Post by mrsurb on 2009-08-07
Until it showed up on /. I hadn't even noticed... for some reason I had done an "apt-get purge ubufox" (maybe as part of apt-get purge firefox-3.0?) and so I don't think that this multi-search is installed in my firefox-3.5. Certainly it does not appear in my add-ons.

---

### Post by doas777 on 2009-08-07
I don't know... the slashdot take on it is basically the same as the one I developed after 1/2 hour reading the information provided.

this is disrespectful, and unacceptable. I will leave ubuntu if this kind of behavior becomes common place. I left MS because they insisted on controling my PC and limiting my privacy. I won't hesitate to leave again.

---

### Post by MorganLowe on 2009-08-07
Wow, seriously? I use Ubuntu on many machines, and I like my Firefox just the way it was. This is the dirtiest thing I have ever seen the Ubuntu team do. I am already downloading Open SUSE to replace this install with. I have used Ubuntu since version 6.10 and this just does it. 

Open in tab searching? Thats easy... type about:config into the address bar, agree to terms, search for "search" doubles click "Search open in new tab" and bam! no privacy violations.  

I noticed this plugin when on my media PC I lost my Gmail button. Now, I lost my trust in Ubuntu. :(  

I feel bad for all the people I installed Ubuntu for in my PC business, telling them it's safe, secure and easy. Telling them the man doesnt watch what you do on Ubuntu and open source was the way to go. I know this is only a small thing, but i wonder what will follow. Watching searches can tell you a lot about someone.

---

### Post by ghindo on 2009-08-07
I don't understand why people are getting so upset about this.

If you read the changelogs (which you probably should if you're running an alpha version), you would have noticed the new add-on.  Even if you *didn't* read the changelogs, you should have noticed the add-on the next time you started Firefox.

The add-on is extremely easy to disable, and is only being used in the development versions of Karmic.  Not only that, but as [this Slashdot commenter noted]("http://yro.slashdot.org/comments.pl?sid=1329313&cid=28988383"), the add-on isn't adding any functionality that isn't already in Firefox.  Mozilla and Google have a symbiotic relationship as well, but I haven't seen any protest about that relationship.

The notion that Canonical is violating and/or profiting off of our privacy is alarmist and ignorant.

---

### Post by taavikko on 2009-08-07
Just a side note that,
When you first install Ubuntu and start firefox for a first time, the start-page of firefox is... ;) Anyone...?

---

### Post by doas777 on 2009-08-07
> **ghindo said:**
> I don't understand why people are getting so upset about this.

If you read the changelogs (which you probably should if you're running an alpha version), you would have noticed the new add-on.  Even if you *didn't* read the changelogs, you should have noticed the add-on the next time you started Firefox.

The add-on is extremely easy to disable, and is only being used in the development versions of Karmic.  Not only that, but as [this Slashdot commenter noted]("http://yro.slashdot.org/comments.pl?sid=1329313&cid=28988383"), the add-on isn't adding any functionality that isn't already in Firefox.  Mozilla and Google have a symbiotic relationship as well, but I haven't seen any protest about that relationship.

The notion that Canonical is violating and/or profiting off of our privacy is alarmist and ignorant.

calling anothers concern about their personal privacy "alarmist and ignorant" is an extremely offensive thing to say. you have disrespected a large chunk of the community, and I think it isn't us privacy advocates that appear "Ignorant"

---

### Post by Moop on 2009-08-07
Call me alarmist and ignorant then. This multi-search addon should have been a opt in option and not something you need to opt out of. 

I don't trust Ubuntu anymore and feel like I need to watch updates for malware, etc.

---

### Post by Bios Element on 2009-08-07
Now would it ruin the party if it was pointed out that this is an alpha for **_TESTING_**, **NOT** meant to be used as a primary OS?

God forbid they use the alpha to ya know, Test things?

---

### Post by hhemken on 2009-08-07
> **ghindo said:**
> Well, we've made /.

[http://yro.slashdot.org/story/09/08/07/1521208/Ubuntus-New-Firefox-Is-Watching-You](http://yro.slashdot.org/story/09/08/07/1521208/Ubuntus-New-Firefox-Is-Watching-You)

As usual, the Slashdot story is a bit alarmist and doesn't mention all the facts in the summary.  Oh well.

That is more or less the definition of a /. post. It scared me enough to immediately come and have a look. While this sort of thing is alarming and can raise suspicions, it doesn't *seem* as bad as it was presented to be. I hope.

---

### Post by Napu5 on 2009-08-07
If this gets into the stable version, I will probably switch to an other distro. I don't mind if Canonical gets paid to make Google the default homepage and search provider, but I don't want adware.

---

### Post by doas777 on 2009-08-07
> **Bios Element said:**
> Now would it ruin the party if it was pointed out that this is an alpha for **_TESTING_**, **NOT** meant to be used as a primary OS?

God forbid they use the alpha to ya know, Test things?

from [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/402767/comments/24](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/402767/comments/24) :

> Generating revenue that supports the project is a feature, not a bug.

Now does that sound like a tool used to test? no. it does not.

---

### Post by SoftReset64738 on 2009-08-07
Call me wishy-washy, but I agree with virtually everyone.  I don't think taking one stance or another is the solution here.

Fact: the addon is in a development/test version of software
Fact: Ubuntu monitors these forums
Fact: Most people don't like this addon/feature

I do not like that Ubuntu did this as an 'opt-out' capability, but I do understand the nature of testing.  Ubuntu should have made the release notes *more* informative...that is the nature of Open Source.

As for trust in Ubuntu, this shouldn't be a deciding factor for removing trust.  If they listen to their users and remove the addon from production level software, just the opposite...it may reaffirm one's trust in Ubuntu.

In short, be mad, voice your opinions, and have some patience.  The great thing about open source is if you don't want that feature, there is nothing stopping us from downloading Mozilla source, or the binary, or the last non-development version, or even going to an entirely different browser.  (ok, maybe not so short...)

-- [SoftReset64738]("http://twitter.com/softreset64738")

---

### Post by phenest on 2009-08-07
I removed Firefox and purged all residual config files to make sure it's completely gone. Then I installed abrowser. No Multisearch addon.

---

### Post by Bios Element on 2009-08-07
> **doas777 said:**
> from [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/402767/comments/24](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/402767/comments/24) :



Now does that sound like a tool used to test? no. it does not.

Sure it does. They're **_testing a feature_**. What else would they test besides features?

---

### Post by click170 on 2009-08-07
I have to say, the way this was implemented has the unshakable stench of Microsoft, er I mean distrust about it.

Getting feedback to improve [anything], sure thats respectable.  Using a Firefox plugin, sure thats a fine way of doing it.  Installing said addon without informing the user that you are installing an addon that will be reporting back on their google search activity (regardless of actual intent) is not fine, its despicable, it shows we may have misplaced our trust in Canonical, and its just downright underhanded.

Especially after having watched the whole Firefox EULA escapade unfold, I was really expecting Canonical to be treading lightly in the waters of things that could upset the community.  All I'm saying is, you could have avoided this episode if you had just included a special notification of some kind in a popup window or balloon.
I think a FireFox plugin that is reporting on your google searches warrants at least a little bit more than simple mention in the changelog, really. 

For those who would say;
"How are they supposed to tread lightly when the slightest little change could piss off the community?"

I think your blowing it out of proportion, it's not like changing some obscure code is going to piss off a large group of people, even if there is always that one nitwit who argues over the smallest change.  I can only think of one other black mark on record which was the Firefox EULA fiasco, BUT this FF addon is still ONLY IN TESTING. Hopefully they have the good sense not to keep it in the actual release.

---

### Post by giorgosts on 2009-08-07
1. No spyware/adware/browser hijacking software please.

2. Not too much harm to the linux community nevertheless.There are plenty of alternatives, eg. various flavors of Debian, Archlinux, opensuse, Fedora. Also subscription based RHEL, which I would consider for providing a higher grade product. Ubuntu is not the start nor the end of FOSS.

---

### Post by mangurt on 2009-08-07
Wow, I found out about this via /.

And I am sorta on the fence about it.  Reading over everything (including the links supplied in the thread), I tend to see it as testing, and testing that is going horribly wrong.  Just like the update option, I don't think this is going to go away.

What to do about it?  Well, either not use Firefox, Not use Ubuntu, or cover your tracks.....

I use Opera for the majority of my web-browsing.  I am NOT going back to windows.  I could "not use Ubuntu" if this goes live, but then I would have to get use to something else....I guess I will go with "cover my tracks"

Hello TOR, here I come!

---

### Post by hikaricore on 2009-08-07
Wonder if UF is going to get /.ed ^_^

---

### Post by ranch hand on 2009-08-07
> **phenest said:**
> I removed Firefox and purged all residual config files to make sure it's completely gone. Then I installed abrowser. No Multisearch addon.
I have thought about that myself but isn't google still in abrouser?  Goggle mines info out of every search for their purposes.

I don't use google, not because of their mining operations but because I just don't like it.

I certainly will not be switching to a Novel product anytime soon.  They are too cozy with MS for me.  If I were to switch it would be Debian and Google is on there too.

Google is too insidious to escape.

This addon sucks but it, at least, was easy to disable and was sending information to folks that, for now, I do trust (particularly with the addon disabled).

---

### Post by reech on 2009-08-07
I don't have a problem  with ubuntu monetising some search results via google much like Mozilla does - though this does seem to have been the wrong way to go about it. 

Does anyone have suggestions for a *good* way to go about this? (I'm also wondering if Mozilla's Google deal had anything to do with the Ubuntu implementation)

---

### Post by wayne_cat on 2009-08-07
> **Bios Element said:**
> Now would it ruin the party if it was pointed out that this is an alpha for **_TESTING_**, **NOT** meant to be used as a primary OS?

God forbid they use the alpha to ya know, Test things?

Does that mean that I can not test Karmic if I don't accept hidden privacy violations.
What comes next ... a hidden account on my system ... connected to the Canonical
office.

---

### Post by phenest on 2009-08-07
So let me get this straight: this add-on is sending search info to Google and Canonical makes some money on the way?

---

### Post by ranch hand on 2009-08-07
> **wayne_cat said:**
> Does that mean that I can not test Karmic if I don't accept hidden privacy violations.
What comes next ... a hidden account on my system ... connected to the Canonical
office.
This is a worry.  I was shocked at all the auto reporting in Vista.  Took me about 3 days to track it all down.  A lot of that had nothing to do with improving the system.

I don't think (yet) that Canonical is interested in that type of thing but this will surely have me watching.

Not a good move with the average user of Linux I would guess.  Certainly does not build trust.

---

### Post by uid313 on 2009-08-07
I can disable it, but not uninstall it.

This is spyware?
I went away from Windows to get rid of spyware.
If Ubuntu going to ship spyware by default, then I am going back to Windows.

---

### Post by johndoe32102002 on 2009-08-07
> **ranch hand said:**
> 
Not a good move with the average user of Linux I would guess.  Certainly does not build trust.

Agreed.  I think Konqueror, Mozilla, Dillo, or W3M might be the alternative browsers to use until this disgrace clears up.

---

### Post by coolbrook on 2009-08-07
I use Mozilla's version of Firefox.

---

### Post by phenest on 2009-08-07
> **reech said:**
> I don't have a problem  with ubuntu monetising some search results via google much like Mozilla does - though this does seem to have been the wrong way to go about it. 

Does anyone have suggestions for a *good* way to go about this? (I'm also wondering if Mozilla's Google deal had anything to do with the Ubuntu implementation)

I don't have a problem with this either. It's not spyware and Canonical is making some money. But, because it involves revenue, it should have been announced. As we're testing it, perhaps a sticky on this forum? If it gets released, a declaration on the Ubuntu home page?

---

### Post by phenest on 2009-08-07
> **uid313 said:**
> I can disable it, but not uninstall it.

This is spyware?
I went away from Windows to get rid of spyware.
If Ubuntu going to ship spyware by default, then I am going back to Windows.

It's not spyware. It's not doing anything different if you had typed it on Google's search page.

> **coolbrook said:**
> I use Mozilla's version of Firefox.

And how is that different?

---

### Post by doas777 on 2009-08-07
> **reech said:**
>  Does anyone have suggestions for a *good* way to go about this? (I'm also wondering if Mozilla's Google deal had anything to do with the Ubuntu implementation)

It's like nuclear war; the only way to win, is not to play...

---

### Post by doas777 on 2009-08-07
> **phenest said:**
> It's not spyware. It's not doing anything different if you had typed it on Google's search page.


that is incorrect. the only differance between spyware and legitimate monitoring, is prior notification, easy removal and opt out by default. 

this functionality was hushed, it cannot be uninstalled, and it is optin by default. that meets the state of california's definition of spyware, and is illegal.

---

### Post by euxneks on 2009-08-07
I don't like it, especially if I cannot uninstall it. Please remove this from the final version.

---

### Post by wayne_cat on 2009-08-07
> **phenest said:**
> I don't have a problem with this either. It's not spyware and Canonical is making some money. But, because it involves revenue, it should have been announced. As we're testing it, perhaps a sticky on this forum? If it gets released, a declaration on the Ubuntu home page?

A declaration or a sticky thread is not enough. There should have been a pop up where I can accept or decline after the first start of firefox ... or ... an EULA ... you know ... Microsoft style.

pop up / EULA = you accept the feature (aka "privacy violations"). You have the choice
no pop up /Eula = you have been tricked ... and the "feature" is spyware

I did not see an EULA / pop up ... I did not agree ... so Canonical has not the right to
make money with my privacy.

---

### Post by SilverWave on 2009-08-07
Note: I support Ubuntu at every opportunity but...

I think we need a promise that this addon will not be installed by default in the final 9.10.

It should not be opt-out.

It should be uninstallable.

If it looks like spyware and it quacks like spyware...

Spyware
From Wikipedia, the free encyclopedia:
Spyware is a type of malware that is installed surreptitiously on personal computers to collect information about users, their computer or browsing habits without their informed consent.

---

### Post by reech on 2009-08-07
> **doas777 said:**
> It's like nuclear war; the only way to win, is not to play...

I'm not asking fo rsuggestions for good ways to implement spyware- I'm asking for good ways that Ubuntu could earn like Mozilla does from Google.

---

### Post by Ewingo401 on 2009-08-07
> **SilverWave said:**
> Note: I support Ubuntu at every opportunity but...

I think we need a promise that this addon will not be installed by default in the final 9.10.

It should not be opt-out.

It should be uninstallable.

If it looks like spyware and it quacks like spyware...

Spyware
From Wikipedia, the free encyclopedia:
Spyware is a type of malware that is installed surreptitiously on personal computers to collect information about users, their computer or browsing habits without their informed consent.


I agree.  Its one thing to test this "feature" in alpha and beta releases.  But if it makes it into the final release I'll make the effort to learn whatever is required to make a full switch to Debian.

---

### Post by ghindo on 2009-08-07
> **phenest said:**
> If it gets released, a declaration on the Ubuntu home page?The developers have said that this extension will probably not make it into the final 9.10 release.
> **doas777 said:**
> this functionality was hushed, it cannot be uninstalledIncorrect.  The developers have explained its functionality on their blogs (which are aggregated on [Planet Ubuntu]("http://planet.ubuntu.com/")) and in [this bug report]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767").  It is also extremely easy to disable a Firefox add-on, so I'm not sure why you are saying it cannot be uninstalled.

I'm also not sure as to why this extension is being labeled "spyware," [as developer Rick Spencer has said]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767/comments/24") (emphasis mine):> In terms of "what kind of usage data" are we collecting, **it's simply the same data that is already sent to Google and Mozilla**: the requested search, and the channel for the search. This is the data that are already provided and collected every time a user performs a search with a search engine anywhere on the web, and we are simply using stock Google tools to see the aggregated results.

---

### Post by rowdog on 2009-08-07
I'm extremely paranoid when it comes to privacy so spyware is an unforgivable sin. I guess it's time to migrate the wife's machine to Debian.

It's a real shame, I used to recommend Ubuntu to a lot of folks. Now I don't.

So long and thanks for all the fish.

---

### Post by coolbrook on 2009-08-07
> **phenest said:**
> And how is that different?

It doesn't include the controversial add-on.

---

### Post by wayne_cat on 2009-08-07
> **SilverWave said:**
> Note: I support Ubuntu at every opportunity but...

I think we need a promise that this addon will not be installed by default in the final 9.10.

It should not be opt-out.

It should be uninstallable.

If it looks like spyware and it quacks like spyware...

Spyware
From Wikipedia, the free encyclopedia:
Spyware is a type of malware that is installed surreptitiously on personal computers to collect information about users, their computer or browsing habits without their informed consent.

and this is from a Canonical statement:

```
In terms of "what kind of usage data" are we collecting, it's simply the same data
 that is already sent to Google and Mozilla: the requested search, and the channel for
 the search. This is the data that are already provided and collected every time a user 
performs a search with a search engine anywhere on the web, and we are simply using 
stock Google tools to see the aggregated results.
```
that means ... it is spyware

---

### Post by ghindo on 2009-08-07
It should also be worth noting that Canonical has to seek approval from Mozilla before they can use the Firefox brand name and logo.  So if this extension doesn't sit well with Mozilla, it probably won't make it into the final release.

---

### Post by phenest on 2009-08-07
> **doas777 said:**
> that is incorrect. the only differance between spyware and legitimate monitoring, is prior notification, easy removal and opt out by default. 

this functionality was hushed, it cannot be uninstalled, and it is optin by default. that meets the state of california's definition of spyware, and is illegal.

As this is alpha testing, you raise a bug. There is already a declaration to say this is not to be used on a production machine. It would only be illegal if it was released.

> **wayne_cat said:**
> A declaration or a sticky thread is not enough. There should have been a pop up where I can accept or decline after the first start of firefox ... or ... an EULA ... you know ... Microsoft style.

Then raise a bug report to the such.

---

### Post by ghindo on 2009-08-07
> **wayne_cat said:**
> that means ... it is spywareBy that definition of spyware, Firefox, *even without the multisearch add-on*, would qualify as spyware.  This is data both Mozilla and Google already collect, yet I have heard no concerns about either of those organizations.

---

### Post by Chayak on 2009-08-07
One of the core values of Linux has always been that it's *free* as in *freedom*.  It seems to me a blatant violation of that core value to slip in an add-on to 'collect data' without the users express knowledge and consent.

It's no big secret that it's possible to build a very accurate personality profile of an individual based upon how they use their computer and even over time with search history.  That data can be very valuable to third parties for targeted marketing in particular, but I'm sure that's not the only use they can find for it.

Ubuntu's definition 'Humanity to others', or 'I am what I am because of who we all are' doesn't seem to mean 'We're watching what you search for and trying to profit off of it.' How does slipping such a disregard for personal privacy by default into Firefox support this?

This isn't Google, Microsoft, or Yahoo storing search results.  That's all outside of your computer.  If anything you should be able to *trust* your computer, which is what Linux has long been about with the whole freedom thing.  They're really stepping on that whole principal with this little 'feature'

---

### Post by Bios Element on 2009-08-07
> **uid313 said:**
> I can disable it, but not uninstall it.

This is spyware?
I went away from Windows to get rid of spyware.
If Ubuntu going to ship spyware by default, then I am going back to Windows.

No you cannot uninstall it. If you actually remove it ubuntu will not load, just like windows. ;)

...
...
...

Or you can stop throwing a fit and disable it.

---

### Post by wayne_cat on 2009-08-07
> **ghindo said:**
> By that definition of spyware, Firefox, *even without the multisearch add-on*, would qualify as spyware.  This is data both Mozilla and Google already collect, yet I have heard no concerns about either of those organizations.

By downloading firefox you agree to their EULA:

[http://www.mozilla.com/en-US/legal/eula/](http://www.mozilla.com/en-US/legal/eula/)
[http://www.mozilla.com/en-US/legal/eula/firefox-en.txt](http://www.mozilla.com/en-US/legal/eula/firefox-en.txt)
[http://www.mozilla-europe.org/en/about/privacy/](http://www.mozilla-europe.org/en/about/privacy/)
[http://www.mozilla-europe.org/en/about/statutes/](http://www.mozilla-europe.org/en/about/statutes/)

I can not find a statement in their EULA, that Canonical is allowed to collect Data.

---

### Post by phenest on 2009-08-07
> **Chayak said:**
> One of the core values of Linux has always been that it's *free* as in *freedom*.  It seems to me a blatant violation of that core value to slip in an add-on to 'collect data' without the users express knowledge and consent.

Google collect this information as part of improving their service. How is that a violation of your freedom?

---

### Post by wayne_cat on 2009-08-07
> **Bios Element said:**
> No you cannot uninstall it. If you actually remove it ubuntu will not load, just like windows. ;)

...
...
...

Or you can stop throwing a fit and disable it.

True ... you can not uninstall it ... but you can delete it

```
sudo rm -r /usr/lib/firefox-addons/extensions/me001@canonical.com
```

---

### Post by phenest on 2009-08-07
> **wayne_cat said:**
> By downloading firefox you agree to their EULA:
I can not find a statement in their EULA, that Canonical is allowed to collect Data.

How many times must it be said: This is alpha software? Why would it be in the EULA?

---

### Post by Chayak on 2009-08-07
> **phenest said:**
> Google collect this information as part of improving their service. How is that a violation of your freedom?

I'm not talking about Google, I'm talking about Ubuntu doing it.  Google and other search engines are a separate issue.  You can proxy your searches to Google to keep your identity hidden.  If it's installed in your browser it's going to call home anyway.

---

### Post by ghindo on 2009-08-07
> **wayne_cat said:**
> I can not find a statement in their EULA, that Canonical is allowed to collect Data.That's probably because the last time Canonical included a Firefox EULA in Ubuntu, users weren't happy about it.

[http://arstechnica.com/old/content/2008/09/ubuntu-firefox-eula-dustup-reignites-oss-licensing-debate.ars](http://arstechnica.com/old/content/2008/09/ubuntu-firefox-eula-dustup-reignites-oss-licensing-debate.ars)

---

### Post by phenest on 2009-08-07
> **Chayak said:**
> I'm not talking about Google, I'm talking about Ubuntu doing it.

Same thing. Ubuntu's search page is... Google! :D

So you don't mind Canonical giving you free software, and an OS at that, but you don't want to give anything in return? Shame on you. :wink:

---

### Post by wayne_cat on 2009-08-07
> **phenest said:**
> How many times must it be said: This is alpha software? Why would it be in the EULA?

Maybe you don't know it ... there are laws to protect people.

Karmic Alpha = you lose your rights?

---

### Post by phenest on 2009-08-07
> **wayne_cat said:**
> Karmic Alpha = you lose your rights?

No. Karmic Alpha = Testing purposes only.

---

### Post by Chayak on 2009-08-07
> **phenest said:**
> Same thing. Ubuntu's search page is... Google! :D

So you don't mind Canonical giving you free software, and an OS at that, but you don't want to give anything in return? Shame on you. :wink:

That's kind of the point of Linux, you don't pay and don't have to give anything back unless you *want* to.  I don't use their default search page anyway.

---

### Post by phenest on 2009-08-07
> **Chayak said:**
> That's kind of the point of Linux, you don't pay and don't have to give anything back unless you *want* to.

But when it's free, you don't have much room for complaint, unless it's constructive. By the way, have you filed a bug report?

> **Chayak said:**
> I don't use their default search page anyway.

So this isn't a problem for you then?

---

### Post by Chayak on 2009-08-07
> **phenest said:**
> But when it's free, you don't have much room for complaint, unless it's constructive. By the way, have you filed a bug report?



So this isn't a problem for you then?

If I had discovered it, yes I would have filed a bug report but it seems it's a known issue.

It's a matter of principal.

I can see this discussion has become counter-productive as you have your opinion and I have mine.  We'll have to agree to disagree and not waste time with further exchanges.

](*,)

---

### Post by wayne_cat on 2009-08-07
> **Chayak said:**
> If I had discovered it, yes I would have filed a bug report but it seems it's a known issue.

It's a matter of principal.

I can see this discussion has become counter-productive as you have your opinion and I have mine.  We'll have to agree to disagree and not waste time with further exchanges.

](*,)

right ... no need to file a bug .... already done (one of many bug reports about this problem)

"Multisearch addon violates user trust"
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/410343](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/410343)

---

### Post by dslink on 2009-08-07
Back to Debian should have never switched to be honest.   This is the problem with companies releasing free and for pay software.

---

### Post by SilverWave on 2009-08-07
IANAL But I think this could be classed as "interception" under EU Law.

[EC starts legal action over Phorm](http://news.bbc.co.uk/1/hi/technology/7998009.stm)

The European Union Directive on Privacy and Electronic Communications requires member states to ensure the confidentiality of their communications and related traffic data. States must, it says, prohibit interception and surveillance unless the users concerned have given their consent.

---

### Post by cmsj on 2009-08-07
> **Moop said:**
> I don't trust Ubuntu anymore and feel like I need to watch updates for malware, etc.

asac has a blog post about it here: [http://www.asoftsite.org/s9y/archives/162-What-is-this-Multisearch-thing-in-my-Firefox-about.html](http://www.asoftsite.org/s9y/archives/162-What-is-this-Multisearch-thing-in-my-Firefox-about.html)

If you read that and the comments you'll see that this is an experiment (and it's happening in a *testing only* version of Ubuntu).

Going by his comment further into the blog post's comments, the data being gathered is which of the search methods people use (FF lets you search via the URL bar, the search bar and the search box on the default homepage). The only way to identify which one people are using is to use something like a google custom search.

It sounds like a usability study to me, not a permanent feature.

I humbly suggest a calmer approach. Take the time to read the blog post, don't jump to conclusions that asac and others are trying to sell you out, these guys are hugely dedicated to Free Software and the community and are working really hard to improve our experience.

(disclaimer: I'm a sysadmin at Canonical, I know asac, but I'm not a developer for Ubuntu and I don't work on the distro directly. I speak here only for myself as an Ubuntu user).

---

### Post by phenest on 2009-08-07
> **SilverWave said:**
> IANAL But I think this could be classed as "interception" under EU Law.

[EC starts legal action over Phorm](http://news.bbc.co.uk/1/hi/technology/7998009.stm)

The European Union Directive on Privacy and Electronic Communications requires member states to ensure the confidentiality of their communications and related traffic data. States must, it says, prohibit interception and surveillance unless the users concerned have given their consent.

I don't think anything is being intercepted.

---

### Post by wayne_cat on 2009-08-07
> **phenest said:**
> I don't think anything is being intercepted.

True ... this is a different problem

---

### Post by Newfoundlander on 2009-08-07
This is why I use Opera for browsing.

---

### Post by Jcink on 2009-08-07
I think some people here who are up in arms about privacy don't understand what this is.

It's just a customized google "adsense for search." Every adsense publisher has the option to get one of these custom searches. When someone clicks on an advertisement on the search page, Ubuntu gets cash.

I don't know FOR SURE what they can or can't see, but as an adsense user myself I think only Google has that information. And I can't make money from the search queries themselves (i.e. I can't resell the logs since I don't have any to begin with), that's all with Google.

Google logs everything you search for, including browser and IP. That firefox start page that they have is almost no different than this in terms of privacy.

I don't look at this addon as "spyware." The *concept* has already been in Firefox for ages and it a huge source of income for Mozilla. 

As long as there is still freedom to turn this off if people don't want it, there's no harm here. Obviously this search thing will help Canonical get money to continue to fund new and better things for the OS - don't we all want that?

If you've *never* ran a search through the google firefox start page or search in the corner, and you never use Google, and don't support them for privacy issues, I can understand then being irate at this change. 

Otherwise... just take a moment to think about what this really is and if it's really that big of a deal.

I do wish they would get the better one that firefox has though, but I have a feeling Google probably has an exclusive deal to do that. Adsense for search is kind of bad because you don't get the full engine.

---

### Post by ranch hand on 2009-08-07
If folks would calm down a bit and read all the stuff about this again they would find that this was added by Ubuntu for information for developing Ubuntu.  It is not making outside money for Ubuntu

Google already gets this information from your browsing for their gain.

I am not saying that Ubuntu was right to do it this way.

As has been stated, 9.10 is a testing release at this point, anyone using it as a production OS is taking their chances and have been warned in a sticky on this forum and on the FIRST install page in installation.

Being concerned is fine but I don't think that getting our knickers in a knot, at this point, is anything but silly.

---

### Post by doas777 on 2009-08-07
> **ranch hand said:**
> If folks would calm down a bit and read all the stuff about this again they would find that this was added by Ubuntu for information for developing Ubuntu.  It is not making outside money for Ubuntu

Google already gets this information from your browsing for their gain.

I am not saying that Ubuntu was right to do it this way.

As has been stated, 9.10 is a testing release at this point, anyone using it as a production OS is taking their chances and have been warned in a sticky on this forum and on the FIRST install page in installation.

Being concerned is fine but I don't think that getting our knickers in a knot, at this point, is anything but silly.

this definitely appears to be about illicitly driving up adwords revenue:
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/402767/comments/24](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/402767/comments/24)

it's bad enough that google know what I search for and  can identify me by IP. I don't particularly want that information sitting in one database, let alone 2. it may only be the same data that google retains, but remember, I hate google for their evil. should I hate ubuntu for the same reason?

It doesn't matter if this addon is just in testing. you don't test something you have no intention of implementing.

---

### Post by neurostu on 2009-08-07
> **doas777 said:**
> this definitely appears to be about illicitly driving up adwords revenue:
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/402767/comments/24](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/402767/comments/24)

it's bad enough that google know what I search for and  can identify me by IP. I don't particularly want that information sitting in one database, let alone 2. it may only be the same data that google retains, but remember, I hate google for their evil. should I hate ubuntu for the same reason?

It doesn't matter if this addon is just in testing. you don't test something you have no intention of implementing.

Um...  dude unless you have a dynamic IP that is changing very often any website can identify you by your IP, not just google. Its a side effect of being a big network called the internet, the websites you load kind of need it to send you the information you request.

Also if you're really that concerned about privacy problems and google then you can always switch to a different search engine. There are plenty of them out there trying to find a user base, so  just use one that doesn't track you.



Finally why do people insist that businesses that are trying to make money are evil? Sure there are times that businesses do things that are immoral and wrong, but any time a company makes a move to make more money people get all up in arms about it.

If my using my browser can help canonical make more money then tell me where to sign. Ubuntu is a great product that I have been using for well over 2 years, if they can get a few pennies from me using my computer why do I care?

Yes i do understand that they should have asked before installing the plugin, but hey you're not even using a BETA your using an ALPHA release so stop your whining and use Jaunty.

---

### Post by zekopeko on 2009-08-07
> **doas777 said:**
> It doesn't matter if this addon is just in testing. you don't test something you have no intention of implementing.

This was done so that developer can do some high volume user testing. And yes they are thinking on implementing a better search experience but they can hardly do it right if they don't know how people search.

---

### Post by tokyoahead on 2009-08-07
reasons do not justify any mean.

it's like saying "we can only improve your lives if we put you all into prison and then asking you what you are missing most."

If they want to do that, they can very well ask for voluntary participation. If ubuntu devs do not know about the sensitivity of this stuff then who will?

---

### Post by Stereotypical Rage on 2009-08-07
The sky is falling! The Sky is falling! THE SKY IS FALLING!

Seriously, some people just need to get a grip and calm down. This change was announced in the ChangeLog for Karmic. (and if you didn't read them or take the time to do research, then it is YOUR OWN FAULT)

I don't understand why we have so many people who have trouble comprehending what ALPHA class software is. Things change so much on Alpha and Beta products. Many changes don't even make the final release. Some are for the better, some are for the worst, but that's life.Some people like making mountains out of mole hills. It's totally illogical and unwarranted especially since this is an ALPHA product and it is strong recommended that it is not to be used in production environments.

Could the project maintainer/Karmic Dev team been a little bit more open when it first came into play? Sure, but that can be said for pretty much ANYTHING anyone EVER does. Shall we become more like Windows Vista now? "Are you sure? Yes/No? Are you really sure? Yes/No? Are you really really sure? Yes/No?..." In the end they(devs) explained themselves. All this "RabbleRabble" (those who are the ignorant ones on the subject) to make noise can stop. It's counter productive as it does more harm than good.

To the few that provide constructive criticism: THANK YOU!

To the people that call this malware: A) It can be disabled B) Does nothing harmful to your computer (from what I have seen and heard) C) I guess Karmic (Alphas) is malware in itself because one update could bork your whole system. D) It (Multisearch) was installed with your consent when you accepted this as an alpha classed OS as things can and will change on a near daily basis.

To the people that call this spyware: Why don't you classify Vanilla Firefox (from Mozilla) spyware? It's doing the same thing out of the box. Google, "Ubuntu" nor Mozilla are going against any privacy laws. If you find fault with Ubuntu, why not find fault with Google and Mozilla?

I welcome the change and wish it could be made better and in time it shall. I've been using Ubuntu since Warty Warthog (4.10) and things have only gotten better (with minor hiccups along the way, nothing too detrimental). I understand that we can't please everyone.


:popcorn::popcorn:

---

### Post by genjix on 2009-08-08
a good feature. saves me typing in google.com when i enter a new tab since my search bar is on wikipedia usually.

id ENABLE this feature to help ubuntu with ad revenue cos it doesnt bother me too much and i trust canonical (i use kubuntu :p)

---

### Post by Grishka on 2009-08-08
> **genjix said:**
> a good feature. saves me typing in google.com when i enter a new tab since my search bar is on wikipedia usually.

id ENABLE this feature to help ubuntu with ad revenue cos it doesnt bother me too much and i trust canonical (i use kubuntu :p)

trust... no one.

---

### Post by Stereotypical Rage on 2009-08-08
> **Grishka said:**
> trust... no one.

Sign off the Internet, Destroy your computer and live your life in solitude. :P

---

### Post by betasam on 2009-08-08
I have been managing a proxy to check requests from firefox, and each a URL is accessed I noticed a lot of hits to safebrowsing.google.com (and I turned it off manually; I prefer doing this in about:config.) You could turn it off from Preferences too.

[RIGHT]browser.safebrowsing.malware.reportURL;[http://safebrowsing.clients.google.com](http://safebrowsing.clients.google.com)
/safebrowsing/diagnostic?client=%NAME%&hl=%LOCALE%&site=
browser.safebrowsing.provider.0.gethashURL;http://safebrowsing.clients.google.com/safebrowsing/gethash?client={moz:client}&appver={moz:version}&pver=2.1
browser.safebrowsing.provider.0.keyURL;https://sb-ssl.google.com/safebrowsing/newkey?client={moz:client}&appver={moz:version}&pver=2.1
[/RIGHT]
 
I suppose this has been around for many versions and has to be turned off. Downloading and Installing Firefox from the Mozilla website also seems another alternative for now.

Seriously, auto-installation of anything that obfuscates URLs or sends them through a "data mining" engine claiming whatever (better search, safer Internet access) should require the authorization of the user.

---

### Post by Stereotypical Rage on 2009-08-08
> **betasam said:**
> Seriously, auto-installation of anything that obfuscates URLs or sends them through a "data mining" engine claiming whatever (better search, safer Internet access) should require the authorization of the user.

You already authorized it when you signed up to Alpha test the software.;)

---

### Post by fisheater on 2009-08-08
[http://yro.slashdot.org/story/09/08/07/1521208/Ubuntus-New-Firefox-Is-Watching-You](http://yro.slashdot.org/story/09/08/07/1521208/Ubuntus-New-Firefox-Is-Watching-You)

sukotto writes "Ubuntu recently released an unannounced and experimental 'multisearch' extension to Firefox alpha 3, apparently in an effort to improve the default behavior of new tabs and of search. In a response to one of the initial bug reports the maintainers mentioned that the extension's other purposes were 'collecting the usage data' and 'generating revenue.' Since this extension installs by itself and offers no warning about potential privacy violations, quite a few people (myself included) feel pretty unhappy. The only way to opt out is to disable the extension manually via Tools > Add-ons."

Bummer, was hoping this was more secure.

FE

---

### Post by lisati on 2009-08-08
[http://ubuntuforums.org/showthread.php?t=1219501](http://ubuntuforums.org/showthread.php?t=1219501)

---

### Post by Bios Element on 2009-08-08
> **Stereotypical Rage said:**
> You already authorized it when you signed up to Alpha test the software.;)

But come on, it's so much more fun to cry about it and throw a little tantrum rather then discuss something. I mean heavens, If they did that they'd never get any attention. ;)

---

### Post by Cato2 on 2009-08-08
The main issue for me is privacy - implementing a new addon that collects user search terms is a serious privacy issue.  Full disclosure of what the addon is doing is required (on the custom search page itself not just release notes), plus a clear privacy policy: who is collecting the data, is it personally identifiable, are IP addresses included, how long is it kept, etc.

There should also be an easy opt-out i.e. instructions to remove the addon, ideally as an apturl link.

---

### Post by Cato2 on 2009-08-08
> **ranch hand said:**
> 
Google already gets this information from your browsing for their gain.


Yes, but they have a clear privacy policy.  This new Ubuntu addon does not - it's been thrown together without any consideration of the privacy implications.

Implementing this addon is not necessarily bad (though I don't like it myself), but doing it without considering privacy implications was a mistake.

---

### Post by vishalrao on 2009-08-08
this thread is on slashdork now... :lolflag:

---

### Post by click170 on 2009-08-08
> **ghindo said:**
> The developers have explained its functionality on their blogs (which are aggregated on [Planet Ubuntu]("http://planet.ubuntu.com/")) and in [this bug report]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767").  It is also extremely easy to disable a Firefox add-on, so I'm not sure why you are saying it cannot be uninstalled.

I'm also not sure as to why this extension is being labeled "spyware," [as developer Rick Spencer has said]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767/comments/24")...:


And I suppose, if the author of some random piece of spyware on the web makes a post in his obscure blog about exactly what his spyware is doing, that makes it ok?  
No, it's not the same thing, and this is open source and there are regular channels that one can subscribe to such as developer mailing lists for this information, but REALLY I think its evident that a lot of users expect an actual GUI notification ^IF^ this makes it into the final release.

This brings to mind the beginning of the movie Hitchhikers Guide To The Galaxy, where earth is being destroyed because the notice that was posted wasn't read by anyone actually on earth.  Those silly humans, the notice was posted for all to read :P .


Also, I think he/she was referring to the actual ability to uninstall a piece of software (as in, remove from your machine), in this case the addon.  Disabling it is not the same as removing it from your computer. Just as killing someone isn't the same as killing someone ^and^ properly disposing of the body.
*shifty eyes*

---

### Post by SilverWave on 2009-08-08
[http://www.asoftsite.org/s9y/archives/162-What-is-this-Multisearch-thing-in-my-Firefox-about.html](http://www.asoftsite.org/s9y/archives/162-What-is-this-Multisearch-thing-in-my-Firefox-about.html)

> So here the basic facts on what Multisearch is:

   1. First of all it’s an experiment designed for an Ubuntu alpha release (meaning: this is not expected to make all happy, nor should someone expect this to be of production quality now).
   2. The multisearch extension adds a new search place to your browser experience, namely: newtab; hence the name “Multisearch”.
   3. The multisearch extension changes search identifiers in all four search places (homepage, awesomebar, quicksearch, newtab); also we had to switch to Google’s “Custom Search” as that was technically the most feasible way for us to get the anonymous usage patterns we are looking for in this experiment.
   4. The multisearch extension can be disabled in Tools -> Addons; this was done intentionally so you can easily (and should) do this if the Custom Search interferes with your workflow.

**The meat regarding usage:**

> #4 prismatic7

We only look at the relative usage ratio of the four search places mentioned; and I strongly disagree that there is any privacy impact. We only get aggregated results and we only look at data at an even higher aggregated level.

**Well that is certainly reassuring and addresses a lot of the concerns that have been raised.**

Please understand that the fear is that you are altering FireFox into FrankensteinFox/BigBrotherFox/SpamFox, tbh I don't want you messing with FireFox any more than is needed to get it working fast.

Should you be messing with newtab and search? Is that not Mozilla's role? 

I would like Canonical to be a profitable company, that's in our interest but privacy and freedom are why we use Ubuntu and so changes need to be handled with care.

Any changes to FireFox should be able to be uninstalled not just disabled, why would you deny this freedom to your users?

Informed Consent is not optional.

I wonder if an unintended consequence of including this in the 9.10 Alpha will be that users will pass on testing it. :(

---

### Post by xeriouxi on 2009-08-08
There's obviously a lot of heated discussion about this going on at the moment. Does anyone know if this change was actually mentioned in the Alpha 3 release notes or was it just randomly discovered?

Alexander Sack did respond to a lot of concerns about Multisearch in his [blog]("http://www.asoftsite.org/s9y/archives/162-What-is-this-Multisearch-thing-in-my-Firefox-about.html") and I think that was a very good thing to do. The thing that I'm now wondering is whether this anonymous usage pattern data collection was given the all-clear by Mark Shuttleworth. If it was, I would have thought he would make some kind of announcement somewhere about it as I'm sure he would have had a thought somewhere in his head that this whole thing might initiate some complaints about it, which I'm sure he would definitely not want.

Personally, if I was using Alpha 3 then I really wouldn't mind that they were collecting anomalous usage data about how I search in Firefox (assuming, of course, it was actually anomalous) but I do agree that there should have been a little bit more information about this whole thing before it triggered off all of these discussions. From what I can see reading people's comments about this, the actual announcement of what Multisearch does came after the Alpha 3 release... is this true or, like I asked at the start, was this mentioned but only in the release notes somewhere? :confused:

---

### Post by phenest on 2009-08-08
> **vishalrao said:**
> this thread is on slashdork now... :lolflag:

Really?

Hello mum! :D (I doubt she's reading it. She has more important things to do.)

I hope this add-on stays in, because it'll be good for Canonical to create some easy revenue via my umpteen searches for pornography. See, I'm not paranoid, nor am I afraid to admit what I'm searching for. What are you searching for if you need privacy. How to make a bomb? (Damn! I meant to say geography, not pornography.)

---

### Post by xebian on 2009-08-08
> **phenest said:**
> Really?

Hello mum! :D (I doubt she's reading it. She has more important things to do.)

I hope this add-on stays in, because it'll be good for Canonical to create some easy revenue via my umpteen searches for pornography. See, I'm not paranoid, nor am I afraid to admit what I'm searching for. What are you searching for if you need privacy. How to make a bomb? (Damn! I meant to say geography, not pornography.)

I didn't see it in the 3.5.2 update.

---

### Post by Stereotypical Rage on 2009-08-08
> **xebian said:**
> I didn't see it in the 3.5.2 update.

An Explaination of MultiSearch does was included on the Release Notes. Only after three days did Alexander Sack respond. But I don't recall ever seeing a full disclosure of what something in an alpha product does unless it's a major change and this wasn't.


Here's the URL to the change. (21 July)
[https://lists.ubuntu.com/archives/karmic-changes/2009-July/004580.html](https://lists.ubuntu.com/archives/karmic-changes/2009-July/004580.html)

---

### Post by jsnipe on 2009-08-08
> **mudi said:**
> Uggh, this is exactly why I don't use Linux Mint, I hated the fact that they installed a revenue-generating "Custom Search" by default.  ](*,)

I'm curious why you hate this?

---

### Post by Stereotypical Rage on 2009-08-08
> **SilverWave said:**
> Any changes to FireFox should be able to be uninstalled not just disabled, why would you deny this freedom to your users?

If you go back through the thread, you can simply remove the Extension's directory (and any extension), which for me is located: [ /usr/lib/firefox-addons/extensions/me001@canonical.com ].

What I assume you and many are looking for is this to be a deb and to be able to remove it via dpkg/apt/synaptic?

---

### Post by xebian on 2009-08-08
> **Stereotypical Rage said:**
> An Explaination of MultiSearch does was included on the Release Notes. Only after three days did Alexander Sack respond. But I don't recall ever seeing a full disclosure of what something in an alpha product does unless it's a major change and this wasn't.


Here's the URL to the change. (21 July)
[https://lists.ubuntu.com/archives/karmic-changes/2009-July/004580.html](https://lists.ubuntu.com/archives/karmic-changes/2009-July/004580.html)

I meant this MultiSearch add-on is no longer included (sneaked-out) in the 3.5.2 update.

---

### Post by xebian on 2009-08-08
> **Stereotypical Rage said:**
> If you go back through the thread, you can simply remove the Extension's directory (and any extension), which for me is located: [ /usr/lib/firefox-addons/extensions/me001@canonical.com ].

What I assume you and many are looking for is this to be a deb and to be able to remove it via dpkg/apt/synaptic?

That's the hard way.

In FireFox there is a Add-On manager thru the preferences or Tools-add-ons where a 'properly' installed add-on can be Un-Installed.  This MultiSearch has the 'Un-Install' button dis-abled.

It should have been a separate deb where you can accept/decline installation as opposed to ( why we have all these outrages) being sneaked-in' through a full Firefox deb.  It should have been like the ubufox deb package.

---

### Post by Mr. Picklesworth on 2009-08-08
> **doas777 said:**
> it's bad enough that google know what I search for and  can identify me by IP

You are asking Google: "hey, tell me what you know about pineapples"
Now, how do you expect Google to *not know what you are looking for* and still give you an answer? If you are this concerned, you should stop talking to Google and crawl the web yourself. Web sites are external from your system; they are entities that think and exist separately.

Here's another head scratcher: Apparently they have a big screen in their Mountain View location that displays the latest search queries as they come in. (I could be wrong; prying this from memory from an article I read a long while ago).

---

### Post by Stereotypical Rage on 2009-08-08
> **xebian said:**
> That's the hard way.

In FireFox there is a Add-On manager thru the preferences or Tools-add-ons where a 'properly' installed add-on can be Un-Installed.  This MultiSearch has the 'Un-Install' button dis-abled.

It should have been a separate deb where you can accept/decline installation as opposed to ( why we have all these outrages) being sneaked-in' through a full Firefox deb.  It should have been like the ubufox deb package.

ubufox was sneaked in too. I don't recall much of a hoopla over it. It too can't be removed via the Uninstall Method you describe (only via deb) and some other extensions from Vanilla Firefox are like that too. Where's the witch burning party on that?

It need not be a deb because it's a TEST. If this were to be made into something, then it would be included within ubufox.

---

### Post by Starks on 2009-08-08
> **Stereotypical Rage said:**
> If you go back through the thread, you can simply remove the Extension's directory (and any extension), which for me is located: [ /usr/lib/firefox-addons/extensions/[EMAIL="me001@canonical.com"]me001@canonical.com[/EMAIL] ].

**What I assume you and many are looking for is this to be a deb and to be able to remove it via dpkg/apt/synaptic?**
Why isn't it?

<___<

---

### Post by Stereotypical Rage on 2009-08-08
> **Starks said:**
> Why isn't it?

<___<

Is it really necessary to be one? (see my previous post)

---

### Post by xeriouxi on 2009-08-08
> **Stereotypical Rage said:**
> ubufox was sneaked in too. I don't recall much of a hoopla over it. It too can't be removed via the Uninstall Method you describe (only via deb) and some other extensions from Vanilla Firefox are like that too. Where's the witch burning party on that?

It need not be a deb because it's a TEST. If this were to be made into something, then it would be included within ubufox.

I think people are more worried about the fact that Multisearch uploads usage data...

---

### Post by zekopeko on 2009-08-08
> **Starks said:**
> Why isn't it?

<___<

Because it was the fastes and easiest way to install it. As was said many time over: it's a user interaction TEST. 
There is no need package it in a deb since it's a hack and won't be supported.

---

### Post by zekopeko on 2009-08-08
> **xeriouxi said:**
> I think people are more worried about the fact that Multisearch uploads usage data...

Less detailed data then Google. So be afraid of a medium side company employing around 200 people or a transnational entity that lives on searching user generated and other data?

And not to mention that Google has far more detailed statistics then Canonical.

---

### Post by xeriouxi on 2009-08-08
> **zekopeko said:**
> Less detailed data then Google. So be afraid of a medium side company employing around 200 people or a transnational entity that lives on searching user generated and other data?

And not to mention that Google has far more detailed statistics then Canonical.

I don't think it's really so much about what they are uploading... more of a worry that they didn't really make it clear enough about their plans to do so until after Alpha 3 was released and people found out about it.

Of course, as you did say, it's nothing compared to the data that Google harvests, but it's the principle that's worrying most people...

---

### Post by Stereotypical Rage on 2009-08-08
> **xeriouxi said:**
> I don't think it's really so much about what they are uploading... more of a worry that they didn't really make it clear enough about their plans to do so until after Alpha 3 was released and people found out about it.

Alpha 3 was released 22/23 July and this came out on 21 July. The day after Alpha 3 was released, lead maintainer had a blog post out on it.:P

---

### Post by xeriouxi on 2009-08-08
> **Stereotypical Rage said:**
> Alpha 3 was released 22/23 July and this came out on 21 July. The day after Alpha 3 was released, lead maintainer had a blog post out on it.:P

Wow... they sure did leave it until the last minute to add it to the alpha release, huh? :P

It's hard to see what the best course of action is for this now... obviously there are still a lot of people who are angry about this whole thing (as you can tell from the [bug report on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767")). I think the only way to calm this whole thing down is through some kind of apology/explanation (i.e. about the lack of information when Alpha 3 was released about what Multisearch was) from either Alexander (in addition to his already existing blog post) or Mark Shuttleworth... what do you think?

---

### Post by doas777 on 2009-08-08
> **Mr. Picklesworth said:**
> You are asking Google: "hey, tell me what you know about pineapples"
Now, how do you expect Google to *not know what you are looking for* and still give you an answer?.

the problem is not that they receive a packet and perform a handler action on it. the problem is that they log the transaction and keep it in a data wharehouse. they claim they "anonymize" the data, but several academic papers have been written about how easily the user can be directly re-identified from the supposedly anonymized data. 

remember a couple years ago when the DHS demanded that google turn over all it's logs? 
google, was able to resist only because of their power. would cannonical do the same? I don't know, and no one here, save mark himself, could tell us. 

there are signifigant dangers to misuse of this logged information. 

more than that, organizations don't log information they don't intend to use somehow. for instance, yesterday, rupert murdock of FOX threatened to stop doing business with amazon on the kindle, because amazon would not expose subscriber information to them. now why does he want that information? he already sold them a subscription that works fine without it. so why would he want it so badly, if he didn't intend to monetize it somehow. perhaps aggregate regional sales, or perhaps to build profiles on individials, and merge it with offline data, to create a wholistic view of a person both in reallife and the net. 

if a user is not careful about their privacy, they will lose it, plain and simple, but a lack of information sometimes hinders innovation. in order to be both innovative, and maintain privacy, all that is needed is restriction on the joinder of datasets derived from multiple parties for multiple purposes, when the data constiutes information about humans or their actions.

---

### Post by Mr. Picklesworth on 2009-08-08
To clarify on what I said earlier, complaining about Multisearch "uploading usage data" is equivalent to complaing that Canonical runs the main repositories for Ubuntu and is thus aware of where requests to download specific applications are coming from.

---

### Post by doas777 on 2009-08-08
> **Mr. Picklesworth said:**
> To clarify on what I said earlier, complaining about Multisearch "uploading usage data" is equivalent to complaing that Canonical runs the main repositories for Ubuntu and is thus aware of where requests to download specific applications are coming from.

which is exactly why we are presented with an optin question at install, which is unchecked by default (for the package popularity contest). a privacy policy and explanation of what the data consist of, and how it is used is also presented. I understand that this is alpha software, but it is flawed from inception if optout is not the most fundemental state. 

web-server logs may also provide a privacy policy, but it is somewhat less enforcable, and is not generally presented in a concilliotory manner, granting the majority of rights in question to the site holder. client side privacy policies are generally somewhat more user-focused, written in plain english, and defining exactly the rights that pertain to the end user.

---

### Post by neurostu on 2009-08-08
> **doas777 said:**
> the problem is not that they receive a packet and perform a handler action on it. the problem is that they log the transaction and keep it in a data wharehouse. they claim they "anonymize" the data, but several academic papers have been written about how easily the user can be directly re-identified from the supposedly anonymized data.

Do you have any idea how near impossible it would be to truly anonymize the data, while still making it useful?  Google would have to unlink searches from each other treating each search as a singular entity, which would effectively destroy their buisness model.

Google can delete all the user related meta data but as people performs searches they reveal a lot about themselves. Just having a list of queries and knowing they were performed by the same user is probably enough to figure out who some people are.
It doesn't matter if the data says who you are if it is linked to an IP, the searches them selves contain enough of the information for personal identifiers to be reconstructed.

---

### Post by estragib on 2009-08-08
> **doas777 said:**
> the problem is that they log the transaction and keep it in a data **wharehouse**.
Typo or very subtle humor?

---

### Post by cach0rr0 on 2009-08-09
Can you guys please remove this? 

The last thing we need is a bunch of scorned "it just works" Ubuntu users over on the Gentoo forums complaining about having to actually put forth effort in configuring their machines. 

With this sort of stupidity they'll be flocking en masse, and I'll be stuck helping them.

---

### Post by doas777 on 2009-08-10
> **neurostu said:**
> Do you have any idea how near impossible it would be to truly anonymize the data, while still making it useful? 

Thats exactly why this is like "Global Thermo-Nuclear Warfare". the only way to win is not to play.

That is why we must maintain a zero tolerance policy on targeted advertising. there is no way they can do it and make money without stealing privacy from us. the result is simply that they must stop. Do not pass go, do not collect 200$, do not try to pretend you earned something by tricking someone onto a website.

---

### Post by mwildam on 2009-08-10
Yes, I totally agree with you. If canonical or mozilla have financial problems I am sure there are other possibilities to help.

---

### Post by johndoe32102002 on 2009-08-10
To keep Google in-check (instead of a Firefox Add-on), try:
[https://ssl.scroogle.org](https://ssl.scroogle.org) to search Google

---

### Post by Bios Element on 2009-08-10
> **doas777 said:**
> Thats exactly why this is like "Global Thermo-Nuclear Warfare". the only way to win is not to play.

That is why we must maintain a zero tolerance policy on targeted advertising. there is no way they can do it and make money without stealing privacy from us. the result is simply that they must stop. Do not pass go, do not collect 200$, do not try to pretend you earned something by tricking someone onto a website.

Get back to the topic at hand already. Quit going on about targeted Advertising. This is about a single firefox **test** that shows how you do your google searches. End of story. Now for heavens sake take off the tinfoil hat and return to the real world rather then protecting your mirage of "privacy".

---

### Post by doas777 on 2009-08-10
> **Bios Element said:**
> Get back to the topic at hand already. Quit going on about targeted Advertising. This is about a single firefox **test** that shows how you do your google searches. End of story. Now for heavens sake take off the tinfoil hat and return to the real world rather then protecting your mirage of "privacy".

that is only part of the "multisearch" extension, who's real job is to redirect you to an adsense enabled page when opening a tab. you can't focus on only half the issue, and still accuse me of the same.

---

### Post by peronmdq on 2009-08-10
[CENTER][IMG]http://img21.imageshack.us/img21/8237/bigbrotherr.jpg[/IMG]

:P
[/CENTER]

---

### Post by zekopeko on 2009-08-10
> **doas777 said:**
> that is only part of the "multisearch" extension, who's real job is to redirect you to an adsense enabled page when opening a tab. you can't focus on only half the issue, and still accuse me of the same.

You probably missed the part where they say that this was the easiest way for them do determine from where the search was done.

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767/comments/24](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767/comments/24)

Read number 2.

Canonical isn't in the search business. They don't care for your searches but from where you do them.

---

### Post by mwildam on 2009-08-11
> **zekopeko said:**
> [https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767/comments/24](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767/comments/24)
Thanks for posting that link.

> Change #1 was an effort to explore a better user experience. Generally, it seems odd when users get a blank page, especially when they are using ff on a netbook in full screen mode. New tab simply makes the screen go white. Note that Mozilla is exploring "new tab" behaviour as well ([http://labs.mozilla.com/2009/03/new-tab-page-proposed-design-principles-and-prototype/](http://labs.mozilla.com/2009/03/new-tab-page-proposed-design-principles-and-prototype/))
I can understand that some users might even prefer to see the search page. In my case I have created my own html page as start page including a google search form. So I think the best solution would be in general that I could configure in Firefox what happens when I open a new tab - use the home page, blank page or custom link. So Firefox is IMHO the place where to add this feature.

> Change #2 is just an artefact of collecting the usage data. We could only see what parts of the FF UI people were using to do searches if we sent them to our custom page. This usage data is important because it helps us channel design and development resources to useful features, and is also important because it can be tied to revenue generation.
From just watching a few people while trying to solve something I can see that some users in general go to the google page and others use the search input box on the upper right corner. I personally do not use always the same way to do a search and I also would use a search form if it is presented when creating a new tab. I would consider it bad if any of the options to search would be removed. And I cannot understand the big additional effort in keeping all options. I further do not want to have a IE8 style interface in Firefox by no means! Keep the focus on productivity and not on fancy modern styles!

---

### Post by tekstr1der on 2009-08-11
This thread can die off now. As alarming as it was, it was just a test.

```
firefox-3.0 (3.0.13+nobinonly-0ubuntu3) karmic; urgency=low

  * good-bye "Multisearch"; we remove our karmic alpha3 experiment called
    "Multisearch" as we are approaching alpha4 (LP: #402767, #402804, #406893,
     #410997, #408484, #403246)
    - remove debian/extensions/me001 at canonical.com/...
    - update debian/firefox-3.0.install
    - update debian/rules

```

---

### Post by zekopeko on 2009-08-11
> **mwildam said:**
> From just watching a few people while trying to solve something I can see that some users in general go to the google page and others use the search input box on the upper right corner. I personally do not use always the same way to do a search and I also would use a search form if it is presented when creating a new tab. I would consider it bad if any of the options to search would be removed. And I cannot understand the big additional effort in keeping all options. I further do not want to have a IE8 style interface in Firefox by no means! Keep the focus on productivity and not on fancy modern styles!

They can't remove search options and still call it Firefox.
And I don't see how IE8 removes those options. It's a decent browser.

My suggestion is to have a mix of Chrome and Opera as the default page. On top of the page there is a Google Search (not custom) that is focused when you open a new tab. Underneath it are 8-9 Thumbnails of your most visited sites, on the right your recently closed tabs. It's simple and to the point.

---

### Post by doas777 on 2009-08-11
> **zekopeko said:**
> You probably missed the part where they say that this was the easiest way for them do determine from where the search was done.

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767/comments/24](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767/comments/24)

Read number 2.

Canonical isn't in the search business. They don't care for your searches but from where you do them.


you must have missed this part from your link
> Generating revenue that supports the project is a feature, not a bug. 
However, we are mindful of not throwing the baby out with the bath water. 
In other words, we must strike the balance of continuing to deliver a top notch user experience while taking advantage of revenue opportunities.

---

### Post by Bios Element on 2009-08-11
> **doas777 said:**
> you must have missed this part from your link

Heaven forbid there's a side-effect of making a few dollars for further dev work. And remember: Never pay rent. Because everything should be free! ;)

---

### Post by zekopeko on 2009-08-11
> **doas777 said:**
> you must have missed this part from your link

No I haven't. You do understand that Google displays those ads and Google is the one that cares about what you search for?

---

### Post by doas777 on 2009-08-12
> **zekopeko said:**
> No I haven't. You do understand that Google displays those ads and Google is the one that cares about what you search for?


from [https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767/comments/24](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767/comments/24)

> In terms of "what kind of usage data" **are we collecting**, it's simply the same data that is already sent to Google and Mozilla: the requested search, and the channel for the search.Look, I understand that you want to look at this as a not bad thing, and I want to look at it as a bad thing.
I also understand that this issue is a mix of good things and bad things. test data for developing good features is good. profiling users to target ads to them is bad. 

I won't tell you that the alteration is all bad, so please don't try to tell me that it's not at all bad (especially since this is the third time it's been directly contradicted by your source material). 
it makes me feel like my rights are in your hands and I have to make you understand, just to protect my own privacy, because people will just roll over and give it away. Every time one person give an inch, we have all lost one. if a million people give an inch, then we're under stazi rule.

---

### Post by zekopeko on 2009-08-12
> **doas777 said:**
> from [https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767/comments/24](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/402767/comments/24)

Look, I understand that you want to look at this as a not bad thing, and I want to look at it as a bad thing.
I also understand that this issue is a mix of good things and bad things. test data for developing good features is good. profiling users to target ads to them is bad. 

I won't tell you that the alteration is all bad, so please don't try to tell me that it's not at all bad (especially since this is the third time it's been directly contradicted by your source material). 
it makes me feel like my rights are in your hands and I have to make you understand, just to protect my own privacy, because people will just roll over and give it away. Every time one person give an inch, we have all lost one. if a million people give an inch, then we're under stazi rule.

Gaaaahhh!! You do understand that those ads are put there by Google? Right? RIGHT?
Your privacy is already compromised by you responding on this forum. In fact any time you interact with a server you are giving information that can be used for profiling.


> Change #2 is just an artefact of collecting the usage data. We could only see what parts of the FF UI people were using to do searches if we sent them to our custom page. This usage data is important because it helps us channel design and development resources to useful features, and is also important because it can be tied to revenue generation.

> In terms of "what kind of usage data" are we collecting, it's simply the same data that is already sent to Google and Mozilla: the requested search, and the channel for the search. This is the data that are already provided and collected every time a user performs a search with a search engine anywhere on the web, and we are simply using stock Google tools to see the aggregated results.

Read those quotes from the comment. The data is already collected by Google and Mozilla. Stop being paranoid. Profit.

---

### Post by doas777 on 2009-08-12
> **Bios Element said:**
> Heaven forbid there's a side-effect of making a few dollars for further dev work. And remember: Never pay rent. Because everything should be free! ;)


would you give your name, address, phonenum and ssn to the guy at the sandwidch counter, so that he can call your name when your sandwich is done? they want more information than that which is necessary to perform the task at hand. now why do they want it, you might ask.

bottom line, if someone is paying cannonical for the information, then they must feel it has value. perhaps they plan to sell it to the cold calling car warentee folks, or perhaps nigerian 419 scammers, or the botnet opperator, or perhaps the biggest criminals of all, the DHS.

---

### Post by doas777 on 2009-08-12
> **zekopeko said:**
> Gaaaahhh!! You do understand that those ads are put there by Google? Right? RIGHT?
Your privacy is already compromised by you responding on this forum. In fact any time you interact with a server you are giving information that can be used for profiling.

Read those quotes from the comment. The data is already collected by Google and Mozilla. Stop being paranoid. Profit.

obviously we don't see the same sentence fragment here:
> *In terms of "what kind of usage data" are we collecting,* 

I don't understand how you could misinterpret that, but so be it.

Please stop being naive. protect yourself while you still have the right to.

---

### Post by plun on 2009-08-12
Well... search engines are evil and dangerous....;)

Is Google a public service or a private company ???

---

### Post by zekopeko on 2009-08-12
> **doas777 said:**
> would you give your name, address, phonenum and ssn to the guy at the sandwidch counter, so that he can call your name when your sandwich is done? they want more information than that which is necessary to perform the task at hand. now why do they want it, you might ask.

You don't need to give the guy your "name, address, phonenum and ssn" so that he can inform you your "sandwich" is ready. Ever heard of (mobile) phones? Or the email? How do other people contact you? By writing X on a specific brick in the park and leaving a letter under the bench?

> bottom line, if someone is paying cannonical for the information, then they must feel it has value. perhaps they plan to sell it to the cold calling car warentee folks, or perhaps nigerian 419 scammers, or the botnet opperator, or perhaps the biggest criminals of all, the DHS.

It's obvious that you are mistaking Canonical/Ubuntu for some sort of a organized crime syndicate. Talk about being paranoid and highly ignorant on how Google Ads work.

Ubuntu (and any other site that has Google Ads) gets the money from Google since Google likes sites using their search engine and embedding their ads in said page. And who pays Google? Why the advertisers. And how does Google know what ads to target? Why by looking at what you searched. 

> **doas777 said:**
> obviously we don't see the same sentence fragment here:

> **In terms of "what kind of usage data" are we collecting,**
I don't understand how you could misinterpret that, but so be it.

Please stop being naive. protect yourself while you still have the right to.

That's the data Google is giving **them** since you search on Google's servers.

---

### Post by snkiz on 2009-08-13
OMG! when is this going to be let go? Canonical held their end of the bargain, the extension is gone now. Hopefully they learned what they needed, plus a bit more about how the community deals with stuff like this.

---

### Post by hikaricore on 2009-08-13
Yep it's gone folks, let it go already.

---

### Post by nbjayme on 2009-08-13
Ubuntu multisearch is not a problem for me.  If this helps support the development of my favorite distro, I'm all go for it.

---

### Post by nbjayme on 2009-08-13
"profiling users to target ads to them is bad. "

This means you don't get unnecessary ads, you get ads that may *matter to you*.  It's not bad.  All websites profile their users through cookies, IP, etc.  This is natural.

Websites need not have your personal information to do profiling.

---

