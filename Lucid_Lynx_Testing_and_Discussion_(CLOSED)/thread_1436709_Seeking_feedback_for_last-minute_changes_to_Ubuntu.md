---
title: "Seeking feedback for last-minute changes to Ubuntu's installer slideshow"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Mr. Picklesworth on 2010-03-23
Hi everybody!

I ended up tinkering way too much with behind the scenes stuff for Ubuntu's awesome new installation slideshow and the new content took longer than it should have to get done.

That's all sorted out now, though. Lots of it is similar to what we had in Karmic; a bit over a third of it has been changed to deliver a more consistent tone and to fit with all the cool new stuff. I don't want to change too much because a lot of translations have been submitted already; I didn't communicate that this needed a later freeze date, with the documentation strings. Alas, that does mean some things I *wanted* to change probably won't be touched just due to priorities, but that could be for the better anyway.

If you've installed Karmic, see if you can spot the differences ;)

If you haven't, the story is that this is displayed alongside the boring progress bar while someone installs Ubuntu. (Although the progress bar is considerably less boring this time). It isn't meant to be a marketing tool, but to introduce someone to Ubuntu and help inspire some interest in exploring the OS and discovering what it has to offer.

[SIZE="3"]You can take a look here:
[http://people.ubuntu.com/~dylanmccall/ubiquity-slideshow-ubuntu/ubuntu/slides/index.html#?controls](http://people.ubuntu.com/~dylanmccall/ubiquity-slideshow-ubuntu/ubuntu/slides/index.html#?controls)[/SIZE]

This is sort of a first draft of the Lucid content, so any constructive feedback would be greatly appreciated. If you have a few minutes, just poke through it (or sit back!), read it and let me know what you found useful, interesting, boring, weird, ugly etc.


[SIZE="1"]Known issues:
The Ubuntu One slide needs updating; someone is working on it, don't worry!

The Firefox image probably isn't displayed because your browser actually cares about dumb stuff like *security*. (It's referring to a location on your local system and works fine when running locally, which it is when actually deployed).

The random Breathe icon is a completely daft choice.

Design stuff isn't perfect. Just ignore the imperfections; this preview isn't about design. (Though I think it's quite pretty).[/SIZE]


[SIZE="3"]Thanks! Every typo fixed is a new user learning to love Ubuntu.[/SIZE]

---

### Post by uRock on 2010-03-23
Looks pretty good. The coloring is kinda dull, but they match the default theme. 

In the Music slide you mention that Ubuntu is ready to play videos and music from the Web, CDs and DVDs. This can be a misleader for newbs who will expect restricted extras and Medibuntu capabilities without them being there yet.

Those are the only things that come to mind. Thanks for asking and most importantly thanks for contributing. I love Ubuntu.:D

Cheers,
Ronnie

---

### Post by djchandler on 2010-03-23
Looks great, even in Google Chrome.

I happen to really like the new themes and colors. Hopefully by the launch next month all the websites that have links in the presentation will be sporting the new branding by then too.;)

Were you planning to use the new typeface used in the branding in your slides? As is, your design is good and clean, just wondering. This is not by any means criticism in that regard. I'm kind of a design and font nut.

**Welcome slide:**

> This release marks a major milestone in the Ubuntu project. It is easier and more reliable then ever, with hundreds of improvements including a new video editor, integrated social networking and a growing selection of extra software.

Extra software: how about, "ever-growing library of carefully selected and useful applications."

> While Ubuntu is installed

Nitpicking here about verb tense. Sorry.

"While Ubuntu is installing" or "while Ubuntu is being installed" may be more correct grammatically.

**Share and enjoy your photos**

Perhaps make less knowledgeable people that are upgrading an old copy of Ubuntu or new users wanting powerful and complex photo editing aware that the Gimp is still available for power users.

**Add a slide?**

"For those wanting to use Ubuntu in the office, strong networking capabilities are built-in to connect with other computers already in your office."

I suppose we shouldn't specifically mention what protocols are supported, just that Ubuntu can work in the office, not only because of the OpenOffice suite, but also that it is possible to configure back-up solutions and servers using Ubuntu.

