---
title: "Looking for feedback on ubiquity-slideshow entry and exit"
date: 2009-09-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Mr. Picklesworth on 2009-09-25
Hi everybody!
The Ubiquity Slideshow got a quick beta freeze exception in which the first, last and Installing Software slides are quite heavily modified.

There'll need to be another because Software Store was renamed to Software Center, so I thought this would be a nice opportunity to find out where we are at and slip in some other fixes! It would be awesome for these slides to be complete for the beta.

So, if you have a few minutes to spare, could you please check out the new slides and let me know how they are? The easiest way to do this is to install the [ubiquity-slideshow-ubuntu]("apt:ubiquity-slideshow-ubuntu") package, then pull up your nearest web browser and open [file:///usr/share/ubiquity-slideshow/slides/index.html#controls]("file:///usr/share/ubiquity-slideshow/slides/index.html#controls"). Just browse through them with the arrows at the bottom (which were added by the #controls thing). Pay specific attention to the first slide and the last two slides.

Something I hope will get scrutinized is my list of examples for great apps available. I decided to focus on what can be done with Ubuntu, and it definitely has been used for robots (remember that fancy self-driving car which was powered by Ubuntu?)... we have Blender, an awesome music studio and panorama software, to boot. The list feels a bit heavy to the tongue, though, however awesome it may be. Maybe if people can suggest their own not-quite-one-liners that describe the richness of free software available for Ubuntu, something super awesome will come out.



I am also working on a heavy rewrite of the middle slides (which are like a desert by contrast). If you would like, you can check out the progress for that at [https://code.launchpad.net/~ubiquity-slideshow/ubiquity-slideshow-ubuntu/middle-tweaks]("https://code.launchpad.net/~ubiquity-slideshow/ubiquity-slideshow-ubuntu/middle-tweaks") and my message about those specifically here: [https://lists.launchpad.net/ubiquity-slideshow/msg00162.html](https://lists.launchpad.net/ubiquity-slideshow/msg00162.html).

---

### Post by ranch hand on 2009-09-26
You are already familiar with my opinion of the slide show.

What I would really like to see is a way to opt out.  One of these days I will get a Live CD that will boot to the desktop.  Then I can do something else on a different workspace. No problem.

However, when you have to use the "install ubuntu" option you have no choice.  This really is a bummer.

I have no idea how hard it would be to have it so that it could be turned off.  If this is a bugger to get done, don't do it.  I am sure that I am not alone in my feelings about this but it is not like life or death.

---

### Post by Totzo on 2009-09-26
I think it looks good. For someone who has never used a gnu linux system before it's reassuring to see that ubuntu uses familiar software. It may be an idea to mention that there are also restricted 3d drivers available in the repos? Obviously this is flagged up when you log in but could be an idea.

You could mention that thunderbird (more well known) is available as an alternative to evolution. You could mention features of the Gimp to the f-spot slide too as it is cross platform and more well known.

I'd rather see this along with a progress bar than a progress bar on it's own.

---

### Post by NCLI on 2009-09-26
I really don't understand why anyone would like to turn it off. It's much more interesting to look at than the progressbar, doesn't really use any additional resources, and you can minimize it!

Sure, you can't minimize the window if you choose "Install ubuntu," but the progressbar will still be there, just like it always has, and you can turn off your monitor if it really bothers you that much ;)

---

### Post by TrueTom on 2009-09-26
Welcome

    * Thank you for choosing Ubuntu.
        Lame... :)

    * While Ubuntu is installing, we invite you to explore your new operating system.
        Does that work on a direct install?

    * Let us know about your Ubuntu Experience at ubuntu.com/community!
        Does that work? If not, do you expect people to remember it or even care?

    * Ubuntu is built to be safe. Feel free to explore!
        Scary wording...


Browse the web with Firefox

    * Ubuntu comes with Firefox 3, one of the most popular and useful web browsers in the world.
        "Popular" and "useful" are lame. Also the wording is inconsistent with the other slides

    * Firefox keeps you safe by blocking pop-ups and warning about malware.
        Scary wording.        

    * You can download add-ons that adapt Firefox to your personal requirements.
        

Relive Memories with F-Spot Photo Manager
    Weird wording :)

    * F-Spot makes it easy to display, organise, edit and share all your photos.
        Get rid of display

    * Import files from your phone and export them to Flickr.
    * Find a picture in seconds with tagging and timelines.
    * Make memories crystal clear by adjusting the colour, removing red-eye or adding effects.
        Again weird wording. Here's what Apple does: iPhoto makes managing your photos as easy as taking them. It helps you organize your photos so you can find them fast. Edit them so they look their best. And share them with your friends and family.
    
Accessibility in Ubuntu

    This whole slide is probably pointless if you need braille or magnification.

    * Ubuntu makes computing easy whatever your circumstances.
    * A range of assistive technologies make Ubuntu one of the most accessible operating systems around.
    * We have you covered whether you want slow key support, magnification, braille or more.

Control your digital life with Evolution

    * Use Evolution for email, calendar, tasks and contact sharing.
        Imperativ is weird. 
    
    * Comprehensive mail filters and search tools make managing your mail a breeze.
    * Calendar events show up in the system clock, so you never miss an important meeting.
        Weird and lame.


Keep in contact with Empathy IM

    * Empathy IM is Ubuntu's instant messaging tool.
    * Empathy connects to all the major IM networks, so you only ever need to learn one interface.
        Needs some name dropping like ICQ, MSN so people actually get the idea.

Office tools at your fingertips

    * OpenOffice.org is a powerful office application that you can start using very quickly.
        Weird wording.
    * OpenOffice.org creates letters, presentations and spreadsheets, as well as drawings and databases.
        No need for "OpenOffice.org" again and again.
    * OpenOffice.org keeps you compatible with your friends, no matter what office software they use.
        Not true ;) ...also lame.

Watch and listen on Ubuntu

    * Movie Player makes it easy to play a huge variety of formats, including streamed content from the BBC, YouTube and other sources.
        lame, weird, too long and probably not true       
    
    * Rhythmbox Music Player helps you share music with your friends, listen to Internet radio or download Creative Commons music.
        weird and lame

    * Rhythmbox also manages your Podcasts subscriptions and connects to your MP3 player, so you can listen to your music on the go.
        inconsistent slide and lame. 


Installing additional software

    Whole slide: Technical, lame, weird

    * Use Add/Remove... to install and uninstall thousands of approved applications from our online repositories.
    * The Ubuntu community makes sure these packages are polished and virus-free to make your life easier and safer.
    * Regular updates keep you up-to-date when improvements and new versions become available.
        

Getting Help with Ubuntu

    * All this is just the beginning!
        weird
    * Ask your questions at ubuntuforums.org, where advanced users help people just like you.
        Insulting users might not be a good idea.        

    * The installation will finish soon. We hope that you enjoy using Ubuntu!
        lame

---

### Post by amano on 2009-09-26
> **TrueTom said:**
> 
    * Use Add/Remove... to install and uninstall thousands of approved applications from our online repositories.
    * The Ubuntu community makes sure these packages are polished and virus-free to make your life easier and safer.
    * Regular updates keep you up-to-date when improvements and new versions become available.


If I am not completely wrong, "Add/Remove..." will be gone once the Karmic K. hits the streets...

TrueTom has some very convincing points though, some really good catches ;)

---

### Post by Totzo on 2009-09-26
> **amano said:**
> If I am not completely wrong, "Add/Remove..." will be gone once the Karmic K. hits the streets...

TrueTom has some very convincing points though, some really good catches ;)

Yes, but apart from saying "lame" and "weird" a lot has he actually come up with anything better? No.

---

### Post by TrueTom on 2009-09-26
> **Totzo said:**
> Yes, but apart from saying "lame" and "weird" a lot has he actually come up with anything better? No.

That isn't a requirement for criticizing.

---

### Post by Totzo on 2009-09-26
> **TrueTom said:**
> That isn't a requirement for criticizing.

Indeed, but it does tend to be a characteristic of critics!

---

### Post by TrueTom on 2009-09-26
> **Totzo said:**
> Indeed, but it does tend to be a characteristic of critics!

I'm not sure I'm getting you there... Are you saying that being a food critic implies that you must be able to cook better than the people you criticize? :)

---

### Post by TrueTom on 2009-09-26
Ok, here's my take on the Firefox slide:

*Before:*

> 
**Browse the web with Firefox**
[LIST]
[*]Ubuntu comes with Firefox 3, one of the most popular and useful web browsers in the world.

[*]Firefox keeps you safe by blocking pop-ups and warning about malware.

[*]You can download add-ons that adapt Firefox to your personal requirements.
[/LIST]


*After:*

> 
**Experience the Web with Firefox 3.5**
[LIST]
[*]Firefox 3.5 is the fastest and most advanced browser in Ubuntu ever.
[*]It protects your privacy and personal information so you can surf worry free.
[*]Apply your own personal note and choose from thousands of themes and add-ons to fit exactly your online needs.
[/LIST]


---