---

### Post by Mr. Picklesworth on 2010-03-23
> **iRock said:**
> Looks pretty good. The coloring is kinda dull, but they match the default theme.

In the Music slide you mention that Ubuntu is ready to play videos and music from the Web, CDs and DVDs. This can be a misleader for newbs who will expect restricted extras and Medibuntu capabilities without them being there yet.

That is a good point. I had left that in there from earlier, when the bit started off with a giant essay about why we can't ship every audio codec by default and how to fix that... but then that got stripped, so the "ready to play DVDs" thing (which, come to think of it, was unchanged! Ack!) makes a lot less sense now. And looks ugly.


As for the colours, I should show off how this will (hopefully) look in Ubiquity, assuming the necessary freeze exception is let through. Still a few little glitches, but if it was perfect we wouldn't have anything to do for Merry Mamenchisaurus :)

[IMG]http://people.canonical.com/~evand/tmp/new-install-desktop.png[/IMG]

(And, to be clear, the background picture and original mockup which the design implements was by some people with the Canonical Design Team and the Ubiquity part is done by Evan D, the Ubiquity guy).

---

### Post by mcduck on 2010-03-23
Looks absolutely great. *Much* better than what we had before. :)

There's a typo on the first slide, though:
*"It is easier and more reliable **then** ever"*

Also, this (from the Office tools -slide) kind of gives image that it would *only open* the files instead of being able to edit & save them as well:
[I]"It opens files from other office applications like Microsoft Office and WordPerfect."
[/I]
Finally, the following text is now on the bottom of the accessibility -slide, and while it makes sense to mention this there perhaps mentioning how customizeable Ubuntu is would deserve a slide of it's own.
*"Remember to check out the Appearance Preferences, too. You can choose between different visual styles and even change the fonts that are used by applications."*

---

### Post by Mr. Picklesworth on 2010-03-23
> **mcduck said:**
> Looks absolutely great. *Much* better than what we had before. :)

There's a typo on the first slide, though:
"It is easier and more reliable **then** ever"

Gyah! I think that's the first time I have ever mixed up "then" and "than" in my life. I'm going to have terrible, terrible nightmares tonight.

Thanks for catching it, though. Fixed! (Not on the web, but on my local copy).

---

### Post by ranch hand on 2010-03-23
I would still like to see a way to skip the slide show and minimize that windo down to just the progress bar and the text that goes with it.

For those of us that like to monitor the installation by having an "always on top" progress bar on top of the system monitor this size is way too big.

And before someone says "well this is for folks new to the OS" I can tell you that I had been running the Live CD a couple of days before installing.  I do not see that wanting to know what the instalation process is doing is not going to be of interest to the Ubuntu noob at all.  And folks that are experienced in Linux but not Ubuntu are not likely to be real fond of not having some control over the install process, at least to the point of being able to reasonably monitor it.

The first time I installed Windows after the Dos period their "slide show" absolutely bugged the snot out of me.  I really doubt that I am the only person that feels that way about these things.

Surely this is not too hard to implement.  Yes it will take some more space on the CD.  Should be in the kb range and there is room.

---

### Post by 101011010010 on 2010-03-23
Hello there, I think that it looks much better. The only problem that I can find is that the Firefox icon doesn't show (I'm using Firefox,lol). Keep up the good work.

---

### Post by philinux on 2010-03-23
> **101011010010 said:**
>  The only problem that I can find is that the Firefox icon doesn't show (I'm using Firefox,lol). Keep up the good work.

See post #1 known issues section.

---

### Post by trystan.snyder on 2010-03-23
> **Mr. Picklesworth said:**
> 
[IMG]http://people.canonical.com/~evand/tmp/new-install-desktop.png[/IMG]

(And, to be clear, the background picture and original mockup which the design implements was by some people with the Canonical Design Team and the Ubiquity part is done by Evan D, the Ubiquity guy).

This is getting really picky, but the minimize icon in the screenshot looks very square and obviously chopped out of the usual three icon (max,min,close) group. Is there anything the design team can do?