### Post by Totzo on 2009-09-26
> **TrueTom said:**
> I'm not sure I'm getting you there... Are you saying that being a food critic implies that you must be able to cook better than the people you criticize? :)

Of course they should!

I'm just saying that it might be more constructive to offer alternative ideas- it's not a critisism :p

---

### Post by Guruji on 2009-09-26
> **TrueTom said:**
> I'm not sure I'm getting you there... Are you saying that being a food critic implies that you must be able to cook better than the people you criticize? :)

I agree, but maybe you could be more specific than just lame & weird, some of the weird wording are obvious I agree but some others need maybe some "underlining" of the weird part.

And what's not true about the movieplayer formats, streaming, bbc, youtube?

---

### Post by Guruji on 2009-09-26
> **Totzo said:**
> Of course they should!

I'm just saying that it might be more constructive to offer alternative ideas- it's not a critisism :p

Sometimes it's hard to offer alternative ideas, ex: I can spot weirdess in the wording of some slides.. but I can't really offer you an alternative as I'm not a native english speaker and might just add more weirdness to the slide. Some are good at spoting, some at providing alternatives etc..
Now eventually you can go back to the thread and provide some ideas to enhance the slides or alternatives.

---

### Post by Totzo on 2009-09-26
From the F-spot website:

>  Organize, Enjoy, and Share Your Photos
F-Spot is a full-featured personal photo management application for the GNOME desktop.
F-Spot simplifies digital photography by providing intuitive tools to help you share, touch-up, find and organize your images. 

Good enough I'd say.

---

### Post by TrueTom on 2009-09-26
> **Guruji said:**
> I agree, but maybe you could be more specific than just lame & weird, some of the weird wording are obvious I agree but some others need maybe some "underlining" of the weird part.

And what's not true about the movieplayer formats, streaming, bbc, youtube?

> 
Movie Player **makes it easy to play** a huge variety of formats, including streamed content from the BBC, YouTube and other sources.


Playing movies is easy for most people that come from another OS. You can't make it easier. This comes from a Linux mindset where playing videos is a hard problem.


> 
Movie Player makes it easy to play a **huge variety of formats**, including streamed content from the BBC, YouTube and other sources.


What is a format? Why is there a huge variety? Is this good? Why should I care? Specifics are better than technical terms. Something along the lines of "let's you enjoy all your favourite videos and DVDs" (in case it can actually play DVDs).


> 
Movie Player makes it easy to play a huge variety of formats, including **streamed content from the BBC, YouTube and other sources**.


What is streamed content? Who is BBC? Why do I need a media player for Youtube? What are other sources? The "probably not true" part refers to the Movie Player sidebar which only has support for Youtube and BCC and nothing else. In addition to that picking Youtube support is a weird feature to showcase. Most people would prefer working Youtube support in the browser.

---

### Post by philinux on 2009-09-26
> **Mr. Picklesworth said:**
> 


I think the slideshow is a great addition to the live cd. I go and make a coffee while I'm reinstalling but for new users these are really useful.

Anyhow you asked for comments so here goes.

Changes I would make.

1.	I would drop  “Ubuntu is designed...”

2.	Firefox helps to keep you safe. It cant guarantee.

3.	I would drop  “Relive memories with” and change bottom bullet to“Improve your photos by...”

4.	Fine.

5.	Evolution, your personal information manager.

6.	Empathy, your instant messaging  tool.

7.	Fine

8.	Movies and Music on Ubuntu. “Watch and listen is not good.”

9.	Fine

10,	Fine

---

### Post by Keyper7 on 2009-09-26
> **TrueTom said:**
> I'm not sure I'm getting you there... Are you saying that being a food critic implies that you must be able to cook better than the people you criticize? :)

No, but it does imply being more specific than "this tastes bad". I never saw a food critic that stopped at this point. :)

On topic, the icons of the slideshow are not consistent. It really bothers me that they don't all have the same theme, feels very unpolished.

---

### Post by Mr. Picklesworth on 2009-09-26
> **Totzo said:**
> Yes, but apart from saying "lame" and "weird" a lot has he actually come up with anything better? No.

Actually, that has pointed out something useful: Of course, people using repositories hosted elsewhere (not the central one) may have an out of date version of this. The new one I'm talking about here is version 7.

I (unusually) appreciate even "this is lame" as long as you're pointing to the specific examples. Most of the particularly lame ones have changed either in release 7 or with the middle-tweaks branch. (Now I'm trying to make them simple again).

TrueTom, I really like your Firefox slide. I changed it a bit earlier, but I'm going to steal some of yours if that's okay...