---

### Post by collinp on 2010-03-23
> Rhythmbox Music Player helps organize your music collection. **You can insert a CD to store its contents on your computer.** The Ubuntu One Music Store is built in, too, so you can choose from millions of songs to purchase online.

The part in bold seems to leave a sort of "unexpected cliffhanger", for lack of a better term. Probably better wording would be:

> You can import and play your music collection, no matter how large or small, with a minimum of trouble.

Or something similar to that, anyway.

---

### Post by philinux on 2010-03-23
@Mr Picklesworth.

Looking good. 

One thing that would trouble me as a new user would be the wording. 

"Installing the system (as superuser)"

The superuser bit either needs and explanation or just remove it.

---

### Post by alex2399 on 2010-03-23
One thing I would do is add a subtle coloured outline to the icons in the slideshow, preferably the same orange as the progress bar. This to attract attention to the icons when they change, since the icons are new and different from other OS's. Users get to see them because it draws their attention and read their meaning, having a better recognition and meaning of the icons once they enter the real installation.

If I look at it, it's just some text scrolling by that doesn't interest me and do not really pay much attention to. So coupling it more visually to icons that convey a meaning may stimulate more people to pay attention. Allthough this may entirely be to the fact that I'm more experienced in this domain than an average user.

Have the outline fade in and out, a bit like a neon light. A duration of about 0,5 to 1,5s. Not sure if it should encompass the white circle or the icon itself, but I'm leaning more toward the circle so persons analyze the contents of the circle. Also round forms are more "friendly" than jagged edges, and in this case still professional looking I imagine.

---

### Post by uRock on 2010-03-23
Ok, the purple background along with the orange bar do make it brighter and easier on the eyes.

Cheers,
Ronnie

---

### Post by Onesimus on 2010-03-24
Here are my comments.  Feel free to ignore completely, but you asked for feedback.


**Welcome Slide**
'Ubuntu is designed to be easy'.  Easy to do what ?  Install, use - I just think it might need clarifying.

**Music and Movies Slide**
I wondered whether the Music Store should get a separate bullet point all of its own.

**Control your digital life**
My dictionary tells me the word 'upcoming' is a US adjective.  In the UK we would probably use 'up and coming'

**Accessibility in Ubuntu**
This may be a style preference, but I don't like the word 'we'.  Who does it refer to ?  Canonical, the community.  I would suggest modifying the sentence so it isn't there.
Similarly for the use of 'our' in some of the other slides

Hope this helps.

---

### Post by ranch hand on 2010-04-04
I reallize that the thread is finished as it has served its purpose.  But I did not want to start a new thread just for this example.

I am redoing my loaner external so that folks can try Ubuntu on their computer and see what it can do.  To do this I need to install a number of OS'.  This time I am just going with Ubuntu.  I am using 9.04, 9.10 and 10.04 in both 32 an 64 bit versions.

Right now I am on the Live DVD for 9.04.

For the first time in a long time (it seems) I have been able to install the way I want to install.  I know that the images are not very large, they do not need to be for this purpose.  This is how I want to be able to set up to monitor the installation.

This is how I did it on my very first install of Ubuntu (first Linux ever).

There is no way to get this functionality with the current setup with the slide show.

We have this fantastic tool in Ubuntu and we are using Linux which is supposed to give you control of your own box.  It would be really nice to be able to do that.

---

### Post by Scott82 on 2010-04-04
I think if you're talking default installation (and the words 'comes ready' implies that), you should scrap the slide for "entertainment with music and movies" and start that one over..... can play CD's, not dvds though (commercial ones at least, and that's what people would expect), 'plug in your mp3 player' is probably badly put, maybe 'plug in your ogg player'. and..... well, play videos from the web..... mmmm, going to start having flash and such installed by default? 'cuz people see something like that and first thought will be youtube.

anyway, just my thoughts on it.... personally, i think the 'restricted extras' package should be 2 packages one called 'closed-source-extras' and one called 'proprietary-codec-pack' but that's just me.... yes, you can install flash, java, etc... seperately, but that's more than one thing and i'm gonna forget some of it until i need it. but the only easy way is to install the stuff that's still never actually been confirmed from what i've seen as to whether or not their legal in the US (and some other places), people always seem to beat around the bush or refer people to a page that beats around the bush and never answers the question on that one. 

anywhoo, i just think it's best to only have messages in there that are lived up to in any opinion. not lived up to in the opinion of people that know what someone else means by it... there's still going to be tons of things that ubuntu excells in to brag about in the slides that nobody in their right mind sits and reads while something as boring as an installation is going on.

:D

fyi, a lot of times ppl thinkof what i write in a negative tone type way..... that's never (or as close to never as possible) actually the case though, so don't get me wrong.... this is meant to be in a more fun / sarcastic way.

oh, and other than that slide, it looks good :D

---

### Post by Mr. Picklesworth on 2010-04-04
> **Scott82 said:**
> I think if you're talking default installation (and the words 'comes ready' implies that), you should scrap the slide for "entertainment with music and movies" and start that one over..... can play CD's, not dvds though (commercial ones at least, and that's what people would expect), 'plug in your mp3 player' is probably badly put, maybe 'plug in your ogg player'. and..... well, play videos from the web..... mmmm, going to start having flash and such installed by default? 'cuz people see something like that and first thought will be youtube.

anyway, just my thoughts on it.... personally, i think the 'restricted extras' package should be 2 packages one called 'closed-source-extras' and one called 'proprietary-codec-pack' but that's just me.... yes, you can install flash, java, etc... seperately, but that's more than one thing and i'm gonna forget some of it until i need it. but the only easy way is to install the stuff that's still never actually been confirmed from what i've seen as to whether or not their legal in the US (and some other places), people always seem to beat around the bush or refer people to a page that beats around the bush and never answers the question on that one. 

anywhoo, i just think it's best to only have messages in there that are lived up to in any opinion. not lived up to in the opinion of people that know what someone else means by it... there's still going to be tons of things that ubuntu excells in to brag about in the slides that nobody in their right mind sits and reads while something as boring as an installation is going on.

:D

fyi, a lot of times ppl thinkof what i write in a negative tone type way..... that's never (or as close to never as possible) actually the case though, so don't get me wrong.... this is meant to be in a more fun / sarcastic way.

oh, and other than that slide, it looks good :D

That one is the source of much debate. Alas, I have vowed never to touch the strings again for the Lucid cycle, because they need to be translated :)
(And I left them pretty similar in content for that reason; because things were already being translated, my changes had to be prioritized and I couldn't really justify playing with that very much).

I'll keep your thoughts in mind for 10.10, though! Thanks for the advice.

---

### Post by VMC on 2010-04-04
One thing I notice on the last two daily-live installs (APR3rd, APR4th), is that the Firefox image is not there. Rhythmbox or music  icon , Fspot are there. Everything else except Firefox image.

---

### Post by Scott82 on 2010-04-04
really, i was just playing around :D had nothing better to do at that time in the night :D. thanks for being professional about it though, most people take it personally when i play around lol. imo it would be kinda nice if it were 2 packages, but that's making everyone not in a country with laws that make no sense adapt due to a few countries out there having stupid laws.... so it's really no better in entirety. sometimes some of us people in the US forget that not everything revolves around us. :D

---

### Post by uRock on 2010-04-04
> **Scott82 said:**
> really, i was just playing around :D had nothing better to do at that time in the night :D. thanks for being professional about it though, most people take it personally when i play around lol. imo it would be kinda nice if it were 2 packages, but that's making everyone not in a country with laws that make no sense adapt due to a few countries out there having stupid laws.... so it's really no better in entirety. sometimes some of us people in the US forget that not everything revolves around us. :D

I think patent laws make perfect sense. What is wrong with getting paid for your hard work? Does your employer expect you to work for free?;)

---

### Post by Scott82 on 2010-04-04
> **iRock said:**
> I think patent laws make perfect sense. What is wrong with getting paid for your hard work? Does your employer expect you to work for free?;)