---

### Post by TrueTom on 2009-09-26
> **Mr. Picklesworth said:**
> Actually, that has pointed out something useful: Of course, people using repositories hosted elsewhere (not the central one) may have an out of date version of this. The new one I'm talking about here is version 7.

I updated and there is indeed a new version. Though, only the first and last slide changed so I still stand by my "this is lame" comments. :)

---

### Post by Mr. Picklesworth on 2009-09-29
Okay, I have the aforementioned changes to all of the middle slides up here:
[http://www3.telus.net/northlight/dylan/ubiquity-slideshow-proposed/#controls](http://www3.telus.net/northlight/dylan/ubiquity-slideshow-proposed/#controls)
Note that the Firefox slide doesn't show an icon because it wants that icon off the local disk. (Which doesn't work when it's on the web).

Again, any feedback at all relevant to this is appreciated :)

---

### Post by Merk42 on 2009-09-29
Don't know if you need the word "just" in "Just attach tags to your photos..." in F-Spot, also in Rhythmbox "Just plug in an MP3 player..."

In Evolution, take out the "You can" for "You can add your favorite..."

That way it's all the similar language, the fact that the user is the one doing it, is a given.


Hey no more "colour" for F-Spot! Of course now it's gone the other way and you have the Software Center / Software Centre thing.  Is that actually able to be addressed with translations?

---

### Post by Mr. Picklesworth on 2009-09-29
> **Merk42 said:**
> Don't know if you need the word "just" in "Just attach tags to your photos..." in F-Spot, also in Rhythmbox "Just plug in an MP3 player..."

In Evolution, take out the "You can" for "You can add your favorite..."

That way it's all the similar language, the fact that the user is the one doing it, is a given.


Hey no more "colour" for F-Spot! Of course now it's gone the other way and you have the Software Center / Software Centre thing.  Is that actually able to be addressed with translations?

Exactly. The defacto standard seems to be to use horrible US spellings for the C locale, then do extra translations for en_GB and en_CA. (Unfortunately, translations are still a bit confuddled, which is why I want to declare the strings frozen. For Lynx, I'll probably leave all the writing up to locales and just have f-spot-title and f-spot-point-1 as the base strings, for example).

I'm going to go ahead and play with your suggestions *right now*, because they absolutely make sense. Especially for consistency. You're right that I was aiming at a more direct tone, and pulling out the maybes really helps that. (Besides, in retrospect, the word "just" reminds me of everything I hate about Apple's written material). Thanks!

---

### Post by philinux on 2009-09-29
Keep going Mr.Picklesworth its looking better.

---

### Post by shafin on 2009-09-29
> Ubuntu is ready to play videos and music from the web and from DVDs.* It works straight away for free and popular formats;*** the ones we can always use without paying license fees**. *In other cases, Ubuntu will ask for permission and then download the right software from the Internet*.I think you can leave out the italicized lines on format. at least remove the bold line. That's material for a deep description, not an introduction.The last line is quite hard to comprehend for a non-technical person.

In the last slide, a link to ubuntuforums.org would be nice. For help on ubuntu, I find this site the most useful.

---

### Post by cariboo on 2009-09-29
On the Getting Help slide, I noticed you dropped the link to the forums, was there a reason for that?

---

### Post by Mr. Picklesworth on 2009-09-29
> **cariboo907 said:**
> On the Getting Help slide, I noticed you dropped the link to the forums, was there a reason for that?

Yep :) The forums are great, but there are many other fantastic help resources. For example, Launchpad Answers (in most apps go to "Help: Get Help Online..." - Beauty!), IRC, the commercial support, locos and the like. ubuntu.com/support has all of those presented nicely. Also, it fits with a URL the user already likely knows (ubuntu.com).
The other option is to list a whole bunch of them in the one place, which is not pleasant.

---

### Post by Mr. Picklesworth on 2009-10-10
Okay, here's the latest version which got a UI exception request. I've had feedback from a few different people, but thought I should ask you guys again!
[http://www3.telus.net/northlight/dylan/ubiquity-slideshow-proposed/#controls](http://www3.telus.net/northlight/dylan/ubiquity-slideshow-proposed/#controls)

A few more little changes to the text, and the icons are mostly swapped for Humanity icons now. I'd like to know what you think of the Ubuntu logo, especially; it's a modification of the start-here icon from the Human icon theme. (I got rid of the glossy lighting effect, most of the original shadow so it just serves as a border now, and added a tiny drop shadow).

Any suggestions for the icon at the very end? The question mark doesn't seem like the best way to cap this.

---