they make sense to a point.... the point that they contradicted other laws that were there, and eventually it seemed to be decided that the corporations rights were greater than the rights of the citizens. imho, you should be able to backup any digital media that you have legally purchased. i see totally well that those rights were abused by some that sold or freely distributed the backups that they had made, but that should mean jail time for those people, not the rights of everyone that's not a douche getting revoked.

and no, i'm not interested in a political discussion on a forum that's world wide and most of the poeple on it probably aren't even part of the country that the politics are being discussed.

---

### Post by uRock on 2010-04-04
> **Scott82 said:**
> they make sense to a point.... the point that they contradicted other laws that were there, and eventually it seemed to be decided that the corporations rights were greater than the rights of the citizens. imho, you should be able to backup any digital media that you have legally purchased. i see totally well that those rights were abused by some that sold or freely distributed the backups that they had made, but that should mean jail time for those people, not the rights of everyone that's not a douche getting revoked.

and no, i'm not interested in a political discussion on a forum that's world wide and most of the poeple on it probably aren't even part of the country that the politics are being discussed.

If you buy the correct systems, you can backup your digital media. Cisco has a home server for loading movies and several or vendors have the same products for home theaters and such.

Anyways, lets give the thread back to Mr.Picklesworth.

---

### Post by dcstar on 2010-04-05
> **philinux said:**
> 
One thing that would trouble me as a new user would be the wording. 

"Installing the system (as superuser)"

The superuser bit either needs and explanation or just remove it.

+1 - the last thing computer novices need is more arcane nerd jargon that means nothing to them.

Unfortunately that Window title also appears on **every** su/root privilege window in a running 10.04 system.

---

### Post by dcstar on 2010-04-09
Just finishing off an install using the Beta 2 release and the Slide Show looks good.

No more confusing "as superuser" message and a pretty reasonable set of information slides to keep a new user interested and informed as to what they are getting with Ubuntu.

It would be interesting to see some feedback from real new users as to what they think of it.

---

### Post by ranch hand on 2010-04-09
This is probably not the best place to get that type of feed back.  I hope first time users are not installing this quite yet.

---

### Post by BrokeMahPC on 2010-04-09
On the "Share and enjoy your photos slide" it's probably unwise to use "touch-up" and "F-spot" in the same sentence. I had a look at some photo-software websites and they use "re-touch".

Got to agree with most others that the "Entertainment with Music and Movies" slide is horribly misleading. I remember I got very frustrated with my first install (intrepid) just trying to play a DVD. It took hours before I found the right solution. When you're new to Linux you often don't know what your looking for so restricted extras should be mentioned somewhere or a post install guide referred to.

Not a fan of the default desktop wallpaper - it looks like a fuzzy close-up of a slice of some out of date supermarket ham I once found in the fridge. I have swapped it for a picture of the Plymouth Splash which looks much better.

Otherwise - it looks great - nice design work on the slides, they are a great introduction.

---

### Post by LiquidMeson on 2010-04-09
> **BrokeMahPC said:**
> On the "Share and enjoy your photos slide" it's probably unwise to use "touch-up" and "F-spot" in the same sentence. I had a look at some photo-software websites and they use "re-touch".

Got to agree with most others that the "Entertainment with Music and Movies" slide is horribly misleading. 

Those who aren't look for it won't find it :p and if they do they'd probably just giggle.

-gman

---

### Post by Mr. Picklesworth on 2010-04-09
> **BrokeMahPC said:**
> On the "Share and enjoy your photos slide" it's probably unwise to use "touch-up" and "F-spot" in the same sentence. I had a look at some photo-software websites and they use "re-touch".

Got to agree with most others that the "Entertainment with Music and Movies" slide is horribly misleading. I remember I got very frustrated with my first install (intrepid) just trying to play a DVD. It took hours before I found the right solution. When you're new to Linux you often don't know what your looking for so restricted extras should be mentioned somewhere or a post install guide referred to.

Thanks!

The reason for saying "touch-up" is that it seems to be the term used in F-Spot's world. If you check out f-spot.org, that's how they describe it. The idea is that people may look for things based on those keywords, so someone will have better luck finding "touch up with F-Spot" then "retouch with F-Spot."
(And with Yelp 3, which will hopefully be in 10.10, the built in Help will finally be useful for *solving* problems instead of creating them!)
Maybe a bit subtle with F-Spot, but I use that trick in a few places. Usually it's to introduce the lingo we take for granted, like "repository", without blatantly beating people over the head with it.

You've helped convince me about the media slide, though. Again, too late for string changes in Lucid, but there is lots of demand to fix that bit, so hopefully it'll be nice in 10.10. There used to be a really complicated blurb about codecs and software freedom, and it took up about half the slide. That's why I stripped it for the much simpler, but arguably less accurate line. (Going on the assumption that, if someone tries to play Flash or some unusual media codec, he immediately has the option to install the needed stuff &#8230; which regrettably misses the fact that not everyone has an Internet connection and that doesn't happen for DVDs).

Still a bit stumped on how to do that job without saying &#8220;you're doomed, give up now!&#8221; &#8212; inspiring and encouraging people &#8212; while informing them on the issues, and without being incredibly complicated.

---

### Post by BrokeMahPC on 2010-04-09
It's a difficult one Mr. Picklesworth and you are correct in the fact that there is no easy solution. 
I think the best answer would be an icon in Applications - Sound and Video that opened an html page or pdf that explained the issue and gave a few solutions for playing restricted media. The slide is not the place to explain all that, it's very complicated.

As for the slide, different wording is required, if you can't think of a way to say it, it's probably best to say nothing at all. Ditch the slide and try to get the above included. Not easy at this late stage but possible.

It's late and I need some sleep but I will have a think about wording tomorrow and post something back.

---

### Post by mörgæs on 2010-04-09
This looks fine in general, and I can not add much to what has already been said (and it is also to late, of course).

The only things that comes to my mind is how long each screen should be presented to the user. My guess is that a beginner should have really long time to read and understand, though the text is short. 

Have you done a test with someone completely new to Ubuntu? Shown him the slide show and asked him afterwards what he remembered? Just an idea, not bitching!

---

### Post by LiquidMeson on 2010-04-09
> **mörgæs said:**
> how long each screen should be presented to the user

Arrows to jump back and forth through slides are nice, for the anxious or if its to fast.

"you're doomed", Licensed audio and video formats are also available in the Ubuntu software store!

---

### Post by vininim on 2010-04-10
It's quite nice! It managed to drive my attention away from the progress bar and working netbook(with Lucid in it :) ). The idea of being able to jump back and forward is a must.

---

### Post by BrokeMahPC on 2010-04-10
Entertainment with music and movies - proposed slide changes for 10.10

Current wording
-Ubuntu is ready to play music and videos from the web, from CDs and  DVDs.
-Plug in an MP3 player to start synchronizing your music collection, or  insert a CD to copy songs to your computer.

I think we all agree this is misleading so best to put these two together with some sort of qualifying phrase,[FONT=Arial] such as:[/FONT]

-With additional software and codecs:
-Ubuntu is ready to play music and videos from the web, from CDs and  DVDs.
-Plug in an MP3 player to start synchronizing your music collection, or  insert a CD to copy songs to your computer.
[SIZE=1]-**Legal Notice** [I]Patent  and copyright laws operate differently depending on which country you  are in. Please obtain legal advice if you are unsure whether a  particular patent or restriction applies to a media format you wish to  use in your country.

[/I][/SIZE]Here is the problem - mentioning installing additional software and  codecs requires the legal notice and we get into the arena of long  winded explanations, but, if we are honest with our wording it's  unavoidable.
I am in favour of not including this info here. What we really need is a  link (eg:How to play DVD's and MP3's) in Menu: Applications - Sound and  Video that takes you to a page like this:[SIZE=1][I][FONT=Arial][SIZE=2]
[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)

Where everything is explained. The first place someone who can't play a DVD is likely to look will be in the menu. It's the lawyers Mr Picklesworth! You will have to check that you aren't digging any potholes with this.
[/SIZE][/FONT][/I][/SIZE]

---

